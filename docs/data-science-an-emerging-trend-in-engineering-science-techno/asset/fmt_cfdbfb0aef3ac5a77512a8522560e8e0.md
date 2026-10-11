
# Error Bars and Statistical Visualization

As you know, any statistical data inevitably contains errors. An error in statistics is simply a difference between the measured value and the actual value. Plotting errors on your charts is a way to convey more information. A graphical representation of errors or uncertainties in the measurement is called an **error bar**. It's a line (a cap line, sometimes) drawn from the data point. The line's length shows us how precise the measurement is. A short error bar means that the values are concentrated, and the data is reliable. A long error bar indicates that the values are spread out, and the data is likely to contain errors.

Fortunately, `matplotlib` allows us to add error bars to various plots. They can be applied to:

*   Line charts
*   Area charts
*   Histograms
*   Bar charts
*   Scatterplots
*   Dot plots

## Density Plot

![density plot](image_rsrc9VX.jpg)
![density plot](image_rsrc9VX.jpg)
![density plot](image_rsrc9VX.jpg)
![](image_rsrc9VY.jpg)

**Fig. 5.4 (a) Density Plot**

### Description

Also known as a **Kernel Density Plot** or **Density Trace Graph**.

A Density Plot visualizes the distribution of data over a continuous interval or time period. This chart is a variation of a [Histogram](https://datavizcatalogue.com/methods/histogram.html) that uses [kernel smoothing](https://en.wikipedia.org/wiki/Kernel_smoother) to plot values, allowing for smoother distributions by smoothing out the noise. The peaks of a Density Plot help display where values are concentrated over the interval.

An advantage Density Plots have over Histograms is that they're better at determining the [distribution shape](https://en.wikipedia.org/wiki/Shape_of_the_distribution) because they're not affected by the number of bins used (each bar used in a typical histogram). A Histogram comprising of only 4 bins wouldn't produce a distinguishable enough shape of distribution as a 20-bin Histogram would. However, with Density Plots, this isn't an issue.

### Anatomy

![](image_rsrc9VZ.jpg)

**Fig. 5.4(b) Density Plot in the form of Histogram**

## 5.5 Contour Plot using Matplotlib – Python

Contour plots, also called level plots, are a tool for doing multivariate analysis and visualizing 3-D plots in 2-D space. If we consider X and Y as our variables we want to plot then the response Z will be plotted as slices on the X-Y plane due to which contours are sometimes referred as **Z-slices** or **iso-response**.

Contour plots are widely used to visualize density, altitudes or heights of the mountain as well as in the meteorological department. Due to such wide usage `matplotlib.pyplot` provides a method `contour` to make it easy for us to draw contour plots.

### `matplotlib.pyplot.contour`

The `matplotlib.pyplot.contour()` are usually useful when `Z = f(X, Y)` i.e Z changes as a function of input X and Y. A `contourf()` is also available which allows us to draw filled contours.

**Syntax:** `matplotlib.pyplot.contour([X, Y,] Z, [levels], **kwargs)`

**Parameters:**

*   **X, Y:** 2-D numpy arrays with same shape as Z or 1-D arrays such that `len(X)==M` and `len(Y)==N` (where M and N are rows and columns of Z)
*   **Z:** The height values over which the contour is drawn. Shape is (M, N)
*   **levels:** Determines the number and positions of the contour lines / regions.

Below examples illustrate the `matplotlib.pyplot.contour()` function in matplotlib.pyplot:

#### Example #1: Plotting of Contour using `contour()` which only plots contour lines.

```
# Implementation of matplotlib function
import matplotlib.pyplot as plt
import numpy as np

feature_x = np.arange(0, 50, 2)
feature_y = np.arange(0, 50, 3)

# Creating 2-D grid of features
[X, Y] = np.meshgrid(feature_x, feature_y)

fig, ax = plt.subplots(1, 1)
Z = np.cos(X / 2) + np.sin(Y / 4)

# plots contour lines
ax.contour(X, Y, Z)
ax.set_title('Contour Plot')
ax.set_xlabel('feature_x')
ax.set_ylabel('feature_y')
plt.show()
```

**Output:**

![Example 1](image_rsrc9W0.jpg)

**Fig. 5.5(a) Contour Plot**

#### Example #2: Plotting of contour using `contourf()` which plots filled contours.

```
# Implementation of matplotlib function
import matplotlib.pyplot as plt
import numpy as np

feature_x = np.linspace(-5.0, 3.0, 70)
feature_y = np.linspace(-5.0, 3.0, 70)

# Creating 2-D grid of features
[X, Y] = np.meshgrid(feature_x, feature_y)

fig, ax = plt.subplots(1, 1)
Z = X ** 2 + Y ** 2

# plots filled contour plot
ax.contourf(X, Y, Z)
ax.set_title('Filled Contour Plot')
ax.set_xlabel('feature_x')
ax.set_ylabel('feature_y')
plt.show()
```

**Output:**

![Example 2](image_rsrc9W1.jpg)

**Fig. 5.5 (b) Filled Contour Plot**

## 5.6 Histograms, Binnings, and Density

A simple histogram can be a great first step in understanding a dataset. Matplotlib's histogram function which creates a basic histogram in one line, once the normal boiler-plate imports are done:

```
%matplotlib inline
import numpy as np
import matplotlib.pyplot as plt

plt.style.use('seaborn-white')
data = np.random.randn(1000)
```

![](image_rsrc9W2.jpg)

**Fig. 5.6(a) A Customized Histogram**

The `hist()` function has many options to tune both the calculation and the display; here's an example of a more customized histogram:

```
plt.hist(data, bins=30, normed=True, alpha=0.5,
         histtype='stepfilled', color='steelblue',
         edgecolor='none');
```

![](image_rsrc9W3.jpg)

**Fig. 5.6 (b) A Stepfilled Histogram**

The `plt.hist` docstring has more information on other customization options available. I find this combination of `histtype='stepfilled'` along with some transparency `alpha` to be very useful when comparing histograms of several distributions:

```
x1 = np.random.normal(0, 0.8, 1000)
x2 = np.random.normal(-2, 1, 1000)
x3 = np.random.normal(3, 2, 1000)

kwargs = dict(histtype='stepfilled', alpha=0.3, normed=True, bins=40)

plt.hist(x1, **kwargs)
plt.hist(x2, **kwargs)
plt.hist(x3, **kwargs);
```

![](image_rsrc9W4.jpg)

**Fig. 5.6(c) Random Histogram**

If you would like to simply compute the histogram (that is, count the number of points in a given bin) and not display it, the `np.histogram()` function is available:

```
counts, bin_edges = np.histogram(data, bins=5)
print(counts)
# [ 12 190 468 301  29]
```

### Two-Dimensional Histograms and Binnings

Just as we create histograms in one dimension by dividing the number-line into bins, we can also create histograms in two-dimensions by dividing points among two-dimensional bins. We'll take a brief look at several ways to do this here. We'll start by defining some data—an x and y array drawn from a multivariate Gaussian distribution:

```
mean = [0, 0]
cov = [[1, 1], [1, 2]]
x, y = np.random.multivariate_normal(mean, cov, 10000).T
```

#### `plt.hist2d`: Two-dimensional histogram

One straightforward way to plot a two-dimensional histogram is to use Matplotlib's `plt.hist2d` function:

```
plt.hist2d(x, y, bins=30, cmap='Blues')
counts, xedges, yedges = np.histogram2d(x, y, bins=30)
cb = plt.colorbar()
cb.set_label('counts in bin')
```

![](image_rsrc9W5.jpg)

**Fig. 5.6(d) 2D Histogram**

Just as with `plt.hist`, `plt.hist2d` has a number of extra options to fine-tune the plot and the binning, which are nicely outlined in the function docstring. Further, just as `plt.hist` has a counterpart in `np.histogram`, `plt.hist2d` has a counterpart in `np.histogram2d`, which can be used as follows:

```
counts, xedges, yedges = np.histogram2d(x, y, bins=30)
```

For the generalization of this histogram binning in dimensions higher than two, see the `np.histogramdd` function.

#### `plt.hexbin`: Hexagonal binnings

The two-dimensional histogram creates a tesselation of squares across the axes. Another natural shape for such a tesselation is the regular hexagon. For this purpose, Matplotlib provides the `plt.hexbin` routine, which will represents a two-dimensional dataset binned within a grid of hexagons:

```
plt.hexbin(x, y, gridsize=30, cmap='Blues')
cb = plt.colorbar(label='count in bin')
```

![](image_rsrc9W6.jpg)
