```
plt.plot(points[:,0],points[:,1],'ro')
plt.show()
```

Listing 4.4 defines the NumPy variable points that define a 2D
list of points with three rows and four columns. The Pyplot API
plot() uses the points variable to display a grid-like pattern.

Figure 4.4 displays a grid of points as defined in Listing 4.3.

![](bbox=[0.203, 0.276, 0.846, 0.646])

FIGURE 4.4 A Grid of Points.

# A DOTTED GRID IN MATPLOTLIB

Listing 4.5 displays the contents of plotdottedgrid1.py that
illust how to plot a “dotted” grid pattern.

LISTING 4.5: plotdottedgrid1.py

```
import numpy as np
```