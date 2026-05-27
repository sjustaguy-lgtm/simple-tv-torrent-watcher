# Simple TV Torrent Watcher

Privacy policy page for the Simple TV Torrent Watcher Chrome Web Store listing.

Simple TV Torrent Watcher is a Chrome/Brave browser extension that keeps a local TV watchlist, checks supported EZTV sources and user-configured RSS feeds, and can send user-selected magnet/torrent links to a user-configured torrent client WebUI/RPC endpoint.

## Best Ways To Add A Show

Paste into **Add Show to Watchlist** or the bulk import box. The scanner ignores codec words such as `HEVC` and `x265` when figuring out the show name. Quality words such as `1080p` and `720p` are kept as that show's first quality choice.

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
| `FROM S02E00` | Adds `FROM` season 2 from the beginning without scanning every older season. |
| `M.I.A | S01E09` | Import/export format; saves `M.I.A` with `S01E09` as the last episode already handled. |

Tip: use `S02E00` when you want the whole season, because it means "I have nothing from season 2 yet." Use `S02E05` when you already have episode 5 and only want newer episodes.

## Privacy Policy

The privacy policy is available in this repository as:

- `index.html`
- `privacy-policy.html`

After GitHub Pages is enabled, the public privacy policy URL should be:

`https://sjustaguy-lgtm.github.io/simple-tv-torrent-watcher/`

## Chrome Web Store

Version 1.8.2 is published. Version 2.0.0 has been submitted as an update with optional host permissions for user-entered WebUI/RPC addresses and custom RSS feed URLs.

The Chrome Web Store extension zip, icons, and screenshots are stored locally on the developer machine in the project `share-package` folder, not in this public repository.
