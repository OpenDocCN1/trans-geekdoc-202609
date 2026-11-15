

Table 3 Experimentation result of the proposed model on Ultrasound images dataset.

| Input | Ground Truth | Segmentation | Ellipse fitting |
|---|---|---|---|
| [Ultrasound Image 1] | [Oval Mask 1] | [Black Oval 1] | [Blue Mask 1] |
| [Ultrasound Image 2] | [Oval Mask 2] | [Black Oval 2] | [Blue Mask 2] |
| [Ultrasound Image 3] | [Oval Mask 3] | [Black Oval 3] | [Blue Mask 3] |

the union area of the two masks. IoU ranges from 0 to 1, where a value closer to 1 indicates better segmentation accuracy. It is given mathematically as:

\(IoU = \frac{TP}{TP + FP + FN}\) (14)

where TP is the number of true positive pixels, FP is the number of false positive pixels, and FN is the number of false negative pixels.

- 2. Precision, Recall, and F1-Score: These metrics are commonly used in binary segmentation tasks. Precision measures the proportion of correctly predicted positive instances (true positives) out of all predicted positive instances. Recall (also known as sensitivity) measures the proportion of true positive instances correctly identified out of all actual positive instances. F1-score is the harmonic mean of precision and recall, providing a single value to assess overall segmentation performance. Mathematically, it is given as:

\(Precision = \frac{TP}{TP + FP}\)
\(Recall = \frac{TP}{TP + FN}\)
\(F1-Score = \frac{2 * Precision * Recall}{Precision + Recall}\) (15)

### 4.4. Results

The experimentation results of the proposed model are presented in Table 3. The columns in the Table represent the input sample image taken from the dataset, the available ground truth marked by the experienced sonographer, the segmentation output of the proposed model, and the final result obtained when the ellipse fitted with the input image.

The performance of the proposed model on basis of epochs to accuracy on basis of area under ellipse taken from the segmented area and the available ground truth and its corresponding loss is presented in Fig. 10.

![](img/6b6056dba6e110e45c1a1524eb95a7df_10_0.png)

(a) Accuracy (b) Loss Fig. 10. Epoch-by-Epoch accuracy and Loss analysis of the proposed model.

Table 4 Performance measures of proposed model on dataset distributed into Training, Validation, and Testing.

| Training | | | | Validation | | | | Testing | | | |
|---|---|---|---|---|---|---|---|---|---|---|---|
| DC | DHC | MAPE | HD | DC | DHC | MAPE | HD | DC | DHC | MAPE | HD |
| 97.31 | 0.304 | 0.65 | 1.09 | 96.45 | 0.354 | 0.71 | 1.12 | 96.30 | 0.387 | 0.71 | 1.11 |

Table 5 Performance evaluation of the proposed model at various epoch sizes. The presented results are the average results on the training dataset.

| Epochs | DC | DHC | MAPE | HC |
|---|---|---|---|---|
| E-50 | 92.68 | 0.495 | 0.88 | 1.87 |
| E-100 | 94.55 | 0.416 | 0.80 | 1.54 |
| E-150 | 95.89 | 0.372 | 0.74 | 1.20 |
| E-200 | 96.32 | 0.343 | 0.69 | 1.18 |
| E-250 | 97.31 | 0.304 | 0.65 | 1.09 |
| Average | 95.35 | 0.386 | 0.752 | 1.376 |

The experimentation results of the proposed model on various statistical performance measure as defined in Eqs. (10)–(13) using the testing dataset is presented in Table 4. The values presented in Table 4 are the average results of the experiment on the complete database. The database comprises three parts i.e. Training, Validation, and Testing. Table 4 shows the metric values as per the sample distribution.

It was also observed that the model performance has a dependency on the number of epochs used in model training and validation. The analysis of model performance is calculated using the various epoch sizes as shown in Table 5. On observation, it was found that the accuracy of the model rises as the epoch count increases. In this work, the experimentation was done on various epoch sizes and found that till the epoch count of 250, the performance increases at an acceptable rate but after that the performance almost becomes saturated.

