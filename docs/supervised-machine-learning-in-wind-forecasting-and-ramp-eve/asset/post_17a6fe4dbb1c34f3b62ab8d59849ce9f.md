

\(\alpha^T (Y - (Xw_1 + eb_1) + e\varepsilon_1 + \xi) = 0. \quad \alpha \ge 0, \quad \beta^T \xi = 0, \quad \beta \ge 0, \quad (4.29)\)

where \(\alpha \in [0, C_1 \varepsilon]\) for \(\beta \ge 0\). These KKT conditions can be written as

\(- \begin{bmatrix} X^T \\ e^T \end{bmatrix} Y + \left( \begin{bmatrix} X^T \\ e^T \end{bmatrix} \begin{bmatrix} X & e \end{bmatrix} + C_3 I \right) \begin{bmatrix} w_1 \\ b_1 \end{bmatrix} + \begin{bmatrix} X^T \\ e^T \end{bmatrix} \alpha = 0, \quad (4.30)\)
\(- Q^T Y + (Q^T Q + C_3 I) u_1 + Q^T \alpha = 0, \quad (4.31)\)

where \(Q = \begin{bmatrix} X & e \end{bmatrix}, u_1 = \begin{bmatrix} w_1^T & b_1 \end{bmatrix}^T\).

Further, we can write \(u_1 = (Q^T Q + C_3 I)^{-1} Q^T (Y - \alpha)\). The dual optimization objective function for the above primal can be written as

\(\max - \frac{1}{2} \alpha^T Q (Q^T Q + C_3 I)^{-1} Q^T \alpha^T + Y^T Q (Q^T Q + C_3 I)^{-1} Q^T \alpha - (e^T \varepsilon_1 + Y^T) \alpha \quad \text{s.t.} \quad \alpha \in [0, C_1]. \quad (4.32)\)

Similarly the other dual can be obtained as

\(\max - \frac{1}{2} \gamma^T Q (Q^T Q + C_4 I)^{-1} Q^T \gamma^T + Y^T Q (Q^T Q + C_4 I)^{-1} Q^T \gamma + (-e^T \varepsilon_2 + Y^T) \gamma \quad \text{s.t.} \quad \gamma \in [0, C_2]. \quad (4.33)\)

Eqs. (4.32) and (4.33) are the duals of the primal objective optimization function. The feature set \(X\) here is linearly separable in the \(n\)-dimensional space. The end regressor \(f(x)\) is given as

\(f(x) = \frac{1}{2}(f_1(x) + f_2(x)) = \frac{1}{2}((w_1 + w_2)^T x + (b_1 + b_2)), \quad (4.34)\)

as the mean of two functions \(f_1(x)\) and \(f_2(x)\), which are the up and down regressors across the predicted hyperplane \(f(x)\).

## Kernel \(\varepsilon\)-twin support vector regression

Regression via SVR may not be always linear, and thus this study needs to be extended to nonlinear regression. A suitable mapping (also called kernel) function is used to transform the input set into higher dimension using \(\phi : \mathbb{R}^n \rightarrow \mathbb{R}^k\), where \(k\) is the dimension of the target space.

![](img/b53e39e35231af65df8ccaa99eb28bee_75_0.png)

## Figure 4.12 Schematic flowchart for \(\epsilon\)-TSVR algorithm.

Fig. 4.12 illustrates step by step the procedure of \(\epsilon\)-TSVR algorithm for regression.

As in [17], the convex optimization problem considering kernel function \(K(X, X^T)\) is given as

```
min 1/2 C3(w1^T w1 + b1^2) + 1/2 ξ*^T ξ + C1 e^T ξ,
s.t. Y - (K(X, X^T)w1 + eb1) = ξ*, (4.35)
Y - (K(X, X^T)w1 + eb1) >= -εe1 - ξ, ξ >= 0, (4.36)
min 1/2 C4(w2^T w2 + b2^2) + 1/2 ξ*^T ξ + C2 e^T η,
s.t. Y - (K(X, X^T)w2 + eb2) = η*, (4.37)
Y - (K(X, X^T)w2 + eb2) >= -εe2 - η, η >= 0, (4.38)
```

where C1, C2, C3, C4 are the hyperparameters for kernel-based \(\epsilon\)-TSVR.

The duals of the primal optimization problems are given as

```
max - 1/2 α^T S(S^T S + C3 I)^-1 S^T α^T + Y^T S(S^T S + C3 I)^-1 S^T α
-(e^T ε1 + Y^T)α   s.t. α ∈ [0, C1], (4.39)
max - 1/2 γ^T S(S^T S + C4 I)^-1 S^T γ^T + Y^T S(S^T S + C4 I)^-1 S^T γ
+(-e^T ε2 + Y^T)γ   s.t. γ ∈ [0, C2], (4.40)
```

![](img/b53e39e35231af65df8ccaa99eb28bee_76_0.png)

## Figure 4.13 River flow forecasting based on \(\epsilon\)-TSVR.

where \(S = [K(X, X^T) e]\), and \(\alpha, \gamma\) are the Lagrangian multipliers, which enable the finding of local maxima and/or minima of the function subject to equality constraints. The end regressor \(f_{\epsilon-TSVR}(x)\) is given as the mean of the two functions:

