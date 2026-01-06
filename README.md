# WristDown

**Markdown notes on your Garmin watch** - Sync notes from your self-hosted [Flatnotes](https://github.com/dullage/flatnotes) server, view them with smooth scrolling, and toggle checkboxes right from your wrist.

<!-- Connect IQ Store Badge - Update URL after publishing -->
[<img src="https://developer.garmin.com/static/available-badge-9e49ebfb7336ce47f8df66dfe45d28ae.svg" width="200">](https://apps.garmin.com/apps/YOUR_APP_ID)

## Screenshots

<!-- Add screenshots here after capturing from device/simulator -->
| Notes List | Note View | Checkbox Toggle |
|------------|-----------|-----------------|
| *Coming soon* | *Coming soon* | *Coming soon* |

## Features

- **Sync notes** from your self-hosted Flatnotes server with JWT authentication
- **Quick notes** - enter up to 3 notes directly in Garmin Connect settings (no server needed)
- **View markdown** with smooth pixel-based scrolling optimized for circular displays
- **Toggle checkboxes** - tap to check/uncheck tasks, changes saved on watch (optionally sync back to server)
- **Multiple font sizes** - Medium, Small, or Tiny to fit more content
- **Sort notes** by title or last modified date
- **Demo mode** - works out of the box with demo.flatnotes.io (no configuration needed)

## Supported Devices

Works on **57+ Garmin watches** including:
- Fenix 6/7/8 series
- Epix (Gen 2) / Epix Pro
- Forerunner 165/255/265/955/965/970
- Venu 2/3/4 series
- Instinct 3 AMOLED
- MARQ (Gen 2) series
- Descent Mk3 series
- ...and many more

Requires **API Level 3.4.0+** and a phone with Garmin Connect Mobile.

## Quick Start

### Demo Mode (No Setup)

WristDown works out of the box! The default server URL points to demo.flatnotes.io, so you can:

1. Install WristDown from the Connect IQ Store
2. Open the app on your watch
3. Select **Sync** - sample notes will be downloaded from the demo server

To use your own server, simply change the server URL in Garmin Connect settings.

### Quick Notes (No Server)

You can enter up to 3 notes directly in the app settings - no server required:

1. Open **Garmin Connect** app on your phone
2. Go to **Devices** → Your watch → **Activities & Apps** → **Apps**
3. Find **WristDown** → **Settings**
4. Enter your notes in the **Note 1**, **Note 2**, **Note 3** fields (supports markdown)
5. Open WristDown on your watch - your notes appear at the top of the list

Quick notes are stored locally on the watch and appear before any synced notes.

### Use Your Own Server

1. Set up a [Flatnotes](https://github.com/dullage/flatnotes) server
2. In the Garmin Connect Mobile app, go to WristDown settings
3. Enter your server URL, username, and password
4. Open WristDown on your watch and select **Sync**

See the [setup guide](docs/setup.md) for detailed configuration including optional checkbox sync-back.

## Server Requirements

WristDown connects to [Flatnotes](https://github.com/dullage/flatnotes), a self-hosted note-taking app. You'll need:

- A running Flatnotes instance accessible over HTTPS
- (Optional) A reverse proxy configured to rewrite PUT→PATCH for checkbox sync-back

See the [detailed setup guide](docs/setup.md) for configuration instructions.

## Markdown Support

WristDown renders common markdown syntax on your watch:

| Feature | Syntax |
|---------|--------|
| **Bold** | `**text**` or `__text__` |
| *Italic* | `*text*` or `_text_` |
| Headers | `#`, `##`, `###` |
| ~~Strikethrough~~ | `~~text~~` |
| `Inline code` | `` `code` `` |
| Checkboxes | `[ ]` unchecked, `[x]` checked |
| Lists | `- item` or `1. item` |
| Horizontal rule | `---` |

See the [full markdown reference](docs/markdown.md) for details.

## Languages

The app interface is available in 22 languages with full translations for English and Lithuanian. Other languages fall back to English.

## Links

- [Setup Guide](docs/setup.md) - Server configuration instructions
- [Markdown Reference](docs/markdown.md) - Supported syntax
- [Flatnotes](https://github.com/dullage/flatnotes) - The note server WristDown connects to
- [Connect IQ Store](#) - *Link coming soon*

## Feedback

Found a bug or have a feature request? Open an issue in this repository.
