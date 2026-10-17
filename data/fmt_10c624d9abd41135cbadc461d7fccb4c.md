
气候引起的温度、降水和降雨模式变化已影响产量质量和食品安全。粮食可获得性是确保粮食安全和生活水平的基本方面（Karanth et al., 2023）。机器学习（`ML`）算法和基因组预测提供了创新技术，以加快育种工作，增加作物产量以应对干旱和气温升高（Cortés & Lopez-Hernandez, 2021）。强降雨增加将导致人类污水溢出污染其他水源，导致各种水源性疾病。强降雨将增加蚊子和其它昆虫的繁殖，导致疟疾、霍乱、登革热、腹泻、伤寒和钩端螺旋体病等各种疾病。此外，温度的轻微上升将影响气候变化，增加人类感染风险。温度升高会危及本土获得性疾病，导致`Campylobacter` sp.在食物上生长（Semenza et al., 2012）。温度升高将增加食物中毒和变质的风险，除非采取必要的措施，如延长冷链得到改善（James & James, 2010）。气候变化对粮食安全有影响（Uyttendaele et al., 2015）。名为气候变化与食品安全新兴风险（`CLEFSA`）的项目解决了不确定性，并通过科学研究证明了随温度升高食源性疾病的风险（Maggiore et al., 2020）。

## 6.6 预测气候和天气

### 6.6.1 TrajGRU 临近预报

临近预报是指开发`AI`算法用于超短期预报。使用遥感技术，它可提前约 3 小时预测天气。临近预报与局部天气现象有关，例如雷暴、气旋和极端温度变化。超短程预报为 0 至 6 小时，短程预报长达 72 小时。临近预报描述当前天气状况并外推数小时，假设预测降水模式没有显著改变。

布鲁诺·凯斯勒基金会和 Arpae 引入了两种不同的`TrajGRU`方法用于临近预报意大利北部气候：

1. 2022 年 5 月 28 日意大利北部的一次对流事件
2. 2022 年 4 月 22 日的一次层状事件

对流涉及在不稳定环境中由于上升气流和下沉气流导致大气中热量和湿气的垂直输送。相比之下，层状是指大范围气流因大尺度风和大气动力学迫使它们斜向叠加的情况。

变量反射率（`Z_60`）和其他此类纬度、经度、地理地图限制以及以度为单位的数据分辨率。

