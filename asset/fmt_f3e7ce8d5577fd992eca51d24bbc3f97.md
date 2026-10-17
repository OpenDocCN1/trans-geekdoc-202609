
朴叶贝斯算法在三种算法中训练时间最短，这使其成为实时天气预测应用更具吸引力的选择。然而，它的性能指标（如 CA、F1 和精确率得分）低于其他算法，这可能会限制它在某些应用中的用处。

神经网络似乎具有较高的 AUC 分，这表明它在预测极端天气事件方面可能良好。然而，它的 CA、F1 和精确率得分低于随机森林算法，这可能会限制它在某些应用中的用处。

# 图表标题

![](img/a35f8e852e0ee65e528c95ad0821783b_311_0.png)

## 6 结论

天气预测是一项重要的研究领域，因为它对人类活动和环境有着影响。数据挖掘技术已广泛应用于天气预测，诸如朴叶贝斯、神经网络和随机森林等算法被常用。这些算法通过分析历史天气数据对未来的天气状况做出预测。

随机森林算法似乎是天气预测中表现最好的算法，与其他算法相比，其报告准确率、AUC 和 F1 分数较高。然而，这些算法的性能取决于特定的数据集和实现方式。总体而言，使用数据挖掘技术进行天气预测已显示出良好的前景，在该领域的持续努力可能会提高准确性和天气预测的可靠性。

# REFERENCES

- [1] Pushpa Mha and Kiran Kumar Patil: "On Crop and Weather Forecasting Based on Agriculture Related Statistical Data, International Journal of Innovative Research in Computer and Communication Engineering, vol 5, Issue 2

- [2] Jha S. K. and Acharya D. P., "Survey of Data Mining Techniques for Weather Forecasting," 2012 International Conference on Computing, Electronics and Electrical Technologies (ICCCET), 2012, pp. 108-113, doi:10.1109/ICCCET.2012.6203897

- [3] Liu R. and Gao Y. H., "Weather Prediction Using Artificial Networks: A Literature Review," 2016 IEEE International Conference on Automations and Mathematics (ICMA), Harbin, 2016, pp. 655-660, doi:10.1109/ICMA.2016

- [4] Kumar M. and Kumar N., "Prediction Using Decision Tree," 2019 9th International Conference on Computing, Communication and Network (ICCCNT),

- [5] Ahmed S. and Saif A., "Weather Forecasting Using Machine Learning," 2020 2nd International Conference on Computer Science and Applications (ICSEA), doi:10.1109/ICSEA

- [6] Liu C. and Y. Sun, "Predicting Precipitation Using Machine Learning: A Review," in IEEE Access, vol 9, pp.15520-15531

- [7] Rahim T. A., Hassanian A. B., and Hassanian E. E., "International Journal of Computer Science and Information, vol.12, no. 8, 2013.

- [8] Yarlagadda S. K., Raghuwanshi S. S., and Venkata V., "A Comparative Study of Data Mining Techniques for Weather Prediction," International Journal of Computer Applications, vol. 97, no. 12, 2014

- [9] Thomas S. and Paul, "Weather prediction using KNN and SVM," International Journal of Computer Applications, vol. 97, no. 12, 2014

- [10] Alghandi M. A. and Alzahani A. H., "Weather Prediction Using Artificial Networks: A Survey," International Journal of Computer Science and Information, vol. 16, no. 1, 2018

- [11] Khan S. S., Pathan S. S., and Zaidi T. A., "Prediction of Weather Using Machine Techniques," in Proceedings of 2017 International Conference on Computing, Communication and Control (ICCCA), pp. 1284-1288

- [12] Alharbi A. N. and Hassanian E. E., "A Hybrid Prediction for Weather Forecasting using Logic and Neural Networks," in Proceedings of 2015 International Conference on Computer, Communication and Control Technology (ICCCT), pp. 92-96

- [13] Shababy S. A., El-Dahab H., and Hassanian E. E., "Intelligent Weather Forecasting Using Logic and Neural Network," in Proceedings of 2014 IEEE 14th International Conference on Intelligent Systems and Applications (ISDA), pp. 510-515

- [14] Bhattacharjee S., S., and Datta D., "A Comparative Study on Prediction of Weather Parameters Using Decision Trees," in Proceedings of 2016 International Conference on Advances in Computing, Communications and Information (JACCI), pp. 1646-1651

- [15] Gupta N. and Moni M. K., "Performance Evaluation of Decision Tree and Artificial Neural Network in Weather Forecasting," in Proceedings of 2014 IEEE International Advanced Computing Conference (IACC), pp. 699–703

# 汽车盲区监控

Aditya Ranjan & Ravi Shankar Pandey

计算机科学与工程系，Birla Institute of Technology, Mesra,

Patna Campus India

