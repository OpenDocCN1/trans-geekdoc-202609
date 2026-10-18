

![StartLayout 1st Row 1st Column rho 1 equals 1 2nd Column equals double-struck upper P left-parenthesis normal upper T Subscript 1 comma 1 Baseline less-than infinity right-parenthesis 2nd Row 1st Column Blank 2nd Column equals sigma-summation Underscript n equals 1 Overscript infinity Endscripts double-struck upper P left-parenthesis normal upper T Subscript 1 comma 1 Baseline equals n right-parenthesis equals sigma-summation Underscript n equals 1 Overscript infinity Endscripts double-struck upper P left-parenthesis normal upper T Subscript 1 comma 1 Baseline greater-than n minus 1 comma bold x Subscript n Baseline equals bold-italic s 1 right-parenthesis 3rd Row 1st Column Blank 2nd Column equals sigma-summation Underscript n equals 1 Overscript infinity Endscripts sigma-summation Underscript i equals 1 Overscript upper K Endscripts double-struck upper P left-parenthesis bold x Subscript n minus 1 Baseline equals bold-italic s Subscript i Baseline comma normal upper T Subscript 1 comma 1 Baseline greater-than n minus 1 comma bold x Subscript n Baseline equals bold-italic s 1 right-parenthesis 4th Row 1st Column Blank 2nd Column equals sigma-summation Underscript n equals 1 Overscript infinity Endscripts sigma-summation Underscript i equals 1 Overscript upper K Endscripts double-struck upper P left-parenthesis bold x Subscript n Baseline equals bold-italic s 1 bar bold x Subscript n minus 1 Baseline equals bold-italic s Subscript i Baseline right-parenthesis double-struck upper P left-parenthesis bold x Subscript n minus 1 Baseline equals bold-italic s Subscript i Baseline comma normal upper T Subscript 1 comma 1 Baseline greater-than n minus 1 right-parenthesis 5th Row 1st Column Blank 2nd Column equals sigma-summation Underscript n equals 1 Overscript infinity Endscripts sigma-summation Underscript i equals 1 Overscript upper K Endscripts p Subscript i comma 1 Baseline double-struck upper P left-parenthesis bold x Subscript n minus 1 Baseline equals bold-italic s Subscript i Baseline comma normal upper T Subscript 1 comma 1 Baseline greater-than n minus 1 right-parenthesis 6th Row 1st Column Blank 2nd Column equals sigma-summation Underscript i equals 1 Overscript upper K Endscripts p SubScript i comma 1 Baseline sigma-summation Underscript m equals 0 Overscript infinity Endscripts double-struck upper P left-parenthesis bold x Subscript m Baseline equals bold-italic s Subscript i Baseline comma normal upper T Subscript 1 comma 1 Baseline greater-than m right-parenthesis 7th Row 1st Column Blank 2nd Column equals sigma-summation Underscript i equals 1 Overscript upper K Endscripts rho Subscript i Baseline p Subscript i comma 1 Baseline period EndLayout](images/c06-math-0076.png)

```math
\rho_1 = 1 = \mathbb{P}(T_{1,1} < \infty)
```

```math
= \sum_{n=1}^{\infty} \mathbb{P}(T_{1,1} = n) = \sum_{n=1}^{\infty} \mathbb{P}(T_{1,1} > n-1, \mathbf{x}_n = \mathbf{s}_1)
```

```math
= \sum_{n=1}^{\infty} \sum_{i=1}^{K} \mathbb{P}(\mathbf{x}_{n-1} = \mathbf{s}_i, T_{1,1} > n-1, \mathbf{x}_n = \mathbf{s}_1)
```

```math
= \sum_{n=1}^{\infty} \sum_{i=1}^{K} \mathbb{P}(\mathbf{x}_n = \mathbf{s}_1 \mid \mathbf{x}_{n-1} = \mathbf{s}_i) \mathbb{P}(\mathbf{x}_{n-1} = \mathbf{s}_i, T_{1,1} > n-1)
```

```math
= \sum_{n=1}^{\infty} \sum_{i=1}^{K} p_{i,1} \mathbb{P}(\mathbf{x}_{n-1} = \mathbf{s}_i, T_{1,1} > n-1)
```

```math
= \sum_{i=1}^{K} p_{i,1} \sum_{m=0}^{\infty} \mathbb{P}(\mathbf{x}_m = \mathbf{s}_i, T_{1,1} > m)
```

```math
= \sum_{i=1}^{K} \rho_i p_{i,1}.
```

