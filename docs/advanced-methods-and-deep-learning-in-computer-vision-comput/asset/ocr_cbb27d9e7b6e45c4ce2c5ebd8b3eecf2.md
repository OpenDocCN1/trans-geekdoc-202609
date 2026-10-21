# # 1. The dramatically changing face of computer vision

At the same time we observe the correct matrix formulation of all the vectors by transposing appropriately. We now find that:

$(R^T P_2)^T C_x P_1 = 0$

:. $P_2^T R C_x P_1 = 0$

Finally, we obtain the ‘essential matrix’ formulation:

$P_2^T E P_1 = 0$

where the essential matrix has been found to be:

$E = R C_x$

Eq. (1.90) is actually the desired result: it expresses the relation between the observed positions of the same point in the two camera frames of reference. Furthermore, it immediately leads to formulae for the epipolar lines. To see this, first note that in the C1 camera frame:

$p_1 = (f_1/Z_1) P_1$

while in the C2 camera frame (and expressed in terms of that frame of reference):

$p'_2 = (f_2/Z_2) P'_2$

Eliminating P1 and P2', and dropping the prime (as within the respective image planes the numbers 1 and 2 are sufficient to specify the coordinates unambiguously), we find:

$p_2^T E p_1 = 0$

as Z1, Z2 and f1, f2 can be canceled from this matrix equation.

Now note that writing p2^T E = l1^T and l2 = E p1 leads to the following relations:

$p_1^T l_1 = 0$

$p_2^T l_2 = 0$

This means that l2 = E p1 and l1 = E^T p2 are the epipolar lines corresponding to p1 and p2 respectively.

# ## 1.4.15 The fundamental matrix

Notice that in the last part of the essential matrix calculation, we implicitly assumed that the cameras are correctly calibrated. Specifically, p1 and p2 are corrected (calibrated) image coordinates. However, there is a need to work with uncalibrated images, using the raw pixel measurements—for all the reasons given in Section 1.4.12. Applying the camera intrinsic