

## 2.3 结论

在现代，各国有必要拥有充足的网络安全（CS）能力，以有效应对与个人数据泄露、网络犯罪或其他恶意行为相关的网络安全风险。全球网络安全指数（GCI）旨在为此类能力提供适当的评估，并可作为基准测试计划的一部分。在本章中，我们探讨了全球南方国家（或“发展中”国家）与其余国家在 GCI 及其支柱方面的一些差异。即使就基准测试问题而言，除了我们已探讨的问题外，还有其他相关的研究问题可供开发和实证评估。还有其他类型的问题可供探讨（例如 [Bruggemann, Koppatz, Scholl & Schuktomow, 2021](#ch2.xhtml#ref2_1)）。因此，鼓励对这些 GCI 数据进行进一步探索。

## 参考文献

*   [Bruggemann, R., Koppatz, P., Scholl, M., & Schuktomow, R.](#ch2.xhtml#R_ref2_1) (2021). Global Cybersecurity Index (GCI) and the role of its 5 pillars. Social Indicators Research, 1–19. doi:[10.1007/s11205-021-02739-y](http://dx.doi.org/10.1007/s11205-021-02739-y)

*   [Dados, N., & Connell, R.](#ch2.xhtml#R_ref2_2) (2012). The Global South. Contexts, *11*(1), 12–13.

*   [ITU](#ch2.xhtml#R_ref2_3) (2020): Global Cybersecurity Index 2020. Retrieved from: [https://www.itu.int/en/ITU-D/Cybersecurity/Documents/GCIv4/New_Reference_Model_GCIv4_V2_.pdf](https://www.itu.int)

*   [Osei-Bryson, K. M., & Ngwenyama, O.](#ch2.xhtml#R_ref2_4) (2014). Advances in Research Methods for Information Systems Research. New York, USA: Springer. doi:[10.1007/978-1-4614-9463-8](http://dx.doi.org/10.1007/978-1-4614-9463-8).

## 针对 RQ2 的分析：决策树归纳

为解决 RQ2，我们进行了决策树（DT）归纳（例如 [Osei-Bryson & Ngwenyama, 2014](#ch2.xhtml#ref2_4)），正确分类率达到了 0.834。相应结果（见 [图 2.2](#ch2.xhtml#fig2_2)）再次表明 `Technical`（技术）和 `Capacity Development`（能力建设）支柱是显著预测因子，但也显示了这些指标的临界点。不出所料，`Technical` 支柱指标的极值分别由全球南方国家组或其他国家组主导。但对于 `Technical` 支柱指标的内部区间，是 `Capacity Development` 的水平区分了这两个群体。鉴于 `Capacity Development` 支柱的特性，`Technical` 指标水平处于此内部区间的全球南方国家应重点提升其 `Capacity Development` 水平，因为这可能比相应提升 `Technical` 支柱水平更负担得起。

![Figure 2.2 Results of decision tree induction](images/fig2_2_B.jpg)

[图 2.2 决策树归纳结果](#ch2.xhtml#R_fig2_2)

## 针对 RQ3 的分析：相关性分析

为解决 RQ3，我们对 2019 年的 `HDI`（人类发展指数）与 2020 年 `GCI` 及其支柱得分进行了相关性分析。虽然使用 2020 年的 `HDI` 得分可能更有用，但在撰写本章时，这些数据尚未公开。然而，也应注意到，有合理理由认为前一年的 `HDI` 水平可能影响当年的 `GCI` 得分。

[表 2.2](#ch2.xhtml#table2_2) 提供了 `Global South` 组和 `Others` 组的相关性分析结果。读者可能会注意到，对于每种组合，`Global South` 组的相关性水平均小于 `Others` 组。一种解释是，对于 `Global South` 组，其整体 `GCI` 及相关支柱的较低水平可能并非由于其相应的 `HDI` 水平。另一种解释可能是，对于 Others 组，GCI 指数可能与其相应的 HDI 水平相关。

[表 2.2 分组相关性分析结果](#ch2.xhtml#R_table2_2)

| **组别** | **HDI:GCI** | **HDI:Tech** | **HDI:CapDev** | **HDI:Legal** | **HDI:Org** | **HDI:Coop** |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| Global South | 0.228 | 0.218 | 0.244 | 0.233 | 0.159 | 0.182 |
| Others | 0.595 | 0.591 | 0.549 | 0.542 | 0.514 | 0.603 |

*HDI 为 2019 年（最新可用）；GCI 为 2020 年（最新可用）*

### 按区域的相关性分析

为获得更深入的见解，我们进行了类似的相关性分析，重点关注区域间的差异（见 [表 2.3](#ch2.xhtml#table2_3) 和 [图 2.4](#ch2.xhtml#fig2_4)），以及美洲次区域间的差异（见 [表 2.4](#ch2.xhtml#table2_4) 和 [图 2.5](#ch2.xhtml#fig2_5)）。这些结果表明，某些区域对之间的相关性存在实质性差异，包括亚太地区与欧洲的对比。可能令人惊讶的是，阿拉伯国家和独联体（CIS）地区的相关性最高。同样有趣的是，非洲和欧洲地区的相关性最低，尽管导致这些低相关性的原因可能不同。这些结果也表明美洲次区域存在差异。加勒比地区的相关性比任何其他地区都更接近非洲地区。此外，除 HDI:Legal 相关性外，均低于非洲地区。在比较区域时，包括美洲次区域和其他区域，加勒比和非洲地区的 HDI:GCI 相关性最低（[图 2.6](#ch2.xhtml#fig2_6)）。北美拥有最高的 HDI:GCI 相关性；不过，这可能用该地区国家数量相对较少来解释。值得注意的是，这三个北美国家被视为美洲最强大、经济最成熟的国家，其中两个是美洲唯一的 G7 成员国。其他 HDI:GCI 相关性较高的组别依次为拉丁美洲和阿拉伯地区，随后是亚太和独联体地区。

![Figure 2.4 Graphic display of correlations by region](images/fig2_4_B.jpg)

[图 2.4 按区域划分的相关性图形显示](#ch2.xhtml#R_fig2_4)

![Figure 2.5 Graphic display of correlations by sub-regions of the Americas](images/fig2_5_B.jpg)

[图 2.5 美洲次区域相关性图形显示](#ch2.xhtml#R_fig2_5)

![Figure 2.6 Graphic display correlations by regions (including sub-regions of the Americas)](images/fig2_6_B.jpg)

[图 2.6 按区域划分的相关性图形显示（含美洲次区域）](#ch2.xhtml#R_fig2_6)

[表 2.3 按区域划分的相关性分析结果](#ch2.xhtml#R_table2_3)

| **区域** | **HDI:GCI** | **HDI:Tech** | **HDI:CapDev** | **HDI:Legal** | **HDI:Org** | **HDI:Coop** |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| Africa | 0.331 | 0.243 | 0.387 | 0.277 | 0.298 | 0.340 |
| Americas | 0.609 | 0.558 | 0.517 | 0.688 | 0.487 | 0.577 |
| Arab | 0.796 | 0.724 | 0.844 | 0.711 | 0.707 | 0.765 |
| Asia-Pacific | 0.642 | 0.660 | 0.579 | 0.573 | 0.673 | 0.597 |
| CIS | 0.668 | 0.723 | 0.638 | 0.406 | 0.495 | 0.758 |
| Europe | 0.381 | 0.381 | 0.381 | 0.238 | 0.353 | 0.381 |

[表 2.4 美洲次区域相关性分析结果](#ch2.xhtml#R_table2_4)

| **次区域** | **HDI:GCI** | **HDI:Tech** | **HDI:CapDev** | **HDI:Legal** | **HDI:Org** | **HDI:Coop** |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| Caribbean | 0.166 | 0.133 | −0.111 | 0.486 | −0.008 | 0.210 |
| Latin America | 0.740 | 0.754 | 0.623 | 0.722 | 0.567 | 0.647 |
| North America | 0.991 | 0.622 | 1.000 | 1.000 | 1.000 | 0.974 |

