
two transmission values, which are further refined to give a dehazed output [20]. Rayleigh scattering techniques, in which atmospheric value is estimated by computing the minimum, average, and maximum pixel value of each R, G, and B channel, have been proposed [21]. Initial transmission is estimated by the Rayleigh scattering model while refined transmission is obtained by a fast guided filter. For nighttime haze, Taylor series expansion is applied to calculate pointwise transmission value, while Retinex theory determines atmospheric value [22]. Bounded channel prior techniques give an accurate transmission map, and different transmission values of many small patches of input image are estimated accurately.

Guided filter and weighted interpolation are further applied to rough transmission to refine details and edges [23].

### 6.3.3 Color Attenuation Prior

Color attenuation prior (CAP) assumes that the difference between brightness and saturation of an image affects the haze density. Also, haze density is directly proportional to scene depth, which can be explained by [24]:

(x) ∝ d(x) ∝ v(x) − s(x) (6.5)

(x) represents haze density, d(x) represents scene depth, v(x) represents brightness of scene, s(x) represents saturation. The linear relationship among scene depth, brightness, and saturation is given by:

d(x) = θ₀ + θ₁ v(x) + θ₂ s(x) (6.6)

where θ₀, θ₁, and θ₂ are unknown linear coefficients; the basic color attenuation prior step is as shown in Figure 6.2.

![](img/0c56ac060cc6089fd33efc0e4aeb71a8_109_0.png)

Figure 6.2 Color attenuation prior flowchart.

For improved color attenuation techniques useful for both synthetic and real scenes, quad decomposition method is applied for air light estimation. The use of a low pass filter is a common technique to remove background noise from an image. In addition to using a low pass filter, adaptive linear weighting can also be used to further remove background noise from an image [25].

Estimated air light using haze line, which assumes that in RGB space hazy pixel values can be modeled as lines, intersects at the air light [26]. Finally, constant scattering coefficient values are replaced by dynamic scattering coefficient values. Color channel transfer is a technique used in image dehazing to recover the colors and contrast of a hazy image. It is based on the assumption that at least one color channel, usually green or blue, has a relatively low attenuation due to the haze. To compensate for chromatic loss, these techniques applied color transfer strategy to lower attenuation color bands [27]. Proposed color shifting awareness techniques calibrate and correct the color of input scene [28]. Finally, gamma correction is applied to remove haze. Varicolored techniques use two modules, i.e., haze color correction and visibility improvement, to restore the color balance of hazy scenes to give clear outputs [29].

### 6.3.4 Fusion Techniques

This technique takes two or more inputs from different adapted versions of dehazing techniques and yields better output [30]. The fusion of contrast enhancement and white balancing is implemented based on per-pixel fashion [31]. Lastly, to reduce artifacts, laplacian pyramid representation is applied. Optimized, fast, single dehazing method includes fusion of different techniques. To determine air light value, dark channel prior is performed followed by white balancing to retain the actual color. Finally, contrast stretching is performed to enhance contrast of output [32]. The fusion technique proposed is based on encoder and decoder architecture. It involves fusion of contrast enhancement, white balancing and, lastly, gamma correction. The convolutional neural network involves fusion of two generative adversarial networks (GAN) [33]. The outdoor unpaired real dataset is trained by cycleGAN, while cGAN preserves the detail of the scene. These techniques work well for both real and synthetic datasets [34].

### 6.3.5 Deep Learning

To remove the limitations of existing dehazing techniques such as assumption-based or complex fusion method, CNN was proposed as shown in Figure 6.3 [35]. Multi-scale CNN is based on training of datasets; it consists of two networks. Coarse networks determine rough transmission value, while fine scales further refine transmission value [36]. The cascaded convolutional neural network (CNN) approach utilizes two subnetworks that work together to determine both the transmission map and the global atmospheric light. This technique removes noise and the scene artifact, as it works on training of datasets [37]. Ranking CNN can reproduce statistical and structural features simultaneously. The regression model is further trained based on learned features to predict scene depth effectively [38].

