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

## Merced County, version 4

Version 4 keeps the version 3 roads, addresses, and park rings. It draws Merced County site-address points on the map as `supplemental_housenumber` when the tiles have no OpenStreetMap `housenumber` with the same number within 15 meters. The label uses the same font, size, and zoom range as the OpenStreetMap numbers. Of 29,041 county points, 16,493 are drawn and 12,548 already sit on an OpenStreetMap number. All 273 points on the new streets east of Overland Avenue and Place Road (Collins, Donovan, Dowell, Meyers, Parker, Sullivan, Barrett, Broadstone, Casey, Gallaway, Kelley, and Geiss) are drawn. A number with no building footprint within 15 meters is drawn alone, with a small dot. No footprint was invented.

`merced.mbtiles` is 22,614,016 bytes, sha256 `92fb227922702d85de047b8c69a41da1f72bc06061ae234e0f49437bd2c0813b`. `roads.sqlite`, `addresses.sqlite`, and `places.sqlite` are unchanged from version 3.

## Merced County, version 5

Version 5 keeps the version 4 address points, house numbers, park rings, and building footprints. It adds Los Banos streets from the Merced County GIS road centerlines that the version 4 tiles did not draw, and it names streets the tiles already draw with no name.

Checked on 2026-09-27. The county centerline service has no edit newer than 2026-05-21. The site-address service has no edit newer than 2026-06-17 (104,075 points, same as version 4). TIGER/Line 2025 (`tl_2025_06047_roads`) does not contain the new west Los Banos streets. TIGER/Line 2026 is not published. The City of Los Banos does not publish a road-centerline layer. Assessment parcels in the circled tract have lot lines and no street-name field, and no right-of-way parcel is named. OpenStreetMap Overpass on 2026-09-27 draws several of these streets with no name. Overture transportation 2026-09-23.1 was already the newest release used for version 4; no newer release was available.

Heron Drive, Sandhill Crane Drive, and Stilt Lane are already in version 4 in the Meadowlands tract (about 37.060, -120.806), including the 2800 block of Stilt Lane. They are several kilometers east of the blank area south of Highway 152 and north of Pioneer Road.

New lines, from county centerlines, drawn because the version 4 tiles had no pavement there:

- Catherine Hostetler Boulevard
- Del Mar Court
- Del Mar Drive
- Estero Court
- Estero Drive
- Gilbert Gonzalez Jr Drive
- Hermosa Court
- Santa Fe Grade (a north segment the tiles did not have)
- Second Street (Volta)
- Solana Drive
- Solimar Drive, the north block with addresses 1835–1853

Names added on pavement the tiles already draw, from the same county centerlines:

- Basalt Drive, Billy Wright Road (an unlabeled stretch), Cardoza Road (west of the labeled part), Columbia Drive, Commerce Way, Dancy Street, Felsite Street, Gabbro Way, Gypsum Court, Gypsum Drive, Honeybell Court, Honeybell Street, Obsidian Place, Onyx Way, Pearl Drive, Ryegrass Way, Sunburst Court, Sunburst Street, Trailer Way, West Santa Barbara Street

Where an unnamed road was already in the road database under that pavement, that road was renamed. Otherwise the county centerline was inserted. Address points for these streets were already in `addresses.sqlite`, and version 4 already draws those house numbers. No house was invented, and no footprint was invented.

Not added, because there is no source that names them:

- The graded ground west of Montara Drive, between the Los Banos Creek / canal corridor and the new lots. Those assessor parcels are large remainder parcels (no subdivision lots, no addresses, no named right-of-way).
- Cherokee Road and Ramos Road. The county lines sit tens of meters off the roads already in the pack, so a second line was not drawn.
- A Frontier Street county segment that runs across streets already in the pack.

`merced.mbtiles` is 22,614,016 bytes, sha256 `8375781104ba62574f2b1694eafd993f1d2c87c31768a39546723dd3174ad295`. `roads.sqlite` is 17,248,256 bytes, sha256 `a374f080c8ab8bb54816a60813cb730cc7abd44c3ed8ec83973b0402da54ba6b`. `addresses.sqlite` and `places.sqlite` are unchanged from version 4.
