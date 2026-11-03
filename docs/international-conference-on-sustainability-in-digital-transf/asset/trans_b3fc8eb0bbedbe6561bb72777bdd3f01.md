
模型预测控制（`MPC`）是一种用于优化功率分流混合动力汽车燃油效率的方法。在初始探索阶段，构建了二次代价函数，并采用 `MPC` 技术将其应用于具有动态变量的时间变化线性系统。初步研究涵盖了这两个组成部分。其后，代价函数被划分为两个不同的组成部分，即代价至终点和阶段代价，从而实现燃油资源的更高效利用。代价至终点可以通过考虑电池的荷电状态（`SOC`）来确定。这提供了实际值的可靠近似。在非线性环境中使用 `MPC` 有助于对所讨论问题进行系统化和可预测的求解。这一现象可归因于所考虑的相对较短的时间范围。这一成就的实现得益于问题区域维度的减少。如数据所示，采用非线性环境中的 `MPC` 方法可以替代替代性商业线性控制器的使用。这种调整已证明燃油效率得到了大幅提升。在通常采用线性语言的情况下，这一现象并不会发生。

## 参考文献

1.  [Chan, C. C.](#ch7.xhtml#R_ref7_1) (2002). 电动和混合动力汽车的最新技术进展。Proceedings of the IEEE, 90(2), 247–275.

2.  [Malikopoulos, A. A.](#ch7.xhtml#R_ref7_2) (2014). 混合动力电动汽车的监督功率管理控制算法：综述。IEEE Transactions on Intelligent Transportation Systems, 15(5), 1869–1885.

3.  [Sharma, A., Sharma, K., Islam, A., and Roy, D.](#ch7.xhtml#R_ref7_3) (2020). 自动机器人电弧焊接工艺中焊接参数的影响。Materials Today: Proceedings, 26, 2363–2367.

4.  [Salmasi, F. R.](#ch7.xhtml#R_ref7_4) (2007). 混合动力电动汽车的控制策略：演变、分类、比较及未来趋势。IEEE Transactions on Vehicular Technology, 56(5), 2393–2404.

5.  [Chaturvedi, R., Islam, A., and Sharma, K.](#ch7.xhtml#R_ref7_5) (2021). 相变材料在太阳能热储存中应用的综述。Materials Today: Proceedings, 43, 293–297.

6.  [Paganelli, G., Delprat, S., Guerra, T. M., Rimaux, J., and Santin, J. J.](#ch7.xhtml#R_ref7_6) (2002). 并联混合动力总成的等效油耗最小化策略。In Vehicular Technology Conference. IEEE 55th Vehicular Technology Conference. VTC Spring 2002 (Cat. No. 02CH37367), (Vol. 4, pp. 2076–2081), IEEE, 2002.

7.  [Kumar, P., Singh, P. K., Nagar, S., Sharma, K., and Saraswat, M.](#ch7.xhtml#R_ref7_7) (2021). 功能化石墨烯不同浓度对热能储存系统充电时间减少的影响。Materials Today: Proceedings, 44, 146–152.

8.  [Gu, B., and Rizzoni, G.](#ch7.xhtml#R_ref7_8) (2006). 基于驾驶模式识别的混合动力电动汽车能量管理自适应算法。In ASME International Mechanical Engineering Congress and Exposition, (Vol. 47683, pp. 249–258).

9.  [Singh, P. K., Singh, P. K., Sharma, K., and Saraswat, M.](#ch7.xhtml#R_ref7_9) (2020). 超声参数对原位胺功能化多层石墨烯/环氧纳米复合材料力学性能的影响。Journal of Scientific and Industrial Research, 79(11), 985–989.

10.  [Borhan, H. A., Vahidi, A., Phillips, A. M., Kuang, M. L., and Kolmanovsky, I. V.](#ch7.xhtml#R_ref7_10) (2009). 功率分流混合动力电动汽车的预测能量管理。In 2009 American Control Conference, (pp. 3970–3976). IEEE, 2009.

11.  [Borhan, H., Vahidi, A., Phillips, A. M., Kuang, M. L., Kolmanovsky, I. V., and Di Cairano, S.](#ch7.xhtml#R_ref7_11) (2011). MPC-based energy management of a power-split hybrid electric vehicle. IEEE Transactions on Control Systems Technology, 20(3), 593–603.

12.  [Shukla, M. K., and Sharma, K.](#ch7.xhtml#R_ref7_12) (2019). 碳纳米填料对环氧基纳米复合材料力学和界面性能的影响：综述。Polymer Science, Series A, 61, 439–460.

13.  [Mousavi, M. A., Heshmati, Z., and Moshiri, B.](#ch7.xhtml#R_ref7_13) (2013). LTV-MPC based path planning of an autonomous vehicle via convex optimization. In 21st Iranian Conference on Electrical Engineering (ICEE), (pp. 1–7), IEEE, 2013.

14.  [Kim, N., Cha, S., and Peng, H.](#ch7.xhtml#R_ref7_14) (2010). 基于庞特里亚金最小值原理的混合动力电动汽车最优控制。IEEE Transactions on Control Systems Technology, 19(5), 1279–1287.

15.  [Sharma, K., and Shukla, M.](#ch7.xhtml#R_ref7_15) (2014). 三相碳纤维胺功能化碳纳米管环氧复合材料：加工、表征和多尺度建模。Journal of Nanomaterials, 2014, 2–2.

16.  [Sciarretta, A., and Guzzella, L.](#ch7.xhtml#R_ref7_16) (2007). 混合动力电动汽车控制。IEEE Control Systems Magazine, 27(2), 60–70.

17.  [Jinquan, G., Hongwen, H., Jiankun, P., and Nana, Z.](#ch7.xhtml#R_ref7_17) (2019). 插电式混合动力电动汽车中一种新颖的基于 MPC 的自适应能量管理策略。Energy, 175, 378–392.

# 8 并联混合动力电动汽车的控制参数优化

Manish Saraswat^([⁷](#fn7))

DOI: [10.1201/9781003534136-8](https://dx.doi.org/10.1201/9781003534136-8)

## Abstract

混合动力电动汽车（`HEV`）的重要控制参数为荷电状态（`SOC`）的下限和上限。车辆的该 `SOC` 直接影响经济性和排放率。在本工作中，并联 `HEV` 使用 `ADVISOR` 进行建模。为测试相同设计的驾驶循环的排放性能和燃油经济性，采用了不同的 `SOC` 限值。借助仿真结果，我们将能够确定 `SOC` 的最佳上限和下限，使车辆实现最佳燃油经济性和排放性能。仿真采用四条不同曲线的重复速度剖面（驾驶循环）进行，即 `UDDS`、`ECE`、`FTP` 和 `HWFET`。针对这些不同的驾驶循环观察 `SOC` 和排放曲线，并将 `HC`、`CO` 和 `NOx` 的排放率（单位为 g/miles）结果制表。

**关键词：** `ADVISOR`, 驾驶循环, 排放性能, 混合动力电动汽车, `SOC`

## Introduction

混合动力电动汽车提供额外的灵活性以改善燃油经济性和排放 [[1](#ch8.xhtml#ref8_1)]。对于混合动力电动汽车（`HEV`），电气储能与电动机耦合，使得车辆能够高效运行。双功率路径可通过双向变换器的耦合实现，使得在低功率运行期间能够关闭发动机，并且可为此类车辆使用更高效且更小的发动机。这可以在保持车辆平均功率承载能力的同时实现 [[2](#ch8.xhtml#ref8_2), [3](#ch8.xhtml#ref8_3) and [4](#ch8.xhtml#ref8_4)]。在此过程中，电池或其他储能系统中的电能通过在发动机高效运行期间接受多余功率来维持。再生制动过程将动能以电能形式储存，也有助于为储能系统充电 [[5](#ch8.xhtml#ref8_5)]。

控制策略在保持 `HEV` 效率方面发挥着重要作用 [[6](#ch8.xhtml#ref8_6)]。早期控制和优化视角被用于研究 `HEV` 的控制策略。一些静态优化方法包括 [[7](#ch8.xhtml#ref8_7)]。

*   动态规划
*   序列二次规划
*   基线策略
*   基于规则的控制策略
*   模糊逻辑控制策略
*   模型预测控制策略
*   实时优化
