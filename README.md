# Sentinel-5P Extension Specification

- **Title:** Sentinel-5P
- **Identifier:** <https://stac-extensions.github.io/sentinel-5p/v0.2.0/schema.json>
- **Field Name Prefix:** s5p
- **Scope:** Item
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @m-mohr

This document explains the Sentinel-5P Extension to the
[SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) specification.

> \[!CAUTION]
> The intention of the first version of the specification was to reflect the existing behavior of the properties
> prefixed with `s5p` as implemented by the [stactools-sentinel5p](https://github.com/stactools-packages/sentinel5p) package.
> The following version deprecated most of the fields in favor of other extensions that are not specific to Sentinel-5P.
> The remaining fields can be used if providers think they offer additional value to users.
> For all other fields the recommended alternatives should be preferred.

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

| Field Name                | Type   | Description                    |
| ------------------------- | ------ | ------------------------------ |
| s5p:processing_mode       | string | One of: `NRTI`, `OFFL`, `RPRO` |
| s5p:collection_identifier | string | One of: `01`, `02`, `03`       |

> \[!NOTE]
> Various fields and objects in this extensions have been deprecated.
> Please see the [document about deprecated fields](deprecated.md) for more information.

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
