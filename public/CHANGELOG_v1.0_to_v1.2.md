# HarvestStat Africa: v1.0 → v1.2 Changelog

## Crop statistics file

**Row counts:** 203,125 (v1.0) → 216,212 (v1.2) | Net +13,087 rows
**Changes:** 35,525 rows added · 22,438 rows removed · 2,939 rows with revised values (>5%)
**Countries affected:** Angola, Benin, Burkina Faso, Ethiopia, Lesotho, Malawi, Mozambique, Somalia, South Africa, South Sudan, Sudan, Zambia

---

## Boundary file

**Admin units:** 1,109 (v1.0) → 1,128 (v1.2) | Net +19 units
**Schema:** New `country_co` column added in v1.2 containing ISO 2-letter country codes (e.g. `AO`, `ET`) — present for all countries.
**Countries with changes:** 3

| Country | Change type | Detail |
|---|---|---|
| Ethiopia | Admin unit restructuring | 77 units removed (2014 delineation), 96 added (2021 delineation); net +19 units |
| DRC | Country name standardised | `DRC` → `Congo, The Democratic Republic of the`; FNIDs and admin names unchanged |
| Tanzania | Country name standardised | `Tanzania` → `Tanzania, United Republic of`; FNIDs and admin names unchanged |

Ethiopia's restructuring updates FNIDs from the `ET2014A…` series to `ET2021R…`. The regions are the same but subdivided more finely — Sidama is split out from SNNPR as its own region, several Oromia and SNNPR zones are disaggregated, and zone names are updated throughout (e.g. `Bench Maji` → `Bench Sheko`, `Argoba` becomes `Argoba Special Woreda`, `Gamo Gofa` is split into `Gamo`, `Gofa`, and others). Users joining the boundary file to the crop statistics file by FNID should use the updated Ethiopia FNIDs; the crop statistics file has been re-keyed to the 2021 delineation in v1.2.

---

## Crop statistics summary table

| Country | Change type | Years affected |
|---|---|---|
| Angola | New rows + value revisions | 2007–2017 |
| Benin | New rows only | 1995–2023 |
| Burkina Faso | New rows + removed rows + value revisions† | 1984–2023 |
| Ethiopia | New rows + removed rows | 1993–2022 |
| Lesotho | New rows only | 2023–2024 |
| Malawi | New rows only | 2024 |
| Mozambique | Removed rows only | 2002–2022 |
| Somalia | New rows + removed rows (re-ingestion) | 1995–2026 |
| South Africa | New rows + value revisions | 1979–2025 |
| South Sudan | New rows + removed rows | 2012–2022 |
| Sudan | Minor value revisions only (~5%) | 1975–2010 |
| Zambia | New rows only | 1980–2017 |

† Burkina Faso large % changes reflect production system restructuring, not corrections to underlying statistics.

---

## Angola
New crop coverage added for 2015–2017 (horticultural crops) and 2007–2009 (staples). Lemon and Mango removed for 2016–2017. Many shared rows show large value revisions indicating a data re-ingestion at revised subnational granularity rather than corrections.

| Crop | New years | Removed years |
|---|---|---|
| Cabbage, Carrots, Chili Pepper, Melon, Okras, Onions, Tomato, Watermelon | 2015–2017 | — |
| Green Bean | 2016–2017 | — |
| Potato, Rice, Soybean | 2007–2017 | — |
| Sweet Potatoes | 2017 | — |
| Lemon, Mango | — | 2016–2017 |

---

## Benin
Two types of additions: a forward extension to 2022–2023 for most existing crops, and two new crop series added across their full historical range. No rows removed.

| Crop | New years | Note |
|---|---|---|
| Most existing crops | 2022–2023 | Forward extension |
| Chili Pepper | 1995–2021 | New crop series |
| Cotton | 1995–2023 | New crop series |
| Tobacco | 1999–2010 | New crop series |
| Cashew (unshelled), Coffee | 2022–2023 | New crops |

---

## Burkina Faso
All major crops extended back to 1984. The 1984–2000 period appears in both added and removed rows because the production system classification was restructured for those years — old system-coded rows were replaced with revised ones. The large apparent value changes in the changed-rows analysis (thousands of %) are artifacts of this restructuring, not genuine corrections to crop statistics. Cotton also gains 2001–2008 and 2011–2012 which were absent in v1.0. Sorghum (Red) gains 2023.

---

## Ethiopia
Comprehensive reconstruction of the historical record. The update replaces prior v1.0 rows for most crops across 1998–2016 with new rows under a revised production system classification, and extends coverage back to 1993 and forward to 2021–2022. Six fruit crop series (Avocado, Lemon, Mango, Orange, Papaya, Pineapple) were removed entirely with no replacement.

