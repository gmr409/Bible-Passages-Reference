# Bible Reference — Single Page HTML

A self-contained, interactive single-page HTML reference guide for Bible study, designed for academic, seminary, and classroom use. No server, no frameworks, no dependencies beyond a Google Fonts connection — open the file in any modern browser and it works.

---

## Features

- **Category navigation bar** — filter passages by thematic section with a single click
- **Two-column reading layout** — passage list on the left, full exegetical detail on the right
- **Sticky detail panel** — the detail column stays in view as you scroll the passage list
- **Dark theme** — warm dark palette optimized for extended reading and low-light environments
- **Accessible font sizing** — body text sized for comfortable reading without magnification
- **Responsive** — collapses to a single-column layout on narrow/mobile screens
- **Print-friendly** — a print stylesheet is included for clean hardcopy output
- **Fully self-contained** — all logic, data, and styles live in one `.html` file

---

## Usage

1. Download the `.html` file
2. Open it in any modern web browser (Chrome, Firefox, Safari, Edge)
3. Use the **category buttons** across the top to filter by section
4. Click any **passage card** in the left column to load the full detail in the right column
5. Select **All passages** to browse the complete index with section dividers

No installation, no internet connection required (fonts will fall back to Georgia if offline).

---

## Customization

All content is defined in a single JavaScript array near the bottom of the file. Each entry follows this structure:

```js
{
  id:       'unique_id',        // internal identifier, no spaces
  cat:      'category_key',     // matches a category button
  catLabel: 'Display Label',    // shown in the detail panel and as section dividers
  ref:      'Book Chapter:Verses',
  desc:     'One-line description shown in the passage list',
  body:     'Full exegetical or explanatory paragraph shown in the detail panel.',
  note:     'Optional scholarly note, source reference, or parallel passage citation.'
}
```

### Adding a new passage

Copy an existing entry in the `passages` array, assign a unique `id`, set the appropriate `cat` value, and fill in the content fields.

### Adding a new category

1. Add a new `<button>` to the `.cat-nav` section in the HTML, following the existing pattern:
   ```html
   <button class="cat-btn" onclick="selectCat(this,'your_key')">VI. Your Category</button>
   ```
2. Set the matching `cat` value on each passage entry that belongs to it.

### Changing the page title and subtitle

Edit the `<title>` tag in the `<head>` and the `<h1>` / `.subtitle` elements inside the `.masthead` div.

### Changing colors or fonts

All visual variables are defined in the `:root` block at the top of the `<style>` section. Key variables:

| Variable | Purpose |
|---|---|
| `--bg` | Page background |
| `--surface` | Passage card background |
| `--card` | Detail panel background |
| `--accent` | Headings, active states, highlights |
| `--text-primary` | Main body text |
| `--text-secondary` | Descriptions and secondary text |
| `--text-tertiary` | Labels, notes, footer |
| `--serif` | Primary serif font (headings, body) |
| `--serif2` | Secondary serif font (labels, notes) |

Fonts are loaded from Google Fonts. To change them, update the `<link>` tag in the `<head>` and the `--serif` / `--serif2` variables.

---

## File Structure

```
your-page.html        # The complete self-contained application
README.md             # This file
```

Because everything lives in a single HTML file, version control is straightforward — commit the `.html` file directly to track changes over time.

---

## Design Notes

- The layout uses a fixed-width left column (320px) and a fluid right column, with a maximum page width of 1100px
- The detail panel uses `position: sticky` so it remains visible while scrolling the passage list
- Category filtering and passage selection are handled entirely in vanilla JavaScript — no libraries or build tools required
- The print stylesheet hides the navigation controls and renders the detail panel for clean hardcopy

---

## Intended Use Cases

- Seminary course reference guides
- Bible study group handouts (digital and printed)
- Academic lecture supplements
- Personal devotional and study tools
- Topical concordance-style reference pages (prophecy, covenant, eschatology, etc.)

---

## Requirements

| Requirement | Details |
|---|---|
| Browser | Any modern browser (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+) |
| Internet | Optional — only needed to load Google Fonts |
| Server | None — open directly as a local file |
| Dependencies | None |

---

*Designed for readability, portability, and ease of maintenance.*
