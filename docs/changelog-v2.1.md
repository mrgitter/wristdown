# WristDown 2.1 Changelog

## New features

- **Bold and italic letters** - on watches that can draw them, bold, italic and bold italic text uses real bold and italic letters as well as its color, and `# Header 1` is bold. Other watches keep the colors. Emoji still show inside bold and italic text.
- **Links** - `[text](https://...)` and `<https://...>` show in blue. Scroll to one, press START or tap it, and it opens on your phone. See [Links](markdown.md#links).
- **Bookmarks** - notes can reopen where you stopped reading: Off (default), Long Notes, or All Notes in **Options > Notes > Bookmarks**, plus a per-note **Bookmark** toggle in note options.
- **Long notes** - a note shows in full up to 15,000 characters (10,000 on Forerunner 255/255S). A longer note shows its first part and is read-only on the watch. Files of 30 KB or more are skipped.
- **Welcome note** - until GitHub, Flatnotes or a Quick Note is set up, the main menu starts with **Welcome**: setup steps, a daily setup reminder, and a link to the docs. It goes away once a source or a Quick Note is configured.
- **Sync setup help** - pressing **Sync** with nothing configured explains what to set up in Garmin Connect and can open the docs on your phone.
- **About** - tips for using the app on the watch, and links to the docs, the Markdown reference, bug reports and the store page.

- **New watches** - vívoactive 5 and vívoactive 6.

## Reminders and tasks

- **Redesigned Reminders screen** - a colored arc of the overdue, today and later totals along the top, a position counter, and a preview of the next reminder at the bottom. On touch watches, tap the top or bottom of the screen to move between reminders.
- **Main menu Reminders item** - laid out like a note item, with "All clear" when nothing is due. New filled reminder icons.
- **Weekday repeat rules** - `🔁 every weekday`, day lists such as `every Monday and Friday`, and `every N weeks on ...` for tasks. See [Days of the week](markdown.md#days-of-the-week-tasks-only).
- **Recurring tasks**:
  - A task whose `🔁` rule isn't supported, or a `🔁` task without a `📅` date, is read-only on the watch, so completing it there can't end the series.
  - Monthly and yearly rules keep their day of month, and advanced dates are always written with the year.
  - Repeat intervals are capped (for example 1 to 520 weeks).
- **Repeating events** - a `@remind(...)` lead of one repeat period or more is ignored; the event notifies at its time.
- **Time zones** - reminder times stay correct after the watch changes time zone.
- **Midnight** - reminder counts and the glance update at local midnight.

Reminder features need a watch with full reminder support; see [Reminders on older watches](../README.md#reminders-on-older-watches).

## User interface

- Sharper 40x40 app icon at the top of the main menu on the Forerunner 255 family, Forerunner 945 LTE, fēnix 7 Pro and 7X Pro (without Wi-Fi), and MARQ Gen 1.
- Consistent screen transitions between menus, notes and messages.
- The reminders list says "1 DAY" instead of "1 DAYS".

## Performance and reliability

- Faster GitHub sync: the folder listing is much smaller.
- Lower memory use during sync, note processing and opening notes.

## Bug fixes

- Fixed watch edits being lost when a note's own upload finished at the same time.
- Fixed a second completion of a recurring task being dropped.
- Fixed old overdue reminders all notifying at once after the reminder data was rebuilt.
- Fixed background reminder checks stopping after an error.
- Fixed crashes on densely formatted notes.
- Fixed long words being cut off when wrapped.
- Fixed glance all-day labels not matching the reminders list.
- Fixed Flatnotes emoji being overwritten on the server: a note whose emoji reach the watch damaged is read-only there, so ticking a task can't write the damaged text back.
- Fixed **Always Show** not taking effect until the app restarted.

Earlier: [WristDown 2.0 changelog](changelog-v2.0.md).
