# Setup Guide

WristDown has three ways to get notes onto the watch:

- **GitHub** - recommended; sync Markdown files from a repository, no server needed.
- **Flatnotes** - still supported if you already run a Flatnotes server.
- **Quick Notes** - up to 3 notes typed directly into Garmin Connect settings.

Until GitHub, Flatnotes or a Quick Note is set up, the main menu starts with **Welcome**: a short note with these steps, a link to the docs, and a daily reminder to set up sync (in the Reminders list, on watches with full reminder support). Welcome and its reminder go away as soon as a source or a Quick Note is configured.

## Recommended: GitHub

GitHub is the main source since 2.0. It works well with a small notes repository, a folder inside a bigger repository, or an Obsidian vault synced with Git.

Use GitHub if you want:

- no server to host,
- `.md` and `.txt` notes from a repository,
- checkbox and recurring-task changes synced back from the watch,
- timed task and event reminders (these work only with GitHub),
- an Obsidian-friendly workflow.

The [GitHub setup guide](github.md) covers the repository, token creation, Garmin Connect settings, Obsidian notes, and troubleshooting.

## Flatnotes

Flatnotes was the original sync source and still works for notes and checkboxes. Task and event reminders are not supported with Flatnotes; they need GitHub as the source.

If you already run a server, see the [Flatnotes setup guide](flatnotes.md) for the prerequisites, Garmin Connect settings, the optional checkbox sync-back proxy rewrite, and troubleshooting.

## Quick Notes

Quick Notes are edited directly in Garmin Connect:

1. Open **Garmin Connect**.
2. Go to **Devices -> Your watch -> Activities & Apps -> Apps**.
3. Select **WristDown -> Settings**.
4. Fill **Note 1**, **Note 2**, or **Note 3**.
5. Open WristDown on the watch.

They appear at the top of the note list. Handy for short static notes, but they don't sync to GitHub or Flatnotes.

## Source priority

If the GitHub repository and token settings are filled in, WristDown syncs from GitHub. Otherwise it falls back to the Flatnotes settings.

Quick Notes are separate from all of that and work alongside either source.

## Note filtering

The **Note Keyword Filter** setting limits which notes get synced, by title or filename.

- GitHub: filters by filename.
- Flatnotes: filters through Flatnotes search.
- Quick Notes: not affected.

Leave it empty to sync everything.

For GitHub, a small dedicated folder beats filtering a big one, because the watch may still have to receive the full file list of the folder before the filter can narrow it down.

## General troubleshooting

### Large or numerous notes fail to load

Watches don't have much memory. Big notes take longer to process or get skipped, and too many notes can make sync fail outright, especially with GitHub, where the first response for a folder lists every file in it.

Recommended limits: keep notes short and keep the watch folder to about 10 notes (don't go past 15). A note shows in full up to 15,000 characters (10,000 on Forerunner 255/255S); a longer one shows its first part and is read-only on the watch. Files of 30 KB or more are skipped. See [Long notes](../README.md#long-notes). Flatnotes isn't hit by the folder-listing issue in the same way, but small, focused notes are still the way to go.

### Too many reminders

Reminder count matters too. During sync, WristDown precomputes everything the reminder list, glance, notifications, and background scheduler need, and the background updates that mark reminders due have to run inside Garmin's strict background CPU and memory limits. So a big reminder set can look fine in the foreground and then quietly fail in the background.

> Higher counts may work on some watches, but for reliable daily use keep active reminders to about 20 or fewer.
> Above about 30, completing a task can make WristDown close on watches with less memory, such as the Forerunner 255.

Fenix 6 Pro family, Forerunner 945 LTE, and MARQ Gen 1 watches run a reduced reminder build: notes and in-note task/reminder dates still work, but there's no reminder list, notifications, background processing, or glance summary. The full model list is in the [README](../README.md#reminders-on-older-watches).

## Security notes

- Use HTTPS for all remote sources.
- Prefer a dedicated GitHub token limited to your one notes repository.
- Revoke the token if you stop using WristDown or lose the watch.
- Don't put real secrets in notes you sync to a watch.
