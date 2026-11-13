
mean and variability of the class as a whole. The better the training set represents the spectral variation of the class, the more accurate the classification results. For an n-band image, a training set for a given class should contain at least 10 × n pixels so that the spectral response pattern of the class can be reliably characterised. The number of training sets depends on the nature of the classes and the complexity of the study area. It is not unusual to have 100 or more training sets in order to adequately represent the spectral variability in the image. After the training sets are selected and delineated, the pixel values in the training sets are extracted and form the sample for the construction of class signatures.

A class signature is a statistical description of the fundamental spectral characteristics of a class, containing the spectral means, standard deviations, variances, minimum values, maximum values, variances, covariance matrix, correlation matrix and other multivariate statistical measures calculated from its training set. In other words, a class signature is a statistical representation of a particular class. It is used by various decision rules to assign classes to each pixel in the image.

Suppose we have an n-band image. Each pixel has a DN value on each band. These DN values form an n-dimensional vector X = [DN1(i,j), DN2(i,j)..., DNn(i,j)], where i, j are the row and column numbers of the pixel and DNk(i,j) is the DN value of the pixel in band k. This vector is called a measurement vector. This representation allows us to consider each pixel as occupying a point, and each training set as occupying a sub-space (that is, a representative point surrounded by some spread or deviation) within the n-dimensional measurement space. Viewed as such, the classification problem is to determine to which sub-space class each measurement vector belongs.

To simplify the explanation, let us look at a two-band image composed of the red band and near-IR band and five training sets representing forest, cropland, grassland, urban and water. Each pixel from the five training sets has an associated 2D measurement vector, which may be plotted on a scattergram, as shown in Figure 7.23. This diagram shows a 2D measurement space with the x-axis representing the DN values in the red band and y-axis representing the DN values in the near-IR band. Five sub-spaces or clusters of pixels (enclosed in ovals) can be identified, each corresponding to a particular type of land cover. Each sub-space shows the general spectral response pattern and spectral variability within the class it represents. Class signatures use statistical measures to describe the spectral response pattern and variability of each class exhibited in their own sub-spaces. When a pixel of an unknown class is tested, we must decide how to quantitatively determine which of the sub-spaces (classes) it belongs to based on the class signatures, given the measurement vector of the pixel. There are a number of techniques that can be used to make a decision, but parallelepiped classifier and maximum likelihood classifier are two commonly used methods.

## 7.5.1.1 Parallelepiped Classifier

This method uses the range of DN values in each training set to define sub-spaces, often called decision regions, for each class.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_402_0.png)

Figure 7.23 Two-dimensional measurement space.

A decision region is usually bounded by the maximum and minimum DN values of each class in each band calculated from the training set. If an unknown pixel lies in a decision region of a particular class, it will be assigned to that class. If it is placed outside all decision regions, it remains unknown. In a 2D measurement space, a decision region is a rectangle, as shown in Figure 7.24. The pixel P is classified to grassland as it is located in its decision region. In general, an unknown pixel at (i,j) is classified to class C if and only if

```
L_{ck} \le DN_k(i, j) \le U_{ck} \quad for \ all \ c = 1,2,...,m; \ k=1,2,...,n \quad (7.20)
```

where m is the number of classes, n is the number of bands, L_{ck} is the minimum DN value of the class C training set in band k

and U_{ck} is the maximum DN value of the class C training set in band k. In some applications, L_{ck} is defined as the mean DN value minus one standard deviation of the class C training set in band k, and U_{ck} is defined as the mean DN value plus one standard deviation of the class C training set in band k. A decision region in a multidimensional measurement space is often called a parallelepiped.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_403_0.png)

Figure 7.24 Decision regions used by the parallelepiped classifier.

The parallelepiped classifier is computationally efficient. However, some decision regions of different classes may overlap. In these cases, unknown pixels falling in the overlap regions are classified as 'not sure' or assigned to one of the overlapping classes. In addition, this method may not be very accurate, as the parallelepipeds are formed based on DN ranges that may not be representative of a class.

