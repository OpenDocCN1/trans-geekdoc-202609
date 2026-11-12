
## Table 2. Top-3 subgroups per dataset maximizing \(\varphi_{\text{raul}}\).

| \(\Omega_i\) | Most certain subgroups S | \(\varphi_{\text{raul}}(S)\) |
|---|---|---|
| \(\Omega_1\) | free sulfur dioxide > 130.444 and alcohol > 10.756 | 1.471 |
| | free sulfur dioxide > 130.444 and sulphates \(\le\) 0.507 | 1.471 |
| | free sulfur dioxide > 130.444 and sulphates \(\le\) 0.411 | 1.471 |
| \(\Omega_2\) | self reference max shares > 562200.000 | 7.082 |
| | and self reference avg shares \(\le\) 76711.111 | |
| | self reference max shares > 749600.000 | 6.532 |
| | and min negative polarity \(\le\) -0.667 | |
| | self reference max shares > 562200.000 | 6.282 |
| | and num self hrefs > 25.778 | |
| \(\Omega_3\) | V12 > 226.693 and V10 \(\le\) 170.078 | 30.025 |
| | V21 \(\le\) -14.767 and V12 > 198.388 | 29.809 |
| | V21 \(\le\) -14.767 and V19 > 77.927 | 29.612 |
| \(\Omega_4\) | Hillshade Noon \(\le\) 56.444 | 0.085 |
| | and Horizontal Distance To Fire Points \(\le\) 7173.000 | |
| | Hillshade Noon \(\le\) 56.444 | 0.085 |
| | and Horizontal Distance To Fire Points \(\le\) 6376.000 | |
| | Hillshade Noon \(\le\) 56.444 | 0.085 |
| | and Horizontal Distance To Fire Points \(\le\) 5579.000 | |
| \(\Omega_5\) | GLUCOSE > 538.333 and SODIUM \(\le\) 135.667 | 136.275 |
| | GLUCOSE > 538.333 and ALBUMIN > 3.133 | 133.106 |
| | GLUCOSE > 538.333 and CHLORIDE \(\le\) 106.000 | 132.774 |
| \(\Omega_6\) | population > 3967.333 and households \(\le\) 1352.333 | 51232.926 |
| | population > 3967.333 and total rooms \(\le\) 8432.000 | 51137.378 |
| | longitude > -115.426 and median income \(\le\) 2.111 | 49965.760 |
| \(\Omega_7\) | V35 \(\le\) -342.419 and V6 \(\le\) -1.723 | 10.106 |
| | V35 \(\le\) -342.419 and V1 > 41.529 | 9.671 |
| | V3 \(\le\) -94.950 and V35 \(\le\) -201.227 | 9.655 |

On the other hand, when comparing the final columns of Tables 1 and 3, the values for the datasets Wine Quality (\(\Omega_1\)) and News Popularity (\(\Omega_2\)) stand out. For the subgroups found on these datasets, we see that \(\varphi_{\text{raul}}\) is smaller than \(AUL(\Omega_i)\), which implies that the average uncertainty loss of the top-ranked subgroups is just larger than average uncertainty loss on the entire dataset. I.e.: Conformalized EMM discovered subgroups for which classifiers are highly unconfident about their prediction set. We notice that for News Popularity dataset, the discovered subgroups demonstrate an uncertainty set of size 10, which is the largest set we encountered within our experiments: Conformalized EMM identified the prediction that contains all the possible labels in the prediction set, which shows the most uncertain performance.

## Table 3. Top-3 subgroups per dataset minimizing \(\varphi_{\text{raul}}\).

| \(\Omega_i\) | Most uncertain subgroups S | \(\varphi_{\text{raul}}(S)\) |
|---|---|---|
| \(\Omega_1\) | sulphates > 0.984 and total sulfur dioxide > 152.667 | −2.529 |
| | sulphates > 0.984 and free sulfur dioxide \(\le\) 33.889 | −1.529 |
| | chlorides > 0.271 and sulphates \(\le\) 0.507 | −1.529 |
| \(\Omega_2\) | LDA 04 > 0.927 and abs title sentiment polarity \(\le\) 1.000 | −1.622 |
| | LDA 04 > 0.927 and abs title sentiment polarity > 0.333 | −1.622 |
| | LDA 04 > 0.927 and abs title sentiment polarity > 0.222 | −1.622 |
| \(\Omega_3\) | V11 \(\le\) 28.576 and V2 \(\le\) 0.342 | −17.820 |
| | V11 \(\le\) 28.576 and V6 \(\le\) 0.371 | −17.276 |
| | V2 \(\le\) 0.122 and V10 \(\le\) 56.849 | −17.271 |
| \(\Omega_4\) | Horizontal Distance To Fire Points > 6376.000 and Hillshade 3pm > 225.778 | −0.790 |
| | Horizontal Distance To Fire Points > 6376.000 and Hillshade 9am \(\le\) 112.889 | −0.790 |
| | Elevation \(\le\) 2525.333 and Horizontal Distance To Fire Points > 5579.000 | −0.665 |
| \(\Omega_5\) | BUN > 87.667 and ALBUMIN \(\le\) 2.600 | −114.185 |
| | ALBUMIN \(\le\) 2.067 and HEMOGLOBIN > 10.867 | −108.213 |
| | ALBUMIN \(\le\) 2.067 and HEMATOCRIT > 32.100 | −98.418 |
| \(\Omega_6\) | median income > 6.944 and housing median age > 46.333 | −117202.286 |
| | median income > 6.944 and housing median age > 40.667 | −115196.680 |
| | median income > 8.556 and housing median age > 46.333 | −114451.983 |
| \(\Omega_7\) | V6 > 8.905 and V2 \(\le\) −164.854 | −18.338 |
| | V3 > 214.741 and V35 \(\le\) 118.308 | −17.146 |
| | V3 > 214.741 and V24 \(\le\) 1054.198 | −17.146 |

