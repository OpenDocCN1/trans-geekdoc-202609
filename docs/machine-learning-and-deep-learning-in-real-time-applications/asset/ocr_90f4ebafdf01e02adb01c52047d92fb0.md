# Deep Convolutional Neural Network-Based Analysis for Breast Cancer Histology Images

# Data Pre-Processing and Augmentation

The extent of H&E the tissue was normalized as described in Algorithm 1 (Macoeno et al., 2009) to retrieve microscopy images which enables for better quantitative analysis and for all images performing 50 random colour augments. (Ruifrok, & Johnston, 2001) the amount of H&E asaccomodied by the RGB colour of the tissue and the H&E colour, multiplying the H&E size of each pixel's two random variables [0.7, 1.3]. Additionally, in experiments, using diverse image criteria, the original 2048 × 1536 pixels would be reduced to half 1024 × 768 pixels. Extracting random crops of two sizes: 800 × 800 and 1300 × 1300 and the crops from downscaled as 400 × 400 pixels and 650 × 650 pixels. Recently, it has been found that downscaled images are sufficient. So that each image is represented by 20 crops. Then the crops are encoded into 20 descriptors. Finally, a set of 20-descriptors is combined into a single descriptor by 3-norm pooling (Boureux, Ponce, & LeCun, 2010). The overall pre-processing pipeline is depicted in Figure 4

Algorithm 1. Normalizing H&E stained on the tissue for obtaining stain vectors.

```
Input: RGB to OD
```

+   1. Convert RGB to OD
2. Remove data with OD intensity less than β
3. Calculate SVD on the OD tuples
4. Create plane from SVD directions corresponding to the two largest singular values
5. Project data onto the plane, and normalize to unit length
6. Calculate angle of (α and (100 - α) percentiles) of the angle
7. Find robust extremes

+   8. Convert extreme values back to OD space

Output: Optimal Stain Vectors

Figure 4. Process flow of Feature Extraction

![](bbox=[0.147, 0.725, 0.852, 0.903])