# Repository Guidelines

## Project Structure & Module Organization
The app is a single-page static client. `index.html` hosts markup, CSS, and vanilla JS logic. `BeeTV.m3u` is a sample playlist for quick checks; keep additional fixture playlists in the repo root or `playlists/` if it grows. When adding assets (logos, icons), prefer an `assets/` folder and load them via relative URLs so the static server finds them without rewriting.

## Build, Test, and Development Commands
- `npx serve . --listen 4173` — serve the static files with live reload headers during development.
- `python -m http.server 4173` — lightweight fallback web server when Node is unavailable.
- `npm run format` (configure via Prettier once added) — run HTML/CSS/JS formatting before submitting.

## Coding Style & Naming Conventions
Use two-space indentation, trailing semicolons in JS, and descriptive `const` names (`channelList`, `state`). Prefer arrow functions for callbacks and keep DOM queries scoped (`document.getElementById`/`querySelector`). CSS sticks to BEM-like class names already present (`.panel`, `.channel`). When extracting scripts into modules, name files in kebab-case (`playlist-parser.js`) and export pure helpers.

## Testing Guidelines
Manual testing is expected: launch the static server, load `BeeTV.m3u`, confirm parsing, searching, and playback behaviors, and verify error messaging by pointing to an offline URL. Add regression playlists named `<feature>-sample.m3u` to capture edge cases (missing metadata, invalid URLs). Document observed browser console warnings inside the PR description.

## Commit & Pull Request Guidelines
The existing history (`added player`) shows short, imperative summaries. Follow the same style (`add drag-drop upload`, `refine channel list`). Each PR should include: motivation, screenshots or GIFs when UI changes, reproduction/testing notes, and links to any tracking issues. Keep diffs focused; open separate PRs for large refactors.

## Security & Configuration Tips
Never commit proprietary playlists; sanitize samples before sharing. The parser trusts user-provided metadata, so escape any injected text when adding new DOM hooks. When introducing remote dependencies, pin versions (similar to the current Hls.js CDN link) to avoid breaking changes.
