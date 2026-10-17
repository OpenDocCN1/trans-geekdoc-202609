# A.8 Abalone Dataset

The Abalone Dataset involves predicting the age of abalone given objective measures of individuals. It is a multiclass classification problem, but can also be framed as a regression. The number of observations for each class is not balanced. There are 4,177 observations with 8 input variables and 1 output variable. The variable names are as follows:

+   1. Sex (M, F, I).
+   2. Length.
+   3. Diameter.
+   4. Height.
+   5. Whole weight.
+   6. Shucked weight.
+   7. Viscera weight.
+   8. Shell weight.
+   9. Rings.

The baseline performance of predicting the most prevalent class is a classification accuracy of approximately 16%. The baseline performance of predicting the mean value is an RMSE of approximately 3.2 rings. A sample of the first 5 rows is listed below.

```
M,0.455,0.365,0.095,0.514,0.2245,0.101,0.15,15
M,0.35,0.265,0.09,0.2255,0.0995,0.0485,0.07,7
F,0.53,0.42,0.135,0.677,0.2565,0.1415,0.21,9
M,0.44,0.365,0.125,0.516,0.2155,0.114,0.155,10
I,0.33,0.255,0.08,0.205,0.0895,0.0395,0.055,7
```

Listing A.6: Sample of the Abalone Dataset.

+   - Download: https://goo.gl/BDYgh5
+   - More Information: https://goo.gl/ieNz0R

# A.9 Ionosphere Dataset

The Ionosphere Dataset requires the prediction of structure in the atmosphere given radar returns targeting free electrons in the ionosphere. It is a binary (2-class) classification problem. The number of observations for each class is not balanced. There are 351 observations with 34 input variables and 1 output variable. The variable names are as follows:

+   1. 17 pairs of radar return data.
+   2. ...