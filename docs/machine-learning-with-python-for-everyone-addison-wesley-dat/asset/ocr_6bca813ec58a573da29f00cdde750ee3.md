```
ax.plot(xs, ys)

# better Python:
# pt = co.namedtuple('Point', ['x', 'y'])(3,3**2)
pt_x, pt_y = 3, 3**2
ax.plot(pt_x, pt_y, 'ro')

line_xs = pt_x + np.array([-2, 2])
# line ys = mid_point + (x amount) * slope_of_line
# one step right gets one "slope of line" increase in that line's up
line_ys = 3**2 + (line_xs - pt_x) * (2 * pt_x)
ax.plot(line_xs, line_ys, 'r-')
ax.set_xlabel('weight')
ax.set_ylabel('cost');
```

![](bbox=[0.29, 0.44, 0.68, 0.69])

In this simple example, if we put an imaginary ball at the red dot, it would roll downward to the left. The red line represents the slope—how steep the blue graph is—at that point. You can imagine that if we are trying to find a low point, we want to follow the slope—with Jack and Jill down the proverbial hill. You might also find it reasonable to be more confident in our direction if the slope is steeper—that is, we can roll down the hill faster if there is a steeper slope. If we do that, here's one take on what can happen.

From the starting point of weight = 3 that we just saw, we can take a step down the hill by moving to the left. We'll take a step that is moderated by the slope at our current point. Then we'll repeat the process. We'll try this ten times and see what happens. Note that we could have picked the starting point randomly—we'd have to be pretty lucky for it to be the minimum.

In [3]:

```
weights = np.linspace(-5,5)
costs   = weights**2
```