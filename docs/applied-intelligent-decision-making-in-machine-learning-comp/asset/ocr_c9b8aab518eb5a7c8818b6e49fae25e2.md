# A Multi-Stage Hybrid Model for Odia Compound Character Recognition 59

a rank-order-matching problem. For this, the Kendall rank correlation coefficient (KRCC) is used and Equation 3. describes KRCC values. Here, the target vector is formed by collecting the top, left, bottom, and right projection sequentially. The image is normalized to $60 \times 60$, the vector size becomes $1 \times 24$.

```
$$\tau = \frac{N_{cp}-N_{dp}}{n(n-1)/2}$ \qquad (3.3)
```

where $N_{cp}$ is the number of concordant pairs and $N_{dp}$ is the number of discordant pairs. Let $\{X_1,X_2,...,X_n\}$ be the observed/target vector and $\{Y_1,Y_2,...,Y_n\}$ be the reference vector, then the random variable is $\{(X_1,Y_1), (X_2,Y_2), ...,(X_n,Y_n)\}$. A set of observations $(X_i,Y_i)$ and $(X_j,Y_j)$ is said to be concordant if $X_i > X_j$ and $Y_i > Y_j$ or $X_i < X_j$ and $Y_i < Y_j$. Similarly a pair $(X_i,Y_i)$ and $(X_j,Y_j)$ is discordant if $X_i > X_j$ and $Y_i < Y_j$ or $X_i < X_j$ and $Y_i > Y_j$. If $X_i = X_j$ or $Y_i = Y_j$ then the pair is neither concordant discordant. The KRCC value varies from -1 to 1, where -1 represents completely out of agreement, 1 represents exactly the same, and zero represents the two vectors being independent. For matching characters, the value closest to 1 is preferred.

# 3.2.4 LOCAL FRE DESCRIPTOR

A local descriptor [23] has been derived from LFD [22]. Here we consider neighbor pixels with radius $R$. Let LCF = $\{f_1,...,f_p\}$ be the set of neighbor pixels that are located around the centre. The local frequency descriptor can be expressed as:

```
$LFD(n) = \sum_{k=1}^{P} f_k e^{\frac{-2\pi(k-1)}{P}}, \qquad for(n=1,...,P)$ \qquad (3.4)
```

where LFD(n) is a vector of $1 \times P$ corresponding to the frequency component of the neighbor pixels in LCF. Among P components, LDF(2) contains the most edge information. The local frequency frequency gradient descriptor (LDFG) is calculated by setting $n = 2$:

```
$LDFG = \sum_{k=1}^{P} f_k e^{\frac{-2\pi(k-1)}{P}}$ \qquad (3.5)
```

LDFG is a complex value; to use it in a neural network Equation 3.5 can be decomposed into real and imaginary parts as:

```
$Re(LDFG) = \sum_{k=1}^{P} f_k \cos(\frac{-2\pi(k-1)}{P})$ \qquad (3.6)
```

```
$Im(LDFG) = -\sum_{k=1}^{P} f_k \sin(\frac{-2\pi(k-1)}{P})$ \qquad (3.7)
```