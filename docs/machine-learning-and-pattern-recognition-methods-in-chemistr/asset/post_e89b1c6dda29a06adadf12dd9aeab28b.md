
## The analytical/measurement sources of multivariate errors

in-class and most probable class (Fig. 5.6). When viewed through the lens of probability, the SIMCA models (both SNV and PLS-DA) indicated a 0% probability that any of the pixels contained the spectrum ABS.

SIMCA is based on PCA of the reference ABS and PCA of the sand class. There is little variation between the spectra that arises from the reference plastic. As such, the spectra of the microplastic need to resemble a certain extent to the spectra of the reference ABS in order to be classified as such. Sand, meanwhile, is a heterogeneous matrix with a great deal of variation and with its own NIR multiple fingerprints. As we observed in PCA, the spectra of sand influence the spectra of the pixels containing the microplastic and lead to increased differences between their spectra and the reference ABS. The samples, or pixels of the image, in this case, are projected into the PCA spaces of each sand and reference ABS. Because of the influence of sand on the spectra of the pixels containing the microplastic, they are not similar enough to the ABS class to be characterized as in-class.

## 3.6 PLS-DA

On the contrary to what could be expected, partial least-squares discriminant analysis (PLS-DA) also proved ineffective in locating the ABS particle. Even clusters of pixels were found to be in-class for ABS by the PLS-DA model based on SNV preprocessed spectra (Fig. 5.7). The map of probability indicates a high probability that each cluster corresponds to the ABS class. As the sample is known to contain one single particle of ABS, this indicates that at least 10 of the clusters represent false positives.

The PLS-DA model based on the first-derivative preprocessed spectra did not successfully locate the ABS microparticle. Instead of finding false positives, this model did not characterize any pixels as ABS.

## 4. Spectral insights on the problem

The unsuccessful results obtained led to a more accurate observation of the spectral signatures of the ABS particle and sand. Taking advantage of the fact that the approximate location of the microparticle was known, and the spectral peaks of ABS, the hyperspectral image was cropped around the microparticle and the area of the peak between 1100 and 1200 nm was calculated. The results are displayed in Fig. 5.8, left. In this manner, the microparticle was easily identified. The number of pixels highlighted in the X direction of the image is low compared to the Y direction. Therefore, in order to operate better, the hyperspectral

![](img/1aed977a858463e62fc6af1793e4677c_119_0.png)
![](img/1aed977a858463e62fc6af1793e4677c_119_1.png)
![](img/1aed977a858463e62fc6af1793e4677c_119_2.png)
![](img/1aed977a858463e62fc6af1793e4677c_119_3.png)
![](img/1aed977a858463e62fc6af1793e4677c_119_4.png)
![](img/1aed977a858463e62fc6af1793e4677c_119_5.png)
![](img/1aed977a858463e62fc6af1793e4677c_119_6.png)
![](img/1aed977a858463e62fc6af1793e4677c_119_7.png)

Fig. 5.6 SIMCA model based on SNV preprocessed spectra in the top of the figure, and based on the first-derivative preprocessing in the bottom of the figure. 

### Most Probable class (SNV model)
### In class (SNV model)
### Probability ABS (SNV model)
### Probability SAND (SNV model)

ABS = Black
Sand = White

ABS = Black
Sand = White

![](img/1aed977a858463e62fc6af1793e4677c_120_0.png)
![](img/1aed977a858463e62fc6af1793e4677c_120_1.png)
![](img/1aed977a858463e62fc6af1793e4677c_120_2.png)
![](img/1aed977a858463e62fc6af1793e4677c_120_3.png) 

### Most Probable class (1D model)
### In class (1D model)
### Probability ABS (1D model)
### Probability SAND (1D model)

ABS = Black
Sand = White

ABS = Black
Sand = White

