lower value results in a larger model with more basis functions. For further information on the selection of d values and a comprehensive explanation of the non-parametric MARS algorithm, please refer to Friedman’s work from 1991.

The format for the MARS equations expressed in terms of max(.) for univariate linear regression of the pth piece of variable x_k as the basis function is presented in Eq. (7.14). This mathematical expression demonstrates how BF_p() is represented within the MARS framework. To ensure clarity, appropriate synonyms have been used, and sentences have been rearranged without altering the intended meaning.

```
$BF_p(x_k) = \max(0, x_k - a_p) \text{ or } BF_p(x_k) = \max(0, a_p - x_k). \quad (7.14)$
```

In mathematical notation, the term max(.) indicates that solely the positive portion of the input is preserved while assigning a zero value to the negative portion, as presented in equation (7.15). Piecewise linear functions can be represented in the form of max(x_k - a_p), with the knot point specified at a particular value a_p.

```
$\max(0, x_k - a_p) = \begin{cases} x_k - a_p, x_k \ge a_p \\ 0, \text{otherwise} \end{cases}, \quad (7.15)$
```

To create a local linear regression with continuous knots, the max (.) function is utilized. Through recursive spline fitting and splitting, the knots are best chosen. The Eq. (7.14) BF_p(x_k) will only be zero when the second term in the equation exceeds zero, which is a crucial point to remember. Additionally, when modeling two variable interactions, the basis function BF_ps() can be expressed using two univariate basis functions for x_k and x_i, as shown in Eq. (7.16):

```
$BF_{ps}(x_k, x_i) = BF_p(x_k) \times BF_s(x_i). \quad (7.16)$
```

# 2.3.2 Group Method of Data Handling (GMDH)

In this study, GMDH is used to develop an explicit mathematical model with degrees of the polynomials to predict the oil recovery factor for CO₂-LSWAG under the miscible condition in a carbonate reservoir. Ivakhnenko (1966) cyberneticist proposed a GMDH polynomial neural network (PNN)) algorithm for constructing high-order regression-type polynomials. However, due to the self-organising nature of the GMDH algorithm (selecting its own input parameters automatically based on the parameter’s contribution to the final output), the GMDH modelling approach is able to overcome many artificial neural network (ANN) limitations as an alternative method (Lv et al., 2023). GMDH employs optimisation criteria to determine network