ORCID ID: 0009-0004-2203-8349

**摘要：** 汽车盲区是指车辆周围在直视前方或通过侧镜、后视镜时无法看到的区域。本文介绍了一种使用安装摄像头的车辆盲区监控系统，旨在减少交通事故。我们首先描述了如何利用多个摄像头通过智能监控来检测盲区。然后，我们描述了盲区检测的重要性及其技术背景。本文提供了一种基于机器学习的均值算法（Mean shift algorithm）的盲区车辆检测算法。在该方法中，在视频的初始帧中为移动目标定义目标窗口，之后通过处理窗口内的数据将跟踪对象从背景中分离。随后会在屏幕上显示警报信息。

*关键词：* 均值算法、图像处理、盲区检测

# 1 引言

随着科学技术的发展，距离感知和跟踪技术已应用于许多日常生活设施，以促进生活安全与便利。例如，如今的驾驶员对安全驾驶越来越感兴趣，汽车制造商也提出了许多安全系统。特别是如车道偏离警告、车辆后方辅助系统和盲区信息系统等碰撞警告技术正受到关注。特别是盲区信息系统，对安全驾驶贡献巨大，并获得了市场的认可。如上所述，盲区是驾驶员无法通过后视镜看到的区域。盲区信息系统通过在车辆两侧安装视觉摄像头来捕获盲区，并在驾驶员换道时提醒其注意来车车辆。目前需要一种利用盲区信息系统测量接近车辆距离的技术。雷达是市场上的另一种技术。雷达使用声波测距、红外雷达等检测距离。某些雷达可以检测物体的形状。然而，车辆雷达的视野通常较窄且存在盲区。盲区覆盖与安装的车辆雷达数量相关。此外，汽车雷达的探测范围有限，难以检测在大范围内移动的物体。因此，需要一种检测盲区移动物体成像技术，让驾驶员可以通过显示设备看到所有盲区的图像。根据过去44年的调查，交通事故发生率呈上升趋势。预计道路死亡和受伤将成为全球死亡和受伤负担的第三大原因之一 [4]。世界上每2秒就会有一人死亡，每月56,047人，每年27,917人。南亚地区的道路死亡人数最高。道路交通数量持续稳定增长 [5]。根据2020年的调查，记录的总事故导致了1,311,714人生命损失和34,279人受伤。遗憾的是，道路交通事故受影响最严重的群体是18–45岁，占事故死亡总人数的约70%。在道路上不同车道间移动时，驾驶员很容易漏掉盲区内的车辆。这就是开发盲区监控系统的动力。为了有效减少事故数量，应安装多个摄像头并对准盲区，以便算法能够实时监控所有事件 [1]。通过这种方式，驾驶员不太可能忘记盲区导致交通事故。文献 [8] 提出了一种基于直接视觉的盲区警告系统（BSWS）。在本文中，我们主要关注开发一种基于直接视觉的盲区监控系统，用于检测车辆盲区内是否有车辆，如果该车进入盲区，则可以根据收集的数据进行发现，然后显示警报。所提工作的整体功能如图1所示。

![](img/a35f8e852e0ee65e528c95ad0821783b_314_0.png)

1. 所提工作的整体功能。

## 相关工作

最近，越来越多的汽车制造商（如宝马）开始为其汽车设计盲区监控系统，以防止盲区后方碰撞。有许多类型的盲区点警告系统，如雷达、超声波和摄像头检测系统 [6]。基于超声波的盲区检测系统（BDSS）成本较低但探测范围较短，车辆在使用时检测需要更多时间，其分辨率也相对较低 [2]。与其他系统相比，基于视觉的系统对周围环境更敏感，且随着横向分辨率增加，误报（报警）的数量会减少 [3]。BDSS 使用传感器和雷达来提高检测准确性。例如，Wong等人 [7] 提出了一种使用超声波传感器和安装在车辆上的四个摄像头的系统来收集周围环境的数据。该系统在处理完收集的数据后，可以预测是否会发生车辆碰撞。视觉摄像头大多安装在车辆两侧的翼子或后镜下方，用于检测移动物体 [12]。2012年，提出了一种基于视觉的系统 [13]。这是一种盲区监控系统，通过从车载摄像头捕获的图像中提取特征来检测车辆。这可以在驾驶员换道时帮助发现潜在的盲区并避免碰撞。Fernandez等人 [14] 认为，盲区监控可以通过基于被动传感器（如视频摄像头）或包括雷达和激光传感器在内的主动传感器系统提供支持。此外，盲区监控可以覆盖多个区域。2014年，Zheng等人 [15] 对地面进行了划分。Baek等人 [16] 执行了HOG分类器。与现有工作不同，本文提出了：

- (A) 使用四个摄像头进行数据增强
- (B) 用于盲区监控的均值算法
- (C) 盲区监控的性能结果

