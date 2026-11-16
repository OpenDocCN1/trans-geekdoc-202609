TABLE 4.2 Main steps of polynomial PLS modeling algorithm.

1. Autoscale the input–output data (faultless data), X and y
2. Let E_Xj = X, E_yj = y, and j = 1
3. Calculate the loading vector and latent variables for nonlinear PLS using NIPALS procedure [19]
4. Determine the polynomial function f(·) that predicts the LV response u_j using the input latent variable t_j,

u_j = γ0 + γ1t_j + γ2t_j^2 + γ3t_j^3 + ⋯ + ϵ_j. (4.7)
The estimated model is computed so that the regression error is minimized and overfit is avoided
5. Calculate the residual matrices E_Xj = X - X̂ and E_yj = y - ŷ
6. Increment j = j + 1 and go to step 3 until all LVs are computed. Cross-validation is used to find the optimized number of LVs, where the output prediction mean squared error (MSE) is minimized

using fractional polynomials is their ability to produce a better description of data with fewer terms than conventional polynomials [37]. Thus, they are relatively flexible and parsimonious, which makes them more suitable to use in NLPLS than the fixed order polynomials. To alleviate these limitations, other extensions of nonlinear PLS, for example, those based on neural networks (NN), have been developed in order to approximate a nonlinear function of the inner model with more flexibility and fewer assumptions [38]. By using NN to learn and construct the inner model of PLS, the residual can be reduced and prediction improved [39,40,19]. Such network PLS methods, however, are not parsimonious and have the tendency to overfit the data [41]; they are also unstable [42]. Recently, Liu et al. developed a nonlinear PLS model by using a Gaussian process regression, a powerful nonlinear model to construct a nonlinear model between each pair of latent variables in the PLS [43]. In their model, augmented data matrices are included to achieve improved prediction performance. In [44], an adaptive neuro-fuzzy inference system (ANFIS) model is used to model the inner relation between the input and output PCs in order to construct a reliable nonlinear PLS model.

# 4.3.2 ANFIS-PLS modeling framework

This section discusses the basic concept of nonlinear PLS, using the ANFIS method, a robust method to tune the parameters of nonlinear inner relations of the PLS model. Fuzzy model-based fault detection approaches have sparked a flurry of research studies over the past decade, in several fields of engineering [45,46]. In [47], a nonlinear fuzzy PLS using the Takagi–Sugeno–Kang (TSK) fuzzy model has been introduced and showed better prediction capability, compared with the conventional PLS. It has also been shown that the fuzzy PLS model overcomes the quadratic PLS and the traditional linear PLS when