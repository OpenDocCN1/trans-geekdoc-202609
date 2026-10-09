
在文本检测方面具有明显的优势。与原始的 EAST 算法相比，改进后的结构使召回率 R 和精确率 P 分别提高了 8% 和 6%，F 值提高了 7%。因此，与其他改进的算法和结构相比，所提出的优化结构具有明显的性能优势。

**表 1.** 几种算法的 R、P 和 F 值评估指标对比结果。

| 算法名称 | R (%) | P (%) | F (%) |
| :--- | :--- | :--- | :--- |
| EAST + VGG16 | 72.8 | 80.5 | 75.4 |
| Seglink [25] | 76.8 | 80.5 | 75 |
| CTPN + VGG16 [26] | 51.6 | 74.2 | 60.9 |
| EAST + resnet50 + BLSTM [27] | 78.07 | 85.10 | 81.64 |
| EAST + PVANET2 × MS [28] | 77.23 | 84.64 | 80.77 |
| TextSne [29] | 83.20 | 73.90 | 78.72 |
| RPN [30] | 86.00 | 70.00 | 77.00 |
| 本文算法 | 80.02 | 86.04 | 82.93 |

# 5. 结论

本文提出了一种用于文本检测的改进 EAST 算法。通过采用混合注意力机制方法并引入轻量级特征提取神经网络结构，可以处理传统网络结构中存在的文本定位复杂、检测不准确以及计算量大的问题。本文方法可以减少计算量，增加网络层数，并提高网络准确性。同时，改进的混合注意力机制与混合金字塔模型相结合，解决了 EAST 算法中对小感受域文本关注不足以及特征提取不充分的问题。此外，在特征融合后还增加了 BLSTM 网络结构，以有效整合文本区域的序列特征，使文本检测更加鲁棒。测试结果表明，本文提出的改进 EAST 算法在自然场景和复杂场景中的文本区域检测性能优于其他现有方法，并显著减少了参数量计算量。

因此，本文提出的改进算法确实是一种优秀的算法。然而，本研究存在三个局限性。首先，在测试算法的过程中，本研究未发现针对改进算法的更优训练方法，本文采用的训练方法仍然基于传统网络模型，尽管这种训练方法在复杂背景下对文本识别精度也能起到一定作用。但是，如果我们能找到一种与轻量级网络更兼容的训练模型，将有助于进一步提高识别精度，并改善小感受野文本关注不足和特征提取不充分的问题。其次，通过大量实验测试得出结论，本文提出的 EAST 算法在识别精度方面与其他算法相比有所提升，且能减少计算量。然而，需要构建定量分析模型的理论来衡量改进算法的计算复杂度。未来，我们将进一步建立定量分析模型的计算器理论并验证其有效性。最后，在本文的实验测试中，使用了专门的文本检测与识别数据集（ICDAR2015）。虽然该数据集广泛适用于常规文本的训练和检测，但它也存在背景场景单一不足的缺点。因此，鉴于本文研究的是复杂背景下的文本识别领域，有必要收集和整理更多复杂场景的文本数据集，为复杂场景下的文本检测和识别提供更可靠、更丰富的模型训练资源。

作者贡献：概念化，M.L.；方法论，M.L. 和 B.L.；软件，B.L.；验证，B.L. 和 W.Z.；形式分析，M.L.；调查，M.L. 和 B.L.；资源，M.L. 和 B.L.；数据整理，B.L.；写作—初稿撰写，M.L. 和 B.L.；写作—审阅与编辑，M.L. 和 B.L.；可视化，B.L. 和 W.Z.；监督，M.L.。所有作者均已阅读并同意已出版版本的稿件。

资助：本研究未获得外部资金资助。

数据可用性声明：本研究中呈现的数据可向通讯作者索取。

利益冲突声明：作者声明无利益冲突。

# 缩写

| 简称 | 全称 |
|---|---|
| CBAM | 卷积块注意力模块 (Convolution Block Attention Module) |
| EAST | 高效且准确的场景文本 (Efficient and Accurate Scene Text) |
| NMS | 非极大值抑制 (non-maximum suppression) |
| FCN | 全卷积网络 (full convolution network) |
| LNMS | 局部感知非极大值抑制 (local perception non-maximum suppression) |
| SE | 挤压-激励 (squeeze-and-excitation) |
| HS | 硬 Sigmoid (h-swish) |
| CAM | 通道注意力模块 (Channel Attention Module) |
| SAM | 空间注意力模块 (Spatial Attention Module) |
| BLSTM | 双向长短期记忆 (bidirectional long short-term memory) |
| ICDAR | 国际文档分析与识别会议 (International Conference on Document Analysis and Recognition) |
| Faster-RCNN | 快速区域卷积神经网络 (Faster-Region-Convolutional Neural Network) |
| CNN | 卷积神经网络 (Convolutional Neural Network) |
| SSD | 单发多框检测器 (Single Shot MultiBoxDetector) |
| CTPN | 连接主义文本候选网络 (Connectivist Text Proposal Network) |
| VGG | 视觉几何组 (Visual Geometry Group) |
| ReLU | 修正线性单元 (Rectified Linear Unit) |
| ResNet | 深度残差网络 (Deep residual network) |
| IoU | 交并比 (Intersection over Union) |
| LSTM | 长短期记忆 (Long Short Term Memory) |
| ADAM | 自适应矩估计 (Adaptive Moment) |
| RRPN | 旋转区域候选网络 (Rotation Region Proposal Network) |

