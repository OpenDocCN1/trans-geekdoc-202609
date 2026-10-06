# Generalized Linear Regression

The derivations stay exactly the same, just the data matrix is now replaced by the basis function matrix, i.e.:

```
$$w^* = (\Phi^T \Phi)^{-1} \Phi^T y$,
```

with $\Phi = \begin{bmatrix} \phi_1^T \ \vdots \ \phi_n^T \end{bmatrix}$

+   - In principle, this allows us to learn any non-linear function, if we know suitable basis functions (which is typically not the case).