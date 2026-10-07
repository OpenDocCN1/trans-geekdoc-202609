# 2D Space

![](bbox=[0.135, 0.038, 0.865, 0.305])

So basically by **finding the right sigma** you can set up the D values to all of the points that you **don't want** in your classification and values **above zero** to the point that you **do want** in your classification. And that will allow you to **separate the two classes**. Allow you to classify each from one. In essence it is a kernel trick

+   - Hence, we have created a **decision boundary** actually going into a higher dimensional space without having to project back to 2D space.

+   - Here higher dimensional space is used but we're still doing the computations in the low dimensional space.

+   - Yes we have this visual representation that involves a higher dimensional space but at the same time if you look at the part we were just calculating this formula in 2D.

# 3.4.5 The Kernel Trick with Multiple landmark

Say all of a sudden you can't adjust your decision boundary and it's non-linear and moreover you find yourself being able to solve harder much more complex problems like this for example:

```
$$K(\vec{x},\vec{l}^1) + K(\vec{x},\vec{l}^2)$$\n(Simplified Formula)$
```

![](bbox=[0.135, 0.545, 0.715, 0.765])

So here is a very simplified formula:

```
$$K(\vec{x},\vec{l}^1) + K(\vec{x},\vec{l}^2)$$
```

+   - If you take **two kernel function** and just **add them up** (in reality you need some coefficients). The points **far from one landmark** and **near** to **another landmark** then it has non-zero value. The points which are far from **both landmark** is a 0 value. That's it.

+   - And the formula would be the point is assigned to the **green class**, when this **equation is greater than zero** and the point is assigned to **read class** when this **equation is equal to zero.**