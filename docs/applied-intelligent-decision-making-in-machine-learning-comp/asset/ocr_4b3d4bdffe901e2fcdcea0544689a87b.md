# Applied Intelligent Decision Making in Machine Learning

![](bbox=[0.125, 0.083, 0.875, 0.413])

**FIGURE 2.3** Image preprocessing steps for feature extraction from an image of weed seedlings. (A) Input color digital image; (B) The “a” color channel in Lab color space; (C) Thresholded regions in dark gray or obtained through Image’s Yen thresholding scheme; (D) Binary image after thresholding; and (E) Final preprocessed binary image (after correction) used for shape feature extraction.

Carefully delineating the individual object before measuring shape features is essential because the performance of ML algorithms solely depends on the quality of the input data. The shape features discussed subsequently (see Section 2.3.3) were extracted from the final preprocessed image (Figure 2.3E; without colored arrows) and used as the training data for ML models.

# 2.3.3 SHAPE FEATURES EXTRACTION

Shape features are dimensionless parameters, which are not affected by image resolution, and were used as measures in classifying objects. Image offers four shape features, such as aspect ratio, circularity, roundness, and solidity (Equations (2.1)–(2.4)), along with various other measurements. Those measurements were used for deriving other shape features reported in the literature (Igathinathe et al., 2008; Sunoj et al., 2017; Di and Sun, 2004) and are presented as follows (Equations (2.5)–(2.13)):

```
Aspect ratio = \frac{a}{b} (2.1)
```

```
Circularity = \frac{4\pi A}{p^2} (2.2)
```