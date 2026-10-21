
![](img/fe161b7f6e96e35e7e853eece52c6dce_520_0.png)

FIGURE 14.10 Estimations in different iterations of DUIR for deblurring on the Starfish in Fig. 14.6. (a) x₁; (b) z₁; (c) x₂; (d) z₆; (e) x₇; (f) z₇.

the shift problem should be properly addressed. To tackle this, we adjust z₀ by using grid interpolation.

### 14.5.2.1 Quantitative and qualitative comparison

Table 14.4 reports the average PSNR(dB) results of DPIR and DUIR on the three testing images. From Table 14.4, we can see the PSNR results vary across different blur kernels and the blur kernels that lead to the highest PSNR for each scale factor are different. More specifically, a larger scale factor generally requires a smoother blur kernel. In addition, DUIR outperforms DPIR by a large margin. Such a phenomenon indicates that end-to-end training is more helpful for superresolution than for deblurring. Fig. 14.12 shows the visual results of DPIR and DUIR on the three testing images. It can be observed that both DPIR and DUIR can significantly improve the visual quality. In comparison, DUIR produces sharper edges than DPIR which is possibly due to the end-to-end-training.

![](img/fe161b7f6e96e35e7e853eece52c6dce_521_0.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_521_1.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_521_2.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_521_3.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_521_4.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_521_5.png)

(a) k_bicubic^{×2}

(b) k_bicubic^{×3}

(c) k_bicubic^{×4}

FIGURE 14.11 Approximated bicubic kernels for scale factors 2, 3 and 4 under the degradation model y = (x ⊗ k)↓s. Note that these kernels contain negative values.

TABLE 14.4 Average PSNR(dB) results of DPIR and DUIR for different combinations of scale factors, blur kernels and noise levels. The best results are highlighted in bold.

| Method | Scale Factor | Noise Level | K1 | K2 | K3 | K4 | K5 | K6 | K7 | K8 |
|---|---|---|---|---|---|---|---|---|---|---|
| DPIR | ×2 | 0 | 31.79 | 32.10 | 31.28 | 29.63 | 28.72 | 28.62 | 29.45 | 27.77 |
| DPIR | ×3 | 0 | 26.04 | 26.82 | 26.97 | 26.89 | 26.73 | 25.89 | 26.58 | 26.49 |
| DPIR | ×3 | 2.55 | 25.91 | 26.49 | 26.23 | 25.43 | 24.81 | 24.44 | 25.29 | 24.13 |
| DPIR | ×3 | 7.65 | 25.53 | 25.67 | 24.91 | 23.68 | 23.14 | 22.81 | 23.56 | 22.33 |
| DPIR | ×4 | 0 | 22.62 | 23.50 | 23.74 | 23.85 | 23.76 | 23.18 | 23.58 | 23.88 |
| DUIR | ×2 | 0 | **33.58** | **34.47** | **33.49** | **31.79** | **31.29** | **31.29** | **31.45** | **30.20** |
| DUIR | ×3 | 0 | **28.05** | **29.53** | **29.88** | **29.87** | **29.40** | **29.37** | **29.43** | **29.25** |
| DUIR | ×3 | 2.55 | **27.77** | **28.74** | **28.47** | **27.70** | **27.15** | **27.20** | **27.42** | **26.54** |
| DUIR | ×3 | 7.65 | **26.87** | **27.13** | **26.43** | **25.47** | **25.15** | **25.03** | **25.24** | **24.47** |
| DUIR | ×4 | 0 | **24.71** | **26.38** | **27.02** | **27.30** | **27.16** | **26.76** | **26.69** | **27.28** |

![](img/fe161b7f6e96e35e7e853eece52c6dce_522_0.png)

FIGURE 14.12 Visual results of DPIR and DUIR on the three testing images. The blur kernel is visualized in the upper right corner of the LR image. (a) LR image; (b) DPIR; (c) DUIR.

### 14.5.2.2 Hand-designed vs. learned hyper-parameters

Figs. 14.13 and 14.14 illustrate the hyper-parameters, i.e., α and β, of DPIR and DUIR for different combinations of scale factor s and noise level σ, respectively. One can see that the learned hyper-parameters of DUIR accord with the hand-designed hyper-parameters of DPIR.

From Figs. 14.13 and 14.14(a), one can see that α is positively correlated with σ and varies with s. This actually accords with the definition of α_k. From Figs. 14.13 and 14.14(b), one can see that β has a decreasing tendency with the number of iterations and increases with scale factor and noise level. This implies that the noise level of HR estimation is gradually reduced across iterations and complex degradation requires a large β_k to tackle the ill-posedness.

