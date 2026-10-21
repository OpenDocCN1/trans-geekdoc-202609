pick-and-place. A useful approach is to assume a general transformation between the world coordinates and the image seen by the camera under perspective projection, and to locate in the image various calibration points which have been placed in known positions in the scene. If enough such points are available, it should be possible to compute the transformation parameters, and then all image points can be interpreted accurately until recalibration becomes necessary.

In what follows, we will find that there are two types of camera calibration: the first is that of extrinsic calibration, in which the position and pose of the camera are determined relative to the world coordinates, via its external parameters; the second is that of intrinsic calibration, in which the image (and pixel) locations are determined in relation to the camera’s internal parameters. Important factors to be discussed are the numbers of extrinsic and intrinsic parameters and their geometric significance.

To proceed, we need to set up the mathematical formulation in a general way, using the general homogeneous transformation G, which takes the form:

\begin{bmatrix} X_H \\ Y_H \\ Z_H \\ H \end{bmatrix} = \begin{bmatrix} G_{11} & G_{12} & G_{13} & G_{14} \\ G_{21} & G_{22} & G_{23} & G_{24} \\ G_{31} & G_{32} & G_{33} & G_{34} \\ G_{41} & G_{42} & G_{43} & G_{44} \end{bmatrix} \begin{bmatrix} X \\ Y \\ Z \\ 1 \end{bmatrix} \tag{1.69}

Note that the final Cartesian coordinates appearing in the image are (x, y, z) = (x, y, f), and these are calculated from the first 3 homogeneous coordinates by dividing by the fourth:

x = X_H/H = (G_{11} X + G_{12} Y + G_{13} Z + G_{14})/(G_{41} X + G_{42} Y + G_{43} Z + G_{44}) \tag{1.70}
y = Y_H/H = (G_{21} X + G_{22} Y + G_{23} Z + G_{24})/(G_{41} X + G_{42} Y + G_{43} Z + G_{44}) \tag{1.71}
z = Z_H/H = (G_{31} X + G_{32} Y + G_{33} Z + G_{34})/(G_{41} X + G_{42} Y + G_{43} Z + G_{44}) \tag{1.72}

However, as we know z, there is no point in determining parameters G_{31}, G_{32}, G_{33}, G_{34}. Accordingly, we proceed to develop the means for finding the other parameters. In fact, because only the ratios of the homogeneous coordinates are meaningful, only the ratios of the G_{ij} values need be computed, and it is usual to take G_{44} as unity: this leaves only 11 parameters to be determined. Multiplying out the first two equations and rearranging gives:

G_{11} X + G_{12} Y + G_{13} Z + G_{14} - x(G_{41} X + G_{42} Y + G_{43} Z) = x \tag{1.73}
G_{21} X + G_{22} Y + G_{23} Z + G_{24} - y(G_{41} X + G_{42} Y + G_{43} Z) = y \tag{1.74}

Noting that a single world point (X, Y, Z) which is known to correspond to image point (x, y) gives us two equations of the above form: it requires a minimum of 6 such points to provide values for all 11 G_{ij} parameters. An important factor is that the world points used for the calculation should lead to independent equations: thus it is important that they should not be coplanar. More precisely, there must be at least 6 points, no 4 of which are coplanar. However, further points are useful in that they lead to overdetermination of the parameters and increase the accuracy with which the latter can be computed. There is no reason why the additional points should not be coplanar with existing points: indeed, a common arrangement is to set up a cube so that 3 of its faces are visible, each face having a pattern of squares with 30–40 easily discerned corner features.