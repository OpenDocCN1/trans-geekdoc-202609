
# 气候模型与环境影响分析

## 概述

气候模型旨在模拟与气候变化预测相关的不确定性。这些模型增强了对气候行为可预测性的理解。科学家利用这些模型，它们基于海洋和大气中观察到的全球模式。让我们理解气候与天气有何不同。天气指的是特定时间、特定地点的气象状况，例如风、雪、阳光和温度。相比之下，气候是指特定地点经历的长期天气特征。本质上，气候是对天气状况的全面总结，考虑了长期内的变化。科学家认为温室气体（`GHGs`）会捕获 incoming 太阳能，导致地球表面变暖。`GHGs` 的急剧上升，特别是 `CO[2]`，会加剧温室效应，从而加剧气候变化。计算机模拟在气候建模中发挥着关键作用，帮助研究人员解读温室气体排放对地球气候的影响。

本研究涵盖的主题包括 `CO` 污染物的排放、森林火灾、气候变化适应、粮食安全、气候预测以及物理引导的机器学习。

## 6.2 一氧化碳污染物——维沙卡帕特南的统计趋势

一氧化碳（`CO`）已知会与其他气体反应，产生有害化合物。这种相互作用会影响其释放到大气中时温室气体的总量。对于本研究，`CO` 数据来自印度安得拉邦的维沙卡帕特南地区，采集时间为 2022 年 4 月、7 月和 12 月。数据被绘制成图表，以展示 `CO` 水平与特定日期之间在月度和小时层面的关系。Fig. 6–1 显示了月度趋势，表明 `CO` 水平在整个月内波动，而非保持一致。Fig. 6–2 表示所考虑的 3 个月的小时数据趋势。从趋势中可以注意到一个显著现象，即在所有月份的上午 10:00 曲线均出现下降。曲线在傍晚高峰时段上升，并在晚上 9:00 左右下降。

![Figure 6–1 The monthly trends of CO in Visakhapatnam.](img/F000092f06-01-9780443219054.jpg)

Figure 6–1 The monthly trends of CO in Visakhapatnam.

![Figure 6–2 The hourly trends of CO in Visakhapatnam.](img/F000092f06-02-9780443219054.jpg)

Figure 6–2 The hourly trends of CO in Visakhapatnam.

`CO` 的几个来源是森林火灾、火山、车辆排放和生物质燃烧。人类排放占大气中 `CO` 的三分之二。下文将探讨森林火灾对扰乱气候变化的影响。

## 6.3 森林火灾——自然空气污染——危害人类

森林是富含矿物质和丰富自然资源的储库。这些森林容易发生自然火灾，并在印度的一些邦以及世界的一些地区持续燃烧数天、数周甚至数月。加利福尼亚、西伯利亚和北美是森林火灾频繁发生、烧毁树木的著名地区。在印度，喜马偕尔邦是极易发生火灾的地区。森林火灾是生态系统的一部分，对财产和野生动物构成威胁，也是呼吸系统和心血管疾病的危险因素。

自然森林火灾会不可控制地破坏野生动物，并导致环境温度升高。火灾三角（热、氧气和燃料）有助于更快地燃烧森林中的绿树并迅速蔓延。因素包括温度、土壤湿度以及树木、灌木和其他潜在燃料的存在（Pacha, 2020）。Goodman and Horton (2021) 报道称，印度最易发生火灾的邦是东北部一些地区、中央邦、奥里萨邦、恰蒂斯加尔邦、喜马偕尔邦和喜马偕尔邦。2020 年（美国）有超过 350 万英亩土地被烧毁，成为有记录以来破坏最严重的季节（Kinver, 2021）。

根据欧盟的地球监测服务，西伯利亚、北美以及地中海周边地区的野火排放了 `CO[2]`，创下了使地球变暖的纪录（France-Presse, 2021）。欧洲中期天气预报中心的大气监测服务（`CAMS`）在 2021 年报告称，全球森林树木燃起大火，在 7 月和 8 月排放了超过 25 亿吨 `CO[2]`——相当于印度所有不同来源的年排放量。Cerdà (2019) 指出，7 月份野火排放的 `CO[2]` 中超过一半来自北美和西伯利亚。

