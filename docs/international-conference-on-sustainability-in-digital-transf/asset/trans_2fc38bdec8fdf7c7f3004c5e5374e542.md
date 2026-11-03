
# 建筑物中的占用检测

## PIR传感器
PIR传感器可能是建筑物中用于占用感知的最广泛使用的方法，尤其是在照明控制方面。尽管过去几年在建筑环境中占用感知方面已有大量研究，PIR传感器的技术局限性仍在阻碍新型占用感知解决方案的探索 \[[3](#ch55.xhtml#ref55_3)\]。建筑物中PIR感知的潜在用途被公认为受诸多基本局限性的限制。(a) PIR传感器只能提供粗略的二元数据（有人或无人）(b) PIR传感器需要从传感器位置到附近场所人员之间的直线视线 \[[4](#ch55.xhtml#ref55_4)\]；(c) PIR传感器需要持续运动才能正常工作（即占用者必须保持坐姿或传感器的视线被物体等障碍物遮挡）(d) PIR传感器会受不同热流的影响，如加热的咖啡/茶、电气设备以及供暖与通风系统。

## 二氧化碳传感器应用
空间中的CO₂量在有人时直接上升。研究表明，CO₂传感器是确定房间内人数的最佳环境传感器 \[[2](#ch55.xhtml#ref55_2)\]。它可以在85%到95%的时间内找到。Szczurek等人使用统计模式匹配提出了一种简单的方法来估计占用人数 \[[5](#ch55.xhtml#ref55_5)\]。首先，研究人员曾使用时间序列技术来测量和记录二氧化碳浓度。然后，他们使用模式匹配来研究时间序列框架与可用性之间的关系。

Dong \[[6](#ch55.xhtml#ref55_6)\]还使用了一组传感器（温度、湿度、CO₂和光）来判断房间内是否有人员。他观察到CO₂传感器数据对预测结果的影响最大。上图显示了传感器组合的两种最常见方式。第一种有一个摄像头、一个PIR传感器和一个CO₂传感器。房间内设置CO₂传感器以确定房间内的人数。占用者的座位上设置PIR传感器以检查人员是否在场。摄像头记录人员的实际移动情况。[图1](#ch55.xhtml#fig55_1)描绘了可用性检测中传感器的应用。这种融合有助于确定办公楼内是否会有多于一人。Arora等人展示了一个通过结合多种传感器数据来估计占用的系统，例如温度、湿度、CO₂、照明、PIR、门状态和能源利用 \[[7](#ch55.xhtml#ref55_7)\]。

![图55.1 使用传感器进行占用检测](images/fig55_1_C.jpg)

[图55.1 使用传感器进行占用检测](#ch55.xhtml#R_fig55_1)

使用环境传感器来猜测房间内的人数或种类更为困难。由于原始传感数据嘈杂且不适用于估计占用，研究旨在使用一种称为“特征工程”的技术，该技术常用于机器学习模型 \[[4](#ch55.xhtml#ref55_4)\]。特征工程的两个部分是特征提取和特征恢复。使用领域知识，特征提取是从原始数据中制作一些信息性表示的过程。特征选择是根据某些参数选择更具洞察力的特征的过程。Zhang等人使用统计建模结合CO₂和电力消耗数据来估计建筑物内的人数 \[[8](#ch55.xhtml#ref55_8)\]。首先，他们使用物理扩散模型从CO₂中提取一些特征。对于训练数据受限的占用预测，使用了两种模型的统计分布：HMM的最大后验概率MAP估计和多假设序贯概率比检验MSPRT。首先，他们取原始传感数据并提取一些相关属性。然后，使用信息增益理论来选择要使用的特征。使用所选特征和DT算法，最终确定了占用人数。在他们的另一项工作中，\[[9](#ch55.xhtml#ref55_9)\]，他们还添加了一个可测量房间声级的麦克风。使用了相同的特征选择方法。DT和RF学习算法被用于估计房间内的人数 \[[10](#ch55.xhtml#ref55_10)\]。[图2](#ch55.xhtml#fig55_2)显示了基于传感器的占用检测的工作方式。

![图55.2 基于传感器占用检测包含的步骤](images/fig55_2_C.jpg)

[图55.2 基于传感器占用检测包含的步骤](#ch55.xhtml#R_fig55_2)

## 结论
建筑物中的占用检测有助于控制照明和通风等事项，从而节省能源并保持建筑舒适。但由于其局限性，PIR和环境传感器在检测人员和收集数据时总会出错。通过提高占用预测的准确性，实际发生情况与预测之间的差异可以大幅减少。当使用CO₂传感器和摄像头记录数据时，数据的准确性很高。光线对摄像头的可见度有很大影响，但CO₂传感器可以弥补这一点。本文讨论了多种占用检测方法，主要使用红外和CO₂传感器。

## 参考文献
1.  [Wang, D., Federspiel, C. C., and Rubinstein, F.](#ch55.xhtml#R_ref55_1) (2005). Modeling occupancy in single person offices. Energy and Buildings, 37, 121–126.

2.  [Candanedo, L. M., Feldheim, V., and Deramaix, D.](#ch55.xhtml#R_ref55_2) (2017). A methodology based on hidden Markov models for occupancy detection and a case study in a low energy residential building. Energy and Buildings, 148, 327–341.

3.  [Sharma, A., Chaturvedi, R., Sharma, K., and Saraswat, M.](#ch55.xhtml#R_ref55_3) (2022). Force evaluation and machining parameter optimization in milling of aluminium burr composite based on response surface method. Advances in Materials and Processing Technologies, 8(4), 4073–4094.

4.  [Amayri, M., Arora, A., Ploix, S., Bandhyopadyay, S., Ngo, Q.-D., and Badarla, V. R.](#ch55.xhtml#R_ref55_4) (2016). Estimating occupancy in heterogeneous sensor environment. Energy and Buildings, 129, 46–58.

5.  [Chaturvedi, R., Sharma, A., Sharma, K., and Saraswat, M.](#ch55.xhtml#R_ref55_5) (2022). Tribological behaviour of multi-walled carbon nanotubes reinforced AA 7075 nano-composites. Advances in Materials and Processing Technologies, 8(4), 4743–4755.

6.  [Dong, B., Andrews, B., Lam, K. P., Höynck, M., Zhang, R., Chiou, Y. S., and Benitez, D.](#ch55.xhtml#R_ref55_6) (2010). An information technology enabled sustainability test-bed (ITEST) for occupancy detection through an environmental sensing network. Energy and Buildings, 42(7), 1038–1046.

7.  [Kumar, P., Singh, P. K., Nagar, S., Sharma, K., and Saraswat, M.](#ch55.xhtml#R_ref55_7) (2021). Effect of different concentration of functionalized graphene on charging time reduction in thermal energy storage system. Materials Today: Proceedings, 44, 146–152.

8.  [Liu, Z., Zhang, J., and Geng, L.](#ch55.xhtml#R_ref55_8) (2017). An intelligent building occupancy detection system based on sparse autoencoder. In IEEE Winter Applications of Computer Vision Workshops (WACVW), 2017, (pp. 17–22).

9.  [Chaturvedi, R., Islam, A., Singh, P. K., and Saraswat, M.](#ch55.xhtml#R_ref55_9) (202). Nanotechnology for advanced energy system: synthesis & performance characterization of nano-fuel. In AIP Conference Proceedings (Vol. 2721, No. 1). AIP Publishing.

10.  [Liu, H., and Motoda, H.](#ch55.xhtml#R_ref55_10) (199). Feature Extraction, Construction and Selection: A Data Mining Perspective, (Vol. 453), Springer Science & Business Media.

