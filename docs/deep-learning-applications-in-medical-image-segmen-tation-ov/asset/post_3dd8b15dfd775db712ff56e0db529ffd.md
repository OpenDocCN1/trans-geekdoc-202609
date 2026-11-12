
## Table 7.1 Comparative analysis of the lung segmentation models.

| S. no. | References | Model | Modality | Dataset | Accuracy | DSC | JC | F1-sc |
|---|---|---|---|---|---|---|---|---|
| 01 | Yahyatabar and Javout (2020) | Dense U-Net | X-rays | JSRT MC | | 97.6, 97.9 | 95.3, 95.59 | |
| 02 | Arvind et al. (2023) | Enhanced U-Net | X-rays | JSRT MC Shenzhen | 93.87% | | | |
| 03 | Boudoukhani et al. (2023) | Attention-gated Residual DeepLabV3+ | | JSRT MC Shenzhen | | 98.03% | 96.14% | |
| 04 | Ghali and Akhloufi (2022) | Vision transformers | X-rays | JSRT MC Shenzhen | 97.47% | | | |
| 05 | Zhang et al. (2021) | Improved U-Net | CT | LIDC/IDRI | | 0.8623 | | |
| 06 | Punn and Agarwal (2022) | Hierarchical segmentation network | CT | “COVID-19 CT dataset, COVID-19 CT Lung and Infection Segmentation Dataset” | 95% | 81% | 89% | |
| 07 | Novikov et al. (2018) | Fully convolutional network (FCN) | X-rays | JSRT | | | 95% | |
| 08 | Sulaiman et al. (2023) | Deep convolutional neural networks | X-rays | MC Shenzhen | 0.97 | 0.93 | 0.96 | |
| 09 | Liu et al. (2022) | Improved U-Net | X-rays | JSRT MC Haut | 98.55, 98.94, 99.41 | 97.92, 97.82, 98.84 | 95.73, 95.55, 97.43 | |
| 10 | Islam et al. (2018) | U-Net based | X-rays | MC Shenzhen | | 98.6% | | |
| 11 | Ait Skourt et al. (2018) | U-Net based | CT | LIDC/IDRI | | 0.9502 | | |
| 12 | Hu et al. (2020) | Mask R-CNN | CT | | 97.68 | | | |
| 13 | Singh et al. (2021) | Deep LF-Net | X-rays | JSRT MC Shenzhen | 99.37%, 99.37%, 98.31% | | | |
| 14 | Ullah et al. (2023) | DED-CNN | X-rays | JSRT MC Shenzhen | | 97.60%, 97.67%, 95.68% | 95.50%, 95.48%, 91.84% | |
| 15 | Ghali and Akhloufi (2022) | Attention RegSeg | X-rays | JSRT MC Shenzhen | 95.69% | | | 95.6 |
| 16 | Munawar et al. (2020) | GAN | X-rays | JSRT MC Shenzhen | | 0.9740 | 0.943 | |
| 17 | Khanna et al. (2020) | Residual U-Net | CT | LUNA16, VESSEL12, HUG-ILD | 98.63, 99.62, 98.68 | | | |
| 18 | El Mansouri et al. (2022) | GAN | X-rays | JSRT | | 0.9778 | | |
| 19 | Kim and Lee (2021) | Self-attention DNN | X-rays | MC JSRT Shenzhen | | 0.982, 0.968, 0.954 | | |
| 20 | Liu et al. (2022) | Wavelet transformation | CT | Multimedia database of interstitial lung diseases (ilds) | 98.04% | 94.91% | | |
| 21 | Lyu and Tian (2023) | MWG-UNet | X-rays | JSRT Shenzhen | 95.28% | 92.31% | | 95.7 |
| 22 | Agnes et al. (2024) | Wavelet U-Net++ | CT | LIDC-IDRI | | 0.936 | 0.878 | |
| 23 | Pal et al. (2022) | Attention UW-Net | X-rays | NIH | | | | 95.7 |

## 7.5.1 Chest X-Ray Datasets

### 7.5.1.1 JSRT ("Japanese Society of Radiological Technology")

