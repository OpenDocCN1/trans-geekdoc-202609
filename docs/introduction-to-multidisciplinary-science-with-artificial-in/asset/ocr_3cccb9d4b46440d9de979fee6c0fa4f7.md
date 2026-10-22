# Box 2.2: Radiation Pressure

EM waves carry momentum despite being massless. If an incident EM wave is absorbed by a body, or it reflects from a body, the EM wave will transfer momentum to the body. The longer the EM wave is incident on the body, the more momentum is transferred. This longer dependence can be ignored by working with the pressure, known as radiation pressure, that is exerted on the surface of the body by the incident EM wave. Radiation pressure is central to the study of stars' interiors in which EM radiation is present along with a mixture of ions, electrons, and photons. The ions and electrons can be treated as an ideal gas and quantum effects can be neglected. Total pressure is P = P_gas + P_rad, where P_gas = P_ion + P_elect, P_ion is the pressure of the ions, P_elect is the electron pressure, and P_rad is the radiation pressure. Gas pressure is most important in low mass stars and radiation pressure is most important in high mass stars. In the first section of this chapter, we determined P_gas. We used the Maxwell-Boltzmann distribution function of ideal gases to obtain the relationship between P_gas, temperature, and volume. Our objective here is to determine P_rad.

```
n(f)df = 4π / c * 2f² df / [exp(hf/k_B T)-1]
```

to determine P_rad from the integral equation in (2.14). With p = hf/c and n_f(f) = n_p(p)dp, it follows that

```
P_rad = 1/3 ∫ n_f(h) h df = 4π/(3c) ∫ 2h f³/c² / [exp(hf/kT)-1] df = 4π k_B⁴ T⁴/(3 c² h³) ∫ x³ / [exp(x)-1] dx = 1/3 a T⁴
```

where a = 4σ_SB/c ≈ 8π⁵ k_B⁴/(15³ h³) is the radiation density constant, x = hf/(k_B T) and df = (k_B T / h) dx . Note that gas pressure is equal radiation to pressure when T³ = (3R)/(aμ) : i.e.,

```
P_gas = P_rad ⇔ R/μ T = 1/3 a T⁴ ⇒ T³ = 3R / (a μ ρ)
```

Note also that, at the center of the sun, P_gas / P_rad ≈ 7×10^{-4}—that is, radiation pressure is not important in the center of the sun. We used ρ = 150 g/cm³, T = 1.6×10^7 K, and R = 8.31 J/K/mol. In order to assess the importance of radiation pressure. Hence radiation pressure appears to be negligible at an average point in the sun. Without recourse to our knowledge of how energy is generated in the sun, a value for its internal temperature has been derived and it has been deduced that the material is essentially an ideal gas with negligible radiation pressure. Clearly radiation pressure becomes increasingly significant as stellar mass increases.