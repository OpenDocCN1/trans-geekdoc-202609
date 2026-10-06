# 4.9 Project: Predicting Wine Color with Several Chemical Properties

We start calculating sensitivity from the *confusion matrix*: 480 wines (the sum of the left column) in the testing dataset are red wines (positive class). From these red wines, 436 were predicted correctly. We can calculate sensitivity as follows:

```
$Specificity = \frac{TP}{TP + FN} = \frac{436}{436 + 44} = 0.9083$
```

Specificity is calculated similarly, but we focus on the right column of the *confusion matrix*: 480 wines (the sum of the entries in the right column) in the testing dataset are white wines (negative class). From these white wines, 434 were predicted correctly. Therefore we can calculate specificity as follows:

```
$Specificity = \frac{TN}{FP + TN} = \frac{434}{46 + 434} = 0.9042$
```

To summarize, based on the dataset, the overall *accuracy* (proportion of correctly predicted wines) was 90.62%, *sensitivity* (proportion of correctly predicted red wines) was 90.83%, and *specificity* (proportion of correctly predicted white wines) was 90.42%.

For the analysis in this section, we used only two predictor (sulfur dioxide content and acidity of the wines). In the following section, you will repeat the analysis with your own model, but you will use all available predictor variables to improve the predictive quality further.

# 4.9 Project: Predicting Wine Color with Several Chemical Properties

Interactive Section
In this section, you will find content together with R code to execute, change, and rerun in RStudio.

The best way to read and work with this section is to open it with RStudio. Then you can interactively with R code exercises and R projects within a web browser. This way can apply what you have learned so far and extend your knowledge. You can also choose to continue reading in the book or online, but you will not benefit from the interactive learning experience.

> Besides *accuracy, sensitivity, and specificity*, many other metrics can be calculated from a *confusion matrix*. Lyer (2021) provides a good overview together with an introduction to confusion matrices.