# 3.3 Hyperbolic Functions

The log-cosh loss is built using hyperbolic functions for the distributions, loss functions and derivatives. As such, it is necessary to refresh our memories about the definitions and identities associated with hyperbolic trigonometric functions. We review the equations and some of their properties below.

Recall the three main hyperbolic functions are

\(\sinh(x) = \frac{e^x - e^{-x}}{2},\)
\(\cosh(x) = \frac{e^x + e^{-x}}{2},\)

and

\(\tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}.\)

We also have the reciprocal hyperbolic functions given by

\(\text{csch}(x) = \frac{1}{\sinh(x)} = \frac{2}{e^x - e^{-x}},\)
\(\text{sech}(x) = \frac{1}{\cosh(x)} = \frac{2}{e^x + e^{-x}},\)

and

\(\coth(x) = \frac{1}{\tanh(x)} = \frac{e^x + e^{-x}}{e^x - e^{-x}}.\)

Some useful properties are as follows:

\(\sinh(-x) = -\sinh(x),\)
\(\cosh(-x) = \cosh(x),\)

and

\(\tanh(-x) = -\tanh(x).\)

Other useful equations include the following:

\(\cosh^2(x) - \sinh^2(x) = 1,\)

and

\(\int_{-\infty}^{x} \frac{1}{\cosh(x)} = \arctan[\sinh(x)] + c.\)

# 3.4 M-Estimation

The log-cosh loss function in machine learning can be used to construct an M-estimator (refer to Chapter 2). The loss function associated with an M-estimator has the general form

\(\text{M-loss} = \sum_{i=1}^n \rho(x_i). \quad (3.4.1)\)