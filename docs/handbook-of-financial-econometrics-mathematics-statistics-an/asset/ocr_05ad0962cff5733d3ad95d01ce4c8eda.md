# An ODE Approach for the Expected Discounted Penalty

Consider the rational function

H(x) = \sum_{j=1}^{m+1} R_j \prod_{k=1}^{m+1} \frac{\eta_j + \rho_k}{x + \rho_k} \prod_{i=1,i \neq h}^{m+1} \frac{x - \eta_i}{\eta_j - \eta_i}. (41.53)

Note that, for each summand in (41.53), the numerator is a polynomial of degree m, and the denominator is a polynomial of degree m + 1. By the principle of partial fraction decomposition, there exist constants D_h, 1 ≤ h ≤ m + 1, such that

\sum_{j=1}^{m+1} R_j \prod_{k=1}^{m+1} \frac{\eta_j + \rho_k}{x + \rho_k} \prod_{i=1,i \neq h}^{m+1} \frac{x - \eta_i}{\eta_j - \eta_i} = H(x) = \prod_{i=1}^{m+1} \frac{D_i \rho_i}{\rho_i + x}. (41.54)

By multiplying both sides of (41.54) by x + ρ_h and then setting x = -ρ_h, we get that D_h is given by the right-hand side of (41.50). On the other hand, since \prod_{i=1,i \neq j}^{m+1} \frac{\eta_j - \eta_i}{\eta_j - \eta_i} = 0 for all h ≠ j,

\sum_{i=1}^{m+1} \frac{D_i \rho_i}{\rho_i + \eta_h} = H(\eta_h) = R_h \prod_{k=1}^{m+1} \frac{\eta_h + \rho_k}{\eta_h + \rho_k} \prod_{i=1,i \neq h}^{m+1} \frac{\eta_h - \eta_i}{\eta_h - \eta_i} = R_h , 1 ≤ h ≤ m+1.

That is, D is a solution to (41.52). Since the solution to (41.52) is unique and (41.48) and (41.52) are equivalent, Q = D is the unique solution of (41.48). By Proposition 41.4.2, we have Φ ≡ \sum_{i=1}^S Q_i e^{\rho_i x} on R_+ .

Remark 41.4.5: We consider some special g.

(1) Assume that g ≡ 1_{(-∞,y)} for some y ≤ 0. Then R_j = e^{-η_j y} for 1 ≤ j ≤ m and R_{m+1} = 0. Hence,

E_x[e^{-r τ}1_{x<y}] = \sum_{h=1}^{m+1} \left[ \frac{-1}{\rho_h \prod_{l=1,l \neq h}^{m+1} (-\rho_h + \rho_l)} \times \sum_{j=1}^{m+1} e^{\eta_j y} \left( \prod_{k=1}^{m+1} (\eta_j + \rho_k) \prod_{i=1,i \neq h}^{m+1} \frac{-\rho_h - \eta_i}{\eta_j - \eta_i} \right) \right] e^{\rho_h x}.

(2) Assume that g ≡ 1_{[0]}. Then R_j = 1 for all j. Hence,

E[e^{-r τ}1_{[0]}(X_τ)] = \sum_{h=1}^{m+1} \left[ \frac{1}{\rho_h \prod_{l=1,l \neq h}^{m+1} (-\rho_h + \rho_l)} \times \sum_{j=1}^{m+1} \left( \prod_{k=1}^{m+1} (\eta_j + \rho_k) \prod_{i=1,i \neq h}^{m+1} \frac{-\rho_h - \eta_i}{\eta_j - \eta_i} \right) \right] e^{\rho_h x}. (Cf. [20])