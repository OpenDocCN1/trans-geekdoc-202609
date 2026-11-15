tr(\boldsymbol{M}_{22:1}^{-1})\left\{\mathcal{H}_{p_2+2}(\lambda^2, 0) - p_2^{-1}c(2 - (p_2 - 2)^{-1})c\right\}. (9.5.12)

Now, c p_2^{-1}(2-c/(p_2-2)) attains a maximum (over c \in (0, 2(p_2-2)) at c = p_2-2 while by Eq. (9.5.6), c \leq 2\lambda^{-1} - 4. Hence, defining q as in Eq. (9.5.9), we note that Eq. (9.5.12) is bounded from below by

tr(\boldsymbol{M}_{22:1}^{-1})\left\{\mathcal{H}_{p_2+2}(\lambda^2, 0) - q \frac{2(p_2-2)-q}{p_2(p_2-2)}\right\}. (9.5.13)

Thus, ensuring positiveness of Eq. (9.5.12) implies that \hat{\rho}_{1n}^{SS} fails to dominate \hat{\rho}_{1n}^{PTR}(\lambda).

# ## 9.6 Summary

In this chapter, we proposed shrinkage and penalty R-estimators for the vector parameter of the auto-regression model of order p. Given the detailed discussions and their usages for the R-estimators in previous chapters, we constructed this chapter concisely, where we only gave the form of the R-estimators along with their asymptotic distributional L_2-risk, through some theorems. The results of this chapter will be useful for time-series regression in the context of robust rank regression.

To end this chapter, in what follows, we provide the ADRE expressions. We first note that the ADL_2-risk(\hat{\rho}_n^{UR}) is given by Eq. (9.4.6),

ADL_2-risk(\hat{\rho}_n^{UR}) = \eta^2 \left( \text{tr}(\Sigma_{11:2}^{-1}) + \text{tr}(\Sigma_{22:1}^{-1}) \right). (9.6.1)

Then, we have

ADRE(\hat{\rho}_{1n}^{PTSSR}(\lambda) : \hat{\rho}_{1n}^{UR}) = \left( 1 + \frac{\Delta^2 \text{Ch}_{\max}(\boldsymbol{M}_{22:1}^{-1})}{\text{tr}(\Sigma_{11:2}^{-1})} \right)^{-1} (9.6.2)

ADRE(\hat{\rho}_{1n}^{LassOR}(\lambda) : \hat{\rho}_{1n}^{UR}) = \left( 1 + \frac{\Delta^2 \text{Ch}_{\max}(\boldsymbol{M}_{22:1}^{-1})}{\text{tr}(\Sigma_{11:2}^{-1})} \right)^{-1} (9.6.3)

ADRE(\hat{\rho}_{1n}^{RR} : \hat{\rho}_{1n}^{UR}) = \left( \frac{\text{tr}(\Sigma_{11:2}^{-1})}{\text{tr}(\Sigma_{11}^{-1})} \right) \left( 1 + \frac{\Delta^2 \text{Ch}_{\max}(\boldsymbol{M}_{22:1}^{-1})}{\text{tr}(\Sigma_{11}^{-1})} \right)^{-1} (9.6.4)

ADRE(\hat{\rho}_{1n}^{PTR}(\lambda) : \hat{\rho}_n^{UR}) = \left[ 1 + \frac{\text{tr}(\boldsymbol{M}_{22:1}^{-1})}{\text{tr}(\Sigma_{11:2}^{-1})} (1 - \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2)) + \frac{\text{tr}(\Sigma_{11}^{-1})}{\text{tr}(\Sigma_{11:2}^{-1})} \mathcal{H}_{p_2+2}(\lambda^2, \Delta^2) \right]