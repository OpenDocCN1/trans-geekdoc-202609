# Chapter 8 : Part 5

# Deep Learning
ANN: Predict Data-point

Here we already trained our ANN, using the given data (six-month observation of customers of a Bank). We have to predict if the customer will leave or stay in the bank using our ANN-model that we just built. The new data is given below:

+   - Use our ANN model to predict the following informations will leave the bank:

| Geography: | France |
|---|---|
| Credit Score: | 600 |
| Gender: | Male |
| Age: | 40 years old |
| Tenure: | 3 years |
| Balance: | $50000 |
| Number of Products: | 2 |
| Does this customer have a credit card? | Yes |
| Is this customer an Active Member: | Yes |
| Estimated Salary: | $50000 |

+   What we need to:
[1] Arrange the new data in correct order (same order of our data-set).
[2] Find the right dummy variable for categorical variables (Geography, Gender, etc.).
[3] Transform the data into a NumPy array.
[4] Scale the data-point,
[5] Make the prediction by converting the probability.

So how should we go to customer?

Arrange the new data in correct order Let's compare our original data-set to Encoded-data-set feature-X
ie. Feature-X after encoding-categorical data and before train-split and feature-scaling, so that we can compare the variables to original data.

# Original-Data-DataFrame

| Index | Row | Customer | Surname | CreditScore | Geography | Gender | Age | Tenure | Balance | NumProducts | HasCard | ActiveMember | EstimatedSalary | Exited |
|---|---|---|---|---|---|---|---|---|---|---|---|---||
| 0 | 1564662 | Herwig | France | Female | 41 | | | | 1 | | 191349 | 0 |
| 1 | 1564711 | Green | Spain | Female | 41 | | | 83087.0 | 1 | | 112542 | 0 |
| 2 | 1561938 | Oniso | France | Female | 42 | | | 159963.5 | 1 | | 119532 | 1 |
| 3 | 1570155 | Buli | Germany | Female | 39 | | | | | | 53286.6 |
| 4 | 1573768 | Mitchell | Spain | Female | 43 | | | 12551.1 | 1 | | 79084.1 | 0 |
| 5 | 1557841 | Chuo | Spain | Female | 45 | | | 114756.2 | 1 | | 149757 | 1 |
| 6 | 1593251 | Bartlett | France | Male | 50 | | | | 1 | | 10082.0 | 0 |
| 7 | 1556168 | Obinna | Germany | Female | 29 | | | 115947 | 1 | | 119347 | 1 |
| 8 | 1579213 | Me | France | Male | 44 | | | 142031 | 2 | 1 | | 74048.5 | 0 |

# Encoded-feature-matrix X

X-NumPy array read()

| | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---|---|---|---|---|---|---|---|---|---|-|
| 0 | 0.0 | 619 | | | | | | 42.0 | 0 | | 1 | 191348.8 |
| 1 | 1.0 | 608 | | | | | | 41.0 | 0 | | 1 | 11254.8 |
| 2 | 0.0 | 502 | 42 | | | | | 159608.3 | 1 | | 1 | 119531.7 |
| 3 | 0.0 | 699 | 39 | | | | | 125082.1 | 1 | | 1 | 53286.6 |
| 4 | 1.0 | 850 | 43 | | | | | 117758.2 | 1 | 79084.1 | |
| 5 | 1.0 | 645 | 44 | | | | | | | 1 | 149756.1 | |
| 6 | 0.0 | 822 | 1 | 58 | | | 7.0 | 0 | | 18862.1 | |
| 7 | 1.0 | 376 | 38 | | | | | 142031.2 | 1 | | 11936.8 | |
| 8 | 0.0 | 500 | 44 | | | | | | | | | 74048.5 |

```
new_dt_price = np.array([[0.0, 0.0, 600, 1, 40, 3, 60000.0, 2, 1, 1, 50000.0]])
```

> From row no. 0 and 7 we notice France = (0.0, 0.0, 0.0, 1.0), Germany = (1.0, 0.0, 0.0) represented using the dummy variables.