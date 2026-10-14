
**关键词：** `Internet of things`, `COVID-19`, `blood bank`, `mobile application`, `android studio`

## I. 引言

在过去的年份里，在紧急情况下寻找捐血者或特定血型非常困难，有时是因为血型稀有或根本没有该血型，这个问题日益严重。通过 Android 应用结合 IoT 传感器开发血库应用是应对 COVID-19 大流行的最佳解决方案 (Bassam et al., 2021)。通过血库应用，用户可以轻松节省时间和精力 (Kayode et al., 2019)。根据 WHO 报告，在 COVID-19 大流行期间每两秒钟就有人需要输血 (Priya et al., 2014)。

人们必须在长队中等待输血，并在不同地点寻找血液。在 COVID-19 期间，人们没有钱购买血液，获得血液非常困难 (Fahim et al., 2016)。在大都市地区，人们觉得捐献或获取血液很困难，同时也给前来捐血的人带来困扰，迫切需要一款适合捐献者和接收者的移动应用。

血型有多种类型，医院中最常见的血型是“O”，在 COVID-19 期间约每 3–4 小时就有 100 万人确诊 (Altameem et al., 2022)。最稀有的血型是“hh”，即 Bombay 血型，由 Dr. Y. M. Bhende 在 1952 年于孟买发现。这部电影《okkadunnadu》因此概念走红。如 [Table 11.1](#ch11.xhtml#tab11_1) 所示，许多人需要不同类型的血液 (Fahim et al., 2016)。

[Table 11.1 Frequency of occurring in different blood groups (Fahim et al., 2016).](#ch11.xhtml#R_tab11_1) 

| S. No  | Approximate frequency of occurring blood type |
| --- | --- |
| 1 | O +ve: 1 person might be among 3 persons |
| 2 | A +ve: 1 person might be among 3 persons |
| 3 | O -ve: 1 person might be among 15 persons |
| 4 | A -ve: 1 person might be among 16 persons |
| 5 | B +ve: 1 person might be among 12 persons |
| 6 | B -ve: 1 person might be among 67 persons |
| 7 | AB +ve: 1 person might be among 29 persons |
| 8 | AB -ve: 1 person might be among 167 persons |
| Incident | Approximate estimation usage of blood |
| 1 | Automobile minor accident: Approximately 45 to 50 units of blood |
| 2 | Heart surgery for a single patient: Approximately 6 units of blood |
| 3 | Organ transplantation for a single patient: Approximately 40 units of blood |

这 4 种常见血型（A、B、AB、O）由 Karl Landsteiner 在 1901 年发明，纪念他的生日为“世界献血者日”。印度在 10 月 1 日庆祝“国家献血日”。如果一个人从 18 岁开始每 90 天献血，直到 60 岁，他/她大约会捐出 30 加仑血液，拯救约 600 生命 (Fahim et al., 2016)。

在本文中，我们将使用 Android Studio 编程在 IoT 医疗传感器上开发血库应用，该应用在注册时询问捐献者或接收者的姓名、电话号码、位置和血型 (Altameem et al., 2022)。用户通过凭据登录，并可轻松查找捐献者或接收者的血型。本报告描述了应用的布局和代码。血库应用也可以使用 Java 编程实现 ([Krishna et al., 2019](#ch11.xhtml#ref11_7))。本项目通过该应用展示用户可以通过询问附近的人获取血液，节省时间。有时交通堵塞会危及生命。该应用还能降低管理成本。所提议的应用提供实时、机器人结构。以下是本研究的目标：

* 根据城市位置，实时共享捐献者或接收者的紧急血液请求，并在此城市内查找捐献者。

* 在紧急时刻和时间紧迫时，能够快速找到血液。

* 该应用提供捐献者附近的实时血液可用性信息。

* 用户可以在注册时提供基本信息后，轻松请求血液或提供血液。

根据现有系统，人们总是冲进医院血库的长队，有时在规定时间内找不到特定血型，这使得情况变得更加困难。为了克服这一问题，本观察性研究和计量方法提供了更好的挽救生命的途径。

* 该应用节省了因在医院长队和血库中心等待血液的用户的时间。

* 查找特定人群的血液可能耗时很长，在此期间可能失去生命。

* 该应用降低了管理成本。

该应用具备高级移动功能，能够根据血液信息管理移动应用的实时数据进行更新，并使用移动搜索引擎查找注册用户的捐献者和接收者。本研究还表明，注册用户可以向捐献者和接收者发送通知。该应用也存在一些缺点，需要互联网连接并管理大型数据库的特定功能。

在本论文第 2 节讨论相关工作，以区分拟议的方法；第 3 节阐述方法论；第 4 节提供实现细节；第 5 节给出结论，随后是参考文献。

## I. 相关工作

大部分研究工作 (Kayode et al., 2019) 都集中在基于 Android 的移动血库应用开发及信息检索程序上。现有研究工作 (Shah et al., 2022) 也侧重于 Android 应用，但最近的大部分工作涉及血库管理的 Web 门户应用开发，而与 IoT 传感器不相连。文献 ([Priya et al., 2014](#ch11.xhtml#ref11_4)) 关注优化捐血者信息系统，涵盖所有捐血者信息处理方法，但未在移动医疗应用环境中实现集成环境。在医疗领域，世界卫生组织和医疗信息系统 (HMS) 表示，人们需要便捷的移动血库应用系统 (Fahim et al., 2016)。

本文的目标是实现与 IoT 的集成环境，Android Studio 移动应用提供实时、移动性和 GPS 连接环境，帮助在 COVID-19 医疗紧急情况下尽快供血。

