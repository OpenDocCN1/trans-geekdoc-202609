
With this chapter, we present the prospects of SiNR and GeNR as metal interconnects under various functionalization and doping scenarios. We have systematically analyzed the performance of various configurations by studying their structural, electronic, and transport properties. Here we will present the key performance parameter based on density functional theory (DFT) calculations and nonequilibrium Green's function (NEGF) formalism-based two-probe analysis that includes quantum resistance ($R_Q$), kinetic inductance ($L_Q$), and quantum capacitance ($C_Q$) for the considered structures.

## 4.4 EDGE FUNCTIONALIZED GENRS FOR INTERCONNECT APPLICATIONS [109]

In this section, we present the analysis of edge oxidation and hydrogenation on electronic and transport properties of zigzag and armchair germanane nanoribbons (ZGeNR and AGeNR); we have modeled all possible terminations of hydrogen and oxygen for AGeNR and ZGeNR. Figures 4.2 and 4.3 present all possible termination cases for AGeNR and ZGeNR, along with the appropriate names, as presented in the caption for each case.

Here, white and red spheres represent the germanium, hydrogen and oxygen atoms respectively. First, to compare structural stability of each configuration, we have calculated the binding energy ($E_b$) as per equation 4.1.

```
$E_b = E_{Total} - E_{Bare} - x_H - y_O \quad (4.1)
```

Here, $E_{Total}, E_{Bare}, E_H, E_O$, indicate the total energy of functionalized AGeNR/ZGeNR, bare AGeNR/ZGeNR, and the H and O- atoms, respectively. Also $x, y$ represent the total count of these atoms respectively. Further, based on the DFT calculations, we also calculated the respect bandgap and Fermi velocity ($v_f$) in each of the cases. These are tabulated in Table 4.1.

![](img/f43fc2d88fdf77da6ccf8abfe605d6a7_102_0.png)

**FIGURE 4.2** The relaxed configurations for functionalized AGeNR (ribbon with width $N_A=7$): (a) H-AGeNR-H, (b) O-H-AGeNR-H, (c) O-AGeNR-H, (d) O-H-AGeNR-O, (e) O-AGeNR-O.

**FIGURE 4.3** The relaxed configurations for functionalized ZGeNR (rib width $n=6$): (a) H-ZGeNR-H, O-ZGeNR-H, (c) O-ZGeNR-O.

TABLE 4.1 Calculated Values of Binding Energy, Bandgap, and Fermi Velocity for Armchair and Zig Germanane Nanoribbons with Considered Edge Terminations

| EDGE STATES | CONFIGURATIONS (AS PER TERMINATIONS) | BINDING ENERGY (EV) | BANDGAP (EV) | FERMI VELOCITY (MISEC) |
|---|---|---|---|---|
| n Armchair | H-ZGeNR | -12.03 | 0.36 (direct) | $6.61 \times 10^3$ |
| | O-ZGeNR-H | -18.97 | 0.18 (indirect) | $1.89 \times 10^4$ |
| | O-ZGeNR-O-H | -15.39 | Metallic | $2.47 \times 10^5$ |
| | O-ZGeNR-O-H | -18.67 | Metallic | $2.95 \times 10^5$ |
| | O-ZGeNR-O | -26.07 | 0.089 (indirect) | $9.14 \times 10^2$ |
| Zigzag | H-ZGeNR | -6.47 | Semimetallic | $9.19 \times 10^4$ |
| | O-ZGeNR-H | -10.08 | Metallic | $4.19 \times 10^5$ |
| | O-ZGeNR-O | -13.65 | Metallic | $5.21 \times 10^5$ |

The tabulated values show that $E_b$ O-termination strengthens the stability of the GeNR structures (both AgGeNR and Zig cases) also suggest that the higher the concentration of O-atom at the edge of GeNRs, the more stable is the overall system. As a result, both O-AgGeNR-O and O-ZGeNR-O are reported to have high values of $E_b$ (viz. -26.07 eV, -13.65 eV, respectively). The electronic properties were tuned for AgGeNR and ZigNR based on the calculated bandgap using E-k diagrams. The tabulated values suggest that the band gap typically reduces the concentration of elemental O-atom at the edges. This typical behavior, on one hand, can be attributed to the symmetry of edge terminating elements. But also, on the other hand, since the charge induced at the edges of AgNRs from O-atom is much larger than the H-atom, the band edges appear near the Fermi level, resulting in much wider bandgap (for O-AgGeNR case). Hence, we can infer that O-functionalized AgNRs are semiconducting or metallic depending upon the site of O-termination. For ZGeNR, the case is quite straightforward, where all the terminations are metallic. This implies that higher concentration of O-atoms at the edges of ZGeNR improves the metallicity of the structure.

To gauge their performances toward interconnect, a two-probe analysis has been performed to calculate transmission channel ($N_{ch}$), kinetic inductance ($L_K$), and quantum capacitance ($C_Q$) for considered structures. The quantum resistance can then be modeled by the equation [58]:

```
$R_Q = \frac{h}{G} \frac{1}{q^2 N_{ch}} \quad (4.2)$
```

