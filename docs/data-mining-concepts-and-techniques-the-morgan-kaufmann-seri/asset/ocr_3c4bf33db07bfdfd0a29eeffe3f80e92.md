+   - KL-divergence follows chain rule, that is, \( D_{KL}(p_{XY}||q_{XY}) = D_{KL}(p_X||q_X) + D_{KL}(p_{Y|X}||q_{Y|X}) \).
+   - KL-divergence is a convex function with respect to PMFs \( p_X \) and \( q_X \).

# A.4.3 Mutual information

In information theory, the *mutual information* of two random variables measures the amount of information we gain on one random variable with the prior knowledge on observing the other random variable. Given two random variables \( X \) and \( Y \), the mutual information \( I(X; Y) \) of random variables \( X \) and \( Y \) is summarized as follows:

\( I(X; Y) = \mathbb{E}_{(x,y) \sim p_{XY}} [\log \frac{p_{XY}(x, y)}{p_X(x) p_Y(y)} ] \
= \begin{cases} \sum_{(x,y)} p_{XY}(x, y) \log \frac{p_{XY}(x,y)}{p_X(x)p_Y(x)}, & \quad X, Y \text{ are discrete r.v.} \\ \int_{(x,y) \sim p_{XY}} p_{XY}(x, y) \log \frac{p_{XY}(x,y)}{p_X(x)p_Y(x)} dx dy, & \quad X, Y \text{ are continuous r.v.} \end{cases} \) (A.74)

where \( p_{XY} \) is the joint distribution of the joint random variable \( (X, Y) \), \( p_X \) is the marginal distribution of random variable \( X \), and \( p_Y \) is the marginal distribution of random variable \( Y \).

**Relationship between mutual information and KL-divergence.** In terms of KL-divergence, mutual information \( I(X; Y) \) of two random variables \( X \) and \( Y \) is equivalent to the KL-divergence between the joint distribution \( p_{XY} \) and the product of their marginal distributions \( p_X \otimes p_Y \). The relationship between mutual information and KL-divergence is summarized as follows:

\( I(X; Y) = D_{KL}(p_{XY} || p_X \otimes p_Y). \) (A.75)

**Relationship between mutual information and entropy.** In terms of entropy, mutual information of two random variables measures how much uncertainty we lose in one random variable by observing the other random variable. The relationship between mutual information and entropy is summarized as follows:

\( I(X; Y) = H(X) - H(X|Y) = H(Y) - H(Y|X) = H(X) + H(Y) - H(X, Y), \) (A.76)

where the last equality holds by applying the chain rule of entropy.

**Conditional mutual information.** Given three random variables \( X \), \( Y \), and \( Z \), the conditional mutual information of the random variables \( X \) and \( Y \) given the random variable \( Z \) is summarized as follows:

\( I(X; Y|Z) = \mathbb{E}_{(x,y,z) \sim p_{XYZ}} [\log \frac{p_{X,Y|Z}(x, y|z)}{p_{X|Z}(x|z) p_{Y|Z}(y, z)}] = H(X|Z) - H(X|Y, Z). \) (A.77)

# Properties of mutual information.

+   - Mutual information is nonnegative, that is, \( I(X; Y) \ge 0, \forall X, Y \).
+   - Mutual information is symmetric, that is, \( I(X; Y) = I(Y; X) \).
+   - Mutual information of a random variable with itself is the entropy of that random variable, that is, \( I(X; X) = H(X) \).