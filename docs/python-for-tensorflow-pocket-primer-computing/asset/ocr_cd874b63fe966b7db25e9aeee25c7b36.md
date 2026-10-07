Earlier in this chapter you saw examples of lines in the plane, including horizontal, slanted, and parallel lines. Most of those lines have a positive slope and a non-zero value for their y-intercept. Although there are scatterplots of data points in the plane where the best fitting line has a negative slope, the examples in this book involve scatterplots whose best fitting line has a positive slope.

Listing 2.22 displays the contents of plot-best-fit2.py that illustrates how to determine the best fitting line for a set of points in the Euclidean plane. The solution is based on so-called “closed form” formulas that are available from Statistics.

# LISTING 2.22: plot-best-fit.py

```
import numpy as np
```

```
xs = np.array([1,2,3,4,5], dtype=np.float64)
ys = np.array([1,2,3,4,5], dtype=np.float64)
```

```
def best_fit_slope(xs,ys):
    m = (((np.mean(xs)*np.mean(ys))-np.mean(xs*ys))
         ((np.mean(xs)**2) - np.mean(xs**xs)))
    b = np.mean(ys) - m*np.mean(xs)
    return m, b
```

```
m,b = best_fit_slope(xs,ys)
print('m:',m,'b:',b)
```

Listing 2.22 starts with two NumPy arrays xs and ys that are initialized with the first five positive integers. The Python function best_fit_slope() calculate the optimal values of m (the slope) and b (the y-intercept) of a set of numbers. The output from Listing 2.22 is here:

```
m: 1.0 b: 0.0
```