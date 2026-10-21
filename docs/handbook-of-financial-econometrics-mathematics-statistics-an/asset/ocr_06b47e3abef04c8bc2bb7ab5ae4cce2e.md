= \frac{B g_0 \exp(At)}{B - g_0 + g_0 \exp(At)}

= \frac{B g_0}{g_0 + (B - g_0) \exp(-At)}. \tag{97C.7}

Substitute $A = \frac{\lambda \bar{r}}{(2 - \lambda)}$ and $B = \bar{r}$ into equation (97C.7), we finally get the solution of equation (97.20),

$g(t) = \frac{\frac{\bar{r}}{(1 - L)}}{1 + \left(\frac{\bar{r}}{g_0} - 1\right) \exp\left(\frac{\lambda \bar{r} t}{\lambda - 2}\right)},$

which is equation (97.21).

# Appendix 97D: Derivation of Equation (97.26)

This appendix presents a detailed derivation of equation (97.26). To obtain the expression for optimal $n(t)$, given $\bar{r}(t) = \bar{r}$, we substitute equation (97.21) into equation (97.18) and obtain

$n(t) = \frac{(2 - \lambda) a' A'(0) \sigma^2(t) e^{\int_0^t g^*(s) ds}}{(1 - \lambda) (\bar{r} - g^*(t))}. \tag{97D.1}$

From equations (97.15), (97.18), and (97.21), we have

$H(t) = \frac{(\bar{r} - g^*(t))^2 (1 - \lambda)}{a' \sigma^2(t) (2 - \lambda)^2}. \tag{97D.2}$

Substituting equations (97D.1) and (97D.2) into equation (97.16), we obtain

$p(t) = \left( \frac{e^{k t}}{n(t)^\lambda} \frac{1 - \lambda}{a' (2 - \lambda)^2} \int_t^T \frac{n(s)^\lambda}{\sigma^2(s)} (\bar{r} - g^*(s))^2 e^{-k s} ds \right), \text{ or }$ 

$p(t) = \left[ \frac{e^{k t - \lambda \int_0^t g^*(s) ds} (1 - \lambda) (\bar{r} - g^*(t))^\lambda}{\sigma^2(t)^\lambda a' (2 - \lambda)^2} \right] W, \tag{97D.3}$

where $W = \int_t^T e^{\lambda \int_0^s g^*(u) du - k s} \sigma^2(s)^{\lambda - 1} (\bar{r} - g^*(s))^{2 - \lambda} ds.$