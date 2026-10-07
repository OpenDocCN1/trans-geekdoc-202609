We have labeled data for temperatures at any place classified as 0 for HOT and 1 for COLD, as shown in Figure 4.10.

| Temperature (x1) | Weather (y) |
|---|---|
| 40 | 0 |
| 2 | 1 |
| -3 | 1 |
| 10 | 1 |
| 20 | 0 |
| 30 | 0 |
| 4 | 1 |
| 7 | 1 |
| 22 | 0 |
| 50 | 0 |
| 60 | 0 |
| -5 | 1 |
| 4 | 1 |
| 6 | 1 |
| 32 | 0 |

> 0 - HOT
1 - COLD

Figure 4.10: Weather data for classification

So, we have independent variable (), and the dependent variable is y.
So, we need to form a linear relationship as follows:

$y = a_0 + a_1x_1$

As this is a classification problem, we will form the Sigmoid function as follows:

$$\sigma(y) = \frac{1}{1+e^{-y}} = \frac{1}{1+e^{-(a_0+a_1x_1)}}$

You can follow the provided Python program to create the Logistic Regression model:

```
X = [40, 2, -3, 10, 20, 30, 4, 7, 22, 50, 60, -5, 4, 6, 32]
y = [0, 1, 1, 1, 0, 0, 1, 1, 0, 0, 0, 1, 1, 1, 0]

import pandas as pd
```