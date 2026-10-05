# Melanoma detection by hybrid attention DCNN-BiLSTM architecture 383

extracting information from the connections between grey imaged pixels. It is generated based on the pixel distance (D), pixel angle (0°, 45°, 90°, and 135°), and the maximum number of transformable grey tone levels (256). First, the image is rescaled based on the number of greyscale levels in the GLCM method. With the selected grey level in the newly created GLCM matrix, the rescaled image provides the total number of nearby pixels at the chosen angle and distance.

This research proposes a novel feature extraction technique for one-dimensional data. At first, the vibration signals were converted into integers between 0 and 255. Using freshly generated data, a co-occurrence matrix is generated. The proposed approach lacks an angle parameter despite a distance parameter. The signal analysis uses statistics derived from the co-occurrence matrix. These attributes can be computed using the following formulas:

```
Angular second moment = $\sum_{x=1}^{S}\sum_{y=1}^{S} \frac{I(x,y)^2}{J}$ (18.09)
```

```
Contrast = $\sum_{x=1}^{S-1}\sum_{y=1}^{S} x^2 \left[ \frac{I(x,y)}{J} \right]^2 \right]$ (18.10)
```

```
Correlation = $\sum_{x=1}^{S}\sum_{y=1}^{S} [xyI(x,y)/J] - \sigma_p\sigma_q / \eta_p\eta_q$ (18.11)
```

```
Variance = $\sum_{x=1}^{S}\sum_{y=1}^{S}(x-\sigma)^2 I(x,y)$ (18.12)
```

```
Inverse different moment = $\sum_{x=1}^{S}\sum_{y=1}^{S} \frac{I(x,y)}{1+(x+y)^2}$ (18.13)
```

```
Sum average = $\sum_{x=2}^{2S} Ix_{p+q}(x)$ (18.14)
```

```
Sum variance = $\sum_{x=2}^{2S}(x-\text{Sum entropy})^2 I_{p+q}(x)$ (18.15)
```

```
Sum entropy = $-\sum_{x=2}^{2S} I_{p+q}(x) \log\{I_{p+q}(x)\}$ (18.16)
```