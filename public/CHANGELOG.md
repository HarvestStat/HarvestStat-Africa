# Changelog
All notable changes to the HarvestStat Africa dataset are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

This project follows a dataset-oriented versioning scheme:
- **Minor versions (x.y)** indicate bug fixes, consistency improvements, and metadata/QC updates based on the same offline raw data.
- **Major versions (x.0)** indicate substantial data updates, schema changes, or new raw data sources.

---

## [1.1] - 2026-01-09
### Summary
This release addresses minor issues and consistency problems identified in v1.0.  
No new raw data were added; all updates are based on the same offline raw data as v1.0.  
A major data update is planned for the next release.

### Added
- An ESRI shapefile of administrative boundaries has been added to `public/`
  ([#83](https://github.com/HarvestStat/HarvestStat-Africa/issues/83)).

### Changed
- Country names are hard-coded to follow **ISO 3166-1 short names** using `pycountry`,
  applied consistently across both data and boundary files
  ([#78](https://github.com/HarvestStat/HarvestStat-Africa/issues/78)).
- Column names in the boundary file are standardized to lower case:
  `fnid`, `country`, `country_code`, `admin_1`, `admin_2`.
- The `public/` folder now contains **only the latest stable release**;
  archived versions are accessible via
  [Git tags](https://github.com/HarvestStat/HarvestStat-Africa/tags)
  and [GitHub Releases](https://github.com/HarvestStat/HarvestStat-Africa/releases).

### Fixed
- All errors in `CropData_{country_code}_profile.ipynb` have been fixed
  ([#86](https://github.com/HarvestStat/HarvestStat-Africa/issues/86)).
- QC algorithm issues have been resolved
  ([#80](https://github.com/HarvestStat/HarvestStat-Africa/issues/80)).
- Crop calendar inconsistencies have been corrected
  ([#79](https://github.com/HarvestStat/HarvestStat-Africa/issues/79)).

---

## [1.0] - 2025-04-09
### Summary
Fixed the `qc_flag` issue from the previous version, ensuring proper functionality.  
Data records remain identical to the March 26, 2025 version, with **574,204 records**
across **33 countries**.  
The updated version has been uploaded to
https://doi.org/10.5061/dryad.vq83bk42w.

---

## [1.0] - 2025-03-28
### Summary
Official release of **HarvestStat Africa v1.0**, corresponding to the
*[Scientific Data](https://doi.org/10.1038/s41597-025-05001-z)* publication.

### Added
- Harmonized subnational crop production statistics for Sub-Saharan Africa
  (574,204 records across 33 countries).
- Initial QC flags and metadata.
- FEWS NET-aligned administrative boundary files.

### Notes
- This release serves as the baseline version.
- A full dataset description is available on Dryad:
  https://datadryad.org/dataset/doi:10.5061/dryad.vq83bk42w

---

## [1.0b] - 2025-03-26
### Summary
Updated crop statistics using the latest FEWS NET Data Warehouse.  
Fixed inconsistencies in planting and harvesting dates for several regions.  
Updated boundary shapefiles to reflect the latest administrative changes.  
This version includes **574,204 records** across **33 countries**.

---

## [1.0b] - 2024-09-04
### Summary
Initial release of the dataset (`v1.0b`), subject to updates during paper revisions.  
Included **546,605 records** across **33 countries**.  
Provided boundary shapefiles in GeoPackage format.