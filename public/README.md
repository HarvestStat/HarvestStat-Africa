# HarvestStat Africa – Harmonized Subnational Crop Statistics for Sub-Saharan Africa

**Authors:**  
D. Lee, W. Anderson, X. Chen, F. Davenport, S. Shukla, R. Sahajpal, M. Budde, J. Rowland, J. Verdin, L. You, M. Ahouangbenon, K. Davis, E. Kebede, S. Ehrmann, C. Justice, and C. Meyer

---

## Author Information

**Donghoon Lee**  
Department of Civil Engineering, University of Manitoba, Winnipeg, Manitoba, Canada  
Email: [Donghoon.Lee@umanitoba.ca](mailto:Donghoon.Lee@umanitoba.ca)

**Weston Anderson**  
Earth System Science Interdisciplinary Center, University of Maryland, College Park, Maryland, USA  
Email: [Weston@umd.edu](mailto:Weston@umd.edu)

**Xuan Chen**  
Earth System Science Interdisciplinary Center, University of Maryland, College Park, Maryland, USA  
Email: [X.Chen@cgiar.org](mailto:X.Chen@cgiar.org)

**Frank Davenport**  
Climate Hazards Center, Department of Geography, University of California, Santa Barbara, California, USA  
Email: [frank.davenport@geog.ucsb.edu](mailto:frank.davenport@geog.ucsb.edu)

**Shraddhanand Shukla**  
Climate Hazards Center, Department of Geography, University of California, Santa Barbara, California, USA  
Email: [shrad@geog.ucsb.edu](mailto:shrad@geog.ucsb.edu)

**Ritvik Sahajpal**  
Department of Geographical Sciences, University of Maryland, College Park, MD, USA  
Email: [ritvik@umd.edu](mailto:ritvik@umd.edu)

**Michael Budde**  
U.S. Geological Survey, Earth Resources Observation and Science Center, Sioux Falls, SD, USA  
Email: [mbudde@usgs.gov](mailto:mbudde@usgs.gov)

**James Rowland**  
U.S. Geological Survey, Earth Resources Observation and Science Center, Sioux Falls, SD, USA  
Email: [rowland@usgs.gov](mailto:rowland@usgs.gov)

**Jim Verdin**  
U.S. Agency for International Development, Washington, DC, USA  
Email: [jverdin@usaid.gov](mailto:jverdin@usaid.gov)

**Liangzhi You**  
International Food Policy Research Institute, Washington, DC, USA  
Email: [l.you@cgiar.org](mailto:l.you@cgiar.org)

**Matthieu Ahouangbenon**  
Department of Geography and Spatial Sciences, University of Delaware, Newark, DE, USA  
Email: [mathdel@udel.edu](mailto:mathdel@udel.edu)

**Kyle Frankel Davis**  
Department of Geography and Spatial Sciences, University of Delaware, Newark, DE, USA  
Email: [kfdavis@udel.edu](mailto:kfdavis@udel.edu)

**Endalkachew Kebede**  
Department of Geography and Spatial Sciences, University of Delaware, Newark, DE, USA  
Email: [endiabe@udel.edu](mailto:endiabe@udel.edu)

**Steffen Ehrmann**  
German Centre for Integrative Biodiversity Research (iDiv) Halle–Jena–Leipzig, Leipzig, Germany  
Email: [steffen.ehrmann@idiv.de](mailto:steffen.ehrmann@idiv.de)

**Christina Justice**  
Department of Geographical Sciences, University of Maryland, College Park, MD, USA  
Email: [justicec@umd.edu](mailto:justicec@umd.edu)

**Carsten Meyer**  
German Centre for Integrative Biodiversity Research (iDiv) Halle–Jena–Leipzig, Leipzig, Germany  
Email: [carsten.meyer@idiv.de](mailto:carsten.meyer@idiv.de)

---

## File List

### **hvstat_africa_data_v1.2.csv**
A CSV file containing harmonized subnational crop statistics.

**Data Structure**

| Column Name              | Description                                                       |
|--------------------------|-------------------------------------------------------------------|
| `fnid`                   | FEWS NET unique geographic unit identifier                        |
| `country`                | Country name                                                      |
| `country_code`           | ISO 3166-1 alpha-2 country code                                   |
| `admin_1`                | First-level administrative unit name                              |
| `admin_2`                | Second-level administrative unit name (if applicable)             |
| `product`                | Crop product name                                                 |
| `season_name`            | Growing season name                                               |
| `planting_year`          | Year when planting begins                                         |
| `planting_month`         | Month when planting begins                                        |
| `harvest_year`           | Year when harvesting ends                                         |
| `harvest_month`          | Month when harvesting ends                                        |
| `crop_production_system` | Crop production system (e.g., irrigated, rainfed)                 |
| `qc_flag`                | Quality control flag (0 = none, 1 = outlier, 2 = low variance)     |
| `area`                   | Cropped area (hectares; ha)                                       |
| `production`             | Production volume (metric tonnes; mt)                             |
| `yield`                  | Yield (metric tonnes per hectare; mt/ha)                          |

### **hvstat_africa_boundary_v1.2.gpkg**
A GeoPackage file containing FEWS NET-aligned administrative boundaries,
linked to crop statistics via `fnid`.

**Data Structure**

| Column Name | Description                                      |
|------------|--------------------------------------------------|
| `fnid`     | FEWS NET unique geographic unit identifier       |
| `country`  | Country name                                     |
| `country_code` | ISO 3166-1 alpha-2 country code              |
| `admin_1`  | First-level administrative unit name             |
| `admin_2`  | Second-level administrative unit name            |
| `geometry` | Administrative boundary geometry                 |

### **hvstat_africa_boundary_v1.2.shp**
A shapefile version of FEWS NET administrative boundaries.
The data structure is identical to the GeoPackage file.

### **fdw_raw_data_v1.2.zip**
This file is not included in the Dryad dataset. From v1.2 onward, the raw FEWS NET Data Warehouse (FDW) data archive used to develop HarvestStat Africa is provided through the [HarvestStat-Africa GitHub releases](https://github.com/HarvestStat/HarvestStat-Africa/releases) for reference and reproducibility purposes. Individual country CSV files are named using ISO 3166-1 alpha-2 codes.

---

## Change Log
Please refer to  
[CHANGELOG.md](https://github.com/HarvestStat/HarvestStat-Africa/blob/main/public/CHANGELOG.md)
for detailed version history and updates.

---

## Source data and derived dataset note

HarvestStat Africa is a derived, harmonized dataset constructed from multiple original source documents and data products. The harmonized HarvestStat Africa data and boundary files are not a direct redistribution of the original source files or database records. The original source materials used to construct the dataset are listed in Table S1 of the Supplementary Information associated with the HarvestStat Africa paper.

---

## Citation
Lee, D., Anderson, W., Chen, X., Davenport, F., Shukla, S., Sahajpal, R., Budde, M., Rowland, J., Verdin, J., You, L., Ahouangbenon, M., Davis, K. F., Kebede, E., Ehrmann, S., Justice, C., & Meyer, C. (2025). **HarvestStat Africa – Harmonized Subnational Crop Statistics for Sub-Saharan Africa**. *Scientific Data*. https://doi.org/10.1038/s41597-025-05001-z