Here, $R_Q$ is defined as the quantum resistance for small dimensions, $N_{ch}$ defines the number of transmission channels. Equation 4.2 highlights that quantum resistance varies inversely with the number of channels, $N_{ch}$. To comment on the value of $N_{ch}$ transmission eigenvalues are then calculate. Transmission represents the probability (or possibility) with which the carrier (electron wave) can pass through the central region; higher probability indicates less scattering and a more flow of carriers. Transmission around the Fermi level is then calculated, and the results are tabulated in Table 4.2. Tabulated values show that only O-H-AGeNR-H-H and O-H-AGeNR-O exhibit non-zero values of $N_{ch}$ ($N_{ch}=1$ and 2, respectively). Similar analysis can be performed for the zigzag couplers, the tabulated values suggest that $R_Q$ will be less than the value of $N_s$ and is the same for all three cases. However, a detailed analysis of the spectrum shows that due to symmetry (which is at the edges of case. O-ZGeNR-O), the channel tends to offer flow of carrier. It is mentioned here that symmetry is a strong function of bias voltage, and it collapses with the increase in bias voltage and inductance. Further, the dynamic performance is typically modeled through equations for $L_K, C_Q$ with respect to 1D nanoscale devices [58]:

```
$L_K = \frac{h}{4q^2 v_f} N_{ch} \quad (4.3)$
```

```
$C_Q = \frac{4q^2}{h} N_{ch} \quad (4.4)$
```

The calculated results are tabulated in Table 4.2. As it is implied from equations 4.3 and 4.4 that both $L_K$ and $C_Q$ depend inversely on the $v_f$ which means the greater the $v_f$ lesser the inductive coupling ($L_K$) and parasitic delay ($C_Q$) will be. Hence, it is essential to calculate the value for each configuration. The $v_f$ values for each case are calculated, and the values were presented in Table 4.1.

## TABLE 4.2 The Calculated Transmission Channel ($N_{ch}$), Kinetic Inductance ($L_K$), and Quantum Capacitance ($C_Q$) for Armchair and Zigzag Nanoribbons with Considered Edge Terminations

| EDGE STATES | CONFIGURATIONS (AS PER TERMINATIONS) | TRANSMISSION CHANNELS ($N_{ch}$) | KINETIC INDUCTANCE ($L_K$) (nHµm) | QUANTUM CAPACITANCE ($C_Q$) (pF/cm) |
|---|---|---|---|---|
| Armchair | H-AGeNR-H-O | NIL | NIL | NIL |
| | O-AGeNR-O | NIL | NIL | NIL |
| | O-H-AGeNR-H-H | 1 | 26.20 | 6.26 |
| | O-H-AGeNR-O-H | 2 | 109.67 | 10.48 |
| | O-AGeNR-O | NIL | NIL | NIL |
| Zigzag | H-ZGeNR-H O-ZGeNR-H | 3 | 23.47 | 50.45 |
| | O-ZGeNR-O | 3 | 5.15 | 11.06 |
| | | 3 | 4.14 | 8.89 |

In Table 4.1 indicate that with increase in concentration of the oxygen atom, all AGeNR configurations– except for O-AGENR-O–the magnitude of $v_i$ increases. Further, in the case of ZGeNR, the significance of the value of $v_i$ is even more, as the value of $N_{ch}$ is constant for each configuration of ZGeNR. The results indicate that with increase in concentration of O-atoms at the edges of ZGeNRs, the value of $v_i$ increases. This leads to significant improvement in the value of $L_c$ and $C_q$ for O-ZGeNR-H and O-ZGeNR-O cases compared to the pristine (H-ZGeNR-H). As mentioned previously, for the higher bias voltage, as $N_{ch}$ tends to reduce $L_c$ and $C_q$ may also ruin the performance of interconnect. These results are further matched with the already reported results for silicene [108].

Hence, through calculations of $R_q$, $L_c$ and $C_q$, it is revealed, that on the significantly higher values of $v_i$ and $N_{ch}$, the O-ZGeNR-O configuration offers minimum quantum resistance and delay can also be a potential candidate for future interconnect applications. Similar analysis can also be done for the silicene nanorib, and it SINRs, making them useful for interconnect applications.

## 4.5 SUBSTITUTIONALLY DOPED GENRS, SINRS FOR INTERCONNECT APPLICATIONS WITH COMMENTS ON RELIABILITY AND SECURITY [110]

Here we present the analysis of the impact of substrate induced impurities (as dopants) on GeNR. For proper comparative and exhaustive study, both AGeNR and ZGeNR have been investigated, with substational Au doping at different sites. We have presented all possible stable configuration, both doped and pristine, that is, undoped AGeNR/ZGeNR cases (for quick comparison), as shown in Figure 4.4.

![](img/f43fc2d88fdf77da6ccf8abfe605d6a7_105_0.png)

**FIGURE 4.4** The relaxed configurations for AGeNR (ribbon width $N_A$ = 7) and ZGeNR (ribbon width $N_Z$ = 6): (a) pristine AGeNR, (b) center-doped (C-AGeNR), (c) pristine ZGeNR, (d) center-doped (C-ZGeNR), (e) edge-doped (E-ZGeNR), and (f) near-edge doped (NE-ZGeNR). Here blue, white and yellow spheres represent the germanium, hydrogen, and gold atoms, respectively.
