# Asian Family Tree

A read-only viewer for the Columbia Mentoring Initiative mentorship lineage. Visitors can browse the tree, step through years, and click people to see their journey. They cannot upload, paste, or edit data from the page itself, the data only ever comes from `data.csv` in this repository.

## Files

- **`index.html`** — the whole app. This is the page people will open.
- **`data.csv`** — your mentorship log. Not included here, add your own (same format you've been using: `Year,Person,Uni,Role,Mentor,Notes`, plus any extra columns like Tags, School, etc.).

## Setup

1. Put your `data.csv` in the same folder as `index.html` (repo root, or whichever folder you publish from).
2. Commit and push both files.
3. Turn on GitHub Pages for this repo: **Settings → Pages → Source → Deploy from a branch**, pick `main` and the root folder (or `/docs` if that's where these files live).
4. GitHub gives you a link like `https://lovek-patel.github.io/CMI_Asian_Family_Tree/`. That's the link to share.

## Updating the tree each year

Edit `data.csv` (in GitHub's web editor, or locally and push), commit, and the published page updates automatically within a minute or two. Nothing else needs to change.

## A note on viewing locally

Opening `index.html` directly by double-clicking it won't load the data, browsers block a page from reading a local file like that. To preview locally before pushing, run a tiny local server from the folder, for example:

```
python3 -m http.server 8000
```

then open `http://localhost:8000` in a browser. GitHub Pages serves files the same way, so the published link will work fine even though double-clicking the file won't.

## What this version does and doesn't do

- **Does:** year slider, step through years, play the whole timeline, tap anyone to open their card and follow their journey, switch between one-year and all-years views, read-only Tags and extra columns if your CSV has them.
- **Doesn't:** no file upload, no pasting CSV, no editing from the page. The only way to change what people see is to edit `data.csv` and push.
