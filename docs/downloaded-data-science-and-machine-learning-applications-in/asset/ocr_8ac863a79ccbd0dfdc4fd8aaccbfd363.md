# 5.3 Analysis of Features Using Model Agnostic Metrics

To maintain consistency in the final model prediction, a similar train/test split was employed, and the PFI results of the input features’ performance on the entire data are presented in Fig. 2.8. The RF model yielded an initial testing R² of 0.92. The importance score is computed so that higher values represent a better predictive power. Generally, the importance score is calculated such that a higher value indicates a greater predictive power. A sizeable portion of the 0.92 accuracy score can be attributed to the importance of the values for the most relevant features. The results showed that some input variables were given a relatively low importance score. The results point to a small set of input variables that account for most of the predictability. Inferences can be drawn from this finding about the relative importance of the features. This result is in line with the high-test accuracy that was calculated.

The initial permutation importance calculated on the training data shows the model dependency on each feature during training. Nevertheless, it is essential to state that this analysis was done for both the training and testing dataset to help account for features that may help with the generalisation power of the model. Overfitting is more likely to occur when a feature is considered important during training but is dismissed as important during testing.

Sensitivity analysis was performed to select the relevant features for further prediction. The RF model was used to predict mud loss using the top

![](bbox=[0.25, 0.64, 0.8, 0.89])

Fig. 2.8. Permutation feature importance of the input variables.