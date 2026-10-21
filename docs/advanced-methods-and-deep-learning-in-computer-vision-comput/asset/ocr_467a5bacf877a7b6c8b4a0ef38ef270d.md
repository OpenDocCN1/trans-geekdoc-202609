are:

x = f X / Z    (1.65)
y = f Y / Z    (1.66)
z = f          (1.67)

To include perspective projection in the above formalism, we need to examine the homogeneous coordinates transformation:

[ 1 0 0 0 ] [ X ]   [ X ]
[ 0 1 0 0 ] [ Y ] = [ Y ]
[ 0 0 1 0 ] [ Z ]   [ Z ]
[ 0 0 1/f 0 ] [ 1 ]   [ Z/f ]    (1.68)

The key to understanding this transformation is to notice that dividing by the fourth coordinate gives the required values of the transformed Cartesian coordinates (f X / Z, f Y / Z, f).

Let us now review this result. First, we have found a 4 × 4 matrix transformation which operates on 4-D homogeneous coordinates. These do not correspond directly to real coordinates, but real 3-D coordinates can be calculated from them by dividing the first 3 by the fourth homogeneous coordinate. Thus, there is an arbitrariness in the homogeneous coordinates in that they can all be multiplied by the same constant factor without producing any change in the final interpretation.

The advantage to be gained from use of homogeneous coordinates is the convenience of having a single multiplicative matrix for any transformation, in spite of the fact that perspective transformations are intrinsically nonlinear: thus a quite complex nonlinear transformation can be reduced to a more straightforward linear transformation. This eases computer calculation of object coordinate transformations, and other computations such as those for camera calibration (see below). We may also note that almost every transformation can be inverted by inverting the corresponding homogeneous transformation matrix. The exception is the perspective transformation, for which the fixed value of z leads merely to Z being unknown, and X, Y only being known relative to the value of Z (hence the need for binocular vision or other means of discerning depth in a scene).

# 1.4.10 Camera calibration

The above discussion has shown how homogeneous coordinate systems are used to help provide a convenient linear 4 × 4 matrix representation for 3-D transformations including rigid body translations and rotations, and nonrigid operations including scaling, skewing and perspective projection. In this last case, it was implicitly assumed that the camera and world coordinate systems are identical, since the image coordinates were expressed in the same frame of reference. However, in general the objects viewed by the camera will have positions which may be known in world coordinates, but which will not a priori be known in camera coordinates, since the camera will in general be mounted in a somewhat arbitrary position and will point in a somewhat arbitrary direction. Thus, the camera system will have to be calibrated before the images can be used for practical applications such as robot