
where, `p_0` denotes joint probability distribution of initial state of RBM network, `p_n` denotes joint probability distribution of RBM network after `n` (``~ ~ \`~~| ¹``).

probability distribution of RBM network at the ends of MCMC. Therefore, `CD_n` can be regarded as a measure location for `p_n` between `p_0` and `p_n`. It constantly assigns `p_0` to `p_n` and gets new `p_0` and `p_n`. The experiments show that `CD_n` will tend to zero and the accuracy is approximate of MCMC after `n < RBM` is shown in Figure 8.

We can get Equation (57) by training process of RBM using contrastive divergence:

(57)

```
Ö < # "
```

(58)

where, `μ` is the momentum.

The above discussion is based on the training of the parameters between hidden layers with one sample `x`. For unsupervised learning, we construct the deep architecture using all samples by inputting them one by one from layer `h0`, train the parameters between `h0` and `h1`. Then `h1` is constructed, the value of `h1` is calculated by `h0` and the trained parameters between `h0` and `h1`. We also can use it to construct the next layer `h2` and so on. The deep architecture is constructed layer by layer from bottom to top. In each time, the parameter space ``WK # ` \_{|`` layer. Accord to the `WK` calculated above, the layer `hk` is obtained as below for a sample `x` fed from layer `h0`:

(59)

For supervised learning, the DBM architecture is trained by `C` labeled data. The optimization problem is formulized as:

![Image 1606](img/index-348_1.jpg)

![Image 1607](img/index-348_2.png)

![Image 1608](img/index-348_3.png)

![Image 1609](img/index-348_4.png)

## EXPERIMENTS

### 1) Face Recognition Databases

We selected some typical databases of images, for example ORL Face Database, which consists of 10 different images for each of the 40 distinct individuals. Each people is imaged in different facial expressions and facial details under varying lighting conditions at different times. All the pictures are captured with a dark background and the individuals are in an upright and frontal position; the facial gestures are not identical, expressions, position, angle and scale are some different; The depth rotation and plane rotary can be `Ø {Á`.

For each face database as above, we randomly choose a part of images as training data and the remaining as testing data. In this `$ #Á` individual image as training data and the rest as testing data. At `\# '`.

All the experiments are carried out in MATLAB R2010b environment running on a desktop with `TM2 Duo CPU T6670 @2.20GHz` and `4.00 GB RAM`.

### 2) Relevant experiments

#### Experiment 1

In this experiment, we preprocessing and get the sample Figure 9 as following: Seeing eliminate most of noise interference.

#### Experiment 2

In this experiment, we make histogram equalization for. From Figure 10 and Figure 11 we can see: After histogram equalization, the distribution of image histogram is more uniform, the range of gray increases some and the contrast has also been stronger. In addition, the `\*! # $` illumination, expanded the representation range of pixel gray, improved the contrast of image, made the facial features more evident and is conducive to follow-up feature extraction and FR.

![Image 1610](img/index-349_1.jpg)

![Image 1611](img/index-349_2.jpg)

![Image 1612](img/index-349_3.jpg)

![Image 1613](img/index-349_4.png)

![Image 1614](img/index-349_5.png)

![Image 1615](img/index-349_6.png)

**Figure 9**?

**Figure 10**. Face images before histogram equalization versus after histogram equalization. (a) Original image; (b) Image after histogram equalization.

![Image 1616](img/index-350_1.jpg)

![Image 1617](img/index-349_2.png)

![Image 1618](img/index-350_3.png)

![Image 1619](img/index-350_4.png)

**Figure 11**. Histogram of original image versus histogram of image after histogram equalization. (a) Histogram of original image; (b) Histogram of image after histogram equalization.

#### Experiment 3

In this experiment, we employ multi-scale two-dimensional wavelet transform to generate the initial geometric features `'` as following: From Figure 12 we can see: Although for compression of images (or dimensionality-reduced), LL sub-graph information capacity has decreased some, but still has very high resolution and the energy of wavelet domain did not decrease a lot. LL sub-graph can be well made for the follow-up feature extraction.

#### Experiment 4

In this experiment, we extract features respectively with PCA and 2D-PCA and compare their effects as following:

`?? {`

contribution rates `' +`

principal components contribution rates extracted with PCA. From Figure 14 we can see when the principal components are extracted for 20, the principal component contribution rate of 2D-PCA is greater than 90%, while the principal component contribution rate of PCA is less than 80%.

Accordingly, 2D-PCA can use less principal component to better describe the image than PCA.

![Image 1620](img/index-351_1.jpg)

![Image 1621](img/index-351_2.jpg)

![Image 1622](img/index-351_3.jpg)

![Image 1623](img/index-351_4.png)

![Image 1624](img/index-351_5.png)

![Image 1625](img/index-351_6.png)

**Figure 12**. Multi-scal two-dimensional wavelet transform.

**Figure 13** # ordinate: energy value.

**Figure 14**. Principal component accumulation contribution rate. Abscissa: principal components; ordinate: total energy value.

![Image 1626](img/index-352_1.jpg)

![Image 1627](img/index-352_2.png)

![Image 1628](img/index-352_3.png)

![Image 1629](img/index-352_4.png)

Figure 15 is the comparing results image of reconstruction with the feature respectively extracted with PCA and 2D-PCA. We can see that the images of reconstruction by 2D-PCA are clearer than the images of reconstruction by PCA when extracting same number of principal components. The reconstruction face extracted 50 principal components by 2D-PCA is almost same clear with the original image. 2D-PCA has better effect than PCA.

#### Experiment 5

In this experiment, we compare the recognition rate of the methods respectively based on PCA + BP, WT + PCA + BP, PCA + HBPNNs and WT + PCA + HBPNNs. The experiment is repeated many times and takes the average recognition rate. The experimental results are shown in Table 1. As shown in Table 1, Recognition rates of HBPNNs are ``\# \` `` HBPNNs) recognition rates of the methods based on WT + PCA are higher than them based on PCA.

#### Experiment 6

This experiment compares the recognition rate of the methods respectively based on WT + 2D-PCA + RBF and WT + 2D-PCA + HRBFNNs. The experiment is repeated for many times and takes the average recognition rate. The experimental results are shown in Table 2. As shown in Table 2, Recognition rates of HRBFNNs are improved very greatly being compared to RBF. Therefore, HRBFNNs being used for FR is more feasible.

#### Experiment 7

`¶~ # ¨ £ ++ ¥` "One-Against-the Rest" for the experiment and choose the method with ``\# ¶~<``. The experiment is repeated for 20 times and takes the average recognition rate. The experimental results are shown in Table 3.

![Image 1636](img/index-354_1.png)

![Image 1637](img/index-354_2.png)

![Image 1638](img/index-354_3.png)

![Image 1639](img/index-354_4.png)

![Image 1640](img/index-354_5.png)

![Image 1641](img/index-354_6.png)

As shown in Figure 16, the recognition effect of MCDFC is always not lower than the average level of other three kinds of classifiers and in almost all cases the effect of MCDFC is optimal.

To eliminate the error of single experiment and greatly reduce the random uncertainty, Table 5 lists the average recognition rates of each ``# ' \`~?|Ç#¯+¯?+¶~``.
