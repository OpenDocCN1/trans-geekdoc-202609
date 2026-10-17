
首先，在分级使用不同的融合方法结合匹配分（例如使用乘积、求和、加权和最小规则），并在排名级结合（例如使用最高排名、Borda 计数和逻辑回归）。如图 4.4 所示，当人脸在用户识别处进行训练时，会产生三个匹配分。其中一个匹配分来自 `FDT-DRBM` 方法，另外两个匹配方法来自 `FaceDeepNet` 系统。在加权融合方法的实现中，所提的 `FaceDeepNet` 系统相比 `FDT-DRBM` 方法分配了更高的权重，以确保获得最高的识别率。

## 表 4.3 所提深度学习方法获得的 Rank-1 识别率

| 原始数据 | 局部特征 | 准确率 | 训练时间 |
|---|---|---|---|
| CNN | 0.89 | 12 h | 40 min |
| DBN | 0.85 | 15 h | 25 min |
| 加权 | 0.96 | 4 h | 10 min |
| 加权 | 0.94 | 4 h | 40 min |

# 多特征生物识别脸部识别系统

## 表 4.4

所提多特征生物识别脸部系统在三个不同脸部数据集上的 Rank-1 识别率。`SR` 和 `PR` 分别指和规则（Sum Rule）和乘积规则（Product Rule）。

| 分数融合方法 | 数据集 | FDT-DRBM | FaceDeepNet | SR | WSR | PR | Max | Min |
|---|---|---|---|---|---|---|---|---|
| FRGC V 2.0 | Exp. 1 | 94.11 | 97.62 | 95.12 | 97.34 | 94.92 | 95.34 | 95.21 |
| | Exp. 2 | 95.10 | 99.54 | 97.33 | 100 | 95.54 | 97.78 | 96.32 |
| | Exp. 4 | 96.21 | 98.33 | 97.13 | 99.12 | 97.13 | 97.12 | 97.12 |
| UFI | CI | 92.23 | 93.60 | 94.32 | 96.66 | 92.12 | 92.31 | 93.21 |
| | LI | 93.12 | 95.29 | 96.12 | 97.38 | 93.64 | 95.15 | 94.12 |
| SDUMCLA-HMT | 95.13 | 95.13 | 98.89 | 100 | 97.53 | 96.23 | 96.21 |

## 表 4.5

所提多特征生物识别脸部系统在三个不同脸部数据集上的 Rank-1 识别率。`HR`、`BC` 和 `LR` 分别指高阶排序（Higher Ranking）、Borda 计数和逻辑回归（Logistic regression）。

| 排序融合方法 | 数据集 | FDT-DRBM | FaceDeepNet | HR | BC | LR |
|---|---|---|---|---|---|---|
| FRGC V 2.0 | Exp. 1 | 94.11 | 97.62 | 96.12 | 93.63 | 99.45 |
| | Exp. 2 | 95.10 | 99.54 | 98.31 | 97.27 | 100 |
| | Exp. 4 | 96.21 | 98.33 | 97.23 | 95.45 | 97 |
| UFI | CI | 92.23 | 93.60 | 92.17 | 95.54 | 97.34 |
| | LI | 93.12 | 95.29 | 96.23 | 96.11 | 88.88 |
| SDUMLA-HMT | 95.13 | 98.89 | 98.89 | 96.42 | 100 |

采用最高排序的方法来比较所提多特征生物识别脸部识别系统与其它现有方法的性能，以衡量其与其他融合方法相比，在利用分类器有效性优势以及消除最终排名列表中主体之间平局方面的效率。表 4.6 比较了在使用 `FRGC V 2.0` 数据集进行三次实验时，所提方法与当前最先进的脸部识别方法的 Rank-1 识别率。

尽管某些方法（如部分最小二乘法 (`PLS`) 方法 [65]）在实验 1 和 2 中获得了略高的识别率，它们在 `FRGC V 2.0` 数据集的其余实验中获得的结果较差。此外，`FaceDeepNet` 系统和通过所提方法获得的融合结果在 `FRGC V 2.0` 数据集的所有实验中均实现了更高的识别率。表 4.7 比较了所提方法与当前最先进的脸部识别方法的 Rank-1 识别率。

## 表 4.6

所提多特征生物识别脸部识别系统与 `FRGC V 2.0` 数据集上最先进方法的对比

| 方法 | Exp.1 | Exp.2 | Exp.4 |
|---|---|---|---|
| Deep C2D-CNN [67] | - | - | 97.86 |
| PLS [65] | 97.5 | 99.4 | 78.2 |
| LBP+DBM [68] | - | - | 63.7 |
| FDT-DRBM | 94.11 | 95.10 | 96.21 |
| FaceDeepNet | 97.62 | 99.54 | 98.33 |
| 融合 (LR) | 99.45 | 100 | 100 |

## 表 4.7

所提多特征生物识别系统与 `UFI` 数据集上最先进方法的对比

