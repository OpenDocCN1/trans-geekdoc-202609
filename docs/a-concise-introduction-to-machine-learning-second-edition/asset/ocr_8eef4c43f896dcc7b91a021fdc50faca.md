![](bbox=[0.218, 0.193, 0.781, 0.368])

![](bbox=[0.218, 0.381, 0.781, 0.56])

Figure 6.6: Data generated for $
u = 2$.

The variance of each element $\Sigma_{ij}$ of $\Sigma$ is calculated as

```
$var[\Sigma_{ij}] = \frac{(
u - d + 1)\Psi_{ij} + $(
u - d - 1)\Psi_{ji}}{(\nu - d - 1)^2(\nu - d - 3)} = var[\Sigma_{ji}],
```

where $\Psi$ is symmetric. On the diagonal, as is $i = j$, this simplifies to

```
$var[\Sigma_{ii}] = \frac{2\Psi_{ii}}{(\nu - d - 1)^2(\nu - d - 3)}$
```

Since $
u$ appears several times in the denominator, it controls the variability in the generated datasets and in turn which are generated. The variability decreases as $
u$ increases. Figures 6.6 and 6.7 show the differences in generated datasets for $
u = 2$ the smallest possible choice, and $
u = 10$ for constant $\alpha = 10$, $\lambda = 1$ and

```
$$\Psi = \left( \begin{matrix} 1 & 3/2 \ 3/2 & 1 \end{matrix} \right).$$
```