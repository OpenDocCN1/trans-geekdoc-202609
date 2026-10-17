
![Fig. 24](img/#Ch006_107-168_S0169716122000578.xhtml#f0125) 使用迁移学习的 VGG 16 性能曲线。

如 Fig. 25 所示，我们可以看到真实分类类别沿主轴分布，从而可以判断模型在前两类茶叶上的表现较好，而在第三、第四类茶叶上表现不佳。总体来看，我们获得了 0.85 的精确率、0.76 的召回率以及 0.9 的 F1 分数。

![Fig. 25](img/#Ch006_107-168_S0169716122000578.xhtml#f0130) 基于不同类别的茶叶分类混淆矩阵。

### 3.8：将天气信息整合到深度学习技术中，用于预测印度各州的 COVID-19 案例数

时间序列数据展示了实验室确认的 COVID-19 案例在印度部分州份（最大病例数出现在第一、第二、第三波）的每日病例数（Fig. 26）。虽然第一例于 2020 年 1 月 30 日报告，但最高病例数（截至 2020 年 9 月在马哈拉施特拉邦每日 24,886 例）出现在第一波疫情期间。然而，COVID-19 的传播动态受多种参数影响，包括病毒变异、人口密度和免疫力、社会经济条件以及气候参数。第二波疫情严重冲击了大多数州份（马哈拉施特拉邦最高 68,631 例/天），主要是由于 delta（B.1.617.2）等更具毒性的变异株在 2021 年 4 月至 5 月（夏季）蔓延。第三波疫情主要由奥密克戎（B.1.1.529）这一高度传染性变异株主导，出现在 2022 年 2 月的冬季。然而，印度每日病例数最高的州仍是马哈拉施特拉邦，南印度的安得拉邦、卡纳塔克邦、喀拉拉邦和泰米尔邦，以及北印度的北方邦也贡献了大量病例。数据还显示，第二波疫情在印度高湿地区的喀拉拉邦一直持续到雨季结束。

![Fig. 26](img/#Ch006_107-168_S0169716122000578.xhtml#f0135) 不同时期印度不同州每日 COVID-19 案例时间序列分析（2020 年 4 月 1 日至 2021 年 12 月 31 日）。

Fig. 26 不同时期印度不同州每日 COVID-19 案例时间序列分析（2020 年 4 月 1 日至 2021 年 12 月 31 日）。

- [美国疾病控制与预防中心（CDC）报告显示，人们主要因吸入携带病毒的微小呼吸道飞沫和气溶胶、以及通过近距离接触被感染者的病毒载飞沫直接喷洒和溅射到黏膜（眼、口、鼻），或触摸被病毒污染的手后再接触黏膜而感染 SARS‑CoV‑2 病毒（来源：[`www.cdc.gov/coronavirus/2019-ncov`](https://www.cdc.gov/coronavirus/2019-ncov)/science/science‑briefs/sars‑cov‑2/transmission.html)。在空气传播的情况下，感染风险取决于空气中病毒云的浓度和活性，这主要取决于周围环境条件，如温度和湿度。源头的安全距离由室内外天气参数决定。为了了解天气参数对印度不同州份 COVID‑19 传播的影响，对 2020 年 4 月 1 日至 2021 年 12 月 31 日期间每日 COVID‑19 病例与包括特定湿度、平均最高温度、平均最低温度和平均温度在内的气象参数进行相关性分析。结果表明，特定湿度在安得拉邦、阿萨姆、喀拉拉邦、奥里萨邦、泰米尔纳德邦之间呈显著（置信度 99%）的正相关，而在恰蒂斯加尔邦、中央邦和马哈拉施特拉邦则呈显著的负相关。温度方面，大多数州份表现出显著的正相关，仅喀拉拉邦除外（Fig. 27）。具体湿度（SH）的时间序列图显示，空气中水汽含量高且季节性变化小的地区 COVID‑19 病例呈正相关，而干燥地区则与 COVID‑19 病例呈负相关（Fig. 27）。

![Fig. 27 (A) Correlation between the daily COVID‑19 cases and the meteorological parameters Specific Humidity (SH), Maximum Temperature (Tmax), Minimum Temperature (Tmin), and Mean Temperature (Tmean) for the period 1st April 2020 to 31st December 2021. (B) Seasonal variability of specific humidity over some of the dry and wet regions in India (bottom figure).](img/f06-27-9780443184307.jpg)

Fig. 27 (A) Correlation between the daily COVID‑19 cases and the meteorological parameters Specific Humidity (SH), Maximum Temperature (Tmax), Minimum Temperature (Tmin), and Mean Temperature (Tmean) for the period 1st April 2020 to 31st December 2021. (B) Seasonal variability of specific humidity over some of the dry and wet regions in India (bottom figure)。

一些早期研究也报告称，环境条件在疾病传播及死亡率方面发挥重要作用。例如，Faruk et al. (2022) 进行研究，探讨环境因素对不同大洲 COVID‑19 传播的影响，发现温度对亚洲国家疾病传播具有显著的正相关，而相对湿度的作用不显著。Manik et al. (2022) 则利用 SIRD（易感‑感染‑恢复‑死亡）和 SEIRD（易感‑暴露‑感染‑恢复‑死亡）数学模型，研究了温度和湿度对再生数的影响，发现温度与再生数呈正相关，而相对湿度在印度部分州份则呈负相关。

为检验单变量和多变量 LSTM 模型在短期和中期预测中的能力，在第三波疫情期间对印度选定州份的每日 COVID‑19 预测数据进行了生成，模型初始化时间跨度为 1–14 天。Fig. 28 展示了在 2022 年 1 月 1 日至 2022 年 2 月 14 日期间，不同印度州份的实验室确认病例与单变量及多变量模型预测的每日病例（lead 1）对比。时间序列图表明，在第三波疫情期间，1 天预测 lead time 的模型在预测大多数受影响严重的州份（包括马哈拉施特拉邦、喀拉拉邦、安得拉邦、卡纳塔克邦和泰米尔纳德邦）表现非常出色。印度南部州份主要受第三波疫情影响。2022 年 1 月最后一周，印度每日病例最高分别出现在喀拉拉邦（55,475 例）、卡纳塔克邦（50,210 例）、马哈拉施特拉邦（48,270 例）和泰米尔纳德邦（30,744 例）。多变量 LSTM 模型在 1 天预测 lead time 内捕捉了大多数印度州份的峰值。

![Fig. 28 Comparison between the laboratories confirmed COVID‑19 cases and univariate and multivariate model forecasted cases over some of the states in India during the period 1st January 2022 to 14th February 2022 (45 days).](img/f06-28-9780443184307.jpg)

Fig. 28 Comparison between the laboratories confirmed COVID‑19 cases and univariate and multivariate model forecasted cases over some of the states in India during the period 1st January 2022 to 14th February 2022 (45 days)。

相对误差（RE）分析也表明，lead 1 预测的误差在大多数选定州份均低于 25%，仅阿萨姆例外（Table 9）。单变量和多变量模型在短期预测（lead 1–lead 3）表现相当。在中期预测（lead 4–lead 14）中，经过天气参数优化的多变量模型的误差低于单变量模型在大多数选定州份（Fig. 29）。

Table 9

2022 年 1 月 1 日至 2022 年 2 月 14 日期间，印度不同州份每日 COVID‑19 病例预测的平均相对误差。

| 州份 | CTL | CTL_SH | CTL_Tmax | CTL_Tmean | CTL_Tmin |
| --- | --- | --- | --- | --- | --- |
| 安得拉邦 | 22.07 | 20.91 | 22.1 | 21.87 | 22.57 |
| 阿萨姆 | 42.98 | 38.07 | 38.11 | 37.22 | 37.28 |
| 恰蒂斯加尔邦 | 22.25 | 23.22 | 22.49 | 23.52 | 25.33 |
| 卡纳塔克邦 | 21.11 | 19.83 | 22.39 | 22.08 | 20.03 |
| 喀拉拉邦 | 16.63 | 17.08 | 17.17 | 16.66 | 16.96 |
| 中央邦 | 20.15 | 19.25 | 23.09 | 22.64 | 22.61 |
| 马哈拉施特拉邦 | 18.07 | 17.41 | 19.17 | 18.85 | 17.76 |
| Rajasthan | 23.96 | 23.91 | 26.57 | 25.83 | 24.95 |
| 泰米尔纳德邦 | 13.32 | 13.61 | 14.63 | 15.63 | 14.18 |
| 特伦甘纳邦 | 18.54 | 18.05 | 19.5 | 20.64 | 19.8 |
| 乌特拉邦 | 20.53 | 22.82 | 20.95 | 20.93 | 25.87 |
| 西孟加拉邦 | 20.85 | 19.54 | 20.71 | 21.08 | 20.34 |

![Fig. 29 Skill (Average relative error) of univariate (CTL) and multivariate (CTL_SH, CTL_Tmax, CTL_Tmin, CTL_Tmean) LSTM models during the third wave (1st January 2022 to 14th February 2022) in India. Here, the L1 to L14 represents the model lead time (initialization) to generate the day 1 COVID‑19 case forecast for the selected state.](img/f06-29-9780443184307.jpg)

Fig. 29 Skill (Average relative error) of univariate (CTL) and multivariate (CTL_SH, CTL_Tmax, CTL_Tmin, CTL_Tmean) LSTM models during the third wave (1st January 2022 to 14th February 2022) in India. Here, the L1 to L14 represents the model lead time (initialization) to generate the day 1 COVID‑19 case forecast for the selected state。

在印度的第三波 COVID-19 浪潮中，印度南部的高湿度州份受到的影响比印度的其他州份更严重。该地区的特定湿度与 COVID-19 病例呈正相关关系。我们的模型结果也证实了，特定湿度集成的多变量 LSTM 模型在中程预测中，其相对误差低于其他气象参数。例如，CTL 和 CTL_SH 实验的 7 天（lead 7）预测的平均相对误差分别为 59.6% 和 52%，这表明将特定湿度数据集成到 LSTM 模型中，误差降低了超过 7%。同样，最低温度数据的集成降低了旁遮普邦、特伦甘纳邦、恰特斯加尔和卡纳塔克的模型误差，平均温度数据的集成则降低了西孟加拉邦和阿萨姆地区的模型误差。在拉贾斯坦邦和中央邦地区，集成最高温度数据后，模型误差相较于其他气象数据有所下降。

## 4: Discussion and future prospects

本章展示了来自 CSIR 印度的多学科研究人员的协作尝试，他们在工业和科学研究中实施了深度学习工具和方法的鲁棒性。最先进的方法以及多种格式的实时数据正在被分析，用于医药、医疗保健、农业、能源等主要行业。深度学习在癌症患者的当前临床护理中具有巨大的潜力，能够带来颠覆性变化并推动精准医学的发展（Ntakolia et al., 2020）。在医疗领域，我们展示了利用深度学习模型分析多组学数据，以诊断和预后胶质母细胞瘤患者（Bhalla and Lagana, 2022）。组织病理和 MRI 扫描主要用于肿瘤的诊断和预后，深度学习模型被用于确定分子亚型并预测体细胞基因突变状态（Lotlikar et al., 2021）。我们还表明，对于某些数值分子数据集，支持向量机（SVM）和随机森林（RF）等机器学习算法也能够预测胶质母细胞瘤的组织病理等级。然而，深度学习模型在实现临床应用所需的精度方面优于 SVM 和 RF 模型。深度学习还可以通过分析患者的分子数据以及组织病理和放射学影像，自动化并加速癌症患者的临床决策。

在本章中，我们还展示了基于 LSTM 的深度学习模型在作物产量评估方面的应用，以及茶叶分类的迁移学习。同样，集群 LSTM 模型被用于印度两个站点的短期风速预测，结果表明其对短期天气预报非常有用。我们还展示了 LSTM 模型（深度学习/机器学习）预测 COVID-19 在印度不同州份中非线性传播行为的能力。早期的研究也表明，气象参数对疾病传播在大多数地区具有显著影响，因此我们有动力将气象数据集成到 LSTM 模型中，以检验模型在印度不同地理位置的州份的预测能力。我们的模型预测是基于第三波（2022 年 1 月 1 日至 2 月 14 日）的数据，使用第一波和第二波确认病例数据（2021 年 4 月 1 日至 2021 年 12 月 31 日）进行训练。我们的结果表明，当模型预测的初始条件为 lead 1 时，LSTM 模型的预测能力非常好（相对误差 RE <25%）在印度大多数选定州份中。然而，随着预测时 lead time（从 lead 1 到 lead 14）的增加，模型错误在大多数州份也在增长，从而限制了预测能力。为了提高更长 lead time 的预测能力，我们将气象参数集成到 LSTM 模型中。结果表明，将气象参数纳入模型系统后，预测能力在 lead 2 到 lead 14 的更长范围内得到改善。我们观察到，包含温度时间序列数据的多变量 LSTM 模型能够降低印度大多数州份的模型误差。然而，特定湿度的集成降低了印度南部高湿地区（包括喀拉拉邦、泰米尔纳德邦和安得拉邦）的模型误差。本研究表明，在印度将气象数据集成到 LSTM 模型中，可提升中程预测的预测能力。进一步将人口密度、免疫信息、社会经济和迁移数据纳入 LSTM 模型系统，预测能力可能会进一步提升。此外，这些基于深度学习的模型可以与数学建模系统相结合，进一步提升预测能力，帮助公共卫生部门进行疫情准备、物流管理和政策决策。

然而，深度学习在医疗、医疗保健和天气预报等关键行业实施前，仍需克服若干局限性。对深度学习卷积神经网络（CNN）的主要批评之一是其“黑盒”方法（Jin et al., 2022）。在没有对其输出进行适当解释的情况下，深度学习模型在对癌症患者作出关键临床决策时不能盲目信任。为解决此问题，我们需要在深度学习中实施白盒方法，以解释和识别对其输出最重要的特征（Jin et al., 2022）。预计，随着可解释人工智能的出现，深度学习模型很快将能够在临床环境中成功应用于癌症护理和管理。

## Acknowledgments

作者们感谢 CSIR 的资助支持，以及所有 CSIR 实验室的主任们在基础设施支持和鼓励方面的提供。

## References

* Aguilar-Morante D., Gomez-Cabello D., Quek H., Liu T., Hamerlik P., Lim Y.C. Therapeutic opportunities of disrupting genome integrity in adult diffuse glioma. *Biomedicine.* 2022;10(2):332.
* Anders S., Pyl P.T., Huber W. HTseq—a Python framework to work with high-throughput sequencing data. *Bioinformatics.* 2015;31:166–169.
* Arunachalam H.B., Mishra R., Armaselu B., Daescu O., Martinez M., Leavey P., Rakheja D., Cederberg K., Sengupta A., Ni'suilleabhain M. Computer aided image segmentation and classification for viable and non-viable tumor identification in osteosarcoma. *Pac. Symp. Biocomput.* 2017;22:195–206.
* Ayris D., Imtiaz M., Horbure K., Williams B., Blackney M., See C.S.H., Shah S.A.A. Novel deep learning approach to model and predict the spread of COVID-19. *Int. Syst. Appl.* 2022;14:200068.
