![](bbox=[0.198, 0.093, 0.873, 0.483])

**FIGURE 4.14** A Histogram to Display IQ Scores.

# PLOT A BEST-FITTING LINE IN MATPLOTLIB

Listing 4.15 displays the contents of plot-best-fit2.py that illustrates how to plot a best-fitting line in Matplotlib.

**LISTING 4.15:** plot-best-fit2.py

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
/
```