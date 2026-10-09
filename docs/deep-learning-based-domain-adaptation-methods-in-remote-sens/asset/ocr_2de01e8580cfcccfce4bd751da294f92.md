# TABLE V: The representative benchmark datasets along with their detailed information for different DA-RSCls task.

| Dataset | Image Size | Resolution | Location/Source | Imaging Mode | Available Date | Categories |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Hyperspectral Optical Image (HSI) Dataset** | | | | | | |
| Houston2013 [224] | 349 x 1905 | 2.5m | University of Houston campus and its neighboring area, USA | HSI, LiDAR | 2013 | 15 |
| Houston2018 [225] | 601 x 2384 | 0.5m ~ 1m | University of Houston campus and its neighboring area, USA | HSI, LiDAR | 2018 | 20 |
| Pavia University | 610 x 340 | 1.3m | Pavia, Northern Italy | HSI | 2003 | 9 |
| Pavia Center | 1096 x 715 | 1.3m | Pavia, Northern Italy | HSI | 2003 | 9 |
| Botswana May1$^{2}$ | 1496 x 256 | 30m | Okavango Delta, Botswana | HSI | 2001 | 9 |
| Botswana June$^{2}$ | 1496 x 256 | 30m | Okavango Delta, Botswana | HSI | 2001 | 9 |
| Botswana July$^{2}$ | 1496 x 256 | 30m | Okavango Delta, Botswana | HSI | 2001 | 9 |
| HyRank: Denil [226] | 1376 x 176 | 30m | Athens | HSI | 2018 | 14 |
| HyRank: Loukia [226] | 945 x 176 | 30m | Athens | HSI | 2018 | 14 |
| KSC$^{3}$ | 512 x 614 | 18m | Kennedy Space Center, Florida, USA | HSI | 1996 | 13 |
| Hanzhou [227] | 500 x 230 | 30m | Hanzhou and Shanghai, China | HSI | 2002 | 3 |
| Shanghai [227] | 1600 x 230 | 30m | Hanzhou and Shanghai, China | HSI | 2002 | 3 |
| Indian Pines [228] | 145 x 145 | 20m | North-Western Indiana, USA | HSI | 1992 | 16 |
| Salinas$^{a}$ | 512 x 207 | 3.7m | Salinas Valley, California, USA | HSI | 1998 | 16 |
| **Aerial and Satellite Optical Image Dataset** | | | | | | |
| AID [1] | 600 x 600 | 0.5m ~ 8m | From Google Earth | R-G-B | 2017 | 30 |
| NWPU [2] | 256 x 256 | 0.2m ~ 30m | From Google Earth | R-G-B | 2016 | 45 |
| UC-Merced [229] | 256 x 256 | 0.3m | National Urban Area, USA | R-G-B | 2010 | 21 |
| WHU-RS19 [230], [231] | 600 x 600 | 0.5m | From Google Earth | R-G-B | 2012 | 19 |
| RSSCN7 [232] | 400 x 400 | 0.5m | From Google Earth | R-G-B | 2015 | 7 |
| PatternNet [233] | 256 x 256 | 0.6m ~ 4.7m | US Cities From Google Earth | R-G-B | 2018 | 38 |
| **SAR Dataset** | | | | | | |
| SAMPLE [234] | 128 x 128 | 0.3m | - | SAR | 2019 | 10 |
| FUSAR-Ship [235] | 512 x 512 | up to 1m | From Gaofen-3 (GF-3) | SAR | 2020 | 15 |
| OpenSARShip [236] | 30 x 30 ~ | 1m | From Sentinel-1 | SAR | 2017 | 17 |
| OpenSARShip 2.0 [237] | 120 x 120 | ~ 10m | From Sentinel-1 | SAR | 2017 | 16 |

across 38 categories. Each category has 800 samples (256 \times 256 pixels) of US cities collected from Google Earth.

In domain adaptation experiments, aerial and satellite optical image datasets such as AID [1], NWPU-RESISC45 [2], UC-Merced [229], WHU-RS19 [230], [231], RSSCN7 [232], PatternNet [233] are used by selecting shared categories and treating them as source and target domains for each other.

**SAMPLE Dataset** [234] contains 1,345 paired synthetic and measured SAR images across 10 vehicle types, generated under matched imaging parameters from the MSTAR dataset$^{1}$. Synthetic and measured images are respectively produced using CAD models and real SAR captures.

**FUSAR-Ship Dataset** [235] comprises over 5,000 high-resolution ship chips cropped from 126 GF-3 scenes. It introduces an extensive SAR ship taxonomy with 15 categories and 98 subcategories, enabling comprehensive development, evaluation, and benchmarking of ship recognition algorithms.

**OpenSARShip Dataset** [236] is a large-scale SAR ship detection benchmark built from Sentinel-1 imagery. It contains 11,346 ship chips from 41 SAR scenes covering 17 AI-defined ship types with detailed subtype annotations. This dataset is valuable for detection, fine-grained classification as well as domain adaptation research.

**OpenSARShip 2.0 Dataset** [237] expands on its predecessor by offering 34,528 SAR ship chips extracted from 87 Sentinel-1 images. It offers multiple data formats, including original, grayscale, pseudo-color, and calibrated versions, supporting deeper analysis of ship targets in SAR imagery.

# 2) Benchmark Datasets for DA-RS2Seg

For DA-RS2Seg, the benchmark datasets (Tab. VI) mainly comprise HR aerial and satellite optical imagery, offering fine-grained spatial details suitable for semantic segmentation. These datasets feature diverse geographic regions and acquisition conditions, enabling comprehensive evaluation of domain adaptation methods.

**ISPRS Dataset** [8] offers pixel-level annotations across 6 land-cover categories and includes Potsdam and Vaihingen datasets. Potsdam contains 38 VHR orthophotos (6000 x 6000 pixels) in IR-R-G, R-G-B, and R-G-B-IR modes, while Vaihingen has 33 orthophotos (~2000 x 2000 pixels) in IR-R-G mode. The domain adaptation segmentation experiments are conducted between the Potsdam and Vaihingen datasets.

**LoveDA Dataset** [6] provides 5,987 VHR remote sensing images (1024 x 1024) from Nanjing, Changzhou, and Wuhan, covering both urban and rural environments. It spans urban and rural domains to evaluate model generalization across diverse geospatial features.

**CITY-OSM Dataset** [7] is an urban-focused dataset that provides pixel-level annotations for cities such as Berlin, Chicago, Zurich, Paris, and Tokyo. It highlights key urban elements with 3 categories: “background”, “road”, and “building”.

**WHU Dataset** [238] delivers extensive pixel-level annotations for building extraction, including aerial and satellite imagery. The aerial subset contains 8,189 RGB images from New Zealand with 0.3 m resolution. The Satellite II subset comprises 17,388 RGB patches from East Asia with 2.7 m resolution. Both subsets provide diverse building types and are available for domain adaptation experiments.

**BLU Dataset** [239] is collected by the Beijing-2 satellite