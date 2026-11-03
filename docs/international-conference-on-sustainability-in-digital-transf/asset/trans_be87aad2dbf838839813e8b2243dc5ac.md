
## 文献综述
Sumithra 等 \[[1](#ch54.xhtml#ref54_1)\] 使用空气和声音传感器提供无污染城市。作者将监测数据上传至云存储进行分析，并随后通知连接到云服务器的用户。Singh 等 \[[2](#ch54.xhtml#ref54_2)\] 使用传感器监测空气和噪声。作者使用 Raspberry Pi 收集传感器数据并将其发送到应用程序。Sindhu 等 \[[3](#ch54.xhtml#ref54_3)\] 描述了利用 PIC 微控制器进行空气监测的概念，该控制器感测大气信号以测量空气中的污染水平。然后将监测数据上传到互联网，通过应用程序进行查看。Kim 等 \[[4](#ch54.xhtml#ref54_4)\] 设计了一个环境监测系统并将结果传输到服务器。作者将他们的系统与国家环境空气质量监测信息系统 (NAMIS) 进行比较。Aarthi 等 \[[5](#ch54.xhtml#ref54_5)\] 使用 LM393 声音传感器、MQ135 气体传感器、DHT11 温度和湿度传感器以及蜂鸣器，并配合与 GPRS 模块和 WIFI 模块接口的 Rasperry Pi 设计空气和噪声污染监测系统。Dhruvil Shah 等 \[[6](#ch54.xhtml#ref54_6)\] 提出了一种具有视觉输出的实时系统，用于检查室内和室外空气质量。Chandana 等 \[[7](#ch54.xhtml#ref54_7)\] 开发了一种空气和噪声质量监测系统，其中监测数据可通过 Wi-Fi 提供给用户，以便进行分析。Anushka Sharma 等 \[[8](#ch54.xhtml#ref54_8)\] 提出了一种方法，其中跟踪数据从城市的固定节点传输到部署在公共交通工具上的移动节点。Lipane 等 \[[9](#ch54.xhtml#ref54_9)\] 展示了一个实时的空气和噪声质量监测系统。远程位置的数据使用 Wi-Fi 模块传输。Joshi \[[10](#ch54.xhtml#ref54_10)\] 提出了一种监测特定区域污染参数的系统，以便使该区域智能化且无污染。

传统方法涉及体力劳动，其中数据采集员会亲自收集数据、检查数据并利用类比产生输出，该输出冗长、耗时且效率低下 \[[11](#ch54.xhtml#ref54_11)\]。监测模型中使用的执行器可以检测有害气体，如二氧化碳 (CO[2] )、二氧化硫 (SO[2] ) 等。对于声音、CO 和污染物水平等变量的高值，会给出标记。当附近物体，有时被称为感知环境，作为自卫和观察环境发挥作用 \[[4](#ch54.xhtml#ref54_4)\] \[[12](#ch54.xhtml#ref54_12), [13](#ch54.xhtml#ref54_13) and [14](#ch54.xhtml#ref54_14)\] 时，它们配备有执行器、小工具、微控制器和各种软件程序。它有助于评估众多特征并将数据持续传输到存储中。

## 硬件描述
本节对设计基于物联网的空气和噪声污染监测系统 \[[15](#ch54.xhtml#ref54_15)\] 中使用的不同硬件组件进行了描述。[表 54.2](#ch54.xhtml#tab54_2) 给出了设计基于物联网解决方案时使用的微控制器/微处理器的简要描述。

[表 54.2 微控制器/微处理器使用。](#ch54.xhtml#R_tab54_2)

| 微控制器/微处理器 || 规格 |
| --- | --- |
| Raspberry Pi || 运行一套开源软件的微处理器。 |
| --- | --- |
| Arduino || 可连接多个数字和模拟传感器的单板微控制器。 |
| Xmega 2560 || 高性能、低功耗的 Microchip 8 位 AVR RISC 基微控制器。 |
| Node MCU || 具有低成本 Wi-Fi 芯片 ESP8266 的微控制器。 |

[表 54.3](#ch54.xhtml#tab54_3) 给出了可在设计空气和噪声污染监测系统时使用的各种传感器/执行器的简要描述。

[表 54.3 传感器/执行器使用。](#ch54.xhtml#R_tab54_3)

| 使用的传感器/执行器 || 规格 |
| --- | --- |
| MQ 2 || 用于检测甲烷、丁烷、液化石油气、烟雾 |
| --- | --- |
| MQ-3 || 用于检测酒精、乙醇、烟雾 |
| MQ 7 || 用于检测 CO 气体。 |
| MQ 135 传感器 || 用于测量空气质量。它用于检测低导电性氧化锡 (SnO[2] )。 |
| 声音传感器 || 用于检测声波的存在。 |
| DHT11 || 这是数字温度和湿度传感器。 |
| 蜂鸣器 || 用于产生报警声音的执行器。 |

[表 54.4](#ch54.xhtml#tab54_4) 给出了用于提供网络连接的其他硬件组件的简要描述。

[表 54.4 集成模块使用。](#ch54.xhtml#R_tab54_4)

| 使用的集成模块 || 规格 |
| --- | --- |
| Wi-Fi 模块 || 用于为 Arduino 板提供 Wi-Fi 连接。 |
| --- | --- |
| GPS 模块 || 获取位置、速度、日期和时间。 |

[表 54.5](#ch54.xhtml#tab54_5) 给出了不同空气质量指数值及其对健康影响的简要描述。

[表 54.5  空气质量指数，对健康的影响。](#ch54.xhtml#R_tab54_5)

| 空气指数 || 对健康的影响 |
| --- | --- |
| 良好 (0-50) || 风险非常低 |
| --- | --- |
| 中等 (51-100) || 总体而言，空气质量是可以接受的。然而，少数污染物对某些高度敏感人群存在中等风险。 |
| 对敏感人群不健康 (101-150) || 一般人群可以接受，但对敏感人群有问题。 |
| 不健康 (151-200) || 对一般人群有问题；对敏感人群有严重风险 |
| 非常不健康 (201-300) || 健康紧急状况警告。 |
| 有害 (301-500) || 非常严重的健康影响。 |

## 结论
噪声和空气污染监测系统为人类在地球上面临的最大问题之一提供了解决方案。它使用了物联网 (IoT) 的最新技术，提供了一个有效的系统来支持健康的生活方式。市政公司代表和公众都可以利用这种安排，通过移动设备接收污染程度的通知。在本工作中，我们讨论了之前研究中为开发利用物联网的类似系统而提出的许多不同策略。用于开发此类系统的不同硬件组件也进行了讨论。随着人们对污染的认识日益提高，物联网的概念为社会福利提供了一个有效的解决方案。

## 参考文献
1. [S. Jiyal, J. Sheetlani and R. K. Saini](#ch54.xhtml#R_ref54_1). (2022). Internet of Things: A Survey on Air Pollution Monitoring, Challenges and Applications. 7th International Conference on Computing, Communication and Security (ICCCS), Seoul, Korea, Republic of, 2022, pp. 1–6, doi: [10.1109/ICCCS55188.2022.10079635](http://dx.doi.org/10.1109/ICCCS55188.2022.10079635).

2. [Singh, A., Pathak, D., Pandit, P., Patil, S., and Golar, P. C.](#ch54.xhtml#R_ref54_2) (2017). IOT based air and sound pollution monitoring system. International Journal of Advanced Research in Electrical, Electronics and Instrumentation Engineering, 6(3), 1273–1278.

3. [Chaturvedi, R., Islam, A., Singh, P. K., and Saraswat, M.](#ch54.xhtml#R_ref54_3) (2023). Nanotechnology for advanced energy system: synthesis & performance characterization of nano-fuel. In AIP Conference Proceedings (Vol. 2721, No. 1). AIP Publishing.

4. [Kim, S. H., Jeong, J. M., Hwang, M. T., and Kang, C. S.](#ch54.xhtml#R_ref54_4) (2017). Development of an IoT based atmospheric environment monitoring system. In International Conference on Information and Communication Technology Convergence (ICTC), 2017.

