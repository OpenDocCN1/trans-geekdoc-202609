curvature. There are several different types of splines. The most common splines used in GIS for spatial interpolation are thin-plate splines. Such a type of spline produces a surface that passes exactly through the sample points while ensuring the surface is as smooth as possible. The general form of a spline function can be written as:

```
f(x,y)=t(x,y)+\sum_{i=1}^n b_i r(d_i) \quad (5.17)
```

where \(\tau\) is the weight, \(c\) is a constant equal to 0.577215 and \(K_0\) is the modified Bessel function (Mitas and Mitasova 1988). Typical values of \(\tau\) are 0, 0.001, 0.01, 0.1 or 0.5. The higher the weight, the smoother the interpolated surface. The \(b_i\) coefficients in equation (5.17) and \(a_1\), \(a_2\) and \(a_3\) in equation (5.18) are found by a system of linear equations:

```
f(x_i, y_i) = z_i (i=1, 2, ..., n) \quad (5.20a)
\sum_{i=1}^n b_i = 0 \quad (5.20b)
\sum_{i=1}^n b_i x_i = 0 \quad (5.20c)
\sum_{i=1}^n b_i y_i = 0 \quad (5.20d)
```

where \(x\) and \(y\) are coordinates, \(t(x, y)\) is a trend function, \(n\) is the number of sample points, \(d_i\) is the distance from the \(i\)th sample point to the point \((x, y)\), \(r(d)\) is a basis function designed to obtain a minimum curvature surface and \(b_i\) are coefficients (Mitas and Mitasova 1999). For thin-plate splines, a basis function minimises the cumulative sum of the squares of the second derivative terms of the surface taken over each point on the surface (Mitas and Mitasova 1999). Different thin-plate splines take different forms of \(t(x, y)\) and \(r(d)\). There are two most commonly used forms of thin-plate splines: regularised spline and spline with tension.

where \(z_i\) is the value at the \(i\)th sample point, and \(n\) is the number of sample points.

A major problem with the regularised spline are the steep gradients in data-poor areas (where there are very few sample points), often known as overshoots. A weight \(\tau\) of higher than 0.5 tends to produce a higher number of overshoots in data-poor areas. These overshoots need to be corrected. Thin-plate splines with tension are designed to mitigate the problem.

# 5.5.4.1 Regularised Spline

# 5.5.4.2 Spline with Tension

For the regularised spline, the trend and basis functions take the following forms:

The spline with tension allows users to control the tension to be applied to the edges of the surface. The trend and basis functions of spline with tension have the following forms:

```
t(x,y) = a_1 + a_2 x + a_3 y \quad (5.18)
r(d) = \frac{1}{2\pi} \left\{ \frac{d^2}{4} \left[ \ln \frac{d}{2\pi} + c - 1 \right] + \tau^2 \left[ K_0 \left( \frac{d}{\tau} \right) + c \right] + \ln \frac{d}{2\pi} \right\} \quad (5.19)
```

```
t(x,y) = a \quad (5.21)
r(d) = - \frac{1}{2\pi \varphi^2} \left[ \ln \frac{d\varphi}{2} + c + K_0(d\varphi) \right] \quad (5.22)
```

where \(\varphi\) is the weight. The higher the weight, the coarser the interpolated surface,