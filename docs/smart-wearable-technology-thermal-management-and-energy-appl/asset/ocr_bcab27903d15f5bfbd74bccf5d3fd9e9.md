![](bbox=[0.143, 0.089, 0.857, 0.343])

Figure 9. Blurred images of defective conductive textile: (a) original image; (b) TIPA result.

# 4. Discussion

This study presents a Textile Image Processing Algorithm (TIPA) specifically designed for the detection of defects in conductive textiles manufactured through the dip-coating process. The proposed algorithm demonstrates significant efficacy, achieving overall accuracy exceeding 85%, with a maximum performance of 100% under optimized conditions. These findings underscore the algorithm's potential to address critical quality control challenges in the domain of conductive textiles, a pivotal component in wearable technology applications. Table 2 presents a comparison between the results of this study and those obtained using various artificial intelligence models trained specifically for detecting stains or spot defects in actual textile fabrics. Except for the basic shallow CNN model, which achieved an accuracy level of 62.67%, other models demonstrated high accuracy, exceeding approximately 90%. The differences between the studies in terms of the image collection methods and training datasets used must be considered. However, this study optimized threshold criteria, achieving a remarkably high accuracy level of 100%, demonstrating the superiority of the proposed model.

Table 2. The comparative accuracy of various TIPAs.

| Algorithm Model | Accuracy [%] |
|---|---|
| CNN [39] | 62.67 |
| VGG16 [39] | 90.17 |
| MobileNet [39] | 97.64 |
| InceptionV3 [39] | 93.92 |
| Xception [39] | 96.89 |
| DAGMC9 [34] | 99.60 |
| This study 2 | 100 |

2 Threshold ratio: 15%.

The primary contribution of this research lies in the multi-step processing framework encompassing preprocessing, filtering, and threshold optimization. By employing techniques such as histogram equalization and size-based filtering, our TIPA effectively identified and classified defect regions characterized by the uneven distribution of conductive particles. This approach builds upon existing studies, emphasizing the necessity of tailored image processing methodologies for detecting defects in textiles with intricate