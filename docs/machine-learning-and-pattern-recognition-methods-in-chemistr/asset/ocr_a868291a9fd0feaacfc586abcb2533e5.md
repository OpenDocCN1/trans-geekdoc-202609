Soft constraints in curve resolution problems 17

Based on the proposed procedure, the estimated concentration profile of the component of interest, **c<sub>aug</sub> (ns × nf)**, should be folded into a matrix, **C(ns × nf)**, where *ns* is the number of samples (rows) of each data matrix, and *nf* is the number of augmented data. In the next step, principal component analysis (PCA) was performed on the **C** matrix to evaluate the deviations of the estimated concentration profiles from the trilinearity constraints. Since the estimated concentration profiles of the different matrices will have the same shape in the ideal cases where trilinearity holds, the first singular value would be significantly larger than the others. In such cases, the value of *k* is expected to be very small or close to zero, and mostly describes the noise variation. The control parameter, *α*, is used to tolerate small deviations from the trilinearity constraints in finding the feasible solutions. The larger parameter *α*, the greater the accepted deviations from the trilinearity constraints. In the grid search algorithm with soft trilinearity constraints, the feasible solution grid points are where the calculated value of *k* for the desired component is less than *α*. Fig. 1.4 represents the implementation of soft trilinearity constraints graphically.

# Matricizing three-way data

# Calculation of k value for resolved profile

![](bbox=[0.147, 0.545, 0.856, 0.829])

**Fig. 1.4** Schematic representation of applying soft trilinearity constraints. The first column of the resolved concentration matrix is folded to give matrix **C₁**. The k value can be obtained by applying PCA on the **C₁**, and calculating the eigen values. (From Tavakk, E., Abdolloahi, H., Gemperline, P.J. (2020). Soft-trilinear constraints for improved quantitation in multivariate curve resolution. Analyst, 145 (1), 223–232).