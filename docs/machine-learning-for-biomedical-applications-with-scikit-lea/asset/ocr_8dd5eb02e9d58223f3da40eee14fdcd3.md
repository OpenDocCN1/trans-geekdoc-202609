![](bbox=[0.248, 0.095, 0.715, 0.265])

Figure 7.2 Example decision stump.

![](bbox=[0.137, 0.333, 0.812, 0.506])

Figure 7.3 Examples of simple weak learning rules for classification.

of 7.2); if it is false, it passes down the other. Each weak learner in a tree is known as a decision stump.

# 7.1.1 Decision stumps

Learning rules for trees may take many forms including linear (Fig. 7.3 center) and non-linear fits (Fig. 7.3 right) [10]; however, most often, classification trees nodes implement axis-aligned learning rules, which make predictions by thresholding on a single feature (Fig. 7.3 left). This is the approach used in scikit-learn.

A biomedical example of such a decision stump is shown for classification of diabetes in Fig. 7.2. Here, a decision is made by optimizing a threshold on blood glucose levels. All examples with blood glucose less than 12 mmol/L are considered healthy and pass down the left branch. All remaining examples are labeled as diabetic and pass down the right. It is expected that, for most problems, such a simple learning rule will result in many misclassified examples. Therefore, the role of subsequent decision stumps in the tree is to further refine the prediction.