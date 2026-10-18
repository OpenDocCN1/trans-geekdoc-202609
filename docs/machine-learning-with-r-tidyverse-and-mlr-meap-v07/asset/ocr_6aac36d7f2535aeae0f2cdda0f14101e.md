![](bbox=[0.131, 0.074, 0.671, 0.319])

**Figure 5.4** Constructing a new axis that only maximizes class centroid separation doesn’t fully resolve the classes (left example). Constructing a new axis that maximizes centroid separation while also minimizing variance within each class results in better separation of the classes (right). x̄ and s² are the mean and variance of each class along the new axis, respectively.

This new axis is called a discriminant function, and is a linear combination of the original variables. For example, a discriminant function could be described by the equation:

$$DF = -0.5 \times var_1 + 1.2 \times var_2 + 0.85 \times var_3$$

In this way, the discriminant function (DF) in the equation above is a linear combination of variables var₁, var₂ and var₃. The combination is linear because we are simply adding the contributions from each variable together. The values that each variable is multiplied by are called the *canonical discriminant function coefficients* and weight each variable by how much it contributes to class separation. In other words, variables which contribute most to class separation will have larger absolute canonical discriminant function coefficients (positive or negative). Variables that contain little or no class separation information will have canonical discriminant function coefficients closer to zero.