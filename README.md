# IPTV Playlist Viewer

A minimalist static client that lets you upload any M3U or M3U8 playlist, browse channel metadata, and stream HLS sources directly in the browser. Everything lives in a single HTML file, so deployment is as simple as serving static assets.

## Project Structure
- `index.html` – UI markup, dark-theme styles, and the vanilla JS playlist parser/player.
- `BeeTV.m3u` – reference playlist for local testing; keep additional fixtures next to it.
- `AGENTS.md` – contributor guide outlining coding style, testing expectations, and PR conventions.

## Quick Start
1. Clone or download this repository.
2. Start a static server from the repo root, e.g. `npx serve . --listen 4173` or `python -m http.server 4173`.
3. Open `http://localhost:4173` in a modern browser.
4. Click **Choose playlist**, load `BeeTV.m3u` (or your own), then select a channel to begin playback.

## Development Workflow
- Use two-space indentation and keep JS in modules or sections with descriptive `const` names; run your formatter (`npm run format` once configured) before committing.
- Manual verification is key: exercise search, selection, playback success, and failure paths (try an offline URL to confirm errors).
- Keep sample playlists anonymized; avoid committing proprietary streams.
- Read `AGENTS.md` for deeper contributor expectations.

## Testing & Troubleshooting
- Browser console warnings should be documented in PRs, especially Hls.js fatal errors.
- If a stream stalls, use the **Clear** button to reset filters, re-select the channel, or reload the playlist.
- When adding new metadata fields, sanitize user-provided text before injecting into the DOM.

## Roadmap & Contributions
Planned improvements include drag-and-drop uploads, persistent playlist history, and stronger validation. Issues and PRs are welcome—please describe motivation, attach screenshots for UI tweaks, and keep changes scoped so reviewers can test quickly.
