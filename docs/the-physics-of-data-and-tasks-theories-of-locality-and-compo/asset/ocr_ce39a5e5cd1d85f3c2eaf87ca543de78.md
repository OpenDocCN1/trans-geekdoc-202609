Computing the averages over the rules, we have:

```
\left\langle h_l^{(l-1)} = \bar{a}_l, h_m^{(l-1)} = \bar{a}_m | \bar{y} \right\rangle_\varphi = p_l^{(l-1)} / Z_y^{(l-1)},
```

```
\left\langle h_l^{(l-1)} = \bar{a}_l, h_m^{(l-1)} \neq \bar{a}_m | \bar{y} \right\rangle_\varphi = p_{\ell-1}(1-p_{\ell-1})\frac{m-1}{mv} / Z_y^{(l-1)},
```

```
\left\langle h_l^{(l-1)} \neq \bar{a}_l, h_m^{(l-1)} \neq \bar{a}_m | \bar{y} \right\rangle_\varphi = f(1-p_{\ell-1})^2\frac{m-1}{mv} / Z_y^{(l-1)},
```

```
Z_y^{(l-1)} = p_l^{(l-1)} + f\frac{m-1}{mv}(1-p_l^{(l-1)})^2,
```

```
\left\langle h_l^{(l-1)} = \bar{a}_l, h_m^{(l-1)} \neq \bar{a}_m \right\rangle_\varphi = 0,
```

```
\left\langle h_l^{(l-1)} \neq \bar{a}_l, h_m^{(l-1)} = \bar{a}_m | \bar{y} \right\rangle_\varphi = f\ p_{\ell-1}(1-p_{\ell-1})\frac{m}{mv} / Z_y^{(l-1)},
```

```
\left\langle h_l^{(l-1)} \neq \bar{a}_l, h_m^{(l-1)} \neq \bar{a}_m | \bar{y} \right\rangle_\varphi = f(1-p_{\ell-1})^2\frac{m}{mv} / Z_y^{(l-1)},
```

```
Z_y^{(l-1)} = f\frac{m}{mv}(1-p_l^{(l-1)})^2,
```

We can combine these results with the margins Equation 357 to obtain a $2 \times 2$ matrix $C$ such that

```
C_{11}^{(l-1)} = \left\langle h_l^{(l-1)} = \bar{a}_l, h_m^{(l-1)} = \bar{a}_m \right\rangle_\varphi, (361)
```

```
C_{12}^{(l-1)} = C_{21}^{(l-1)} = \left\langle h_l^{(l-1)} = \bar{a}_l, h_m^{(l-1)} \neq \bar{a}_m \right\rangle_\varphi, (362)
```

```
C_{22}^{(l-1)} = \left\langle h_l^{(l-1)} \neq \bar{a}_l, h_m^{(l-1)} \neq \bar{a}_m \right\rangle_\varphi, (363)
```

Similarly, the conditional marginals of Equation 358-359 can be written as a $2 \times 2$ matrix $T^{(l-1)}$:

```
T_{11}^{(l-1)} = \left\langle h_l^{(0)} = \bar{a}_l | h_m^{(l-1)} = \bar{a}_l^{(l-1)} \right\rangle_\varphi, (364)
```

```
T_{12}^{(l-1)} = \left\langle h_l^{(0)} = \bar{a}_l | h_m^{(l-1)} \neq \bar{a}_l^{(l-1)} \right\rangle_\varphi, (365)
```

```
T_{21}^{(l-1)} = \left\langle h_l^{(0)} \neq \bar{a}_l | h_m^{(l-1)} = \bar{a}_l^{(l-1)} \right\rangle_\varphi, (366)
```

```
T_{22}^{(l-1)} = \left\langle h_l^{(0)} \neq \bar{a}_l | h_m^{(l-1)} \neq \bar{a}_l^{(l-1)} \right\rangle_\varphi, (367)
```