# 3 提出的方法

该算法基于安装在车辆左侧、右侧和后方的四个摄像采集的数据。观察周围环境可能会导致严重的碰撞 [9]。在该方法中，摄像头检测算法的目标区域，然后使用均值算法识别每个区域。该区域被表示为多边形，系统会提醒驾驶员。均值算法实际上是一种与聚类相关的更广泛的统计概念。算法在每个数据点上放置一个核，并汇总为核密度估计（KDE）。KDE具有对应于高密度数据密度的峰和谷。算法获取数据点的拷贝，并在迭代中将点略微移动到附近的KDE峰值。算法在点上移动直到其几乎不再移动。这有助于简化数据并使聚类更加清晰。图像可以分解为RGB色彩空间。当我使用KDE时，每个像素在峰值处都有蓝色。颜色之间的微妙淡变被消除了，随着点的移动，彩虹的每种颜色变得更加。结果是每个带更容易被计算机识别。这一过程用于图像分割。系统会持续监控物体，直到物体从多边形中移除，它不再构成碰撞威胁，从而系统移除警报信息。所提工作的流程图如图2所示。

![](img/a35f8e852e0ee65e528c95ad0821783b_315_0.png)

图2 所提工作的流程图。

## 4 结果

汽车盲区监控系统的目标是检测盲区并提醒驾驶员。这比任何方法都高效且速度更快。该算法被用于开发汽车盲区监控系统。为了获得工作模型，首先在车辆的前后各侧安装了四个摄像头。图3显示了安装在车辆上的摄像头位置及其覆盖区域。

![](img/a35f8e852e0ee65e528c95ad0821783b_316_0.png)

图 3. 车辆摄像头布局。

这些摄像头不断将视频流发送到运行在后端的 `Python` 程序。该程序对获取的视频流执行所需的图像处理任务，并应用所提算法监控盲区，同时生成错误消息以警告驾驶员注意潜在威胁。

图 4 显示了发生车辆检测定义的边界或区域。在通过摄像头和算法处理检测到盲区后，如果车辆进入盲区区域，所提算法将生成如图 5 所示的警告消息。

![](img/a35f8e852e0ee65e528c95ad0821783b_316_1.png)

图 4. 后视摄像的盲区。

![](img/a35f8e852e0ee65e528c95ad0821783b_316_2.png)

图 5. 生成碰撞危险警告信号。

实验不仅在白天进行，还在不同的驾驶条件下夜间进行。如下表 1 所示，该系统在所有测试条件下的表现均良好。

## 表 1. 盲区监控系统结果。

| 测试 | 白天 | 夜间 |
| :--- | :--- | :--- |
| 静止 65km/h | 通过 | 通过 |
| 超车 | 通过 | 通过 |

## 结论

本文介绍了一种利用安装在车内的摄像头视频，当车辆出现在其盲区时进行检测并发出警报的方法。使用均值偏移（Mean-shift）算法来实现盲区监控，由于不需要训练数据，该算法高效且快速。它直接处理采集的视频帧。在本文中，该算法分为两个部分：目标区域的定义，其次是均值偏移算法在目标跟踪中的应用。通过警告消息及时通知驾驶员潜在危险，持续确保车辆安全，并实现了其目的。

## 参考文献

- [1] W. Yan. Introduction to Intelligent Surveillance: Surveillance Data Capture, Transmission, and Analytics. Springer, 2017.
- [2] R. Mahapatra, K. Kumar, M. Khurana, and R. Rajajan. Ultra Sonic Sensor Based Blindspot Accident Prevention System. In IEEE International Conference on Advanced Computer Technology and Engineering, pages 992–995, 2008.
- [3] J. Alon, E. Vidal, A. Rotter, and M. Mullenberg. Lane-change Decision Aid System Based on Motion-Vehicle Tracking. IEEE Transactions on Computer Electronics, 57(2):2736, 2008.
- [4] Murray, C. J. and Lopez, A. D. (Eds.). (1996). The Global Burden of Disease: A Comprehensive Assessment of Mortality and Disability from Diseases, Injuries and Risks in 1990 and 2020. Boston: Harvard University Press.
- [5] Jayaprakash G Huber, Abu Waris, Mirzah Muhammad Nasir, Ajmal Khan, Road Traffic Accident Risk in India: Scientific Study from 1997 to 2020.
- [6] M. Ra, H. Jung, S. Bajaj, and W. Kim. Part-based Blind Vehicle Detection in Side-rectilinear Images for Blind-spot Detection. Expert Systems with Applications, 101:116–128, 2018.
- [7] C. Wang and O. Uidai. Intelligent Round Sensing Using Fuzzy Inference System. In IEEE Conference on Systems, pages 102–107, 2007.
