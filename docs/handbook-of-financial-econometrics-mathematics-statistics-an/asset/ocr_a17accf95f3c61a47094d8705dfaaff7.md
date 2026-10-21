to appropriate integrals. Therefore, Itô's formula may be obtained by applying Taylor's theorem instead of remembering the specific result in equation (27.15). More specifically, the differential of Y(t, w) = u[t, S(t, w)], where S(t, w) is a stochastic process with differential given by equation 27.16. It may be computed by using Taylor's theorem and the following multiplication rules

$$dt \times dt = 0, \quad dZ \times dZ = dt, \quad dt \times dZ = 0, \qquad (27.16)$$

as

$$dY = u_t dt + u_S dS + \frac{1}{2} (dS)^2 = u_t dt + u_S (\mu dt + \sigma dZ) + \frac{1}{2} u_{SS} (\mu dt + \sigma dZ)^2.$$

By carrying out these multiplications and using the rules in equation (27.16), equation (27.15) is obtained.

The multiplication rules (27.16) are also a very good guide for applying easily Itô's lemma to functions of more than one variable. Indeed, in a more general case, we have a number of Itô processes X_i with i = 1, ..., N that are driven by m independent Wiener processes

$$dX_i(t) = \mu_i (X_i, t) \cdot dt + \sum_{k=1,\dots,m} \sigma_{ik} (X_i, t) \cdot dZ_k(t, w), \qquad (27.17)$$

and a function that depends on their values Y = f(t, X_1, X_2, ..., X_N). Then the multivariable form of the Itô's lemma takes the form

$$dY(t) = \frac{\partial f}{\partial t} \cdot dt + \sum_{i=1:N} \frac{\partial f}{\partial X_i} \cdot dX_i + \frac{1}{2} \sum_{i,j=1:N} \frac{\partial^2 f}{\partial X_i \partial X_j} \cdot dX_i \cdot dX_j. \qquad (27.18)$$

Now, we can use a set of the extended multiplication rules

$$dt \cdot dt = 0,$$
$$dt \cdot dZ_i = 0,$$
$$dZ_i(t, w) \cdot dZ_i(t, w) = dt,$$
$$dZ_i(t, w) \cdot dZ_j(t, w) = 0, \quad i \neq j, \qquad (27.19)$$

with the help of which we can evaluate multivariate functions of these processes. If the Wiener processes that drive X_i are not independent but correlated, then the corresponding multiplication rule simply changes to

$$dZ_i(t, w) \cdot dZ_j(t, w) = \rho_{ij} \cdot dt, \quad i \neq j. \qquad (27.20)$$