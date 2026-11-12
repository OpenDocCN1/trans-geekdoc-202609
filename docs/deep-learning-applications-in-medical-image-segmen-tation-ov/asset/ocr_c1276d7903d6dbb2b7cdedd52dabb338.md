Thus, the model M1 is ER times likely to be the optimal growth model compared to M2. Likewise, the Bayesian weights and corresponding ER_BIC are also computed as given in equation 4.16 and 4.17:

```
w_{BIC_k} = \frac{e^{-0.5\Delta BIC_k}}{\sum_{m=1}^{12} e^{-0.5\Delta BIC_m}}, k=1, 2 ... 12 \quad (4.16)
ER_{BIC} = \frac{w_{BIC_{M1}}}{w_{BIC_{M2}}} \quad (4.17)
```

Therefore, the ER is an essential metric to assess the relative likelihood of a model with respect to other models. This enables better decision-making in model selection.

# 4.3.4 Study of Hemispheric Differences in Myelination

The growth model fitting is expanded to evaluate potential hemispheric differences in myelination. There are several changes in the pediatric brain including developmental and maturational aspects, such as increase in brain size and cortical folding patterns. In this context, it is interesting to investigate the differences in myelination progress between the right and left hemispheres of the developing brain.

Primarily, we segment the hemispheres based on the inter-hemispheric fissure (IHF). The IHF is a deep groove that separates the right and left hemispheres. However, the IHF is not always oriented vertically to the image axis. There is a certain degree of rotational and translational offset. To identify the IHF, we propose a novel approach based on a pseudo midline (PML). For this, a horizontal projection of the extracted brain image (obtained in Section 3.2) is derived and its minimum is computed. The PML is designated as an imaginary line passing through this minimum point. This line is then rotated in small angular increments of 0.1° over the entire image. The rotated PML with zero or near-zero brain crossovers is considered the line of IHF. Using this IHF, the brain is split into its right and left hemispheres along with the myelinated regions, as shown in Figure 4.2.

![](bbox=[0.112, 0.722, 0.888, 0.842])

Figure 4.2 Inter-hemispheric separation: (a) extracted brain image, (b) pseudo midline superimposed on the brain, (c) inter-hemispheric fissure superimposed on the brain, (d) separated hemispheres, and (e) demarcated MWM.