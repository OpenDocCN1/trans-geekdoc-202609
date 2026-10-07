# HORIZONTAL LINES IN MATPLOTLIB

Listing 4.1 displays the contents of hlines1.py that illustrates how to plot horizontal lines using matplotlib. Recall that the equation of a non-vertical line in the 2D plane is y = m*x + b, where m is the slope of the line and b is the y-intercept of the line.

# LISTING 4.1: hlines1.py

```
import numpy as np
import matplotlib.pyplot as plt

# top line
x1 = np.linspace(-5,5,num=200)
y1 = 4 + 0*x1

# middle line
x2 = np.linspace(-5,5,num=200)
y2 = 0 + 0*x2

# bottom line
x3 = np.linspace(-5,5,num=200)
y3 = -3 + 0*x3

plt.axis([-5, 5, -5, 5])
plt.plot(x1,y1)
plt.plot(x2,y2)
plt.plot(x3,y3)
plt.show()
```

Listing 4.1 uses the np.linspace() API in order to generate a list of 200 equally spaced numbers for the horizontal axis, all of which are between -5 and 5. The three lines defined via the variables y1, y2, and y3, are defined in terms of the variables x1, x2, and x3, respectively.