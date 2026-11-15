| Algorithm | Advantages | Gaps | References |
|---|---|---|---|
| SURF | The main advantage of SURF lies in its speed. SURF uses Hessian matrix, integral images, and DoG to resolve the images and speed up the calculations.
It has a small descriptor vector 64-D as compared to SIFT that had 128-D vector, makes it easier to. | The SURF algorithm
is not stable to
rotation changes,
and it does not
work properly
with illumination. | [17, 19] |

The 9x9 box filters approximate Gaussian second-order derivatives with
= 1.2. These approximations are represented by Dxx, Dyy, and Dxy. Now,
we can approximate the determinant of the Hessian by the following:

```
det(H_approx) = D_xx D_yy - (w D_xy)^2    (2.8)
```

By using the above equation, a SURF key point is determined [17, 18].

# 2.3 Neural Network–Based Algorithms

Deep learning is a powerful artificial intelligence technique that uses multi-
ple informational layers to produce the best results across a variety of
classes. Deep learning has demonstrated excellent performance in several
fields, particularly in the clustering, dividing, and recognition of images
[7]. A very powerful form of a neural network is a convolutional neural
network that is used for image recognition, classification and much more.
We shall discuss the basic structure of a convolutional neural network, dif-
ferent architectures, generational improvements and why they are superior
to traditional methods.