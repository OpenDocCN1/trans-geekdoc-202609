![](bbox=[0.14, 0.12, 0.855, 0.48])

FIGURE 2.12 HSV planes are represented in grayscale. (a) RGB image, (b) H plane, (c) S plane, and (d) V plane.

markings, which are easier to specify in this model. Figure 2.12 shows the HSV components of an image, represented in grayscale.

# 2.3.6 Conversion from HSV to RGB

To conduct the conversion, it is first assumed that the values of the HSV planes present data within the interval [0,1]. For the calculation of the values of the RGB color planes starting from the information of an image defined in the HSV color model, an auxiliary variable is calculated, defining that:

```
A' = (6 \cdot H) \mod 6 \qquad (2.17)
```

This expression returns a value ranging from 0 to 6. With this value, other variables are determined as follows:

```
c_1 = A' \quad x = (1 - S) \cdot V
c_2 = (6 \cdot H) - c_1 \quad y = (1 - (S \cdot c_2)) \cdot V \qquad (2.18)
z = (1 - (S \cdot (1 - c_2))) \cdot V
```