in which $N$ is the number of data and $C(B)$ is a complexity penalty that increases with the number of basis function (BF) in the model. It is defined as

$C(B) = (B + 1) + dB$ (22.12)

where $d$ is a penalty for each BF included into the model and $B$ is number of basis functions [24].

# 22.3.2 GMDH

GMDH is a learning machine based on the polynomial theory of complex systems [22]. From this network, the most significant input parameters, number of layers, the number of neurons in middle layers, and optimal topology design of the network are defined automatically. Therefore, the GMDH network is included those of active neurons known as a self-organized model. The structure of the GMDH network is configured thorough the training stage with polynomial model which produces the minimum error between the predicted value and observed output. The formal definition of the system identification problem is to find an approximate function \(\hat{f}\) that can be used to predict the actual output \(\hat{y}\) or a given input vector \(X = (x_1, x_2, ..., x_n)\) as close as possible to actual output y. Therefore, \(n\) observations of multi-input-single-output data pairs are considered as:

$y_i = f(x_{i1}, x_{i2}, x_{i3}, ... x_{in})(i = 1, 2, ...., M)$ (22.13)

The general relationship between input and output variables can be expressed by a complicated discrete form of the Volterra function, a series in the form of

$y = w_0 + \sum_{i=1}^n w_i x_i + \sum_{i=1}^n \sum_{j=1}^n w_{ij} x_i x_j + \sum_{i=1}^n \sum_{j=1}^n \sum_{k=1}^n w_{ijk} x_i x_j x_k + \cdots$ (22.14)

which is known as the Kolmogorov-Gabor polynomial [36]. In the present study, a quadratic polynomial of the GMDH network is used that is written as:

Quadratic: \(\hat{y} = w_0 + w_1 x_i + w_2 x_j + w_3 x_i x_j + w_4 x_i^2 + w_5 x_j^2\) (22.15)

The weighting coefficients of Eq. (22.14) are calculated using regression techniques such that the difference between actual output, \(y\), and the calculated value, \(\hat{y}\), for each pair of \(x_i\) and \(x_j\) as input variables is minimized. In this way, the weighting coefficients of the quadratic function \(G_i\) are obtained to optimally fit the output to the whole set of input–output data pairs, which is defined as: