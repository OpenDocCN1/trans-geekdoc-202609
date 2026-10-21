![](bbox=[0.2, 0.09, 0.82, 0.6])

FIGURE 14.12 Visual results of DPIR and DUIR on the three testing images. The blur kernel is visualized in the upper right corner of the LR image. (a) LR image; (b) DPIR; (c) DUIR.

DPIR. From Figs. 14.13 and 14.14(a), one can see that α is positively correlated with σ and varies with s. This actually accords with the definition of α_k. From Figs. 14.13 and 14.14(b), one can see that β has a decreasing tendency with the number of iterations and increases with scale factor and noise level. This implies that the noise level of HR estimation is gradually reduced across iterations and complex degradation requires a large β_k to tackle the illposedness.

# 14.5.2.3 Intermediate results

Figs. 14.15 and 14.16 provide the visual results of x_k and z_k at different iterations of DPIR and DUIR on the Starfish image from Fig. 14.12. One can observe from Fig. 14.15 that, al-