for \( k \in \mathbb{N}_0 \), since \( b c'(\text{prox}_{b\zeta}(u)) + \text{prox}_{b\zeta}(u) - u = 0 \) by the definition of \( \text{prox}_{b\zeta} \) in (4.25) for \( b > 0 \).

Given \( \bar{b}_0 > 0 \), \( \hat{\beta}^0 \in \mathbb{R}^p \) and \( \theta^0 := X \hat{\beta}^0 \), the GAMP recursion (4.29) therefore takes the form

```
\(\hat{\beta}^{k+1} = \delta \bar{b}_{k+1} X^T \{ y - \zeta'(\text{prox}_{\bar{b}_k \zeta}(\theta^k + \bar{b}_k y)) \} + \frac{\bar{b}_{k+1}}{\bar{b}_k} \hat{\beta}^k,\)
\(\theta^{k+1} = X \hat{\beta}^{k+1} - \bar{b}_{k+1} \{ y - \zeta'(\text{prox}_{\bar{b}_k \zeta}(\theta^k + \bar{b}_k y)) \}\)
```

for \( k \in \mathbb{N}_0 \), where \( \bar{b}_{k+1} = -1/(\delta \bar{c}_k) \). Using (4.9) from Lemma 4.1, as well as (4.27), we now write the corresponding state evolution recursion (4.6)–(4.7) for (4.66) in terms of \( \bar{\mu}_k := \delta \bar{\mu}_k \mu_k \) and \( \bar{\sigma}_k := \delta \bar{b}_k \sigma_k \). This yields

```
\(\bar{b}_{k+1} = \frac{\bar{b}_k}{\delta} \left( 1 - \mathbb{E} \left\{ \frac{1}{1 + \bar{b}_k \zeta''(\text{prox}_{\bar{b}_k \zeta}(Z_k + \bar{b}_k Y))} \right\} \right)^{-1},\)
\(\bar{\mu}_{k+1} = \frac{\delta^2 \bar{b}_{k+1}}{\mathbb{E}(\bar{\beta}^2)} \mathbb{E} \left( Z \left\{ Y - \zeta'(\text{prox}_{\bar{b}_k \zeta}(Z_k + \bar{b}_k Y)) \right\} \right) + \bar{\mu}_k,\)
\(\bar{\sigma}_{k+1}^2 = \delta^2 \bar{b}_{k+1}^2 \mathbb{E} \left( \left\{ Y - \zeta'(\text{prox}_{\bar{b}_k \zeta}(Z_k + \bar{b}_k Y)) \right\}^2 \right)\)
```

for \( k \in \mathbb{N}_0 \), where given independent \( Z \sim N(0, \mathbb{E}(\bar{\beta}^2)/\delta) \), \( \tilde{G}_k \sim N(0, 1) \) and \( \bar{\varepsilon} \sim P_{\bar{\varepsilon}} \), we set

```
\( Y = h(Z, \bar{\varepsilon}) = \mathbb{1}_{\{\bar{\varepsilon} \le \zeta'(Z)\}}, \quad Z_k = \mu_{Z,k} Z + \sigma_{Z,k} \tilde{G}_k = \bar{\mu}_k Z + \delta^{-1/2} \bar{\sigma}_k \tilde{G}_k \)
```

in view of (4.63), (4.8) and the definition of \( f_{k+1} \) in (4.65). Sur and Candès (2019b, Section 3.1) showed that (4.67) is equivalent to the original state evolution recursion they defined in Sur and Candès (2019a, Section 4.1).

In accordance with **Step 1** in Section 4.4, we seek a fixed point \( (\hat{\beta}^*, \theta^*, \bar{\mu}_*, \bar{\sigma}_*, \bar{b}_* > 0) \) of (4.66)–(4.67) satisfying

```
\(\theta^* = X \hat{\beta}^* - \bar{b}_* \{ y - \zeta'(\text{prox}_{\bar{b}_* \zeta}(\theta^* + \bar{b}_* y)) \},\)
\( 0 = X^T \{ y - \zeta'(\text{prox}_{\bar{b}_* \zeta}(\theta^* + \bar{b}_* y)) \},\)
```

```
\(\bar{\sigma}_*^2 = \delta^2 \bar{b}_*^2 \mathbb{E} \left( \left\{ Y - \zeta'(\text{prox}_{\bar{b}_* \zeta}(Z_* + \bar{b}_* Y)) \right\}^2 \right),\)
\( 0 = \mathbb{E} \left( Z \left\{ Y - \zeta'(\text{prox}_{\bar{b}_* \zeta}(Z_* + \bar{b}_* Y)) \right\} \right),\)
```