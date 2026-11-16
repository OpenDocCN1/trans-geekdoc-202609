training m sub-sample sets, m regression trees are constructed and the remaining samples are used as the test set to verify the prediction effect of the model. Then, set the regression model parameter “mtry”. Assuming that there are k evaluation features of the fabric sample, randomly select a subset of mtry features (mtry < k) as the splitting node and determine the best splitting based on the optimal branching criterion. Finally, each regression tree stops growing based on the number of trees (ntree), and after training, m decision trees are generated to form a Random Forest regression model. The arithmetic mean of the training results of the m decision trees is taken as the final model prediction result. The Random Forest prediction model is shown in Figure 1. The prediction effect of the model is evaluated using the root mean square error (RMSE) and the coefficient of determination (R²) of the test set as shown in the following formula:

```
$$RMSE = \sum_{n=1}^{i} (y_i - y'_i)^2 / n$$
```

```
$$R^2 = 1 - RMSE / Y^2$$
```

where $y_i$ represents the true value of the test sample in the test set, $y'_i$ represents the predicted value of the regression model, $Y^2$ represents the variance of the predicted value, and $n$ is the number of samples in the test set.

![](bbox=[0.07, 0.42, 0.93, 0.57])

Figure 1. Random Forest regression model.

# 3. Experimental Section

# 3.1. Materials

This study involves analyzing the thermal contact coolness of multiple types of wet fabrics. All samples were selected from commonly used clothing fabrics in the market, and included fabrics of different materials and types. The parameters of all the fabrics are shown in Table 1. Before the experiment, the fabrics were subjected to low-temperature ironing to ensure a smooth surface. Then, the samples were cut into pieces with a length and width of 0.3 m and stored for later use after being placed in a room with a temperature of 24 °C and relative humidity of 65% for 24 h. Ionized water made in the laboratory was used to wet the fabrics.

The fabric thickness and surface density can be directly measured. There are many methods for measuring fabric porosity. In this study, fabric surface density, fabric thickness, and fabric fiber density were used to calculate the porosity [22] (see Equation (11)).

```
$$\varepsilon = 1 - \frac{m}{h \cdot \rho_{fib}}$$
```

where $\varepsilon$ is the porosity of the fabric, %; $\rho_{fib}$ is the fiber density at the stipulated regain, g/m³; and $m$ is the measured surface density of the fabric, g/m³.