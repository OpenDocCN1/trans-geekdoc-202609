Observe that in equation (27.34),

$$\mu_C C = C_t + C_S \mu S + \tfrac12 C_{SS} \sigma^2 S^2 \tag{27.35}$$ $$\sigma_C C = C_S \sigma S. \tag{27.36}$$

In other words, $\mu_C C$ is the expected change in the call-option price and $\sigma_C^2 C^2$ is the variance of such a change per unit of time. Itô’s lemma simply indicates that if the call-option price is a function of a spot stock price that follows an Itô process, then the call-option price also follows an Itô process with mean and standard deviation parameters that are more complex than those of the stock price. The Itô process for a call is given by equations (27.35) and (27.36).

The infinitesimal change in the value of the portfolio $dP$ is caused by the change in the prices of the assets. This follows from the fact that their respective quantities are rebalanced only after first taking into account the change on the asset prices, in other words the rebalancing strategy is previs- ible. Mathematically this is expressed as $dN_1 = dN_2 = 0$, which yields

$$dP = N_1 (dS) + N_2 (dS) + dQ$$ $$= (\mu dt + \sigma dZ) N_1 S + (\mu_C dt + \sigma_C dZ) N_2 C + r Q \, dt. \tag{27.37}$$

Let $w_1$ be the fraction invested in stock, $w_2$ be the fraction invested in options, and $w_3$ be the fraction invested in the riskless asset. As before, $w_1 + w_2 + w_3 = 1$, that is, all of the funds available are invested in some type of asset and furthermore the dynamic strategy remains at all times self-financing. Set $w_1 = N_1 S / P$, $w_2 = N_2 C / P$, $w_3 = Q / P = 1 - w_1 - w_2$. Then equation (27.37) becomes

$$\frac{dP}{P} = (\mu dt + \sigma dZ) w_1 + (\mu_C dt + \sigma_C dZ) w_2 + (r \, dt) w_3. \tag{27.38}$$

At this point, the notion of economic equilibrium (also called risk-neutral or preference-free pricing) is introduced in the analysis. This notion plays an important role in modeling financing behavior, and its appropriate formulation is considered to be a major breakthrough in financial analysis.

More specifically, design the proportions $w_1, w_2$ so that the position is riskless for all $t \ge 0$, that is, let $w_1$ and $w_2$ be such that $$\operatorname{Var}\left(\frac{dP}{P}\right) = \operatorname{Var}(w_1 \sigma dZ + w_2 \sigma_C dZ) = 0. \tag{27.39}$$