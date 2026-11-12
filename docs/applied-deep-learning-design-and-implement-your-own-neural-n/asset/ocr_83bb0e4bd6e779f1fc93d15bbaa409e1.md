# # Multi-class cross-entropy loss

The multi-class cross-entropy loss function is a simplification of the binary cross-entropy loss function. The loss for input vector X and the corresponding one-hot encoded target vector t is defined as follows:

\( L(X_i, t_i) = - \sum_{j=1}^n t_{ij} * \log(p_{ij}) \)

where \( Y_i \) in the preceding equation is a one-hot encoded vector (\( Y_{i1'}, Y_{i2'}...... Y_{in} \)),

\( t_{ij} = \left\{ \begin{array}{ll} 1, & \text{if the element } i^{th} \text{is in class } j \\ x, & \text{otherwise} \end{array} \right. \)

\( P_{ij} \) is the probability that the i\(^{th}\) element is in class j.

# # KL divergence

KL divergence, also known as _Kullback-Liebler Divergence_, is a measure of the difference between the probability distribution to the other distribution.

For probability distributions R and S, KL divergence of R from S is given by the following:

\( D_{KL}\left(\frac{R}{S}\right) = \left\{ \begin{array}{ll} - \sum_x R(x). log \frac{S(x)}{R(x)} = \sum_x R(x). log \frac{R(x)}{S(x)}, & \text{for discrete distributions} \\ - \int R(x). log \frac{S(x)}{R(x)} . dx = \int R(x). log \frac{R(x)}{S(x)} . dx = , & \text{for coninuous distributions} \end{array} \right. \)

**Example 6:** Let P and Q be the distributions shown in the following figure and table. Then, KL Divergence is computed as follows: