where $\mathbf{T}' = \begin{bmatrix} 1 & 1 & 1 & \cdots & 1 \\ T_1 & T_2 & T_3 & \cdots & T_n \end{bmatrix}$, $\mathbf{X}' = \begin{bmatrix} 1 & 1 & 1 & \cdots & 1 \\ X_1 & X_2 & X_3 & \cdots & X_n \end{bmatrix}$, and $\mathbf{Y}' = [Y_1\; Y_2\; Y_3\; \cdots\; Y_n]$.

However, finding an instrumental variable uncorrelated with $\eta_i$ and $\varepsilon_i$ while highly correlated with $V_i$ and $U_i$ is difficult. Durbin (1954) suggests that if the order of $U_i$ is the same as the order of $X_i$, then a better instrumental variable would be $T_i = i$, where $X_i$ are ordered by magnitude. That is,

$T' = \begin{bmatrix} 1 & 1 & 1 & \cdots & 1 \\ 1 & 2 & 3 & \cdots & n \end{bmatrix}$ and $X' = \begin{bmatrix} 1 & 1 & 1 & \cdots & 1 \\ X_1 & X_2 & X_3 & \cdots & X_n \end{bmatrix}$.

This variable will lead to a more efficient estimate than that of the method of grouping. If we let $T_i = 1$ for $X_i$ greater than its median, $T_i = 0$ for $X_i$ equal to its median, and $T_i = -1$ for $X_i$ smaller than its median, then the estimator of the instrumental variable method will be the same as the estimator of Wald’s two-group grouping method. Therefore, Wald’s two-group grouping method is a special case of the instrumental variable method. In other words, the instrumental variable method is more generalized than the grouping method.

Griliches and Hausman (1986) propose an instrumental variable approach to reduce the bias resulted from measurement error. In a penal data framework, they show that instrumental variables estimator is consistent if the measurement error $\varepsilon_{i,t}$ is i.i.d across $i$ and $t$ and unobserved independent variable is serially correlated. An instrumental variable using the lags or the difference of lags of the unobserved independent variable can result in a consistent estimator when $T$ is finite and $N$ approaches to infinite.

However, Griliches and Hausman’s i.i.d assumption is too strong. Bjorn (2000) further relaxes Griliches and Hausman’s i.i.d assumption, and, instead, assumes that the regressor has $\tau$ period moving average process. Bjorn (2000) shows that using the lags of the variables at least $\tau - 2$ periods as instruments can clear the memory of the moving average process and obtain the consistent estimator.

Lewbel (1997) show simple functions of the model data can be used as instruments for two-staged least squares (TSLS) estimation. Such instruments can be used for identification and estimation when no other instruments are available or improve efficiency.

Given the standard linear regression model with measurement error:

$Y_i = a + b'W_i + cX_i + e_i$, and \(37.34\)