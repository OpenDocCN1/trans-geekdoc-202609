
is evaluated and analyzed by the Performance parameters. Those include Spearman Rank Ordered Correlation Coefficient (SROCC), Pearson Linear Correlation Coefficient (PLCC), and Root Mean Square Error (RMSE). These parameters are the most significant algorithm to evaluate NR-IQA [41]. Prediction monotonicity of the proposed method is measured through SROCC parameter and can be defined as:

SROCC(Q_obj, Q_sub) = 1 - (6 Σ D_i) / [N(N² - 1)] (11.24)

Where Q_obj and Q_sub are predicted and actual score, respectively. Subjective score is the actual score predicted by human eye. D_i is the grade difference among Q_obj and Q_sub for sample i. And N is the number of images in the evaluation database.

PLCC defines the correlation between the subjective score and objective prediction score. Prediction accuracy is measured through PLCC parameter and can be defined as:

PLCC(Q_obj, Q_sub) = cov(Q_obj, Q_sub) / [σ(Q_obj) σ(Q_sub)] (11.25)

The absolute deviation between subjective and objective score can be measured by RMSE and can be defined as:

RMSE = √[ (1/N) Σ_{i=1}^N (S_i - O_i)² ] (11.26)

Where S and O are subjective mean opinion score and objective mean opinion score, respectively. Subjective assessment is evaluated by large number of observers. Tables 11.4–11.6 show that the performance results of proposed method in terms of SROCC, PLCC, and RMSE, respectively, for different distortions include JPEG 2000 (JP2K), JPEG, additive white noise (WN), Gaussian Blur (GB), and Fast Fading (FF). It is observed that the proposed method has a high measure of consistency with subjective qualitative assessment of human visual observation. Table 11.4 shows the performance comparison of the proposed method with respect to SROCC. The proposed methods SROCC result is 0.952 considering all the distortions. We can see that the FR IQA methods are competitive with the proposed algorithm in terms of SROCC performance, and proposed method is statistically efficient than the state-of-the-art NR-IQA methods. Our proposed method improvements over SROCC score is 1.2% than WLBP [32] method in case of JP2K artifact, 0.73% than WLBP [32] method in case of JPEG artifact, 0.20% than DIIVINE [20] method in case of WN distortion, 1.04% than CORNIA [19] method in case of GB distortion, 1.53% than WLBP [32] method in case of FF distortion, and 0.84% than WLBP [32] method considering all distortions.

## Table 11.4 SROCC performance comparison on NIH database on various distortions

| Methods | JP2K | JPEG | WN | GB | FF | ALL |
|---|---|---|---|---|---|---|
| PSNR | 0.842 | 0.861 | 0.935 | 0.725 | 0.855 | 0.846 |
| SSIM [8] | 0.938 | 0.953 | 0.964 | 0.853 | 0.936 | 0.887 |
| IFC [9] | 0.939 | 0.916 | 0.936 | 0.894 | 0.942 | 0.911 |
| BRISQUE [15] | 0.916 | 0.929 | 0.958 | 0.924 | 0.958 | 0.935 |
| CORNIA [19] | 0.906 | 0.876 | 0.961 | 0.946 | 0.923 | 0.916 |
| DIIVINE [20] | 0.923 | 0.935 | 0.976 | 0.935 | 0.905 | 0.932 |
| WLBP [32] | 0.926 | 0.939 | 0.971 | 0.939 | 0.961 | 0.944 |
| Proposed | 0.938 | 0.946 | 0.978 | 0.956 | 0.976 | 0.952 |

## Table 11.5 PLCC performance comparison on NIH database on various distortions

