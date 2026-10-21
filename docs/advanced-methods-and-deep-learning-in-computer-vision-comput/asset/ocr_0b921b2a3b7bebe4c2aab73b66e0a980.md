![](bbox=[0.2, 0.13, 0.83, 0.47])

FIGURE 14.10 Estimations in different iterations of DUIR for deblurring on the Starfish in Fig. 14.6. (a) x₁; (b) z₁; (c) x₂; (d) z₆; (e) x₇; (f) z₇.

the shift problem should be properly addressed. To tackle this, we adjust z₀ by using grid interpolation.

# 14.5.2.1 Quantitative and qualitative comparison

Table 14.4 reports the average PSNR(dB) results of DPIR and DUIR on the three testing images. From Table 14.4, we can see the PSNR results vary across different blur kernels and the blur kernels that lead to the highest PSNR for each scale factor are different. More specifically, a larger scale factor generally requires a smoother blur kernel. In addition, DUIR outperforms DPIR by a large margin. Such a phenomenon indicates that end-to-end training is more helpful for superresolution than for deblurring. Fig. 14.12 shows the visual results of DPIR and DUIR on the three testing images. It can be observed that both DPIR and DUIR can significantly improve the visual quality. In comparison, DUIR produces sharper edges than DPIR which is possibly due to the end-to-end-training.

# 14.5.2.2 Hand-designed vs. learned hyper-parameters

Figs. 14.13 and 14.14 illustrate the hyper-parameters, i.e., α and β, of DPIR and DUIR for different combinations of scale factor s and noise level σ, respectively. One can see that the learned hyper-parameters of DUIR accord with the hand-designed hyper-parameters of