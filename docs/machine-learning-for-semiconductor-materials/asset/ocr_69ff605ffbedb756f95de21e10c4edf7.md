![](bbox=[0.17, 0.1, 0.83, 0.57])

# FIGURE 7.3 (Continued)

# 7.2.2 PRE-SETUP SPECIFICATIONS OF TCAD

The numerical investigation of the cylindrical BioFET is analyzed using the values listed in Table 7.1 on the ATLAS TCAD simulator [45]. To imitate real-time conditions, related models have to be incorporated during simulation: the Shockley-Read-Hall (SRH) model supports carrier generation and recombination, the concentration-dependent mobility (CONMOB) model relates the impurity profile to low field mobility at room temperature, and the parallel electric field-dependent mobility (FLDMOB) model accounts for field-dependent mobility [46]. To solve the nonlinear and complex differential equations, the Newton-Gummel method is employed, which integrates both decoupled and coupled iterations [46, 47].

# 7.2.3 COMPUTATIONAL METHODOLOGY

Biomolecules are defined by their specific charge densities (ρ) and dielectric constants (K_bio) [20, 26, 47]. For example, non-hybridized DNA carries a negative charge