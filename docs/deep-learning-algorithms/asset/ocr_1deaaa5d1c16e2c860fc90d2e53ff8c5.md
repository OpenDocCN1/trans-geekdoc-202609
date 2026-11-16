# Data Description

In our experiments, we experimented and validated the proposed framework with AVIRIS and ROSIS hyperspectral datasets. AVIRIS hyperspectral data 92AV3C was obtained by the AVIRIS sensor in June 1992. ROSIS hyperspectral datasets were gathered by a sensor known as the reflective optics system imaging spectrometer (ROSIS-3) over the city of Pavia, Italy. In particular, we employed the Indian Pines dataset, which depicts Indiana and consists of 145 × 145 data size and 224 spectral bands in the wavelength range 0.4 to 2.510^-6 meters. It contains a total of 16 categories, as shown in Table 1. Its true mark is shown in Figure 2. The other datasets we employed are the Pavia University datasets, whose number of spectral bands are 102. Nine land cover classes are selected, which are shown in Figure 3. The numbers of samples for each class are displayed in Table 2.

# Table 1. Sixteen classes of Indian Pines dataset

| Class code | Ground object class | Number of training samples | Number of testing samples |
|---|---|---|---|
| C1 | Alfalfa | 30 | 24 |
| C2 | Corn-notill | 734 | 700 |
| C3 | Corn-min | 434 | 400 |
| C4 | Corn | 134 | 100 |
| C5 | Grass/Pasture | 297 | 200 |
| C6 | Grass/Trees | 397 | 300 |
| C7 | Grass/pasture-mowed | 16 | 10 |
| C8 | Hay-windrowed | 289 | 200 |
| C9 | Oats | 10 | 10 |
| C10 | Soybeans-notill | 538 | 430 |
| C11 | Soybeans-min | 1268 | 1200 |
| C12 | Soybean-clean | 314 | 300 |
| C13 | Wheat | 112 | 100 |
| C14 | Woods | 694 | 600 |
| C15 | Bldg-Grass-Tree-Drives | 190 | 190 |
| C16 | Stone-steel towers | 50 | 45 |

For investigating the performance of the proposed methods, experiments were organized step by step. The influence of the convolution kernel size and the depth of the network on the classification results was first analyzed. Then, we verified the performance of exponential momentum training algorithm. Finally, classifications based on CNN framework were conducted.