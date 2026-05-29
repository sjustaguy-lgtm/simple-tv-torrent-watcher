# Chrome Web Store Update Notes - 2.0.2

## What changed

- Fixed the EZTV toolbar Settings button so it opens the extension Settings screen from the extension background in a new extension tab.
- This avoids Brave blocking `chrome-extension://.../popup.html#settings` with `ERR_BLOCKED_BY_CLIENT` when the request starts from the EZTV page.
- Fixed optional WebUI/RSS permission handling so permission requests happen only from the user-triggered extension Settings flow.
- Removed the inline EZTV-page Settings form; the EZTV toolbar Settings button now opens the extension Settings screen.
- Added show-entry guide support for whole-season entries like `FROM S02E00` and quality hints like `FROM 1080p s03`.
- Added optional remote WebUI access for user-entered torrent client addresses.
- Added support for user-added RSS feeds.
- Kept built-in EZTV scanning and TVMaze title lookup.
- Kept local browser storage for watchlists, settings, and episode markers.

## Permission explanation

Version 2.0.2 uses `optional_host_permissions` for `http://*/*` and `https://*/*`.

These permissions are not used to read unrelated browsing activity. They are requested only after the user enters and saves a torrent client WebUI/RPC address or an RSS feed URL. The extension asks the browser for access to that user-provided address so it can:

- send selected magnet/torrent links to the user's own torrent client WebUI/RPC endpoint, or
- read the user's chosen RSS feed and compare release titles against the local watchlist.

The extension continues to use fixed host permissions for TVMaze, EZTV mirrors, localhost, and 127.0.0.1.

## Suggested review note

Simple TV Torrent Watcher 2.0.2 is a bugfix update. It fixes the EZTV-page Settings button by opening Settings from the extension background in a new extension tab, avoiding Brave client blocking of direct extension URLs from webpage context. It also keeps optional WebUI/RSS host access limited to user-entered addresses and user-triggered Settings actions. The extension does not collect browsing history, does not transmit user data to the developer, and stores watchlists/settings locally in `chrome.storage.local`.
