

购物已成为我们日常生活中的常见场景。基于数字孪生技术的交互式在线虚拟商店正在为人们带来沉浸式体验。通过增强现实（AR）或 VR 技术，人们可以了解产品的更多详细信息。随着物联网（IoT）和 5G 技术的发展，可以感知并反馈物理对象的状态，包括形状、大小、颜色等静态状态，以及位置、运输和姿态等动态状态。对于这个虚拟购物应用，能够实时展示商品这些特性的数字孪生技术及其关联的感知网络发挥着重要作用。为了更好地模拟顾客在线下购物过程中的选取动作，开发了一种柔性机械操纵器。为了匹配该操纵器的特性，操纵器上配备了若干基于 TENG 的传感器和热释电传感器，并辅以机器学习（ML）方法进行数据处理。基于该系统，已建立一家虚拟商店，为客户提供沉浸式人机交互环境（Sun 等人，2021 年）。

如图 48.4a 和 b 所示，这种由 3D 打印机制造的柔性机械操纵器由三个气动执行器组成。当执行器充气时，它们会同时变形，且弯曲角度在特定范围内与气压呈线性关系。该系统中的基于 TENG 的长度传感器（L-TENG）是一种单电极接触-分离式 TENG。覆有镍织物导电纺织品的齿轮作为运动部件。贴在铜电极上的 PTFE 薄膜作为固定部件。一条条带一端与齿轮固定，另一端固定在执行器的尖端。当柔性执行器充气时，齿轮在条带的驱动下旋转。在旋转过程中，齿轮的每个齿都作为 TENG 的摩擦电层。随着齿轮旋转，定子电极与地之间的电位差周期性地驱动定子电极与地之间的电荷流动并产生输出峰值。齿轮上每个齿与 PTFE 薄膜的接触-分离过程产生一个输出峰值。因此，气动手指的变形可以通过齿轮每两个齿之间的角度和输出峰值的数量来计算。触觉传感器基于接触-分离模式 TENG 阵列。该传感器附着在带有硅橡胶层的热塑性聚氨酯（TPU）基板上。沿气动手指的长边以一定间隔分布着三个短电极，并沿长边附着一个长电极。实验表明，三个短电极的电压比可以判断接触位置，因为输出电压与接触点到电极的距离成反比，而长电极的电压可以判断接触面积，因为接触面积会在电极上引入不同的电荷，从而导致接触面积与电压大小之间呈线性关系。为了更好地模拟现实购物过程，一种基于热释电的温度传感器也安装在柔性机械操纵器的尖端。

![](img/0dd4397c67b063014553965e4f1cf7e4_871_0.png)

图 48.4 基于 TENG 的 3D 扫描系统的工作原理。（a）现实世界与数字世界中多样物品的示意图。（b）3D 扫描的总体方案。（c）基于 TENG 的 3D 扫描系统的硬件设置。（d）基于 TENG 的 3D 扫描系统的电子系统。（经 Zhang, Jiayue, Shaoxin Li, Zihao Zhao, Yukui Gao, Di Liu, Jie Wang, and Zhong-Lin Wang，2022 年 授权转载，“用于数字孪生应用的高灵敏三维摩擦电传感器”（Highly sensitive three-dimensional triboelectric sensor for digital twin applications）一文，原载《纳米能源》第 97 卷，107198 页。）

对于气动夹爪的每个手指，都有一个由一个通道组成的 L-TENG 和一个由四个通道组成的 T-TENG。总共有 15 个通道用于抓握数据采集，包括接触面积、接触位置和弯曲角度信息。在抓握过程中，该传感器网络与柔性机械操纵器的出色柔性和兼容性使基于 TENG 的感知网络能够反馈 3D 感知空间。与单一传感器相比，该感知网络可以揭示更多信息，例如弯曲速度、碰撞振动、接触序列等随时间变化的其他特性。借助三层一维卷积神经网络（1D-CNN），即使在物体抓握角度变化的情况下，该系统也能实现高达 96.1% 的感知精度。基于这种智能操纵器，用户可以在虚拟商店中查看产品的更多详细信息（图 48.4d-f）。除了几何信息外，被抓握物体的温度还可以通过基于热释电的温度传感器进行感知。

未来，随着人工智能（AI）和物联网（IoT）技术的进步，该操纵器实现的虚拟购物过程可以同步在线客户的操作、真实机器人的运动以及感知反馈信息。这种具备自供电感知系统的 AI 支持操纵器充当数字孪生技术的一个应用，为智能工业、购物、教育和医疗保健提供了一种可能的解决方案。

## 参考文献

