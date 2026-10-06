Even though this baby was not born preterm, the corresponding image (Fig. 6.5, right) shows that this baby has more CSF, similar to preterm babies, which may be the reason why it was assigned to the preterm cluster.

#  6.3.4 Exercises

+   1. The file `structures_first_second_scan.csv` contains volumes of 86 brain structures calculated from 36 MRI scans of preterm babies. Some of these scans were acquired shortly after birth in the preterm period (GA<37) and others at term equivalent age (GA≥37). Perform spectral clustering of the volumes into two clusters to identify which scans were acquired at preterm period and at which term-equivalent age. Display the clustering result.

+   2. The file `babies.csv` contains the affinity matrix of pairwise similarities calculated using NCC, as described in Sect. 6.3.3. Perform 3D spectral clustering of the babies into three clusters and display similarly to Fig. 6.6, left. Use code from Sect. 6.3.3. Display the first two coordinates of the embedded space color coded by gestational age at birth (GAB), similarly to Fig. 6.6, right. You can find the GAB in the file ages.csv.

3 The skeleton code and datasets for exercises 1 and 2 are available from github.com/MachineLearning-BiomedicalApplications/notebooks.