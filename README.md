# Simple TV Torrent Watcher

Simple TV Torrent Watcher is a local-first browser extension for Brave, Chrome,
Edge, Opera, Vivaldi, Arc, and other Chromium-based browsers. It adds a watchlist
and new-episode scanner to supported EZTV pages, can check user-added RSS feeds,
and can send selected magnet links to a supported torrent client WebUI or to the
local torrent app on the same computer.

Chrome Web Store:

https://chromewebstore.google.com/detail/kdmhdojmjaececadkhjgkcfalgjnfahi?utm_source=item-share-cb

Project page:

https://sjustaguy-lgtm.github.io/simple-tv-torrent-watcher/

Privacy policy:

https://sjustaguy-lgtm.github.io/simple-tv-torrent-watcher/privacy-policy.html

## What It Does

- Adds buttons on supported EZTV pages:
  - **Scan for New Episodes**
  - **Watchlist**
  - **Add Show to Watchlist**
  - **Settings**
- Keeps a show watchlist in browser storage.
- Imports and exports backup lines like `M.I.A | S01E09`.
- Imports qBittorrent-style filenames like `Show.Name.S02E06.1080p`.
- Supports season requests like `FROM s02`, `FROM S02E00`, and `FROM season 2`.
- Uses `S02E00` as a whole-season marker, so episode 1 and newer in that season
  can be found without scanning every older season.
- Keeps quality words such as `1080p` as that show's first quality choice.
- Uses TVMaze to help resolve show names.
- Checks EZTV through its public API.
- Checks optional user-added RSS feeds that include torrent links or magnet links.
- Sends selected magnets to supported WebUI/RPC clients, or opens magnet links
  through the local torrent app.

## Supported Torrent Clients

Direct WebUI/RPC support is included for:

- qBittorrent
- Transmission
- Deluge
- uTorrent
- BitTorrent
- aria2

You can also use **Same computer torrent app** mode if you want the browser to
open magnet links locally.

## Best Ways To Add A Show

Paste into **Add Show to Watchlist** or the bulk import box. The scanner ignores
codec words such as `HEVC` and `x265` when figuring out the show name. Quality
words such as `1080p` and `720p` are kept as that show's first quality choice.

| What you type | What it does |
| --- | --- |
| `FROM` | Adds the show and tracks it from now on. |
| `FROM s02` | Adds season 2 and starts from `S02E00`, so episode 1 and newer in season 2 can be found. |
| `FROM S02E00` | Same as above; useful when you want the whole season. |
| `FROM s02e05` | Adds the show with `S02E05` marked as already handled, so scans look for newer season 2 episodes. |
| `FROM 2x05` | Same as `S02E05` using the alternate episode format. |
| `FROM season 2` | Same as `s02`; adds the whole season starting from `S02E00`. |
| `FROM season 2 episode 5` | Same as `S02E05`. |
| `FROM 1080p s03` | Adds season 3 starting from `S03E00` and prefers `1080p` first. |
| `M.I.A | S01E09` | Import/export format; saves `M.I.A` with `S01E09` as the last episode already handled. |

Tip: use `S02E00` when you want the whole season, because it means "I have
nothing from season 2 yet." Use `S02E05` when you already have episode 5 and only
want newer episodes.

## Privacy

The extension is local-first. Watchlists, settings, custom RSS feed addresses,
and torrent-client connection settings are stored in your browser profile using
`chrome.storage.local`.

The developer does not collect, receive, sell, or store your watchlist, browsing
history, torrent-client settings, credentials, IP address, or analytics.

The extension only makes network requests needed for features you choose to use,
such as supported EZTV pages, TVMaze, custom RSS feeds you add, or your own
torrent client WebUI.

## Public Pages

- `index.html` is the public project page.
- `privacy-policy.html` is the public privacy policy.
- The installable extension is distributed through the Chrome Web Store link
  above.

## Legal Note

This project is only a browser extension for managing a local TV watchlist and
opening or sending magnet links selected by the user. Use it only where legal in
your country.
