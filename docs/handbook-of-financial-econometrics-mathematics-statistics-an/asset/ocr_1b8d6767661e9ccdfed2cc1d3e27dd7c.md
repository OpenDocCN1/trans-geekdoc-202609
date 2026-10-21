There are three cases to consider:

(a) λ → 0 when σ₁² → 0, then in this case from equation (37.19), we know that
\hat{β} = (-S_XY S_YZ + S_XZ S_YY) / (S_XX S_YY - S_XY²). (37.20)

(b) λ → ∞ when σ₃² → 0, in this case from (37.20), we know that
\hat{β} = (-S_ZZ S_YY - S_YZ²) / (S_XZ S_YY + S_XY S_YZ). (37.21)

(c) When both σ₁² > 0 and σ₃² > 0, then
\hat{β} = [k₁ ± sqrt(k₁² + 4λ k₀²)] / (2λ k₀). (37.22)

When β is determined, γ can also be estimated. After both β and γ are estimated, then α can be estimated by
\hat{α} = ar{Z} - \hat{β} ar{X} - \hat{γ} ar{Y}. (37.23)

(Case ii) When Z, X, and Y are all observed with errors.
(a) both σ₁² and σ₂² are known.
We can obtain the two normal equations as follows:
S_XZ = β(S_XX - \hat{σ}₁²) + γ S_XY. (37.24)
S_YZ = β S_XZ + γ(S_YY - \hat{σ}₂²). (37.25)

Solving equations (37.24) and (37.25) by Cramer's rule we have
\hat{β} = [S_XZ S_YY - S_XY S_YZ - S_XZ \hat{σ}₂²] / [S_XX S_YY - \hat{σ}₁² S_YY - \hat{σ}₂² S_XX + \hat{σ}₁² \hat{σ}₂² - (S_XY)²]. (37.26)
\hat{γ} = [S_YZ S_XX - S_XZ S_YY - S_YZ \hat{σ}₁²] / [S_XX S_YY - \hat{σ}₁² S_YY - \hat{σ}₂² S_XX + \hat{σ}₁² \hat{σ}₂² - (S_XY)²].

(b) both \hat{σ}₂² = λ₁ \hat{σ}₁² and \hat{σ}₃² = λ₂ \hat{σ}₁² are known.
We can obtain β estimator as one of real roots of the following cubic equation
\hat{β}³ H₃ + \hat{β}² H₂ + \hat{β} H₁ + H₀ = 0. (37.27)
where