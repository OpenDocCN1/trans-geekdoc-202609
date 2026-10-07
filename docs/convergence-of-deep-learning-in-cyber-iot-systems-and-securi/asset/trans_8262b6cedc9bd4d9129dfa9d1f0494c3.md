

深度学习在物联网系统中的收敛与安全

### 表 8.2 AR 数据库的识别率。

| PC | 未掩码脸部识别率 (%) | 掩码脸部识别率 |
|---|---|---|
| 30 | 67.71% | 64.37% |
| 60 | 84.12% | 80.11% |
| 90 | 88.21% | 83.83% |
| 120 | 90.97% | 85.55% |
| 150 | 92.13% | 88.84% |
| 180 | 92.87% | 89.12% |
| 210 | 92.96% | 89.69% |
| 240 | 94.29% | 91.13% |
| 270 | 94.95% | 91.70% |
| 300 | 94.01% | 91.41% |

![](img/081dc7f102a379cb0898a0e19b8f199_0.png) 图 8.11 未掩码脸部数据库识别率与特征维度的性能对比。对抗新冠-19 的掩码脸部识别技术

![](img/081dc7f102a379cb0898a0e19b8f200_0.png) 图 8.12 掩码脸部 ORL 数据库识别率与特征维度的性能对比。![](img/081dc7f102a379cb0898a0e19b8f201_0.png) 图 8.13 未掩码脸部 AR 数据库识别率与特征维度的性能对比。深度学习在物联网系统中的收敛与安全

![](img/081dc7f102a379cb0898a0e19b8f201_0.png) 图 8.14 AR 数据库（掩码脸部）识别率与特征维度的性能对比。所提技术与传统 PCA 相比提供了更高的精度。与现有方法的对比见表 8.3 和表 8.4，显示了所提技术与其他方法相比的性能提升。

### 表 8.3 AR 数据库上与其他方法的对比。

| 方法 | 识别率 (%) |
|---|---|
| PCA+CRC RLS [32] | 90.00% |
| SRC [35] | 90.10% |
| 所提方法 | 94.95%（针对未掩码脸部） 91.70%（针对掩码脸部） |

### 表 8.4 ORL 数据库上与其他方法的对比。

| 方法 | 识别率 (%) |
|---|---|
| PCA+SRC-MP [36] | 89.00% |
| PCA+SR [37] | 90.70% |
| PPCA [38] | 90.5% |
| 所提方法 | 91.50%（针对未掩码脸部） 90.35%（针对掩码脸部） |

## 8.6 结论

本文提出了一种利用特征级融合方法的高效人脸识别（FR）方法，该方法提高了掩码和未掩码脸部的识别率。该技术集成了离散曲波变换、PCA 和压缩感知。由于融合特征的维度较低，该方法适用于实时问题。在 ORL 和 AR 数据库上的仿真结果清楚表明，所提技术与其他技术相比更优越，并在 ORL 数据库上提供了 91.5% 的最大识别率，在 AR 数据库的未掩码脸部上识别率为 94.95%。对于掩码脸部，该技术也表现良好，ORL 数据库的最高识别率为 90.35%，AR 数据库的最高识别率为 91.70%。结果表明，在掩码和未掩码脸部的两种情况下，所提技术与传统 PCA 相比提供了更高的识别率。所提技术在未来可以扩展为：

-   可以使用其他融合方法进行特征选择，以在不同的人脸识别约束下获得更好的识别率。
-   可以使用变换域中其他特征的重要性来提高识别率。
-   可以应用深度学习技术来提高识别率。

## 参考文献

- Yang, M. and Zhang, L., Gabor feature based sparse representation for face recognition with Computer Vision, in: Proc. 11th European Conference on Computer Vision, p. 448–461, p. 6316, 2010.
- Candes, E., Demanet, L., Donoho, D., Ying, L., Fast discrete curvelet transforms. Multiscale Model., 5, 861–899, 2006.
- Wright, J., Yang, A., Ganesh, A., Sastry, S., Ma, Y., Robust face recognition via sparse representation. IEEE Trans. Pattern Anal. Mach. Intell., 31, 210–227, 2009.
- Nagesh, P. and Li, B., A compressive sensing approach for expression-variant recognition, in: Proc. IEEE Conference on Computer Vision and Pattern Recognition, p. 1518–1525, 2009.
- Lin, Z., Wenrui, Z., Li, S., Infrared face recognition based on compressive sensing, in: Proc. IEEE International Conference on Science and Automation, vol. 2, 51–54, 2011.
- Sirovich, L. and Kirby, M., Low-dimensional procedure for characterization of human faces. J. Opt. Soc. A, 4, 519–524, 1987.
- Jadhav, A., Jadhav, A., Ladhe, T., Yolekar, C., Automated attendance system using face recognition. Int. Res. Eng. Technol. (IJET), 4, 1467–1471, 2017.
- Punjani, A., Obaid, C., Yasir, C., Automated attendance system using face recognition. Int. Adv. Res. Comput. Eng. (IJARCET), 6, 1–5, 2017.
- Kutty, N.M. and Mathai, S., Face recognition - a tool for automated attendance system. Int. J. Sci. ., 7, 334,,,,, 20,,.,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,, Monitoring system using face techniques. Int. Res. Eng. Technol. (IJET), 6, 1629–1034, 2019.
- Bah, S. and Ming, F., An improved face recognition algorithm and its application. Array, 5, 1–7, 2020.
- Mallikarjuna Reddy, A., Venkata Krishna, V., Sumalatha, L., Face recognition based on Cross motif. Int. Image Graph. Signal Process., 3, 59–66, 2018.
- Takar, P., Benco, M., Mizdos, T., Radil, R., A new method for face recognition using convolutional neural network. Digital Image Process. Graphics, 15, 2, 27, 2020.
- Kembi, I.L. and Chusheng, G., Enhancing face identification using local binary patterns and K-nearest neighbors. Imaging, 3, 37–12, 2017.
- Gaikwad, A.T., Airain, R.H., Maitlo, A., Ruk, S., Shaikh, H., Study of face recognition techniques: a survey. Glob. J. Eng. Sci. Res., 5, 368–373, 2018.
- Lal, M., Mumlar, K., Airain, R.H., Maitlo, A., Rehman, A., Int. J. Adv. Comput. Sci. Appl., 9, 6, 42–49, 2018.
- Sharif, M., Naz, F., Yasmin, M., Shahid, M.A., Rehman, A., Face recognition as a survey. Int. J. Sci. Technol. Rev., 10, 2, 166–177, March 2017.
- Ramaiah, N.P., Ijjina, E.P., Mohan, C.K., Illumination invariant face recognition using convolutional neural networks. IEEE International Conference on Signal Processing, Informatics, and Energy Systems (SPICES), 1–4, 2015.
- Bhangale Kishore, B., Jadhav Kamal, M., Shirke Yogesh, R., Robust face invariant recognition using DCP and LB. IJMTE, 8, 1026–1034, 2018.
- Taigman, Y., Yanga, M., Ranzato, M., Wolf, L., Deep Face: closing the gap for human-level performance in face verification; in: IEEE Conference on Computer Vision and Pattern Recognition, pp. 1701–1708, 2014.
- Taskar, M., Kahraman, N., Erdem, C.E., Face recognition: a review. Digital Image Process. Graphics, 15, 2, 27, 2020.

