Here, we rewrite the jth equation in our simultaneous equation model (116.41) in terms of the full set of T observations:

y_j = Y_j γ_j + X_j* β_j + ε_j* = Z_j* δ_j + ε_j,   j = 1,2,   (116.44)

where y_j denotes the T × 1 vector of observations for the endogenous variables on left-hand side of jth equation. Y_j denotes the T × 1 data matrix for the endogenous variables on right-hand side of this equation. X_j* is a data matrix for all exogenous variables in this equation. For example, consider the dividend equation in our simultaneous equation model, y_j and Y_j are data matrices defined as ΔDIV and ΔK, respectively. X_j* = [1 ΔDIV_- P*] is a T × 3 data matrix for the exploratory variables, where ΔDIV_- denotes one-period-lagged data matrix of ΔDIV. Z_j* = [ΔK 1 ΔDIV_- P*] is a T × 4 data matrix for all variables on right-hand side of this equation. Since the jointly determined variables y_j and Y_j (ΔDIV and ΔK) are determined within the system, they are correlated with the disturbance terms. This correlation usually creates estimation difficulties because the ordinary least squares estimator would be biased and inconsistent (e.g., Johnston and DiNardo, 1997, Greene, 2018). The two-stage least squares (2SLS) approach is the most common method used to deal with this endogeneity problem resulting from the correlation of Z_j* and ε_j.

However, in reality, the expected earnings (P*) and marginal q (Q*) are not observable. Now we assume that there is an error of measurement in P* and Q* as follows:

P = P* + v_p   and   Q = Q* + v_q,   (116.45)

where P and Q denote observed data matrix of accounting earnings and Tobin's q, respectively. Assume that the measurement errors v_p and v_q are independent of all exploratory variables and random disturbances ε:

y_j = Y_j γ_j + X_j β_j + ν_j = Z_j δ_j + ε_j,   j = 1,2,   (116.46)

where Z_j = [Y_j X_j]. The 2SLS estimation uses all the exogenous variables in this system as instruments to obtain the predictions of Y_j. In the first stage, we regress Y_j on all exogenous variables X = [1 ΔDIV_- K_-1 P Q] in the system to receive the predictions of the endogenous variables on right-hand side of this equation (116.46), Ŷ_j = X(X'X)^-1 X'Y_j. In the second stage, we regress y_j on Ŷ_j and X_j to obtain the estimator of δ_j in equation (116.46). Using Ŷ_j in place of Y_j in Z_j yields W_j = [Ŷ_j X_j]. Note that