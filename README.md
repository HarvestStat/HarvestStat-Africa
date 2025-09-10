# HarvestStat-Africa: Open-Access Harmonized Subnational Crop Statistics
![GitHub](https://img.shields.io/github/license/HarvestStat/HarvestStat-Africa)
![GitHub last commit](https://img.shields.io/github/last-commit/HarvestStat/HarvestStat-Africa)
![GitHub issues](https://img.shields.io/github/issues/HarvestStat/HarvestStat-Africa)
![GitHub pull requests](https://img.shields.io/github/issues-pr/HarvestStat/HarvestStat-Africa)
<!-- ![GitHub forks](https://img.shields.io/github/forks/HarvestStat/HarvestStat-Africa)
![GitHub stars](https://img.shields.io/github/stars/HarvestStat/HarvestStat-Africa) -->

## Overview

The HarvestStat-Africa is a repository that contains cleaned and harmonized subnational global crop production data for Africa from various sources, including the Famine [Early Warning Systems Network (FEWS NET)](https://fews.net/) of the U.S. Department of State Office of Global Food Security and the Food and Agriculture Organization (FAO).</br>

This repository provides access to a comprehensive crop dataset that allows researchers, policymakers, and stakeholders to explore trends and patterns from  the subnational to the global level, enabling better-informed decisions related to food security, trade, and development.</br>

## Data sources
The data in this repository is compiled from various sources, including:
- Famine Early Warning Systems Network (FEWS NET). This is the primary source of information
    - [FEWS NET Data Warehouse (FDW)](https://fews.net/data)
- Food and Agriculture Organization (FAO)
    - [FAOSTAT](https://www.fao.org/faostat/en/#home)
- National agricultural agencies

## Repository structure
This repository is organized as follows:
- `data/`: stores raw and intermediate crop statistics generated during internal processing.
- `docs/`: contains documentation related to the data.
- `notebook/`: includes Jupyter notebook and Python files for processing crop data for each country.
- `public/`: holds the semi-final & final processed datasets in CSV, Parquet, and GeoPackage formats, ready for public use.

## Setting up the environment
To set up the environment using `environment.yml`, follow these steps:

1. Clone the repository:
    ```bash
    git clone https://github.com/HarvestStat/HarvestStat-Africa.git
    cd HarvestStat-Africa
    ```

2. Create the conda environment:
    ```bash
    conda env create -f environment.yml
    ```

3. Activate the environment:
    ```bash
    conda activate hvstat
    ```

4. Start your preferred development environment (e.g., Jupyter Notebook, VSCode):

## Current data status
HarvetStat currently contains subnational crop statistics for **`33`** countries.
<!-- (see [current data status per country](/docs/data_status_per_country.md)):</br> -->
- Admin-1 level: Angola, Burundi, Central African Republic, Chad, DRC, Ghana, Kenya, Lesotho, Liberia, Mali, Mauritania, Mozambique, Nigeria, South Africa, South Sudan, Sudan, Tanzania, Zimbabwe
- Admin-2 level: Benin, Burkina Faso, Cameroon, Ethiopia, Guinea, Madagascar, Malawi, Niger, Rwanda, Senegal, Sierra Leone, Somalia, Togo, Uganda, Zambia

<img src="./docs/current_status_map.png" alt="drawing" width="400"/>

## Data access
The data in this repository is available in the `public` folder in CSV and GeoPackage formats.

To access the data, download the files from the `public` folder.
- hvstat_africa_data_{version}.csv: The final processed crop statistics dataset.
- hvstat_africa_boundary_{version}.gpkg: Boundary data for subnational administrative units.

The version of the dataset is specified in the filename. The current version is `v1.0`.

The official release version is available on [Dryad - HarvestStat Africa](https://datadryad.org/dataset/doi:10.5061/dryad.vq83bk42w).

## Data structure
The dataset contains the following columns:

| Column Name             | Description                                                     |
| ----------------------- | --------------------------------------------------------------- |
| `fnid`                  | FEWS NET's unique geographic unit identifier                    |
| `country`               | Name of the country                                             |
| `country_code`          | ISO 3166-1 alpha-2 country code                                 |
| `admin_1`               | Name of the first-level administrative unit                     |
| `admin_2`               | Name of the second-level administrative unit (if applicable)    |
| `product`               | Name of the crop product                                        |
| `season_name`           | Name of the growing season                                      |
| `planting_year`         | Year when planting begins                                       |
| `planting_month`        | Month when planting begins                                      |
| `harvest_year`          | Year when harvesting ends                                       |
| `harvest_month`         | Month when harvesting ends                                      |
| `crop_production_system`| Type of crop production system (e.g., irrigated, rainfed, etc.) |
| `qc_flag`               | Quality control flag (0 = no flag, 1 = outlier, 2 = low variance)|
| `area`                  | Cropped area (hectares; ha)                                     |
| `production`            | Crop quantity produced (metric tonnes; mt)                      |
| `yield`                 | Crop yield (metric tonnes per hectare; mt/ha)                   |

For details, please see the paper in the [Citation](#citation) section.

## Citation
The data in this repository is available for free and unrestricted use. Users are encouraged to cite the following:

D. Lee, W. Anderson, X. Chen, F. Davenport, S. Shukla, R. Sahajpale, M. Budde, J. Rowland, J. Verdin, L. You, M. Ahouangbenoni, K. Davis, E. Kebede, S. Ehrmannk, C. Justice, and C. Meyer. (2024), HarvestStat Africa – Harmonized Subnational Crop Statistics for Sub-Saharan Africa. EarthArXiv, [https://doi.org/10.31223/X5M123](https://doi.org/10.31223/X5M123).

<details>
<summary>BibTeX</summary>
<pre>
@article{lee_eaxv2024,
  author       = {Lee, Donghoon and
                  Anderson, Weston and
                  Chen, Xuan and
                  Davenport, Frank and
                  Shukla, Shraddhanand and
                  Sahajpal, Ritvik and
                  Budde, Michael and
                  Rowland, James and
                  Verdin, Jim and
                  You, Liangzhi and
                  Ahouangbenon, Matthieu and
                  Davis, Kyle Frankel and
                  Kebede, Endalkachew and
                  Ehrmann, Steffen and
                  Justice, Christina and
                  Meyer, Carsten},
  title        = {{HarvestStat Africa – Harmonized Subnational Crop Statistics for Sub-Saharan Africa}},
  year         = {2024},
  journal      = {EarthArXiv},
  note         = {Preprint},
  doi          = {10.31223/X5M123},
  url          = {https://doi.org/10.31223/X5M123}
}
</pre>
</details>

## How to contribute
Contributions to this repository are welcome, including new data sources or improvements to the existing data. To contribute, please create a pull request with a clear description of the changes proposed.

## Contact 
- Please contact Donghoon Lee ([Donghoon.Lee@umanitoba.ca](Donghoon.Lee@umanitoba.ca) and Weston Anderson [Weston@umd.edu](Weston@umd.edu)) for any questions or collaborations.</br>
- Users are encouraged to [open an issue](https://github.com/HarvestStat/HarvestStat/issues) for questions, feedback, or bug reports.

## License
The data in this repository is licensed under the MIT License.
