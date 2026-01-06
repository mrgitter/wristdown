# Server Setup Guide

WristDown syncs notes from a [Flatnotes](https://github.com/dullage/flatnotes) server. This guide covers how to set up your server for WristDown compatibility.

## Prerequisites

- A running Flatnotes instance
- HTTPS enabled (required for Garmin Connect IQ)
- A reverse proxy (nginx recommended)

## Flatnotes Installation

Follow the [official Flatnotes documentation](https://github.com/dullage/flatnotes) to set up your server. The quickest method is Docker:

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

## Critical: PUT to PATCH Workaround

**This step is required for checkbox sync-back to work.**

Garmin Connect IQ does not support the HTTP PATCH method. Flatnotes uses PATCH for updating notes. To work around this, configure your reverse proxy to rewrite PUT requests to PATCH.

### nginx Configuration

```nginx
server {
    listen 443 ssl;
    server_name notes.yourdomain.com;

    ssl_certificate /path/to/cert.pem;
    ssl_certificate_key /path/to/key.pem;

    location /api/notes/ {
        # Rewrite PUT to PATCH for Flatnotes compatibility with Garmin
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

### Caddy Configuration

```caddyfile
notes.yourdomain.com {
    @put_notes {
        method PUT
        path /api/notes/*
    }

    handle @put_notes {
        # Caddy doesn't have built-in method rewriting
        # You may need a plugin or alternative approach
        reverse_proxy localhost:8080
    }

    reverse_proxy localhost:8080
}
```

Note: Caddy's method rewriting requires additional configuration. nginx is recommended for full compatibility.

## Garmin Connect Mobile Settings

After installing WristDown from the Connect IQ Store:

1. Open the **Garmin Connect** app on your phone
2. Go to **Devices** → Select your watch → **Activities & Apps** → **Apps**
3. Find **WristDown** and tap **Settings**
4. Enter:
   - **Server URL**: `https://notes.yourdomain.com` (include https://)
   - **Username**: Your Flatnotes username
   - **Password**: Your Flatnotes password

Settings sync to your watch automatically when connected via Bluetooth.

## Authentication

WristDown uses JWT (JSON Web Token) authentication:

1. On first sync, WristDown requests a token from `/api/token`
2. The token is stored on the watch
3. All subsequent requests include the token in the Authorization header
4. Tokens are refreshed automatically when needed

## API Endpoints Used

| Endpoint | Method | Purpose |
|----------|--------|---------|
| `/api/token` | POST | Authenticate and get JWT token |
| `/api/search` | GET | List available notes |
| `/api/notes/{title}` | GET | Fetch note content |
| `/api/notes/{title}` | PUT* | Update note (checkbox changes) |

*PUT is rewritten to PATCH by the reverse proxy

## Troubleshooting

### "Connection Error" on Sync

- Verify your server URL is correct and includes `https://`
- Check that your server is accessible from the internet
- Ensure SSL certificate is valid (not self-signed)
- Confirm your phone has internet connectivity

### Notes Sync but Checkboxes Don't Save

- Verify the PUT→PATCH rewrite is configured in your reverse proxy
- Check nginx/proxy logs for 405 Method Not Allowed errors
- Test manually: `curl -X PUT https://notes.yourdomain.com/api/notes/test`

### "Authentication Failed"

- Double-check username and password in Garmin Connect settings
- Verify Flatnotes is configured with `FLATNOTES_AUTH_TYPE=password`
- Try logging into Flatnotes web interface with same credentials

### Notes Not Appearing

- Ensure notes exist in your Flatnotes `/data` directory
- Check that note files have `.md` extension
- Verify Flatnotes container has read permissions on the notes directory

### Large Notes Fail to Load

WristDown has memory constraints typical of embedded devices. Very large notes may:
- Take longer to process
- Display a warning if memory usage is high
- Fail to load if they exceed available memory

Consider breaking very long notes into smaller ones.

## Security Considerations

- Always use HTTPS in production
- Keep your Flatnotes instance updated
- Use a strong password
- Consider network-level restrictions (VPN, IP allowlisting) for additional security
