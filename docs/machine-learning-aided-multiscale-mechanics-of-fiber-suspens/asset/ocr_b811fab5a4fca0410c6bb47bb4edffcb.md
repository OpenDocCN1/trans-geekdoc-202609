resulting in the equation (Milton, 2002, §9)

```
(1 - f_2)(\bar{\mathbb{A}} - \mathbb{A}_2)^{-1} = (\mathbb{A}_1 - \mathbb{A}_2)^{-1} + f_2 \Gamma_{\mathbb{A}_2}(\mathbf{n}).
```

Here, the coating material \( m_2 \) must not be rigid or a void, the tensor \( (\mathbb{A}_1 - \mathbb{A}_2) \) must be invertible, and \( f_2 \) denotes the volume fraction of the coating material \( m_2 \). Also, the fourth order tensor \( \Gamma_{\mathbb{A}_2}(\mathbf{n}_r) \in (\mathbb{R}^3)^{\otimes 4} \) is defined by equation (5.25) as

```
\Gamma_{\mathbb{A}_2}(\mathbf{n}_r) = \Gamma_{\mathbb{I}}(\mathbf{n}_r) [\Gamma_{\mathbb{I}}(\mathbf{n}_r) \mathbb{A}_2 \Gamma_{\mathbb{I}}(\mathbf{n}_r)]^\dagger \Gamma_{\mathbb{I}}(\mathbf{n}_r),
```

where the inverse is taken on the subspace onto which \( \Gamma_\mathbb{I} \) projects. To compute the effective properties \( \bar{\mathbb{A}} \) of a rank-\( R \) CLM, we recursively apply equation (5.42) for the effective material properties of rank-one layered materials, such that (Milton, 2002, §9)

```
(1 - f_2)(\bar{\mathbb{A}} - \mathbb{A}_2)^{-1} = (\mathbb{A}_1 - \mathbb{A}_2)^{-1} + f_2 \sum_{r=1}^R c_r \Gamma_{\mathbb{A}_2}(\mathbf{n}_r).
```

Here, the scalars \( c_r \) are computed from the volume fractions \( f_1^{(r)} \) of the core material \( m_1 \) in the rank-\( r \) sub layer of the rank-three CLM, such that

```
c_r = \frac{f_1^{(r-1)} - f_1^{(r)}}{f_2},
```

i.e., the properties

```
\sum_{r=1}^R c_r = 1 \quad \text{and} \quad c_r > 0,
```

hold. Because the rank-0 sub layer consists solely of the core material \( m_1 \) by definition, the volume fraction \( f^{(0)} = 1 \) is one. Equation (5.44) is essential to compute the effective properties of layered materials with infinite material contrast, and thus for the treatment of such materials using a DMN architecture. In Appendix A, we employ equation (5.44)