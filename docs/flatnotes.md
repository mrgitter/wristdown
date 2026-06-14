# Flatnotes Setup

Flatnotes was WristDown's original sync source and is still supported if you run a server. For most new users, [GitHub](github.md) is the simpler option, since there is nothing to host.

Flatnotes sync covers notes and checkboxes. The timed task and event reminders added in 2.0 work only with GitHub as the sync source.

## Prerequisites

- A running [Flatnotes](https://github.com/dullage/flatnotes) instance
- HTTPS enabled
- Garmin Connect Mobile paired with the watch
- Optionally, a reverse proxy rewrite for checkbox sync-back (see below)

## Flatnotes installation

Follow the official Flatnotes documentation. A simple Docker setup looks like this:

```bash
docker run -d \
  -p 8080:8080 \
  -e FLATNOTES_AUTH_TYPE=password \
  -e FLATNOTES_USERNAME=your_username \
  -e FLATNOTES_PASSWORD=your_password \
  -e FLATNOTES_SECRET_KEY=your_secret_key \
  -v /path/to/notes:/data \
  dullage/flatnotes:latest
```

## Garmin Connect settings

After installing WristDown:

1. Open the **Garmin Connect** app on your phone.
2. Go to **Devices -> Your watch -> Activities & Apps -> Apps**.
3. Select **WristDown -> Settings**.
4. Fill in the **Flatnotes Settings** section:
   - **Flatnotes URL:** `https://notes.yourdomain.com`
   - **Flatnotes Username:** your Flatnotes username
   - **Flatnotes Password:** your Flatnotes password
5. Save the settings.
6. Open WristDown on the watch and hit **Sync**.

WristDown uses Flatnotes whenever the GitHub repository and token settings are empty.

## Note filtering

The **Note Keyword Filter** setting limits which notes get synced, using Flatnotes search. Leave it empty to sync everything.

## Optional PUT to PATCH rewrite

You only need this for checkbox sync-back. Without it, checkboxes still work on the watch, but the changes won't be written back to Flatnotes.

The reason it exists: Garmin Connect IQ can't send HTTP PATCH requests, and PATCH is what Flatnotes expects for note updates. The workaround is to have your reverse proxy rewrite WristDown's PUT into a PATCH.

nginx example:

```nginx
server {
    listen 443 ssl;
    server_name notes.yourdomain.com;

    ssl_certificate /path/to/cert.pem;
    ssl_certificate_key /path/to/key.pem;

    location /api/notes/ {
        if ($request_method = PUT) {
            proxy_method PATCH;
        }
        proxy_pass http://localhost:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }

    location / {
        proxy_pass http://localhost:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

Caddy example:

```caddyfile
notes.yourdomain.com {
    @put_notes {
        method PUT
        path /api/notes/*
    }

    handle @put_notes {
        reverse_proxy {
            to localhost:8080
            method PATCH
        }
    }

    reverse_proxy localhost:8080
}
```

## Troubleshooting

### Connection errors

- Make sure the server URL starts with `https://`.
- Check that the server is reachable from the internet.
- Check that the SSL certificate is valid.
- Double-check the username and password.

### Checkbox changes don't sync back

- Confirm the PUT-to-PATCH rewrite is configured in your proxy.
- Confirm Flatnotes accepts note updates through the proxy.
- If you don't need sync-back, you can skip the rewrite entirely.

## Security notes

- Use HTTPS.
- Keep your Flatnotes credentials private.
- Don't put real secrets in notes you sync to a watch.
