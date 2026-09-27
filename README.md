# Patrol GPS offline region packs

This repository hosts offline map region packs for the Patrol GPS app.
`manifest.json` lists the available regions; file URLs in it are relative to
this repository's raw base URL:

    https://raw.githubusercontent.com/BradRoland/patrol-gps-packs/main

Each region folder (e.g. `us-ca-merced/`) contains:

- `*.mbtiles` – vector map tiles
- `roads.sqlite` – road network data
- `addresses.sqlite` – address points
- `places.sqlite` – named park polygons for the "In {park}" line

The files contain only public map and address data. No app code or personal data.

## Attribution

© OpenStreetMap contributors (ODbL); OpenFreeMap © OpenMapTiles, data from OpenStreetMap; Merced County GIS site address points, used with attribution.

## Merced County, version 3

`us-ca-merced` is manifest version 3. The base tiles and OSM roads are the Geofabrik California extract `california-260925.osm.pbf` (last modified 2026-09-25) and OpenFreeMap planet `20260913_164504_pt` (TileJSON last modified 2026-09-14). Streets missing from that extract were added from Merced County GIS road centerlines, with US Census TIGER/Line 2024 as a fallback. Building footprints that do not overlap OpenStreetMap buildings were added from Overture Maps 2026-09-23.1.

Version 3 adds names for streets east of Overland Avenue and Place Road in Los Banos (intersection about 37.07331, -120.82629). OpenStreetMap already draws those ways, including the live map of 2026-09-26, but without names. The names are the county centerline `fullrdname` values. The label follows the centerline and does not draw a second road. No name was invented, and no line was derived from address points or parcels.

TIGER/Line 2025 (`tl_2025_06047_roads`, shapefile dated 2025-09-13) is published and does not contain those streets. TIGER/Line 2026 is not published. Overture transportation 2026-09-23.1, the newest release on 2026-09-26, does not name them either. Overture buildings for that release do not cover the new houses (4 of 274 addresses on those streets are within 30 m of a footprint). No footprints were invented.

County site-address points were rechecked on 2026-09-26. The service still has 104,075 points. Nothing was created or edited after 2026-06-18. The address database is unchanged from version 2. Zero new addresses were added in the Overland / Place box or countywide.

| Source | Used for | License / terms |
| --- | --- | --- |
| OpenStreetMap, via Geofabrik and OpenFreeMap | Base vector tiles, roads, and house numbers | ODbL. © OpenStreetMap contributors. |
| OpenFreeMap and OpenMapTiles | Tile hosting and schema | OpenFreeMap project MIT. OpenMapTiles code BSD 3-Clause, design CC BY 4.0. |
| Merced County GIS site address points | Address database | Public as-is disclaimer. Attribute Merced County GIS. Not a named open license. |
| Merced County GIS road centerlines (DATAMARK VEP) | Missing streets, and names on streets OpenStreetMap draws unnamed. Overland / Place edits run through 2025-07-22. | Same county as-is terms. Attribute Merced County GIS. |
| Merced County GIS assessment parcels | Public service, checked for right-of-way gaps. No street-name field, and no geometry was copied. | Same county as-is terms. |
| US Census TIGER/Line 2024, 2025 checked | Fallback roads not already covered. The 2025 file adds none of the Overland / Place streets. | Public domain. |
| Overture Maps 2026-09-23.1 | Non-overlapping building footprints, and a transportation check that did not add these names. | ODbL. |
| California Protected Areas Database (CPAD), queried on Merced County GIS 2026-09-27 | Los Banos park outlines in `places.sqlite` and the `supplemental_park` tile layer. Park outlines and names that come from OpenStreetMap are covered by the OpenStreetMap row. | Attribute the California Protected Areas Database and Merced County GIS. |

The City of Los Banos does not publish a road-centerline download.

Live Overpass for the box (2026-09-26T23:50:05Z) is one day newer than the Geofabrik extract and still does not name these streets.
