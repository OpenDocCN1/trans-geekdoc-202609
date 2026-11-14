![](bbox=[0.06, 0.065, 0.91, 0.27])

![](bbox=[0.06, 0.28, 0.91, 0.51])

![](bbox=[0.06, 0.52, 0.95, 0.72])

**Fig. 6** Generalization to an independent patient cohort. a, Two examples (immune-high and -low) from the TCGA-SKCM cohort, showing H&E images, predicted protein multiplexes and expression profiles of MelanA, CD3 and CD20 markers. Scale bars, 2 mm (top) and 2.5 mm (bottom). b, Model architecture for multimodal survival and immune subtype prediction. c, Survival prediction results (i), displaying time-dependent C-index scores (left) and Kaplan–Meier survival curves for all test patients aggregated across five cross-validation folds for the multimodal setting, with separation of low- and high-risk groups (right). Immune subtype prediction results (ii), showing the weighted F1-score (left) and confusion matrix (right) for classification into low, intermediate and high immune subtypes. The confusion matrix corresponds to the fold with the highest weighted F1-score. For bar plots, bars represent mean values and error bars indicate s.d. Cls, classifier head; F, residual neural network feature extractor ResNet18; Hx, H&E IMC features; Hx p, predicted IMC features.

# Discussion

In this study, we introduced HistoPlexer, a generative model for predicting high-order (11-channel) multiplexed protein expression profiles, including both tumour and immune markers, directly from H&E images. By simultaneously predicting markers, HistoPlexer effectively captured sparse markers and preserved biologically meaningful

relationships, as validated through spatial correlation analysis of protein co-localization patterns. Our comprehensive evaluation showed consistent outperformance of the MP approach over SP alternatives, with higher MS-SSIM and PSNR and lower RMSE-SW and MSE values. Domain experts found the generated IMC images realistic, with HYPE error rates of 61.6% and 72.8% for lymphocyte and tumour markers.