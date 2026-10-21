# Appendix 55A: Descriptive Statistics on UK Sell-Side Analyst Recommendations

# Appendix 55B: Stata Codes for the Time-Series Bootstrapping Simulations

# Appendix 55B.1: The Stata .ado file, bs_resid.ado, for Procedure I: Resampling the residuals independently with fixed common risk factors — Kosowski et al. (2006) bootstrapping simulations

# Appendix 55B.2: The Stata .ado file, bs_resid.ado, for Procedure II: Jointly resampling both the residuals and common risk factors — Fama and French (2010) bootstrapping simulations

# Appendix 55B.3: The Stata do file, “bs_resid.do”, for bootstrapping simulation

# Appendix 55C: Summary Statistics and Correlations for the Daily Risk Factor Returns

# Abstract

Data mining is quite common in econometric modeling when a given dataset is applied multiple times for the purpose of inference; it in turn could bias inference. Given the existence of data mining, it is likely that any reported investment performance is simply due to random chance (luck). This study develops a time-series bootstrapping simulation method to distinguish skill from luck in the investment process. Empirically, we find little evidence showing that investment strategies based on UK analyst recommendation revisions can generate statistically significant abnormal returns. Our rolling window-based bootstrapping simulations confirm that the reported insignificant portfolio performance is due to sell-side analysts’ lack of skill in making valuable stock recommendations, rather than their bad luck, irrespective of whether they work for more prestigious brokerage houses.

# Keywords

Data mining • Time-series bootstrapping simulations • Sell-side analysts • Analyst recommendations.

# 55.1 Introduction

An interesting question of financial economics is whether the reported investment performance is as a result of random chance (luck), or data mining, which is considered to be a dangerous econometric practice that should be avoided (see, White, 2000; Barber et al., 2001). Despite the nonexistence of a solid intrinsic relationship, extensive tests on a given set of sample frequently