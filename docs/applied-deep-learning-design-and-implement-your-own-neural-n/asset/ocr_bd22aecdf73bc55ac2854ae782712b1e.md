![](bbox=[0.35, 0.1, 0.7, 0.32])

Figure 4.32: Detection of an edge and perpendicular gradient vector

# # Image gradient operators

To calculate the image gradient, we need to calculate the partial derivatives with respect to x and y, that is, \(\frac{\partial f}{\partial x}(x, y)\) and \(\frac{\partial f}{\partial y}(x, y)\).

From equation (4.9) and equation (4.10), we know that:

\(G_x = \frac{\partial f}{\partial x}(x, y) = f(x + 1, y) - f(x, y)\)

The preceding equation is implemented by using the following mask:

![](bbox=[0.47, 0.59, 0.53, 0.67])

Figure 4.33: 1-dimensional mask for \(G_x\) (Gradient vector in “x” direction)

And

\(G_y = \frac{\partial f}{\partial y}(x, y) = f(x, y + 1) - f(x, y)\)

Which can be implemented by the following mask:

![](bbox=[0.45, 0.83, 0.55, 0.88])

Figure 4.34: 1-dimensional mask for