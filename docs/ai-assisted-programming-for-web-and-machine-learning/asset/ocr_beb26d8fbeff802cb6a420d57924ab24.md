+   - **Why it matters:** Helps detect overfitting (validation loss rising while training loss decreases) or underfitting (both losses remain high).
- **Useful for early stopping decisions** and understanding model convergence.

# Confusion matrix heatmap

A confusion matrix heatmap offers a visual summary of model predictions across classes, making it easier to spot misclassifications and class-level performance patterns, outlined as follows:

+   - **What it shows:** Visual breakdown of true positives, false negatives, and true negatives for each class.
- **Why it matters:** Helps identify which classes are confused with each other, particularly useful in multi-class classification.

Use **seaborn.heatmap()** for a labeled, color-coded matrix.

# ROC and precision-recall curves

ROC and precision-recall curves are essential visualization tools for evaluating classification performance, especially under class imbalance, detailed as follows:

+   - **What they show:**
  - **ROC curve:** Plots true positive rate vs. false positive rate.
  - **Precision-recall curve:** Highlights performance on imbalanced datasets.
- **Why they matter:** Reveal threshold-dependent trade-offs and help select decision thresholds based on business risk.