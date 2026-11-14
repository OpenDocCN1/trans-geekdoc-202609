# Model fitting

Neural networks have **many** unknown parameters (weights).

# Counting parameters

+   - p + 1 parameters in one node
+     - p covariates plus intercept (bias)
+     - parameters: $(\alpha_{k0}, \alpha_{k1}, ..., \alpha_{kp})$
+   - k = 1, ..., K nodes per layer plus intercept: $(\beta_{g0}, ..., \beta_{gK})$
+   - g = 1, ..., G layers

Total of $K(p + 1) + G(K + 1)$ parameters