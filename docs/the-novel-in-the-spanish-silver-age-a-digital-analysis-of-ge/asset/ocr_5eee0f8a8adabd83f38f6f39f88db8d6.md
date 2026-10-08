offers an explanation for the variation in the classification of the subgenres, the easy-genre-difficult-genre question: Why do some subgenres yield higher results? These results show that once the five characteristics of the categories are obtained (the canonicity of the text, the number of authors, the number of texts, the agreement of the labels in several sources, and the specificity of the features), the researcher can predict almost perfectly accurately an algorithm will be able to classify the subgenre.

The regression analysis also gives a coefficient for each independent variable, which expresses their effect on the regression, shown in the table below.

**Table 15: Coefficients of the regression analysis to predict results of the classification**

| independent variables | coefficient |
| mean kappa | 0.063 |
| number.texts | 0.006 |
| LitHist.pages | -0.006 |
| number.authors | -0.008 |
| std.zscores.features | -0.011 |

The greater the coefficient is in absolute terms, the greater its effect it is on the results of the classification of subgenres. Thus, the positive or negative sign does not only reflect the direction of the correlation. Two variables stand out clearly: the agreement in sources (mean Kappa) and the specificity of features (std.zs-features). These are the variables with the strongest effect on the classification result. These two variables with high coefficients correlate strongly as the others can be seen in Figure 101, while the canonicity has the weakest correlation with the others. In other words, the agreement of the labeling may have a strong effect solely because it correlates with the specificity of the features. This is why I run a second regression analysis leaving the agreement of the labeling and using the remaining four variables as independent variables (i.e. canocity, number of texts, number of authors and specificity of the features). By doing this, I am attempting to predict the classification results with one fewer data point for each category, therefore expecting a lower result. However, this analysis yields a higher R² of 0.63 (p-value of F-statistic < 0.01). The results of the regression analysis improve when one of the correlating variables is ignored.