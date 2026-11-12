RE = \frac{\alpha}{\alpha + \Omega} (10.7)

This model is primarily made up of three components, and those components are noise filtering, noise detection, and classification. Our proposed model outperforms other state-of-art models and achieved 99.9% accuracy, 98.9% sensitivity, and 99.9% specificity (Figure 10.4, Table 10.4).

# Comparison chart of the proposed model with state-of-the-art technique

![](bbox=[0.13, 0.34, 0.86, 0.555])

FIGURE 10.4 Result analysis of the proposed model.

TABLE 10.4 Proposed Model versus State-of-the-Art Approach Comparison Table

| | Features | Classes | Dimension | Accuracy | Sensitivity | Specificity |
|---|---|---|---|---|---|---|
| Proposed model | DWT + RR + TEO + ELM | 18 | 17 | 99.9 | 98.9 | 99.9 |
| Zidelmal et al. | Frequency content + RR + QRS | 2 | 13 | 97.2 | 99 | - |
| Ebrahimzadeh et al. | HOS + timing interval + DCT | 5 | 24 | 95.18 | 95.61 | 98.8 |
| Rabee et al. | WT multiresolution | 14 | 251 | 99.2 | 96.2 | 100 |
| Alajlan et al. | HOS of second order | 2 | 604 | 94.9 | 92.1 | 95.1 |
| Ye et al. | WT + ICA + RR | 16 | 18 | 99.3 | 91.3 | - |
| Pathoumvanh et al. | DCT | 5 | 5 | 99.11 | 97.01 | 99.4 |