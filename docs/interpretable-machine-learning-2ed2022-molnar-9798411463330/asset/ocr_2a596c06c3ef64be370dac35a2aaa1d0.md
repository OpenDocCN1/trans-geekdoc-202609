# 4.6 RuleFit

decision rule (feature) for the bicycle prediction could be: “temp > 10” and another rule could be “temp > 15 & weather=GOOD”. If the weather is good and the temperature is above 15 degrees, the temperature is automatically greater then. In the cases the second rule applies, the first rule applies as well. The interpretation of the estimated weight for the second rule is: “Assuming all other features remain fixed, the predicted number of bikes increases by $\beta_2$ when the weather is good and temperature above 15 degrees.”. But, it becomes really clear that the ‘all other feature fixed’ is problematic, because if rule 2 applies, rule 1 applies and the interpretation is nonsensical.

# 4.6.5 Software and Alternative

The RuleFit algorithm is implemented in R by Fokkemma and Christoffersen (2017)$^{25}$ and you can find a Python version on GitHub$^{20}$.

A similar framework is skope-rules, a Python module that also extracts rules from performing-rules. It differs in the way it learns the rules. First, skope-rules remove low-performing rules, based on recall and precision thresholds. Then, duplicate and similar rules are removed by performing a selection based on the diversity of logical terms (variable +larger/smaller operator) and performance (F1-score) of the rules. This final step does not rely on using Lasso, but considers only the out-of-bag F1-score and the logical terms which form the rules.

The immodels package$^{28}$ also contains implementations of other rule sets, such as Bayesian rule sets, Boosted rule sets, and SLIPPER rule sets as a Python package with a unified scikit-learn interface.

$25}$Fokkemma, Marjolein, and Benjamin Christoffersen. “Pre: Prediction rule ensembles”. https://CRAN.R-project.org/package=pre (2017).

$26}$https://github.com/christophM/rulefit

$27}$https://github.com/scikit-learn-contrib/skope-rules

$28}$https://github.com/csinva/immodels