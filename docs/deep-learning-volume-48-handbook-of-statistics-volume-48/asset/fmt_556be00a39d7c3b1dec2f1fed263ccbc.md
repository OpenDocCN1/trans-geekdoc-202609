
Here β is a bounded variable whose value is bounded between 0 and 1. Variables M and U represent the intensities of methylated and unmethylated probes in the array (`[Weinhold et al., 2016](#Ch006_107-168_S0169716122000578.xhtml#bb0385)`). β values of CpG sites of the genome of 608 low and high-grade glioma patients were considered in the DM matrix.

The Affymetrix SNP 6.0 (SNP6) array data were used to identify repeated genomic regions in the genome and calculate copy numbers of these repeats in TCGA-LGG and TCGA-GBM cohorts. Numeric copy number variation (CNV) of genes was estimated using the GISTIC2 pipeline (`[Mermel et al., 2011](#Ch006_107-168_S0169716122000578.xhtml#bb0255)`). CNVs were estimated for only protein-coding genes. Further threshold of Numeric CNVs of genes was implemented by a noise cutoff value of 0.3. The following criteria were applied to categorize the numeric CNV values to copy numbers gain, loss, and neutral states of a given gene.

1.  (i) Genes with CNV ≤ −0.3 are categorized as copy number loss and denoted by numerical value −1.

2.  (ii) Genes with CNV ≥ 0.3 are categorized as copy number gain and denoted by numeric value +1.

3.  (iii) Genes with −0.3 ≤ CNV ≤ +0.3 are categorized as neutral and denoted by the numeric value 0.

####  2.1.2: COVID-19 data

The present study utilized the state-level daily COVID-19 case data which was collected from the Ministry of Health and Family Welfare (MoHFW), Government of India from 1st April 2020 to 31st March 2022. In India, COVID-19 tests were conducted using RATs (Rapid Antigen Tests) and the RT-PCR (Reverse-Transcriptase Polymerase-Chain-Reaction) testing methodology. However, the RT-PCR test is more sensitive than the RATs for detecting the COVID-19 virus in the human body, whereas, RATs are more useful for understanding the disease spread and pro‑active health measures due to the shorter diagnosis time and inexpensive compared to the RT-PCR test.

####  2.1.3: Meteorological data

#####  2.1.3.1: Gridded meteorological data

The state-level daily meteorological parameters include specific humidity, average temperature, and maximum and minimum temperature data extracted from NCEP/NCAR reanalysis gridded data (`[Kalnay et al., 1996](#Ch006_107-168_S0169716122000578.xhtml#bb0190)`) (`[https://psl.noaa.gov/](https://psl.noaa.gov/)`). These meteorological parameters are utilized for the training of the multivariate LSTM model to predict COVID-19 cases in India. The rainfall data utilized for the prediction of crop yield was collected from the IMD (India Meteorological Department) gridded data during the period 1961–2016.

#####  2.1.3.2: Station-level meteorological data

The Council of Scientific and Industrial Research (CSIR), India has established several meteorological towers in different parts of the country for collecting some of the major metrological parameters. These towers are capable of collecting data at three different levels such as at 2, 20, and 30 m heights. We have predicted wind speed at New Delhi and Bengaluru stations set up by CSIR. Four different meteorological parameters such as temperature (T), pressure (P), humidity (H) and wind speed (V) at 30 min averaged intervals are collected from 20 m height towers from 2010 to 2013 for the study of wind speed prediction. [Fig. 1](#Ch006_107-168_S0169716122000578.xhtml#f0010) shows the sample data of daily wind speed (averaged from 2010 to 2013) measured at New Delhi and Bengaluru stations in India.

![Fig. 1 Annual Cycle of wind speed (m/s) at New Delhi and Bengaluru stations in India. The daily wind speed is averaged for the period 2010–13 and presented in the figure.](images/S0169716122000578/f06-01-9780443184307.jpg)

[Fig. 1](#Ch006_107-168_S0169716122000578.xhtml#B-f0010) Annual Cycle of wind speed (m/s) at New Delhi and Bengaluru stations in India. The daily wind speed is averaged for the period 2010–13 and presented in the figure.

#####  2.1.3.3: Crop production data

The rice production data for different Asian countries were collected from the “Food and Agriculture Organization” (`[FAO](http://www.fao.org/home/en/,%20n.d)`) from 1961 to 2016 to predict rice production in India.

####  2.1.4: Image data

The magnetic resonance images (MRI) of the human brain and histopathology images of glioma tissue samples (stained by Hematoxylin and Eosin) of TCGA-LGG and TCGA-GBM cohorts were used to construct deep convolutional neural network (CNN) models for predicting cellular/histopathological grades, molecular subtypes, mutations status of driver genes, and survival of glioma patients. Pre and post-contrast T1 weighted MR images and whole-slide histopathology images (WSI) of glioma patients were collected from The Cancer Image Archive (TCIA) (`[https://www.cancerimagingarchive.net/](https://www.cancerimagingarchive.net/)`). Metadata (e.g., tumor grades, molecular subtypes, survival) and somatic mutations of select cancer driver genes *EGFR* and *TP53* of all patients were also obtained from TCGA data portal (`[https://portal.gdc.cancer.gov/](https://portal.gdc.cancer.gov/)`). MRI and histopathology images of glioma patients with tumor grades, molecular subtypes, mutation status of *EGFR* and *TP53* genes, and overall survival (OS) data were utilized for training the CNN models. Given these criteria, MR and WS images of 1152 patients were finally considered for training and testing of the CNN models.

MR images were available in Digital Imaging and Communications in Medicine (DICOM) format (`[Guthrie et al., 2001](#Ch006_107-168_S0169716122000578.xhtml#bb0170)`). Dicom images are not machine-readable; hence these images were converted to png format, which was further passed through several filtering steps to eliminate any potential noise from image files. De-noising MR image is a crucial step for enhancing image quality without compromising the integrity of the whole image (`[Coupe et al., 2008](#Ch006_107-168_S0169716122000578.xhtml#bb0135)`). Different de-noising algorithms are available, such as Gaussian blur, Median blur, Anisotropic Diffusion Filter, Total Variation, etc. (`[Coupe et al., 2006](#Ch006_107-168_S0169716122000578.xhtml#bb0130)`). Literature evidence suggests that the non-local means (NL means) algorithm, based on the neighborhood filtering technique, outperforms the conventional filtering algorithm and increases the signal-to-noise ratio (SNR) in the MR image (`[Coupe et al., 2006](#Ch006_107-168_S0169716122000578.xhtml#bb0130)`). Following the de-noising step using the Fast NL means algorithm on the converted png image, all images were further resized to 128 × 128 pixels and labeled with tumor grades, molecular subtypes, *EGFR,* and *TP53* genes mutation status, and overall survival in months.