数据来源为[`climateindex.eu/`](https://climateindex.eu/)。`TrajGRU` model 1 利用反射率图像作为训练输入进行临近预报，如图 6–5 所示。该图展示了用作输入的反射率图像，不同的颜色梯度代表不同强度的降水。可以观察到 2022 年 5 月 28 日对流事件和 2022 年 4 月 22 日层状事件的模式。标注指示了关键地理区域和气象现象。地图边界、纬度和经度线为预报区域提供了地理背景。

![Figure 6–5 Visualization of the TrajGRU model 1 outputs for nowcasting forecasts in Northern Italy. Map lines delineate study areas and do not necessarily depict accepted national boundaries.](img/F000092f06-05-9780443219054.jpg)

Figure 6–5 Visualization of the `TrajGRU` model 1 outputs for nowcasting forecasts in Northern Italy. Map lines delineate study areas and do not necessarily depict accepted national boundaries.

`TrajGRU` model 2 使用反射率图像和闪电数据进行临近预报训练，如图 6–6 所示。闪电数据源自空军气象局运营的 LAMPINET 网络。颜色梯度代表不同级别的反射率，而闪电发生由不同的标记指示。

![Figure 6–6 TrajGRU model with reflectivity images and lightning. Map lines delineate study areas and do not necessarily depict accepted national boundaries.](img/F000092f06-06-9780443219054.jpg)

Figure 6–6 `TrajGRU` model with reflectivity images and lightning. Map lines delineate study areas and do not necessarily depict accepted national boundaries.

### 6.6.2 Case study of Italy (E³CI)

**European Extreme Events Climate Index (E³CI)** is an innovative operational service designed for weather-induced hazard assessment and management. It is supported by the Foundation Big Data and Artificial Intelligence for Human Development (IFAB).

For the E³CI of Italy during the period 1981–2010, one can observe average values close to zero on the same period. However, larger values have been noted in recent years, attributed to the effects of climate change. The mean of the components of E³CI is presented in Table 6–4.

Table 6–4

Mean of components of E³CI for Italy (1981–2010).

| Components | Mean |
| --- | --- |
| Cold stress | −0.000525 |
| Drought | −0.002776 |
| E³CI | −0.000994 |
| Extreme precipitation | −0.000536 |
| Extreme wind | −0.001316 |
| Heat stress | 0.000184 |

Fig. 6–7 displays the increasing magnitude of extremes, as represented by components such as extreme precipitation, extreme wind, heat stress, alongside the composite E³CI index for the year 1980, 1990, 2000, 2010, and 2020. A spatial pattern reflecting the country-wide average value for Italy is depicted in Fig. 6–8.

![Figure 6–7 Temporal analysis of extreme events in Italy (1980–2020). This figure displays the increasing magnitude of extreme events over the decades. The components illustrated include extreme precipitation, extreme wind, and heat stress, in conjunction with the composite E3CI index.](img/F000092f06-07-9780443219054.jpg)

Figure 6–7 Temporal analysis of extreme events in Italy (1980–2020). This figure displays the increasing magnitude of extreme events over the decades. The components illustrated include extreme precipitation, extreme wind, and heat stress, in conjunction with the composite E³CI index.

![Figure 6–8 Spatial pattern of average extreme event values in Italy. This map visualizes the country-wide average values of extreme events in Italy, providing a spatial representation of regions most affected by climate-induced extremes. Map lines delineate study areas and do not necessarily depict accepted national boundaries.](img/F000092f06-08-9780443219054.jpg)

Figure 6–8 Spatial pattern of average extreme event values in Italy. This map visualizes the country-wide average values of extreme events in Italy, providing a spatial representation of regions most affected by climate-induced extremes. Map lines delineate study areas and do not necessarily depict accepted national boundaries.

The ERA5 dataset for the country Italy and Germany is obtained from [`e3ci.dataclime.com/`](https://e3ci.dataclime.com/). This dataset includes parameters such as cold stress, forest fires, drought, heat stress, extreme wind and precipitation, and E³CI, spanning the period from January 1981 to August, 2023 (as depicted in Figs. 6–9 and 6–14). The graphs were plotted using `STATA 12`. Since the data contain both positive and negative values for the parameters, the graphs may display curves below the 0 mark.

![Figure 6–9 ERA5 of Italy.](img/F000092f06-09-9780443219054.jpg)

Figure 6–9 ERA5 of Italy.

Fig. 6–10 displays the E³CI model’s representation of extreme precipitation for Italy in April 2023, sourced from an interactive map. Similarly, Fig. 6–11 shows the model’s output for August 2023. The interactive map and model details can be accessed at [`www.ifabfoundation.org/e3ci/`](https://www.ifabfoundation.org/e3ci/). The map illustrates areas of varying precipitation intensity across the country, providing insights into regions most impacted by rainfall during this month.

![Figure 6–10 E3CI model representation of extreme precipitation for Italy in April 2023. Map lines delineate study areas and do not necessarily depict accepted national boundaries.](img/F000092f06-10-9780443219054.jpg)

Figure 6–10 E³CI model representation of extreme precipitation for Italy in April 2023. Map lines delineate study areas and do not necessarily depict accepted national boundaries.

![Figure 6–11 E3CI model representation of extreme precipitation for Italy in August 2023. Map lines delineate study areas and do not necessarily depict accepted national boundaries.](img/F000092f06-11-9780443219054.jpg)

Figure 6–11 E³CI model representation of extreme precipitation for Italy in August 2023. Map lines delineate study areas and do not necessarily depict accepted national boundaries.

### 6.6.3 Case study of Germany (E³CI)

In Germany, seasonal analysis was performed based on the parameters by heat stress, cold stress, drought, extreme precipitation, and extreme wind as depicted in Fig. 6–12. Additionally, extreme precipitation was charted for Belgium, Luxembourg, Germany, Italy, and the Netherlands, with notable findings for Belgium in July 2021 (see Fig. 6–13).

![Figure 6–12 Seasonal analysis of various climatic parameters.](img/F000092f06-12-9780443219054.jpg)

Figure 6–12 Seasonal analysis of various climatic parameters.

![Figure 6–13 Comparative chart showing extreme precipitation for the countries of Belgium, Luxembourg, Germany, Italy, and the Netherlands. Map lines delineate study areas and do not necessarily depict accepted national boundaries.](img/F000092f06-13-9780443219054.jpg)

Figure 6–13 比较比利时、卢森堡、德国、意大利和荷兰极端降水的图表。地图线划定了研究区域，不一定代表公认的国界。
