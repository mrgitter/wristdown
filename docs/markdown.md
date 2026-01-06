# Markdown Reference

WristDown renders markdown notes on your Garmin watch. This document covers supported syntax and the interactive checkbox feature.

## Supported Syntax

| Feature | Syntax | Example |
|---------|--------|---------|
| **Bold** | `**text**` or `__text__` | **important** |
| *Italic* | `*text*` or `_text_` | *emphasis* |
| Headers | `#`, `##`, `###` | Rendered larger |
| ~~Strikethrough~~ | `~~text~~` | ~~done~~ |
| `Inline code` | `` `code` `` | `variable` |
| Checkbox (unchecked) | `[ ]` | Interactive |
| Checkbox (checked) | `[x]` or `[X]` | Interactive |
| Unordered list | `- item` | Bullet point |
| Ordered list | `1. item` | Numbered |
| Horizontal rule | `---` | Separator line |

## Interactive Checkboxes

The checkbox feature is what makes WristDown unique for task management on your watch.

### How It Works

1. **View** - Checkboxes are displayed with clear checked/unchecked states
2. **Navigate** - Use the up/down buttons to move focus between checkboxes
3. **Toggle** - Press select/tap to toggle the focused checkbox
4. **Auto-save** - Changes are saved locally immediately
5. **Sync back** - When you exit the note, changes sync to your Flatnotes server

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
- Changes sync when you exit the note view, not immediately on toggle
- If sync fails, changes remain saved locally until next successful sync

## Headers

Headers are rendered in larger text to provide visual hierarchy:

```markdown
# Large Header
## Medium Header
### Small Header
```

All three header levels are supported. Headers help organize longer notes.

## Text Formatting

You can combine formatting in a single line:

```markdown
This is **bold** and *italic* text with `code`.
```

Nested formatting (bold italic) is not currently supported.

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

1. **Keep notes concise** - Large notes may be slow to load
2. **Use headers** - They help navigate longer content
3. **Use checkboxes** - Interactive and useful for quick tasks
4. **Short lines** - Circular displays have limited width
5. **Avoid complex formatting** - Simple markdown works best
