
由性能参数进行评估和分析。这些包括 Spearman 秩相关系数（SROCC）、Pearson 线性相关系数（PLCC）和均方根误差（RMSE）。这些参数是评估 NR-IQA [41] 的最重要算法。所提出方法的预测单调性通过 SROCC 参数进行衡量，可定义为：

SROCC(Q_obj, Q_sub) = 1 - (6 Σ D_i) / [N(N² - 1)] (11.24)

其中 Q_obj 和 Q_sub 分别为预测分数和实际分数。主观分数是由人眼预测的实际分数。D_i 是样本 i 的 Q_obj 与 Q_sub 之间的等级差异。N 为评估数据库中的图像数量。

PLCC 定义了主观分数与客观预测分数之间的相关性。预测精度通过 PLCC 参数进行衡量，可定义为：

PLCC(Q_obj, Q_sub) = cov(Q_obj, Q_sub) / [σ(Q_obj) σ(Q_sub)] (11.25)

主观分数与客观分数之间的绝对偏差可通过 RMSE 进行衡量，可定义为：

RMSE = √[ (1/N) Σ_{i=1}^N (S_i - O_i)² ] (11.26)

其中 S 和 O 分别为主观平均意见分数和客观平均意见分数。主观评估由大量观察者进行评估。表 11.4–11.6 显示了所提出方法在 SROCC、PLCC 和 RMSE 方面的性能结果，分别针对不同的失真，包括 JPEG 2000（JP2K）、JPEG、加性白噪声（WN）、高斯模糊（GB）和快速衰落（FF）。观察到所提出方法与人眼视觉观察的主观定性评估具有高度一致性。表 11.4 显示了所提出方法在 SROCC 方面的性能比较。考虑所有失真时，所提出方法的 SROCC 结果为 0.952。可以看出，在 SROCC 性能方面，FR IQA 方法与所提出算法具有竞争力，所提出方法在统计上比最先进的 NR-IQA 方法更有效。所提出方法在 SROCC 分数上的改进在 JP2K 伪影情况下比 WLBP [32] 方法高 1.2%，在 JPEG 伪影情况下比 WLBP [32] 方法高 0.73%，在 WN 失真情况下比 DIIVINE [20] 方法高 0.20%，在 GB 失真情况下比 CORNIA [19] 方法高 1.04%，在 FF 失真情况下比 WLBP [32] 方法高 1.53%，在考虑所有失真时比 WLBP [32] 方法高 0.84%。

## 表 11.4 在 NIH 数据库上各种失真下的 SROCC 性能比较

| 方法 | JP2K | JPEG | WN | GB | FF | ALL |
|---|---|---|---|---|---|---|
| PSNR | 0.842 | 0.861 | 0.935 | 0.725 | 0.855 | 0.846 |
| SSIM [8] | 0.938 | 0.953 | 0.964 | 0.853 | 0.936 | 0.887 |
| IFC [9] | 0.939 | 0.916 | 0.936 | 0.894 | 0.942 | 0.911 |
| BRISQUE [15] | 0.916 | 0.929 | 0.958 | 0.924 | 0.958 | 0.935 |
| CORNIA [19] | 0.906 | 0.876 | 0.961 | 0.946 | 0.923 | 0.916 |
| DIIVINE [20] | 0.923 | 0.935 | 0.976 | 0.935 | 0.905 | 0.932 |
| WLBP [32] | 0.926 | 0.939 | 0.971 | 0.939 | 0.961 | 0.944 |
| 提出 | 0.938 | 0.946 | 0.978 | 0.956 | 0.976 | 0.952 |

## 表 11.5 在 NIH 数据库上各种失真下的 PLCC 性能比较

