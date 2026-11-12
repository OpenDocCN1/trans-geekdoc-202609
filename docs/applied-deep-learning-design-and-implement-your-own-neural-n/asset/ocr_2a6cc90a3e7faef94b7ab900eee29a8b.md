# # Sharpening filters (high pass filters)

The sharpening filter is used to highlight the transitions in intensity. These filters are also known as derivative filters. Sharpening filters are based on first- and second- order derivatives. They are just opposite to the smoothing filters; that is, these filters remove blurring from the input images and highlight the intensity transitions in the edges.

The derivative of any function is defined with respect to differences. These differences can be defined in many ways. Various types of discontinuities that exist in an image are ramps, Edges, Isolated points, the steps, and constant intensities are shown in *figure 4.16*:

![](bbox=[0.183, 0.343, 0.833, 0.59])

*Figure 4.16:* Horizontal scan line section of an image

The first-order and second-order derivatives are used to figure out these discontinuities in an image as follows. For defining the first-order derivative, we have the following three conditions:

+   • The first-order derivative should be $0$ in flat segments or, say, areas having constant intensity.
+   • The first-order derivative should not be $0$ on the onset of change in intensity (step).
+   • The first-order derivative should not be $0$ along the ramps.

In one-dimension, the first-order derivative is defined as follows:

```
f'(x) = f(x + 1) - f(x)   (4.6)
```