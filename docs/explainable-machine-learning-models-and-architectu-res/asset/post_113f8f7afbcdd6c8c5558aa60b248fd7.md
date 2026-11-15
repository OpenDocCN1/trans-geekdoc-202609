
## 2.2 Traditional Image Recognition Algorithms

Traditional image recognition algorithms consist of a detector and descriptor vector. Before assigning an invariant descriptor or feature to each region, they first identify places of interest in the compared pictures and choose a region surrounding each one. Thus, by matching the descriptors, correspondences can be found. It is best if detectors and descriptors are as invariant as feasible [3].

### 2.2.1 Harris Corner Detector (1988)

It is a mathematical approach to extracting corners in an image and deducing features in an image. This was first introduced in 1988 and since then it has been used in many algorithms. Determining corners is done by calculating the change in intensity of an image. It is calculated using the eq below which is derived using the Taylor function for the 2D equation.

```
E(u,v) = \sum_{x,y} w(x,y) \left[ I(x+u, y+v) - I(x,y) \right]^2 \qquad (2.1)
```

Where the term I(x+u, y+v) represents the shifted/new intensity and the shift is u and v and I(x,y) represents the original intensity. The above equation can be rewritten in the matrix form as follows,

```
E(u,v) \approx \begin{bmatrix} u & v \end{bmatrix} M \begin{bmatrix} u \\ v \end{bmatrix} \qquad (2.2)
```

Where the M in the above equation is

```
M = \sum_{x,y} w(x,y) \begin{bmatrix} I_x I_x & I_x I_y \\ I_x I_y & I_y I_y \end{bmatrix} \qquad (2.3)
```

We then next calculate the trace and determinant of matrix M to find R, where R is:

$R = det(M) - k(trace(M))^2$ (2.4)

where,

- det(M)=λ1λ2
- trace(M)=λ1+λ2
- λ1 and λ2 are the eigenvalues of M

So, the magnitudes of these eigenvalues decide whether a region is a corner, an edge, or flat.

- When |R| is small, which happens when λ1 and λ2 are small, the region is flat.
- When R<0, which happens when λ1>>λ2 or vice versa, the region is edge.
- When R is large, which happens when λ1 and λ2 are large and λ1~λ2, the region is a corner.

A simple mathematical method for identifying which windows exhibit significant differences when moved in any direction is the Harris Corner Detector. Each window has a score R connected to it. We determine which ones are corners and which ones are not based on this score [5]. The Harris Corner Detector is found to be invariant to translation, rotation, and illumination changes [11], but not scale invariant, as we see some algorithms

![](img/d2107fc60629942e7da5355e47fcc33d_31_0.png)

Figure 2.1 Visualizing corner detection.

that adopted and improved on Harris corner detector (the most famous one being SIFT) [12]. Figure 2.1 above, shows the region variance from flat region to edge and then to a corner region.

### 2.2.2 SIFT (2004)

In SIFT algorithm (Scale-invariant feature transform) image processing and recognition we try to reduce the image to a set of locally distinct points together with the information of said points. We then look for those points in other images and if the data matches, we can say that the image is similar, even if it is from a different viewpoint [4]. The initial goal of the SIFT method is to compare two images (or two image parts) that can be deduced from each other (or from a common image) by a rotation, a translation, and a scale change. The method turns out to be robust also to rather large changes in viewpoint angle, which explains its success [13].

We take a patch around the key point into account and use intensity values or the changes in intensity values, i.e., the image gradient in this area is used to describe it and turn it into a Descriptor Vector.

Now if we have multiple images where we detect the same key points, we can conclude that these are the same images; here, being the same does not necessarily mean being the same as they can be from different angles and with different lighting conditions.

The two images need not be the same, but they are of the same location from varying angles, and by matching the key points in the images we can conclude that they are of the same place [4, 14].

### Computation of the SIFT Key Points

The locally distinct points or key points are found using the Difference of Gaussians Approach, which means the taken image is blurred using Gaussian Blur at different magnitudes. Then all the images are subtracted from each other and then we stack the difference images on top of each other. Then we look for extreme points, so points where the neighbours in the X-Y image space are as well as in the space of different levels of smoothing which are locally distinct and which stand out; they are the key points. This is done not only for one image resolution; it is also performed on an image pyramid which means images which are differently scaled in size to find key points that also are distinct concerning scale changes, i.e., if you're closer to an object you'll find the same key point if you're further away [3].

### Computation of SIFT Descriptor Vector

This is computed by looking into the local neighbourhood of the key point that we found. We then break the neighbourhood into small areas and find the Gradients in these small areas. We use Gradients as these are rather strong to elimination changes and some viewpoint changes. The next step is to collect gradients in the local regions into histograms, like how often certain Gradients occur, what their magnitude is, etc. Then at the end around the key point, say, in a 4x4 region we have 16 local zones, so we make 16 histograms [13].

### Affine Transformations

Depending on variations to the camera and its settings, the illumination, and the object itself, images of even an identical object might differ significantly. For monitoring, searching, and comprehending photos, one option to handle some of these changes is to utilize a description of the object that is unaware of some of the modifications stated above. Commonly employed for this purpose are affine invariants [15].

### Affine Invariance

This means that surfaces are considered the same under affine transformations, i.e., linear transformations x → Ax + b, including squeezing and shearing [15].

### 2.2.3 ASIFT

ASIFT or Affine Scale-invariant Feature Transform is based on SIFT but unlike SIFT, ASIFT can accommodate all the six properties and is capable of simulating with enough accuracy even the distortion caused by the camera’s optical axis direction. The ASIFT approach replicates all picture views that may be obtained by altering the two camera axis orientation parameters, namely the latitude and longitude angles. The SIFT approach is then used to cover the remaining four parameters [13].

### Advantages of ASIFT over SIFT

- When the number of matches produced by the SIFT algorithm is significant, ASIFT has better accuracy than SIFT [4, 13].
- For the various image types being tested, ASIFT performs better. When visually inspected, the performance is evident in terms of both the number of matches and accuracy [4, 16].
- Even though the computational complexity of ASIFT is more than the SIFT considering the kind of processing power we have today, ASIFT presents a better face for image matching and image registration applications [4].
- ASIFT covers all six affine invariants, unlike SIFT [4, 13].

### 2.2.4 SURF (2006)

A quick and reliable approach for local, similarity-invariant representation and comparison of pictures is the SURF method (Speeded Up Robust Features). The SURF approach's key appeal is its ability to compute operators quickly using box filters, enabling real-time applications like tracking and object detection [17].

### Motivations behind SURF:

- Faster detection of key points
- Less complicated
- Scale and rotation invariant and invariant to photometric changes
- Reduced descriptor dimensions as the feature size directly affects the cost of computation, so we try to maintain a low-size descriptor.

### SURF Key Points

The extraction of SURF key points is based on three main methods that reduce the complexity of an image, which makes the SURF algorithm faster than SIFT [17].

- Integral Images
- Hessian Matrix
- Difference of Gaussian
