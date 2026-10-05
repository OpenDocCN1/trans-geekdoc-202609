# Editors and Other Tools

The Jupyter Notebook now contains support for q and the kernel can be accessed at just (b). It brings functionalities like syntax highlighting, code completion, loading of scripts, and mainly the inline display of charts created through embedPy and matplotlib. The aforementioned library, embedPy, which allows integration of Python to q. Figure 4.2 shows an example of code run through jupyterq and an example usage of the notebook in conjunction with matplotlib.

A slight disadvantage may be encountered when using jupyterq its speed. In q, we can achieve an amazing speed of execution on large data sets without needing to install further libraries. In some cases, Jupyterq can be a performance bottleneck, and tasks like data exploration would be affected, compared to other tools. The advantage of the notebook is in sharing code and data extracts with people, as well as the extra plotting libraries. The following tools we should cover be more adapted to development and data exploration in q and offer some basic plotting, depending on one use case, i. whether one needs to navigate through much

![](bbox=[0.104, 0.373, 0.896, 0.863])

```
In [22]:
examples/import matplotlib.pyplot as plt
n:50
t=50
y=5*n75
y.flip(y:10 mavg y;avgs y)
matplotlib.pyplot as plt
plt.plot(x,y)
plt.xlabel("X values")nplt.ylabel("Y values")nplt.title("a timeseries using pyplot")nplt.show();
```

**FIGURE 4.2** Jupyterq Chart window