# CHAPTER 8 LOCAL MODEL-AGNOSTIC METHODS

on the conditional expected prediction. With the change in the value function, features that have no influence on the prediction can get a TreeSHAP value different from zero.

The disadvantages of Shapley values also apply to SHAP: Shapley values **can be misinterpreted** and access to data is needed to compute them for new data (except for TreeSHAP).

It is **possible to create intentionally misleading interpretations** with SHAP, which can hide biases $^{46}$. If you are the data scientist creating the explanations, this is not an actual problem (it would be an advantage if you are the evil data scientist who wants to create misleading explanations). For the receivers of a SHAP explanation, it is a disadvantage: they cannot be sure about the truthfulness of explanation.

# 8.6.12 Software

The authors implemented SHAP in the shap$^{47}$ Python package. This implementation works for tree-based models in the scikit-learn$^{48}$ machine learning library for Python. The shape package was also used for the examples in this chapter. SHAP is integrated into the tree boosting frameworks xgboost$^{49}$ and LightGBM$^{50}$. In R, there are the shapper$^{51}$ and fastshap$^{52}$ packages. SHAP is also included in the R xgboost$^{53}$ package.

> $46}$Slack, Dylan, Sophie Hilgard, Emily Jia, Sameer Singh, and Himabindu Lakkaraju. "Fooling lime and shap: Adversarial attacks on post hoc explanation methods." In Proceedings of the AAAI/ACM Conference on AI, Ethics, and Society, pp. 180-186 (2020).
$^{47}$https://github.com/slundberg/shap
$^{48}$https://scikit-learn.org/stable/
$^{49}$https://github.com/dmlc/xgboost/tree/master/python-package
$^{50}$https://github.com/microsoft/LightGBM
$^{51}$https://modelatorit.github.io/shapper/
$^{52}$https://github.com/bengreenwell/fastshap
$^{53}$https://rdrr.org/cran/xgboost/man/plot.shap.html