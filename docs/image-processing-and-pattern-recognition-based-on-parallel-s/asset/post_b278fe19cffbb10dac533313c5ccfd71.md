
However, adoption of the final decision on the classification of the object in this case is easier to implement. The use of parallel shift technology allows regularisation of information. Any reduction of entropy leads to an increase in the productivity of the intellectual systems.

## 4.1 Determination of Spatial Orientation of Planes

Common image recognition algorithm based on the use of parallel shift technology has been previously described in the book. Besides pattern recognition, this algorithm with minor modifications can be used to determine the spatial orientation of the object. In this case, the object is considered as a flat image. In the three-dimensional object, its surface is composed of many areas, each belonging to a separate plane and as a flat image. If there is an opportunity to select these areas of the common image, it is possible to determine their spatial orientation (Belhumeur et al., 1997).

Let us assume that we have an image, the parameters of which are stored in memory of recognition device as A pattern. At an arbitrary location of the image in the space of this figure will be displayed as a B projection of the A pattern to receptor field plane (Fig. 4.1).

When determining the spatial orientation of the plane with the figure, the property of the projection area is used.

$$
S_B = S_A \cos \gamma \tag{4.1}
$$

where \(\gamma\) is the angle between the planes, which contain the A and B figures. These planes for sake of convenience will be called analogically A plane and B plane.

\(B\) plane is located perpendicularly from the intellectual system to the image. The peak of plane \(\gamma\) angle is a straight line that forms in the plane of the receptive field (\(B\) plane) and the \(\phi\) angle with the horizontal. When shifting copies of the figures A and B along this line, the corresponding values of FAI for this area are linked by the property of the projection area.

![](img/d6ed6c69a61b1252a9084096bb4904c6_66_0.png)

Fig. 4.1: The projection B for etalon A to arbitrary plane

It is not possible to immediately determine the \(\phi\) direction. It is, therefore, necessary to carry out a search for all shifts of the B figure copies in the direction from 0 to \(\pi\). Conducting a search for directions from \(\pi\) to 0 is not necessary due to the presence of central symmetry in the sets of the function of the area of intersection and integral coefficients. This procedure is similar to the rapid recognition process (a common recognition algorithm described earlier). It compares the integral factors of the real B image for directions \(x = \phi\) and \(y = \phi + \frac{\pi}{2}\). At this stage, it is used for integral coefficients, the constant property when changing the basic parameters of the functions of the area of intersection, i.e. when scaling

Thus, to determine the \(\phi\) direction, it is necessary to perform the following. For each of the possible directions of displacement in the range between 0 and \(\pi\) we get the function of the area of intersection and their integral coefficients of the real image. The Y class etalons are determined, which satisfy the following formulas:

$$
k_{x_A} = k_{x_B}
$$

$$
k_{y_A} = k_{y_B}
$$

For the class Y figures, it is necessary to determine which of the directions \(x = \phi\) or \(y = \phi + \frac{\pi}{2}\) is the direction of the line—the top of the plane \(\gamma\) angle or the direction of the projection.

To find the right projection direction, it is essential to compare the function of the area of intersection of real images and the function of area of intersection of Y class etalons for directions \(x = \phi\) and \(y = \phi + \frac{\pi}{2}\).

This is similar to the detailed stage of the recognition algorithm. The comparison area (4.1). Since the dimensions of the pattern figures and the real image may differ, the scaling of corresponding FAI is applied. Before comparing, scaling with preservation of function proportions is performed.

On this stage, the following four possible scenarios are possible: Option 1.

$$
\frac{FAI(x)_B}{FAI(x)_A} = \text{const} = \cos \gamma \tag{4.4}
$$

and

$$
\frac{FAI(y)_B}{FAI(y)_A} = \text{const} > 1 \tag{4.5}
$$

