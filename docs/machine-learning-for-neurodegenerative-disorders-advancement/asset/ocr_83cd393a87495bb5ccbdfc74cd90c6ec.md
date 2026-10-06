feature disproportionately influences the model due to its scale. This step is crucial for maintaining the model's integrity and reliability. Uniform scaling of features to have a mean of 0 and a standard deviation of 1, especially for features Xi in the dataset. The standardized feature Zi can be calculated as

```
Zi = \frac{\Xi - \mu\Xi}{\sigma\Xi} (8.14)
```

where muXi is the mean and sigmaXi is the standard deviation of the feature Xi. This ensures that all features contribute equally to the model, preventing any feature from dominating due to its scale.

# 8.3.3.2.4 Tailoring to ASD Prediction

Tailoring extraction to the unique characteristics of ASD prediction is also vital. This involves considering factors like family history and the chosen screening method, as these elements can significantly influence the outcomes. For example, screening methods may be more sensitive to specific age or symptom patterns, and for these we can refine the dataset further. Tailoring extraction involves considering domain-specific features, such as family history and chosen screening method. For instance, we may assign weights to features based on their relevance to ASD, and a weighted sum:

```
S = \sum_{i=1}^{m} w iXi (8.15)
```

where S is a composite score for prediction. This refines the dataset by focusing on the most relevant features for ASD prediction. By implementing these steps, the feature extraction results in a well-organized and informative dataset, such as the Kaggle Autism Dataset. This refined dataset is ready for training and evaluating data science models, providing a solid foundation for accurate and reliable ASD prediction. The careful selection, transformation, and scaling of features ensures that the models built on this data are both efficient and effective, contributing to better understanding and early identification of ASD.

# 8.3.3.3 Vote

In data science, the vote model is a simple and efficient model. This methodology involves several models contributing to their forecasts, with a majority vote deciding the final result. The projected class is to vote by each model, and the class with the highest votes becomes the final forecast. Mathematically, the predicted class (C) is found as the mode of the predicted classes from models if there are "n" individual models (predictive model):

```
C = mode(C1, C2, ..., Cn) (8.16)
```

Here C1, C2, ..., represent the predicted classes from each individual model. The vote model is particularly useful when different models bring diverse perspectives or expertise, and the collective decision helps enhance overall prediction accuracy.

**8.3.3.4 AdaBoost**

The AdaBoost model stands out as a a potent ensemble learning approach in data science. In AdaBoost, numerous weak models are amalgamated to form a robust model. The algorithm assigns weights to individual data points and iteratively refines these weights to emphasize the significance of misclassified points in successive iterations. The final model is a weighted sum of the individual weak models. The weight of each weak model (alpha) is determined based on its performance, with