# 108 Transforming Healthcare

Voeia et al. investigated the use of pre-trained convolutional neural networks with residual connections (ResNet) and image-processing techniques to identify ACL injuries and classify tear levels [21]. Their adapted ResNet 3D volumes created from 2D image slices. The approach achieved peak accuracies of 97.15% with a custom split, 96.32% through Monte Carlo cross-validation, improving three-class classifier performance by 7% in raw accuracy.

Cedeno-Moro et al. introduced a framework using stacked autoencoders (SAE) for analyzing ground reaction force (GRF) signals from the GaitRec database [22]. The analysis identifies features for knee ligament ruptures and classifying their severity as high, mid, or mild. The process includes two stages: detecting the injury and evaluating features for severity classification. The framework achieved 87% accuracy and 90% F1-Score for detecting ligament ruptures, as well as 86.5% accuracy with 87% F1-Score for severity classification.

In conclusion, a number of techniques for the automatic categorization of ACL rupture in MRI have been proposed from various sources used in this research. Furthermore, many methods were employed to calculate the efficacy of the models, which have shortcomings and require a lot of time even when they are automated. The fastest detection of knee problems is a tough endeavor due to the heterogeneity in MR images.

# 5.3 DATASET DESCRIPTION

From 2006, the Clinical Hospital Centre Rijeka in Croatia collected the KneeMRI dataset prospectively from examination reports performed on a Siemens Avanto 1.5T MR scanner using the proton density-weighted suppression technique [23]. Around 917 12-bit grayscale volumes of the left or right knee make up the dataset. Out of 172 partial ruptures (18.8%), 55 entirely ruptured (6.0%), and 690 healthy patients (75.2%) made up the collection of 917 knee datasets. A double-blind method was used to diagnose the ACL in every volume recording. Specifically, each volume record labeled as either (1) healthy, (2) partially injured, or (3) entirely ruptured. From the original volumes, a broader rectangular region of interest (ROI) was manually extracted and is marked.

# 5.4 METHODOLOGY

# 5.4.1 Feature extraction using Gray-Level Co-occurrence Matrix

An essential step in image processing and computer vision is feature extraction, which involves locating and displaying unique structures in a picture.