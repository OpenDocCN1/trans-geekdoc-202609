
## 7.4 Coding Exercise

The above code example illustrates the process of codebook generation using the LBG algorithm. Refer to the example and try to complete the following assignment:

- Apply the LBG algorithm on red, green and blue color components for codebook generation.

## 7.5 Feature Extraction by Gray Level Co-occurrence Matrix (GLCM)

Texture features have the characteristics to describe the visual pattern based on spatial definition of images. Identifying the specific texture in an image is carried out by representing the texture as a two-dimensional gray level variation known as the gray level co-occurrence matrix (GLCM) [1]. The GLCM is defined as a statistical method for discovering the textures that consider the spatial relationships of pixels. The GLCM function represents the texture of an image by computing the frequency of existence of pixel pairs with specific values and with specific pixel relationships in an image followed by extraction of statistical measures from the matrix. (7.2) defines the normalized probability of the co-occurrence matrix.

\[
P_\delta(i,j)=\frac{\#\{(x,y),(x+d_x,y+d_y)\mid (x,y)\in S,\ f(x,y)=i,\ f(x+d_x,y+d_y)=j\}}{\#S} \tag{7.2}
\]

where x,y = 0, 1, ..., N − 1 are pixel coordinates, i,j = 0, 1, ..., L − 1 are gray levels, S = pixel pairs in image with certain relationship, #S = number of elements in S and P_δ(i,j) = probability density.

Different directions are considered for computation of GLCM, such as δ = 0°, δ = 45°, δ = 90° and δ = 135°. Four statistical parameters for energy, contrast, entropy and correlation are calculated based on the GLCM as shown in equations 7.3–7.6. The repetition of pixel pairs is measured by the energy or angular second moment (ASM). The variance of gray level is quantified by contrast. The disorder of the image is measured by entropy, and correlation has returned a measure of how correlated a pixel is to its neighbor over the whole image.

\[
ASM=\sum\sum P^2(i,j) \tag{7.3}
\]

\[
CON = \sum\sum (i-j)^2 P(i,j) \tag{7.4}
\]

\[
ENT = -\sum\sum P(i,j)\log[P(i,j)] \tag{7.5}
\]

\[
COR = \frac{\sum\sum ij\,P(i,j)-\mu_x\mu_y}{\sigma_x\sigma_y} \tag{7.6}
\]

where μx and μy and σx and σy denote the mean and standard deviation for P_X and P_Y, respectively; P_X = sum of each row of co-occurrence matrix and P_Y = sum of each column of co-occurrence matrix. The mean and standard deviation of all the parameters are used to compute the feature vector for each image and the dimension of feature vector is 8 per image.

The technique of feature extraction is applied on four public datasets, namely, Wang dataset, OT-Scene dataset, Corel dataset and Caltech dataset, and is tested for classification results with four different classifiers namely, K Nearest Neighbor (KNN), Ripple-Down Rule (RIDOR), Artificial Neural Network (ANN) and Support Vector Machine (SVM). The results are given in Table 7.2.

**TABLE 7.2**

*Classification Performances by Feature Extraction using GLCM with Four Different Public Datasets using Four Different Classifiers*

| Datasets | Metrics | KNN | RIDOR | ANN | SVM |
|---|---:|---:|---:|---:|---:|
| Wang | Precision | 0.615 | 0.481 | 0.633 | 0.565 |
|  | Recall | 0.617 | 0.492 | 0.634 | 0.566 |
|  | MR | 0.079 | 0.092 | 0.076 | 0.080 |
|  | F1-Score | 0.604 | 0.485 | 0.631 | 0.553 |
| OT-Scene | Precision | 0.528 | 0.461 | 0.578 | 0.475 |
|  | Recall | 0.526 | 0.462 | 0.580 | 0.483 |
|  | MR | 0.082 | 0.093 | 0.080 | 0.094 |
|  | F1-Score | 0.526 | 0.461 | 0.573 | 0.448 |
| Corel | Precision | 0.535 | 0.444 | 0.464 | 0.468 |
|  | Recall | 0.548 | 0.441 | 0.456 | 0.475 |
|  | MR | 0.082 | 0.094 | 0.097 | 0.093 |
|  | F1-Score | 0.524 | 0.442 | 0.400 | 0.449 |
| Caltech | Precision | 0.436 | 0.577 | 0.527 | 0.369 |
|  | Recall | 0.544 | 0.587 | 0.583 | 0.506 |
|  | MR | 0.090 | 0.080 | 0.079 | 0.100 |
|  | F1-Score | 0.466 | 0.578 | 0.544 | 0.388 |

> **Observation:** The Wang and OT-Scene datasets show maximum classification performance with the ANN classifier, the Corel dataset shows maximum classification with the KNN classifier and the Caltech dataset shows maximum classification with the RIDOR classifier.

```text
selection:
  sections:
  - section
  pages:
  - page
  spreads:
  - spread
  robots:
  - robots
```

## 7.8 Evaluation of Proposed Techniques

Two techniques of texture content-based feature extractions were introduced in the previous subsections. The techniques were tested for classification results with four different widely used public datasets. Four different classifiers were used for the comparison. The two techniques are compared based on Precision, Recall, Misclassification Rate (MR) and F1-Score values in Figs. 7.3–7.6.

The comparisons based on Precision, Recall, MR and F1-Score shown in Figs. 7.3–7.6 establish feature extraction with VQ using LBG as a superior technique compared to that of the GLCM method of feature extraction for content-based image classification.

The LBG technique divides the gray values into separate clusters based on likelihood and separates the given test image into local partitions for feature extraction. This has locally addressed the adversities of test images, namely, variance in gray levels within the object and the background, inadequate contrast, etc., while calculating the code vectors from each cluster. This has further facilitated robust feature extraction from the region of interest in the test images.

![](img/2bc397c57b3b49c1ff177a21ce3b8fc5_156_0.png)

**FIGURE 7.3** Comparison of Precision Values of Classification by Feature Extraction with VQ using LBG and GLCM for All Four Datasets using Four Different Classifiers.

> **Observation:** Classification by feature extraction with VQ using LBG has higher Precision values compared to GLCM.

![](img/2bc397c57b3b49c1ff177a21ce3b8fc5_158_0.png)

**FIGURE 7.5** Comparison of Misclassification Rate (MR) of Classification by Feature Extraction with VQ using LBG and GLCM for All Four Datasets using Four Different Classifiers.

> **Observation:** Classification by feature extraction with VQ using LBG has lower MR values compared to GLCM.

![](img/2bc397c57b3b49c1ff177a21ce3b8fc5_158_1.png)

**FIGURE 7.6** Comparison of F1 Scores of Classification by Feature Extraction with VQ using LBG and GLCM for All Four Datasets using Four Different Classifiers.

> **Observation:** Classification by feature extraction with VQ using LBG has higher F1-Score values compared to GLCM.

![](img/2bc397c57b3b49c1ff177a21ce3b8fc5_159_0.png)

**FIGURE 7.7** Comparison of Classification Results by Feature Extraction using Bottom-Hat Technique to That of Existing Techniques.

> **Observation:** Classification results for feature extraction with bottom-hat transform exceed the classification results for the existing techniques.

The results for classification by feature extraction with VQ using LBG in Fig. 7.7 have clearly outclassed the existing techniques, profoundly enhanced the rate of Precision, Recall and F1-Score and reduced the MR for content-based image classification.

Finally, the average time taken for feature extraction from each image in a Wang dataset with VQ using the LBG technique is compared to the existing techniques discussed in References [2–5]. A comparison is shown in Fig. 7.8.

The comparison in Fig. 7.8 shows that feature extraction with VQ using the LBG technique consumes maximum average time compared to the existing techniques discussed in References [2–5].

## 7.10 Statistical Significance

**HYPOTHESIS 7.1:** *There is no difference between the Precision values of classification results obtained by feature extraction with VQ using LBG with respect to the existing techniques.*

![](img/2bc397c57b3b49c1ff177a21ce3b8fc5_160_0.png)

**FIGURE 7.8** Comparison of Average Time Consumed for Feature Extraction.

> **Observation:** Feature extraction with VQ using the LBG technique consumes maximum average time compared to existing techniques.

A paired *t*-test is carried out to establish the difference in Precision values for classification by feature extraction with VQ using LBG compared to the existing techniques. Initially, the mean, standard deviation (SD) and standard error of the mean (SEM) of the Precision values of classification of different categories for feature extraction with VQ using LBG are calculated in Table 7.3.

The results for the *t*-test to determine whether the difference in Precision values for classification is generated from a population with zero mean are displayed in Table 7.4.

The *p*-values in Table 7.4 indicate significant difference in Precision results for classification by feature extraction with VQ using LBG compared to the existing feature extraction techniques. Comparison of the mean, SD and SEM of Tables 7.3 and 7.4 shows that the mean value of Precision of

**TABLE 7.3**

*Value of Mean, Standard Deviation and Standard Error of the Mean for Precision Values of Classification by Feature Extraction with VQ using LBG*

| Proposed Technique | Mean | Standard Deviation (SD) | Standard Error of the Mean (SEM) |
|---|---:|---:|---:|
| Feature extraction with VQ using LBG | 0.899 | 0.085 | 0.020 |
