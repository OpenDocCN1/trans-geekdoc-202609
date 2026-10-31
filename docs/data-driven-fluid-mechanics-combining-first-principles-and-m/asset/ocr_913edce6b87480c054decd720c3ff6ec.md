![](bbox=[0.15, 0.17, 0.88, 0.35])

Figure 19.2 Optimum classification lines for different initial perturbations, in terms of the kinetic energy and of the enstrophy. (a) Case A, N_c = 10 (b) Case B, N_c = 10. (c) Case B, N_c = 6. (d) Case B, N_c = 4. In all cases, 768 flows and n_keep = 5. The contour lines contain 50%, 70%, and 90% of the joint probability density functions (p.d.f.) of the diagnostic variables for: ————, most significant cases; — — —, least significant cases.

![](bbox=[0.25, 0.52, 0.85, 0.78])

Figure 19.3 Efficiency of support vector machine classifiers. Unit efficiency is perfect classification, and 0.5 is random choice. Rows are the cases in Table 19.1, and columns are the different combinations of diagnostic variables.

enstrophy is consistent with the spectrum in Figure 19.1(c), which shows that the cell size when N_c = 10 preserves details of the spectrum of the order of the vortex size, but it is little surprising that small cells work so well for the kinetic energy, whose spectrum peaks at the scale of the box, suggesting that, at least at this low Reynolds number, the causality of the kinetic energy remains concentrated at the scale of individual vortex pairs. In fact, the effectiveness of the enstrophy and of the energy behave differently with the cell size. While the mean effectiveness of ω_c^2 as a diagnostic variable in case A decays from 1 to 0.72 as N_c = 10 → 4, that of q_c^2 in case B only decays from 1 to 0.89 in the same range.

The difference among perturbation methods is best displayed by constructing for each case a conditional “template” for the immediate neighborhood of the significant