# Stein–Saleh-type vs. Ridge:

From the risk functions, we have

```
ADL_2^*-risk\left(\hat{\beta}_n^{SSR}\right) - ADL_2^*-risk\left(\hat{\beta}_n^{ridgeR}(k)\right) = \eta^2 \left[ tr C_{11:2}^{-1} + tr(C_{22:1}^{-1}) \right. \\ - \left. \left\{ (p_2 - 2) tr C_{22:1}^{-1} \left( 2E[\chi_{p_2+2}^{-2}(\Delta^2)] - (p_2 - 2)E[\chi_{p_2+2}^{-4}(\Delta^2)] \right) \right\} \right. \\ + \left. (p_2^2 - 4)\Delta^2 Ch_{min}(C_{22:1}^{-1}) E[\chi_{p_2+4}^{-4}(\Delta^2)] \right] \\ - \eta^2 \left[ tr(I_{p_2} + k C_{22:1}^{-1})^{-2} C_{22:1}^{-1} \right] \\ - k^2 \delta_2^T (C_{22:1} + k I_{p_2})^{-2} \delta_2 \\ = \eta^2 \left[ tr(C_{22:1}^{-1}) \left\{ (p_2 - 2) tr C_{22:1}^{-1} \left( 2E[\chi_{p_2+2}^{-2}(\Delta^2)] \right. \right. \right. \\ - \left. \left. \left. (p_2 - 2)E[\chi_{p_2+2}^{-4}(\Delta^2)] \right) \right\} \right. \\ - \left. \eta^2 \left[ tr(I_{p_2} + k C_{22:1}^{-1})^{-2} C_{22:1}^{-1} \right] \right. \\ - \left. k^2 \delta_2^T (C_{22:1} + k I_{p_2})^{-2} \delta_2 + (p_2^2 - 4)\Delta^2 Ch_{min}(C_{22:1}^{-1}) E\left[ \chi_{p_2+4}^{-4}(\Delta^2) \right] \right] \ge 0.
```

On the other hand, we can obtain

```
ADL_2-risk\left(\hat{\beta}_n^{SSR} : c_{11:2}, C_{22:1}\right) - ADL_2-risk\left(\hat{\beta}_n^{ridgeR}(k_{opt}) : c_{11:2}, C_{22:1}\right) \\ = \eta^2 \left\{ p_2 - (p_2 - 2)^{\epsilon} E[\chi_{p_2}^{-2}(\Delta^2)] - \frac{p_2 \Delta^2}{p_2 + \Delta^2} \right\}.
```

See Saleh et al. (2019).

Note that the first function is increasing in \(\Delta^2\) with its minimum at \(\Delta^2 = 0\) and as \(\Delta^2 \to \infty\), it tends to \(p_2\). The second function is also increasing in \(\Delta^2\) with a value 0 at \(\Delta^2\) and approaches the value \(p_2\) as \(\Delta^2 \to \infty\). Hence, the risk difference is non-negative for all \(\Delta^2 \ge 0\). Therefore, the ridge-type uniformly outperforms Stein–Saleh-type.

# PRSRE vs. Ridge-type:

From the risk functions we obtain

```
ADL_2^*-risk\left(\hat{\beta}_n^{SSR+}\right) - ADL_2^*-risk\left(\hat{\beta}_n^{ridgeR}(k)\right) \\ = ADL_2-risk(\hat{\beta}_n^{SSR}) - ADL_2-risk(\hat{\beta}_n^{ridgeR}(k)) \\ - \eta^2 tr(C_{11:2}) E[(1 - (p_2 - 2)\chi_{p_2+2}^{-2}(\Delta^2)) I(\chi_{p_2+2}^2(\Delta^2) < p_2 - 2)] \\ + \Delta^2 Ch_{min}(C_{22:1}^{-1}) \{ 2E[(1 - (p_2 - 2)\chi_{p_2+2}^{-2}(\Delta^2)) I(\chi_{p_2+2}^2(\Delta^2) < p_2 - 2)]
```