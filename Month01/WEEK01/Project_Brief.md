# PROJECT BRIEF

## 1. THE QUESTION

Which neighborhoods in Yaoundé contain the largest populations living in low-lying areas within 200 metres of a waterway?

## 2. WHY IT MATTERS

Yaoundé’s dense urban development, varied terrain and numerous waterways create places where populations may be more exposed to flooding. Identifying where large populations overlap with relatively low-lying terrain and proximity to waterways can help urban planners and disaster-risk stakeholders identify priority areas for further investigation. This project is a screening analysis, not a flood prediction model.

## 3. THE DATA I NEED

| Dataset | Purpose |
|---|---|
| OpenStreetMap / Geofabrik Cameroon — Yaoundé boundary + mapped waterways | Define the study area and create the 200 m waterway buffer. |
| SRTM elevation (~100 m) | Identify the lowest 20% of terrain within Yaoundé as the project’s relative low-lying zone. |
| WorldPop Cameroon population, 2020 (~100 m) | Estimate the population contained in the potential exposure zone. |

## 4. WHERE EACH DATASET COMES FROM

**OpenStreetMap / Geofabrik — Cameroon OSM extract** — Cameroon OpenStreetMap data in `.osm.pbf` format, used to identify the Yaoundé study area and mapped waterways.

https://download.geofabrik.de/africa/cameroon.html

**WorldPop — SRTM elevation, Cameroon** — SRTM-derived elevation at 3 arc-seconds (approximately 100 m); GeoTIFF, WGS 84.

https://hub.worldpop.org/geodata/summary?id=23306

**WorldPop — Population Counts, Cameroon, 2020** — Estimated population per grid cell at 3 arc-seconds (approximately 100 m); GeoTIFF, WGS 84.

https://hub.worldpop.org/geodata/summary?id=6347

## 5. WHAT I WILL BUILD

A Yaoundé Population Exposure to Low-Lying Areas Near Waterways Map, plus a ranked table showing the areas with the largest estimated populations inside the potential exposure zones. The workflow will clip the data to Yaoundé, derive the lowest 20% of terrain, buffer mapped waterways by 200 m, intersect the two zones, overlay WorldPop population, and aggregate the results by the selected geographic unit. The final product will be a reproducible screening tool for identifying priority areas for further flood-exposure and urban-resilience investigation.
