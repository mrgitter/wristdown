# Markdown Reference

WristDown renders markdown notes on your Garmin watch. Since Garmin watches don't support bold/italic fonts, formatting is displayed using colors and visual styles.

## Supported Syntax

| Syntax | How it's displayed |
|--------|-------------------|
| `**bold**` or `__bold__` | Yellow text |
| `*italic*` or `_italic_` | Light gray text |
| `**_bold italic_**` | Orange text |
| `# Header 1` | White text with underline |
| `## Header 2` | Light gray text with underline |
| `### Header 3` | Light gray text with underline |
| `` `code` `` | Cyan text |
| `~~strikethrough~~` | Dark gray text |
| `[ ]` | Interactive checkbox (unchecked) |
| `[x]` or `[X]` | Interactive checkbox (checked) |
| `- item` | Bullet point |
| `1. item` | Numbered list |
| `---` | Horizontal line |

## Interactive Checkboxes

The checkbox feature is what makes WristDown useful for task management on your watch.

### How It Works

1. **View** - Checkboxes are displayed with clear checked/unchecked states
2. **Navigate** - Use the up/down buttons to move focus between checkboxes
3. **Toggle** - Press select/tap to toggle the focused checkbox
4. **Auto-save** - Changes are saved locally immediately
5. **Sync back** - When you exit the note, changes can sync to your Flatnotes server (if configured)

### Example Task List

```markdown
# Shopping List

- [x] Milk
- [x] Bread
- [ ] Eggs
- [ ] Butter

# Tasks

- [x] Reply to email
- [ ] Review document
- [ ] Call dentist
```

### Checkbox Tips

- Checkboxes must be at the start of a line (after the list marker if using lists)
- Both `[x]` and `[X]` are recognized as checked
- Changes are saved locally on the watch immediately
- Server sync-back requires PUT→PATCH proxy configuration (see [setup guide](setup.md))

## Headers

Headers are rendered with underlines to provide visual hierarchy:

```markdown
# Main Header
## Section Header
### Subsection Header
```

All three header levels are supported. Headers help organize longer notes.

## Text Formatting

You can combine formatting in a single line:

```markdown
This is **bold** and *italic* text with `code`.
```

Bold italic (`**_text_**`) is also supported and displays in orange.

## Lists

Both unordered and ordered lists are supported:

```markdown
Unordered:
- First item
- Second item
- Third item

Ordered:
1. First step
2. Second step
3. Third step
```

List items can contain checkboxes:

```markdown
- [ ] Unchecked task
- [x] Completed task
```

## Horizontal Rules

Use three or more dashes to create a horizontal line separator:

```markdown
Section one content here.

---

Section two content here.
```

## Display Optimization

WristDown is optimized for circular Garmin watch displays:

- **Dynamic text width** - Text width adjusts based on vertical position (narrower at top/bottom edges, wider in the center)
- **Smooth scrolling** - Pixel-based scrolling for comfortable reading
- **Font sizes** - Choose Medium, Small, or Tiny in Options to fit more content

## Unsupported Syntax

The following markdown features are not currently rendered:

- Links `[text](url)` - displayed as plain text
- Images `![alt](url)` - not displayed
- Block quotes `> quote` - displayed as plain text
- Code blocks (fenced) - displayed as plain text
- Tables - displayed as plain text
- Nested lists - flattened to single level

## Tips for Watch-Friendly Notes

1. **Keep notes concise** - Large notes take longer to process
2. **Use headers** - They help organize longer content
3. **Use checkboxes** - Interactive and useful for quick tasks
4. **Short lines** - Circular displays have limited width
5. **Simple formatting** - Basic markdown works best on small screens