The “Standard Digital Image Database of chest radiographs” with and without lung nodules was created by the “Academic Committee of the Japanese Society of Radiological Technology” in 1998, (Shiraishi et al. 2000) supported by the Japan Radiological Society (JRS) and collaborated with healthcare facilities in the United States and Japan. JSRT stands as the most frequently used dataset with renowned usage in “nodule detection and lung segmentation research,” comprising “247 posteroanterior (PA) chest X-rays” with a “resolution of 2048×2048” pixels. Among these 154 CXR images are “with lung nodules” (54 benign and 100 malignant nodules) and “93 without nodules.” These CXRs are stored as PNG files with a 12-bit grayscale depth. In addition, the database includes patients’ details such as age, gender, diagnosis (benign or malignant), X and Y coordinates of nodules, and a basic diagram showing nodule location. Regarded as a valuable repository, this dataset has found widespread usage in various research studies focusing on the identification of lung nodules from chest X-rays. (Kaggle, 2020).

### 7.5.1.2 Montgomery County (MC) Dataset

The “Montgomery County (MC)” dataset is a collaborative effort between the “Department of Health and Human Services in Montgomery County, Maryland and US National Library of Medicine (USNLM).” The Montgomery dataset comprises labeled X-ray images captured in a frontal view. This data repository contains “138 posteroanterior (PA) chest X-rays” obtained through the tuberculosis (TB) screening program. Among these CXRs, 80 CXRs depict normal chest conditions without TB manifestations, while 58 exhibit indications of TB. The dataset is accompanied by ground truth masks corresponding to each X-ray image in the dataset. These masks are binary images that provide delineation of lung areas and aid in the identification of specific pulmonary regions within the X-ray images. Each CXR in the dataset is accompanied by clinical readings stored in text files (.txt), and individual ground truth masks are provided for both right and left lungs in the form of .png files. These X-ray images maintain high image quality, with a “resolution of 12 bits per pixel and a pixel size of 0.0875 mm”. (Kaggle, 2018).

### 7.5.1.3 Shenzhen Dataset

The Shenzhen dataset, created collaboratively by “USNLM and Shenzhen No. 3 People’s Hospital, Guangdong Medical College, China,” comprises 662 PA chest X-rays. Out of these, 326 CXRs depict normal cases, while 336 X-rays show manifestations of TB, including some pediatric anteroposterior (AP) X-rays. The dataset contains images of different sizes, with widths ranging from 1130 to 3001 pixels and heights from 948 to 3001 pixels. Most images are approximately 3K × 3K pixels in size. The CXR images are saved with the file extension “.jpeg” and were captured using a “Philips DR Digital Diagnostic System.” Only 566 ground masks are provided for these images. These images are notably high-resolution, boasting dimensions of 4020 × 4892 or 4892 × 4020 pixels. Each X-ray image within this dataset exhibits a grayscale depth of 12 bits, allowing for a comprehensive range of 4096 gray-scale levels for enhanced imaging. This repository serves as a precious asset for detailed chest imaging research and analysis due to its high-resolution images and the availability of corresponding masks for further analysis and identification of anatomical features.

### 7.5.1.4 Indian Dataset

The Indian dataset includes a total of 7470 medical images, corresponding to these images, 3955 detailed radiology reports are utilized for various medical applications or studies. The dataset is sourced from various hospitals affiliated with Indiana University. These hospitals likely contribute their medical images and associated reports to form this comprehensive dataset. These images and reports contribute to a comprehensive repository supporting diverse medical applications. Utilizing text-mining techniques, the dataset incorporates eight disease labels per image, enabling the association of multiple labels with individual images. This diverse labeling system facilitates image classification based on pathology, encompassing a wide range of medical conditions. The radiographs vary in dimensions from 1024 to 4248 pixels, both in width and height, initially existing in “Digital Imaging and Communications in Medicine (DICOM) format.” Later, these were converted to PNG format for enhanced accessibility and standardized usage. Researchers at the US National Library of Medicine have used this dataset for distinct studies, such as CXR view classification, (Xue et al. 2015) identification of image rotations, (Santosh et al. 2015) and detection of foreign objects in these images.

### 7.5.1.5 National Institutes of Health Chest X-Ray Dataset (NIH)

The NIH dataset, also referred to as “chest X-ray 14”, (Wang et al. 2017) is a significant repository comprising “112,120” CXR images annotated with “disease labels from 30,805 unique patients.” These labels were derived using “Natural Language Processing (NLP) techniques,” extracting disease classifications from the related radiological findings. This dataset encompasses 14 different thorax disease categories, along with an additional category indicating “no findings.” However, the absence of definitive ground truth masks posed a significant challenge. This dataset presents a broad spectrum of pathological conditions. By providing access to this dataset, this publication aims to equip scientists with resources to enhance algorithmic training for disease identification and diagnosis,
