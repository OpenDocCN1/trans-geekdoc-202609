
### 树莓派
单板 Raspberry Pi 3 计算机在机器人领域很受欢迎。此外，研究项目也采用它。Raspberry Pi 价格实惠且重量轻。这就是说树莓派用于管理项目。机器人移动以及按钮按下时喷水。

### 温度传感器
便宜的数字温度传感器是 DHT11。热敏电阻用于测量空气质量并将其转换为数字信号。数据用于传输数字信号引脚。虽然使用起来很简单，但必须小心处理。为了从数据上拉，需要一个 4.7k 或 10k 电阻连接到 VCC 引脚 [[14](#ch56.xhtml#ref56_14)]。

### 火焰传感器
火焰传感器用于在火灾开始时探测火灾。“火焰传感器”这一术语指的是传感器对环境光的高灵敏度。该传感器可在 760 至 1100 nm 范围内探测附近的火源。传感器的输出为数字信号。这些机器人采用传感器用于诸如报警之类的功能 [[15](#ch56.xhtml#ref56_15)]。

### Node MCU
Node MCU 是一个开源物联网平台。Node MCU 是廉价固件设备的名称。物联网应用和原型都使用它进行开发。MCU 节点中的 ESP32 微控制器具有蓝牙和 WiFi。还有以太网。它使用 7 至 12 伏特工作。

## 火灾灭火机器人工作模型
在任何可能发生火灾事故的地方，都安装了传感器模块。该模块由用于数据传输的 Node MCU 和温度、烟雾和火焰传感器组成。一旦发现火灾，Node MCU 就会将数据发送到 Firebase。接收器由两个组件组成：Android 应用程序和第一半部分的 Raspberry Pi。树莓派接收来自 Pi 相机的數據，該數據由 Android 應用程序用于显示视频。WIFI 模块是 Android 应用程序的一部分，用于连接机器人和 Android 应用程序。通过 Android 应用程序，向机器人传输命令以向前、向左、向右移动并灭火。机器人车辆配备了水箱和无线操作的喷水泵。使用 Android 应用程序设备，命令从发送端传输到接收端，以指示机器人在各个方向（包括向前、向后、向左和向右）移动。在接收端，三个电机连接到 Raspberry Pi；其中两个用于移动车辆，而第三个用于移动机器人的手臂。任何智能手机都能够进行远程操作。[图 56.2](#ch56.xhtml#fig56_2) 显示了工作模型流程图 [[16](#ch56.xhtml#ref56_16)]。

![图 56.2 流程图显示火灾灭火机器人工作原理](images/fig56_2_B.jpg)

[图 56.2 流程图显示火灾灭火机器人工作原理](#ch56.xhtml#R_fig56_2)

### 应用
用作灭火器。
用于家庭安防。
用于办公室的服务器机房。

## 结论
由于机械进步，人类参与的需求已减少，机器人目前已在包括人类福祉在内的多个不同领域得到应用。频繁发生的火灾对个人及其财产构成重大危害，并可能夺去消防员扑灭大火的生命。偶发火灾可能对财产和人类生命造成严重损害。在这种情况下，具有探测和扑灭火灾能力的自主灭火装置将至关重要。早期灭火机器人设计在很大程度上依赖于传感器，例如火焰探测器来探测火灾。本文利用移动 Android 机器人和深度学习开发了火灾保护和探测框架。我们实施了深度学习及其算法，以及可通过 Android 操作的灭火装置，以防止火灾。这些火灾探测和预防系统的最常见位置是在住宅建筑和灭火器中。

## 参考文献
1. [Ramasubramanian, S., Muthukumaraswamy, S. A., and Sasikala, A.](#ch56.xhtml#R_ref56_1) (2020). 利用人工智能进行灭火机器人火灾探测。收录于 2020 年第 4 届智能计算与控制系统国际会议 (ICICCS)。IEEE, 2020.
2. [Chaturvedi, R., Islam, A., Singh, P. K., and Saraswat, M.](#ch56.xhtml#R_ref56_2) (202). 用于先进能源系统的纳米技术：纳米燃料的合成与性能表征。收录于《AIP 会议论文集》(第 2721 卷，第 1 期)。AIP Publishing.
3. [Raj, P. Anantha, and M. Srivani](#ch56.xhtml#R_ref56_3). (2018). 基于物联网机器人技术的自主灭火移动机器人。IEEE 计算智能与计算研究国际会议 (ICCIC)。IEEE, 2018.
4. [Raj, P. A., and Srivani, M.](#ch56.xhtml#R_ref56_4) (2018). 基于物联网机器人技术的自主灭火移动机器人。收录于 2018 年 IEEE 计算智能与计算研究国际会议 (ICCIC)。IEEE, 2018.
5. [Kumar, P., Singh, P. K., Nagar, S., Sharma, K., and Saraswat, M.](#ch56.xhtml#R_ref56_5) (2021). 功能化石墨烯不同浓度对热能储存系统充电时间减少的影响。Materials Today: Proceedings, 44, 146–152.
6. [Raj, P. A., and Srivani, M.](#ch56.xhtml#R_ref56_6) (2018). 基于物联网机器人技术的自主灭火移动机器人。收录于 2018 年 IEEE 计算智能与计算研究国际会议 (ICCIC)。IEEE, 2018.
7. [Chaturvedi, R., Sharma, A., Sharma, K., and Saraswat, M.](#ch56.xhtml#R_ref56_7) (2022). 多壁碳纳米管增强 AA 7075 纳米复合材料的摩擦学行为。Advances in Materials and Processing Technologies, 8(4), 4743–4755.
8. [Bansal, S., and Tomar, V. K.](#ch56.xhtml#R_ref56_8) (2022). 物联网中的挑战与安全威胁及解决方案架构。收录于 2022 年第 2 届可再生能源及其控制中的电力电子与物联网应用国际会议 (PARC)。IEEE, 2022.
9. [Sowah, R. A., Ofoli, A. R., Krakani, S. N., and Fiawoo, S. Y.](#ch56.xhtml#R_ref56_9) (2016). 基于模糊逻辑的实时多传感器火灾探测与通知系统的硬件设计和基于网络的通信模块。IEEE Transactions on Industry Applications, 53(1), 559–566.
10. [Sharma, A., Chaturvedi, R., Sharma, K., and Saraswat, M.](#ch56.xhtml#R_ref56_10) (2022). 基于响应面法的铝毛刺复合材料铣削的力评估和加工参数优化。Advances in Materials and Processing Technologies, 8(4), 4073–4094.
11. [Fadlullah, Z. M., Tang, F., Mao, B., Kato, N., Akashi, O., Inoue, T., and Mizutani, K.](#ch56.xhtml#R_ref56_11) (2017). 最先进的深度学习：机器智能演进以实现明日智能网络流量控制系统。IEEE Communications Surveys & Tutorials, 19(4), 2432–2455.
12. [Taiwo, O., Ezugwu, A. E., Oyelade, O. N., and Almutairi, M. S.](#ch56.xhtml#R_ref56_12) (2022). 基于深度学习模型的增强型智能家居控制与安全系统。Wireless communications and mobile computing, 2022, 1–22.
13. [Bansal, S., and Tomar, V. K.](#ch56.xhtml#R_ref56_13) (2022). 面向物联网应用的 11T SRAM 单元的仿真与分析。收录于《通信、器件与网络进展》。新加坡：Springer, (pp. 329–340)。
14. [Wu, X., Dunne, R., Zhang, Q., and Shi, W.](#ch56.xhtml#R_ref56_14) (2017, October). 边缘计算支持的智能灭火：机遇与挑战。收录于第五届 ACM/IEEE 网络系统与技术热点研讨会论文集 (pp. 1–6)。