If the formulas (4.4) and (4.5) are true, then this pattern is selected correctly. Projection takes place relative to the direction of perspective \(x = \phi\); else we move on to the next etalon of \(Y\) class for which the true formulas are (4.2) and (4.3). Option 2.

$$
\frac{FAI(x)_B}{FAI(x)_A} = \text{const} > 1 \tag{4.6}
$$

and

$$
\frac{FAI(y)_B}{FAI(y)_A} = \text{const} = \cos \gamma \tag{4.7}
$$

If the formulas (4.6) and (4.7) are true, then this model is selected correctly. Projection takes place relative to the direction of perspective \(y = \phi + \frac{\pi}{2}\); otherwise, we move on to the next etalon \(Y\) class for which the true formulas are (4.2) and (4.3). Option 3.

$$
\frac{FAI(x)_B}{FAI(x)_A} = \text{const} = 1 \tag{4.8}
$$

and

$$
\frac{FAI(y)_B}{FAI(y)_A} = \text{const} = 1 \tag{4.9}
$$

If the formulas (4.8) and (4.9) are true, then this model is selected correctly. This option is fully consistent with the detailed step of the recognition algorithm. The real image \(B\) form corresponds to the standard \(A\) form; otherwise, we move on to the next etalon of \(Y\) class, for which the true formulas are (4.2) and (4.3). Option 4.

$$
\frac{FAI(x)_B}{FAI(x)_A} \neq \text{const} \tag{4.10}
$$

and

$$
\frac{FAI(y)_B}{FAI(y)_A} \neq \text{const} \tag{4.11}
$$

In this case, the pattern is not correctly selected; we go to the next pattern of \(Y\) class, for which the true formulas are (4.2) and (4.3). At all stages, comparison is being made with regard to the valid coefficients of comparison \(dk\) and \(dS\).

If no pattern is found which can have projection as real B figure, then it is advisable to perform a system learning process for inclusion in the array of patterns.

For simple shapes, it should be considered that each triangle is a projection of an equilateral triangle, each ellipse is a projection of the circle, and each parallelogram is a projection of a square. These properties can be used in the classification of ellipses and parallelograms.

With this method was calculated angles \(\phi\) and \(\gamma\) and we can accurately determine the spatial orientation of the 2D shape relative to the plane of the receptor field, if its parameters are available among the array of pattern. Determination of the spatial orientation of objects is necessary for the operation of automatic systems ‘eye-hand’ of autonomous robots and of assembly lines. No effective methods for selecting certain parts of the surface of 3D-objects have been developed. In this case some of these component parts that are irregularly allocated on the assembly line may be labelled, thus allowing capturing of components by devices of assembly line using the method for determining the spatial orientation of the planes on the basis of parallel shift technology.

## 4.2 Use of Different Types of Shifts of Image Copies in Video Processing Devices Based on PST

Before proceeding to the description of the methods for determining the parameters of the movement of objects on the basis of the use of the parallel shift technology, one important point should be emphasised. It was previously mentioned that it is possible for formation of the function of the area of intersection using both cyclic and non-cyclic shifts of image copies. For example, in a cyclic shift to right, the following actions take place. If a copy of the figure falls outside the right boundary of the receptor field, it appears to be at the same level as the left portion of the receptor field and continues its movement to the right (Fig. 4.2).

If not using a cyclic shift of the figure copy to the right, it goes beyond the right edge of the receptive field. Shift type is determined by the copy of the image matrix, which is built on the selected shift registers. In the section about the formation of the function of the area of intersection at the stage of pre-treatment, it was named as the B matrix. If it was built on the cyclic shift registers, the cyclic shift process is obtained. When using no cyclic shift registers, no cyclic shift occurs.

Different types of copy image shift may be applied in various devices. Methods of determining the object motion parameters through the use of a parallel shift technology will also differ. Organisation of the cyclic shift should be applied mainly in prosthesis of visual organs in biological beings. The biological information systems operate with uninterrupted stream of information, which is perceived by their receptors.
