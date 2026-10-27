# 5.2 Generating Partial Energy Coefficient from Transformed Images

The significance of any image transform is to relocate the high-frequency components toward the upper end of the image and the low-frequency components toward the lower end of the image. The mentioned property is used as a tool to drastically reduce the size of feature vectors by exclusion of insignificant coefficients as shown in Fig. 5.1. A smaller dimension of feature vector has resulted in less time for comparison of feature vectors in the classification process.

Extraction of feature vectors is carried out in 14 steps from the transformed images. Initially, all coefficients of transformed images are considered as feature vectors that have included 100% of the transformed coefficients. Henceforth, gradual reduction in size of the feature vectors as 50%, 25%, 12.5%, 6.25%, 3.125%, 1.5625%, 0.7813%, 0.39%, 0.195%, 0.097%, 0.048%, 0.024%, 0.012% and 0.06% respectively of the complete transformed coefficients is carried out to locate the high-frequency component of the transformed image. For an image of dimension 256 × 256, the process has reduced the feature size from 256 × 256 to 2 × 2 per color component.

**The following steps are used for classification with feature extraction using partial energy coefficients:**

+   - Red, Green and Blue color components are extracted from a given image.
+   - Image Transform is applied on each of the components to extract feature vectors.
+   - The extracted feature vectors from each of the components are stored as a complete set of feature vectors.
+   - Further, partial coefficients from the entire feature vector set are extracted to form the feature vector database.

![](bbox=[0.157, 0.702, 0.878, 0.892])

**FIGURE 5.1**
Steps for Extraction of Partial Energy Coefficient from Image.