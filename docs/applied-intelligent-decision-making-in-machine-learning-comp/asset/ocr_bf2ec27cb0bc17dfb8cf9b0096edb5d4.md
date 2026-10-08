# A Multi-Stage Hybrid Model for Odia Compound Character Recognition

![](bbox=[0.215, 0.095, 0.784, 0.203])

**FIGURE 3.2** An overview of the OCR process.

# 3.2.2 STRUCTURAL SIMILARITY

Human eyes focus on the structure of an image rather than luminance, contrast, and structure comparison. The SSIM [47] explains this by giving ranking value to image quality that is very similar to a subjective human evaluation standard. This is expressed mathematically in Equations 3.1 and 3.2. The overall presentation of the SSIM evaluation is shown in Figure 3.3.

```
$SSIM = [l(x,y)]^c [c(x,y)]^c [s(x,y)]^c \quad (3.1)$
```

where $s$ denotes structure, $c$ denotes contrast, and $l$ indicates local luminance. The expression correlates to the human visual system and by taking $a = \beta = \gamma = 1$ it can be simplified as

```
$SSIM = \frac{(2\mu_{max_y}\mu_y + C_1)(2\sigma_{xy} + C_2)}{(\mu_x^2 + \mu_y^2 + C_1)(\sigma_x^2 + \sigma_y^2 + C_2)} \quad (3.2)$
```

where $C_1 = (K_1 * L)^2, C_2 = (K_2 * L)^2$, and $L$ denotes the highest intensity level. The values of $K_1$ and $K_2$ are computed by philosophical study and are set to 0.01 and 0.03 respectively.

SSIM evaluates images on a structural domain rather than an error domain. Hence, for each template image, the score with respect to the target image becomes different. It ranges from 0 to 1 and a higher value indicates better matching. It has been observed from experiment that the recognition performance of all 211 classes is very high for

![](bbox=[0.203, 0.71, 0.796, 0.896])

**FIGURE 3.3** Schematic diagram of the SSIM system.