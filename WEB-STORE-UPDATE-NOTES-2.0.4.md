# Chrome Web Store Update Notes - 2.0.4

## What changed

- Fixed pasted qBittorrent/EZTV filename parsing so release-group/uploader suffixes like `-MeGusta[eztvx.to]` are not saved as part of the show name.
- Fixed double-suffixed filenames like `Daredevil.Born.Again.S02E08.1080p.HEVC.x265-MeGusta[EZTVx.to].mkv[eztvx.to]`.
- Confirmed exact title matching still rejects loose matches such as `Daredevil Born Again` matching plain `Daredevil`, and `Scrubs 2026` matching plain `Scrubs`.
- Kept the 2.0.3 EZTV RSS fallback and RSS magnet parsing fixes.
- No new permissions were added.
- No storage keys changed; watchlists remain in `chrome.storage.local`.

## Suggested review note

Simple TV Torrent Watcher 2.0.4 is a bugfix update. It improves pasted torrent filename parsing so uploader/release group suffixes are not accidentally stored as part of the show name, while preserving exact title matching for titles such as Daredevil Born Again, Scrubs 2026, M.I.A, and High Potential. No new permissions were added. The extension stores watchlists/settings locally in chrome.storage.local and does not collect or transmit user data to the developer.