| Category | Crops | New years |
|---|---|---|
| Major cereals | Maize, Sorghum, Teff, Millet, Barley, Wheat | 1993–2022 |
| Pulses & oilseeds | Fava Bean, Field Peas, Lentils, Grass Pea, Linseed, Rape, Neug, Sesame Seed, Fenugreek, Oats | 1995–2021 |
| Cash crops | Coffee, Chat, Groundnuts, Sugarcane, Hops | 1996–2021 |
| Vegetables & roots | Potato, Cabbage, Onions, Tomato, Beet, Taro, etc. | 2001–2021 |
| New crops | Beans (Red), Mung bean, Yams, Carrots | 2013–2021 |
| Removed entirely | Avocado, Lemon, Mango, Orange, Papaya, Pineapple | — |

---

## Lesotho
Small forward extension only. Five crops gain 2023; Maize, Sorghum, and Wheat additionally gain 2024.

---

## Malawi
Single new row: Maize 2024.

---

## Mozambique
Removals only — no new rows added. A broad set of crops lost scattered years between 2002 and 2022, with Virginia Peanut losing the most (2002–2022). Several crop series removed entirely: Ginger, Jute, Macadamia, Tea, Banana (2020).

| Crop | Removed years |
|---|---|
| Virginia Peanut | 2002–2022 |
| Maize, Rice | 2002–2020 |
| Cassava, Bambara groundnut, Beans (Rosecoco), Cowpea, Millet, Pigeon Pea, Sorghum | 2012–2020 |
| Cotton, Soybean, Sugarcane, Mung bean, Jute | 2015–2020 |
| Sesame Seed, Sunflower Seed | 2014–2015 |
| Ginger, Chili Pepper, Tobacco, Beans (mixed) | 2015 |
| Banana, Macadamia, Tea | 2020 |

---

## Somalia
Wholesale re-ingestion: old rows replaced across all affected crops. The crop `Pepper` was removed and replaced by `Chili Pepper`. Years extend to 2026 (Deyr season planted October 2024, harvesting March 2026 — the harvest year encoding is now corrected from the prior version). Years beyond 2024 should be treated with caution as they may represent incomplete seasons.

| Crop | New years | Removed years |
|---|---|---|
| Maize, Sorghum | 1995–2026 | 1995–2023 |
| Cowpea | 2003–2026 | 2003–2023 |
| Sesame Seed | 2005–2026 | 2004–2023 |
| Rice | 2008–2026 | 2008–2023 |
| Onions, Tomato | 2009–2026 | 2009–2023 |
| Groundnuts (In Shell) | 2012–2025 | 2012–2023 |
| Chili Pepper | 2011–2026 | — |
| Watermelon | 2011–2026 | 2011–2023 |
| Pepper | — | 2011–2023 |

---

## South Africa
Forward extension to 2023–2025 for all existing crops, plus Oats added as a new series (2013–2025). Shared rows show systematic yield corrections of 6–25% for Maize, Soybean, and Wheat across multiple years

| Crop | New years |
|---|---|
| Oats | 2013–2025 (new series) |
| Barley | 2016–2025 |
| Canola Seed | 2017–2025 |
| All other crops | 2023–2025 |

---

## South Sudan
Cereal Crops aggregate series added for 2013–2022. The 2012–2013 rows present in v1.0 were removed and replaced with corrected 2013 data.

---

## Sudan
No structural changes. Five crops show borderline value revisions of ~5% for scattered years between 1975 and 2010 (Sorghum, Millet, Sesame Seed, Sunflower Seed, Cotton (American)). These are within rounding tolerance and do not represent material corrections.

---

## Zambia
Large historical backfill with no removals. Most crops gain continuous national-level coverage from 1990 onward; Maize extends back to 1980. Several new crop series added.

| Crop | New years | Note |
|---|---|---|
| Maize | 1980–2017 | Earliest coverage in dataset |
| Beans (mixed), Millet, Rice, Sorghum, Soybean | 1990–2017 | |
| Sunflower Seed | 1991–2017 | |
| Sweet Potatoes | 1999–2017 | |
| Cowpea, Potato | 2002–2017 | |
| Bambara groundnut | 2005–2017 | New series |
| Cottonseed | 2005–2009 | |
| Wheat | 1990–1993, 2011, 2015 | |
| Pineapple | 2013 | New series |
| Sugarcane | 2011, 2015 | New series |
| Coffee | 2014 | |
| Cassava | 2014–2015 | |
| Velvet Bean | 2006 | New series |
