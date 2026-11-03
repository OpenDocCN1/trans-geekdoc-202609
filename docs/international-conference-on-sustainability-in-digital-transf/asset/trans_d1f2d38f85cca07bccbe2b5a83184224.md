
# 60

[图 60.3 (a) 和 3(b) 显示模拟驱动循环的图](#ch60.xhtml#R_fig60_3)

车辆使用以下参数进行模拟，如下[表 60.1](#ch60.xhtml#tab60_1)所示 -

[表 60.1 车辆参数。](#ch60.xhtml#R_tab60_1)

| 车辆重量 || 15000 Kg |
| --- | --- |
| 电机额定值(功率) || 43 KW |
| --- | --- |
| 扭矩 || 200 nm |
| 发动机额定值 || 120 hp |
| 电池组 || VRLA |
| 电池容量 || 110 Ah |
| 端子电压 || 145 V |

模拟的一半针对 `SOC` 的下限执行，另一部分针对 `SOC` 的上限执行。由于 `SOC` 值过低或过高会损害电池，因此有必要保持 20 至 80 百分比的实际限制。我们为上限或终点形成组，运行单独的模拟，并尝试确定哪个组的 `soc` 范围最优。由于它取决于 `SOC` 的初始值，因此需要考虑的两个关键方面是发动机的运行程序和整体燃油使用量。

## 结论

为了使 `HEV` 有效运行，电动机与电能存储相连。为了提高燃油效率并减少排放，混合动力电动汽车提供了额外的灵活性。由于双向转换器的连接，提供了两条功率路径，从而可以在低功率运行期间切断发动机，并为这种车辆使用更小、更高效的发动机。这在保持车辆平均功率承载能力的同时是可行的。储能单元在电力需求较低时充电，在电力需求较高时放电。控制电续航里程和燃油经济性的部件是 `ESS`。`UDDS` 和 `HWFET` 是两条不同的曲线，其重复的速度曲线（驱动循环）用于运行模拟。为了优化部件的运行有效性，必须整体考虑系统。控制策略将采用主动方法实施。虽然其他技术不包括此额外要素，但该技术最大化运行效率以最大化燃油经济性。本研究提到了并联混合动力汽车的能力控制器作为提高燃油经济性的一种方式。已安装的旧功率控制器优化了操作，但没有利用全部潜力。

## 参考文献

1. [Schaltz, E., Khaligh, A., and Rasmussen, P. O.](#ch60.xhtml#R_ref60_1) (2009). 影响燃料电池混合动力汽车中电池/超电容器储能尺寸对电池寿命的影响。 IEEE Transactions on Vehicular Technology, 58(8), 3882–3891.

2. [Song, Z., Hofmann, H., Li, J., Hou, J., Han, X., and Ouyang, M.](#ch60.xhtml#R_ref60_2) (2014). 具有混合储能系统的电动汽车能量管理策略比较。 Applied Energy, 134, 321–331.

3. [Chaturvedi, R., Islam, A., Singh, P. K., and Saraswat, M.](#ch60.xhtml#R_ref60_3) (202). 先进能源系统的纳米技术：纳米燃料的合成与性能表征。 In AIP Conference Proceedings (Vol. 2721, No. 1). AIP Publishing.

4. [Beck, R., Richert, F., Bollig, A., Abel, D., Saenger, S., Neil, K.](#ch60.xhtml#R_ref60_4), et al. (200). 并联混合动力汽车驱动系统的模型预测控制。 In Proceedings of the 44th IEEE Conference on Decision and Control, (pp. 2670–2675). IEEE, 2005.

5. [Kumar, P., Singh, P. K., Nagar, S., Sharma, K., and Saraswat, M.](#ch60.xhtml#R_ref60_5) (2021). 功能化石墨烯不同浓度对热能存储系统充电时间减少的影响。 Materials Today: Proceedings, 44, 146–152.

6. [Saxena, A., Kumar, J., and Deolia, V. K.](#ch60.xhtml#R_ref60_6) (2021). 使用遗传算法优化 NPIC 控制器。 IOP Conference Series: Materials Science and Engineering, 1104(1), 012001. IOP Publishing, 2021.

7. [Beck, R., Richert, F., Bollig, A., Abel, D., Saenger, S., Neil, K.](#ch60.xhtml#R_ref60_7), et al. (200). 并联混合动力汽车驱动系统的模型预测控制。 In Proceedings of the 44th IEEE Conference on Decision and Control, (pp. 2670–2675). IEEE, 2005.

8. [Chaturvedi, R., Sharma, A., Sharma, K., and Saraswat, M.](#ch60.xhtml#R_ref60_8) (2022). 多壁碳纳米管增强 AA 7075 纳米复合材料的摩擦学行为。 Advances in Materials and Processing Technologies, 8(4), 4743–4755.

9. [Bhangu, B. S., Bentley, P., Stone, D. A., and Bingham, C. M.](#ch60.xhtml#R_ref60_9) (2005). 用于预测混合动力电动汽车铅酸电池荷电状态和健康状态的非线性观测器。 IEEE Transactions on Vehicular Technology, 54(3), 783–794.

10. [Sharma, A., Chaturvedi, R., Sharma, K., and Saraswat, M.](#ch60.xhtml#R_ref60_10) (2022). 基于响应面法铝毛刺复合材料铣削中的力评估和加工参数优化。 Advances in Materials and Processing Technologies, 8(4), 4073–4094.

11. [Kumar, Y., Pushkarna, M., and Gupta, G.](#ch60.xhtml#R_ref60_11) (2020). 使用传统技术在馈线不平衡特性中实现微电网。 In 2020 3rd International Conference on Intelligent Sustainable Systems (ICISS), (pp. 1489–1494). IEEE, 2020.

12. [Han, S., Han, S., and Aki, H.](#ch60.xhtml#R_ref60_12) (2014). 用于电动汽车充电应用的实用电池磨损模型。 Applied Energy, 113, 1100–1108.

# 61 电动汽车充电系统的辅助电源优化

Kanchan Yadav^([^(60)](#fn60))

DOI: [10.1201/9781003534136-61](https://dx.doi.org/10.1201/9781003534136-61)

## 摘要

除了几乎每辆汽车都有自己的电池充电系统外，只有少数允许使用单独的系统为辅助电源充电，通常是电池。控制该充电系统的 `AC-DC` 功率电路对于保持标称特性并延长电池寿命是必要的。此外，它应确保电池在充电和放电过程中保持完好无损。电池经历的充放电循环次数与其循环寿命之间的关系是反向的。在优化 `V2G` 操作时，应细致考虑退化成本和电池循环寿命。谨慎执行的电池充电和放电做法不仅考虑车辆所有者的便利性，还考虑电网的容量和需求。在这种需要实时控制的情况下，必须考虑能源成本、电池 `SoH` 和 `SoC` 以及其他变量。

**关键词：** 电池充电，电池放电，电网系统，使用寿命，功率电路，荷电状态，健康状态

## 引言