However, the performance of the proposed model in estimating the size of the fetus's head circumference is presented in Table 6. The performance of calculating the head circumference is estimated by finding the absolute difference in the head circumference between the segmented output and the available ground truth. The results in Table 6 show the sample images, their available ground truth with fetus head circumference size, and the segmented region with estimated fetus head size. The last column of Table 6 shows the absolute difference in the segmented result and available ground truth. The results as shown

Table 6 Experimentation result of the proposed model on an estimation of Fetus Head Circumference (FHC). Results are shown for the randomly selected images from the training and validation set.

| Input | Ground truth | Segmentation | FHC_Grt (mm) | FHC_Seg (mm) | Abs Diff. (mm) |
|---|---|---|---|---|---|
| [Image] | [Image] | [Image] | 71.96 | 73.24 | 1.28 |
| [Image] | [Image] | [Image] | 87.32 | 87.98 | 0.66 |
| [Image] | [Image] | [Image] | 67.84 | 68.97 | 1.13 |
| [Image] | [Image] | [Image] | 78.08 | 78.14 | 0.06 |
| [Image] | [Image] | [Image] | 74.31 | 75.55 | 1.24 |
| Average of Absolute Difference | | | | | 0.874 |

Table 7 Experimentation result of the proposed model using other benchmark performance measures. Results are shown for the randomly selected images from the training and validation set.

| Input | Ground Truth | Segmentation | IoU | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| [Image] | [Image] | [Image] | 0.96 | 0.95 | 0.94 | 0.94 |
| [Image] | [Image] | [Image] | 0.95 | 0.95 | 0.94 | 0.94 |
| [Image] | [Image] | [Image] | 0.95 | 0.94 | 0.94 | 0.95 |
| [Image] | [Image] | [Image] | 0.96 | 0.96 | 0.94 | 0.94 |
| [Image] | [Image] | [Image] | 0.95 | 0.95 | 0.95 | 0.94 |
| **Average** | | | 0.95 | 0.94 | 0.94 | 0.95 |

in Table 6 are for the randomly selected five images from the Training and Validation set. The last row of the table gives the average absolute difference for all the images. It is found that the average absolute difference of the sample shown in Table 6 is 0.874 mm. While for the whole Training and Validation dataset the average absolute difference is 0.304 mm and 0.354 mm respectively.

The experimentation result of the proposed model on some of the state-of-art benchmark performance measures are presented in Table 7.

## 5. Comparative analysis

The performance of the proposed model when compared with the state-of-art methods is found satisfactory as the gains in results on different metrics for fetus segmentation are on the higher side. Here we presented the quantitative analysis of the proposed methodology in two forms i.e. comparative analysis with several state of art deep models, with a transfer Learning aspect, and comparison with some of the existing works on the HC18 dataset.

### 5.1. Quantitative comparison with benchmark models

The comparative analysis of the proposed methodology with some of the benchmark deep models, initially designed for various other applications, was used for comparison perspective. The models are used based on Transfer Learning, which means model weights are carried forward for new applications. Some of the models which are used for comparison are UNet, WNet, 3D-UNet with Augmentation, VNet, and Cascaded Network. The comparative analysis of these models with the proposed model is shown in Table 8.

The comparative analysis of the proposed model with the other state-of-art models of segmentation using the benchmark performance measures is shown in Table 9.

### 5.2. Quantitative comparison with existing literature

The comparative analysis of the proposed methodology with some of the existing works on the HC18 dataset is presented in Table 10.

Table 8 Comparative Analysis of Proposed Model with existing Benchmark Models.

| Models | DC | DHC | MAPE | HC |
| :--- | :--- | :--- | :--- | :--- |
| UNet | 78.4 | 0.872 | 0.815 | 1.39 |
| UNet++ | 96.54 | 0.297 | 0.68 | 1.15 |
| D-UNet+Augmentation | 84.62 | 0.657 | 0.724 | 1.2 |
| WNet | 80.34 | 0.773 | 0.797 | 1.27 |
| VNet | 85.48 | 0.587 | 0.701 | 1.18 |
| Cascaded Network | 90.15 | 0.446 | 0.687 | 1.12 |
| Proposed Model | 97.31 | 0.304 | 0.65 | 1.09 |

