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
- **View markdown** with smooth pixel-based scrolling optimized for circular displays
- **Toggle checkboxes** - tap to check/uncheck tasks, changes sync back to server
- **Multiple font sizes** - Medium, Small, or Tiny to fit more content
- **Sort notes** by title or last modified date
- **Demo mode** - try the app with the public demo.flatnotes.io server (no setup required)

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

### Try Demo Mode (No Setup)

1. Install WristDown from the Connect IQ Store
2. Open the app on your watch
3. Select **Demo** from the menu
4. Browse sample notes from demo.flatnotes.io

### Use Your Own Server

1. Set up a [Flatnotes](https://github.com/dullage/flatnotes) server
2. Configure the server for WristDown compatibility ([setup guide](docs/setup.md))
3. In the Garmin Connect Mobile app, go to WristDown settings
4. Enter your server URL, username, and password
5. Open WristDown on your watch and select **Sync**

## Server Requirements

WristDown connects to [Flatnotes](https://github.com/dullage/flatnotes), a self-hosted note-taking app. You'll need:

- A running Flatnotes instance accessible over HTTPS
- A reverse proxy (nginx) configured to handle the PUT→PATCH workaround

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
