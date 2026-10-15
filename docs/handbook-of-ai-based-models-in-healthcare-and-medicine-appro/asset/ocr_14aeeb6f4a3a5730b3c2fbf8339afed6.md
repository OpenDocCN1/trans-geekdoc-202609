![](bbox=[0.1, 0.13, 0.9, 0.46])

FIGURE 9.4 Pertinent attribute extraction using modified EfficientNet-B0 CNN.

*width: w = φ^θ*  (9.2)

*resolution: r = ζ^θ*  (9.3)

where θ is a compound parameter and δ, φ, and ζ are the scaling parameters of individual dimensions. A grid search technique is employed to select the optimum values of coefficients by validating the constraints δ φ² ζ² ≈ 2 and δ ≥ 1, φ ≥ 1, ζ ≥ 1. The layers of the model are outlined in Table 9.2.

# TABLE 9.2
Details of EfficientNet-B0 Model

| Stage | Operator | Resolution | No. of Channels | No. of Layers |
|---|---|---|---|---|
| 1 | Conv k3 | 224×224 | 32 | 1 |
| 2 | MIBConv1, k3 | 112×112 | 16 | 1 |
| 3 | MIBConv6, k3 | 112×112 | 24 | 2 |
| 4 | MIBConv6, k5 | 56×56 | 40 | 2 |
| 5 | MIBConv6, k3 | 28×28 | 80 | 3 |
| 6 | MIBConv6, k5 | 14×14 | 112 | 3 |
| 7 | MIBConv6, k5 | 14×14 | 192 | 4 |
| 8 | MIBConv6, k3 | 7×7 | 320 | 1 |
| 9 | Conv k1/pooling/FC | 7×7 | 1280 | 1 |

k3: 3×3, k5: 5×5, and k1: 1×1