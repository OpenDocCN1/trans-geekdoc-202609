
| LDAM-CosFace (`[Cao et al., 2019](#Ch007_169-221_S0169716123000020.xhtml#bb0120))` || 98.93 || 97.80 || 97.23 || 97.50 || 97.87 || 0.75 |

| RamFace (`[Yang et al., 2021](#Ch007_169-221_S0169716123000020.xhtml#bb0900))` || 97.40 || 96.25 || 95.50 || 96.58 || 96.43 || 0.78 |

| MetaCW (`[Jamal et al., 2020](#Ch007_169-221_S0169716123000020.xhtml#bb0350))` || 99.13 || 97.86 || 97.73 || 98.11 || 98.21 || 0.63 |

| Sensitive Loss (`[Serna et al., 2022a](#Ch007_169-221_S0169716123000020.xhtml#bb0735))` || 97.23 || 95.82 || 96.50 || 96.95 || 96.62 || 0.61 |

| MvCoM-URFace (`[Liu et al., 2022](#Ch007_169-221_S0169716123000020.xhtml#bb0510))` || 98.85 || 97.18 || 97.15 || 96.98 || 97.54 || 0.88 |

| MvComM-CosFace (`[Liu et al., 2022](#Ch007_169-221_S0169716123000020.xhtml#bb0510))` || 99.16 || 98.06 || 97.78 || 98.28 || 98.32 || 0.60 |

[Table 8](#Ch007_169-221_S0169716123000020.xhtml#B-t0045)

性别预测模型在 UTKFace、MORPH 和 LFWA 数据集上的性能比较（%）使用多任务学习（`[Das et al., 2018](#Ch007_169-221_S0169716123000020.xhtml#bb0175)`）、过滤下降（`[Nagpal et al., 2020b](#Ch007_169-221_S0169716123000020.xhtml#bb0580)`）和 SIP（`[Majumdar et al., 2021a](#Ch007_169-221_S0169716123000020.xhtml#bb0515)`）算法进行偏差缓解。

| 偏差估计 || 模型训练数据 ||  | 错误 || 出生日期 || PSE |
| --- | --- | --- | --- | --- | --- |
| G1 || G2 |
|  ||  || 预训练 || 22.64 || 41.37 || 9.36 || 22.02 |
| --- | --- | --- | --- | --- | --- |
|  ||  || 微调 || 15.61 || 29.30 || 6.84 || 15.17 |
|  || MORPH || 多任务学习 || 23.65 || 37.87 || 7.11 || 18.83 |
|  ||  || 过滤下降 || 28.08 || 34.99 || 3.46 || 14.86 |
| UTKFace ||  || SIP || 10.18 || 22.30 || 6.06 || 11.93 |
|  || 预训练 || 18.25 || 51.74 || 16.74 || 30.90 |
|  || 微调 || 15.00 || 31.67 || 8.33 || 17.09 |
|  || LFWA || 多任务学习 || 24.01 || 38.52 || 7.25 || 19.20 |
|  ||  || 过滤下降 || 29.77 || 33.33 || 1.78 || 12.79 |
|  ||  || SIP || 11.91 || 23.15 || 5.62 || 11.97 |
|  ||  || 预训练 || 41.27 || 19.02 || 11.12 || 22.91 |
|  || 微调 || 5.84 || 28.52 || 11.34 || 17.53 |
|  || UTKFace || 多任务学习 || 10.00 || 22.80 || 6.40 || 12.34 |
|  ||  || 过滤下降 || 8.88 || 21.67 || 6.40 || 11.90 |
| MORPH ||  || SIP || 14.11 || 3.59 || 5.26 || 8.34 |
|  || 预训练 || 53.80 || 20.58 || 16.61 || 31.88 |
|  || 微调 || 8.69 || 18.75 || 5.03 || 9.92 |
|  || LFWA || 多任务学习 || 9.63 || 23.07 || 6.72 || 12.64 |
|  ||  || 过滤下降 || 9.88 || 20.94 || 5.53 || 11.06 |
|  ||  || SIP || 15.92 || 4.75 || 5.58 || 9.21 |
|  ||  || 预训练 || 29.88 || 39.39 || 4.75 || 17.65 |
|  || 微调 || 3.99 || 54.18 || 25.09 || 35.48 |
|  || UTKFace || 多任务学习 || 27.46 || 36.70 || 4.62 || 16.47 |
|  ||  || 过滤下降 || 30.16 || 34.05 || 1.95 || 13.20 |
| LFWA ||  || SIP || 18.12 || 26.58 || 4.23 || 12.30 |
|  || 预训练 || 19.12 || 58.50 || 19.69 || 35.56 |
|  || 微调 || 5.50 || 50.42 || 22.46 || 32.65 |
|  || MORPH || 多任务学习 || 39.67 || 28.74 || 5.47 || 18.34 |
|  ||  || 过滤下降 || 34.43 || 37.32 || 1.45 || 13.90 |
|  ||  || SIP || 15.95 || 27.33 || 5.69 || 13.62 |
The bias is quantified using the Degree of Bias (DoB) and Precise Subgroup Equivalence (PSE) metrics.

##  8: Topography of commercial systems and patents

Face-based technologies are widely patented all over the world. On searching for patents using the keywords “face recognition,” more than 450k patents are returned (`h[ttps://www.lens.org/lens/searc](http://www.lens.org/lens/search/patent/list?preview=trueq%3Dface%20recognition)h/paten[t/list?preview=trueq=face%20recognition`)(`http://www.lens.org/lens/search/patent/list?preview=trueq=face%20recognition`)). The patents in face recognition technology have grown considerably since the early 2000s. This trend is presented in [`Fig. 14](#Ch007_169-221_S0169716123000020.xhtml#f0075)`, where the number of patents is depicted to have grown from approximately 5k in the year 2000 to 50k in the year 2021. The top owners of these patents are tech giants such as Google, Microsoft, and Apple (see right [`Fig. 14](#Ch007_169-221_S0169716123000020.xhtml#f0075)`). In the last 2 years, over 35k patents have been filed and published on face recognition technology. A small selection of patents published in 2022 is listed in [`Table 9](#Ch007_169_169-221_S0169716123000020.xhtml#t0050)`). While facial recognition technology is heavily patented, the face recognition systems of renowned companies were openly criticized in 2018 for their biased behavior and unacceptable performance toward certain demographic subgroups (`[Buolamwini and Gebru, 2018](#Ch007_169-221_S0169716123000020.xhtml#bb0110)`). In [`Table 1](#Ch007_169-221_S0169716123000020.xhtml#t0010)`, the face verification performance of commercial off-the-shelf systems (COTS) across different ethnicities is summarized. The research highlighting this bias was published in 2019. In a follow-up study to their work in 2018 (`[Raji and Buolamwini, 2019](#Ch007_169-221_S0169716123000020.xhtml#bb0660)`), the authors observed that the companies had significantly reduced their error margins for the female and darker-skinned subgroups. However, research published in 2021 has showcased a disparity in the face detection performance of commercial systems (`[Dooley et al., 2022](#Ch007_169-221_S0169716123000020.xhtml#bb0220)`).

![Fig. 14 (Left) Graph depicting the number of patents filed, published, and granted under “face recognition” since 1950. (Right) The top owners of “face recognition” patents.](images/S0169716123000020/f07-14-9780443184307.jpg)

[Fig. 14](#Ch007_169-221_S0169716123000020.xhtml#B-f0075) (Left) Graph depicting the number of patents filed, published, and granted under “face recognition” since 1950. (Right) The top owners of “face recognition” patents.

[Table 9](#Ch007_169-221_S0169716123000020.xhtml#B-t0050)

List of some of the patents related to facial recognition technology published in 2022.

| Application No. || Title || Assignees || Inventors |
| --- | --- | --- | --- |
| JP 2022001988 A || Face Recognition Management System And Face Recognition Management Server || Almex Inc || Inoue Susumu |
| --- | --- | --- | --- |
| TW M623082 U || Face Recognition Card Transaction System || Taiwan Cooperative Bank Co Ltd || Chen Yu-Wei |
| ZA 202108983 B || A Face Recognition System Based On Convolutional Neural Network || Univ Southwest || Dong Tao |
| WO 2022/041263 A1 || Face Recognition-based Access Control System || Suzhou Sdc Tech Co Ltd || Xia Zeyu |
| US 11281922 B2 || Face Recognition System, Method For Establishing Data Of Face Recognition, And Face Recognizing Method Thereof || Pegatron Corp || Tseng Yu-Hung |
| KR 20220043905 A || Face Recognition System For Training Face Recognition Model Using Frequency Components || Posco ICT Co Ltd || Kim Seong Uk |
| US 11301669 B2 || Face Recognition System And Method For Enhancing Face Recognition || Pegatron Corp || Tseng Yu-Hung |
| WO 2022/078572 A1 || Access Control With Face Recognition And Heterogeneous Information || Assa Abloy AB || Chen Jianbo |
| US 11315360 B2 || Live Facial Recognition System And Method || Wistron Corp || Chang Yao-Tsung |
| US 11328152 B2 || Recognition System Employing Thermal Sensor || Pixart Imaging Inc || Chen Nien-Tse |
| US 11335128 B2 || Methods And Systems For Evaluating A Face Recognition System Using A Face Mountable Device || Visa Int Service Ass || Arora Sunpreet Singh |
| WO 2022/105015 A1 || Face Recognition Method And System, Terminal, And Storage Medium || Shenzhen Inst Of Adv Tech CAS || Qian Jing |
| US 11354936 B1 || Incremental Clustering For Face Recognition Systems || Amazon Tech Inc || Chandarana Dharmil Satishbhai |
