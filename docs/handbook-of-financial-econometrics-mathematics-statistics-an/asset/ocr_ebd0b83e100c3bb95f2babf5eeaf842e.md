Finally, inserting the values for the first and second securities yields

```
$$E(R_p) = (-0.0013 - 0.0147) W_1 + (0.0079 - 0.0147) W_2 + 0.0147$$ $$= -0.016 W_1 - 0.0068 W_2 + 0.0147. \tag{80A.3}$$
```

As can be seen, equation (80A.3) is a linear function in two variables and as such is readily graphable. Since given a certain level of portfolio return the function will solve jointly for the weights of securities 1 and 2, it solves indirectly for the weight of security 3.

The variance formula shown in equation (80.16) is converted in a similar manner by substituting in equation (80A.1) as follows:

```
$$\sigma_p^2 = \sum_{i=1}^{3} \sum_{j=1}^{3} W_i W_j \operatorname{Cov}(R_i, R_j) = \operatorname{Var}(R_p)$$ $$= W_1^2 \sigma_{11} + W_2^2 \sigma_{22} + W_3^2 \sigma_{33} + 2W_1W_2\sigma_{12} + 2W_1W_3\sigma_{13}$$ $$\quad + 2W_2W_3\sigma_{23}$$ $$= W_1^2 \sigma_{11} + W_2^2 \sigma_{22} + (1 - W_1 - W_2)^2 \sigma_{33} + 2W_1W_2\sigma_{12}$$ $$\quad + 2W_1(1 - W_1 - W_2)\sigma_{13} + 2W_2(1 - W_1 - W_2)\sigma_{23}$$ $$= (\sigma_{11} + \sigma_{33} - 2\sigma_{13})W_1^2 + (2\sigma_{33} + 2\sigma_{12} - 2\sigma_{13} - 2\sigma_{23})W_1W_2$$ $$\quad + (\sigma_{22} + \sigma_{33} - 2\sigma_{23})W_2^2 + (-2\sigma_{33} + 2\sigma_{13})W_1$$ $$\quad + (-2\sigma_{33} + 2\sigma_{13})W_2 + \sigma_{33}. \tag{80A.4}$$
```

Inserting the covariances and variances of the three securities from Table 80.3 yields

```
$$\sigma_p^2 = [0.0226 + 0.0581 - 2(0.0007)]W_1^2$$ $$\quad + [2(0.0581) + 2(0.0003) - 2(0.0007) - 2(0.0009)]W_1W_2$$ $$\quad + [0.0404 + 0.0581 - 2(0.0009)]W_2^2$$ $$\quad + [-2(0.0581) + 2(0.0007)]W_1 + [-2(0.0581) + 2(0.0007)]W_2$$ $$\quad + 0.0581$$ $$= 0.0793W_1^2 + 0.1136W_1W_2 + 0.0967W_2^2 - 0.1148W_1$$ $$\quad -0.1148W_2 + 0.0581. \tag{80A.5}$$
```