| Parameters | CGAA FET | MC-DD-Ge/Si-INW-FET |
|---|---|---|
| Channel doping | 1 × 10¹⁶/cm³ | 1 × 10¹⁶/cm³ |
| Silicon thickness (t_si) | 10 nm | 10 nm |
| Channel length (L_ch) | 30 nm | 30 nm |
| Oxide thickness (t_ox) | 2 nm | 2 nm |
| Work function (φ_m) | 4.88 eV | 4.6 eV |
| Gate thickness (t_g) | 2 nm | 2 nm |
| Filler thickness (t_f) | 5 nm | 5 nm |

to prioritize a lower r₂/r₁ ratio while ensuring moderate values for both r₁ and r₂ to ensure an adequate number of mobile charges in the channel. In the proposed macaroni structure (MC-DD-Ge/Si-INW-FET), the r₂/r₁ ratio is set at 5 nm, which is moderately low and is expected to help in minimizing fluctuations in the threshold voltage. Table 10.1 provides a synopsis of the parameters comparing conventional gate-all-around FET (CGAA FET) and MC-DD-Ge/Si-INW-FET. The drawback of this configuration lies in its expensive and intricate fabrication process. Challenges include achieving and sustaining precise temperatures for vacuum dielectrics, difficulty in accurate doping concentrations, and the high cost of required fabrication equipment.

Numerical simulations are conducted using an ATLAS 3D device simulator [20], incorporating various models such as the SRH, CONMOB, FLDMOB, hot electron injection (HEI), Concannon nonlocal gate current (N. CONCAN), bandgap narrowing (BBT.STD) [21], and drift diffusion models. The syntax of the band-to-band tunneling (BTBT) BBT.STD model is specifically employed to accurately analyze and implement our proposed DDM-GAA FET device, focusing on gate-induced drain leakage (GIDL) characteristics similar to fabricated devices [22]. Detailed descriptions of these models can be found in Table 10.2. Carrier transport problems are solved numerically using the Newton-Gummel technique [23].

# 10.3 RESULT AND DISCUSSION

# 10.3.1 MC-DD-Ge/Si-INW-FET for Analog Applications

Figure 10.2 illustrates the variations in band energy across the channel length for both MC-DD-Ge/Si-INW-FET and CGAA FET under different drain voltages (V_DS = 0.0 V and 1.0 V, respectively). In the case of MC-DD-Ge/Si-INW-FET, there is a noticeable decrease in band energy toward the drain end as depicted in the graph. This reduction in band energy is influenced by two factors: the filler acting as a dielectric and the high-k dielectric located at the drain side, which significantly reduces electron tunneling from the valence band to the conduction band. Consequently, BTBT, involving electron transition from the valence band to the conduction