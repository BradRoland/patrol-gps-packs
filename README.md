# Patrol GPS offline region packs

This repository hosts offline map region packs for the Patrol GPS app.
`manifest.json` lists the available regions; file URLs in it are relative to
this repository's raw base URL:

    https://raw.githubusercontent.com/BradRoland/patrol-gps-packs/main

Each region folder (e.g. `us-ca-merced/`) contains:

- `*.mbtiles` – vector map tiles
- `roads.sqlite` – road network data
- `addresses.sqlite` – address points

The files contain only public map and address data. No app code or personal data.

## Attribution

© OpenStreetMap contributors (ODbL); OpenFreeMap © OpenMapTiles, data from OpenStreetMap; Merced County GIS site address points, used with attribution.
