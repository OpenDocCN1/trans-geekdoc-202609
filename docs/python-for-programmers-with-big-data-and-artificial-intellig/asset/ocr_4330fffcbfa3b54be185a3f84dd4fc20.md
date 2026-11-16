lick here to view code image

```
In [3]: import pandas as pd

In [4]: temps_df = pd.DataFrame(temps, columns=['Fahrenheit', 'Celsius'])

In [5]: axes = temps_df.plot(x='Fahrenheit', y='Celsius', style='.-')

In [6]: y_label = axes.set_ylabel('Celsius')
```

![](bbox=[0.215, 0.2, 0.915, 0.6])

# Components of the Simple Linear Regression Equation

The points along any straight line (in two dimensions) like those shown in the preceding graph can be calculated with the equation:

```
y = mx + b
```

where

+   - m is the line’s slope,
+   - b is the line’s intercept with the y-axis (at x = 0),
+   - x is the independent variable (the date in this example), and
+   - y is the dependent variable (the temperature in this example).

In simple linear regression, y is the predicted value for a given x.