\( f_{\epsilon-TSVR}(x) = \frac{1}{2}((w_1^T + w_2^T)K(X, X^T) + (b_1 + b_2)). \quad (4.41) \)

## River flow forecasting: a case study for Nile river

Next, we discuss the river flow volume forecasting based on \(\epsilon\)-TSVR model. Monthly mean for river flow volume is collected from https://people.sc.fsu.edu/~jburkardt/datasets/time_series/. A total of 570 samples are taken and are segmented into training (470) and testing (100) sets. The input set for the regression is constructed by wavelet decomposition of river flow time series. The detailed and approximate signals are then treated as predictor variables. Figs. 4.13 and 4.14 illustrate the predicted time-series plots and scatter plots for \(\epsilon\)-TSVR and persistence models.

Based on the manual tuning of the hyperparameters, from Table 4.4 we obtain the RMSE 0.0257 of \(\epsilon\)-TSVR model and 0.6150 of the persistence model.

![](img/b53e39e35231af65df8ccaa99eb28bee_77_0.png)

## Figure 4.14 Scatter plot for \(\epsilon\)-TSVR and persistence algorithm.

## Table 4.4 Performance metrics for \(\epsilon\)-TSVR and persistence model.

| Model | RMSE | MSE | \(R^2\) | NMSE | U1 | U2 |
|---|---|---|---|---|---|---|
| \(\epsilon\)-TSVR | 0.0257 | 0.0006 | 0.9653 | 0.013 | 0.0012 | 0.3440 |
| Persistence | 0.6150 | 0.3782 | 5.5652 | 6.771 | 0.0845 | 6.6146 |

In this chapter, we primarily discussed SVR and its variants for regression analysis. These supervised learning models are applied for wind speed time-series datasets from different places around the globe to assess the performance of each model. The forecasting performance in terms of overfitting and underfitting is further discussed in subsequent chapters. Further, the superiority of hybrid forecasting models has led to an increased research in the field of wind speed forecasting.

## References

- [1] V. Vapnik, A. Lerner, Pattern recognition using generalized portrait method, Automation and Remote Control 24 (1963) 774–780.
- [2] C. Cortes, V. Vapnik, Machine Learning 20 (3) (1995) 273–297.
- [3] T. Joachims, Text categorization with support vector machines: learning with many relevant features, in: Machine Learning: ECML-98, Springer Berlin Heidelberg, 1998, pp. 137–142.
- [4] B. Schölkopf, A. Smola, K.-R. Müller, Kernel Principal Component Analysis, Lecture Notes in Computer Science, Springer Berlin Heidelberg, 1997, pp. 583–588.
- [5] A. Shirzad, M. Tabesh, R. Farmani, A comparison between performance of support vector regression and artificial neural network in prediction of pipe burst rate in water distribution networks, KSCE Journal of Civil Engineering 18 (4) (2014) 941–948.
- [6] V.N. Vapnik, The Nature of Statistical Learning Theory, Springer New York, 2000.
- [7] J. Chen, H. Chen, Y. Huo, W. Gao, Application of SVR models in stock index forecast based on different parameter search methods, Open Journal of Statistics 07 (02) (2017) 194–202.
- [8] Y. Tao, H. Yan, H. Gao, Y. Sun, G. Li, Application of SVR optimized by Modified Simulated Annealing (MSA-SVR) air conditioning load prediction model, Journal of Industrial Information Integration 15 (2019) 247–251.
- [9] W.-C. Hong, Y. Dong, F. Zheng, C.-Y. Lai, Forecasting urban traffic flow by SVR with continuous ACO, Applied Mathematical Modelling 35 (3) (2011) 1282–1291.
- [10] X. Wang, J. Wen, S. Alam, X. Gao, Z. Jiang, J. Zeng, Sales growth rate forecasting using improved PSO and SVM, Mathematical Problems in Engineering 2014 (2014) 1–13.
- [11] J. Suykens, J. Vandewalle, Neural Processing Letters 9 (3) (1999) 293–300.
- [12] J. Liu, H. Zheng, Y. Zhang, X. Li, J. Fang, Y. Liu, C. Liao, Y. Li, J. Zhao, Dissolved gases forecasting based on wavelet least squares support vector regression and imperialist competition algorithm for assessing incipient faults of transformer polymer insulation, Polymers 11 (1) (2019) 85.
- [13] R.M. Adnan, X. Yuan, O. Kisi, R. Anam, Improving accuracy of river flow forecasting using LSSVR with gravitational search algorithm, Advances in Meteorology 2017 (2017) 1–23.
- [14] Uci machine learning repository: combined cycle power plant data set, https://archive.ics.uci.edu/ml/datasets/Combined+Cycle+Power+Plant, 2019. (Accessed 22 August 2019).
- [15] X. Peng, TSVR: an efficient twin support vector machine for regression, Neural Networks 23 (3) (2010) 365–372.
- [16] D. Gupta, M. Pratama, Z. Ma, J. Li, M. Prasad, Financial time series forecasting using twin support vector regression, PLoS ONE 14 (3) (2019) e0211402.
- [17] Y.-H. Shao, C.-H. Zhang, Z.-M. Yang, L. Jing, N.-Y. Deng, An ε-twins support vector machine for regression, Neural Computing & Applications 23 (1) (2012) 175–185.