| 方法 | JP2K | JPEG | WN | GB | FF | ALL |
|---|---|---|---|---|---|---|
| PSNR | 0.883 | 0.871 | 0.976 | 0.731 | 0.886 | 0.834 |
| SSIM [8] | 0.936 | 0.913 | 0.971 | 0.835 | 0.913 | 0.873 |
| IFC [9] | 0.905 | 0.899 | 0.955 | 0.925 | 0.928 | 0.915 |
| BRISQUE [15] | 0.945 | 0.936 | 0.962 | 0.933 | 0.897 | 0.925 |
| CORNIA [19] | 0.923 | 0.925 | 0.958 | 0.946 | 0.935 | 0.921 |
| DIIVINE [20] | 0.937 | 0.932 | 0.961 | 0.953 | 0.853 | 0.932 |
| WLBP [32] | 0.939 | 0.941 | 0.953 | 0.955 | 0.845 | 0.935 |
| 提出 | 0.951 | 0.948 | 0.968 | 0.972 | 0.955 | 0.946 |

## 表 11.6 在 NIH 数据库上各种失真下的 RMSE 性能比较

| 方法 | JP2K | JPEG | WN | GB | FF | ALL |
|---|---|---|---|---|---|---|
| PSNR | 7.116 | 8.108 | 3.658 | 9.055 | 7.883 | 9.204 |
| SSIM [8] | 5.314 | 6.923 | 3.855 | 7.321 | 5.325 | 8.843 |
| IFC [9] | 6.833 | 7.211 | 4.653 | 4.653 | 4.012 | 6.254 |
| BRISQUE [15] | 6.484 | 9.156 | 7.521 | 7.751 | 9.656 | 9.092 |
| CORNIA [19] | 8.332 | 9.287 | 7.615 | 7.521 | 8.921 | 9.321 |
| DIIVINE [20] | 8.585 | 9.632 | 8.202 | 8.202 | 10.246 | 9.998 |
| WLBP [32] | 7.969 | 9.129 | 9.116 | 9.116 | 10.004 | 9.634 |
| 提出 | 6.321 | 8.183 | 6.929 | 6.924 | 8.125 | 8.652 |

表 11.5 显示了所提出方法在 PLCC 方面的性能比较。考虑所有失真时，所提出方法的 PLCC 结果为 0.946。所提出方法在 PLCC 分数上的改进在 JP2K 伪影情况下比 BRISQUE [15] 方法高 0.63%，在 JPEG 伪影情况下比 WLBP [32] 方法高 0.73%，在 WN 失真情况下比 BRISQUE [15] 方法高 0.61%，在 GB 失真情况下比 WLBP [32] 方法高 1.74%，在 FF 失真情况下比 CORNIA [19] 方法高 2.09%，在考虑所有失真时比 WLBP [32] 方法高 1.16%。表 11.6 显示了所提出方法在 SROCC 方面的性能比较。所提出方法的 RMSE 结果在考虑所有失真时为 8.652。所提出方法在 RMSE 分数上的改进在 JP2K 伪影情况下比 BRISQUE [15] 方法高 2.57%，在 JPEG 伪影情况下比 WLBP [32] 方法高 11.48%，在 WN 失真情况下比 BRISQUE [15] 方法高 8.54%，在 GB 失真情况下比 CORNIA [19] 方法高 8.62%，在 FF 失真情况下比 CORNIA [19] 方法高 9.79%，在考虑所有失真时比 BRISQUE [15] 方法高 5.02%。

## 11.4 结论

本章开发了一种在小波域中运行的失真通用无参考图像质量评估（NR-IQA）算法。提出了一种基于 NSS 的无参考质量评估方法，用于在不使用参考图像的情况下评估医学图像的质量，考虑应用于图像安全和授权的各种失真。首先，从失真图像的小波域中提取特征，然后使用 SVR 技术进行处理以估计图像质量指数。实验在 NIH 数据库上进行，所提出算法在 SROCC、PLCC 和 RMSE 参数方面优于现有的 NR-IQA 方法。仿真结果证明，所提出方法的质量指数与 FR-IQA 方法一致，且优于现有的 NR-IQA 方法。未来，可考虑在各个域中的图像特征开发混合方法，以从医学图像中提取更多特征，从而生成更准确的质量指数。

## 参考文献