## 6 Conclusion

We introduce Conformalized Exceptional Model Mining (Conformalized EMM): a method to discover subgroups in a dataset where a multi-class classifier or regressor is exceptionally certain or uncertain about its own prediction. We express this (un)certainty in terms of the size of the Adaptive Prediction Set for multi-class classification problems, and the interval length in Conformalized Quantile Regression for regression problems. The (un)certainty expression is subsequently fed to the mSMoPE (multiplex Soft Model Performance Evaluation) model class for EMM, discovering exceptional subgroups evaluated by the Average Uncertainty Loss, a quantity expressing how well the soft model outputs can represent the confidence of the model predictions. The quality measure \(\varphi_{\text{raul}}\) is designed to find coherent subspaces of the dataset where the soft model performs highly certain (when maximizing \(\varphi_{\text{raul}}\)), highly uncertain (when minimizing \(\varphi_{\text{raul}}\)) or exceptional (when maximizing \(|\varphi_{\text{raul}}|\)). Since EMM results in easily interpretable subgroups, our focus is not on letting the machine improve the machine: the primary goal in the mSMoPE model class for EMM is to provide a better understanding to the domain expert.

We illustrate the findings one could expect from the mSMoPE model class by experiments on seven datasets. Some discovered subgroups are troublesome for our model, and some subgroups are found where our model has barely any problems. The mSMoPE model class highlights as a particularly troublesome area a subgroup in News Popularity dataset whose characterizing feature is associated with all the classes in the dataset, and as a particularly benign area a subgroup that is associated with one particular class. Overall, when maximizing \(\varphi_{\text{raul}}\), one easily finds small subgroups on which the soft model performs highly certain; the subgroups on which the soft model performs highly uncertain are typically less trivial, hence they demand further attention. The mSMoPE model class for EMM helps to understand multi-class classification and regression, which leads to ideas on how to improve the overall classifier or regressor performance.

### Acknowledgments.
This work was supported by National Natural Science Foundation of China (NSFC) under Grant No.62476047. This work was partly supported by H2020 SmartChange project, funded within EU's Horizon Europe research program (GA No. 101080965) and NWO EDIC project.

### Disclosure of Interests.
The authors have no competing interests to declare that are relevant to the content of this article.

## References

- 1. Agrawal, R., Srikant, R.: Fast algorithms for mining association rules in large databases. In: Proceedings of the VLDB, pp. 487–499 (1994)
- 2. Ahmad, M.A., Eckert, C., Teredesai, A.: Interpretable machine learning in healthcare. In: ICBCHI, pp. 559–560 (2018)
- 3. Angelopoulos, A.N., Bates, S., Fannjiang, C., Jordan, M.I., Zrnic, T.: Prediction-powered inference. Science **382**(6671), 669–674 (2023)
- 4. Angelopoulos, A.N., Bates, S., Jordan, M., Malik, J.: Uncertainty sets for image classifiers using conformal prediction. In: ICLR (2020)
- 5. Arora, R., Basu, A., Mianjy, P., Mukherjee, A.: Understanding deep neural networks with rectified linear units. In: ICLR (2018)
- 6. Arrieta, A.B., et al.: Explainable artificial intelligence (xai): concepts, taxonomies, opportunities and challenges toward responsible ai. Inform. Fusion **58**, 82–115 (2020)
- 7. Atzmueller, M.: Subgroup discovery. WIREs Data Mining Knowl. Discov. **5**(1), 35–49 (2015)
- 8. Bay, S.D., Pazzani, M.J.: Detecting group differences: mining contrast sets. DMKD **5**, 213–246 (2001)
- 9. Bertin-Mahieux, T., Ellis, D.P., Whitman, B., Lamere, P.: The million song dataset. In: ICMIR (2011)