| 方法 | CI | LI |
|---|---|---|
| E-LBP [69] | 65.28 | - |
| MGM+LBP [70] | 51.07 | - |
| POEMMask-50 [71] | 68.93 | - |
| M-BNCC [72] | - | 74.55 |
| LBPHIS [62] | 55.04 | 31.89 |
| LDPHIS [62] | 50.25 | 29.43 |
| POEMHIS [62] | 67.11 | 33.96 |
| FS-LBP [62] | 63.31 | 43.21 |
| FDT-DRBM | 92.23 | 93.12 |
| FaceDeepNet | 93.60 | 95.29 |
| 融合 (LR) | 97.34 | 98.88 |

使用 `UFI` 数据集的这两个划分部分。可以看出，`FDT-DRBM` 方法和 `FaceDeepNet` 系统在 `FRGC V 2.0` 数据集的所有实验中均实现了更高的识别率。

## 表 4.8

所提多特征生物识别系统与 `SDUMLA-HMT` 数据集上最先进方法的对比

| 方法 | 准确率 |
|---|---|
| MLP [66] | 93.35 |
| CLVQ [66] | 95.54 |
| CRBF [66] | 92.25 |
| FDT-DRBM | 95.13 |
| FaceDeepNet | 98.89 |
| 融合 (LR) | 100 |

在 `SDUMLA-HMT` 数据集上。可以看出，`FDT-DRBM` 方法和 `FaceDeepNet` 系统在 `FRGC V 2.0` 数据集的所有实验中均实现了更高的识别率。

## 4.5 脸部验证实验

在本节中，所提系统在脸部验证任务上进行了评估。尽管某些方法在实验 1 和 2 中获得了略高的识别率，它们在 `FRGC V 2.0` 数据集的其余实验中获得的结果较差。此外，`FaceDeepNet` 系统和通过所提方法获得的融合结果在 `FRGC V 2.0` 数据集的所有实验中均实现了更高的识别率。

所提 `FDT-DRBM` 方法在 `LFW` 数据集上与当前最先进的方法进行了对比，例如 `Curvet-Fractal` [7]、`DDML` [34]、`LBP`、`Gabor` [74] 以及 `MSBSIF-SIEDA` [75]，使用了相同的评估协议（例如 `Restricted`），如表 4.10 所示。可以看出 `Curvet-Fractal` [7] 取得了略高的识别率，但所提的 `FDT-DRBM` 方法能够在其他最先进的脸部验证结果中取得积极的结果。

# 多生物识别脸部识别系统

## 表 4.9

使用不同得分融合方法在 `LFW` 数据集上提出的脸部识别方法的的性能对比

| FDT-DRBM | FaceDeepNet | SR | WSR | PR | Max | Min |
|---|---|---|---|---|---|---|
| 0.9542 ± 0.0192 | 0.9899 ± 0.0210 | 0.9918 ± 0.0110 | 0.9992 ± 0.0232 | 0.9837 ± 0.0164 | 0.9758 ± 0.0177 | 0.9880 ± 0.0211 |

![](img/be8864cedd9a2fb32f3521f7cd37aa21_135_0.png)

图 4.13 使用不同分数级融合方法的 ROC 曲线。

其中使用了包含大量训练样本（>100K）的多样化数据集。如表 4.10 所示，与 `MDFR Framework` [7] 使用 `FaceDeepNet` 系统以及整个多生物脸部识别系统（例如使用加权和规则 `WSR`）所报告的结果相比，准确率分别提高了 0.16% 和 1.09%。这些鼓舞的结果证明了所提脸部识别方法良好的泛化能力，以及在现实应用中部署的可性。

## 4.6 结论

在本章中，提出了一种基于多模态深度学习的名为 `FDT-DRBM` 的多生物脸部识别方法。该方法基于整合分形维度和 `DRBM` 分类器的优点，具体取决于

## 表 4.10

在不同评估协议下，`LFW` 数据集上提出的方法与最先进方法的性能对比

| 方法 | 准确率 ($\mu \pm \sigma_S$) | 协议 |
|---|---|---|
| DeepFace [31] | 0.9735 \pm 0.0025 | 无限制 |
| DeepID [76] | 0.9745 \pm 0.0026 | 无限制 |
| ConvNet-RBM[77] | 0.9252 \pm 0.0038 | 无限制 |
| VGG Net [79] | 98.95 | 无限制 |
| ConvolutionalDBN [78] | 0.8777 \pm 0.0140 | 限制 |
| DDML [34] | 0.9068 \pm 0.0141 | 限制 |
| VMRS [80] | 0.9110 \pm 0.0059 | 限制 |
| HPEN+HD-LBP+ DDML [74] | 0.9257 \pm 0.0036 | 限制 |
| HPEN+HD-Gabor+ DDML [74] | 0.9280 \pm 0.0047 | 限制 |
| Sub-MSL+Hybrid+LFW3D [81] | 0.9165 \pm 0.0104 | 限制 |
| MSBIEF-SIEDA [75] | 0.9463 \pm 0.0095 | 限制 |
| 3-layers DBN [71] | 0.9353 \pm 0.0165 | 限制 |
| Curvelet-Fractal [7] | 0.9622 \pm 0.0272 | 限制 |
| MDFR Framework [71] | 0.9883 \pm 0.0121 | 限制 |
| FDT-DRBM | **0.9542 \pm 0.0192** | 限制 |
| FaceDeepNet | **0.9899 \pm 0.0210** | 限制 |
| Fusion (WSR) | **0.9992 \pm 0.0232** | 限制 |

