# 2 Color Images

# 2.1 RGB Images

The RGB color model is based on the combination of the primary colors red (R), green (G), and blue (B) [1]. The origin of this model is in television technology and can be considered the fundamental representation of color in computers, digital cameras, and scanners, as well as in image storage [2]. Most image processing and rendering programs use this model for internal color representation.

The RGB model is an additive color format, which means that the combination of colors is based on the addition of the individual components with black as the base. This process can be understood as the overlapping of three light rays of red, green, and blue colors that are directed toward a white sheet of paper and whose intensity can be continuously controlled [3]. The intensity of the different color components determines both the resulting color hue and illumination. White and gray or levels of gray are produced in the same way through the combination of the three corresponding RGB primary colors.

The RGB model forms a cube whose coordinate axes correspond to the three primary colors R, G, and B. RGB values are positive, and their values are restricted to the interval [0, Vmax] where normally [0, Vmax] = 255. Each possible Ci color corresponds to a point inside the RGB cube, with the components:

```
Ci = (Ri, Gi, Bi) (2.1)
```

where 0 ≤ R, G, B ≤ Vmax. Normally, the range of values of the color components is normalized in the interval [0,1] in such a way that the color space would be represented by the unit cube shown in Figure 2.1. Point N = (0, 0, 0) corresponds to black, W = (1, 1, 1) corresponds to white, and all points on the line between S and W are the grayscale hues where the R, G, and B components have the same value.

Figure 2.2 shows a color image, which will be used as a test image several times in the chapter. In the same way, the respective RGB components of the image are also shown in Figure 2.2.