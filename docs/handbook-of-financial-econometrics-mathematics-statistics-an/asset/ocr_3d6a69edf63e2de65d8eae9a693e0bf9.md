The dependent variable, *EARLY_ij*, is equal to 1 if BHC *i* early adopted the accounting standard *j* and 0 otherwise. *YEAR_N* is an indicator variable equal to 1 if the accounting standard was issued in year *N* and 0 otherwise. All other variables are defined in Appendix 17B. As an examination of Hypothesis 1, the test variable of interest is *ROA*; β₁ is expected to be negative. To test hypothesis 2, the test variables are *AFSOFINV*, *LOANRISK*, *EXPOSUREDER*, *CREDITRISKDER*, and *NONINTCHG*; the respective coefficients are expected to be positive. The static logit model assumes independence between the response variables (i.e., early adoption decisions) given the covariates and does not include the lagged response variable in the regressors.

To test whether the motivation for information disclosure/signaling to better access external financing varies with the potential income effect upon adoption of a standard (i.e., Hypothesis 3), the following logit model (unbalanced static binary panel data analysis) is estimated with heteroskedasticity-corrected standard errors and separately for accounting standards with (1) income-decreasing effects, (2) income-increasing effects, (3) *ex ante* undetermined income effects, and (4) only disclosure requirements:

*EARLY_ij* = β₀ + β₁*ROA_ij* + β₂*RPCERTAINTY_ij*  
+ β₃*ROA_RPCERTAINTY_ij* + β₄*AFSOFINV_ij*  
+ β₅*LOANRISK_ij* + β₆*EXPOSUREDER_ij*  
+ β₇*CREDITRISKDER_ij* + β₈*NONINTCHG_ij*  
+ β₉*BADNEWS_ij* + β₁₀*CONTRACT_ij* + β₁₁*SIZE_ij*  
+ β₁₂*LEVERAGE_ij* + β₁₃*T1LEV_ij* + β₁₄*DROE_ij*  
+ β₁₅*MKTHERF_ij* + Σ_N β_N *YEAR_N* + ε_ij.   (17C.2)

All variables are defined in Appendix 17B. To examine Hypothesis 3, it is expected that *ROA*, *AFSOFINV*, *LOANRISK*, *EXPOSUREDER*, *CREDITRISKDER*, and *NONINTCHG* are most consistent with the predictions in the case of accounting standards with only disclosure requirements.

In contrast to a static logit model, a dynamic logit model includes a lagged response variable and fixed/random effects specific to each BHC among the covariates and assumes the current response variable is conditionally independent of other prior lagged response variables. Additionally, the initial observation of the response variable must be known for a dynamic logit model with random effects (e.g., Heckman, 1981a, 1981b, 1981c; Wooldridge, 2000;