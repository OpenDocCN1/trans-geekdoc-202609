# CHAPTER 8 LOCAL MODEL-AGNOSTIC METHODS

# 8.1 Individual Conditional Expectation (ICE)

Individual Conditional Expectation (ICE) plots display one line per instance that shows the instance's prediction changes when a feature changes.

The partial dependence plot for the average effect of a feature is a global method because it does not focus on specific instances, but on an overall average. The equivalent to a PDP for individual data instances is called individual conditional expectation (ICE) plot (Goldstein et al. 2017). An ICE plot visualizes the dependence of the prediction for each feature separately, in one line per instance, compared to one line overall in partial dependence plots. A PDP is the average of the lines of an ICE plot. The values for a line (and one instance) can be computed by keeping all features the same, creating variants with the black box model for these newly instances. The result is a set of points for an instance with the feature value from the grid and the respective dependencies.

A more formal definition: In ICE plots, for each instance in $\{(x_S^{(i)}, x_C^{(i)})\}_{i=1}^N$ the curve $\hat{f}_S^{(i)}$ is plotted against $x_S^{(i)}$, while $x_C^{(i)}$ remains fixed.

# 8.1.1 Examples

Let's go back to the cervical cancer dataset and see how the prediction of each instance is associated with the feature "Age". We will analyze a random forest that predicts the probability of cancer for a woman given risk factors. In the partial dependence plot we have that the cancer probability increases around the age of 50, but this is true for every woman in the dataset? The ICE plot reveals that for most women the age effect follows the average pattern of an increase at 50, but there are some exceptions: For the few women who have a high predicted probability at a young age, the predicted cancer probability does not change much with age.

The next figure shows ICE plots for the bike rental prediction. The underlying prediction is a random model.

All curves seem to follow the same course, so there are no obvious interactions. That means the PDP is already a good summary of the relationships between the displayed features and the predicted number of bicycles

> ¹Goldstein, Alex, Adam Kapeler, Julian Bleisch, and Emil Pitkin. "Peeking inside the black box: Visualizing statistical learning with plots of individual conditional expectation." journal of Computational and Graphical Statistics, 24, no. 1 (2015): 44-65.