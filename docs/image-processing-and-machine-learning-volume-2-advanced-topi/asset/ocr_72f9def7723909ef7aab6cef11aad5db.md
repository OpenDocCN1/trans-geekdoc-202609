For better coverage of the color space of the CMY model, in practice, it is usually complemented by incorporating the color black (K) as part of the scheme, where the value of K is defined as follows:

```
K(x, y) = min(C(x, y), M(x, y), Y(x, y))
```

Using black as part of the color model allows you to reduce the values of the CMY planes by increasing the amount of the plane defined by the black value. In consideration of this incorporation, there are some variants of the model due to the way in which the black color plane contributes to the processing.

# 2.5.1 Transformation from CMY to CMYK (Version 1)

```
\begin{bmatrix} C'(x, y) \\ M'(x, y) \\ Y'(x, y) \\ K'(x, y) \end{bmatrix} = \begin{bmatrix} C(x, y) - K(x, y) \\ M(x, y) - K(x, y) \\ Y(x, y) - K(x, y) \\ K(x, y) \end{bmatrix}
```

# 2.5.2 Transformation from CMY to CMYK (Version 2)

```
\begin{bmatrix} C'(x, y) \\ M'(x, y) \\ Y'(x, y) \end{bmatrix} = \begin{bmatrix} C(x, y) - K(x, y) \\ M(x, y) - K(x, y) \\ Y(x, y) - K(x, y) \end{bmatrix} \cdot \begin{cases} \frac{1}{1-K} & \text{if } K < 1 \\ 1 & \text{if not} \end{cases}
```

Since the values of all the planes that define this color model (CMYK) strongly depend on the printing process and the type of paper used, in practice, each plane is individually calibrated.

# 2.5.3 Transformation from CMY to CMYK (Version 3)

```
\begin{bmatrix} C'(x, y) \\ M'(x, y) \\ Y'(x, y) \\ K'(x, y) \end{bmatrix} = \begin{bmatrix} C(x, y) - f_1(K(x, y)) \\ M(x, y) - f_1(K(x, y)) \\ Y(x, y) - f_1(K(x, y)) \\ f_2(K(x, y)) \end{bmatrix}
```