# 6.5.1. Microscopic Interpretation of Electrical Conductivity

Let us write the motion equation, in (6.79), for electrons and ions separately:

```
m_e [∂/∂t + v_e · ∇] (n_e v_e) = -∇p_e - n_e e (E + v_e × B) + m_e n_e ν_ei (v_i - v_e), (6.252)
```

```
m_i [∂/∂t + v_i · ∇] (n_i v_i) = -∇p_i + n_i e (E + v_i × B) - m_e n_i ν_ei (v_i - v_e), (6.253)
```

where subscript e is used for electrons and i for ions. We used the fact that ρ_e = m_e n_e, ρ_i = m_i n_i, ρ_e,e = -n_e e, and ρ_e,i = Z_i n_i e, and again assumed that Z_i = 1 (i.e., the ions are protons). The last term in (6.252) describes the rate of momentum transfer during collisions between ions and electrons. It represents the mean momentum transferred between ions and electrons and ν_ei is electron-ion collision frequency. It is equal, with opposite signs, to the last term in (6.253) because momentum conservation requires the two terms to be of opposite signs. We assume no gravity. We did not include the effects of ion-to-ion and electron-to-electron collisions in (6.252) and (6.253) because the like particle collisions do not change the total momentum (which is averaged over all particles of that species) whereas collisions between unlike particles do exchange momentum between the species.

Let us now assume that the plasma is at rest or in uniform motion (particle acceleration is zero) and the pressure and magnetic field are zero. Equation of motion in (6.252) reduces to

```
0 = -n_e E - m_e n_e ν_ei v_e  ⇔  J = σ E , (6.254)
```

where J = -n_e e v_e = ρ_e,e v_e  and  σ = e² n_e / (m_e ν_ei)  (6.255)

and σ is the electric conductivity. This formula for electric conductivity allows us to link the macroscopic quantity, σ, defined in Chapter 3, to the microscopic scale. By increasing the electron particle density, n_e, in (6.255), we increase plasma conductivity, and by increasing the ion-electron collision frequency, ν_ei, we increase plasma resistivity. It is clear that the law, J = σ E, does not work when B ≠ 0, v is not a constant vector, and/or p is not constant.

Let us turn to the derivation of generalized Ohm's law: n_i = n_e = n. By multiplying equation (6.252) by -e/m_e and adding it to equation (6.253) multiplied by e/m_i, neglecting the inertia terms, which are (v_e · ∇)v_e and (v_i · ∇)v_i, we obtain

```
∂/∂t [e n (v_i - v_e)] = - (e/m_i) ∇p_i + (e/m_e) ∇p_e + e² n (1/m_e + 1/m_i) E + e² [ (v_e × B)/m_e + (v_i × B)/m_i ] - e n ν_ei [ (v_i - v_e) - (m_e / m_i) (v_i - v_e) ] . (6.256)
```