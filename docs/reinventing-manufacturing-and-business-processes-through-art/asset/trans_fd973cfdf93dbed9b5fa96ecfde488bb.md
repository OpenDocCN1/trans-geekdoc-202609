

## 金属切削 IoT 路线图

## 7.9.2 规划部门

当前的制造环境面临高复杂性、动态生产条件和市场状况不稳定等挑战。同时，对于低成本的产品定制以及缩短交付周期的需求（Schuh et al., 2017）。为了克服这些挑战，业界正在寻找新技术。IoT 是克服当前市场挑战的优越技术。在工业 4.0 背景下，生产计划与控制（PPC）的功能可以预测全球生产数量以提高盈利能力，并优化交付时间（Arnold and Chapman, 2004）。它还涉及对制造过程的控制，允许资源的实时集成（Moeuf et al., 2018）。机器学习算法、通过 IoT 采集的实时数据以及生产规划的集成，有助于规划阶段的决策。

1. 根据循环时间和设备可用性，为所有工序步骤准备能力分析。
2. 研究流程以识别瓶颈设备，并将剩余设备分类为供料设备和非关键设备。
    - 瓶颈设备是定义了生产线或机器区域最大产能的设备。对于这些设备，目标是实现尽可能长的运行时间，以最大化生产能力。
    - 供料设备是为瓶颈设备提供设备的设备。对于这些设备，目标是按照计划的顺序和时间生产零件，以便及时为瓶颈设备供。时间应基于生产线的标准作业通过视觉拉动信号给出。
    - 非关键设备是位于流程中瓶颈设备之后的设备。对于这些设备，目标是保持生产流，以实现整体交付周期的缩短。
3. 计划工时是在组件工艺创建过程中决定的小时；实际工时是从运行数据报告中获取的小时。

在此背景下，为每个组件准备计划工时与车间实际工时的对比报告。基于此比较，必须对计划与实际小时之间的差距进行差距分析。在分析过程中，应考虑操作员技能、加工工具、加工参数和焊接参数。目标是通过持续改进缩小差距，并与之前的组件相比缩短循环时间。必须进行分析以识别减少关键组件计划工时的可能性以及所采取的行动。

## 7.9.3 质量管理

质量管理主要由质量规划、质量控制、质量保证和质量改进组成。质量管理包括决定实现质量目标的质量目标、操作流程和资源。质量控制侧重于满足质量要求。质量保证侧重于提供对将满足质量要求的信心。质量改进寻求产品质量的持续改进。质量管理中的实时数据集成可以提高质量。透视分析算法用于各种操作过程以实现质量目标。可以使用模糊逻辑或人工神经网络（例如）来决定控制产品质量的关键参数。如果操作员以不当参数操作机床，可以通过自动停止机床来实现质量保证。可以使用优化算法确定持续改进产品质量的最佳参数。

## 7.9.4 维护管理

IoT 集成到维护系统中可以提高整体效率。诊断分析算法有助于检测故障根源，从而缩短维修时间。温度和振动等实时数据有助于预测性维护。

## 7.10 结论

本研究深入讨论了 IoT 在金属切削中的实施；它首先介绍了 IoT 在金属切削中的阶段，并讨论了 IoT 在金属切削中面临的挑战。金属切削中 IoT 的实现技术根据制造的关键活动进行了总结：生产、规划、质量管理和维护。研究表明，生产部门可以利用实时信息识别车间现场的问题。我们可以有效测量详细讨论的金属切削过程中的非增值活动和增值活动。规划部门可以比较计划工时和实际工时，为下一个周期进行准确规划。此外，识别瓶颈和设备供料有助于生产部门意识到需要关注哪些机器，以确保组件的按时完成。质量部门可以使用 IoT 决定最佳参数以提高产品质量。维护部门可以通过实时状态监测提高 OEE。此外，收集的数据可以使用各种人工智能算法进行预测性维护。

## 7.11 研究局限性

网络安全是工业 4.0 面临的最大挑战，本研究未涵盖此内容。行业数据管理可能由于未经授权的数据更改、未经授权的数据删除和非法访问而崩溃。设计、营销和供应链的集成也未包含在研究中。

## 金属切削 IoT 路线图

## 7.12 未来展望

在研究中，HMI 用于存储加工的各种活动。然而，由于人为干预，始终存在错误风险。需要自动记录这些活动以收集 100% 准确的数据。可能的解决方案之一是使用图像处理。通过卷积神经网络，我们可以训练算法，然后它可以用于自动记录时间。

## 参考文献

Aivaliotis, P., Georgoulis, K., & Alexopoulos, K. (2019). Using digital twin in manufacturing: state of the Art and Gap analysis. In 2019 IEEE International Conference on Engineering, Technology and Innovation (ICE/ITMC) (pp. 1–5). IEEE, France.

Alptekin, A., & Corbett, C. (2008). Mass customization vs. mass production. Service Operations, 10(2), 204–217.

Arnold, J. T., & Chapman, S. N. (2004). Introduction to materials management.

Atzoria, L., Iera, A., & Vaniakos, G. (2010). The internet of things: a survey. Computer Networks, 54(15), 2787–2885.

Benardos, P. G. (2021). Things and industrial applications for precision machining. Solid state phenomena (Vol. 261, pp. 440–447). Switzerland: Trans Tech.

Cakir, M., Guvenc, A., & Mistoglu, S. (2021). The experimental application of popular machine learning algorithms on predictive maintenance and the design of IoT based monitoring system. Computers & Industrial Engineering, 151, 106948.

Chen, X., Li, C., Tang, Y., & Li, Q. (2018). A framework for energy monitoring of machining workshops over IoT. Proced CIRP, 72, 1386–1389.

Cooper, C., & Kaplinsky, R. (Eds.). (2005). Technology and development in the third industrial revolution. London: Routledge.

Crognier, G., Taurnies, P., Ruiz, M., & Panciatici, P. (2021). Grid operation-based usage maintenance planning. Electric Power Systems Research, 190, 106682.

Dai, H., Wang, H., Xu, G., Wan, J., & Imran, M. (2020). Data analytics for manufacturing internet of things: opportunities, challenges and enabling technologies. Enterprise Information Systems, 14(9-10), 1279–1303.

Deshayes, L., Lynch, D., Anvest, I., Gilsinn, R., . . & Porta, F. (2006). Smart machining systems: systems and research trends. Innovation in life cycle engineering and sustainable development (pp. 363–380). Dordrecht: Springer.

Dutta, S. P., Sal, K., Mukhopadhay, S., & Sen, R. (2013). Application of digital image processing in condition monitoring: a review. CIR Journal of Manufacturing Science and Technology, 6(3), 212–232.