Image sensing networks measure air quality index based on haze relevant feature and three-dimensional CNN [39]. Multi-feature bilinear techniques determine transmittance value, which include different steps. Firstly, feature is extracted through trained dataset. Secondly, non-linear mapping is done. Lastly, haze-free images are restored without noise and abrupt edges [40]. Dual network has two components, i.e., dehazing and denoising networks. Dehazing network determines air light using AL-Net, while generating the transmission map using TM-Net. Finally, noise from textural layer is removed by denoising network [41]. CycleGAN uses unsupervised training method, which produces haze mask. The use of haze mask and hazy version result in clean output by reformulated scattering model [42]. Atmospheric value and transmission map are determined at the same time [43]. This technique reduces the computational time but does not work well for dense haze. CNN uses a patch map selection network, which is determined based on the selected patch size for each pixel. This technique visually and qualitatively showed better results [44]. A knowledge transfer technique consists of a teacher network, which utilizes clear images for training to learn robust and strong prior [45].

![](img/0c56ac060cc6089fd33efc0e4aeb71a8_110_0.png)

Figure 6.3 Encoder layer and decoder layer of the CNN.

**Table 6.2** SSIM and PSNR values for synthetic scenes (Figure 6.4).

| Techniques | Prior based/without prior | SSIM (Synthetic scene) | PSNR (Synthetic scene) |
|---|---:|---:|
| DCP (He *et al.*) | Prior based | 0.58 | 27.78 |
| CAP (Zhu *et al.*) | Prior based | 0.48 | 27.96 |
| CNN (Rashid *et al.*) | Without prior based | 0.59 | 27.78 |
| FCN (Mondal *et al.*) | Without prior based | 0.67 | 28.76 |

**Table 6.3** Average CIEDE2000 values for real scene dataset (45 images).

| Techniques | Prior based/without prior | CIEDE2000 (Real scene) |
|---|---:|
| CLAHE (Soni *et al.*) | Prior based | 40.01 |
| DCP (He *et al.*) | Prior based | 9.90 |
| CAP (Zhu *et al.*) | Prior based | 12 |
| CNN (Rashid *et al.*) | Without prior based | 4.95 |
| FCN (Mondal *et al.*) | Without prior based | 6.71 |

**Table 6.4** Average SSIM and PSNR values for synthetic scenes for outdoor haze dataset (45 images).

| Techniques | Prior based/without prior | SSIM (Synthetic scene) | PSNR (Synthetic scene) |
|---|---:|---:|
| DCP (He *et al.*) | Prior based | 0.65 | 28.01 |
| CAP (Zhu *et al.*) | Prior based | 0.55 | 27.97 |
| CNN (Rashid *et al.*) | Without prior based | 0.62 | 28.04 |
| FCN (Mondal *et al.*) | Without prior based | 0.68 | 28.60 |

## 6.5 Output for Synthetic Scenes

![](img/0c56ac060cc6089fd33efc0e4aeb71a8_113_0.png)

![](img/0c56ac060cc6089fd33efc0e4aeb71a8_113_1.png)

![](img/0c56ac060cc6089fd33efc0e4aeb71a8_113_2.png)

![](img/0c56ac060cc6089fd33efc0e4aeb71a8_113_3.png)

![](img/0c56ac060cc6089fd33efc0e4aeb71a8_113_4.png)

![](img/0c56ac060cc6089fd33efc0e4aeb71a8_113_5.png)

![](img/0c56ac060cc6089fd33efc0e4aeb71a8_113_6.png)

Figure 6.4 Synthetic scenes using different techniques.

## 6.6 Output for Real Scenes

![](img/0c56ac060cc6089fd33efc0e4aeb71a8_113_7.png)

![](img/0c56ac060cc6089fd33efc0e4aeb71a8_113_8.png)

![](img/0c56ac060cc6089fd33efc0e4aeb71a8_113_9.png)

![](img/0c56ac060cc6089fd33efc0e4aeb71a8_113_10.png)

![](img/0c56ac060cc6089fd33efc0e4aeb71a8_113_11.png)

![](img/0c56ac060cc6089fd33efc0e4aeb71a8_113_12.png)

Figure 6.5 Real hazy scenes using different techniques.
