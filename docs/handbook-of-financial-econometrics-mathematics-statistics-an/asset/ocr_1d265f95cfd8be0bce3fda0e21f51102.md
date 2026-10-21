# 51.4.1.5 Out-of-sample pricing performance

In out-of-sample option pricing, the presence of more parameters may actually cause over-fitting and have the model penalized if the extra parameters do not improve its structural fitting. For this purpose, Bakshi et al. rely on the previous day’s option prices to back out the required parameter/volatility values and then use them as inputs to compute the current day’s model-based option prices. Next, they subtract the model-determined price from its observed counterpart, to compute both the absolute and the average percentage pricing errors and their associated standard errors. This prevents the biases in the objective function (equation (51.17)) in favor of more expensive calls, such as long-term and in-the-money calls. To make our results comparable with those of Bakshi et al. (1997), we also follow their approach by changing the objective function in (equation (51.17)) to absolute pricing errors

APE(t) ≡ min_{V(t),Φ} Σ_{n=1}^N |ε_n[V(t),Φ]|  (Table 51.3)  (51.18)

and percentage pricing errors

PPE(t) ≡ min_{V(t),Φ} Σ_{n=1}^N ε_n[V(t),Φ] / Ĉ_n(t, τ_n, K_n).  (Table 51.4).  (51.19)

Pricing errors reported under the heading “All-Options-Based” are obtained using the parameter/volatility values implied by all of the previous day’s call options; those under “Maturity-Based” are obtained using the parameter/volatility values implied by those previous-day calls whose maturities lie in the same category (short-term, medium-term, or long-term) as the option being priced; those under “Moneyness-Based” are obtained using the parameter/volatility values implied by those previous-day calls whose moneyness levels lie in the same category (OTM, ATM, or ITM) as the option being priced.

In Table 51.3, we compare the out-of-sample pricing errors of the CEV model with those of the BS, the SV, the SVSI, and the SVJ models from Bakshi et al. (1997). We mark those results of the CEV model which are better or equal to the results of the SV model. In general, the out-of-sample pricing errors of the CEV model are in-between the BS model and the SVJ model. In OTM and part of the ATM option cases (S/K < 1.00), the CEV model performs better than the SV model, while in the deep ATM and ATM options, the CEV model has larger pricing errors than the SV model. In Table 51.4, percentage pricing errors of the CEV model also show similar