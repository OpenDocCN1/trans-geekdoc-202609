that each asset return satisfies the following system of pricing restrictions

E_t r_{1,t+1} - r_{f,t+1} = - V_{11}/2 + γ V_{1m} + (γ - 1) V_{1h} + (1 - γ) ∑_{l=1}^{L} ω^l V_{1e}^l

+ (1 - γ) ∑_{l=1}^{L} ω^l V_{1eh}^l,

⋮

E_t r_{N,t+1} - r_{f,t+1} = - V_{NN}/2 + γ V_{Nm} + (γ - 1) V_{Nh}

+ (1 - γ) ∑_{l=1}^{L} ω^l V_{Ne}^l + (1 - γ) ∑_{l=1}^{L} ω^l V_{Neh}^l,  (12.41)

where we replace V_{iπ} and V_{iπh} in equation (12.35) with V_{ie} and V_{ieh} because the empirical evidence shows that for our sample countries, the fluctuations in domestic inflation are almost negligible relative to exchange rate changes.⁹

Let r_t denote the N × 1 time series vector which includes N risky assets, r_i ∀ i = 1, …, N. In matrix notation, equations (12.41) and (12.36) can be re-expressed in terms of random log excess return as

[ z_t ; r_t - r_{f,t} i ] = [ Φ z_{t-1} ; -1/2 h_{d,t} + γ h_{m,t} + (γ - 1) h_{h,t} + (1 - γ) h_{e,t} + (1 - γ) h_{eh,t} ] + [ u_t ; ξ_t ],

ε_t = [ u_t ; ξ_t ] | I_{t-1} ~ N(0, H_t),

H_t : (K + N) × (K + N) = [ H^{11}_{K×K}  H^{12}_{K×N} ; H^{21}_{N×K}  H^{22}_{N×N} ],  (12.42)

where i is an N × 1 vector of one, H_t is the conditional covariance matrix of asset returns, h_{d,t} is the diagonal element of H^{22}_{N×N} which denotes the

⁹Note that DeSantis and Gerard (1998) make the same simplification. Our dataset is also similar to theirs.