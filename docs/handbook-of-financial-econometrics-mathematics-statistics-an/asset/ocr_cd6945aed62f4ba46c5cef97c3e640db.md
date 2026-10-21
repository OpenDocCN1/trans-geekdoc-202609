The reasons are, first, there is no imposed restriction to force the same γ to appear in both equations and, second, ΔP_t^+ and ΔP_t^- are not, strictly speaking, linear functions of X_{D,t} and X_{S,t}.

# 99.4.3 Maximum likelihood estimator

Quandt (1988) employs an appropriately formulated full-information maximum likelihood technique. He suggests one can use the log likelihood function represented as equation (99.16) to find the ML estimator

L = T log |α₂ - α₁ + 1/γ| - T log 2π - T/2 log |Ω| - 1/2 Σ_t u'_t Ω^{-1} u_t,  (99.16)

where

u'_t = ( Q_t - α₁ P_t - β₁' X_{D,t} + 1/γ ΔP_t^+, Q_t - α₂ P_t - β₂' X_{S,t} + 1/γ ΔP_t^- ).

On the other hand, Amemiya (1974) shows the following iterative method of obtaining the maximum likelihood estimators. He suggests the maximum likelihood estimators can be obtained by solving the following equations simultaneously:

α_{1,MLE} = α_{1,LS}    β_{1,MLE} = β_{1,LS},  (99.17a)
α_{2,MLE} = α_{2,LS}    β_{2,MLE} = β_{2,LS},  (99.17b)
σ_μ² = 1/T [ Σ_A (Q_t - α₁ P_t - β₁' X_{D,t})² + Σ_B (Q_t + 1/γ ΔP_t - α₁ P_t - β₁' X_{D,t})² ],  (99.17c)
σ_v² = 1/T [ Σ_B (Q_t - α₂ P_t - β₂' X_{S,t})² + Σ_A (Q_t - 1/γ ΔP_t - α₂ P_t - β₂' X_{S,t})² ],  (99.17d)
Tγ + 1/σ_v² Σ_A ( Q_t - 1/γ ΔP_t - α₂ P_t - β₂' X_{S,t}) ΔP_t - 1/σ_μ² Σ_B ( Q_t + 1/γ ΔP_t - α₁ P_t - β₁' X_{D,t}) ΔP_t = 0.  (99.17e)

That is, the ML estimators of α and β are the same as LS estimators given γ applied to equation (99.15). The equations for σ_μ² and σ_v² (equations (99.17c) and (99.17d)) are the residual sums of squares of equations (99.15a) and (99.15b), given γ, divided by T as for the usual ML estimators. Equation (99.17d) is a quadratic function in γ. Following