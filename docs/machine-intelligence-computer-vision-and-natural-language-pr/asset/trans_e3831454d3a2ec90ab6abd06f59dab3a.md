

# 108 机器智能

![](img/f07153152e20646619066fcf6f1ecf5b_132_0.png)

图 5.10（续）

# 使用深度学习算法的运动图像目标检测 ■ 109

![](img/f07153152e20646619066fcf6f1ecf5b_133_0.png)

![](img/f07153152e20646619066fcf6f1ecf5b_133_1.png)

图 5.10（续）

# 110 机器智能

![](img/f07153152e20646619066fcf6f1ecf5b_134_0.png)

图 5.10（续）

## 5.5 结论

在本研究中，将五类物体作为检测对象，用于检测它们是否出现在用于交通环境中自动驾驶车辆的图像帧中。这项工作代表了使用 YOLO 架构的目标检测。YOLOv4 是最新且最快的算法，具有极高的真阳预测准确率。预测边界框的宽度、高度以及 IOU（交并比）方法被用于识别实时检测。在未来，可以对算法进行微调，并增加不同天气条件下的类别数量。在未来的未来的工作中，使用权重文件的网络架构将优于使用不同数量物体的预训练模型，并增加数据集中的类别数量。

## 参考文献

- 1. Taek-Hoon Jung, Benjamin Cates, In-Kyo Choi, Sang-Hon Lee, and Jong-Min Choi (2020) “基于多摄像头的自动拖拉机人员识别系统”。 http://doi.org/10.3390/designs40040054
- 2. https://towardsdatascience.com/a-comprehensive-guide-to-convolutional-neural-networks-the-el5-way-3db2hf16a453
- 3. https://towardsdatascience.com/r-cnn-far-rnn-far-rnn-yolo-detect-object-algorithms-36d53571365
- 4. Joseph Redmon and Ali Farhadi (2018) “Yolov3: 增量改进。” arXiv:1804.02767v1
- 5. https://towardsdatascience.com/review-yolov2-yolo9000-only-look-once-only-object-detection-7883d2b2a65
- 6. Yu-Cheng Fan, Yelamanda Chandra, Ting-Wei Chen, and Chun-Ju Huang (2021) “基于 LS-R-YOLOv4 神经网络的 LiDAR 实时目标检测”。Journal of Sensors, 1–11. doi:10.1190/2557562628
- 7. A. Bochovskiy, C. Y. Wang, and H. Y. Liao (2020) “Yolov4: 目标检测的最佳速度与准确性。”https://arxiv.org/abs/2004.10934
- 8. Qi Wu, Runzi Lin, HanYue, Hong Huang, Yun Yang, and Zhagang Yao (2020) “基于改进 YOLO 网络的场景下小目标检测研究”。IEEE Access. doi:10.1109/ACCESS.2020.296628
- 9. Tanvir Ahmed, Yinglong Ma, Muhammad Yahya, Bela Ahmad, Shah Nazir, Amin Haq, and Rahman Ali (2020) “使用改进 YOLO 神经网络的目标检测”。Scientific Programming. doi:10.1155/2020/8403262
- 10. J. Redmon, S. Divala, R. Girshick, and A. Farhadi (2016) “You Only Look Once: 统一实时目标检测”。发表于 2016 年 IEEE 计算机视觉与模式识别会议 (CVPR), 美国内华达州拉斯维加斯，页 779–788。
- 11. P. L. Chithra and Y. Gomathi (2021) “基于 YOLO3 的行人检测视频分析”。获取于：https://researchgate.com/publication/36321111
- 12. Upulie Handage and Kugananderthy Lakshini (2021) “使用 YOLO 进行实时目标检测：综述”。预印本. doi:10.1310/RG,2.2.24367.66723.
- 13. Heet Thakkar, Noopur Tambe, Sananjana Tambe, and Vaishali Gaidiane (2020) “使用 YOLO 和 SORT 通过检测进行跟踪”。International Journal of Scientific Science, Engineering and Information Technology, 3 月 20 日：224–229. doi:10.32628/CSEIT206256.
- 14. Shubham Pal and Pramila Chawan (2019) “使用深度学习进行实时目标检测：综述”。International Research Journal of Engineering.
- 15. Wenbo Lan, Jianwu Dang, Yangping Wang and Song Wang (2018) “基于 YOLO 模型的行人检测”。发表于 IEEE 机电与自动化国际会议，9781-53

# 第 6 章：使用机器学习算法检测视网膜病变

## 6.1 引言

糖尿病是一种代谢疾病，视网膜病变会导致视力损害。视网膜病变是导致失明的主要原因。根据世界健康组织的数据，视网膜病变影响了全球 8000 万人。美国疾病控制与预防中心（CDC）估计美国有 2900 万人患有此。视网膜病变影响了 3700 万人。视网膜病变在早期阶段是有效的。美国疾病控制与预防中心估计视网膜病变影响了 4500 万人。尽管如此，晚期糖尿病视网膜病变通常没有症状，需要进行密切监测。视网膜病变在早期阶段通过定期检查检查可以发现。糖尿病视网膜病变在不治疗的情况下会导致失明。非增殖性糖尿病视网膜病变表现为棉絮斑、微血管异常或浅表视网膜出血。即使如此，增殖性糖尿病视网膜病变（PDR）可能很长一段时间没有症状，需要密切监测。一种计算机辅助筛查系统使用机器学习分类器如 K 近邻 (kNN)、支持向量机 (SVM)、高斯混合模型 (GMM) 和 Adaboost 对病变与非病变进行分类分析。多种方法被用于视网膜病变检测和增殖性视网膜病变的诊断程序。本研究使用了不同光照和视角的眼底图像来生成视网膜病变的严重程度。Alazzam 等人（2021）的工作声称径基方法具有良好的诊断准确性，并可能用于视网膜病变。在机器学习和先进智能的支持下，糖尿病网站可以预测糖尿病和视网膜病变。

## 6.2 背景

### 6.2.1 增殖性视网膜病变

随着疾病进展，严重的非增殖性糖尿病视网膜病变进入高级或增殖阶段，此时血管会增生生长。视网膜缺氧导致脆弱的新血管沿视网膜生长。如果不及时治疗，这些新血管可能会出血，导致视力模糊并破坏视网膜。纤维血管增殖还导致牵引性视网膜脱离。新血管也可能生长到眼角引起新生性青光眼。非增殖性糖尿病视网膜病变表现为棉絮斑、微血管异常或浅表视网膜出血。图 6.1 显示了视网膜病变散射激光治疗的眼底图像。

