Table 3. The results of different evaluation indicators. 
| SRIE | NPE | GLADNet | EnlightenGAN | Retinex-Net | Proposed Method |
|---|---|---|---|---|---|
| SSIM | 0.4977 | 0.5842 | 0.7115 | 0.6260 | 0.5594 | 0.7581 |
| PSNR (dB) | 11.8550 | 16.8034 | 19.3821 | 19.2303 | 16.7739 | 19.4536 |
| NIQE | 7.2873 | 8.2562 | 6.1744 | 4.528 | 9.7303 | 4.2874 |
| LOE | 575 | 439 | 493 | 445 | 1106 | 417 |

# 5. Conclusions

This paper proposed a modified Retinex-Net algorithm. By using an efficient attention mechanism method and constructing information interaction between the attention modules, the performance of attention mechanism can be maximized to a certain extent to ameliorate the network’s learning ability. The denoising loss can effectively suppress noise and retain the essential structure of the image. The color loss restores the image to a more natural color, making the result more robust. The final enhancement result of the proposed algorithm is moderate in brightness, and is not too dark or too bright. The color is natural and not distorted, avoiding artifacts and excessive noise. The objective evaluation indexes such as PSNR and SSIM have also achieved better results. The primary research goal in the future is to improve the running time of the algorithm and to extend it to the task of object detection or object recognition under low light.

**Author Contributions:** Conceptualization, M.L.; methodology, M.L. and J.C.; software, J.C.; validation, J.C. and X.H.; formal analysis, M.L.; investigation, M.L. and J.C.; resources, M.L. and J.C.; data curation, J.C.; writing—original draft preparation, M.L. and J.C.; writing—review and editing, M.L., J.C.; visualization, J.C. and X.H.; supervision, M.L. All authors have read and agreed to the published version of the manuscript.

**Funding:** This research received no external funding.

**Institutional Review Board Statement:** Not applicable.

**Informed Consent Statement:** This study did not involve humans and chose to exclude this statement.

**Data Availability Statement:** The data presented in this study are available on request from the corresponding author.

**Conflicts of Interest:** The authors declare no conflict of interest.

# References

+   1. Hu, X.; Ma, P.; Mai, Z.; Peng, S.; Yang, Z.; Wang, L. Face hallucination from low quality images using definition-scalable inference. *Pattern Recognit.* **2019**, *94*, 110–121. [CrossRef]
2. Pan, R.; Zeng, L.; Wum, S.; Wang, R. Feature detection method for low illumination image. *Sens. Microsys.* **2021**, *40*, 110–113+117.
3. Liu, M.; Su, T.; Wang, Y. Companding multiscale Research on Retinex image enhancement algorithm. *J. Harbin Univ. Sci. Technol. 2020*, *25*, 93–99.
4. Jiang, J.L.; Liu, G.M.; Zhu, Z.; Huang, Z.; Zheng, J.Y. Dynamic Multi-Histogram Equalization Based on Fast Fuzzy Clustering. *Acta Electron. Sin.* **2022**, *50*, 167–176.
5. Wang, L.; Chang, X.; Ren, W. Color Image Enhancement Simulation Based on Weighted Histogram Equalization. *Comput. Simul. 2021*, *38*, 126–131.
6. Xuan, D.; Guan, W.; Yi, P.; Wen, J. Fast Efficient Algorithm for Enhancement of Low Lighting Video. In Proceedings of the 2011 IEEE International Conference on Multimedia and Expo, Barcelona, Spain, 11–15 July 2011; IEEE: Toulouse, France; pp. 1–6.
7. He, K.; Sun, J.; Tang, X. Single Image Haze Removal Using Dark Channel Prior. *IEEE Trans. Pattern Anal. Mach. Intell. 2011*, *33*, 2341–2353. [PubMed]
8. Land, E.H. The Retinex Theory of Color Vision. *Sci. Am.* **1978**, *237*, 108–128. [CrossRef] [PubMed]
9. Yang, J.; Xu, Z.; Yang, H.; Jiang, Z.; Li, K. Low-light image enhancement based on Retinex decomposition and adaptive gamma correction. *IET Image Process.* **2020**, *15*, 211–220. [CrossRef]
10. Liu, S.; Song, W.; He, L.; Li, Y.; Ding, W. Retinex-Based Fast Algorithm for Low-Light Image Enhancement. *Entropy* **2021**, *23*, 746. [CrossRef] [PubMed]