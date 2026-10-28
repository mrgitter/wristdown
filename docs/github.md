# GitHub Setup

GitHub is the recommended note source for WristDown. It works well with a small notes repository, a folder inside a bigger repository, or an Obsidian vault synced with Git.

> Keep the folder you point WristDown at small: about 10 notes, 15 at most. The initial folder listing can get too large for the watch when there are many files in it, even if each file is tiny.

## 1. Prepare a repository

If you don't have a GitHub account yet, create one at [github.com](https://github.com/). Then create a **private** repository for your notes and add a few `.md` files.

Decide which repository, branch, and folder will hold your watch notes. For example:

```text
Repository: your-github-name/your-notes-repo
Branch: main
Folder: watch
```

The repository goes in GitHub's `owner/repo` format. If your notes sit in the repository root, you'll just leave the folder setting empty later.

Example layout:

```text
my-notes/
  watch/
    shopping.md
    tasks.md
    travel.md
```

WristDown reads exactly one folder (or the root, if the folder setting is empty). Don't point it at the root of a big repository or a whole Obsidian vault. Make a dedicated folder for watch-ready notes and sync just that.

## 2. Create a GitHub token

WristDown uses a fine-grained personal access token to read your notes. If you give the token **Contents: Read and write**, it can also write checkbox and recurring-task changes back.

### Open the fine-grained token settings

Create the token here: [https://github.com/settings/personal-access-tokens/new](https://github.com/settings/personal-access-tokens/new)

Or click through GitHub's settings:

1. Sign in to GitHub in a browser.
2. Click your profile picture in the upper-right corner.
3. Click **Settings**.
4. In the left sidebar, click **Developer settings**.
5. Expand **Personal access tokens**.
6. Click **Fine-grained tokens**.
7. Click **Generate new token**.

### Name the token

Anything works, for example:

```text
wristdown-notes
```

### Choose the resource owner

Under **Resource owner**, pick the GitHub user or organization that owns your notes repository. For `your-github-name/your-notes-repo`, that's `your-github-name`.

### Choose an expiration

GitHub recommends setting an expiration date, and that's the safer choice. **No expiration** is fine too if you don't want to rotate tokens.

Just know that if the token expires, sync stops working until you create a new token and update it in Garmin Connect.

### Limit repository access

Under **Repository access**, select **Only select repositories**, then pick your notes repository.

Don't choose **All repositories**. This token should only ever be able to access your watch notes.

### Pick the Contents permission

| Permission | Use this if | WristDown can |
|---|---|---|
| **Contents: Read-only** | You only want to read notes on the watch | Sync notes from GitHub, refresh changed notes, and work offline after sync |
| **Contents: Read and write** | You want watch changes synced back to GitHub | All of the above, plus write checkbox and recurring-task updates back to your Markdown files |

GitHub may also show **Metadata: Read-only**. That permission is required by GitHub; leave it as-is.

### Set the permissions

In the **Permissions** section:

1. Open **Repository permissions**.
2. Find **Contents**.
3. Set it to **Read-only** or **Read and write**.
4. Leave every other repository permission at **No access** (apart from the required **Metadata: Read-only** if shown).
5. Leave account and organization permissions unchanged.

### Generate the token

Click **Generate token**.

GitHub shows the token value exactly once. Copy it right away and keep it somewhere until you've pasted it into Garmin Connect. Treat it like a password.

## 3. Configure Garmin Connect

After installing WristDown:

1. Open the **Garmin Connect** app on your phone.
2. Go to **Devices -> Your watch -> Activities & Apps -> Apps**.
3. Select **WristDown -> Settings**.
4. Fill in the **GitHub** section:
   - **Repository:** in `owner/repo` format, for example `your-github-name/your-notes-repo`
   - **Token:** the token you just copied
   - **Folder:** the folder with your watch notes, for example `watch`; leave empty for the repository root
   - **Branch:** usually `main`
5. Save the settings.
6. Open WristDown on the watch and hit **Sync**.

If the repository and token are filled in, WristDown uses GitHub. Otherwise it falls back to [Flatnotes](flatnotes.md).

## 4. Use with Obsidian

I tested WristDown with [Obsidian](https://obsidian.md/) notes kept in GitHub via:

- the [Obsidian Git community plugin](https://community.obsidian.md/plugins/obsidian-git)
- the [Tasks community plugin](https://community.obsidian.md/plugins/obsidian-tasks-plugin)

The workflow that works well for me:

1. Keep your vault, or a notes folder from it, in GitHub.
2. Put the watch-friendly notes in the folder WristDown syncs.
3. Use Obsidian Tasks syntax for due dates and recurrence.
4. Let Obsidian Git push your edits to GitHub.
5. Hit **Sync** on the watch.

Example task note:

```markdown
# Today

- [ ] Water plants 🔁 every day 📅 2026-06-04
- [ ] Review release notes 📅 2026-06-05
- [x] Pay invoice 📅 2026-06-01 ✅ 2026-06-01
```

When you toggle a task on the watch, WristDown updates the Markdown file in GitHub (with a **Read and write** token). For recurring tasks, it writes the next occurrence back into the note.

> Note: the Tasks plugin keeps a completed line and creates a new active one each time a recurring task is done. WristDown keeps a single active line per recurring task and rewrites it in place. If that history matters to you, read the [Markdown reference](markdown.md) before completing recurring Tasks-plugin tasks from the watch.

## Note filtering

The **Note Keyword Filter** setting limits GitHub-synced notes by filename. Leave it empty to sync everything in the folder.

A small dedicated folder is more reliable than a filter on a big one, because the watch may still have to receive the full file list before the filter can narrow it down.

## Troubleshooting

### GitHub sync fails

- Check that **Repository** is exactly `owner/repo`.
- Check that the **Branch** exists.
- Check the **Folder**, or leave it empty for the repository root.
- Verify the token can access that repository.
- For private repositories, make sure the token is scoped to that repository.
- For sync-back, make sure the token has **Contents: Read and write**.
- If the folder has many files, move the watch notes into a smaller dedicated folder. Aim for 10 or fewer; 15 is the realistic ceiling.

### Notes don't appear

- Use `.md` or `.txt` files.
- Put files directly in the configured folder; nested folders are skipped.
- Files of 30 KB or more are skipped. A note shows in full up to 15,000 characters (10,000 on Forerunner 255/255S); a longer one shows its first part and is read-only on the watch.
- Keep the folder small. Too many files can make the initial sync payload fail before any notes are processed.
- Check whether the **Note Keyword Filter** is excluding them.

### Task changes don't sync back

- Confirm **Contents** is set to **Read and write**.
- Confirm the note still exists in GitHub.
- If the file was edited on GitHub after the watch last synced it, WristDown throws away the local change rather than overwrite the newer content. The GitHub version wins.
- Run **Sync** again to refresh the watch copy.

### Token problems

- If sync worked before and then stopped, check whether the token expired.
- If GitHub asks for organization approval, wait for the approval or use a repository on your personal account.

## Security notes

- Prefer a dedicated token limited to your one notes repository.
- Revoke it if you stop using WristDown or lose the watch.
- Don't put real secrets in notes you sync to a watch.

References:

- [GitHub: Managing your personal access tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)
- [GitHub: Permissions required for fine-grained personal access tokens](https://docs.github.com/en/rest/authentication/permissions-required-for-fine-grained-personal-access-tokens?apiVersion=2026-03-10)
