![](bbox=[0.286, 0.104, 0.725, 0.262])

Figure 7.10 The Pavia Center image and the ground-truth labels for each pixel. The Pavia Center set has 1.2 million samples. The DBN-based classification of each sample contains 10.9 million operations, and the Zynq7100-based DANoC achieves 2036 effective GOPS at 1.9 watts power consumption.

| Datasets | Bands | Samples (million) | Features | Classes |
|---|---|---|---|---|
| Indian Pines | 224 | 0.02 | 2016 | 16 |
| Salinas | 224 | 0.11 | 2016 | 16 |
| Pavia University | 103 | 0.37 | 927 | 9 |
| Pavia Center | 102 | 1.20 | 918 | 9 |

dataset, which contains 1.2 million samples. Each pixel in the image is recorded with 102 spectral bands covering the wavelengths from 401 nm to 889 nm. The goal of classification is determining nine labels associated with each pixel.

Our experiments examine four well-known datasets of hyperspectral images (Table 7.1). All the examined datasets are downloaded from the hyperspectral website [32]. The scene of the India Pines is gathered by the AVIRIS sensor and consists of 21025 samples with 224 spectral reflectance bands in the wavelength ranging from 0.4 × 10−6 to 2.5 × 10−6 meters. The label of each pixel falls into sixteen classes. The Salinas dataset is collected by the 224-band AVIRIS sensor over the Salinas Valley, California, and is characterized by high spatial resolution (3.7-meter pixels). The area covered comprises 11.11 thousand samples of 16 classes. Similar to the Pavia Center data set, the Pavia University set has nine classes and 0.37 million samples recorded with 103 spectral bands.

Differently from traditional technologies, the hyperspectral imaging can get the spatial and spectral data simultaneously, resulting in high-dimensional samples. For practical remote sensing applications, the number of labeled training samples for each class is usually less than a few hundreds.