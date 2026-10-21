Kraus, A. and Litzenberger, R. (1975). Market Equilibrium in a Multiperiod State Preference Model with Logarithmic Utility. Journal of Finance, 30, 1213-1227.
Lintner, J. (1983). The Lognormality of securities returns, portfolio selection and market equilibrium. Unpublished manuscript, Harvard University.
Loève, M. (1963). Probability Theory, 3rd edn. Princeton, NJ: Van Nostrand.
Merton, R. (1971). Optimum Consumption and Portfolio Rules in a Continuous Time Model. Journal of Economic Theory, 3, 373-413.
Rothschild, M. and Stiglitz, J. (1971). Increasing Risk II: Its Economic Consequences. Journal of Economic Theory, 3, 66-84.
Royden, H. L. (1988). Real Analysis, 3rd Ed. New York: Macmillan.
Rubinstein, M. L. (1977). The strong case for the generalized logarithmic utility models as the premier model of financial markets. Financial Decision Making under Uncertainty. In H. Levy and M. Sarnat, eds., New York: Academic Press.
Samuelson, P. (1969). Lifetime Portfolio Selection by Dynamic Stochastics Programming. Review of Economics and Statistics, 51, 239-246.

# Appendix 65A

Consider the approximately maximum likelihood estimator of β, β̂_ML given by (65.2).

# Result 1.

E(β̂_ML) = [(T - 1)β - 1]/(T - 3)

Proof:

E(β̂_ML) = E( Ȳ / S² + 1/2 ) = 1/2 + E(Ȳ) E(1/S²) = 1/2 + μ (T - 1)/(T - 3) 1/σ²
= [(T - 1)β - 1]/(T - 3).

# Result 2.

Var(β̂_ML) = (T - 1)² / [(T - 3)(T - 5)σ⁴] ( σ²/T + 2μ²/(T - 3) )

Proof:

Var(β̂_ML) = Var( Ȳ/S² + 1/2 ) = E( Ȳ/S² )² - [ E( Ȳ/S² ) ]²
= E( Ȳ/S² )² - (T - 1) μ² / [(T - 3) σ⁴]
and
E( Ȳ/S² )² = E(Ȳ²) E(1/S⁴) = (σ²/T + μ²) (T - 1)² / [(T - 3)(T - 5)] 1/σ⁴.
Therefore,
Var(β̂_ML) = (T - 1)² / [(T - 3)(T - 5)σ⁴] ( σ²/T + 2μ²/(T - 3) )
and the asymptotic variance follows by letting T → ∞.