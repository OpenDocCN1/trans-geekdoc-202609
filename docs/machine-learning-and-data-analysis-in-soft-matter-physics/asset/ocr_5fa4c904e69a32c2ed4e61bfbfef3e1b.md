parameters from the autocorrelation function (which is itself obtained from the covariances). This is done using the Yule–Walker equations.

# # Yule-Walker equations

The Yule-Walker equations, named for Udny Yule and Gilbert Walker, are the following set of equations.

```
$$\gamma_m = \sum_{k=1}^P \phi_k \gamma_{m-k} + \sigma_\epsilon^2 \delta_{m,0},$$
```

where m = 0, ..., p, yielding p + 1 equations. Here

$\gamma_m$ is the autocovariance function of $X_t$, $\sigma_\epsilon$ is the standard deviation of the input noise process, and $\delta_{m,0}$ is the Kronecker delta function.

Because the last part of an individual equation is non-zero only if m = 0, the set of equations can be solved by representing the equations for m > 0 in matrix form, thus getting the equation

```
$$\begin{bmatrix} \gamma_1 \\ \gamma_2 \\ \gamma_3 \\ \vdots \\ \gamma_P \end{bmatrix} = \begin{bmatrix} \gamma_0 & \gamma_{-1} & \gamma_{-2} & \cdots \\ \gamma_1 & \gamma_0 & \gamma_{-1} & \cdots \\ \gamma_2 & \gamma_1 & \gamma_0 & \cdots \\ \vdots & \vdots & \vdots & \ddots \\ \gamma_{p-1} & \gamma_{p-2} & \gamma_{p-3} & \cdots \end{bmatrix} \begin{bmatrix} \phi_1 \\ \phi_2 \\ \phi_3 \\ \vdots \\ \phi_p \end{bmatrix}$$
```

which can be solved for all

\(\{\phi_m; m = 1, 2, ..., p\}\). The remaining equation for m = 0 is

```
$$\gamma_0 = \sum_{k=1}^P \phi_k \gamma_{-k} + \sigma_\epsilon^2,$$
```

which, once \(\{\phi_m; m = 1, 2, ..., p\}\) are known, can be solved for \(\sigma_\epsilon^2\).

An alternative formulation is in terms of the autocorrelation function. The AR parameters are determined by the first p+1 elements \(\rho(\tau)\) of the autocorrelation function. The full autocorrelation function can then be derived by recursively calculating

```
$$\rho(\tau) = \sum_{k=1}^P \phi_k \rho(k - \tau)$$
```