# 162 Machine Learning for Social and Behavioral Research

To examine the interaction between these two predictors, we have to create a three-dimensional partial dependence plot. Given that both the outcome and one predictor is binary, it is much more difficult to assess, however, we display this plot in Figure 6.17. In this figure, each panel (no and yes) are essentially mirror images, thus we only interpret the right panel. Here, when ADWRWRTH is yes, it doesn't matter what the value of ADBPINTF is, because all but the lowest response option on ADPINTF is associated with a high predicted probability of enduring suicidal ideation. We see discrepant results when ADWRWRTH is no. Each increase in the ADBPINTF response option is associated with an increase in predicted probability (outside of the two response options). This constitutes a relatively clear interactive effect. If we suspected interaction effects (or nonlinear effects) among additional predictors, we could create these plots for several predictor variables.

**FIGURE 6.17.** Three-dimensional partial dependence plot for ADPBINTF and ADWRWRTH.

![](bbox=[0.222, 0.466, 0.777, 0.773])