![](img/fe161b7f6e96e35e7e853eece52c6dce_523_0.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_523_1.png)

(a)

(b)

FIGURE 14.13 The hyper-parameters, i.e., (a) α and (b) β, of DPIR for superresolution with respect to different combinations of noise levels and scale factors.

![](img/fe161b7f6e96e35e7e853eece52c6dce_523_2.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_523_3.png)

(a)

(b)

FIGURE 14.14 The hyper-parameters, i.e., (a) α and (b) β, of DUIR for superresolution with respect to different combinations of noise levels and scale factors.

### 14.5.2.3 Intermediate results

Figs. 14.15 and 14.16 provide the visual results of x_k and z_k at different iterations of DPIR and DUIR on the Starfish image from Fig. 14.12. One can observe from Fig. 14.15 that, although the LR image contains no noise, the closed-form solution x₁ would introduce severe structured noise. After passing x₁ through the Gaussian denoiser, such structured noise is removed, as can be seen from z₁. Meanwhile, the tiny textures and structures are smoothed out and the edges become blurry. As the number of iterations increases, x₇ contains less structured noise than x₁, while z₇ recovers more details and sharper edges than z₁. One can observe from Fig. 14.16 that, 𝒟 and 𝒫 can facilitate each other for iterative and alternating blur removal and detail recovery. Interestingly, different from the Gaussian denoiser prior of DPIR, 𝒫 can also act as a detail enhancer for high-frequency recovery which is possibly attributed to the task-specific training. In addition, it does not reduce blur kernel induced degradation, which verifies the decoupling between 𝒟 and 𝒫. As a result, the end-to-end trained DUIR has a task-specific advantage over DPIR.

![](img/fe161b7f6e96e35e7e853eece52c6dce_524_0.png)

### 14.6 Discussion and conclusions

In this chapter, we introduce the deep plug-and-play methods and deep unfolding methods that can integrate model-based methods and learning-based methods for image restoration. Specifically, with the aid of the half-quadratic splitting algorithm which can decouple the data and prior terms, deep plug-and-play methods can replace the prior subproblem with learning-based denoiser prior, while deep unfolding methods learn an end-to-end trainable, iterative network by solving the prior subproblem via neural modules. As a result, both deep plug-and-play methods and deep unfolding methods can inherit the flexibility of model-based methods, while maintaining the advantages of learning-based methods. In order to better understand the working mechanism of both kinds of method, quantitative and qualitative results as well as a comparative analysis of hyper-parameter setting and intermediate results are provided. The results demonstrate that while deep unfolding methods learn similar hyper-parameters to the hand-designed ones of deep plug-and-play methods, the learned prior modules are different from those of the Gaussian denoiser priors. For example, the learned prior module of deep unfolding methods can also enhance the details while the Gaussian denoiser prior of deep plug-and-play methods does not have such a merit.

![](img/fe161b7f6e96e35e7e853eece52c6dce_525_0.png)

FIGURE 14.16 HR estimations in different iterations of DUIR for superresolution on the Starfish in Fig. 14.12.
(a) x₁; (b) z₁; (c) x₂; (d) z₆; (e) x₇; (f) z₇.

While the proposed deep plug-and-play methods and deep unfolding methods have shown great promise, they also have several drawbacks for real applications. First, they are nonblind methods which require an accurate estimation of degradation parameters such as the blur kernel. If the estimated blur kernel deviates largely from the ground-truth one, performance would deteriorate seriously. Second, they are designed on the ideal degradation model which rarely matches for real images. If the real-world noise does not follow an additive white Gaussian distribution, this would lead to a drop in performance.

## Acknowledgments

This work was partly supported by the ETH Zürich Fund (OK), and a Huawei Technologies Oy (Finland) project.

## References

- Abdelhamed, A., Brubaker, M.A., Brown, M.S., 2019. Noise flow: noise modeling with conditional normalizing flows. In: IEEE International Conference on Computer Vision, pp. 3165–3173.
- Afonso, M.V., Bioucas-Dias, J.M., Figueiredo, M.A., 2010. Fast image recovery using variable splitting and constrained optimization. IEEE Transactions on Image Processing 19 (9), 2345–2356.
- Agustsson, E., Timofte, R., 2017. NTIRE 2017 challenge on single image super-resolution: dataset and study. In: IEEE Conference on Computer Vision and Pattern Recognition Workshops, vol. 3, pp. 126–135.
