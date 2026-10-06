# Text Separation From Document Images

Figure 19. (a) Quantitative Analysis and (b) Training and Validation Loss of ResU-Net

![](bbox=[0.137, 0.167, 0.823, 0.386])

# c. Results of U-Net and ResU-Net Results on test data

Table 1 shows the quantitative analysis on both deep models (U-Net and ResU-Net) which were finuned on the document test dataset. The results of ResU-Net are better than U-Net due to the presence of the residual connections in.

Table 1. Comparative results of text segmentation of Devnagari scanned images on U-Net and ResU-Net model

| Parameters | U-Net | ResU-Net |
|---|---|--|
| Accuracy | 0.9763 | 95.031% | 98.802% |
| Precision | | 94.729% | 98.480% |
| Recall | | 80.4912% | 83.220% |
| F1-Score | | 86.106% | 90.032% |

# SUMMARY (COMPARISON OF TRADITIONAL TECHNIQUES WITH THE DEEP LEARNING APPROACH)

Conventional or traditional image processing requires the features that need to be classified to be hand-coded. The image needs to be analysed at every step in traditional methods of image processing. Pre-processing, transformations, and identification of filters are some necessary steps to apply the input to find the features. As discussed in the chapter, text extraction using traditional image processing methods includes pre-processing, block extraction, perimeter detection, and text extraction. On the other hand, deep learning learns the features while training the models. The network is very deep and is made up of a large number of layers of neurons. Each layer has features extracted at the output of the