In [37]:

```
cov_XY = 0.0
for (x_i, y_i), (x_j, y_j) in it.combinations(zip(X,Y), 2):
    cov_XY += (x_i - x_j) * (y_i - y_j)
print("Cov(X,Y):", cov_XY / (n**2))
```

Cov(X,Y): 21.28

Back to the last equation: 1/(2n²) Σ_{i,j} (x_i − x_j)(y_i − y_j). Using this form, we get a very nice way to interpret covariance. Can you think of a simple calculation that takes x s and y s, subtracts them, and multiplies them? I’ll grab a sip of water while you think about it. Here’s a hint: subtracting values can often be interpreted as a distance: from mile marker 5 to mile marker 10 is 10 − 5 = 5 miles.

OK, time’s up. Let me rewrite the equation by ignoring the leading fraction for a moment: Cov(X, Y) = c_magic Σ_{ij} (x_i − x_j)(y_i − y_j). If you’ve been following along, once again, we have an ever-present dot product. It has a very nice interpretation. If I have a rectangle defined by two points, {x_i, y_i} and {x_j, y_j}, I can get length = x_i − x_j and height = y_i − y_j. From these, I can get the area = length × height = (x_i − x_j)(y_i − y_j). So, if we ignore c_magic, the covariance is simply a sum of areas of rectangles or a sum product of distances. That’s not so bad, is it? The covariance is very closely related to the sum of areas created by looking at each pair of points as corners of a rectangle.

We saw c_magic earlier, so we can deal with the last pain point. Let’s rip the bandage off quickly: c_magic is 1/(2n²). If there were n terms being added up and we had 1/n, we’d be happy talking about the average area. In fact, that’s what we have here. The squared value, 1/n², comes from the double summation. Looping i from 1 to n and j from 1 to n means we have n² total pieces. Averaging means we need to divide by n². The 1/2 comes from not wanting to double-count rectangles.

If we include c_magic = 1/(2n²), the covariance is simply the average area of the rectangles defined by all pairs of points. The area is signed, it has a + or a −, depending on whether the line connecting the points is pointed up or down as it moves left-to-right—the same pattern we saw in Figure 8.6. If the idea of a signed area—an area with a sign attached to it—is making you scratch your head, you’re in good company. We’ll dive into this more with examples and graphics in the following section.

# 8.5.1.3 Visualizing Covariance

Let’s visualize what is going on with these rectangle areas and covariances. If we can think of covariance as areas of rectangles, let’s draw these rectangles. We’ll use a simple example with three data points and two features. We’ll draw the diagonal of each of the three rectangles and we’ll color in the total contributions at each region of the grid. Red indicates a positive overall covariance; blue indicates a negative covariance. Darker colors indicate more covariance in either the positive or negative direction: lighter colors, leading to white, indicate a lack of covariance. Our technique to get the coloring right is to (1) build a NumPy array with the proper values and (2) use matplotlib’s matshow, matrix show, to display that matrix.