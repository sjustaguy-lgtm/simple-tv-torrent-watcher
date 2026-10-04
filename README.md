# Simple TV Torrent Watcher 2.0.72.0

A browser extension for Brave, Chrome, Edge, Arc, Opera and Vivaldi. No desktop
helper, Python installation or separate server is required.

## What Changed

- One title parser for the popup, page toolbar and imports.
- Copied episode titles no longer become part of the show name.
- Years and regional editions stay distinct. Punctuation and letter case do not
  affect matching, including `M.I.A`, `M I A` and `MIA`.
- Adding a show offers **Only new / future episodes** or **Add all prior episodes too**.
- Quality is chosen before file size. At the same quality, the smaller known file wins.
- Optional Pirate Bay search, page buttons and per-release Add buttons.
- Failed or unchecked older episodes remain available after a later episode is sent.
- New-season transitions remain enabled; season requests set a starting season.
- Season-date checks keep currently airing shows and unhandled aired episodes active.
- Full watchlist backups preserve individual episode history without client credentials.
- Existing watchlists and connection settings use the same browser storage keys.

## Add A Show

The default option is **Only new / future episodes**:

| What you paste | Starting point |
| --- | --- |
| `FROM` | Episodes from the time you add the show onward. |
| `FROM S04E05` | Episode 5 is already handled; look for episode 6 and later seasons. |
| `FROM 4x05` | Same as `S04E05`. |
| `FROM season 4 episode 5` | Same as `S04E05`. |
| `FROM S04E00` | Start with episode 1 of season 4, then continue into later seasons. |
| `FROM s04` or `FROM season 4` | Same starting point as `S04E00`. |
| `FROM 1080p s04` | Start at season 4 and prefer 1080p. |
| `M.I.A \| S01E09` | Backup format: episode 9 is already handled. |
| `FROM S04E06 The Heart Is A Lonely Hunter 720p HEVC x265-MeGusta [eztv]` | Save FROM, episode 6 already handled, with 720p preferred. |
| `Boston.Blue.S01E19.1080p.HEVC.x265-MeGusta[eztvx.to]` | Save Boston Blue, episode 19 already handled, with 1080p preferred. |
| `Scrubs.2026.S01E09.1080p.WEB.x265-MeGusta` | Save Scrubs 2026 separately from the original Scrubs. |

A pasted episode number always means **you already have that episode**, unless
you explicitly select **Add all prior episodes too**. Choosing all prior
episodes clears that starting marker and includes available older episodes.
If you also specify a season, older episodes begin at that season.

For a name without an episode marker, the future-only option uses TVMaze's
aired-episode dates at the time you added the show. When metadata is unavailable,
existing releases provide a starting point. Supplying an episode marker is the
most precise choice when you already have some episodes.

Scans show results for review. **Send Selected** sends the checked releases;
**I Already Have Selected** records those individual episodes without sending them.
The last-episode display advances, but failed or unchecked results are retained.

## Quality And File Size

Settings offers three choices:

| Release selection | Priority |
| --- | --- |
| Preferred quality, then smallest file | Your quality order, then file size, then seeder/uploader tie-breakers. |
| Highest resolution, then smallest file | 2160p, 1080p, 720p, 480p; smaller files break ties at the same resolution. |
| Preferred uploader, then quality | The older uploader-first behavior. |

The default quality order is **1080p, 720p**. A quality in a pasted filename
becomes that show's first choice, including when Highest resolution is selected.

Example: **1080p EDITH at 1 GB** versus **1080p MeGusta at 450 MB** selects
MeGusta in either size-aware mode. An available 1080p release still beats a
smaller 720p release when 1080p is first in your quality order.

File sizes come from the release source. Missing sizes are shown as unknown,
never treated as zero. Preferred minimum seeders is a tie-breaker; it does not
hide exact episodes with zero reported seeders.

## Pirate Bay

