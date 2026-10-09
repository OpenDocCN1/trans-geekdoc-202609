![](bbox=[0.18, 0.12, 0.79, 0.44])

**Figure 3.** The dynamic range compression curve.

We take the reciprocal of the global tone mapping function and histogram equalization results at the same time and build a functional relationship between the global tone mapping function and histogram equalization based on the least squares criterion:

$$F(\alpha) = \sum_{i=1}^{H} \sum_{j=1}^{W} \left[ \frac{\alpha + I_{ij}}{I_{ij}} - \frac{1}{f(I_{ij})} \right]^2 \tag{10}$$

where $f(I_{ij})$ is the calculation result of histogram equalization. According to the least squares criterion, the derivative of $\alpha$ is 0; this shows that Equation (11) holds, and Equation (12) is obtained:

$$\frac{\partial F(\alpha)}{\partial \alpha} = 0 \tag{11}$$

$$\sum_{i=1}^{H} \sum_{j=1}^{W} \left[ \frac{(\alpha + I_{ij}) f(I_{ij}) - I_{ij}}{I_{ij} f(I_{ij})} \right] = 0 \tag{12}$$

By solving Equation (12), the parameter $\alpha$ of the global tone mapping function can be obtained:

$$\alpha = \sum_{i=1}^{H} \sum_{j=1}^{W} \frac{I_{ij} [1 - f(I_{ij})]}{f(I_{ij})} \tag{13}$$

According to the obtained parameters, the global tone mapping functions corresponding to different images can thus be obtained, and the dynamic range compression of different images can be achieved.

# 3.4. LDR Image Generation

# 3.4.1. Detail Layer Estimation

The maximum value between each pixel RGB channel is set as the luminance component of the image, as shown in Equation (14).

$$L(x,y) = \max\{R(x,y), G(x,y), B(x,y)\} \tag{14}$$