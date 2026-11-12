![](bbox=[0.187, 0.096, 0.875, 0.352])

Figure 18.8 Testing stage using Shearlet transform.

Transform-based texture classification system is presented in Figure 18.3. It contains of two parts; the training part and the testing part.

The training part for AHESTBTCS is shown in Figure 18.7. The image datasets are categorized into training and testing datasets. The image samples from testing datasets are applied to adaptive histogram equalization block to get an enhanced Image. This is then applied to the Shearlet Transform block to obtain 49 Shearlet coefficients. Two feature descriptors, norm-1 (mean) and norm-2 (Standard deviation), are extracted from these Shearlet coefficients. The system is learned using minimum distance classifier and SVM.

The characteristics are deposited in the library for forthcoming reference.

The testing phase for AHESTBTCS is shown in Figure 18.8. For MDC, the attributes measured during the training phase are matched with features stored in the feature library. For SVM, during the training phase, the classification is done by labels assigned during testing.

# 18.5 Result and Discussion

Our experiment uses MATLAB 2021. MATLAB is interactive and uses arrays without dimensions. Experimental results are evaluated and analyzed.

# 18.5.1 Experimental Dataset

The experiments were conducted with six different datasets. Brodatz-13, Brodatz-30, Brodatz-112, KTH–TIPS, KTH–TIPS2-a, and CURet datasets. From Brodatz-112 datasets, 13 images have been taken for basic selection, like the number of levels and filter size selection. Brodatz-13 and Brodatz-30 datasets, each texture sample has been partitioned into 4 and 16 subsamples. The Brodatz-112, KTH – TIPS, KTH – TIPS2-a, and CUrRet data set has several classes, and each image belongs to the same types of texture images. The variation between statistical features is very small; hence, these dataset images are divided by