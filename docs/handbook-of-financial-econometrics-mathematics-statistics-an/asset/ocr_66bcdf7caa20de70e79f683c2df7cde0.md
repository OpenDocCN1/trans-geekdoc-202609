![](bbox=[0.05, 0.05, 0.95, 0.55])

# Figure 50.1: Four models with different powers.

+   3. Divide the sample into default and survival groups.
+   
+   4. In the default group, compute the cumulative probability greater than each percentile of default probabilities. This will be plotted on the y axis.
+   
+   5. In the survival group, compute the cumulative probability greater than each percentile of default probabilities. This will be plotted on the x axis.
+   
+   6. Plot the ROC curve.
+   
+   7. For each structural model, repeat Steps 1-6. Calculate the Accuracy Ratio (AR) and the z-statistic of the difference of ARs between two models. The z-statistic is computed by the method of comparing the areas under ROC curves by Hanley and Hajian and Tilaki (1997).12

> SAS program is available on http://www.medicine.mcgill.ca/epidemiology/hanley/software/.