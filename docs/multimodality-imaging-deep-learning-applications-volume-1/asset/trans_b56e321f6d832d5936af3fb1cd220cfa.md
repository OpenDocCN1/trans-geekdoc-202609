
-   [早期模型使用了多种图像特征，如纹理、亮度、对比度和颜色，用于划分边界。在这方面，El Barghouty *et al* \[[59](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8bib59)\] 使用了灰度中位数（GSM）来描述低风险和高风险。在另一项工作中，Acharya *et al* \[[40](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8bib40)\] 使用基于机器学习的模型来估算血栓图像中的风险。该论文首次提出了基于深度学习的狭窄风险调查。关于血管腔检测和基于狭窄的中风风险分析，已有一些工作完成，分别列于表格 [8.14](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8t14) 和 [8.15](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8t15)。

**表 8.14.** LD 错误基准表。 (经 \[[66](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8bib66)\] 许可复制。)

| 作者 | 方法 | 图像数量 | LD 错误偏差 (mm) | PoM (%) |
| --- | --- | --- | --- | --- |
| Saba *et al* (2015) \[[60](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8bib60)\] | 高斯滤波 + 谱分析 (GSA) | 404 |  |  |
*   GSA1: 0.25 ±inline-graphic style="height:0.75em;" xlink:href="bk978-0-7503-2244-7ch8ieqn1.gif"/ 0.24

*   GSA2: 0.27 ±inline-graphic style="height:0.75em;" xlink:href="bk978-0-7503-2244-7ch8ieqn2.gif"/ 0.26

 |  |
| --- | --- | --- | --- | --- |
| Araki *et al* (2016) \[[47](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8bib47)\] | 基于区域 (RB) | 300 |  | RB: 97.9 |
| Araki *et al* (2016) \[[47](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8bib47)\] | 基于边界 (BB) | 300 |  | BB: 85.2 |
| Araki *et al* (2016) \[[61](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8bib61)\] | 谱分析 | 404 |  | 
*   SA1: 0.26 ±inline-graphic style="height:0.75em;" xlink:href="bk978-0-7503-2244-7ch8ieqn3.gif"/ 0.28

*   SA2: 0.27 ±inline-graphic style="height:0.75em;" xlink:href="bk978-0-7503-2244-7ch8ieqn4.gif"/ 0.26

 |  |
| --- | --- | --- | --- | --- |
| Krishna *et al* (2017) \[[35](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8bib35)\] | 尺度空间 | 404 |  | 
*   SS1: 0.25 ±inline-graphic style="height:0.75em;" xlink:href="bk978-0-7503-2244-7ch8ieqn5.gif"/ 0.24

*   SS2: 0.27 ±inline-graphic style="height:0.75em;" xlink:href="bk978-0-7503-2244-7ch8ieqn6.gif"/ 0.25

 | 
*   SS1: 95.9

*   SS2: 95.1

 | 
| Saba *et al* (2017) \[[48](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8bib48)\] | 级联 + 区域 + 边界 (LSRB) | 100 |  | LSRB: 96.2 |
| 提出的 || 深度学习 || 407 |  | 
*   DL1: 0.19 ±inline-graphic style="height:0.75em;" xlink:href="bk978-0-7503-2244-7ch8ieqn7.gif"/ 0.27

*   DL2: 0.23 ±inline-graphic style="height:0.75em;" xlink:href="bk978-0-7503-2244-7ch8ieqn8.gif"/ 0.23

*   DL3: 0.21 ±inline-graphic style="height:0.75em;" xlink:href="bk978-0-7503-2244-7ch8ieqn9.gif"/ 0.19

 | 
*   DL1: 96.7

*   DL2: 96.1

*   DL3: 96.4

 |

**表 8.15.** 狭窄基准表。 (经 \[[66](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8bib66)\] 许可复制。)

| 作者 | 方法 | 患者数量 | 狭窄阈值 |
| --- | --- | --- | --- |
| Bruno *et al* (2001) \[[62](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8bib62)\] | 手动 | 22 | 
*   风险: SSI < 50%

 |

| --- | --- | --- | --- |
| Nicholaidas *et al* (2005) \[[63](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8bib63)\] | 手动 | 1115 | 
*   低风险: SSI <30%

*   轻度风险: 30%< SSI < 49%

*   高风险: SSI >50%

 |

| Kakkos *et al* (2008) \[[64](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8bib64)\] | 手动 | 821 | 
*   风险: 60%<SSI<99%

 |

| Schieneider *et al* (2010) \[[65](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8bib65)\] | 手动 |  | 
*   风险: 60%<SSI<99%

 |

| 提出的 || 深度学习 || 204 | 
*   低风险: SSI <25%

*   轻度风险: 25%< SSI <50%

*   高风险: SSI >50%

 |

### 8.7 结论

本文介绍了基于深度学习的血栓检测和狭窄测量的若干新方面。还进行了心血管风险分析。研究表明，基于深度学习的血管腔检测是估算狭窄和进行风险分析的有力工具。未来，基于深度学习的工具可以在诊断中心用于临床诊断和预后。这些工具可以帮助临床医生更快、更准确地做出决策，并制定治疗方案，促进快速康复并避免心血管疾病。

### 参考文献

\[1\] Virani S S, Alonso A, Benjamin E J, Bittencourt M S, Callaway C W, Carson A P, Chamberlain A M, Chang A R, Cheng S and Delling F N 2020 Heart disease and stroke statistics—2020 update: a report from the American Heart Association *Circulation* [E139–596](http://dx.doi.org/10.1161/CIR.0000000000000757)

\[2\] [https://www.cdc.gov/nchs/hus/data-finder.htm?&subject=Heart%20disease](https://www.cdc.gov/nchs/hus/data-finder.htm?&subject%3DHeart%20disease)

\[3\] Suri J S, Kathuria C and Molinari F 2010 *Atherosclerosis Disease Management* (Berlin: Springer)

\[4\] Saba L, Sanches J M, Pedro L M and Suri J S 2014 *Multi-modality Atherosclerosis Imaging and Diagnosis* (Berlin: Springer)

\[5\] Spence J D 2015 Management of asymptomatic carotid stenosis *Neurol. Clin.* [**33** 443–57](http://dx.doi.org/10.1016/j.ncl.2014.12.008)

\[6\] Carr S, Farb A, Pearce W H, Virmani R and Yao J S 1996 Atherosclerotic plaque rupture in symptomatic carotid artery stenosis *J. Vasc. Surg.* [**23** 755–66](http://dx.doi.org/10.1016/S0741-5214\(96\)70237-9)

\[7\] Orho‐Melander M 2015 Genetics of coronary heart disease: towards causal mechanisms, novel drug targets and more personalized prevention *J. Int. Med.* [**278** 433–46](http://dx.doi.org/10.1111/joim.12407)

\[8\] Prabhakaran D, Jeemon P and Roy A 2016 Cardiovascular diseases in India: current epidemiology and future directions *Circulation* [**133** 1605–20](http://dx.doi.org/10.1161/CIRCULATIONAHA.114.008729)

\[9\] Pandey A K, Blaha M J, Sharma K, Rivera J, Budoff M J, Blankstein R, Al-Mallah M, Wong N D, Shaw L and Carr J 2014 Family history of coronary heart disease and the incidence and progression of coronary artery calcification: Multi-Ethnic Study of Atherosclerosis (MESA) *Atherosclerosis* [**232** 369–76](http://dx.doi.org/10.1016/j.atherosclerosis.2013.11.042)

\[10\] Saba L, Mallarini G, Sanfilippo R, Zeng G, Montisci R and Suri J 2012 Intima media thickness variability (IMTV) and its association with cerebrovascular events: a novel marker of carotid therosclerosis? *Cardiovasc. Diag. Ther.* **2** 10

\[11\] Molinari F, Zeng G and Suri J S 2010 A state of the art review on intima–media thickness (IMT) measurement and wall segmentation techniques for carotid ultrasound *Comput. Methods Programs Biomed.* [**100** 201–21](http://dx.doi.org/10.1016/j.cmpb.2010.04.007)

\[12\] Ayer J, Charakida M, Deanfield J E and Celermajer D S 2015 Lifetime risk: childhood obesity and cardiovascular risk *Eur. Heart J.* [**36** 1371–6](http://dx.doi.org/10.1093/eurheartj/ehv089)

\[13\] D’Alessandro A and De Pergola G 2015 Mediterranean diet and cardiovascular disease: a critical evaluation of a priori dietary indexes *Nutrients* [**7** 7863–88](http://dx.doi.org/10.3390/nu7095367)

\[14\] Critchley J A and Capewell S 2003 Mortality risk reduction associated with smoking cessation in patients with coronary heart disease: a systematic review *JAMA* [**290** 86–97](http://dx.doi.org/10.1001/jama.290.1.86)

\[15\] Keating S T, Plutzky J and El-Osta A 2016 Epigenetic changes in diabetes and cardiovascular risk *Circ. Res.* [**118** 1706–22](http://dx.doi.org/10.1161/CIRCRESAHA.116.306819)

\[16\] Haskell W L, Lee I-M, Pate R R, Powell K E, Blair S N, Franklin B A, Macera C A, Heath G W, Thompson P D and Bauman A 2007 Physical activity and public health: updated recommendation for adults from the American College of Sports Medicine and the American Heart Association *Circulation* [**116** 1081](http://dx.doi.org/10.1161/CIRCULATIONAHA.107.185649)
