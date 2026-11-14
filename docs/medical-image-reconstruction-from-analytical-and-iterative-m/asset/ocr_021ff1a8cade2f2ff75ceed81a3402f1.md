X^{(k)} = (A^T W A + \beta I)^{-1} \left[ I - (I - \alpha a^T W A - \alpha \beta I)^k \right] A^T W P, \quad (8.23)

and the corresponding modified ramp function for the noise-weighted Bayesian FBP algorithm is given as

RAMP_m(\omega) = \frac{w_m}{w_m/|\omega| + \beta} \left[ 1 - \left( 1 - \frac{\alpha w_m}{|\omega|} - \alpha \beta \right)^k \right] = |\omega| \frac{1}{1 + \beta |\omega| / w_m} \left[ 1 - \left( 1 - \frac{\alpha w_m}{|\omega|} - \alpha \beta \right)^k \right], \quad (8.24)

where m is the angle index and w_m is the noise weighting for the mth angle. In a Bayesian algorithm, the iteration number can be arbitrarily large. Let k -> infinity, then the window function associated with eq. (8.24) becomes

W_m(\omega) = \frac{1}{1 + \beta |\omega| / w_m}. \quad (8.25)

In order to see what this window function W_m(\omega) in eq. (8.25) looks like, let us plot some cases of the window function in Figure 8.5. Let the sampling interval on [0, 0.5] be 0.5/512 = 1/1,024. Let beta/a be 1. It is observed from Figure 8.5 that a smaller weight w_m gives a narrower bandwidth and stronger lowpass filtering.

The implementation of a noise-weighted Bayesian-FBP algorithm is almost the same as a noise-weighted Landweber FBP algorithm; the only difference is in the window function expressions.

![](bbox=[0.13, 0.56, 0.63, 0.85])

Fig. 8.5: Window functions for the Bayesian-FBP algorithm with w_m = 0.1, 0.4, and 0.7, respectively.