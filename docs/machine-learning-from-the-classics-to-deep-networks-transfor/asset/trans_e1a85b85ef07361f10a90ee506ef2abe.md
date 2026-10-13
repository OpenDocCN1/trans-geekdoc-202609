

$P(f\_{i} = 0|\mathbf{d}) = \exp\left( - \sum\limits\_{j = 1}^{m}\theta\_{ij}d\_{j} \right),$

其中 $\theta\_{ij} := -\ln(1 - P\_{ij})$ 且

$P(f\_{i} = 1|\mathbf{d}) = 1 - \exp\left( - \sum\limits\_{j = 1}^{m}\theta\_{ij}d\_{j} \right).$

观察公式 [(15.1)](#Chp015_755-803_B9780443292385000214.xhtml#deq1) 中对应阴性发现的项，其对复杂度的贡献是线性的（指数的乘积对应于求和）。然而，与阳性发现相关的项则并非如此。例如，考虑所有发现均为阴性的极端情况。此时

```
P(\mathbf{f} = 0|\mathbf{d}) = \prod\limits\_{i = 1}^{n}\exp\left( - \sum\limits\_{j = 1}^{m}\theta\_{ij}d\_{j} \right) = \exp\left( - \sum\limits\_{i = 1}^{n}\left( \sum\limits\_{j = 1}^{m}\theta\_{ij}d\_{j} \right) \right).
```

现在考虑 $f\_1 = 1$ 而其余为 $f\_i = 0$，$i = 2, \dots, n$。此时

