registration, iii) visualization and iv) simulation. Segmentation is the method of creating specific models from images of patient's anatomy. Registration aligns each other with multiple data sets. Visualization helps to simulate and evaluate the strategies and planned treatments. There are many imaging techniques that are complementary and offering different insights.

# Image Quality Analysis

In mathematical models the data extracted from images helps in achieving clinical, biomedical, experimental progress in scientific research. Arrays of data samples arranged geometrically quantify the physical phenomenon of time variation in haemoglobin deoxygenating on neuronal metabolism, i.e. diffusion of water molecules inside tissues. The scope of organizing observations in biophysical world lead to increase in the emergence of new processing technology combining complex and sophisticated mathematical models to physiological dysfunction by Bloembergen, Purcell & Pound (1948) and Canet (1996). Shape analysis is detecting similarly shaped objects to automatically analyze and represent it in a digital form. The objects are modelled either by scanning or by extracting 2D or 3D images and simplified for a shape description. The simplified representations are easy to handle and reconstruct the original object. Segmentation in an image gives lots of data. Shape descriptors are required to evaluate to the same (vector or scalar) value for all sizes, positions, and/or orientations of any given shape. The various ways of analyzing a biomedical image by means of shape considered under study is given below:

# Spatial Domain Shape Metrics

This is the broadly used metric to the measures aspect ratio, compactness, regularity on describing the shape of a feature. The metric is considered as their boundary points. If K boundary points define distance then for kth point described in equation (1)

```
r_k(\phi) = \sqrt{(x_k - x_c)^2 + (y_k - y_c)^2}
```

Were the associated angle 9 is as follows (equation (2))

```
tan \phi = \frac{(y_k - y_c)}{(x_k - x_c)}
```

This representation converts the perimeter value r_k the sequence, where 0 < r < k. The aspect ratio, A is given in equation (3):

```
A = \frac{\max r_k}{\min r_k}
```

The cluster shown in part having a zero-valued background, black is the segmentation process and the lines highlighted in white are the perimeter. The dashed lines that are thick are the diagonal lines with features approximated. In diagram B the centroid is the intersection of the diagonal lines and the