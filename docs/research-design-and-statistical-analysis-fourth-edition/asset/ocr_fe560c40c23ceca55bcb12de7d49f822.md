# 198 Research Design and Statistical Analysis

In SPSS, select the Compare Means and Proportions submenu of the Analyze pull-down list, then choose One-Way ANOVA. Move the Score variable to the box labeled “Dependent List” and Method to the box labeled “Factor,” then click OK. If Method fails to appear in the list of available variables, a few more steps are required. SPSS only allows numeric variables to serve as the factor in ANOVA. Because the Method identifies test conditions by their names (i.e., strings of characters), we must first create a new variable that replaces those with numeric values. Using the Recode into Different options in the Transform menu, move Method to the Input-Variable in the middle box, and type a new variable name in the Output variable. Let's call it FactorA. Then, click “change” and “Old and New Values.” In the window pops up, enter each Method name (e.g., Control) and a numeric Value (e.g., 1), then press “Add.” Once all levels of Method have been assigned new values, click “Continue” to see FactorA in the Data View. Now the ANOVA can be run as described, using FactorA as the factor.

# 8.5 Measures of Importance

The p-value in Table 8.3 informs us that the effects of the method of memorization are statistically significant, if p = .05. In addition, we need some indication of practical or theoretical importance of our result. Generally, we need a measure that assesses the magnitude of the effect of our treatment. We will find that the EMS analyses guided the logic of the F test are also very useful in about appropriate ways in which assess the importance of an effect. We will consider several possible measures in this section. Several sources also present discussions of these and other measures (e.g., Kirk, 1996; Maxwell, Camp & Arvey, 1981; Olejnik & Algina, 2000, 2003).

# 8.5.1 Measuring Strength of Association in the Sample: η² (Eta-Squared)

Greek-letter designs are usually reserved for proportion, but η² is a sample statistic that is often used as a measure of association between the dependent and independent variables (Cohen, Cohen, West, & Aiken, 2003). It describes the proportion of variability in the sample that is primarily attributable to the treatment factor as

> η² = \frac{SS_{A}}{SS_{total}} (8.9)

Referring to Table 8.3, we have

η²_{method} = 173.9/819.9 = .212

Eta-squared has the advantage of being easily calculated and easily understood as a proportion of sample variability. However, the value of η² is influenced not only by the relative magnitudes of the treatment effect and error variance, but also by design choices and sample size details that don't associate with a population effect: n, df_{A}, and df_{error}. That is, η² is influenced by the number of levels of an experimental factor (df_{A}) and even by the spacing of the levels (Okada & Hoshino, 2017). In addition, σ²r corresponds to the numerator of η², meaning that η² is a positively biased estimator. For these reasons, other statistics that