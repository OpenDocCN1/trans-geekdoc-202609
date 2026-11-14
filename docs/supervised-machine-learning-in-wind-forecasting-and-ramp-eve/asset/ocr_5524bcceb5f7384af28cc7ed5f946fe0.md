![](bbox=[0.285, 0.095, 0.755, 0.315])

Figure 5.6 XBoost algorithm for gradient boosted machines.

given as

```
\frac{\partial L(y, \hat{y})}{\partial \hat{y}_i} = \frac{\partial}{\partial \hat{y}_i} \sum_{i=1}^N |y_i - \hat{y}_i| = -sign(y_i - \hat{y}_i). \quad (5.7)
```

The accuracy of a GBM model depends on the number of weak learners and the learning rate. Further, the essence of a GBM model lies in the boosting technique, which combines all the weak models in a stagewise manner and then in a parallel manner, as seen in the random forest model. Mathematically, the GBM model in recursive form is given as

```
F_m(x) = F_{m-1}(x) + \eta \Delta_m(x), \quad (5.8)
```

where \(\eta\) represents the learning rate, and \(\Delta_m\) refers to a regression model fitted to the residuals. Fig. 5.6 illustrates the XBoost algorithm used for obtaining the best regressor.

In our wind speed prediction simulations, the source codes for random forest and GBM are presented in Appendices A.4 and A.5, respectively.

Song et al. [9] presented a GBM model for predicting clathrate hydrate phase equilibria in salts. The inputs to the model include 11 variables in terms of gases like CH$_4$, CO$_2$, and N$_2$ and salts KCl and NaCl. Two models for deep neural network (DNN) and gradient boosted regression trees with pressure and temperature as outputs are used. Results reveal that the GBM model outperforms DNN for both temperature and pressure as inputs to the model. Further, the GBM model based on temperature as output gave better performance than the GBM model based on pressure.