1. Open the extension's **Settings**.
2. Enable **Search Pirate Bay too** and click **Save**.
3. Approve access to `apibay.org` and `thepiratebay.org`.
4. Reload any open Pirate Bay tabs.

The watchlist scanner searches Pirate Bay as well as EZTV and configured RSS feeds.
The same title, episode and quality checks apply to all sources. The toolbar
also works on Pirate Bay pages, and episode search rows have a **+** Add button.

Support covers the official `thepiratebay.org` domain, including its HTTP pages.
Arbitrary mirrors are not automatically trusted. Only TV-category, individual
episode releases are included; season-pack torrents are not expanded into
episodes. Source availability and search caps can limit older results. Search
warnings are displayed instead of silently claiming the source succeeded.

## Import And Export

Open **Add** / **Add Show to Watchlist**, then expand **Import / export watchlist**.

- **Copy export** produces familiar lines such as `M.I.A | S01E09`.
- Paste names, copied filenames or export lines into the import box, then click Import.
- **Copy full backup** produces JSON with starting points, episode history and
  future-only/all-prior choices. Paste it into the same import box to restore.
- Full backups exclude torrent-client settings, passwords and credentials.
- Simple text lines treat the saved marker as all earlier episodes already
  handled. Use the full backup to preserve gaps and individual send history.

## Torrent Clients

Direct WebUI/RPC sending supports qBittorrent, Transmission, Deluge, uTorrent,
BitTorrent and aria2. Same-computer mode opens magnets in your registered app.

| Client | Common local address |
| --- | --- |
| qBittorrent | `http://localhost:8080` |
| Transmission | `http://localhost:9091` |
| Deluge | `http://localhost:8112` |
| uTorrent / BitTorrent | `http://localhost:8080` |
| aria2 | `http://localhost:6800/jsonrpc` |

For another computer, enter its WebUI IP address instead of localhost.
Enable the client's WebUI, enter credentials in the extension's Settings,
click Save, approve that host's permission prompt, then click Test Client.

Extra RSS feeds can be entered as `My Feed | https://example.com/rss.xml`,
one per line. Each address requires your approval. Feeds need episode titles
and magnet/torrent links; enclosure sizes enable file-size comparisons.

Auto-check is disabled by default. If enabled at 15 minutes or more, it scans
and sends pending episodes automatically using your saved delivery mode.

## Install Or Update

For a normal installation, use the published Chrome Web Store listing:
https://chromewebstore.google.com/detail/kdmhdojmjaececadkhjgkcfalgjnfahi

For a local unpacked copy:

1. Extract the sharing ZIP to a permanent folder.
2. Open your browser's Extensions page and enable Developer mode.
3. Click Load unpacked and select the folder containing `manifest.json`.
4. Keep the folder in that location.

Use `brave://extensions` in Brave, `chrome://extensions` in Chrome/Arc,
`edge://extensions` in Edge, `opera://extensions` in Opera, or
`vivaldi://extensions` in Vivaldi.

To update an existing unpacked installation, replace its files in the same
folder, click its Reload button, and refresh open EZTV/Pirate Bay tabs.
**Do not remove and reinstall the extension** to apply this update.
This update does not clear browser storage. Store and unpacked installations
have separate extension identities and therefore separate watchlists.

This package targets Chromium browsers. It is not a signed Firefox or Safari
extension. A ZIP is an upload/sharing package, not a bypass for browser-store
installation requirements.

## Permission Notes

`storage` keeps settings and episode history locally. `alarms` supports
optional automatic scans. `activeTab` reads the current supported page after
you open the popup. `declarativeNetRequest` supports qBittorrent WebUI request
headers. `scripting` registers the bundled page toolbar on Pirate Bay only
after you enable that source and grant its optional host access.

Existing required hosts are TVMaze, EZTV and loopback addresses. Pirate Bay,
user-entered WebUI addresses and RSS sources use optional site permissions.
No remote executable code, analytics or client credentials are bundled.
