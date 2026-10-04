```
double betatz0 = zmean - (betatz1 * tmean); // Calculating y-intercept

// Creating a count to retrieve actual values depending on the position of
tpredicted value
int count = 0;
for (int n = 0; n < (window - a + pmin); n++) {
  if (count == (window + (a - 1) + pmin)) {
    // Fetching the actual value
    actual_s = pacRec[count];
  }
  count++;
}
```

```
// Using the inner class to input the independent variables (x2) and the
dependent variable (y2)
MultipleLinearRegression regression = new MultipleLinearRegression(x2,
y2);
System.out.println();
```

```
// Calculating the predicted value using the new coefficients from the
class
double newpred_xr = betatz0 + (betatz1 * time[pvalue]);
double newpred_zr = betatz2 + (betatz1 * time[pvalue]);
```

```
double newbeta0 = regression.beta(0); // intercept
double newbeta1 = regression.beta(1); // slope 1
double newbeta2 = regression.beta(2); // slope 2
```

```
// Calculating the predicted variable using the general formula
of coefficients
mlPrediction = newbeta0 + newbeta1 * newpred_xr + newbeta2 * newpred_zr;
```

```
// Finding individual errors by comparing the predicted value to the
actual one
double mlr_percent_error;
if (actual_s == 0) {
  mlr_percent_error = ((Math.abs(mlrPrediction - actual_s)) / 1) * 100;
} else {
  mlr_percent_error = ((Math.abs(mlrPrediction - actual_s)) / actual_s);
}
```

```
// Putting all the individual errors in an array
mlr_errors[a] = mlr_percent_error;
```

```
// Printing information for MLR on the console
System.out.println("Actual value for row " + (window + (a - 1) + pmin + 1)
+ + " is: " + actual_s);
```