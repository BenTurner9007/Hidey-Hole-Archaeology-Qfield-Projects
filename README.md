# Hidey Hole Archaeology — Fieldwalking QField Project

A ready-to-use QGIS/QField project for running community and society **fieldwalking surveys**. It packages a GeoPackage of spatial layers, symbology, and data-entry rules so a local archaeology group can go from "empty QGIS project" to "recording finds on a phone in the field" with minimal setup.

## What's in this repository

```
.
└── field_walking_geopackage/
    ├── fieldwalking_layers.gpkg          # GeoPackage: layers, styles, and the embedded QGIS project
    ├── FIELDWALKING_SETUP.md             # Step-by-step guide: QGIS → QField Cloud → phone
    └── Fieldwalking project explained.md # Reference for each layer and its attributes
```

## The layers

The GeoPackage (`fieldwalking_layers.gpkg`) includes:

- [**`fieldwalking_find`**](./field_walking_geopackage/Fieldwalking%20project%20explained.md#fieldwork-recording--fieldwalking_find) (point) — records an individual find. Categorised symbology by artefact type (via a `artefact_types` value-relation table), an enforced-unique find number, finder name (via a `field_operatives` value-relation table), a photo field, and auto-populated date, GPS accuracy, and easting/northing/height.
- **`areas_covered`** (polygon) — the ground actually walked, with an auto-recorded date, for spatial coverage analysis.
- **`areas_unavailable`** (polygon) — areas that couldn't be surveyed (e.g. flooded, crops), with a date and a free-text description, so gaps in coverage are documented rather than just absent.

Full attribute-by-attribute details are in [`Fieldwalking project explained.md`](field_walking_geopackage/Fieldwalking%20project%20explained.md).

## Getting started

1. Download `fieldwalking_layers.gpkg` from this repository.
2. Add it as a GeoPackage connection in QGIS and open the embedded project.
3. Install the QField Sync plugin and convert the project to a QField Cloud project.
4. Sync to the QField app on your phone and start recording finds in the field.

The full walkthrough, with screenshots, is in [`FIELDWALKING_SETUP.md`](field_walking_geopackage/FIELDWALKING_SETUP.md).

## Customising for your own survey

This project was built for one local group's needs, but it's meant to be adapted:

- Add new artefact types by editing the `artefact_types` value-relation table, then re-classify the `fieldwalking_find` symbology so each type gets its own colour.
- Add field operatives to the `field_operatives` table so they appear in the Finder Name dropdown.
- If running multiple QField devices at once, agree find-number blocks between recorders up front to avoid duplicate IDs.

## License / reuse

Feel free to download, adapt, and reuse this project for your own fieldwalking surveys.
