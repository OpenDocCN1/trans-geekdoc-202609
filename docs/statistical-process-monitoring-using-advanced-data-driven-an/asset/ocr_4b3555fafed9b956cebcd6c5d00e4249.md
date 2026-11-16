Importantly, ANFIS first uses a subtractive clustering procedure to find the initial rules and then applies five layers of the neural network model to tune the rule parameters [54]. The first layer in the ANFIS architecture focuses on the fuzzy formation by finding the membership functions for each input value. The second layer (called rule layer) generates fuzzy rules. The main role of the third layer is to normalize membership functions. The fourth layer is responsible for the conclusive part of fuzzy rules, and the last layer provides the final output. In the model training phase, the least-squares and back-propagation gradient descent algorithms are used to evaluate the parameters of the fuzzy inference system [48]. The network weights are trained by minimizing the residuals, e_i, given as

```
J_i = \|\mathbf{e}_i\|^2 = \|\mathbf{U}_i - \mathbf{f}_i(\mathbf{T}_i, \Theta)\|^2. \quad (4.9)
```

Essentially, by keeping the outer relation unchanged, ANFIS-PLS benefits from the PLS characteristics by mapping the process variables in the directions that maximize the covariance. Hence, this allows transforming the multivariate regression problem to several univariate regressions, which are handled individually using ANFIS.

# 4.3.2.1 Nonlinear PLS-based monitoring

Primarily, we have to obtain the model first, then perform fault detection procedures accordingly. The basic point of fault detection using NLPLS approaches is similar to that of using linear PLS. Importantly, the estimation of the residual space, crucial in fault detection, depends on modeling with an appropriate process. Generally, the latent space is monitored by using the Hotelling's \(T^2\), whereas the residual space is inspected via the squared prediction error (SPE) or Q charts [55] (Fig. 4.5). The \(T^2\) statistic is computed as

```
T^2 = \sum_{i=1}^m \left(\frac{t_i}{\lambda_i}\right)^2, \quad (4.10)
```

![](bbox=[0.22, 0.72, 0.78, 0.9])

FIGURE 4.5 NLPLS-based fault detection methodology.