- [1] Cao, F., Huang, H. K., & Zhou, X. Q. (2003). 在 HIPAA 强制的 PACS 环境中医学影像安全. Computerized Medical Imaging and Graphics, 27(2–3), 185–196.
- [2] Herbadji, D., Belmeguenai, A., Derouiche, N., & Liu, H. (2020). 基于增强二次混沌映射的颜色图像加密方案. IET Image Processing, 14(1), 40–52.
- [3] Chow, L. S., & Paramesran, R. (2016). 医学图像质量评估综述. Biomedical Signal Processing and Control, 27, 145–154.
- [4] Alqahtani, F., Amoon, M., & El-Shafai, W. (2022). 基于分数傅里叶的医学图像认证方法. CMC-Computers Materials & Continua, 70(2), 3133–3150.
- [5] Sun, T., Wang, X., Zhang, K., Jiang, D., Lin, D., Jv, X., ... & Zhu, W. (2022). 基于小波包和能量熵的医学图像认证方法. *Entropy*, 24(6), 798.
- [6] Stępień, I., & Oszust, M. (2022). 磁共振图像无参考图像质量评估方法的简要综述. *Journal of Imaging*, 8(6), 160.
- [7] Marwan, M., Kartit, A., & Ouahmane, H. (2018). 使用机器学习增强医疗云安全. *Procedia Computer Science*, 127, 388–397.
- [8] Wang, Z., Bovik, A. C., Sheikh, H. R., & Simoncelli, E. P. (2004). 图像质量评估：从误差可见性到结构相似性. *IEEE Transactions on Image Processing*, 13(4), 600–612.
- [9] Sheikh, H. R., & Bovik, A. C. (2006). 图像信息与视觉质量. *IEEE Transactions on Image Processing*, 15(2), 430–444.
- [10] Jayageetha, J., & Vasanthanayaki, C. (2018). 使用基于 CSO 的深度神经网络的医学图像质量评估. *Journal of Medical Systems*, 42, 1–9.
- [11] Padmapriya, R., & Jeyasekar, A. (2022). 带图像去噪的盲图像质量评估：综述. *Journal of Pharmaceutical Negative Results*, 13, 386–392.
- [12] Omarova, G., Starovoitov, V., Myrzamuratova, A., Akzullakyzy, L., Takuadina, A., Tanirbergenov, A., ... & Sadirmekova, Z. (2023). 使用对比度增强的医学图像无参考质量评估. *Journal of Theoretical and Applied Information Technology*, 101(1), 267–281.
- [13] Kumar, J., Chen, F., & Doermann, D. (2012, November). 文档和场景图像的锐度估计. In *Proceedings of the 21st International Conference on Pattern Recognition (ICPR2012)* (pp. 3292–3295). IEEE.
- [14] Saad, M.A., Bovik, A. C., & Charrier, C. (2012). 盲图像质量评估：DCT 域中的自然场景统计方法. *IEEE Transactions on Image Processing*, 21(8), 3339–3352.
- [15] Mittal, A., Moorthy, A. K., & Bovik, A. C. (2012). 空域中的无参考图像质量评估. *IEEE Transactions on Image Processing*, 21(12), 4695–4708.
- [17] Li, J., Yu, J., Xu, L., Xue, X., Chang, C.-C., Mao, X., & Hu, J. (2018). 基于 CNN 的图像质量评估和图像去噪级联算法用于图像安全和授权. *Security and Communication Networks*, 2018(2), 1–13.
- [18] Moorthy, A. K., & Bovik, A. C. (2011). 盲图像质量评估：从自然场景统计到感知质量. *IEEE Transactions on Image Processing*, 20(12), 3350–3364.
- [19] Ye, P., Kumar, J., Kang, L., & Doermann, D. (2012, June). 无参考图像质量评估的无监督特征学习框架. In *2012 IEEE conference on computer vision and pattern recognition* (pp. 1098–1105). IEEE.
- [20] Saad, M. A., Bovik, A. C., & Charrier, C. (2010). 基于 DCT 统计的盲图像质量指数. *IEEE Signal Processing Letters*, 17(6), 583–586.
- [21] Mittal, A., Soundararajan, R., & Bovik, A. C. (2013). 构建“完全盲”图像质量分析器. *IEEE Signal Processing Letters*, 20(3), 209–212.
