# Simple TV Torrent Watcher Add-on 2.0.7

Simple TV Torrent Watcher 2.0.7 is a local-first browser extension for Brave, Chrome,
Edge, Opera, Vivaldi, Arc, and other Chromium-based browsers. It adds a watchlist
and new-episode scanner to supported EZTV pages, can check user-added RSS feeds,
and can send selected magnet links to a supported torrent client WebUI or to the
local torrent app on the same computer.

## What it can do

- Keep a show watchlist in browser storage.
- Add visible buttons directly on EZTV pages:
  - **Scan for New Episodes**
  - **Watchlist**
  - **Add Show to Watchlist**
  - **Settings** opens the extension Settings screen in a new extension tab.
- Import/export backup lines like `M.I.A | S01E09`.
- Import qBittorrent-style filenames like `Show.Name.S02E06.1080p`.
- Add season targets like `The Boys season 4` or `The Boys s4`.
- Add whole-season requests like `FROM S02E00`.
- Check EZTV through its JSON API and built-in EZTV RSS fallback when the API lags.
- Check extra user-added RSS feeds that include torrent links or magnet links.
- Resolve show names through TVMaze.
- Reuse shared RSS/feed data during a scan so larger watchlists do not re-download the same feeds for every show.
- Send magnets to supported WebUI/RPC clients on this or another computer.
- Or open magnet links through the same-computer torrent app.
- Pre-fill show info when opened on an EZTV show page.

## What changed in 2.0.7

- Keeps `S02E00` as a real episode marker so whole-season entries work reliably.
- Prevents imports and automatic sends from moving a saved `last downloaded` marker backward.
- Tries another EZTV API mirror when one mirror responds with zero torrents.
- Merges built-in EZTV RSS mirrors instead of stopping at the first feed with rows.
- Preserves season-specific export/import entries, for example `FROM 1080p season 2 | S02E05`.
- Keeps exact title matching behavior for names like `Daredevil Born Again`, `Scrubs 2026`, and `M.I.A`.
- Keeps the same permissions and storage keys, so existing watchlists and settings stay in browser storage.

## What it cannot do without a native helper

- Scan local drives like `M:\`.
- Silently control arbitrary desktop torrent-adder programs.
- Write files to arbitrary folders.

Those are browser security limits, not project limits.

## Best Ways To Add A Show

Paste into **Add Show to Watchlist** or the bulk import box. The scanner ignores
codec words such as `HEVC` and `x265` when figuring out the show name. Quality
words such as `1080p` and `720p` are kept as that show's first quality choice.
Uploader/release group suffixes such as `-MeGusta[eztvx.to]` are removed from the saved show name.

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

Tip: use `S02E00` when you want the whole season, because it means "I have
nothing from season 2 yet." Use `S02E05` when you already have episode 5 and only
want newer episodes.

## Load It

### Arc / Brave / Chrome / Edge / Opera / Vivaldi

1. Open `chrome://extensions`.
2. Turn on **Developer mode**.
3. Click **Load unpacked**.
4. Select this `ARC_BRAVE_CHROME_EDGE_OPERA_VIVALDI_LOAD_UNPACKED` folder.

After replacing files in this folder, go back to `chrome://extensions`, click the
extension's reload button, then refresh any open EZTV tabs.

For Brave, keep this unpacked folder in a permanent location and load this same
folder each time. The extension ID is pinned so saved browser storage, including
the watchlist, survives browser restarts when the same folder stays in place.

Important: Brave/Chrome treat manually loaded add-ons as developer extensions.
For a truly normal permanent install, the extension must be signed through a
browser store or installed by browser policy.

## Public Pages

- `index.html` is the public project page.
- `privacy-policy.html` is the public privacy policy.
- The installable extension is distributed through the Chrome Web Store link above.

### Firefox

1. Open `about:debugging#/runtime/this-firefox`.
2. Click **Load Temporary Add-on**.
3. Pick `manifest.json` inside this folder.

## Torrent Client Setup

Open **Settings** and choose:

- **WebUI / direct connection** when you want the extension to send straight to a torrent client.
- **Same computer torrent app** when you want the browser to open magnet links locally.

Direct WebUI/RPC support is included for:

- qBittorrent
- Transmission
- Deluge
- uTorrent
- BitTorrent
- aria2

Common host defaults:

- qBittorrent: `http://localhost:8080`
- Transmission: `http://localhost:9091`
- Deluge: `http://localhost:8112`
- uTorrent / BitTorrent: `http://localhost:8080`
- aria2: `http://localhost:6800/jsonrpc`

For qBittorrent:

1. Open **Tools -> Options -> Web UI**.
2. Enable the Web UI.
3. Set the username and password.
4. If the add-on is on a different computer, allow that computer on your LAN/firewall.

Then open the extension popup **Settings**, choose qBittorrent, enter the host,
username, password, and click **Test Client**. If you are on an EZTV page, the
toolbar **Settings** button opens this same Settings screen in a new extension tab.

If qBittorrent refuses the add-on even with the right password, check Web UI security
settings. Some qBittorrent setups block browser-extension requests with CSRF protection.
For a trusted home LAN setup, either allow local/LAN clients in qBittorrent Web UI
settings or use the add-on's **Same computer torrent app** mode instead.

## Extra RSS Feeds

Open **Settings** and paste one RSS feed per line in **Extra RSS feeds**.

Use this format when you want a label:

```text
My Feed Name | https://example.com/rss.xml
```

Or paste only the feed URL:

```text
https://example.com/rss.xml
```

The extension will ask permission for each feed address you add. Custom RSS feeds
must include normal episode filenames such as `Show.Name.S02E06.1080p` and either
a magnet link or torrent link.

## Current Web Store Package

- `webstore/chrome-web-store-upload-2.0.7.zip`

## Chrome Web Store 2.0.7 Permission Notes

Version 2.0.7 uses optional host permissions for user-entered WebUI and RSS addresses.
That means the extension does not need full network access at install time. When a
user saves a remote qBittorrent/Transmission/Deluge/uTorrent/BitTorrent/aria2 host,
or adds a custom RSS feed, the browser asks permission only for that exact address.
