Either way, the optimization process includes an estimate of a risk-aversion coefficient ($\lambda$). It can be estimated by the CAPM risk premium, $[E (R_m) - R_f]$, relative to the variance of the portfolio. It represents a return–risk tradeoff that is central to portfolio analysis. During the reverse optimization, it scales the estimates of the variance–covariance matrix. Combined with the capitalized market weights, the result is the implied vector of equilibrium returns, as follows:

```
\(\Pi = \lambda\Sigma w_m\) (6)
```

where,

+   - \(\Pi\) is the implied excess equilibrium return vector ($N \times 1$ column vector);
+   - \(\lambda\) is the risk-aversion coefficient, which incorporates the expected return-risk tradeoff;
+   - \(\Sigma\) is the variance–covariance matrix of excess returns ($N \times N$ matrix); and,
+   - \(w_m\) is the market capitalization weights ($N \times 1$ column vector) of the assets.*

The optimization procedure used here is standard, as opposed to those that rely on “shrinkage” of the data or other means of data arrangement (Jorion 1991). Incorporated into the optimization, the estimates from equation (4) embody an exponentially weighted moving average (EWMA) coefficient of 0.97, as reportedly used by major financial institutions (Hoadley 2017). It weighs more recent observations more heavily than older observations, helping to capture any possible momentum effects. It is defined as follows:

```
$EWMA_{i,t} = \gamma R_{i,t} + (1-\gamma)EWMA_{i,t-1}$ (7)
```

where,

+   - $EWMA_{i,0} = $ arithmetic average of the historical rates of return;
+   - $R_{i,t} = $ rate of return on security $i$ at time $t$;
+   - $n = $ number of observations, including $EWMA_{i,0}$; and
+   - $\gamma = 0 < \gamma \le 1$, which determines the length of the memory, in this case, 0.97.

* Formally, $N$ assets make up the market, with $M_p$ representing the market portfolio and \(\Sigma\) representing the variance–covariance matrix. The equilibrium expected returns on the securities, in the form of a vector, have a mean of $\mu$, with $\lambda$ reflecting risk tolerance. The equilibrium CAPM expected returns are \(\Pi = \lambda \Sigma P_M\). The optimal portfolio $M_p^* = \Sigma^{-1} \mu / \lambda\).