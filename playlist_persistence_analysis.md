# Playlist Persistence Analysis

Goal: automatically restore the last playlist when the viewer reopen the page. The app currently depends on the user uploading an M3U file via `<input type="file">`, so no playlist reference survives page reloads.

## Browser Security Limits
- Browsers never remember the exact file that was picked through a file input for privacy reasons. After a refresh you cannot programmatically re-use the previous `File` handle.
- Without explicit storage, only derived data we stash (e.g., channel list JSON) can be restored—not the actual disk file path.

## Feasible Approaches
1. **Serialize playlist text into storage**: After parsing, store the raw M3U string or the parsed array in `localStorage`/IndexedDB. On load, check storage and hydrate state without any user action. Works offline, but storage quotas (~5–10 MB) mean large playlists may exceed limits and storing full text exposes channel URLs in the browser profile.
2. **Use the File System Access API**: In Chromium browsers, `window.showOpenFilePicker` returns a persistent file handle if the user grants permission. You can store that handle via `handle.requestPermission()`, then call `handle.getFile()` on the next visit. Not supported on Safari/Firefox, so you’d need progressive enhancement.
3. **Generate downloadable cache**: After upload, offer “Save session” that produces a JSON file of parsed channels. On return, user re-uploads the JSON (faster than sourcing remote playlist) but still involves one interaction.

## Recommendations
- Implement localStorage caching of parsed channel metadata plus a flag indicating the original filename/date; fall back gracefully if storage fails.
- Optionally add File System Access API support for Chromium to re-open the original playlist seamlessly, while still providing standard upload for other browsers.
- Clearly surface privacy messaging (cached playlist is stored locally and can be cleared via a “Forget playlist” button).
