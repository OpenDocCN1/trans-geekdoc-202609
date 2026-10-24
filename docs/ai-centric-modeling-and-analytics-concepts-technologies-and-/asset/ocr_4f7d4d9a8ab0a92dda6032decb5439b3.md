# TABLE 11.4
Classification Report of EfficientNetV2B1 Model Trained for Merged Dataset.

| Classification report |  | Precision | Recall | F1 score |
|---|---|---|---|---|
| Glaucomatous |  | 0.85 | 0.73 | 0.79 |
| Non-glaucomatous |  | 0.83 | 0.92 | 0.87 |
| Accuracy |  |  |  | 0.84 |
| Macro-average |  | 0.84 | 0.82 | 0.83 |
| Weighted average |  | 0.84 | 0.84 | 0.84 |

The trade-off between the two where we can see the link between the two is loss vs. accuracy. The accuracy of the model increased with a decrease in loss. In the example, as the loss decreases, the accuracy of the model increases, and vice versa.

# 11.7.2.8 Classification Report

The effectiveness of the model was assessed using a classification report (Table 11.4). The report provides several measures for each category in the dataset, including accuracy, recall, and F1 score.

As shown in Table 11.4, the dataset has two classes: 0 (glaucoma) and 1 (non-glaucoma). The report shows the following metrics for each class:

+   - **Precision:** The precision for class 0 is 0.85, which means that 85% of the samples predicted as class 0 are actually class 0. The precision for class 1 is 0.83, which means that 83% of the samples predicted as class 1 are actually class 1.
+   - **Recall:** For class 0, the recall is 0.73, which means that 73% of the samples that belong in class 0 were properly predicted to be in class 0. The recall for class 1 is 0.92, which means that 92% of the samples that are truly in class 1 were forecasted as class F1 score in a correct manner.

The harmonic mean of accuracy and recall is the F1 score. The F1 scores for classes 0 and 1 are 0.79 and 0.87, respectively.

The model successfully predicted 84% of the samples, with an accuracy of 84%.

The average accuracy, recall, and F1 score for all classes comprised the macro-average and weighted average.

Overall, the model is performing well in predicting class 1 (non-glaucoma) samples with a high recall of 0.92 and a high F1 score of 0.87. However, it can be improved in predicting class 0 (glaucoma) samples with a lower recall of 0.73 and F1 score of 0.79.

# 11.8 CONCLUSION

This chapter describes a TL approach for glaucoma detection. There are two vertices by which the five different datasets, namely, Drishti-GS, ACRIMA, ORIGA, HRF, and Multi Eye Disease datasets, which includes retinal (fundus) and pupil images, are trained on ‘EfficientNetV2’ series of TL models.