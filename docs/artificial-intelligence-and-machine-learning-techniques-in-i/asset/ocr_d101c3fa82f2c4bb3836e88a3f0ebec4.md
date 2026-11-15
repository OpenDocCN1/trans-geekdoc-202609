Suzie, Vipmen, News, and Foreman with 30 frames/s is presented in the standard database. The sample watermarks tried in the experiments are cameraman, Nature, and logo.

Several tests via MATLAB 2013 are conducted to estimate the robustness of the proposed technique. On the watermarked video, several image-and frame-oriented attacks mentioned in the results were applied. PSNR and NCC were used to assess the quality of the output video and retrieved watermark, the formula is represented in eqs 6.4 and 6.5.

\( PSNR(M,\hat{M})=10 \text{Log}_{10} \frac{255^2}{\frac{1}{LxK} \sum_{i=1}^L \sum_{j=1}^k (M_{ij}-\hat{M}_{ij})^2} \quad (6.4) \ 
NC=\frac{\sum_i \sum_j M(i,j).M(i,j)}{\sum_i \sum_j [M(i,j)]^2} \quad (6.5) \)

# TABLE 6.2 PSNR and NCC Values After Applying Various Attacks.

| Type of attack | PSNR (dB) of watermarked video | PSNR of extracted watermark | NCC of extracted watermark |
|---|---|---|---|
| No attack | 58.33 | 59.51 | 0.98 |
| Gaussian noise | 49.91 | 50.51 | 0.93 |
| Poission noise | 48.38 | 52.32 | 0.90 |
| Salt and pepper noise | 47.42 | 49.78 | 0.88 |
| Blur | 57.31 | 53.65 | 0.96 |
| Brighten | 55.64 | 54.47 | 0.95 |
| Frame averaging | 57.23 | 45.83 | 0.96 |
| Frame swapping | 58.23 | 53.31 | 0.93 |

# 6.3.1 RESULT COMPARISONS WITH EXISTING ALGORITHMS

The robustness of watermarked video produced by the proposed technique is correlated with existing methods. The performance variation of the proposed technique in the results of PSNR and NCC values for different attacks is represented in Table 6.2. PSNR fluctuation of output video between the existing and proposed approach is represented in Figure 6.6. It is witnessed from Table 6.2 and Figure 6.6 that the proposed methods