## 7.5.1.2 Maximum Likelihood Classifier

This method applies a probability model to determine the decision regions. Each pixel is evaluated and assigned to the class of which it has the highest probability of being a member. It assumes that the DN values of the training set for each class in each band are normally distributed. Under this assumption, a class can be characterised by the mean vector \(\overline{M_c} = (\overline{DN_{c1}}, \overline{DN_{c2}}, ..., \overline{DN_{cn}})\), where \(\overline{DN_{ck}}\) is the mean DN value of the training set obtained for class c in band k, and the covariance matrix \(C_c\) also derived from the training set. Given \(M_c\) and \(C_c\), the statistical probability of a pixel to be a member of class c is computed as

```
\(p_c = 2 \times \pi^{-0.5n} |C_c|^{-0.5} \exp \left[ \begin{matrix} -0.5 \times (X - M_c)^T \times \\ C_c^{-1} \times (X - M_c) \end{matrix} \right] \quad \text{(7.21)}\)
```

where \(X\) is the measurement vector of the pixel, \(n\) is the number of bands, \(|C_c|\) is the determinant of the covariance matrix \(C_c\). And \(T\) is the matrix operation of transpose. For more information about the determinant and transpose of a matrix, please refer to a linear algebra textbook. For a given unknown pixel, the probability for each class is calculated using equation 7.21. The pixel gets \(k\) probability values for \(k\) classes. It is assigned to the class that has the highest probability (that is, the maximum likelihood). If the highest probability is smaller than a threshold probability value the analyst specifies, the pixel remains unclassified.

In order to improve computing efficiency, equation 7.21 can be modified as follows:

```
\(-ln(p_c) = ln(|C_c|) + (X - M_c)^T \times C_c^{-1} \times (X - M_c) \quad \text{(7.22)}\)
```

The preceding equation does not affect the rank order of the values of \( P_c, c = 1, 2, \dots, k \). Both equation 7.21 and equation 7.22 assume that each of the \( k \) classes is equally likely to occur in the area covered by the image. However, in many applications, some classes may occur more often than others. The anticipated likelihood of occurrence or a priori probability of each class can be calculated based on the proportion of the area covered by each class estimated from scientific reports, land cover maps or aerial photographs. These prior probabilities can be incorporated into the maximum likelihood classifier. One way to do this is to subtract twice the logarithm of the prior probability of class \( c \) from the log likelihood of the class derived from equation 7.22 (Strahler 1980). This extension is often termed the Bayesian classifier. With this method, a class with a higher prior probability is given a higher weight so that an unknown pixel is more likely assigned to this class than to other classes with lower prior probabilities.

The maximum likelihood classifier makes use of the statistics from the class signatures. Sufficient training data need to be sampled to allow estimation of the mean vector and the covariance matrix. This method cannot be applied if the DN values of the training sets do not follow the normal distribution.

## 7.5.2 Unsupervised Classification

In contrast to supervised classification, unsupervised classification does not require the image analyst to specify land cover classes and provide training sets prior to classification. Rather, it automatically groups spectral clusters of pixels based on the DN values in the image using a particular clustering algorithm. The image analyst then matches them to land cover classes.

There are many clustering algorithms available for unsupervised classification. k-means clustering (introduced in Section 6.7.3) and ISODATA (Iterative Self-Organising Data Analysis Techniques; Tou and Gonzalez 1974) are two of the widely used methods. Both involve iterative procedures and require the image analyst to specify the number of classes to be expected in the image. The k-means algorithm seeks to find the centres of the clusters in the multidimensional measurement space of the input bands that minimise the distance from the pixels to the cluster they belong to. It involves the following steps:

- 1 Randomly locate the user-specified number of cluster centres in the multidimensional measurement space, and calculate their mean vectors.

## Practical 7.10 See the Support Material

In this practical, you are going to learn how to perform a supervised classification in ArcGIS Pro or QGIS.