![](img/1aed977a858463e62fc6af1793e4677c_120_4.png)
![](img/1aed977a858463e62fc6af1793e4677c_120_5.png)
![](img/1aed977a858463e62fc6af1793e4677c_120_6.png)
![](img/1aed977a858463e62fc6af1793e4677c_120_7.png)

Fig. 5.7 PLS-DA model based on SNV preprocessed spectra in the top of the figure, and based on the first-derivative preprocessing in the bottom of the figure.

![](img/1aed977a858463e62fc6af1793e4677c_121_0.png)

**Fig. 5.8** Left, normalized area of the peak between 1100 and 1200 nm. Middle, a resized hyperspectral image of the same area. Right, spectral signatures (raw and SNV) of the spectra colored according to degree seen in the middle.

image was rescaled in both directions (using bicubic interpolation). By doing so, the spectral resolution is not affected since the neighbor pixels are interpolations of the real pixels. Nevertheless, a better spatial resolution is obtained (Fig. 5.8).

Observing the raw spectra of the selected area (Fig. 5.8), it can be observed how the scattering of the pixels containing sand is much larger than the scattering of the pixels containing any trace of ABS. When the scattering is corrected (with SNV), it looks evident that the signal of the ABS in the pixels belonging to the microparticle is several degrees smaller than the signal of the pure plastic. The spectra of sand influence the spectra of the pixels containing the microplastic and leading to increased differences between their spectra and those of reference ABS.

These observations, together with the previous results, point to answers to the questions posted at the very beginning of this chapter. Not only does the chemometric strategy play a fundamental role, it is of utmost importance to be aware of the effects of the chemometric strategy, the nature of the microparticle, the nature of the background, and the suitability of the instrument:

- The instrument used in this study might not be the most adequate for this task. Better said, the limit of detection (spatial and spectral) of the instrument was not good enough.
- It might also be that the chemometric strategies were not the most adequate ones. This opens up endless space for improvement. Nevertheless, the chemometric strategy is strongly linked to the database quality that is used. In this case, the strategy used for building the database is the most common strategy. This suggests that any spectrum in the sample should resemble a certain degree to the spectra in the library.
- It has been demonstrated that the multicomponent character of the sand (surroundings of the microparticle) also plays a fundamental role, especially if the NIR beam penetrates the microparticle and if the reflection intensities of the sand are much larger than the reflection intensity of the microparticle.
- The microparticle is composed by the same material as the pellets used for building the database. Moreover, microparticles were measured at the same time and under the same conditions. Nevertheless, the spectrum of the microparticle is much smaller than the spectrum of the pure plastic. This demonstrates that there is a strong interaction between the spectra of the microparticle and the scattering effects of the spectra of the sand.

## 5. Future work

NIR-HSI is gaining traction as a feasible technique for the detection and classification of microplastics directly in sand, soil, and marine sediments, which is an exciting prospect given the labor-intensive nature of separating microplastics from heterogeneous solid matrices. Given that this is a relatively new application of NIR-HSI, it is important to understand the limits and uncertainty associated with it. The results obtained clearly indicate that:

- (1) The NIR radiation penetrates the microparticle, suggesting a “translectance” effect between the sand and the plastic. This not only amplifies the signal of the microplastic, but also amplifies the signal of the sand, which appears to have high reflectivity power. The small size of the microparticle, together with its low thickness, suggests that even the spectra located in the middle of the microparticle suffer from the high influence of the spectra of the sand.
- (2) The spectra of the edges of the microplastic are certainly highly affected by the scattering of the sand. This suggests uncertainty in the characterization of those pixels as microplastics, creating an uncertainty boundary that must be further studied.

As before, this work is an introduction to a more complex topic where different theories and algorithms will be tested to calculate the spatial and spectral limits of detection.

## Acknowledgments

This work has been developed with the support of the Spanish Ministry of Science and Innovation through projects PID2020–116885RB-I000 and ELKARTE21/50 Investigación estratégica de las propiedades, aplicaciones y efectos de los nanomateriales poliméricos.