分别提取环境条件下表面纹理的糙度和波动，并高效地对输入和目标类别的联合分布进行建模。此外，提出了一种 `FaceDeepNet` 系统，通过在从 `FDT-DRBM` 方法获得的局部特征表示之上训练两种判别性深度学习方法（例如 `CNN` 和 `DBN`），来学习额外且互补的面部特征表示。所提方法在四个在面部表情、光照条件、姿态、噪声等方面具有高度多样性的大型无限制数据集（例如 `SDMLA-HT`、`FRGC V 2.0`、`UFL` 和 `LFW`）上进行了测试。开展了大量的实验，通过在所有使用的数据集上应用所提的 `FaceDeepNet` 系统和整个多生物识别系统（例如使用 `WSR`），在脸部识别和验证任务中均实现了新的领先准确率。所得结果证明了 `FDT-DRBM` 方法的可靠性和效率，其与当前最先进的脸部识别方法（例如 `CLVQ`、`Curvelet-Fractal`、`DeepID` 等）相比具有竞争力的结果。对于未来的工作，有必要使用更大的数据集（包含在更具挑战性的条件下更多人脸图像）进一步验证所提多生物识别系统的有效性和可靠性。

## 参考文献

1. K. Nandakumar, A. Ross, and A. K. Jain, "Introduction to biometrics," in Appearance of 15th European Signal Processing Conference (EUSIP) (Poznan, Poland), 2007, pp. 271–292.

2. A. Leste, "Identification system based on multi-model approach," International Journal of Electronics and Computer Engineering, vol. 3, no. 5, 2278–2209.

3. M. Leste and A. Leste, "Multi-view face detection based on kernel analysis and learning," International Journal on Soft Computing (IJSC), vol. 2, no. 2, 1–13.

4. A. Leste, R. Q., and S. I., "A fast and accurate localization technique for healthcare security," IEEE International Conference on Computer and Information Technology: Ubiquitous Computing; Pervasive Intelligence and Computing, 2015.

5. R. Rafri and H. Ansari, "A survey of face recognition techniques," Journal of Information Systems, vol. 5, no. 2.

6. （此处省略后续参考文献翻译，保持格式一致）

# 多重生物识别脸部识别系统

37. M. Kostinger, M. Wohlhart, P. M. Roth, and H. Bischof, “基于特征值约束的大规模度量学习，”发表于 IEEE Society Conference on Vision and Pattern Recognition, 2012, pp. 2288–2295.

38. H. V. Nguyen and L. Bai, “用于脸验证的余弦相似度度量，”发表于 Asian Conference on Computer Vision, Springer Berlin Heidelberg, 2011, pp. 1–12.

39. C. Peng, X. Wang, N. Wang, and J. Li, “异构脸部识别的图形表示，”IEEE Transactions on Pattern Analysis and Intelligence, vol. 30, no. 2, pp. 301–312.

40. C. Peng, N. Wang, J. Li, and X. Bao, “DLFace: 用于跨模态脸部识别的深度局部描述符，”Pattern Recognition, vol. 90, pp. 161–171, 2019.

41. C. Peng, X. Bao, S. Member, and D. Tao, “基于多表示的脸部素描，”IEEE Transactions on Neural Networks and Learning, vol. 27, no. 11, pp. 2201–2215.

42. Y. Gao, J. Ma, and A. Lullie, “无标签样本脸部识别的半监督稀疏表示，”IEEE Transactions on Image Processing, vol. 26, no. 5, pp. 2545–2560.

43. M. Hassaballah and S. Aly, “脸部识别：成就与未来方向，”Computer Vision, vol. 9, no. 4, pp. 614–626, 2005.

44. R. Lopes and N. Berthen, “分形与多分形分析：综述，”Medical Image Analysis, vol. 13, no. 4, pp. 634–649, 2009.

45. B. Mandelbrot, 《自然的分形几何学》。美国国会图书馆出版目录数据，美国，1983.

46. B. Mandelbrot, “自相似性与分形维，”Physica Scripta, vol. 32, pp. 257–260.

47. K. Lin, K. Lam, and W. Si, “利用分形维度的人眼，”发表于 International Conference on Image Processing, 2001, pp. 1079–1082.

48. M. F. Farhan, L. E. George, and A. T. Hussein, “利用分形几何的指纹识别，”International Journal of Advanced Research in Computer Science and Software Engineering, vol. 4, no. 1, pp. 52–61.

49. G. Hinton, “受限玻尔兹机训练的实用指南：受限玻尔兹机训练的指南，”Neural Networks: Tricks of the Trade. Springer, Berlin, Heidelberg, 2010, pp. 599–618.
