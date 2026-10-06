# An Enhanced Technique for Predicting Autism Spectrum Disorder

better models receiving higher weights. The final prediction $H(x)$ is obtained by combining the weighted predictions of all weak models:

```
$H(x) = \text{sign}\left(\sum_{i=1}^{t} \alpha_i h_i(x)\right) \quad (8.17)
```

Here $T$ is the number of weak models, $\alpha$ is the number of weak models, $h_t(x)$ is the prediction of the t-th model, and $\text{sign}(\cdot)$ is the sign function indicating the class prediction. AdaBoost is adaptive, focusing more on difficult-to-predict instances in each iteration, leading to a robust and accurate ensemble model.

# 8.3.3.5 VO-ADA Model

Creating a new hybrid VO-ADA model using voting and AdaBoost for predicting autism involves multiple models to improve overall performance. The formula for a hybrid model combines voting and AdaBoost. The formula for could be

```
$Ensemble_{VO}(x)} = \text{Majority Vote}(\text{model1}(x), \text{model2}(x), \text{model3}(x)) \quad (8.18)
```

This implies that the ensemble generates a prediction by considering the majority vote from the three individual models. To integrate with AdaBoost, the process is as follows:

```
$Ensemble_{AdaBoost}(x)} = \text{AdaBoost}(Ensemble_{VO}, x) \quad (8.19)
```

In this case, apply AdaBoost to the ensemble of the three models, which involves giving more weight to the misclassified instances in each iteration. The following steps are used to combine the

*Step 1*: $w_j = \frac{1}{N}$, where Nis the number of instances.

+   *Step 2*: For each boosting iteration:
- Train the ensemble(voting) on the training set with $W_r$
- Compute the error $\epsilon$ of the ensemble in the training set.
- Compute the weight of the ensemble in the classifier: $\epsilon = \frac{1}{N}\sum \exp(-sign(y)\# Ensemble_{VO}(x)))$ Where $y$, is the true label.
- Normalize the sample weights: $w_j = \frac{w_j}{\epsilon}$.

*Step 3*: The final prediction is made by combining the weighted predictions of the ensemble models.

The illustration in Figure 8.2 attempts to predict ASD. The loading of the autism dataset and the definition of the characteristics (X) and target (y) start the process. After that, the data are split into testing and training sets. Two different decision tree models are defined as base models, and an AdaBoost model is constructed using one of the decision trees as the base estimator. The decision trees and AdaBoost are then trained to create a voting model. Following a fitting of the ensemble model to the training set, predictions are produced for the test set. Finally, the real labels in the test data are used to evaluate the combined model's accuracy. This coordinated strategy combines the advantages of both voting and boosting models to improve predictive performance for the classification of ASD.