森林火灾在扰动期间会增加沉积物和水产出（Katila et al., 2019）。可持续发展目标（`SDG`）削弱了森林对气候和发展的贡献（Baumgartner, 2019）。森林砍伐和森林火灾是实现可持续发展目标的主要问题，即该地区面临极端天气事件脆弱性增加（`SDG 1`），观察到降雨损失和作物传粉者（`SDG 2`），以及森林火灾可能导致严重的呼吸道疾病（`SDG 3`）（[`www.weforum.org/agenda/2020/09/climate-feedback-climate-change-forest-fires`](https://www.weforum.org/agenda/2020/09/climate-feedback-climate-change-forest-fires)）。

2019 年 4 月，韩国高城火灾（Hirschlag, 2023）成为该国最具毁灭性的野火，肆虐 3 天，吞噬 529 公顷土地，摧毁 2000 多座建筑，并导致约 4200 人疏散。这场大火造成估计 460 万美元的损失，并夺去两条生命。

野火释放出大量细颗粒物（`PM[2.5]`）甚至更细的纳米颗粒，对人类健康有害。这些微小颗粒比人类头发细 30 倍，可以轻松穿透肺膜并损害呼吸系统，进入血液循环（Aguilera et al., 2021）。到 2019 年底，在澳大利亚的丛林大火期间，由于新南威尔士州的野火，呼吸问题导致的住院人数增加了 34%。

美国西部 2004–09 年的森林火灾研究估计，大约有 46 M 人暴露于烟雾波中。烟雾导致 `PM[2.5]` 水平升高，因呼吸系统疾病住院率增加了 7.2%。研究得出结论，该年造成了 339,000 例过早死亡。空气净化器中的高效颗粒空气过滤器（`HEPA`）过滤器可以减少室内细颗粒物。

美国国家航空航天局的研究人员发现，地球周围在南极洲等地的对流层中被烟雾笼罩。它影响了全球火灾产生的五分之一气溶胶。吸入这种大小的颗粒会引起多种健康问题，如心脏病、中风、慢性阻塞性肺病以及包括肺炎在内的下呼吸道感染。研究估计，加利福尼亚北部野火在一周内释放的 `CO[2]` 就与 2017 年加利福尼亚所有汽车和卡车全年释放的量相当，估计 `PM[2.5]` 排放量更高。

1950 年 6 月，Chinchaga 火灾在加拿大不列颠哥伦比亚省开始，蔓延失控，并在 5 个月后于阿尔伯塔省结束；估计该火灾烧毁了约 1.2 M 公顷（3 M 英亩）的北方森林，而 2020 年记录的火灾烧毁了 1.6 Mha，2021 年在加利福尼亚，共有 16 kha 的森林被烧毁。

20 世纪初，加利福尼亚、华盛顿和俄勒冈的气温急剧上升。西北地区降雨取代了降雪，气温升高导致积雪减少，土壤干涸。所有这些因素结合起来造成了更干燥的条件，使野火更容易点燃和蔓延。2020 年的火灾排放量是 21 世纪历史平均水平的华盛顿和俄勒冈的三倍。在加利福尼亚，野火产生的排放量比全州所有经济活动的日排放量高出 4–8 倍。随着 `CO[2]` 浓度的升高，全球气温升高已被观察到。

在 1999–2012 年期间对加利福尼亚森林火灾的研究中，随着野火特异性 `PM[2.5]` 每增加 10 μg/m³，呼吸系统住院率的增加范围为 1.3% 至 10%（Holm et al., 2021）。野火排放的主要成分是有机碳和元素碳，以及气体，包括 `CO[2]`、`CO`、`NO[2]` 和挥发性有机化合物（`VOC`）。儿科哮喘就诊次数有所增加，总体上儿童在野火期间反复高暴露时有长期健康影响的潜在风险（Reid & Maestas, 2019）。研究指出，野火烟雾的长期呼吸健康影响会使暴露后 10 年肺功能下降（[`bhuvan.nrsc.gov.in/home/index.php`](https://bhuvan.nrsc.gov.in/home/index.php)）。

### 6.3.1 森林火灾造成的经济损失结果

经济损失（Table 6–1）按印度各州从 2013 年到 2018 年因森林火灾造成的损失表示。最高的是 2016 年和 2018 年的喜马偕尔邦。Table 6–2 表示印度森林调查局（`FSI`）使用 Modi 传感器检测到的 2018–20 年期间印度森林火灾的最高数量。记录到的火灾数量最多的是马德亚 Pradesh（`MP`）（4929）、米佐拉姆（2795）和阿萨姆（3000）。

**Table 6–1**  
印度经济损失（按州，2013–18）。

| State | Loss in terms of the currency value in INR (year-wise) |
| --- | --- |
|  | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 |
| Mizoram | – | – | 15.32 | 1.25 | 0.64 | – |
| Uttarakhand | 4.39 | 23.57 | 7.94 | 46.5 | 18.34 | 86.05 |
| Uttar Pradesh | – | – | 0.27 | – | 8.21 | 0.27 |
| Himachal Pradesh | 52 | 100 | 130 | 300 | 55 | 300 |
| Meghalaya | – | – | – | – | 7.2 | – |
| Kerala | – | – | 0.35 | 0.22 | 2.49 | – |

*Source*: From Ministry of Environment, Forest and Climate Change. ([`moef.gov.in/`](https://moef.gov.in/)).

**Table 6–2**  
印度森林调查局使用 Modi 传感器检测到的印度森林火灾数量（按州，2018–20）。

| States | Jan–June 2018 | Nov 2018–June 2019 | Nov 2019–June 2020 |
| --- | --- | --- | --- |
| Assam | 1660 | 1940 | 3000 |
| Madhya Pradesh | 4929 | 2723 | 1383 |
| Mizoram | 2339 | 2795 | 2816 |

*Source:* [`www.data.gov.in`](http://www.data.gov.in).

Fig. 6–3 显示了 2021 年 10 月 15 日至 20 日期间印度部分地区森林火灾的发生情况，树木持续燃烧。数据取自 ISRO 的 Bhuvan 网站。

![Figure 6–3 Forest fires from October 15 to 20, 2021 (https://bhuvan.nrsc.gov.in/home/index.php). Map lines delineate study areas and do not necessarily depict accepted national boundaries.](img/F000092f06-03-9780443219054.jpg)

Figure 6–3 2021 年 10 月 15 日至 20 日的森林火灾（[`bhuvan.nrsc.gov.in/home/index.php`](https://bhuvan.nrsc.gov.in/home/index.php)）。地图线划定研究区域，不一定描绘公认的国家边界。

人工神经网络（`ANNs`，Al-Kahlout et al., 2020; Nebot & Mugica, 2021; Safi & Bouroumi, 2013）和支持向量机（Li et al., 2020）也被用于预测森林火灾。

**Table 6–3**  
森林火灾特征。

| Parameter | Description |
| --- | --- |
| **Spatial attributes** | |
| X | `x`-axis |
| Y | `y`-axis |
| **Temporal attributes** | |
| Month | Month (in year) |
| Day | Day (in week) |
| **Fire weather index attributes** | |
| FFMC | Fine fuel moisture code |
| DMC | Duff moisture code |
| ISI | Initial spread index |
| DC | Drought code |
| **Weather attributes** | |
| Temp | Outer temperature (°C) |
| RH | Outer relative humidity (%) |
| Wind | Outer wind speed (km/h) |
| Rain | Outer rain (mm/m²) |
| Area | Total area burnt (ha) |

![Figure 6–4 Convolution Neural Network model predicts potential forest fire occurrences. This diagram showcases the model’s architecture and data flow, with inputs derived from various forest fire characteristics (as outlined in Table 6–3) leading to the prediction of both the subsequent fire event’s date and the approximate area at risk of burning.](img/F000092f06-04-9780443219054.jpg)

Figure 6–4 卷积神经网络模型预测潜在森林火灾发生情况。该图展示了模型的架构和数据流，输入源自各种森林火灾特征（见 Table 6–3 所述），从而预测下一场火灾事件的日期以及可能被烧毁的近似面积。

根据 Buonocore et al. (2022)，数字孪生技术使公用事业公司能够在任何给定天气条件下模拟任何灾害发生的可能性。森林数字孪生框架被提出并用于森林管理。实时跟踪和预测借助数字孪生技术有助于保护公众健康免受空气质量风险的影响（Jiao et al., 2023）。自动飞行计划创建使用数字孪生，以利用人工智能实现无人机（`UAV`）状态监测和预测用于森林火灾（Bae et al., 2022）。数字孪生（Sahal et al., 2021）通过利用运营数据智能提供自动检测。Yun et al. (2022) 提出了数字孪生的架构，以提供用于预测灾害的准确服务。

## 6.4 气候变化适应

联合国秘书长安东尼奥·古特雷斯曾评论道：“气候变化是我们这个时代的决定性问题……我们每一天不作为，都是我们更接近我们都不想要的命运的一天——一个将在人类和地球生命造成的损害中世代回响的命运”（[`www.undrr.org/climate-action-and-disaster-risk-reduction`](https://www.undrr.org/climate-action-and-disaster-risk-reduction)）。

有令人信服的证据表明全球平均气温和海洋温度上升，雪和冰加速融化，海平面上升。这种深刻的转变导致气候变化，进而以两种重要方式加剧灾害风险。

1. 天气和气候灾害的放大，以及
2. 由于生态系统退化以及水和粮食资源可用性减少，社区对自然灾害的脆弱性加剧。

某些地区经历了加剧的干旱、作物受损以及野火风险增加。相反，降水增加的地区容易发生洪水和山体滑坡，这通常会导致大量人员伤亡和资产损失。

政府间气候变化专门委员会（`IPCC`）将减缓描述为：“人为干预以减少气候系统的人为强迫；它包括减少温室气体来源和排放以及增强温室气体汇的策略”（Edenhofer, 2014）。

各种机器学习技术已应用于气候研究，例如降雨预测，以及使用多层感知器神经网络算法预测干旱（Ali et al., 2017）。开发了一个 `ANN` 模型来估算土耳其的日平均年太阳辐射，从而创建了基于卫星的太阳辐射图（Şahin et al., 2013）。地理信息系统和贝叶斯信念网络被引入用于评估多伦多的洪水脆弱性指数（Abebe et al., 2018）。`ANN` 模型已被应用于气候变化适应（`CCA`）政策（Biesbroek et al., 2020），而 `CNNs` 已被用于野火检测（Oh et al., 2020）。此外，在 Jain et al. (2023) 的研究中，人工智能（`AI`）已被确定为 `CCA` 的有前景的工具。

## 6.5 粮食安全——气候变化的影响
