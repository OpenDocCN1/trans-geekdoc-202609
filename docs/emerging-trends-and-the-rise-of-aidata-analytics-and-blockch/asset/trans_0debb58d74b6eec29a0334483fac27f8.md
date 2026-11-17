

| IoT Layers | Countermeasures | Countermeasure Description | Security Threats | Reference |
|:---|:---|:---|:---|:---|
| 路由安全 | | 应用不同的路由算法，以保障传输至不同传感器节点的数据机密性 | (1) 路由攻击 (2) 蠕洞攻击 | Mendez et al. (2017); Ahmed et al. (2017); Noor and Hassan (2019); Tariq et al. (2019) |
| GPS 方法论 | | 它在发送方和接收方之间生成多条路径，并检查路由的存在 | RFID 复制 | Ahmed et al. (2017) |
| 身份认证 | | GPS 方法论有助于跟踪网络中所有无线电频率传输并避免任何欺骗。只有经过身份认证和授权的设备才能发送。这确保了无线电频率传输识别不会被复制 | RFID 复制 | Mendez et al. (2017); Ahmed et al. (2017); Abba et al. (2017); Noor and Hassan (2019); Kouicem et al. (2018) |
| 密码学算法 | | 使用密码学算法可防止攻击者访问或篡改关键数据，从而确保数据不被篡改 | Hello flood攻击 窃听 信息窃取 欺骗攻击 | Wei et al. (2019), Ahmed et al. (2017); Abba et al. (2017); Moin et al. (2019); Kouicem et al. (2018), Tariq et al. (2019); Wei et al. (2019); Kouicem et al. (2019); Wang et al. (2019); Kouicem et al. (2018) |
| 零知识证明 | | 零知识证明允许在不提供除声明本身以外的任何信息的情况下验证声明，它确保机密性 | | |
| 同态加密技术访问控制 模糊信任计算 | | 完全同态加密方案允许对加密数据进行计算。该机制采用信任计算方法来确定恶意节点，从而在移动自组网中确定安全路由。 | (1) 灰洞 (2) 黑洞 | Wei et al. (2019); Ahmed et al. (2017); Wang et al. (2019); Hassan et al. (2019); Tariq et al. (2019) |
| 多重签名 | | 确保数据在未经多个授权用户签名之前不能被传输。多重签名有助于防止攻击节点干扰正在传输的数据，从而增强数据安全性。 | | Yu et al. (2018) |
| 流量分析 | | 具有分析网络流量流向的能力。它检查来自物联网设备的流量流向，收集的模式用于识别合法流量。 | (1) Hello flood攻击 (2) DoS/DDoS攻击 | Rathore et al. (2019) |
| 攻击识别 | | 欺骗参考有助于确定攻击者试图伪造消息以干扰安全身份保护的节点。 | 消息欺骗 | Noor and Hassan (2019) |
| 消息认证码 | | 发送给接收方以打开交易的代码。 | 窃听 | Ferrag et al. (2020) |

| IoT Layers | Countermeasures | Countermeasure Description | Security Threats | Reference |
|:---|:---|:---|:---|:---|
| 处理层 | 分层共识协议 | 将多变量拜占庭共识减少为二进制 | 拜占庭攻击 | Moin et al. (2019), Wang et al. (2019), Wei et al. (2019) |
| | 动态委员会加密 | 满足有效性属性的拜占庭共识 | | Wei et al. (2019) |
| | | 它用于保证实时状态更新 | 数据传输攻击 | Wang et al. (2019), Ahmed et al. (2017), Alrabai (2019), Hassija et al. (2019) |
| | 加密 | 它确保物联网中的数据机密性，即数据在发送/传输前被加密 | (1) 未经授权的访问 | Ahmed et al. (2017), Hassija et al. (2019), Mendez et al. (2017), Noor and Hassan (2019), Kouicem et al. (2018) |
| | | | (2) 云端泛洪攻击 | |
| | | | (3) SQL注入攻击 | |
| | | | (4) 中间人攻击 (MiTM) | |
| | | | (5) 签名包装攻击 | |
| 身份认证 | | 可通过使用公钥基础设施 (PKI) 的身份认证方法来解决 WSN 安全问题，以防止恶意节点数据注入 | (1) 云端泛洪攻击 | Mendez et al. (2017), Ahmed et al. (2017), Wang et al. (2019), Wei et al. (2019), Noor and Hassan (2019), Kouicem et al. (2018) |
| 代码验证 | | 它确保输入数据经过验证，以防止 SQL 注入等代码注入攻击。它在设备或边缘层提供高级别安全性 | (2) 签名包装攻击 | Ahmed et al. (2017), Hassija et al. (2019), Mendez et al. (2017), Noor and Hassan (2019), Kouicem et al. (2018) |
| 入侵检测系统 | | 它持续控制入侵者活动日志，并在执行任何不确定操作时触发警报 | (3) SQL注入攻击 | |
| | | | (4) 中间人攻击 (MiTM) | |
| 防火墙 | | 执行数据包过滤以阻止不需要的数据包 | SQL注入攻击 | Ahmed et al. (2017), Hassija et al. (2019), Kouicem et al. (2018) |
| Web应用程序扫描器 | | Web应用程序扫描器用于检测 Web 应用程序前端中的任何威胁 | 向第三方数据泄露 | Ahmed et al. (2017), Hassija et al. (2019), Kouicem et al. (2018) |
| 数据碎片化 | | 将数据分成片段并拆分用于存储目的。它最大限度地降低云服务器中数据被盗的风险 | 虚拟化威胁 | |
| 超安全 | | 它防止内存页被篡改 | | |

