The expression for the stiffness matrix $\mathbf{K}$ is:

```
$$\mathbf{K} = \begin{bmatrix} \mathbf{K}_{aa} & \mathbf{K}_{ab} & \mathbf{K}_{ac} \ \mathbf{K}_{ba} & \mathbf{K}_{bb} & \mathbf{K}_{bc} \ \mathbf{K}_{ca} & \mathbf{K}_{cb} & \mathbf{K}_{cc} \end{bmatrix} \quad (4.30)$
```

where

```
$$\mathbf{K}_{aa}(p,q) = \frac{L}{R} \int_0^L \left[ n^2A_{66} - \frac{n^2B_{66}}{R} + \frac{n^2D_{66}}{4R^2} \right] \varphi_p^{(\eta)}\varphi_q^{(\mu)} + \frac{R^2A_{11}}{L^2} \varphi_p^{(\eta)}\varphi_q^{(\eta)}\] d\eta \quad (4.31)$
```

```
$$\mathbf{K}_{ab}(p,q) = \frac{L}{R} \int_0^L \left( \frac{nRA_{12}}{L} - \frac{nB_{12}}{L} \right) \varphi_p^{(\eta)}\varphi_q^{(\eta)} + \frac{3nD_{66}}{L} \left( \frac{nRA_{66}}{L} - \frac{nB_{66}}{L} \right) \varphi_p^{(\eta)}\varphi_q^{(\eta)}\} d\eta \quad (4.32)$
```

```
$$\mathbf{K}_{ac}(p,q) = \frac{L}{R} \int_0^L \left[ \left( \frac{RA_{12}}{L} + \frac{nB_{12}}{L} \right) \varphi_p^{(\eta)}\varphi_q^{(\eta)} + \left( \frac{n^2D_{66}}{LR} - \frac{2n^2B_{66}}{L} \right) \varphi_p^{(\eta)}\varphi_q^{(\eta)} \rightright] - \frac{R^2B_{11}}{L^3} \varphi_p^{(\eta)}\varphi_q^{(\eta)}\} d\eta \quad (4.33)$
```

```
$$\mathbf{K}_{ba}(p,q) = \frac{L}{R} \int_0^L \left[ \left( \frac{nRA_{12}}{L} + \frac{nB_{12}}{L} \right) \varphi_p^{(\eta)}\varphi_q^{(\eta)} + \frac{3nD_{66}}{4L} \left( \frac{nRA_{66}}{L} - \frac{nB_{66}}{L} \right) \varphi_p^{(\eta)}\varphi_q^{(\eta)}\right] d\eta \quad (4.34)$
```

```
$$\mathbf{K}_{bb}(p,q) = \frac{L}{R} \int_0^L \left[ n^2A_{22} - \frac{2n^2B_{22}}{R} + \frac{n^2D_{22}}{R^2} \right] \varphi_p^{(\eta)}\varphi_q^{(\eta)} + \frac{R^2A_{66}}{L^2} + \frac{3RB_{66}}{L} + \frac{9D_{66}}{4L^2} \varphi_p^{(\eta)}\varphi_q^{(\eta)}\} d\eta \quad (4.35)$
```

```
$$\mathbf{K}_{bc}(p,q) = \frac{L}{R} \int_0^L \left[ \left( \frac{2nRB_{66}}{L^2} + \frac{3nD_{66}}{L^2} \right) \varphi_p^{(\eta)}\varphi_q^{(\eta)} - \left( \frac{nRB_{12}}{L^2} + \frac{nD_{12}}{L^2} \right) \varphi_p^{(\eta)}\varphi_q^{(\eta)}\right] + \left( nA_{22} + \frac{n^2B_{22}}{R} + \frac{n^2D_{22}}{R^2} \right) \varphi_p^{(\eta)}\varphi_q^{(\eta)}\} d\eta \quad (4.36)$
```