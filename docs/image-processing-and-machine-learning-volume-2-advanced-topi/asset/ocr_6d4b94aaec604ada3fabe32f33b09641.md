![](bbox=[0.13, 0.12, 0.79, 0.47])

FIGURE 3.10
Different nonlinear transformations. (a) and (b) Twirl transformation, (c) and (d) Ripple transformation, and (e) and (f) spherical distortion.

```
r = \sqrt{d_x^2 + d_y^2}
\beta = a \tan 2(d_y, d_x) + \alpha \cdot \left( \frac{r_{max}}{r_{max}} \right) \tag{3.38}
```

Figure 3.10a and d show two examples of the Twirl transformation, considering the center of the image as the point of rotation \(\mathbf{x}_c\), \(r_{max}\) as half the main diagonal of the image, and the angle of rotation \(\alpha = 28^\circ\).

# 3.1.6.2 The Twirl Transformation in MATLAB

This section presents how to implement the Twirl transformation in MATLAB. The implementation methodology uses the inverse formulation of the transformation; that is, it starts by finding the correspondence of the transformed values with those of the original. This is convenient since the transformation itself, according to Equations 3.36 and 3.37, is expressed in terms of the inverse formulation. The code for this implementation is shown in Program 3.3, considering as the point of rotation \(\mathbf{x}_c\) the center of the image, \(r_{max}\) as half the main diagonal of the image, and the angle of rotation \(\alpha = 28^\circ\).