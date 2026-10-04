# Version 2.0.72.0

Improves copied show-name parsing and keeps years and regional editions distinct.
Adds all-prior and future-only choices when adding shows. Release selection now
prefers quality first, then the smallest file at that quality; the old
uploader-first option remains available. Adds optional Pirate Bay search and page
buttons. Fixes episode-history tracking so failed or unchecked earlier episodes
are not skipped after a later send. Improves season transitions and date pauses.
Adds full watchlist backups. Existing watchlists and connection settings remain.

## New Permission Justification

**scripting:** Registers the extension's bundled toolbar on the official Pirate
Bay pages only when the user enables Pirate Bay in Settings and grants access.
No remote code is loaded or executed.

**Optional hosts:** apibay.org provides Pirate Bay title searches; thepiratebay.org
hosts the optional page toolbar. These sites are requested only when the user
enables this source. Existing user-entered WebUI/RSS permissions remain optional.

## Privacy Disclosure

When enabled, Pirate Bay searches send show-title search terms directly to API
Bay. As with TVMaze/EZTV/RSS requests, that service receives standard connection
information. No watchlist or credentials are sent to the developer. Credentials
are sent only to the user's configured torrent-client endpoint.
