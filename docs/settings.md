# Settings Guide

WristDown settings live in two places:

- **Options** in the watch app, for day-to-day preferences.
- **Garmin Connect** on your phone, for account setup, Quick Notes, filtering, and the PIN.

## Watch options

Open WristDown on the watch, then select **Options**.

### Sync

| Setting | What it does |
|---|---|
| **Auto-Refresh** | Lets WristDown check for updates and upload your GitHub task/checkbox changes on its own, instead of waiting for a manual Sync. Off by default. |
| **Sync Alerts** | How automatic uploads report back: **Alert + Vibrate**, **Vibrate only**, or **Silent**. |

With **Auto-Refresh** on, WristDown checks for newer notes, refreshes a stale GitHub note when you open it, and uploads pending changes after you leave a note. If a full sync is needed, it still asks first.

With it off, your watch changes are still saved locally; they're uploaded the next time you run **Sync**.

### Notes

| Setting | What it does |
|---|---|
| **Font Size** | Note text size: Medium, Small, or Tiny. |
| **Sort** | Sort synced notes by **Last Modified** or **Title**. Quick Notes stay at the top. |
| **Scrollbar** | The note scroll indicator: Off, Always, or only for Long Notes. |
| **Bookmarks** | Reopen notes where you stopped reading: Off (default), Long Notes (three screens or more), or All Notes. Each note can override this under Note options. |

### Reminders

| Setting | What it does |
|---|---|
| **Position** | Puts **Reminders** at the top or bottom of the main menu. |
| **Always Show** | Shows **Reminders** even when there's nothing due. |
| **Notifications** | Lets due reminders appear as Garmin notifications. |

Reminder notifications work from data already stored on the watch, so they keep working when you're away from connectivity.

> On Fenix 6 Pro family, Forerunner 945 LTE, and MARQ Gen 1 watches, the reminder list, reminder options, notifications, background processing, and glance summary aren't available, because those lower-memory watches run a reduced reminder build. Notes, sync, Markdown display, checkboxes, and in-note task/reminder dates all still work. Full device list in the [README](../README.md#reminders-on-older-watches).

### About

Shows the built-in WristDown note: tips for using the app on the watch, and links to these docs, bug reports and the store page. Until you set up GitHub, Flatnotes or a Quick Note, it is the Welcome note instead, with setup steps and a daily reminder to set up sync (in the Reminders list, on watches with full reminder support).

## Note options

While viewing a note:

- **Touchscreen watches:** swipe right-to-left.
- **Button watches:** hold MENU/UP.

From there you can choose **Protect with PIN** or **Remove Protection**. Set the PIN first in Garmin Connect.

**Bookmark** turns reading-position memory on or off for this note, whatever the global **Bookmarks** setting says. When it's on, the note reopens where you left it. If the note's layout changed since then (a new font size, or an edit from sync), it opens at about the same place in the note.

## Garmin Connect settings

Open **Garmin Connect -> Devices -> Your watch -> Activities & Apps -> Apps -> WristDown -> Settings**.

### GitHub

| Setting | What it does |
|---|---|
| **Repository** | Your repository as `owner/repo`. |
| **Token** | Your GitHub token. Give it write access if you want watch changes uploaded. |
| **Folder** | The folder with your watch notes. Leave empty for the repository root. |
| **Branch** | Usually `main`. |

If **Repository** and **Token** are filled in, WristDown uses GitHub.

### Flatnotes Settings

| Setting | What it does |
|---|---|
| **Flatnotes URL** | URL of your Flatnotes server. |
| **Flatnotes Username** | Your Flatnotes username, if needed. |
| **Flatnotes Password** | Your Flatnotes password, if needed. |

If GitHub isn't configured, WristDown uses Flatnotes.

### App Settings

| Setting | What it does |
|---|---|
| **Note Keyword Filter** | Syncs only notes matching the keyword. Leave empty to sync everything. |

For GitHub, a small dedicated folder is usually easier than a broad folder plus a filter.

### Quick Notes

| Setting | What it does |
|---|---|
| **Note 1**, **Note 2**, **Note 3** | Short notes typed directly into Garmin Connect. They appear at the top of the watch note list and don't sync to GitHub or Flatnotes. |

### Security

| Setting | What it does |
|---|---|
| **App PIN** | A 3-5 digit PIN for protected notes. Leave empty to disable PIN protection. |
| **PIN Grace Period** | How soon the PIN is required again after a successful unlock. |

## Local changes

For GitHub notes, task and checkbox changes made on the watch are saved locally first, then uploaded:

- automatically, when **Auto-Refresh** is on; or
- the next time you run **Sync**.

> If the note was edited on GitHub before your watch change gets uploaded, the watch change is discarded and the GitHub version wins. Run **Sync** to get the latest copy.

## Offline workflow

For travel, errands, workouts, or anywhere connectivity is bad:

1. Run **Sync** before you go offline.
2. Keep reminder **Notifications** on if you want reminders from your stored notes.
3. Turn **Auto-Refresh** off if you don't want sync attempts while offline.
4. Use tasks and checkboxes normally.
5. Back online, run **Sync** to upload what's pending.

If connectivity is just spotty rather than gone, I'd recommend **Auto-Refresh** on with **Sync Alerts** set to **Vibrate only** or **Silent**. WristDown tries uploads when it can, without showing sync messages every time you move in and out of coverage.

> Reminder notifications in this workflow need a watch with full reminder support; they're not available on Fenix 6 Pro family, Forerunner 945 LTE, or MARQ Gen 1.
