# Notehouse

A personal OneNote-style web app. It imports notebook, section, and page content from Microsoft OneNote, then keeps the imported notes in this browser's IndexedDB. Edits stay local and are not written back to OneNote. No notebook content or API keys are included in this repository.

## Run on GitHub Pages

1. In this repository, open **Settings → Pages**.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Select branch **main** and folder **/(root)**, then save.
4. Open `https://l2practice.github.io/note-text/` after GitHub Pages finishes publishing.

## Enable OneNote import

1. Open the Microsoft Entra admin center and register a single-page application. Select the account type that includes your Microsoft account.
2. Under **Authentication → Add a platform → Single-page application**, add this exact redirect URI: `https://l2practice.github.io/note-text/`.
3. Under **API permissions**, add **Microsoft Graph → Delegated permissions → Notes.Read**. The app only requests read access.
4. Copy **Application (client) ID** from the app registration overview.
5. In Notehouse, open **Settings**, paste the client ID, save, then choose **Import from OneNote** and sign in.

Microsoft's `Notes.Read` delegated permission lets the signed-in user authorize reading OneNote notebooks. Work or school accounts may be subject to their organization's consent policy.

## Data and privacy

- Imported notes and edits are stored in this browser on this device. Clearing browser site data removes them.
- The Microsoft client ID and optional Gemini key are saved in browser local storage; no client secret belongs in this public repository.
- If Gemini is enabled, prompts and the current page text are sent to the Gemini API using the key you provide.
- Microsoft Graph is used to read notebooks directly after you sign in. This app does not send notebook data to a Notehouse server.

## Limits

- This is a static, single-user app, not a multi-user service.
- Some OneNote-specific objects or formatting may not render exactly like OneNote.
- The app does not sync edits back to OneNote and does not generate `.onepkg` files.
