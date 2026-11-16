# Notehouse

A standalone, OneNote-style web app hosted on GitHub Pages. It does not connect to a Microsoft account or sync edits back to OneNote. Import a local OneNote export to bring its notes into this workspace.

## Use the app

Open [https://l2practice.github.io/note-text/](https://l2practice.github.io/note-text/) and choose **Import OneNote file**. The importer accepts `.onepkg`, `.one`, and `.onetoc2` files. In OneNote desktop, export a notebook as a OneNote Package (`.onepkg`) first, then select that file in the web app.

The OneNote parser runs in the browser. The selected notebook file is not uploaded to this repository or to a Notehouse server. The app loads its parser library from esm.sh when importing, so an internet connection is needed for that step. Conversion extracts readable note content into sections and pages; OneNote-specific layout, handwriting, embedded objects, and some formatting may not be preserved exactly.

## Storage and privacy

- Notes and edits are stored in this browser's IndexedDB, with local storage as a fallback. They are available on this browser and device only. Clearing this site's browser data can delete them.
- There is no Google Drive or Microsoft account sign-in in this standalone version.
- Gemini chat is optional. Add your own Gemini API key in **Settings**. The key stays in this browser; when you use chat, your prompt and current page text are sent to Google's Gemini API.
- Keep a separate backup of important notes. GitHub Pages hosts the app files, not each user's notes.

## Publish

This repository is configured for GitHub Pages from the `main` branch and repository root. The app is a static `index.html`; changes pushed to `main` are published by GitHub Pages.
