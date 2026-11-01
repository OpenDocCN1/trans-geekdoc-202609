
[Figure 19.14](#Chapter19-06.xhtml#fig19-14) gives an intuitive explanation of why L1 regularization leads to weights of zero, while L2 regularization does not. Note that minimizing `Loss(w) + λComplexity(w)` is equivalent to minimizing `Loss(w)` subject to the constraint that `Complexity(w) ≤ c`, for some constant `c` that is related to `λ`. Now, in [Figure 19.14(a)](#Chapter19-06.xhtml#fig19-14) the diamond-shaped box represents the set of points `w` in two-dimensional weight space that have L1 complexity less than `c`; our solution will have to be somewhere inside this box. The concentric ovals represent contours of the loss function, with the minimum loss at the center. We want to find the point in the box that is closest to the minimum; you can see from the diagram that, for an arbitrary position of the minimum and its contours, it will be common for the corner of the box to find its way closest to the minimum, just because the corners are pointy. And of course the corners are the points that have a value of zero in some dimension.

Description

In both graphs, the horizontal axis is labeled `w subscript 1` and the vertical axis is labeled `w subscript 2`. There are three concentric ovals with the center in the first quadrant. The middle and outer ovals cross the vertical axis into the second quadrant. The ovals are oriented toward the upper left. Left Figure: A square has its center at the origin, two vertices on the vertical axis, and two vertices on the horizontal axis. The vertex on the positive vertical axis is labeled `w asterisk`. The outermost oval passes through point `w asterisk` on the vertical axis. Right Figure: A circle has its center at the origin. The outermost oval is tangent to the circle at a point labeled `w asterisk` on the circle in the first quadrant.

×![](images/Fig-276.jpg)

Figure 19.14 Why L1 regularization tends to produce a sparse model. Left: With L1 regularization (box), the minimal achievable loss (concentric contours) often occurs on an axis, meaning a weight of zero. Right: With L2 regularization (circle), the minimal loss is likely to occur anywhere on the circle, giving no preference to zero weights.

In [Figure 19.14(b)](#Chapter19-06.xhtml#fig19-14), we’ve done the same for the L2 complexity measure, which represents a circle rather than a diamond. Here you can see that, in general, there is no reason for the intersection to appear on one of the axes; thus L2 regularization does not tend to produce zero weights. The result is that the number of examples required to find a good `h` is linear in the number of irrelevant features for L2 regularization, but only logarithmic with L1 regularization. Empirical evidence on many problems supports this analysis.

Another way to look at it is that L1 regularization takes the dimensional axes seriously, while L2 treats them as arbitrary. The L2 function is spherical, which makes it rotationally invariant: Imagine a set of points in a plane, measured by their `x` and `y` coordinates. Now imagine rotating the axes by 45o. You’d get a different set of (`x'`,`y'`) values representing the same points. If you apply L2 regularization before and after rotating, you get exactly the same point as the answer (although the point would be described with the new (`x'`, `y'`) coordinates). That is appropriate when the choice of axes really is arbitrary—when it doesn’t matter whether your two dimensions are distances north and east; or distances northeast and southeast. With L1 regularization you’d get a different answer, because the L2 function is not rotationally invariant. That is appropriate when the axes are not interchangeable; it doesn’t make sense to rotate “number of bathrooms” 45o towards “lot size.”

## 19.6.4 Linear classifiers with a hard threshold

Linear functions can be used to do classification as well as regression. For example, [Figure 19.15(a)](#Chapter19-06.xhtml#fig19-15) shows data points of two classes: earthquakes (which are of interest to seismologists) and underground explosions (which are of interest to arms control experts). Each point is defined by two input values, `x1` and `x2`, that refer to body and surface wave magnitudes computed from the seismic signal. Given these training data, the task of classification is to learn a hypothesis `h` that will take new (`x1`, `x2`) points and return either 0 for earthquakes or 1 for explosions.

Description

In both graphs, the horizontal axis is labeled `x subscript 1` and ranges from 4.5 to 7 in increments of 0.5 units. The vertical axis is labeled `x subscript 2` and ranges from 2.5 to 7.5 in increments of 0.5 units. The linear fit line starts at approximately (4.5, 2.6), rises toward the upper right, and exits the viewing window at (7, 7). Part (“a”): The data points are scattered around the line. All open orange circle data points are above the line and all green circle data points are below the line. Figure (b): The data points are scattered around the line. All open orange circle data points except two, and one green circle are above the line. One of the open orange circle points above the line touches the line. All green circle data points except one, and two red open circles are below the line. One of the green circle points below the line touches the line.

×![](images/Fig-277.jpg)

Figure 19.15(a) Plot of two seismic data parameters, body wave magnitude `x1` and surface wave magnitude `x2`, for earthquakes (open orange circles) and nuclear explosions (green circles) occurring between 1982 and 1990 in Asia and the Middle East (Kebeasy et al., 1998). Also shown is a decision boundary between the classes. (b) The same domain with more data points. The earthquakes and explosions are no longer linearly separable.

A decision boundary is a line (or a surface, in higher dimensions) that separates the two classes. In [Figure 19.15(a)](#Chapter19-06.xhtml#fig19-15), the decision boundary is a straight line. A linear decision boundary is called a linear separator and data that admit such a separator are called linearly separable. The linear separator in this case is defined by

<p class="sidebar">Decision boundary</p> <p class="sidebar">Linear separator</p> <p class="sidebar">Linear separability</p>

$\\begin{matrix} {x\_{2}\\text{~=~1}\\text{.7}x\_{\\text{1}} - \\text{4}\\text{.9}} & \\text{or} & {- 4.9 + 1.7x\_{1} - x\_{2}\\ = \\ 0.} \\\\ \\end{matrix}$

The explosions, which we want to classify with value 1, are below and to the right of this line; they are points for which `–4.9 + 1.7x1 – x2 > 0`, while earthquakes have `–4.9 + 1.7x1 –x2 < 0`. We can make the equation easier to deal with by changing it into the vector dot product form—with `x0 = 1` we have

```
− 4.9*x[0] + 1.7*x[1] − x[2] = 0,
```

and we can define the vector of weights,

`w` = ⟨−4.9,1.7,−1⟩.

and write the classification hypothesis

`h[w](x)` = 1 if `w ⋅ x` ≥ 0 and 0 otherwise.

Alternatively, we can think of `h` as the result of passing the linear function `w · x` through a threshold function:

<p class="sidebar">Threshold function</p>

`h[w](x)` = `Threshold(w ⋅ x)` where `Threshold(z)` = 1 if `z` ≥ 0 and 0 otherwise.

The threshold function is shown in [Figure 19.17(a)](#Chapter19-06.xhtml#fig19-17).

Description
