# Deprecated fields in the Sentinel-5 Extension Specification

The following document describes all deprecated fields and objects that had been defined before.
For the sake of simplicity the deprecated content has been moved to this separate document.

## Fields

The fields in the table below can be used in these parts of STAC documents:

- [ ] Catalogs
- [ ] Collections
- [x] Item Properties (incl. Summaries in Collections)
- [ ] Assets (for both Collections and Items, incl. Item Asset Definitions in Collections)
- [ ] Links

| Field Name             | Type          | Description                                                  |
| ---------------------- | ------------- | ------------------------------------------------------------ |
| s5p:product_name       | string        | **DEPRECATED** Use `product:type` instead. One of: `aer-ai`, `aer-lh`, `ch4`, `cloud`, `co`, `hcho`, `no2`, `np-bd3`, `np-bd6`, `np-bd7`, `o3`, `o3-tcl`, `so2`, ... |
| s5p:product_type       | string        | **DEPRECATED** Use `product:type` instead. One of: `L2__AER_AI`, `L2__AER_LH`, `L2__CH4___`, `L2__CLOUD_`, `L2__CO____`, `L2__HCHO__`, `L2__NO2___`, `L2__NP_BD3`, `L2__NP_BD6`, `L2__NP_BD7`, `L2__O3_TCL`, `L2__O3____`, `L2__SO2___`, ... |
| s5p:spatial_resolution | [number]      | **DEPRECATED** Use `spatial_resolution` (raster extension) instead |
| s5p:shape              | [integer]     | **DEPRECATED** Use proj:shape instead                        |
| s5p:aer_ai             | Aer Ai Object | **DEPRECATED** Only for products with name `aer-ai`          |
| s5p:aer_lh             | Aer Lh Object | **DEPRECATED** Only for products with name `aer-lh`          |
| s5p:ch4                | CH4 Object    | **DEPRECATED** Only for products with name `ch4`             |
| s5p:cloud              | Cloud Object  | **DEPRECATED** Only for products with name `cloud`           |
| s5p:co                 | CO            | **DEPRECATED** Only for products with name `co`              |
| s5p:hcho               | HCHO Object   | **DEPRECATED** Only for products with name `hcho`            |
| s5p:no2                | NO2 Object    | **DEPRECATED** Only for products with name `no2`             |
| s5p:npbd3              | NPBD Object   | **DEPRECATED** Only for products with name `np-bd3`          |
| s5p:npbd6              | NPBD Object   | **DEPRECATED** Only for products with name `np-bd6`          |
| s5p:npbd7              | NPBD Object   | **DEPRECATED** Only for products with name `np-bd7`          |
| s5p:o3                 | O2 Object     | **DEPRECATED** Only for products with name `o3`              |
| s5p:o3_tcl             | O3 TCL Object | **DEPRECATED** Only for products with name `o3-tcl`          |
| s5p:so2                | SO2 Object    | **DEPRECATED** Only for products with name `so2`             |

### Object for Aer Ai

| Field Name                 | Type    | Description |
| -------------------------- | ------- | ----------- |
| input_band                 | string  |             |
| irradiance_accompanied     | string  |             |
| geolocation_grid_from_band | integer |             |

### Object for NO2 / CO / Aer Lh / CH4

| Field Name                 | Type     | Description |
| -------------------------- | -------- | ----------- |
| input_band                 | [string] |             |
| irradiance_accompanied     | string   |             |
| geolocation_grid_from_band | integer  |             |

### Object for O3 / SO2 / Cloud / HCHO

| Field Name                 | Type    | Description |
| -------------------------- | ------- | ----------- |
| cloud_mode                 | string  |             |
| geolocation_grid_from_band | integer |             |

### Object for O3 TCL

| Field Name                  | Type      | Description                                                  |
| --------------------------- | --------- | ------------------------------------------------------------ |
| shape_ccd                   | [integer] |                                                              |
| shape_csa                   | [integer] |                                                              |
| stratosphere_start_datetime | string    | RFC3339 datetime in UTC                                      |
| stratosphere_end_datetime   | string    | RFC3339 datetime in UTC                                      |
| troposphere_start_datetime  | string    | RFC3339 datetime in UTC                                      |
| troposphere_end_datetime    | string    | RFC3339 datetime in UTC                                      |
| input_orbits                | [integer] |                                                              |
| input_files                 | [string]  | List of product IDs, e.g. `S5P_OFFL_L2__O3_____20200303T114449_20200303T132620_12373_01_010107_20200306T170003` |

### Object for NPBD

| Field Name           | Type      | Description |
| -------------------- | --------- | ----------- |
| analysed_s5p_band    | integer   |             |
| VIIRS_band           | [integer] |             |
| number_of_scaled_fov | integer   |             |