| IoT Layers | Countermeasures | Countermeasure Description | Security Threats | Reference |
|:---|:---|:---|:---|:---|
| 应用层 | 防病毒软件和反间谍软件 加密 入侵检测系统 | 防病毒软件和反间谍软件对于确保数据完整性和机密性至关重要。它确保物联网中的数据机密性，即数据首先被加密后再发送/传输。IDS 检测并防止 DoS 风险 | 病毒和蠕虫攻击 隐写攻击 拒绝服务 (DoS) | Ahmed et al. (2017), Hassija et al. (2019) Ahmed et al. (2017) Mendez et al. (2017), Ahmed et al. (2017), Alba et al. (2017), Noor and Hassan (2019), Kouicem et al. (2018), Tariq et al. (2019) |
| | 防火墙 | 执行数据包过滤以阻止不需要的数据包 | 恶意代码注入攻击 | Wang et al. (2019), Hassija et al. (2019), Ahmed et al. (2017), Kouicem et al. (2018) |
| | 监控 | 监控摄像头可以分析异常，并将汇总和可疑数据发送到数据中心，以实现更快的响应时间 | 欺骗攻击 | Ahmed et al. (2017), Hassija et al. (2019) |
| | 风险评估 | 它通过防止未经授权访问数据来避免物联网网络中的安全漏洞 | 旁信道攻击 | Ahmed et al. (2017) |
| | 密钥管理 | 它保护物联网数据传输 | 数据窃取攻击 | Mendez et al. (2017), Moin et al. (2019), Noor and Hassan (2019), Tariq et al. (2019) |
| | 密码学算法 | 使用密码学算法可防止攻击者访问或篡改关键数据，从而确保数据隐私 | (1) 女巫攻击 (2) 身份伪造 (3) 自私攻击 | Hassan (2019), Tariq et al. (2019) Wei et al. (2019), Ahmed et al. (2017), Alaba et al. (2017), Moin et al. (2019), Noor and Hassan (2019), Tariq et al. (2019) |

## 按安全目标划分的威胁

![](img/577e2d5cd96499c3f37cac44f61f91b4_112_0.png)

## 按物联网层划分的威胁

![](img/577e2d5cd96499c3f37cac44f61f91b4_112_1.png)

## 按安全目标划分的安全机制

![](img/577e2d5cd96499c3f37cac44f61f91b4_112_2.png)

## 按物联网层划分的安全机制

![](img/577e2d5cd96499c3f37cac44f61f91b4_112_3.png)

图 2. 按物联网层和安全目标划分的威胁与安全机制

## 区块链对物联网安全目标的影响

![](img/577e2d5cd96499c3f37cac44f61f91b4_112_4.png)

## 区块链对物联网层的影响

![](img/577e2d5cd96499c3f37cac44f61f91b4_112_5.png)

## 按重要程度划分的区块链特性

![](img/577e2d5cd96499c3f37cac44f61f91b4_112_6.png)

图 3. 区块链特性对物联网安全的影响

另一方面，数据完整性可以通过区块链的不可篡改特性来实现，该特性防止已注册的交易被更改（Moin et al., 2019）。此外，它有助于跟踪并执行来自各种设备的交易，从而消除物联网应用中的中心化服务器（Koshy et al., 2020）。

区块链系统在智能设备首次连接到系统时会分配一对唯一密钥（Yu et al., 2018）。这些密钥（公钥及其匹配的私钥）存储在区块链中（Yu et al., 2018），从而提供更高级别的安全性。然后设备可以自由相互交互，签名结合公钥可用于验证它们（Zhu and Badr, 2018; Yu et al., 2018）。区块链通过利用公钥获取特定身份的更多信息来帮助解决隐私问题（Alotaibi, 2019; Sun et al., 2017）。对称加密有助于实现

