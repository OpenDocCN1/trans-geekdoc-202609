and Zhao, 2010). Finan cially distressed firms are characterized by lower bond ratings (Kish and Livingston, 1992). In summary, we have the following two propositions.

# **Proposition 8.** A higher ratio of discretionary assets has a positive effect on the sequential conversion rate and reduces the CB’s risk-mitigating effect, which is strengthened for financially distressed firms.

# **Proposition 9.** A higher ratio of free cash flow has a positive effect on the sequential conversion rate and reducing the CB’s risk-mitigating effect, which is strengthened for financially distressed firms.



To infer the above nine propositions regarding the relationships between the rate of sequential conversion and the signaling and risk-mitigating effects of CBs, statistical survival model is considered. The traditional survival model, namely, the Cox proportional hazard model (see, e.g., Cox, 1972) failed to cope with the problem to estimate the instantaneous hazard rate of conversions that occur recurr ently over time. Instead, the recurrent survival analysis technique, an extension of the Cox proportional hazard model, can resolve the problem (see, e.g., Prentice et al., 1981; Andersen and Gill, 1982; Duchateau et al., 2003; Box-Steffensmeier et al., 2006). Depending on events’ categories and dependency within an individual, two types of recurrent survival analysis were developed, namely, the Andersen–Gill (AG) recurrent survival model (see, e.g., Andersen and Gill, 1982) and the conditional risk set model (PWP) by Prentice et al. (1981).



The AG model is based on a non-homogeneous Poisson counting process, in which all the recurrent events within an individual are treated as identical and independent.

The advantage of the AG model lies in its efficiency and precision to give the most reliable estimates of covariate effects (see, e.g., Therneau and Grambsch, 2000).

In the AG model, the instantaneous rate λik(t) of experiencing the kth conversion at time t for the ith bond, 1 ≤ i ≤ N, is a parametric function λik(t) in the form

```
λik(t) = λ0(t) exp{β1 X1i(t) + ⋯ + βq Xqi(t)}, (59.2)
```