| Methods | JP2K | JPEG | WN | GB | FF | ALL |
|---|---|---|---|---|---|---|
| PSNR | 0.883 | 0.871 | 0.976 | 0.731 | 0.886 | 0.834 |
| SSIM [8] | 0.936 | 0.913 | 0.971 | 0.835 | 0.913 | 0.873 |
| IFC [9] | 0.905 | 0.899 | 0.955 | 0.925 | 0.928 | 0.915 |
| BRISQUE [15] | 0.945 | 0.936 | 0.962 | 0.933 | 0.897 | 0.925 |
| CORNIA [19] | 0.923 | 0.925 | 0.958 | 0.946 | 0.935 | 0.921 |
| DIIVINE [20] | 0.937 | 0.932 | 0.961 | 0.953 | 0.853 | 0.932 |
| WLBP [32] | 0.939 | 0.941 | 0.953 | 0.955 | 0.845 | 0.935 |
| Proposed | 0.951 | 0.948 | 0.968 | 0.972 | 0.955 | 0.946 |

## Table 11.6 RMSE performance comparison on NIH database on various distortions

| Methods | JP2K | JPEG | WN | GB | FF | ALL |
|---|---|---|---|---|---|---|
| PSNR | 7.116 | 8.108 | 3.658 | 9.055 | 7.883 | 9.204 |
| SSIM [8] | 5.314 | 6.923 | 3.855 | 7.321 | 5.325 | 8.843 |
| IFC [9] | 6.833 | 7.211 | 4.653 | 4.653 | 4.012 | 6.254 |
| BRISQUE [15] | 6.484 | 9.156 | 7.521 | 7.751 | 9.656 | 9.092 |
| CORNIA [19] | 8.332 | 9.287 | 7.615 | 7.521 | 8.921 | 9.321 |
| DIIVINE [20] | 8.585 | 9.632 | 8.202 | 8.202 | 10.246 | 9.998 |
| WLBP [32] | 7.969 | 9.129 | 9.116 | 9.116 | 10.004 | 9.634 |
| Proposed | 6.321 | 8.183 | 6.929 | 6.924 | 8.125 | 8.652 |

Table 11.5 shows the performance comparison of the proposed method with respect to PLCC. The proposed methods PLCC result is 0.946 considering all the distortions. Our proposed method improvements over PLCC score is 0.63% than BRISQUE [15] method in case of JP2K artifact, 0.73% than WLBP [32] method in case of JPEG artifact, 0.61% than BRISQUE [15] method in case of WN distortion, 1.74% than WLBP [32] method in case of GB distortion, 2.09% than CORNIA [19] method in case of FF distortion, and 1.16% than WLBP [32] method considering all distortions. Table 11.6 shows the performance comparison of the proposed method with respect to SROCC. The proposed methods RMSE result is 8.652 considering all the distortions. Our proposed method improvements over RMSE score is 2.57% than BRISQUE [15] method in case of JP2K artifact, 11.48% than WLBP [32] method in case of JPEG artifact, 8.54% than BRISQUE [15] method in case of WN distortion, 8.62% than CORNIA [19] method in case of GB distortion, 9.79% than CORNIA [19] method in case of FF distortion, and 5.02% than BRISQUE [15] method considering all distortions.

## 11.4 CONCLUSION

A distortion generic No Reference Image Quality Assessment (NR-IQA) algorithm was developed in this chapter that operates in Wavelet domain. A NSS-based no reference quality assessment method was proposed for assessing quality of a medical image without using a reference image considering various distortions to be applied in image security and authorization. First, the features are extracted from the distorted image in wavelet domain and is then processed using SVR technique to estimate the image quality index. Experiments were performed on NIH database, and the proposed algorithm achieved a good performance over existing NR-IQA methods in terms of SROCC, PLCC, and RMSE parameters. Simulation results proved that the quality index of the proposed method is in line with FR-IQA methods and better than existing NR-IQA methods. In the future, a hybrid method may be developed considering the image features in various domains to extract more features from the medical images to produce a more accurate quality index.

## REFERENCES

