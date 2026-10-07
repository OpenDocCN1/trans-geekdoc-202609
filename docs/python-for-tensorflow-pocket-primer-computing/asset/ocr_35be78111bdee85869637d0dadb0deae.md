Listing 4.11 displays the contents of simple-line.py illustrates how to plot a simple line in Matplotlib.

# LISTING 4.11: simple-line.py

```
import numpy as np
import matplotlib.pyplot as plt
x = [7,11,13,15,17,19,23,29,31,37]
plt.plot(x) # OR: plt.plot(x, 'ro-') or bo
plt.ylabel('Height')
plt.xlabel('Weight')
plt.show()
```

Listing 4.11 defines the array x that contains a hard-coded set of values. The Pyplot API plot() uses the variable x to display a line segment. Figure 4.11 displays a simple line based on the code in Listing 4.11.