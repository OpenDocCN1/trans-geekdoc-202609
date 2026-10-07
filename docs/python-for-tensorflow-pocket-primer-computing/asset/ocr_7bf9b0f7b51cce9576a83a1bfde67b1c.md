FIGURE 4.7 A Colored Grid of Line Segments.

# A COLORED SQUARE IN AN UNLABELED GRID IN MATPLOTLIB

Listing 4.8 displays the contents of plotgrid3.py that illustrates how to display a colored square inside a grid.

# LISTING 4.8: plotgrid3.py

```
import matplotlib.pyplot as plt
import numpy as np
from itertools import product
import matplotlib.pyplot as plt
import matplotlib.colors as colors

N = 15
# create an empty data set
data = np.ones((N, N)) * np.nan

# fill in some fake data
for j in range(3)[: -1]:
    data[N//2 - j : N//2 + j +1, N//2 - j : N//2 + j +1] = j

# make a figure + axes
fig, ax = plt.subplots(1, 1, tight_layout=True)

# make color map
my_cmap = colors.ListedColormap(['r', 'g', 'b'])

# set the 'bad' values (nan) to be white andntransparent
my_cmap.set_bad(color='w', alpha=0)

# draw the grid
```