It should be noted that the AUs labeled by each database were different. Hence, comparison between posed and spontaneous images was not possible for all databases. The only comparison would be between DISF and B-DFE, however, B-DFE is a 3D image database and features extracted from those images DISF, which are 2D images. A comparison between those two would not be a fair comparison. The feature vector of a 2D image was in the form [width, height, 3] and the feature vector in the 3D image dataset was of the form [width, height, depth, 3], i.e., both representations would be different and not comparable. A possible way to perform feature extraction by passing 3D volumes through a pre-trained 3D network/algorithm, or to perform 2D feature extraction on each slice of the volume and combine the features for each slice, using PCA to reduce the dimensionality. However this would impact the accuracy. Therefore, such a comparison was not presented.

# 4. Results

# 4.1. Recognition and Reliability Measures

Recognition rate and the Intra-Class Correlation (ICC) values were evaluated to evaluate the proposed AU intensity measurement in our study. The statistical index, i.e., the ICC has a range from 0 to 1.

```
ICC = \frac{BMS - EMS}{BMS + (k-1) \times EMS} (5)
```

```
EMS = \frac{(k-1) \times (n-1)} (6)
```

```
BMS = \frac{BSS}{n-1} (7)
```

It is also the measure of conformity for the data set since it has multiple targets. This study is basically we n participants are being judged by k number of judges. In our study, we assume n = 6 and k = 2. The purpose of using ICC is because it is preferred over the Pearson correlation between measurement and judges. The ICC shows the proportion of total variance between the targets. Here, BMS = Between Mean Squares, EMS = Residual Mean Squares which are defined by the ANOVA (Analysis of Variance).

# 4.2. Result Analysis Based on Intensity of Emotions

The previous section discusses the feature extraction techniques implemented for measuring AU intensities in facial emotions. The techniques implemented include the LBP, Histogram of Oriented Gradient Features, and Gabor Features. These are followed by classification techniques such as Support Vector Machine, Random Forest and Nearest Neighbor Classifiers. Given all the observations, we implement the network for measuring the intensity of emotion recognition for each AU. The results are present in Table 3.

As shown in Table 3, the best results were achieved with the LBP with the nearest neighbor classifier using all three features. This is because it models static relationships between the AU intensities. All the values in the table are percentage accuracy in detection. AUs which were not present for certain cases, have been indicated as NA (Not Applicable) while zero indicates that the AU was present, but accuracy was not recognized at all.