- Baytekin, Bilge, H. Tarik Baytekin, and Bartosz A. Grzybowski. 2012. “什么驱动接触带电表面上的化学反应？”《美国化学学会杂志》13（17）：7223–7226。
- Baytekin, H. Tarik, Bilge Baytekin, Thomas M. Hermans, Bartłomiej Kowalczyk, and Bartosz A. Grzybowski. 2013. “以自由基控制表面电荷作为保护电子电路的抗静电聚合物的原理。”《科学》341（6152）：1368–1371。
- Chen, Jun, Guang Zhu, Jin Yang, Qingshen Jing, Peng Bai, Weiqing Yang, Xuewei Qi, Yuanjie Su, and Zhong-Lin Wang. 2015. “用于自供电人机交互的个性化按键动态。”《ACS Nano》9（1）：105–116。
- Fan, Feng-Ru, Zhong-Qun Tian, and Zhong-Lin Wang. 2012. “柔性摩擦电发电机。”《纳米能源》1（2）：328–334。
- Guo, Hengyu, Xianjie Pu, Jie Chen, Yan Meng, Min-Hsin Yeh, Guanlin Liu, Qian Tang, Baodong Chen, Di Liu, and Song Qi. 2018. “一种用于社交机器人和助听器的高灵敏自供电摩擦电听觉传感器。”《科学机器人》3（20）：eaat2516。
- Jing, Qingshen, Guang Zhu, Peng Bai, Yannan Xie, Jun Chen, Ray P. S. Han, and Zhong-Lin Wang. 2014. “用于采集往复滑动运动能量的封装式摩擦电纳米发电机。”《ACS Nano》8（4）：3836–3842。
- Li, Zhaoling, Jun Chen, Hengyu Guo, Xing Fan, Zhen Wen, Min-Hsin Yeh, Chongwen Yu, Xia Cao, and Zhong-Lin Wang. 2016. “基于摩擦电气的废水中重金属离子自供电检测与去除。”《先进材料》28（15）：2983–2991。
- Lin, Long, Sihong Wang, Yannan Xie, Qingshen Jing, Simiao Niu, Youfan Hu, and Zhong-Lin Wang. 2013. “用于采集旋转机械能的分段结构盘式摩擦电纳米发电机。”《纳米快报》13（6）：2916–2923。
- Lin, Long, Yannan Xie, Sihong Wang, Wenzhuo Wu, Simiao Niu, Xiaonan Wen, and Zhong-Lin Wang. 2013. “用于自供电静态和动态压力检测及触觉成像的摩擦电主动传感器阵列。”《ACS Nano》7（9）：8266–8274。
- Lin, Shiquan, Liang Xu, Laipan Zhu, Xiangyu Chen, and Zhong-Lin Wang. 2019. “纳米尺度接触电起中的电子转移：光子激发效应。”《先进材料》31（27）：1901418。
- Lin, Zong-Hong, Gang Cheng, Ya Yang, Yu Sheng Zhou, Sangmin Lee, and Zhong Lin Wang. 2014. “作为主动式 UV 光探测器的摩擦电纳米发电机。”《先进功能材料》24（19）：2810–2816。
- Lin, Zong-Hong, Guang Zhu, Yu Sheng Zhou, Ya Yang, Peng Bai, Jun Chen, and Zhong-Lin Wang. 2013. “一种用于汞离子检测的自供电摩擦电纳米传感器。”《应用化学》125（19）：5169–5173。
- Lu, Cun Xin, Chang Bao Han, Guang Qin Gu, Jian Chen, Zhi Wei Yang, Tao Jiang, Chuai He, and Zhong Lin Wang. 2017. “温度对摩擦电纳米发电机性能的影响。”《先进工程材料》19（12）：1700275。
- Niu, Simiao, Ying Liu, Sihong Wang, Long Lin, Yu-Sheng Zhou, Youfan Hu, and Zhong-Lin Wang. 2013. “滑动模式摩擦电纳米发电机理论。”《先进材料》25（43）：6184–6193。
- Niu, Simiao, Ying Liu, Sihong Wang, Long Lin, Yu-Sheng Zhou, Youfan Hu, and Zhong-Lin Wang. 2014. “单电极摩擦电纳米发电机的理论研究与结构优化。”《先进功能材料》24（22）：3332–3340。
- Niu, Simiao, Sihong Wang, Long Lin, Ying Liu, Yu-Sheng Zhou, Youfan Hu, and Zhong-Lin Wang. 2013. “接触模式摩擦电纳米发电机作为有效电源的理论研究。”《能源与环境科学》6（12）：3576–3583。
- Niu, Simiao, Sihong Wang, Ying Liu, Yu Sheng Zhou, Long Lin, Youfan Hu, Ken C. Pradel, and Zhong Lin Wang. 2014. “光栅结构摩擦电纳米发电机的理论研究。”《能源与环境科学》7（7）：2339–2349。
- Sun, Zhongda, Mingu Zhu, Zixuan Zhang, Zhaocong Chen, Qiongfeng Shi, Xuechuan Shan, Raye Chen Hua Yeow, and Chengkuo Lee. 2021. “基于自供电传感器增强型柔性机械操纵器的 AIoT 使能虚拟商店应用。”《先进科学》8（14）：2100230。
- Wang, Sihong, Long Lin, and Zhong-Lin Wang. 2012. “基于纳米尺度摩擦电效应的能量转换，用于可持续为便携式电子设备供电。”《纳米快报》12（12）：6339–6346。
- Wang, Sihong, Long Lin, Yannan Xie, Qingshen Jing, Simiao Niu, and Zhong-Lin Wang. 2013. “基于面内电荷分离机制的滑动摩擦电纳米发电机。”《纳米快报》13（5）：2226–2233。
- Wang, Sihong, Yannan Xie, Simiao Niu, Long Lin, and Zhong-Lin Wang. 2014. “用于采集接触和非接触模式下移动物体或人体运动能量的独立式摩擦电层纳米发电机。”《先进材料》26（18）：2818–2824。
- Wang, Zhong-Lin. 2014. “摩擦电纳米发电机作为新型能源技术和自供电传感器——原理、问题与展望。”《法拉代讨论》176：447–458。
- Wang, Zhong-Lin. 2021. “从接触电起到摩擦电纳米发电机。”《物理学进展报告》84（9）：096502。
- Wang, Zhong-Lin, and Aurelia Chi Wang. 2019. “关于接触电起的起源。”《材料今天》30：34–51。
- Wu, Ying, Yunjian Su, Junjie Bai, Guang Zhu, Xiaoyun Zhang, Zhanolin Li, Yi Xiang, and Jingliang Shi. 2016. “一种用于 pH 检测的自供电摩擦电纳米传感器。”《纳米材料杂志》2016。vol. 2016，文章 ID 5121572，6 页，2016 年。https://doi.org/10.1155/2016/5121572

