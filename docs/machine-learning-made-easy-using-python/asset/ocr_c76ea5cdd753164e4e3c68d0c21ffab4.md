# # PyPlot in Matplotlib

matplotlib.pyplot is a collection of functions that make matplotlib work like MATLAB. Each pyplot function makes some change to a figure: e.g., creates a figure, creates a plotting area in a figure, plots some lines in a plotting area, decorates the plot with labels, etc.

To test it yourself, jump to Jupyter Notebook and start of importing the matplotlib.pyplot module.

```
In []: import matplotlib.pyplot as plt
```

To plot a simple graph, use the plot function and pass a list, and then use the show function to view the graph

```
In [1]: import matplotlib.pyplot as mplt
mplt.plot([1,3,6,9])
mplt.show()
```

![](bbox=[0.147, 0.578, 0.797, 0.811])

We have successfully plotted our graph with some random values in a list.

If we want we can name x and y axis using the xlabel and ylabel respectively.