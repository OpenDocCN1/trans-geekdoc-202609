carefully tuned based on the performance indicators employed and on the characteristics of the data input.

# Question 10: How can you interpret the output of a gradient-boosted regression model?

**Answer**: When it comes to performance, it is possible to end up with quite complex interpretations, especially when it comes to interpreting the output of a gradient-boosted regression model which involves bringing out the features that the model deems fit to make in their predictions.

Here is a brief explanation:

+   1. **Feature importance**:
+      a. **Definition**: Examine components that have higher importance numbers, which represents their input toward the predictions.
+      b. **Visualization**: Illustrate importance via chart/plot for a glance at areas of interest.
+   2. **Partial dependence plots (PDP)**:
+      a. **Purpose**: Use one or more features to understand how they affect prediction while controlling the other feature(s).
+      b. **Interpretation**: It is crucial to observe how variation of a specific feature affects the model’s outcome.
+   3. **Individual prediction explanations**:
+      a. **SHapley Additive exPlanation (SHAP) values**: To explain the contribution of each feature in a predictor variable, one needs to use the variable SHAP values.
+      b. **Insight**: Get the idea of the high or low prediction to a certain instance based on which aspect is