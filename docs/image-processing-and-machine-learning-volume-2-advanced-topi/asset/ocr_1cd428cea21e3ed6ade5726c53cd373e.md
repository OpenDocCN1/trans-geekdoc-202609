To rotate an image, use the imrotate function. The general syntax of this function is:

```
B = imrotate(A,angle,method)
```

This function performs a rotation of image A, considering its center as the axis of rotation. The angle by which the image is rotated is defined in the Angle variable, while the interpolation method used is described by the method variable and corresponds to one of those defined in Table 3.1. MATLAB allows the implementation of spatial transformations such as the affine or projective transformation, the effects of which are in any case more interesting and elaborate than imresize or imrotate. Considering the above, the way to carry out this type of transformation in MATLAB is a little more complicated, for which the following procedure is developed:

+   1. The parameters of the geometric transformation are defined, which could consist of a series of parameters that define the mapping performed by the operator T(x,y).
+   2. A transformation structure is created, called TFORM, which can be considered as the coupling in matrix form of the parameters defined in step 2.
+   3. The spatial operation is performed by using the imtransform function.

As a first step, the transformation to be performed must be defined. In many types of geometric transformations, the parameters can be characterized by a transformation matrix MT of size 3 × 3. Table 3.2 shows the relationship between some simple transformations and the transformation matrix that models them.

For the creation of the TFORM structure that absorbs the important characteristics of the transformation, the maketform function is used. The general syntax of this function is:

```
TForm = maketform(type, MT)
```

This function creates the TFORM structure from the definition of the MT transformation matrix and the type of geometric operation to be performed. The type of geometric operation can be either ‘affine’ or ‘projective’. The ‘affine’ transformation includes rotation, translation, scaling, and distortion. In this type of geometric operation, as seen in this chapter, the lines remain as lines, with the special property that parallel lines remain as such. Considering this property, the rectangles become parallelograms.

In the ‘projective’ transformation, the lines are also preserved as lines, with the difference that if they are parallel, they do not remain as such in the resulting image. This transform takes its name precisely from the fact that