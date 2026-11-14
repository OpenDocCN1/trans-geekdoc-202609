```
X^{(k)} = \left[ \sum_{n=0}^{k-1} \left( I - \alpha A^T W A \right)^n \right] \alpha A^T W P + \left( I - \alpha A^T W A \right)^k X^{(0)}.
```

Our FBP algorithm will be derived based on eq. (8.2). There are two terms in eq. (8.2). We will study them one at a time. Let us define two matrices in eq. (8.2):

```
F^{(k)} \equiv \left[ \sum_{n=0}^{k-1} \left( I - \alpha A^T W A \right)^n \right] \alpha A^T W
```

and

```
H^{(k)} \equiv \left( I - \alpha A^T W A \right)^k .
```

Thus eq. (8.2) can be rewritten as

```
X^{(k)} \equiv F^{(k)} P + H^{(k)} X^{(0)} .
```

The first term in eq. (8.5) only depends on the projections \( P \), while the second term only depends on the initial condition \( X^{(0)} \). Equation (8.2) is not in a closed form because there is a \( \sum_{n=0}^{k-1} \) on the right-hand side. Our next step is to remove this \( \sum_{n=0}^{k-1} \) sign.

# 8.2 The Landweber algorithm: from nonrecursive form to closed form

In order to turn \( \sum_{n=0}^{k-1} \left( I - \alpha A^T W A \right)^n \) into a closed form, let us recall the summation formula for the geometric series:

```
\sum_{n=0}^{k-1} r^n = \frac{1-r^k}{1-r} .
```

A similar summation formula exists for matrices:

```
\sum_{n=0}^{k-1} B^n = \left( I - B \right)^{-1} \left( I - B^K \right)
```

if \( \left( I - B \right)^{-1} \) exists. Equation (8.7) can be easily verified by left-multiplying \( \left( I - B \right) \) on both sides. Thus, we have

```
F^{(k)} = \alpha \sum_{n=0}^{k-1} \left( I - \alpha A^T W A \right)^n \alpha A^T W = \left( A^T W A \right)^{-1} \left[ I - \left( I - \alpha A^T W A \right)^k \right] A^T W .
```

If the initial condition is zero, that is, \( X^{(0)} = \vec{0} \), the \( k \)th iteration of the Landweber algorithm has a closed form of