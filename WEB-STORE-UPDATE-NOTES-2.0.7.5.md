Simple TV Torrent Watcher 2.0.7.5 fixes copied filename cleanup for shows saved with release tags still attached.

- Repairs saved names such as `Futurama MeGusta EZTV` back to `Futurama` during scan.
- Cleans trailing `MeGusta`, `TGx`, `EZTV`, and `EZTVx.to` tags when importing copied torrent names.
- Keeps exact new episode matches visible even when EZTV reports zero seeders.
- Keeps stricter title checks on EZTV API results so similarly named shows do not cross-match.
- Existing watchlists and settings remain in browser storage.
