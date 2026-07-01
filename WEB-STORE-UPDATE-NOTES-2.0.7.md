Simple TV Torrent Watcher 2.0.7 is a reliability update for scan results, imports, and full-season watch entries.

- Keeps `S02E00` as a valid marker so whole-season entries can find `S02E01` and newer episodes correctly.
- Prevents older backup/import lines from moving a saved last-downloaded marker backward.
- Prevents automatic sends from moving a saved marker backward.
- Tries another EZTV API mirror when one mirror responds successfully but returns zero torrents.
- Merges built-in EZTV RSS mirrors instead of using only the first feed with rows.
- Preserves season-specific backup lines such as `FROM 1080p season 2 | S02E05`.
- Keeps strict title matching for names such as `Daredevil Born Again`, `Scrubs 2026`, and `M.I.A`.
- Does not change storage keys, so existing watchlists and settings remain in browser storage.
