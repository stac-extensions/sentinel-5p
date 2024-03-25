# Sentinel-5P Extension Specification

- **Title:** Sentinel-5P
- **Identifier:** <https://stac-extensions.github.io/sentinel-5p/v1.0.0/schema.json>
- **Field Name Prefix:** s5p
- **Scope:** Item
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @m-mohr

This document explains the Sentinel-5P Extension to the
[SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) specification.

The intention of the first version of the specification is to define the existing behavior of
the properties prefixed with `s5p` as created by the
[stactools-sentinel5p](https://github.com/stactools-packages/sentinel5p) package and used by
[Microsoft Planetary Computer](https://planetarycomputer.microsoft.com/api/stac/v1). Future versions
will aspire to standardize fields such as the numerous coverage calculations into separate extensions that are not specific to Sentinel-5P.

- [Examples](examples/)
- [JSON Schema](json-schema/schema.json)
- [Changelog](./CHANGELOG.md)

## Fields

The fields in the table below can be used in these parts of STAC documents:

- [ ] Catalogs
- [ ] Collections
- [x] Item Properties (incl. Summaries in Collections)
- [ ] Assets (for both Collections and Items, incl. Item Asset Definitions in Collections)
- [ ] Links

| Field Name                | Type          | Description                                                  |
| ------------------------- | ------------- | ------------------------------------------------------------ |
| s5p:product_name          | string        | One of: `aer-ai`, `aer-lh`, `ch4`, `cloud`, `co`, `hcho`, `no2`, `np-bd3`, `np-bd6`, `np-bd7`, `o3`, `o3-tcl`, `so2`, ... |
| s5p:product_type          | string        | One of: `L2__AER_AI`, `L2__AER_LH`, `L2__CH4___`, `L2__CLOUD_`, `L2__CO____`, `L2__HCHO__`, `L2__NO2___`, `L2__NP_BD3`, `L2__NP_BD6`, `L2__NP_BD7`, `L2__O3_TCL`, `L2__O3____`, `L2__SO2___`, ... |
| s5p:processing_mode       | string        | One of: `NRTI`, `OFFL`, `RPRO`                               |
| s5p:collection_identifier | string        | One of: `01`, `02`, `03`                                     |
| s5p:spatial_resolution    | [number]      |                                                              |
| s5p:shape                 | [integer]     | **DEPRECATED** Use proj:shape instead                        |
| s5p:aer_ai                | Aer Ai Object | Only for products with name `aer-ai`                         |
| s5p:aer_lh                | Aer Lh Object | Only for products with name `aer-lh`                         |
| s5p:ch4                   | CH4 Object    | Only for products with name `ch4`                            |
| s5p:cloud                 | Cloud Object  | Only for products with name `cloud`                          |
| s5p:co                    | CO            | Only for products with name `co`                             |
| s5p:hcho                  | HCHO Object   | Only for products with name `hcho`                           |
| s5p:no2                   | NO2 Object    | Only for products with name `no2`                            |
| s5p:npbd3                 | NPBD Object   | Only for products with name `np-bd3`                         |
| s5p:npbd6                 | NPBD Object   | Only for products with name `np-bd6`                         |
| s5p:npbd7                 | NPBD Object   | Only for products with name `np-bd7`                         |
| s5p:o3                    | O2 Object     | Only for products with name `o3`                             |
| s5p:o3_tcl                | O3 TCL Object | Only for products with name `o3-tcl`                         |
| s5p:so2                   | SO2 Object    | Only for products with name `so2`                            |

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

## Contributing

All contributions are subject to the
[STAC Specification Code of Conduct](https://github.com/radiantearth/stac-spec/blob/master/CODE_OF_CONDUCT.md).
For contributions, please follow the
[STAC specification contributing guide](https://github.com/radiantearth/stac-spec/blob/master/CONTRIBUTING.md) Instructions
for running tests are copied here for convenience.

### Running tests

The same checks that run as checks on PR's are part of the repository and can be run locally to verify that changes are valid. 
To run tests locally, you'll need `npm`, which is a standard part of any [node.js installation](https://nodejs.org/en/download/).

First you'll need to install everything with npm once. Just navigate to the root of this repository and on 
your command line run:
```bash
npm install
```

Then to check markdown formatting and test the examples against the JSON schema, you can run:
```bash
npm test
```

This will spit out the same texts that you see online, and you can then go and fix your markdown or examples.

If the tests reveal formatting problems with the examples, you can fix them with:
```bash
npm run format-examples
```
