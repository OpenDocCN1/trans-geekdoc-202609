# 9.4.3 Numerical Example: Predicting Prices for Diamonds with a Neural Network

In this section, we will choose an individual diamond (see Table 9.1) and predict its price based on the Neural Network displayed in Figure 9.2 and also based on the prediction Equation (9.8).

# Table 9.1 Sample Diamond from DataDiamonds

| Price | Carat | Clarity |
|--- |--- |--- |
| 506 | 0.3 | 3 |

Table 9.1 shows that the diamond has 0.3 carats ($Carat_i = 0.3$) and a clarity of 3 ($Clarity_i = 3$). All predictors are omitted for now. For the initial prediction that the values of the $eta$ parameters are all randomly chosen:

```
$\beta_1 = 0.1, \beta_2 = -0.9, \beta_3 = 0.5, \beta_4 = -0.1, \beta_5 = 0.8, \beta_6 = 0.6,\n\beta_7 = -0.1, \beta_8 = 0.8, \beta_9 = 0.9$
```

The prediction process is displayed in Figure 9.2. The color of the connectors between the neurons shows if the related parameter is positive (black) or negative (red). The connector's thickness reflects whether the parameter — in absolute terms is small or large. As an exercise, compare the connectors in Figure 9.2 with the randomly chosen $eta$ values.

![](bbox=[0.118, 0.569, 0.879, 0.831])

# FIGURE 9.2 Graphical Representation of a Fitted Neural Network Structure

In the very left in Figure 9.2, you can see that the input neurons I