# 附录 A

![](img/e4200cc4308edaf8913e513b0f96dbb6_568_0.png)

![](img/e4200cc4308edaf8913e513b0f96dbb6_569_0.png)

![](img/e4200cc4308edaf8913e513b0f96dbb6_569_1.png)

图 A2. 标准可分离卷积和深度可分离卷积。

![](img/e4200cc4308edaf8913e513b0f96dbb6_569_2.png)

图 A3. SE 模块结构示意图。

![](img/e4200cc4308edaf8913e513b0f96dbb6_570_0.png)

**图 A4.** 空间注意力机制示意图。

# 参考文献

1. Ren, S.; He, K.; Girshick, R.; Jian, S. Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks. *IEEE Trans. Pattern Anal. Mach. Intell.* **2017**, *39*, 1137–1149. [CrossRef] [PubMed]
2. Hwang, Y.; Lee, J.G.; Moon, U.C.; Park, H.H. SSD-TSEFFM: New SSD Using Trident Feature and Squeeze and Extraction Feature Fusion. *Sensors* **2020**, *20*, 3630. [CrossRef] [PubMed]
3. Li, X.B.; Chen, L. Face detection in natural scenes based on improved Faster-RCNN. *J. Comput. Eng. Appl.* **2021**, *47*, 210–216.
4. Yun, N.; Lee, S. Analysis of effectiveness of tsunami evacuation principles in the 2011 Great East Japan tsunami by using text mining. *Multimed. Tools Appl.* **2016**, *75*, 12955–12966. [CrossRef]
5. Huang, X. Automatic video scene text detection based on saliency edge map. *Multimed. Tools Appl.* **2019**, *78*, 34819–34838. [CrossRef]
6. Zhou, B.; Liu, Y.Q.; Min, Z.; Jin, Y.; Ma, S.P. Retrieval effectiveness analysis for anchor texts. *J. Softw.* **2011**, *22*, 1714–1724. [CrossRef]
7. Sun, J.; He, X.; Wu, M.; Wu, X.; Lu, B. Detection of tomato organs based on convolutional neural network under the overlap and occlusion backgrounds. *Mach. Vis.* **2020**, *31*, 15–22. [CrossRef]
8. Chang, L.; Zhang, S.; Du, H.; You, Z.; Wang, S. Position-aware lightweight object detectors with depthwise separable convolutions. *J. Real-Time Image Processing* **2020**, *34*, 857–871. [CrossRef]
9. Pang, Y.; Zhang, Y.J.; Lin, L.Z.; Cai, Y.Q. Improved scene text detection in any direction based on EAST. *J. Chongqing Univ. Posts Telecommun.* **2021**, *56*, 868–876.
10. Yang, B.; Du, X.Y. Natural scene text localization algorithm based on improved EAST. *J. Comput. Eng. Appl.* **2019**, *55*, 161–165.
11. Qiao, T.; Su, H.S.; Liu, G.H.; Wang, M. Object detection algorithm based on improved feature extraction network. *J. Adv. Lasers Optoelectron.* **2019**, *56*, 134–139.
12. Saha, S.; Chakraborty, N.; Kundu, S.; Paul, S.; Mollah, A.F.; Basu, S.; Sarkar, R. Multi-lingual scene text detection and language identification. *Pattern Recognit. Lett.* **2020**, *138*, 16–22. [CrossRef]
13. Wang, X.; Xue, F.; Wang, W.; Liu, A. A network model of speaker identification with new feature extraction ways and asymmetric BLSTM. *Neurocomputing* **2020**, *403*, 167–181. [CrossRef]
14. Li, X.Q.; Liu, J.; Zhang, S.W.; Zhang, G.X.; Zheng, Y. Single shot multi-oriented text detection based on local and non-local features. *Int. J. Doc. Anal. Recognit.* **2020**, *23*, 241–252. [CrossRef]
15. Namici, F.; Ghods, V.; Khalesi, H. Hasan Khalesi Scene text detection using enhanced Extremal region and convolutional neural network. *Multimed. Tools Appl.* **2020**, *79*, 27137–27159. [CrossRef]
16. Arkunkar, P.; Shantharajah, S.P.; Geetha, M. Improved canny detection construction for processing and segmentation text from the images. *Clust. Comput.* **2018**, *22*, 7015–7021. [CrossRef]
17. Wang, D.F.; Chen, C.B.; Ma, T.L.; Li, C.H.; Miao, C.Y. YOLOv3 pedestrian detection algorithm based on depth-separable convolution. *J. Comput. Appl. Softw.* **2020**, *37*, 218–223.
18. Liu, K.; Pan, G.Y.; Zheng, D.G.; Gu, J.J.; Meng, C.Y. An aviation forensics target detection algorithm based on RetinaNet and SE fusion. *J. Mod. Def. Technol.* **2022**, *50*, 25–32.
19. Zhao, L.L.; Wang, X.Y.; Zang, Y.; Zhang, M.Y. Research on vehicle target detection technology based on YOLOv5 and SENet. *J. J. Graphics.* **2022**, *4038*, 1–8.

