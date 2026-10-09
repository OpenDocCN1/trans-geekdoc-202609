In this way, we can project the new sample x into v as follows:

$$(v\cdot \Phi(x)) = \sum_{i=1}^{l} a_{i} k(x_{i}, x) \quad . \tag{9.62}$$

Estimating the covariance matrix of l dimension from l samples may make the matrix N ambiguous. For this reason, a multiple of the unit matrix can be simply added, e.g., replacing N with $N_{\mu}$:

$$N_{\mu} = N + \mu I \quad . \tag{9.63}$$

The above problem can also be considered in one of the following different forms. (i) It makes the numericalisation of the problem more stable, and for a sufficiently large $\mu$, $N_{\mu}$ will become positive definite. (ii) This method is similar to the method in [60], reducing the number of bases based on the sample eigenvalue estimates. (iii) It re- forces the normalisation of $\|a\|^{2}$, which is a suitable solution with a small expansion coefficient. Although the real impact on the normalisation problem is unknown, there is indeed a link in the SVM [55]. In addition, there is a method for normalising N, i.e., using the penalty term $\|v^{2}\|$, which is similar to SVM (plus the full kernel matrix $K_{ij} = k(x_{i}, x_{j})$).

# ### 9.5.4 Kernel of the Lie group

For the sample sets of the Lie group matrix, the matrix itself does not have the dot product. However, the result of matrix multiplication in the group operation is still a matrix. Therefore, the vector-based kernel function cannot be used for samples of the Lie group matrix, and we need to design new kernel functions.

# #### 9.5.4.1 RBF kernel of the Lie group

The Gaussian RBF kernel function is one of the most frequently used kernel functions. It is also called a radial basis function because it performs a good high- dimensional spatial linear mapping for the nonlinear data set of Figure 9.8. The vector-based RBF kernel function is of the form

$$k(x, y) = \exp \left( - \frac{\|x - y\|^{2}}{2 \sigma^{2}} \right) \quad . \tag{9.64}$$

In the above equation, the difference between the two vectors x and y is modulo, and there is no matrix subtraction for the general matrix Lie group. However, in the man- ifold space where the Lie group is located, the component that subtracts another ele- ment from one element can be achieved by the group operation and the inverse of the group element, e.g., $x^{-1}y$, $x, y \in G$. However, in addition to the exchange of the Lie group, the general group of the Lie group is not exchangeable, i.e., $\|x^{-1}y\| \neq \|y^{-1}x\|$. Moreover, for the matrix Lie group, we have $\|\log (x^{-1}y)\| = \|\log (y^{-1}x)\|$. From another