# Week 2 — Data Note

## Project

**Question:** Which neighborhoods in Yaoundé contain the largest populations living in low-lying areas within 200 metres of a waterway?

This week's work focused on acquiring, opening, checking and preparing the datasets required for the project.

---

## 1. OpenStreetMap / Geofabrik Cameroon

**Source:** OpenStreetMap data distributed through Geofabrik

**Source link:** https://download.geofabrik.de/africa/cameroon.html

**Original file:** `Cameroon-260910.osm.pbf`

**Purpose:** Provide mapped geographic features for Yaoundé, including administrative boundaries, linear features, points and polygons. The Yaoundé study-area layers were derived from the Cameroon extract in QGIS.

### Yaoundé administrative units

**File:** `yaounde_admin_units.gpkg`

- Feature count: 7
- Geometry: Polygon
- Key columns: `type`, `admin_level`, `boundary`, `name`
- Missing values: No major missing values identified in the key administrative fields used for the project.

### Yaoundé boundary

**File:** `yaounde_boundary.gpkg`

- Feature count: 1
- Geometry: Polygon
- Purpose: Dissolved Yaoundé study-area boundary used to clip the datasets.
- Missing values: Not relevant to the spatial boundary itself.

### Yaoundé lines

**File:** `yaounde_lines.gpkg`

- Feature count: 97,404
- Geometry: Line
- Key columns: `osm_id`, `name`, `highway`, `waterway`, `other_tags`
- Waterway features: 2,456
- Missing values: The `waterway` field contains NULL values for features that are not classified as waterways. These records were retained in the source-derived layer and will only be excluded when extracting waterways for the analysis.

### Yaoundé points

**File:** `yaounde_points.gpkg`

- Feature count: 240,516
- Geometry: Point
- Key columns: `osm_id`, `name`, `other_tags`
- Missing values: Some descriptive OSM attributes contain NULL values because not every mapped point has all attributes populated.

### Yaoundé multilinestrings

**File:** `yaounde_multilinestring.gpkg`

- Feature count: 6
- Geometry: MultiLineString
- Key columns: `osm_id`, `name`, `type`
- Missing values: Some descriptive attributes may contain NULL values because not every OSM feature has all attributes populated.

---

## 2. SRTM Elevation

**Source:** WorldPop

**Source link:** https://hub.worldpop.org/geodata/summary?id=23306

**Original dataset:** `cmr_srtm_topo_100m.tif`

**Working file:** `yaounde_srtm_100m.tif`

**Purpose:** Provide elevation data for identifying relatively low-lying terrain within Yaoundé.

- Geometry: Raster grid
- Dimensions: 196 rows × 306 columns
- Resolution: Approximately 100 m
- CRS: WGS 84 geographic coordinate system
- Main variable: Elevation

Raster feature count is not applicable because this is a grid of cells rather than a vector feature layer.

---

## 3. WorldPop Population Counts

**Source:** WorldPop

**Source link:** https://hub.worldpop.org/geodata/summary?id=6347

**Original dataset:** `cmr_ppp_2020.tif`

**Working file:** `yaounde_population_2020.tif`

**Purpose:** Estimate the population located within the potential exposure zone.

- Geometry: Raster grid
- Dimensions: 196 rows × 306 columns
- Resolution: Approximately 100 m
- CRS: WGS 84 geographic coordinate system
- Main variable: Estimated population per grid cell

Raster feature count is not applicable because this is a grid of population cells rather than a vector feature layer.

---

## Data Preparation

The original Cameroon OSM extract and national raster datasets were processed in QGIS to create Yaoundé-specific working datasets.

The workflow included:

1. Selecting the seven Yaoundé administrative units from the OSM data.
2. Dissolving them into a single Yaoundé study-area boundary.
3. Clipping the OSM vector layers to the Yaoundé boundary.
4. Clipping the SRTM elevation raster to the study area.
5. Clipping the WorldPop population raster to the study area.
6. Identifying 2,456 mapped waterway features from the Yaoundé lines dataset.

The original datasets were retained separately from the derived Yaoundé working layers.

---

## Data Quality and Missing Values

NULL values were not automatically removed. Missing values were assessed according to their meaning and relevance to the analysis.

In the OSM data, NULL values are expected in some fields because different feature types do not necessarily have the same attributes. For example, the `waterway` field is not populated for features that are not classified as waterways.

For the waterway analysis, only relevant waterway features will be selected rather than deleting records from the original OSM-derived layer.

The raster datasets are grid-based and contain data cells representing elevation or estimated population. Their dimensions are reported rather than a vector feature count.
