# Data Note — Yaoundé Geospatial Project

## Project Question

Which areas of Yaoundé contain the largest populations living in low-lying areas within 200 metres of a waterway?

## 1. OpenStreetMap — Cameroon

**File:** `Cameroon-260910.osm.pbf`

**Source:** OpenStreetMap data downloaded from Geofabrik  
https://download.geofabrik.de/africa/cameroon.html

**Purpose:** Provides the spatial data needed to identify the Yaoundé study area and mapped waterways.

**Format:** `.osm.pbf`

**Geometry:** The OSM extract contains multiple vector layers, including points, lines and multipolygons.

**Features:** The `lines` layer contains a very large number of features and was successfully opened in QGIS. The exact total feature count is still being verified. The `multipolygons` layer currently displays 99 features in QGIS.

**Key columns:** OSM attribute fields include information such as `name`, `waterway`, `boundary`, and `admin_level`, depending on the layer.

**Data quality / gaps:** Many attribute fields are sparsely populated. In the initial inspection of the `lines` layer, the `waterway` field contained values for only a small number of observed features, while most records were empty. This requires further investigation to determine how waterways are represented in the OSM extract and which features should be used for the project.

## 2. SRTM Elevation — Cameroon

**File:** `cmr_srtm_topo_100m.tif`

**Source:** WorldPop  
https://hub.worldpop.org/geodata/summary?id=23306

**Purpose:** Provides elevation data for identifying relatively low-lying terrain within the Yaoundé study area.

**Format:** Geographic 2D GeoTIFF

**Geometry:** Raster grid, with elevation values stored in raster cells.

**Coverage:** Cameroon

**Resolution:** Approximately 100 m

**Dimensions:** 5,416 rows × 6,714 columns

**Key information:** Each raster cell contains an elevation value.

**Data quality / gaps:** The raster was successfully opened and inspected in QGIS. No specific major data gap was identified during the initial inspection.

## 3. WorldPop Population — Cameroon, 2020

**File:** `cmr_ppp_2020.tif`

**Source:** WorldPop  
https://hub.worldpop.org/geodata/summary?id=6347

**Purpose:** Provides estimated population distribution for 2020 and will be used to estimate the population within the potential exposure zones.

**Format:** GeoTIFF

**Geometry:** Raster grid

**CRS:** EPSG:4326 — WGS 84 Geographic

**Pixel size:** Approximately 0.00083° × -0.00083°

**Dimensions:** 6,087 rows × 6,646 columns

**Minimum value:** 0.0007

**Maximum value:** 256.4467

**Key information:** Estimated population values are stored in raster cells.

**Data quality / gaps:** The raster contains varying population values across cells, including very low values. These values should be distinguished from NoData cells during later analysis.

## Initial Data Assessment

The three datasets were downloaded from real sources and opened in QGIS. The SRTM and WorldPop datasets were successfully inspected as raster layers. The Cameroon OpenStreetMap PBF was also loaded into QGIS as multiple vector layers. Initial inspection shows that the OSM data contain a large number of features and some sparsely populated attribute fields. Further inspection will be required to isolate the Yaoundé boundary and the relevant mapped waterways for the spatial analysis.
