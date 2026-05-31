# Chrome Web Store Update Notes - 2.0.3

## What changed

- Added built-in EZTV RSS fallback alongside the EZTV JSON API. This fixes cases where a new episode is already visible in EZTV RSS but the JSON API has not caught up yet.
- Fixed RSS parsing for `<torrent:magnetURI>` so EZTV RSS and compatible feeds send the actual magnet link, not the episode webpage URL.
- Kept the 2.0.2 Settings-button fix: the EZTV toolbar Settings button opens the extension Settings screen from the extension background in a new extension tab.
- Kept local browser storage for watchlists, settings, and episode markers.
- No new permissions were added.

## Why this matters

A show like `FROM S04E05` should find `FROM S04E06 The Heart Is A Lonely Hunter 720p HEVC x265-MeGusta [eztv]` when the episode is available. EZTV can publish that episode in RSS before it appears in the JSON API, so 2.0.3 checks the built-in EZTV RSS feed too.

## Suggested review note

Simple TV Torrent Watcher 2.0.3 is a bugfix update. It adds built-in EZTV RSS fallback for cases where the EZTV JSON API lags behind the RSS feed, and fixes RSS magnet parsing for torrent:magnetURI entries. No new permissions were added. The extension stores watchlists/settings locally in chrome.storage.local and does not collect or transmit user data to the developer.
