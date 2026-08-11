Simple TV Torrent Watcher 2.0.7.2 fixes season movement and year-disambiguated matching without changing permissions or storage keys.

- Treats a saved season target as a starting season instead of a permanent season lock, so a show saved from season 4 can still find season 5.
- Fixes season-date checks so a dated new-season premiere, such as `S05E01`, is detected after the previous season is complete.
- Allows trusted EZTV API results fetched by IMDB id to match even when the release title omits the year from a year-disambiguated show.
- Keeps strict title matching for RSS/custom-feed rows, preserving exact matching for names such as `Daredevil Born Again`, `Scrubs 2026`, and `M.I.A`.
- Existing watchlists, settings, and saved episode markers remain in browser storage.
