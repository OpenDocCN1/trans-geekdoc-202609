```
poly = np.poly1d(coeffs)
ax.plot(xs, poly(xs))
ax.set_title(title)
```

![](bbox=[0.14, 0.22, 0.88, 0.57])

Massaging the general forms of these equations towards our earlier linear equation y1 = c1 x + c0 gets us to things like y2 = c2 x^2 + c1 x + c0. One quick note: x = x^1 and 1 = x^0. While I can insert suitable mathese here, trust me that there are very good reasons to define 0^0 = 1. Taken together, we have

y2 = c2 x^2 + c1 x^1 + c0 x^0 = sum_{i=0}^{2} c_i x^i

You know what I'm about to say. Go ahead, play along and say it with me. You can do it. It's a dot product! We can turn that equation into code by breaking up the x_i and the coefficients c_i and then combining them with a np.dot.

In [34]:

```
plt.Figure((2, 1.5))

xs = np.linspace(-10, 10, 101)
coeffs = np.array([2, 3, 4])
ys = np.dot(coeffs, [xs**2, xs**1, xs**0])

# nice parabola via a dot product
plt.plot(xs, ys);
```