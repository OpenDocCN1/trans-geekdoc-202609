difference between the current date and previous date of transaction by DH. Time decay function (e ^-dt) establishes the principle that states the more recent the transaction higher the value of DRscore. The formula to calculate DRscore is given in equation 6. Agent calculates confidence by estimating divergence (Div) in total TE and DRscore values. Div is given by equation 6.4. Confidence achieved by the agent is given in equation 6.5. Finally, the DR of DH is the product of confidence with the total DRscore value given by equation 6.6.

```
Tscore = s/n  (6.1)
TE = e^-dt * Tscore  (6.2)
DRscore = TE / Σ e^-dt  (6.3)
Div = | Σ TE - Σ DRscore |  (6.4)
Conf = k1 * k2 * (1-Div)  (6.5)
```

k1 = 1 if (t_c - t0) * ψ < N, else k1 = N / ((t_c - t0) * ψ)

k2 = 1 if (t_c - t0) * φ < S, else k2 = S / ((t_c - t0) * φ)

t_c: current date of transaction with DH

t_p: previous dates of transaction with DH.

N: Total number of transaction, S: Total number of successful transaction

t0: date of first transaction

ψ: Threshold for number of transactions per day

φ: Threshold for successful transactions per day

Thresholds ψ, φ can be set as per the requirements of the user.

```
DR = Conf * Σ DRscore  (6.6)
```

Fig. (6.2) shows the logical community-level view of MRep where α, β, γ and δ signifies weight to R, F, N and S groups respectively.