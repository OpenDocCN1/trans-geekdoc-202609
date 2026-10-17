

![Figure 2.1 Creating a fake beacon using kali linux.](images/fig2_1.jpg)

[Figure 2.1 使用 kali linux 创建伪造信标。](#ch02.xhtml#Ffig2_1)

![Figure 2.2 Rate of flow of network frames during beacon forgery attack.](images/fig2_2.jpg)

[Figure 2.2 信标伪造攻击期间网络帧的流速。](#ch02.xhtml#Ffig2_2)

[Figure 2.2](#ch02.xhtml#fig2_2) 显示了攻击期间受害者和接入点处信标在网络中的流量。我们观察到，在信标泛滥期间，来自同一接入点的信标帧数量有所增加。由此，我们推断信标帧伪造成功。

### 2.5.2 信标泛滥

信标泛滥会阻止受害者选择正确的接入点。我们通过向受害者发送具有相同 ssid 的伪造接入点信标来模拟该攻击。该泛滥攻击使用 Python 中的 `SCAPY` 库进行模拟。使用 kali linux 模拟的信标泛滥攻击的截图以及接收到具有特定 ssid 的信标的图表分别在 [图 2.3](#ch02.xhtml#fig2_3) 和 [2.4](#ch02.xhtml#fig2_4) 中给出。

![Figure 2.3 Beacons flooding using kali linux.](images/fig2_3.jpg)

[Figure 2.3 使用 kali linux 进行信标泛滥。](#ch02.xhtml#Ffig2_3)

![Figure 2.4 Rate of flow of network frames during beacon flooding attack.](images/fig2_4.jpg)

[Figure 2.4 信标泛滥攻击期间网络帧的流速。](#ch02.xhtml#Ffig2_4)

[Figure 2.4](#ch02.xhtml#fig2_4) 显示了信标泛滥攻击期间信标帧的增加，但与伪造攻击不同，这些信标具有相同的 ssid 但不同的 bssid。高信标流速表明泛滥攻击已成功执行，如 [图 2.2](#ch02.xhtml#fig2_2) 所示。信标泛滥攻击更容易检测，因为受害者会被大量帧淹没。

### 2.5.3 去认证攻击

去认证帧在 WiFi 802.11 协议中由客户端/接入点用于终止连接，因为它们不需要数据包确认。攻击者使用这些帧断开合法用户的连接，并阻止其连接到合法接入点。它们还可用于消耗接入点的资源，从而使其无法以固定间隔发送信标。此类攻击可用于信标泛滥、MitM（中间人攻击）。使用 kali linux 模拟的去认证攻击的快照以及去认证帧流量的图表分别在 [图 2.5](#ch02.xhtml#fig2_5) 和 [2.6](#ch02.xhtml#fig2_6) 中给出。

![Figure 2.5 De-authentication attack using kali linux.](images/fig2_5.jpg)

[Figure 2.5 使用 kali linux 进行去认证攻击。](#ch02.xhtml#Ffig2_5)

![Figure 2.6 Rate of flow of de-authentication frames during de-authentication attack.](images/fig2_6.jpg)

[Figure 2.6 去认证攻击期间去认证帧的流速。](#ch02.xhtml#Ffig2_6)

[Figure 2.7](#ch02.xhtml#fig2_7) 显示了攻击期间网络中去认证帧的到达速率。仅当接入点从网络中去认证一个站点时，才会观察到这些帧。去认证帧的异常增加表明发生了去认证攻击。

![Figure 2.7 Graphical results for evaluation of balanced dataset.](images/fig2_7.jpg)

[Figure 2.7 平衡数据集评估的图形结果。](#ch02.xhtml#Ffig2_7)

### 2.5.4 攻击建模

在本小节中，我们描述了所提方法的方法论，该方法涉及信标伪造的建模和仿真。

我们建议模拟每种信标攻击，捕获网络流量，并分析潜在风险。特别是，在攻击期间捕获了数据包，并将其存储在 pcap 文件中。然后使用 `tshark` 从文件中以文本格式提取数据，其截图如 [图 2.8](#ch02.xhtml#fig2_8) 所示。从文本文件中删除了不需要的空格。提取的一些特征特定于去认证帧或信标帧，如 [表 2.1](#ch02.xhtml#table2_1) 所示。

![Figure 2.8 Sample of the extracted data.](images/fig2_8.jpg)

[Figure 2.8 提取数据的示例。](#ch02.xhtml#Ffig2_8)

[表 2.1 从 pcap 文件中提取的特征](#ch02.xhtml#Ttable2_1)

| 提取的特征 || 描述 |

| --- | --- |

| `wlan.da` || 帧的目的地 |

| --- | --- |

| `wlan.fixed.timestamp` || 到达时间戳 |

| `wlan.bssid` || 帧的 bssid（Mac 地址） |

| `frame.time` || 时间戳 |

| `wlan radio.signal dbm` || 无线信号强度 |

| `wlan.fixed.beacon` || 信标间隔 |

| `wlan.sa` || 接入点的源地址 |

| `wlan.fixed.capabilities.ess` || 信道能力（扩展服务集） |

| `wlan.fixed.capabilities.ibss` || 信道能力（ibss） |

| `wlan.ra` || 接收器地址（去认证帧） |

| `wlan.fixed.capabilities.cfpoll.ap` || 信道能力（CFP 参与） |

| `wlan.fixed.capabilities.privacy` || 信道能力（隐私） |

| `wlan.fixed.capabilities.preamble` || 信道能力（短前导码） |

| `wlan.fixed.capabilities.pbcc` || 信道能力（pbcc） |

| `wlan.fixed.capabilities.agility` || 信道能力（信道敏捷性） |

| `wlan.fixed.capabilities.spec man` || 信道能力（频谱管理） |

| `wlan.fixed.capabilities.short slot time` || 信道能力（短时隙时间） |

| `wlan.fixed.capabilities.radio measurement` || 信道能力（已实现无线测量） |

| `wlan.fixed.capabilities.apsd` || 信道能力（apsd） |

| `wlan.ssid` || 接入点的 ssid（接入点名称） |

| `wlan.fixed.capabilities.del blk ack` || 信道能力（延迟块 ACK） |

| `frame.time epoch` || 纪元时间 |

| `frame.time relative` || 从第一个帧到达以来经过的时间 |

| `wlan.sa` || 源地址（去认证帧） |

| `wlan.fixed.capabilities.imm blk ack` || 信道能力（立即块 ack-结束） |

| `wlan.fixed.capabilities.dsss ofdm` || 信道能力（允许 DSSS-OFDM） |

| `wlan.fixed.reason code` || 去认证原因 |

#### 2.5.4.1 特征提取

数据预处理后，计算了来自同一源的两个连续帧之间的频率和时间差。提取的特征描述如下。

1. 频率 – 频率使用到达时间计算。计算在 3 秒时间跨度内到达的去认证帧数量。记录第一个帧的到达时间，并且每 3 秒更新一次数值。较高的频率表明网络中去认证帧数量较多，从而导致去认证攻击。频率按公式 2.7 计算。

    `Frequency = ND / T` (2.7)

其中，

1. ND = 去认证帧数量

2. T = 更新时间

2. 时间差 – 时间差基于帧的纪元时间计算，如公式 2.8 所示。这主要用于检测信标伪造，因为信标以固定间隔 100 个传输单元（TUs）传输。

`Time_Difference = ATCF - ATPF` (2.8)

其中，

1. ATCF = 来自同一源的当前帧的到达时间

2. ATPF = 来自同一源的前一帧的到达时间

## 2.6 数据集分类

