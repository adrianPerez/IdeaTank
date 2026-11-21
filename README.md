# IdeaTank

A searchable, taggable index for your ideas. Paste text or upload a file, and IdeaTank finds the ideas in it, lets you review them, and adds them to an index you can search, tag, filter and sort.

It is a single file, `index.html`, with no server and no build step. Open it in a browser, or host it anywhere static (for example GitHub Pages: Settings → Pages → deploy from this branch).

## What it reads

| Source | How ideas are found |
|---|---|
| Pasted text, `.txt`, `.md` | One idea per list item, heading, paragraph or line (chosen automatically; you can switch in the preview) |
| Pasted rich text from Word or Google Docs | Keeps the lists, headings and bold titles |
| Pasted spreadsheet cells, `.csv`, `.tsv`, `.xlsx`, `.xls`, `.ods` | One idea per row. Columns are guessed (Title, Description, Tags, Attribute, Ignore) and you can change them |
| `.docx` | Lists and headings, or the largest table if the document is mostly a table |
| `.pdf` | Text-based PDFs (scanned images have no text to read) |
| `.rtf`, `.html`, `.json` | Converted to text or rows; a JSON IdeaTank backup restores directly |

Inside each idea it also picks up:

- **Title and description** from `Title: description`, `Title – description`, a **bold lead**, or a first line followed by more lines.
- **Tags** from `#hashtags`, a `Tags: a, b` line, or a tags/category column.
- **Attributes** from `Key: value` sub-lines such as `Effort: Medium` or `Owner: Dana`, and from extra spreadsheet columns.
- **Section headings**, which can become tags.

Ideas whose title is already in the index are flagged and unchecked in the preview.

## Working with the index

- Search across titles, descriptions, tags and attributes. Use `"exact phrases"` and `tag:name`. Press `/` to jump to search.
- Select tags in the side panel to filter. Choose whether ideas need **any** or **all** of the selected tags.
- Sort by newest, oldest, recently edited, title, tag, number of tags, or untagged first. Turn on **Group by tag** to see ideas under each tag.
- Add a tag to any idea with **+ Tag**, remove it with **×**, or select several ideas and tag, untag or delete them together.
- **Edit tags** lets you rename (renaming onto an existing tag merges them) or delete a tag everywhere.
- Every destructive action has **Undo**.

## Where data lives

Ideas are stored in your browser's local storage on this device. Use **Backup** to download a JSON backup or a CSV, and add the backup file with **Add ideas** to restore it elsewhere.

## Readability and legibility choices

| Choice | Basis |
|---|---|
| **Atkinson Hyperlegible Next** typeface (Mono for counts) | Designed by the Braille Institute for low-vision readers; easily confused glyphs (`I l 1`, `O 0`, `b d p q`) are deliberately differentiated |
| 18px base text, adjustable to 20 and 22px | Larger text improves reading for people with dyslexia (Rello, Pielot & Marcos, 2016) and keeps text above the critical print size for most readers (Legge & Bigelow, 2011) |
| 1.55 line height (1.8 option), lines ≤ 70 characters, left aligned, no justification, no all-caps labels | WCAG 2.2 SC 1.4.8 (Visual Presentation) and 1.4.12 (Text Spacing); line-length research (Dyson & Haselgrove, 2001) |
| Dark text on a light background by default | Positive polarity gives better legibility and proofreading accuracy (Piepenbrock et al., 2013); dark mode is still offered |
| Warm off-white `#F8F5EE` instead of pure white; warm near-black `#1F1D1A` instead of pure black | Reduces glare; warm, light-tinted backgrounds read better for people with dyslexia (Rello & Bigham, 2017; British Dyslexia Association style guide) |
| All text at **≥ 7:1 contrast** in both themes (body 15.4:1 light, 14.4:1 dark) | WCAG 2.2 SC 1.4.6 Contrast (Enhanced, AAA) |
| Dark mode uses dark gray `#1A1917` and off-white text, not pure black/white | Avoids halation for readers with astigmatism |
| Blue accent, no red/green pairs, selected tags shown with a ✓ and fill as well as color | WCAG SC 1.4.1 (Use of Color); safe for common color-vision deficiencies |
| Controls 36–44px tall, 3px focus outlines | WCAG SC 2.5.8 (Target Size) and 2.4.7 / 2.4.13 (Focus) |

## Libraries

Loaded from cdnjs only when you upload that file type: mammoth 1.6.0 (`.docx`), pdf.js 3.11.174 (`.pdf`), SheetJS 0.18.5 (spreadsheets). Everything else is plain HTML, CSS and JavaScript.
