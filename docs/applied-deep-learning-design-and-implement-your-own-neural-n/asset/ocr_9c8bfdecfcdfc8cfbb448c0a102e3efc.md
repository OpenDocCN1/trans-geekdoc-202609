```
$$ grad f(x, y) = \nabla f(x, y) = \left[ \frac{\partial f}{\partial x}(x, y), \frac{\partial f}{\partial y}(x, y) \right] = [G_x, G_y] \quad (4.23) $$
```

This vector points in the direction of the largest rate of change of f(x, y). The magnitude of the image gradient is given as follows:

```
$$ Mag\left( \nabla f(x, y) \right) = \sqrt{G_x^2 + G_y^2} \quad (4.24) $$
```

Also, the direction of the image gradient is given as follows:

```
$$ \beta\left( \nabla f(x, y) \right) = tan^{-1} \left( \frac{G_y}{G_x} \right) \quad (4.25) $$
```

Let us take an example where there is a change in the intensity levels in only a horizontal direction, as shown in figure 4.26:

![](bbox=[0.33, 0.36, 0.66, 0.43])

**Figure 4.26:** Change of pixel intensity values in the horizontal direction

For the only change in the x-direction, the image gradient is given as follows:

```
$$ \nabla f(x, y) = \left[ \frac{\partial f}{\partial x}(x, y), 0 \right] $$
```

Similarly, the change in the intensity levels in only the vertical direction is shown in figure 4.27:

![](bbox=[0.44, 0.625, 0.52, 0.89])

**Figure 4.27:** Change of pixel intensity values in the vertical direction