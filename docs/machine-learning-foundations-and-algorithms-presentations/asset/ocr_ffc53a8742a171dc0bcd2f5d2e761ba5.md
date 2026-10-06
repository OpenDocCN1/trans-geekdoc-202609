# # Regularized Least Squares

With the sum-of-squares error function and a quadratic regularizer, we get

```
$$L_{\text{ridge}} = (y - \Phi w)^T(y - \Phi w) + \lambda w^T w$
$E_D(w) \quad E_W(w)$
```

+   - This particular choice of regularizer is known as **weight decay** because in sequential learning algorithms, it encourages weight values to decay towards zero, unless supported by the data.
- In statistics, it is called **ridge regression**.

Derivations can be done similarly as before. The solution is given by

```
$$w^*_{	ext{ridge}} =(\Phi^T \Phi + \lambda I)^{-1}\Phi^T y$$
```

+   - $I$ is the Identity matrix
- The matrix $(\Phi^T \Phi + \lambda I)$ is now full rank and can be more easily inverted