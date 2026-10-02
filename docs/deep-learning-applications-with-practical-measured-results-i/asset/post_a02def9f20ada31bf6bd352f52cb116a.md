
The classification process of hyperspectral image based on deep transfer learning is shown in Figure 7.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_198_0.png)

Figure 7. Hyperspectral image classification process based on deep transfer learning.

## 5. Optimal Neighborhood Noise-Reduction Method

In order to reduce the salt-and-pepper noise in the initial classification results, an optimal neighborhood noise reduction method based on the eight-neighbor mode label was proposed in this article. The optimal neighborhood noise reduction method was used to reprocess the initial classification result of the hyperspectral image. In the method, the hyperspectral image classification label data was used as the input, and the central pixel label was compared to the label of its eight-neighborhood pixel.

If L(i,j) is used to represent the classification result label of a central pixel P(i,j) of the hyperspectral image, the class labels of the central pixel P(i,j) and the eight neighborhood pixels are shown in Figure 8.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_199_0.png)

Figure 8. Class labels of the central pixel and its eight neighborhood pixels.

As shown in Figure 8, based on the traversal of all the pixel labels of the hyperspectral image, the class label L_(i,j) of one central pixel P_(i,j) and the class labels of the eight neighborhood pixels were combined into a 3×3 matrix. The 3×3 matrix was transformed into a 1×9 one-dimensional vector. Then the mode M of the nine labels and the number m of the mode labels were calculated. The threshold was set to N (0 ≤ N ≤ 9), and the pixel label of the hyperspectral image that did not need to be classified was set to 0. The central pixel is considered to be noise when the following conditions are met: The class label L_(i,j) of the central pixel is not equal to the mode of the nine pixel labels, the mode label is not 0, and the number of the mode labels is m ≥ N. Since the label of 0 means that the pixel does not need to be classified, the mode label with the value of 0 is excluded to avoid the edge misjudgment. If the central pixel P_(i,j) is confirmed to be noise, it is replaced with the mode label of the eight neighborhood pixels. The initial value of the threshold N is generally set to 5. When the central pixel label L_(i,j) is not equal to the mode label of the nine pixels, the mode label is not 0, and the number of the mode labels is m ≥ 5, the central pixel is considered to be noise. The threshold N can be modified according to actual conditions. If the threshold is too large, the noise-reduction effect may not be obvious; if the threshold is too small, the actual information may be misjudged as noise.

The pseudo-code of the optimal neighborhood noise reduction process is shown as follows:

```
Input: The classification result dataset X of the hyperspectral image, the label of 0 for the pixels that do not need to be classified, and the threshold N=5
Output: The noise-reduced classification result data set X of the hyperspectral image and classified image with noise reduction.
Load classification result dataset X
for i=1; i< X.shape[0]; i++
for j=1; j<X.shape[1]; j++
loop traversing each pixel label L_(i,j)
Transforming the 3×3 matrix composed of the central pixel label L_(i,j) and its eight neighborhood pixel labels into a 1×9 one-dimensional vector
Calculating the mode M and its number m of central pixel label and the eight neighborhood pixels labels.
if the class label L_(i,j) of the central pixel is not equal to the mode number M of the nine labels
if the mode label is not 0 and the number of the mode label is m≥N
The central pixel P_(i,j) is noise
Replace the central pixel label L_(i,j) with the mode label M to remove the noise
end if
end if
Update the hyperspectral image classification result label L_(i,j) of each pixel P_(i,j)
end loop L_(i,j)
end for
end for
```

## 6. Experiments and Analysis

### 6.1. Dataset

In order to verify the proposed method in this article, the experiments were conducted on the datasets with similar characteristics. The selected dataset included the Indian Pines dataset, the Salinas dataset, the Pavia University dataset, and the Pavia Center dataset. Both the Indian Pines dataset and the Salinas dataset were acquired by AVIRIS sensors. The corrected spectral dimensions for both datasets were 200 and 204, respectively, which were very close. The real ground objects were divided into 16 classes [44]. The Pavia University dataset and the Pavia Center dataset were collected by ROSIS sensors. The corrected spectral dimensions of these two datasets were 103 and 102, respectively, and the real ground objects were divided into nine classes [45]. The datasets are gotten from the website (http://www.ehu.eus/ccwintco/index.php?title=Hyperspectral_Remote_Sensing_Scenes).

The Indian Pines dataset and the Salinas dataset were similar, and the Pavia University dataset and the Pavia Center dataset were similar. In addition, the former two datasets had a smaller sample size than the latter two datasets. Therefore, the Salinas dataset and the Pavia Center dataset were used as the source datasets in the transfer learning method, while the Indian Pines dataset and the Pavia University dataset were used as the corresponding object datasets. First, the structures and parameters of the shallow network were obtained and validated from the training on the Salinas dataset and Pavia Center dataset. Then the obtained structure and parameters were transferred to the Indian Pines dataset and Pavia University dataset with relatively small sample sizes. Finally, the structure and parameters of the network were fine-tuned.

There was a big difference between the Indian Pines dataset and the Pavia University dataset, which could be used to validate the proposed classification method fully. The Indian Pines dataset had a small sample size and can mainly reflect the vegetation information, including rich species and mostly regular block distribution, rich spectral information and low spatial resolution. The Pavia University dataset had a large image size and can mainly reflect the landscape information of the urban landscape. Although there were few species, the shape of the object was irregular, and the spatial resolution was high.

### 6.2. Experiments and Result Analysis

### 6.2.1. Experiments of Dimensionality Reduction Methods

In order to test the effectiveness of the proposed methods in the dimensionality reduction and noise reduction for the hyperspectral images, the classification performance of IM, IM_SPE methods, and these methods superimposed with optimal neighborhood noise-reduction method (IM_DN, IM_SPE_DN methods) were tested and compared with that of the spectral information based CNN classification method (SPE) [46], the spatial information based CNN classification method (PCA1, PCA first principal component) [47], the CNN classification method based on the integration of the spectral information and the first principal component of the spatial information (PCA1_SPE), and the CNN classification method based on PCA's first three principal components of the spectral information (PCA3) [48]. We use OA, AA and Kappa coefficients to evaluate the performance of different methods.

(1) Experiments on Indian pines dataset

The classification performance on the Indian pines dataset is shown in Table 1. From Table 1, for the Indian pines dataset, the PCA1_SPE, PCA3, IM, and IM_SPE classification methods provided the best classification accuracy. Moreover, the OA, AA and Kappa coefficients of IM and IM_SPE methods were superior to those of SPE, PCA1, PCA1_SPE, and PCA3 methods, which indicated that the information measure-based classification method (IM and IM_SPE) had better performance than the spectral information-based classification method (SPE) and the PCA-based classification method (PCA1, PCA1_SPE and PCA3). Among all classification methods, the IM_DN and IM_SPE_DN methods had the best OA, AA, and Kappa coefficients, due to the combination of the dimensionality reduction based
