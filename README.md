# Notehouse

A standalone, OneNote-style web app hosted on GitHub Pages. It does not connect to a Microsoft account or sync edits back to OneNote. Import a local OneNote export to bring its notes into this workspace.

## Use the app

Open [https://l2practice.github.io/note-text/](https://l2practice.github.io/note-text/) and choose **Import Markdown/ZIP** to load a Markdown folder or ZIP exported by OneNote Md Exporter. Notebook folders become notebooks, section folders become sections, Markdown files become pages, and locally referenced images and attachments are stored with the page so they remain available offline and in Drive sync. You can also choose **Import OneNote** for `.onepkg`, `.one`, and `.onetoc2` files.

The importers run in the browser. Selected files are not uploaded to this repository or to a Notehouse server. Importing Markdown ZIPs loads JSZip, Marked and DOMPurify from esm.sh, so an internet connection is needed for that step. Images and linked attachments are embedded in imported page data. The direct OneNote parser extracts readable note content into sections and pages; OneNote-specific layout, handwriting, embedded objects, and some formatting may not be preserved exactly.

The menu bar groups document, edit, view, insert, formatting, tools, Gemini, window, and help commands. The NotePro SVG icon pack is embedded in `index.html`, so the icons do not require separate asset hosting. Browser-controlled actions such as minimizing or arranging windows use the browser/operating-system window controls.

## Google Drive sync

Notehouse stores its own `Notehouse/notehouse-notebooks.json` file in each signed-in user's Google Drive. It uses the same OAuth client ID and `nt-worker` Apps Script token-keeper settings as `/notes` on this domain, so an existing **Always-on connection** there is reused automatically. Both apps run under `https://l2practice.github.io`, which lets them share this browser's connection settings. The notebook contents are separate from Notes' PDF library.

When the token keeper is configured and linked, Notehouse requests a fresh short-lived Drive access token in the background and checks Drive for changes about once a minute. Without the token keeper, direct Google sign-in works for the current OAuth access-token period. For automatic renewal beyond an hour, configure the Notes app's **Settings → Always-on connection** once. In Notehouse, the token keeper URL and private key can also be entered under **Settings → Always-on connection settings**. Each person should use their own Apps Script token keeper and Google account; the refresh token stays in that person's Apps Script properties, not in this app or repository. The setup guide and Apps Script source are linked from the app settings.

Notes are also cached in this browser for offline use. Drive sync is per Google account; opening the app on another device with the same connected account loads the same notebook file. Gemini chat is optional. Add your own Gemini API key in **Settings**; the key stays in this browser, while prompts and current page text are sent to Google's Gemini API when used.

Audio transcription also uses the saved Gemini key and sends the selected audio clip or microphone recording to Google's Gemini API. Dictation uses the browser's speech recognition support when available.

## Publish

This repository is configured for GitHub Pages from the `main` branch and repository root. The app is a static `index.html`; changes pushed to `main` are published by GitHub Pages.
