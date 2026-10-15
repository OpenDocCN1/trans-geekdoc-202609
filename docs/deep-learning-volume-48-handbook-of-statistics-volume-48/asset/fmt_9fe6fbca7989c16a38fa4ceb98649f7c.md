
| [Klare et al. (2012)](#Ch007_169-221_S0169716123000020.xhtml#bb0425), [Albiero et al. (2020a)](#Ch007_169-221_S0169716123000020.xhtml#bb0035), [Robinson et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0685), [Vangara et al. (2019)](#Ch007_169-221_S0169716123000020.xhtml#bb0820), [Krishnapriya et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0455), [Srinivas et al. (2019a](#Ch007_169-221_S0169716123000020.xhtml#bb0760),[b)](#Ch007_169-221_S0169716123000020.xhtml#bb0765), [Acien et al. (2018)](#Ch007_169-221_S0169716123000020.xhtml#bb0010), [Serna et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0720), [Nagpal et al. (2019)](#Ch007_169-221_S0169716123000020.xhtml#bb0570), [Garcia et al. (2019)](#Ch007_169-221_S0169716123000020.xhtml#bb0270), [Kortylewski et al. (2019)](#Ch007_169-221_S0169716123000020.xhtml#bb0440), [Gwilliam et al. (2021)](#Ch007_169-221_S0169716123000020.xhtml#bb0315), [Celis and Rao (2019)](#Ch007_169-221_S0169716123000020.xhtml#bb0135), [Terh¨orst et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0795), [Majumdar et al. (2021b)](#Ch007_169-221_S0169716123000020.xhtml#bb0520) || [Buolamwini and Gebru (2018)](#Ch007_169-221_S0169716123000020.xhtml#bb0110), [Deuschel et al., (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0205), [Krishnan et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0450), [Muthukumar (2019)](#Ch007_169-221_S0169716123000020.xhtml#bb0565), [Nanda et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0585), [Joo and Karkkainen (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0375), [Denton et al. (2019)](#Ch007_169-221_S0169716123000020.xhtml#bb0200), [Quadrianto et al. (2019)](#Ch007_169-221_S0169716123000020.xhtml#bb0645), [Barlas et al. (2021)](#Ch007_169-221_S0169716123000020.xhtml#bb0095), [Serna et al. (2021](#Ch007_169-221_S0169716123000020.xhtml#bb0725), [2022b)](#Ch007_169-221_S0169716123000020.xhtml#bb0730) |

| --- | --- |

##  6: Fair algorithms and bias mitigation

In this section, we provide a taxonomy of the bias mitigation techniques proposed for various face analysis tasks (see [Fig. 9](#Ch007_169-221_S0169716123000020.xhtml#f0050)). We discuss the mitigation techniques proposed for face detection and recognition in [Section 6.1](#Ch007_169-221_S0169716123000020.xhtml#s0205), followed by mitigation techniques for attribute prediction in [Section 6.2](#Ch007_169-221_S0169716123000020.xhtml#s0230). The proposed techniques are primarily constituted by deep learning techniques, which are subdivided into popular classes of algorithms. These classes include Adversarial learning-based algorithms, Generative algorithms, and Black-box learning algorithms. The techniques which do not fall into any of these classes are labeled as Bias-aware deep learning techniques.

![Fig. 9 Different bias mitigation techniques classified by the taxonomy proposed for tasks of face recognition and attribute prediction.](images/S0169716123000020/f07-09-9780443184307.jpg)

[Fig. 9](#Ch007_169-221_S0169716123000020.xhtml#B-f0050) Different bias mitigation techniques classified by the taxonomy proposed for tasks of face recognition and attribute prediction.

###  6.1: Face detection and recognition

The majority of the algorithms developed for mitigating bias in face detection and recognition are based on deep learning. Based on the taxonomy presented in [Fig. 9](#Ch007_169-221_S0169716123000020.xhtml#f0050), the following face detection and recognition approaches have been proposed in the literature for the development of fairer algorithms. The approaches have also been summarized in [Table 6](#Ch007_169-221_S0169716123000020.xhtml#t0035).

[Table 6](#Ch007_169-221_S0169716123000020.xhtml#B-t0035)

Taxonomy of different approaches for bias mitigation in facial analysis tasks of face recognition and attribute prediction.

| Approaches || Face detection and recognition || Attribute prediction |

| --- | --- | --- |

| Adversarial || [Alasadi et al. (2019)](#Ch007_169-221_S0169716123000020.xhtml#bb0025), [Gong et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0295), [Dhar et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0210) || [Wang et al. (2019b)](#Ch007_169-221_S0169716123000020.xhtml#bb0855), [Adeli et al. (2021)](#Ch007_169-221_S0169716123000020.xhtml#bb0015), [Dash et al., (2022)](#Ch007_169-221_S0169716123000020.xhtml#bb0180), [Dullerud et al. (2022)](#Ch007_169-221_S0169716123000020.xhtml#bb0235), [Wang et al. (2022a)](#Ch007_169-221_S0169716123000020.xhtml#bb0870) |

| --- | --- | --- |

| Black-box/Pre-trained || [Serna et al. (2022a)](#Ch007_169-221_S0169716123000020.xhtml#bb0735), [Terhorst et al. (2020a)](#Ch007_169-221_S0169716123000020.xhtml#bb0800) || [Dwork et al. (2018)](#Ch007_169-221_S0169716123000020.xhtml#bb0245), [Kim et al. (2019a)](#Ch007_169-221_S0169716123000020.xhtml#bb0415), [Nagpal et al. (2020a)](#Ch007_169-221_S0169716123000020.xhtml#bb0575), [Roh et al. (2021)](#Ch007_169-221_S0169716123000020.xhtml#bb0690), [Majumdar et al. (2021a](#Ch007_169-221_S0169716123000020.xhtml#bb0515), [2021c)](#Ch007_169-221_S0169716123000020.xhtml#bb0525), [Jang et al. (2022)](#Ch007_169-221_S0169716123000020.xhtml#bb0355), [Du et al. (2021)](#Ch007_169-221_S0169716123000020.xhtml#bb0230) |

| Generative || [McDuff et al. (2019)](#Ch007_169-221_S0169716123000020.xhtml#bb0540), [Yucer et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0920), [Conti et al. (2022)](#Ch007_169-221_S0169716123000020.xhtml#bb0170) || [Mullick et al. (2019)](#Ch007_169-221_S016.1: Face detection and recognition

The majority of the algorithms developed for mitigating bias in face detection and recognition are based on deep learning. Based on the taxonomy presented in [Fig. 9](#Ch007_169-221_S0169716123000020.xhtml#f0050), the following face detection and recognition approaches have been proposed in the literature for the development of fairer algorithms. The approaches have also been summarized in [Table 6](#Ch007_169-221_S0169716123000020.xhtml#t0035).

[Table 6](#Ch007_169-221_S0169716123000020.xhtml#B-t0035)

Taxonomy of different approaches for bias mitigation in facial analysis tasks (see [Fig. 9](#Ch007_169-221_S0169716123000020.xhtml#f0050)). We discuss the mitigation techniques proposed for face detection and recognition in [Section 6.1](#Ch007_169-221_S0169716123000020.xhtml#s0205), followed by mitigation techniques for attribute prediction in [Section 6.2](#Ch007_169-221_S0169716123000020.xhtml#s0230). The proposed techniques are primarily constituted by deep learning techniques, which are subdivided into popular classes of algorithms. These classes include Adversarial learning-based algorithms, Generative algorithms, and Black-box learning algorithms. The techniques which do not fall into any of these classes are labeled as Bias-aware deep learning techniques.

![Fig. 9 Different bias mitigation techniques classified by the taxonomy proposed for tasks of face recognition and attribute prediction.](images/S0169716123000020/f07-09-9780443184307.jpg)

[Fig. 9](#Ch007_169-221_S0169716123000020.xhtml#B-f0050) Different bias mitigation techniques classified by the taxonomy proposed for tasks of face recognition and attribute prediction.

###  6.1: Face detection and recognition

The majority of the algorithms developed for mitigating bias in face detection and recognition are based on deep learning. Based on the taxonomy presented in [Fig. 9](#Ch007_169-221_S0169716123000020.xhtml#f0050), the following face detection and recognition approaches have been proposed in the literature for the development of fairer algorithms. The approaches have also been summarized in [Table 6](#Ch007_169-221_S0169716123000020.xhtml#t0035).

[Table 6](#Ch007_169-221_S0169716123000020.xhtml#B-t0035)

Taxonomy of different approaches for bias mitigation in facial analysis tasks of face recognition and attribute prediction.

| Approaches || Face detection and recognition || Attribute prediction |

| --- | --- | --- |

| Adversarial || [Alasadi et al. (2019)](#Ch007_169-221_S0169716123000020.xhtml#bb0025), [Gong et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0295), [Dhar et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0210) || [Wang et al. (2019b)](#Ch007_169-221_S0169716123000020.xhtml#bb0855), [Adeli et al. (2021)](#Ch007_169-221_S0169716123000020.xhtml#bb0015), [Dash et al., (2022)](#Ch007_169-221_S0169716123000020.xhtml#bb0180), [Dullerud et al. (2022)](#Ch007_169-221_S0169716123000020.xhtml#bb0235), [Wang et al. (2022a)](#Ch007_169-221_S0169716123000020.xhtml#bb0870) |

| --- | --- | --- |

| Black-box/Pre-trained || [Serna et al. (2022a)](#Ch007_169-221_S0169716123000020.xhtml#bb0735), [Terhorst et al. (2020a)](#Ch007_169-221_S0169716123000020.xhtml#bb0800) || [Dwork et al. (2018)](#Ch007_169-221_S0169716123000020.xhtml#bb0245), [Kim et al. (2019a)](#Ch007_169-221_S0169716123000020.xhtml#bb0415), [Nagpal et al. (2020a)](#Ch007_169-221_S0169716123000020.xhtml#bb0575), [Roh et al. (2021)](#Ch007_169-221_S0169716123000020.xhtml#bb0690), [Majumdar et al. (2021a](#Ch007_169-221_S0169716123000020.xhtml#bb0515), [2021c)](#Ch007_169-221_S0169716123000020.xhtml#bb0525), [Jang et al. (2022)](#Ch007_169-221_S0169716123000020.xhtml#bb0355), [Du et al. (2021)](#Ch007_169-221_S0169716123000020.xhtml#bb0230) |

| Generative || [McDuff et al. (2019)](#Ch007_169-221_S0169716123000020.xhtml#bb0540), [Yucer et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0920), [Conti et al. (2022)](#Ch007_169-221_S0169716123000020.xhtml#bb0170) || [Mullick et al. (2019)](#Ch007_169-221_S0169716123000020.xhtml#bb0560), [Choi et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0150), [Ramaswamy et al. (2021)](#Ch007_169-221_S0169716123000020.xhtml#bb0665), [Tan et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0780), [Georgopoulos et al. (2021)](#Ch007_169-221_S0169716123000020.xhtml#bb0290), [Kolling et al. (2022)](#Ch007_169-221_S0169716123000020.xhtml#bb0435) |

| Bias-aware DeepLearning || [Amini et al. (2019)](#Ch007_169-221_S0169716123000020.xhtml#bb0060), [Huang et al. (2019)](#Ch007_169-221_S0169716123000020.xhtml#bb0330), [Vera-Rodriguez et al. (2019)](#Ch007_169-221_S0169716123000020.xhtml#bb0825), [Wang et al. (2019a)](#Ch007_169-221_S0169716123000020.xhtml#bb0850), [Terhorst et al. (2020b)](#Ch007_169-221_S0169716123000020.xhtml#bb0805), [Bruveris et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0950), [Gong et al. (2021)](#Ch007_169-221_S0169716123000020.xhtml#bb0300), [Yang et al. (2021)](#Ch007_169-221_S0169716123000020.xhtml#bb0900), [Franco et al. (2022)](#Ch007_169-221_S0169716123000020.xhtml#bb0265), [Wang et al. (2022)](#Ch007_169-221_S0169716123000020.xhtml#bb0865), [Liu et al. (2022)](#Ch007_169-221_S0169716123000020.xhtml#bb0510) || [Ryu et al. (2018)](#Ch007_169-221_S0169716123000020.xhtml#bb0700), [Das et al. (2018)](#Ch007_169-221_S0169716123000020.xhtml#bb0175), [Alvi et al. (2018)](#Ch007_169-221_S0169716123000020.xhtml#bb0055), [Kim et al. (2019b)](#Ch007_169-221_S0169716123000020.xhtml#bb0420), [Nagpal et al. (2020b)](#Ch007_169-221_S0169716123000020.xhtml#bb0580), [Wang et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0860), [Chuang and Mroueh (2021)](#Ch007_169-221_S0169716123000020.xhtml#bb0160), [Park et al. (2021)](#Ch007_169-221_S0169716123000020.xhtml#bb0615), [Agarwal et al. (2022)](#Ch007_169-221_S0169716123000020.xhtml#bb0020), [Cao et al. (2022)](#Ch007_169-221_S0169716123000020.xhtml#bb0125) |

####  6.1.1: Adversarial learning approaches
