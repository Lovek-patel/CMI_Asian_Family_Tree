# Asian Family Tree

Columbia Mentoring Initiative mentorship lineage, as two separate tools:

- **`index.html`** — the public page. Anyone with the link can browse the tree, step through years, and click people to see their journey. Nothing on this page can be edited, and it defaults to showing every year at once (click **This year** to narrow to one class).
- **`editor.html`** — the chairs-only tool. Load your log, click anyone to add tags or a photo, then export an updated CSV to commit. **Don't link this one publicly**, just use it yourself and push the file it produces.

Neither file has any data baked in. Both read from a CSV you provide.

## Files in this repo

| File | Who it's for | Notes |
|---|---|---|
| `index.html` | Everyone | The link you share |
| `editor.html` | Chairs | Keep this out of anything you hand out, or just don't link to it |
| `manifest.json` | — | Tells `index.html` which CSV file is current |
| `data_2023_2026.csv` (your file) | — | Your actual log, not included here, you already have it |

## Setup

1. Put your data file (for example `data_2023_2026.csv`) in the same folder as `index.html`.
2. Open `manifest.json` and make sure `dataFile` matches that file's exact name:
   ```json
   { "dataFile": "data_2023_2026.csv" }
   ```
3. Commit and push everything.
4. Turn on GitHub Pages: **Settings → Pages → Source → Deploy from a branch**, pick `main` and the folder these files live in.
5. Share the resulting link, something like `https://lovek-patel.github.io/CMI_Asian_Family_Tree/`. That link opens `index.html` by default.

## Updating the tree each year

The data file's name can change year to year (`data_2023_2026.csv` this year, maybe `data_2023_2027.csv` next year), the app doesn't care what it's called. When you add a new year or rename the file:

1. Update the CSV.
2. If you renamed the file, update `manifest.json` to point at the new name.
3. Commit and push. The published page picks it up automatically, no code changes needed.

## Adding tags and photos

This is the one thing that happens in `editor.html`, not on the public page:

1. Open `editor.html` locally (see "viewing locally" below) and load your current data file (upload or paste).
2. Tap anyone, add tags, and/or paste a photo URL or a relative path like `photos/jane.jpg` (if you commit the photo itself into a `photos/` folder in the repo).
3. Click **Export CSV (with tags & photos)**. This downloads your log with `Tags` and `Photo` columns added or updated, everything else in the file is left exactly as it was.
4. Replace your data file with the exported one, commit, and push. The public page will now show those tags and that photo for that person, read-only.

People with no tags or photo look exactly as clean as everyone else, there's no empty placeholder, just their initials as an avatar.

## Viewing locally before you push

Opening either HTML file by double-clicking it won't load any data, browsers block a page from reading local files that way. Run a tiny local server from the folder instead:

```
python3 -m http.server 8000
```

then open `http://localhost:8000` (for the public page) or `http://localhost:8000/editor.html` (for the editor). GitHub Pages serves files the same way, so the published link works fine even though double-clicking the file doesn't.

## What each page does and doesn't do

**`index.html` (public)**
- Does: year slider, step through years, Play years, tap anyone to open their card and follow their journey, switch between This year and All years (All years is the default), read-only tags and photo if the data has them.
- Doesn't: no upload, no paste, no download, no way to add or change anything.

**`editor.html` (chairs)**
- Does: everything the public page does, plus upload/paste a CSV, add tags and a photo per person, and export a merged CSV.
- Edits you make here stay in your own browser until you click Export, nothing is shared or published until you commit the exported file.