- [1] Cao, F., Huang, H. K., & Zhou, X. Q. (2003). Medical image security in a HIPAA mandated PACS environment. Computerized Medical Imaging and Graphics, 27(2–3), 185–196.
- [2] Herbadji, D., Belmeguenai, A., Derouiche, N., & Liu, H. (2020). Colour image encryption scheme based on enhanced quadratic chaotic map. IET Image Processing, 14(1), 40–52.
- [3] Chow, L. S., & Paramesran, R. (2016). Review of medical image quality assessment. Biomedical Signal Processing and Control, 27, 145–154.
- [4] Alqahtani, F., Amoon, M., & El-Shafai, W. (2022). A fractional fourier based medical image authentication approach. CMC-Computers Materials & Continua, 70(2), 3133–3150.
- [5] Sun, T., Wang, X., Zhang, K., Jiang, D., Lin, D., Jv, X., ... & Zhu, W. (2022). Medical image authentication method based on the wavelet packet and energy entropy. *Entropy*, 24(6), 798.
- [6] Stępień, I., & Oszust, M. (2022). A brief survey on no-reference image quality assessment methods for magnetic resonance images. *Journal of Imaging*, 8(6), 160.
- [7] Marwan, M., Kartit, A., & Ouahmane, H. (2018). Security enhancement in healthcare cloud using machine learning. *Procedia Computer Science*, 127, 388–397.
- [8] Wang, Z., Bovik, A. C., Sheikh, H. R., & Simoncelli, E. P. (2004). Image quality assessment: From error visibility to structural similarity. *IEEE Transactions on Image Processing*, 13(4), 600–612.
- [9] Sheikh, H. R., & Bovik, A. C. (2006). Image information and visual quality. *IEEE Transactions on Image Processing*, 15(2), 430–444.
- [10] Jayageetha, J., & Vasanthanayaki, C. (2018). Medical image quality assessment using CSO based deep neural network. *Journal of Medical Systems*, 42, 1–9.
- [11] Padmapriya, R., & Jeyasekar, A. (2022). Blind image quality assessment with image denoising: A survey. *Journal of Pharmaceutical Negative Results*, 13, 386–392.
- [12] Omarova, G., Starovoitov, V., Myrzamuratova, A., Akzullakyzy, L., Takuadina, A., Tanirbergenov, A., ... & Sadirmekova, Z. (2023). No-reference quality assessment of medical images using contrast enhancement. *Journal of Theoretical and Applied Information Technology*, 101(1), 267–281.
- [13] Kumar, J., Chen, F., & Doermann, D. (2012, November). Sharpness estimation for document and scene images. In *Proceedings of the 21st International Conference on Pattern Recognition (ICPR2012)* (pp. 3292–3295). IEEE.
- [14] Saad, M.A., Bovik, A. C., & Charrier, C. (2012). Blind image quality assessment: A natural scene statistics approach in the DCT domain. *IEEE Transactions on Image Processing*, 21(8), 3339–3352.
- [15] Mittal, A., Moorthy, A. K., & Bovik, A. C. (2012). No-reference image quality assessment in the spatial domain. *IEEE Transactions on Image Processing*, 21(12), 4695–4708.
- [17] Li, J., Yu, J., Xu, L., Xue, X., Chang, C.-C., Mao, X., & Hu, J. (2018). A cascaded algorithm for image quality assessment and image denoising based on CNN for image security and authorization. *Security and Communication Networks*, 2018(2), 1–13.
- [18] Moorthy, A. K., & Bovik, A. C. (2011). Blind image quality assessment: From natural scene statistics to perceptual quality. *IEEE Transactions on Image Processing*, 20(12), 3350–3364.
- [19] Ye, P., Kumar, J., Kang, L., & Doermann, D. (2012, June). Unsupervised feature learning framework for no-reference image quality assessment. In *2012 IEEE conference on computer vision and pattern recognition* (pp. 1098–1105). IEEE.
- [20] Saad, M. A., Bovik, A. C., & Charrier, C. (2010). A DCT statistics-based blind image quality index. *IEEE Signal Processing Letters*, 17(6), 583–586.
- [21] Mittal, A., Soundararajan, R., & Bovik, A. C. (2013). Making a “completely blind” image quality analyzer. *IEEE Signal Processing Letters*, 20(3), 209–212.
