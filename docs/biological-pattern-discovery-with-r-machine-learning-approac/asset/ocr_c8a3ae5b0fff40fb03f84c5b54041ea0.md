# Protease Cleavage Pattern Discovery

# 103

![](bbox=[0.166, 0.097, 0.822, 0.303])

Fig. 3.11. The demonstration to show classifier robustness can be analysed. The upper panels show a classifier with a greater degree of the overlap between two prediction densities. The discrimination power of the classifier is less robust against the threshold variation. The lower panels show a classifier with a light degree of overlap between two prediction densities. The discrimination power of the classifier is more robust against the threshold variation. The curves stand for the prediction densities and the shaded areas stand for the thresholds. The dots stand for the thresholds.

No doubt, it is straightforward to check the overlap between two densities of two classes shown in Figure 3.11 for the purpose of the robustness measurement of a classifier. Therefore, the receiver operating characteristic (ROC) curve has been developed for the classifier robustness evaluation [Hanley and McNeil, 1982]. Using this technique, a threshold for the discrimination between two classes is varied from the lowest to the highest (the threshold variation). At this time, the classification performance is recorded correspondingly. The latter will change along with the threshold variation. Therefore ROC is a technique to examine how the classification accuracy variation is sensitive against the threshold variation.

Technically, two measurements are used in an ROC analysis. They are the false positive rate and the true positive rate. The false positive rate is used as the horizontal axis of an ROC space and the true positive rate is used as the vertical axis of an ROC space. Therefore, an ROC plot is a two-dimensional visualisation of the robustness of a classifier.

Figure 3.12(a) shows an example. Suppose seven thresholds have been used. Seven pairs of classification performance measures (the false positive rates and the true positive rates) are obtained. They are then mapped onto the two-dimensional space shown in Figure 3.12(a). Each