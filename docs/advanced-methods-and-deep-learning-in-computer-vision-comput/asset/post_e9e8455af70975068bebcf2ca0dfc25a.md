

![](img/fe161b7f6e96e35e7e853eece52c6dce_50_0.png)

FIGURE 1.17 Stereo imaging using two lenses. The axes of the optical systems are parallel, i.e., there is no 'vergence' between the optical axes.

In this geometry, a general point appears in the two images as $(x_1, y_1)$ and $(x_2, y_2)$. In general, the two optical systems need not have parallel optical axes and will exhibit a nonzero 'vergence' angle. However, the zero-vergence case is often employed and for simplicity is the one considered here. Note that the two sets of coordinates corresponding to the general point $(X, Y, Z)$ in the scene will differ because the baseline $b$ between the optical axes causes relative displacement or 'disparity' of the points in the two images.

Next, with a suitable choice of $Z$-axis on the perpendicular bisector of the baseline $b$, we obtain two equations:

$$x_1 = (X + b/2)\, f / Z \tag{1.50}$$

$$x_2 = (X - b/2)\, f / Z \tag{1.51}$$

Calculating the disparity $D = x_1 - x_2$ immediately permits the depth $Z$ to be obtained:

$$Z = b f / (x_1 - x_2) \tag{1.52}$$

Whereas this seems to be an ideal way of proceeding with 3-D vision, there is a fundamental problem—that of confirming that both points in a stereo pair actually correspond to the same point in the original scene. Note also that to obtain high accuracy in the determination of depth, a large baseline $b$ is required: unfortunately, as $b$ is increased, the correspondence between the images decreases, so it becomes more difficult to find matching points: this is because the two images become increasingly different and difficult to match.

The standard way of dealing with the stereo correspondence problem mentioned above is the epipolar line approach illustrated in Fig. 1.18.

![](img/fe161b7f6e96e35e7e853eece52c6dce_51_0.png)

FIGURE 1.18 Geometry of epipolar lines. A point P₁ in one image plane may have arisen from any one of a line of points in the scene, and may appear in the alternate image plane at any point on the so-called epipolar line E₂.

To understand this technique, imagine that we have located a distinctive point in the first image and that we are marking all possible points in the object field which could have given rise to it. This will mark out a line of points at various depths in the scene and, when viewed in the second image plane, a locus of points can be constructed in that plane. This locus (in the alternate image) is the epipolar line corresponding to the original image point. If we now search along the epipolar line for a similarly distinctive point in the second image, the chance of finding the correct match is significantly enhanced. This method not only cuts down the amount of computation required to find corresponding points, but also significantly reduces the incidence of false alarms. In the simple geometry of Fig. 1.17, all epipolar lines are parallel to the x-axis, although this only applies for the case of zero vergence. Note that the correspondence problem is rendered considerably more difficult by the fact that there will be points in the scene that give rise to points in one image but not in the other: this may arise because of occlusion or gross distortion of one of the points. Thus, it is necessary to search for consistent sets of solutions in the form of continuous object surfaces in the scene.

The difficulties caused by the correspondence problem have led to a number of alternative approaches. One of the most prominent has been 'shape from shading'—mapping how the surface orientation varies by analyzing the apparent brightness of the surface. While much has been achieved by this approach, it involves assumptions about the reflectance and specularity of the surfaces and how these vary with the orientation of (a) the surface and (b) the source of illumination. It also requires the application of complex iterative algorithms—a topic that cannot be dealt with in detail here. Similarly, 'photometric stereo', which involves illuminating scenes in turn by separate light sources and analyzing the resulting images, is too complex to be considered in detail here.

Next, 'shape from texture' is an approach that also allows details of surface orientation to be analyzed by examining the relative areas of textural elements. However, this is a specialized method that is not very frequently applied. Another approach is that of 'structured lighting'—typically based on directing patterns of light stripes, or other arrangements of light spots or grids, onto the object field—which has been exceedingly widely used for inspection and assembly on factory lines, though it can hardly be said to be in wide use in other types of application such as surveillance. Again, this has to be regarded as a specialized rather than a general technique for gauging 3-D object shapes.

It should be remarked that all but the last of these approaches lead to the production of surface orientation maps rather than measurement of depth per se, so computation of depth and surface shape has to be deduced from the raw orientation measurements.

Overall, the methods described above employ various means for estimating depth at all places in a scene, and hence are able to map out 3-D surfaces in a fair amount of detail. However, they do not give any clue as to what these surfaces represent. In some situations it may be clear that certain planar surfaces are parts of the background, e.g., the floor and the walls of a room, but in general individual objects will not be inherently identifiable. Indeed, objects tend to merge with each other and with the background, so specific methods are needed to segment the 3-D 'space map' and finally recognize the objects, giving detailed information on their positions and orientations. Clearly, obtaining a depth map of a 3-D object is no closer to identifying it than a boundary map such as a centroidal profile is to recognizing a 2-D object: specific means must be devised to perform the identification. Unfortunately, this task is significantly more difficult in 3-D than it is in 2-D. For example, whereas a Hough transform can in principle be applied in both cases, in 3-D it is hugely more complicated and computation intensive than in 2-D, as the number of free parameters will normally have increased from 3 to 6 for a static shape with no unknown shape parameters—there being 3 degrees of freedom for translation and 3 for rotation. Note also that the computational complexity normally varies not with the number of degrees of freedom but with an exponent of this number.

One further point should be added: over the past few years, sensors have been devised that provide RGB-D (color and depth) outputs: these provide depth information from optical 'time-of-flight'. LIDAR is well known but expensive and works better at long range, whereas matrix-based time-of-flight cameras work better at short range and typically use laser-generated light pulses that are a few nanoseconds apart. These types of advance help to solve the stereo correspondence problem. However, they do not eliminate the problem of interpreting 3-D surfaces, for which the large number of degrees of freedom to be wrestled with by object identification algorithms remains problematic: on the contrary, they serve to highlight this as the most substantial remaining problem.

Given that computational complexity is the primary source of these problems, it is natural to examine each depth map for salient features and to interpret the scenes accordingly: once we have object descriptions based on relatively few salient features rather than bulk surface descriptions, there would appear to be hope of achieving rapid, reliable identifications. We look into this possibility further in the following section.

### 1.4.2 Pose ambiguities under perspective projection

In this section we define weak and full perspective and aim to understand the perspective n-point (PnP) problem—the problem of finding the pose of objects from n features under various forms of perspective.

