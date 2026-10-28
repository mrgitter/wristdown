# WristDown 2.0 Changelog

For what changed after 2.0, see the [WristDown 2.1 changelog](changelog-v2.1.md).

## 2.0.1

- Added support for the fēnix 9 series (fēnix 9, 9 Pro and 9 Pro Solar).
- Fixed checkboxes and list items indented with spaces.
- Fixed bold italic text written with mixed markers (such as `**_text_**`) and underscores inside words.
- Fixed notes with uppercase file extensions (such as `.MD`) not syncing from GitHub.
- Fixed a crash syncing long notes on Fenix 6 Pro family, Forerunner 945 LTE and MARQ Gen 1 watches.
- Existing notes receive the formatting fixes automatically after updating.

## 2.0.0

### New features

- **GitHub note source** - sync Markdown and text notes from a GitHub repository, branch, and folder.
- **GitHub sync-back** - checkbox and task changes made on the watch are uploaded back to GitHub.
- **Conflict protection** - if a note changed on GitHub before the watch uploads an edit, the GitHub version is kept.
- **Obsidian-style task reminders** - due dates, done dates, and supported recurrence rules are parsed from task lines in GitHub notes.
- **Recurring task completion** - completing a recurring GitHub task advances its due date and updates the task line.
- **Reminders view** - tasks and events from GitHub notes in a dedicated screen, grouped by urgency.
- **Reminder notifications** - optional Garmin notifications when a reminder is due.
- **Event reminders** - plain list items with event dates, including yearly dates such as birthdays.
- **Frontmatter preservation** - YAML frontmatter is kept on sync-back.
- **Folder and branch settings** - notes folder and branch configurable in Garmin Connect.
- **Scrollbar option** - scroll indicator shown always, only for long notes, or never.
- **Reminder options** - reminder menu position, empty-state visibility, and notification behavior.

### User interface

- Main menu reminder item shows reminder counts and urgency.
- New reminder detail screen: one reminder per screen, due labels, navigation to the source note.
- New glance with a segmented reminder status bar.
- New note, task, and reminder category icons.
- Clearer styling for checked and unavailable checkboxes.
- Touching a note that starts with checkboxes snaps focus to the first checkbox.
- Options menu grouped into Sync, Notes, Reminders, and About.
- Important sync errors stay on screen longer.

### Performance and reliability

- Replaced the built-in scroll animation with a custom timer-based one: smoother, no skipped frames, scales with scroll distance.
- Added flick momentum to touch scrolling; button scroll steps adjusted to screen size.
- Reduced release build size to lower memory pressure on older watches.
- Reduced reminder build for Fenix 6 Pro family, Forerunner 945 LTE, and MARQ Gen 1: notes, sync, Markdown display, checkboxes, and in-note task/reminder dates are kept; the reminder list, reminder options, notifications, background processing, and glance summary are omitted.

### Bug fixes

- Fixed an out-of-memory crash risk during rapid note scrolling.
- Fixed inconsistent dimming color for disabled/secondary note text.
- Fixed missing left-swipe for note options on touch watches; PIN protection can now be changed from the note screen.
