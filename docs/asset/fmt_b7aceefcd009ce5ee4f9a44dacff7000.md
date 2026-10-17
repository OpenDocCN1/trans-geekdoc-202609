
# Dynamic Decision-Making For Stabilized Deep Learning Software ...

## Networks

Neely et al. [8] 提出了一种新的动态多跳路由算法，用于在无线自组网和传感器网络中实现能源高效的数据/包转发，并受到队列稳定性的约束。

## 安全应用：监控

Mo et al. [9] 设计了一个基于深度学习的 CCTV 分布式监控系统框架。在该系统中，多个深度学习框架存在，每个深度学习模型都有其独立的配置。在这种情况下，存在复杂度与性能之间的权衡。

因此，拟议的 CCTV 监控算法会根据系统中的队列积压情况自适应选择深度学习模型，以在 maximization 目标下最大化识别性能，同时受到 CCTV 队列稳定性的约束。Kim et al. [10] 还设计了一种新的面部识别深度学习框架，用于 CCTV 监控平台。与拥有多个深度学习模型不同，该系统有一个学习系统（基于开源软件库 `OpenFace`），并控制 CCTV 摄像头的采样率。最终，拟议的决策算法会动态选择 CCTV 采样率，以在 maximization 目标下最大化识别性能，同时受到 CCTV 队列稳定性的约束。

## Others

图 [11] 说明了基于 Lyapunov 优化框架的动态控制算法用于动态强化学习策略设计。此外，图 [12, 13] 介绍了基于 Lyapunov 优化框架的自适应控制算法在股票市场定价和智能电网中的应用。

## CONCLUSIONS

本章介绍了一种动态控制决策算法，灵感来源于 Lyapunov 优化理论，在存在实用性/性能与延迟权衡的情况下。因此，动态控制决策算法旨在实时深度学习平台的时间平均实用性最大化（或惩罚最小化）。如讨论所示，基于 Lyapunov 优化的算法具有可扩展性、与硬件/系统无关、自配置且低复杂度。因此，它可以应用于视频流、无线网络、安全应用和智能电网等各种新兴应用。

![Image 402](img/index-96_1.png)

![Image 403](img/index-96_2.png)

![Image 404](img/index-96_3.png)

## ACKNOWLEDGEMENTS

本工作得到韩国国家研究基金（2019R1A2C4070663, 2019M3E4A1080391）的支持。J. Kim 是对应作者（电子邮件：joongheon@korea.ac.kr）。

![Image 405](img/index-97_1.png)

![Image 406](img/index-97_2.png)

![Image 407](img/index-97_3.png)

## REFERENCES

1. Kim D, Kwon J, Kim J. Lowcomplexity online model selection with Lyapunov control for reward maximization in stabilized real-time deep learning platforms. In: Proceedings of the IEEE International Conference on Systems, Man, and Cybernetics (SMC ‘18); 7–10 October, 2018; Miyazaki, Japan: IEEE; 2018. pp. 4363-4368

2. Neely M. Stochastic Network Optimization with Application to Communication and Queueing Systems. Vermont, USA: Morgan & Claypool; 2010

3. Kim J, Caire G, Molisch A. Qualityaware streaming and scheduling for device-to-device video delivery. IEEE/ ACM Transactions on Networking. 2016;24:2319-2331. DOI: 10.1109/ TNET.2015.2452272

4. Choi M, Kim J, Moon J. Adaptive detector selection for queue-stable word error rate minimization in connected vehicle receiver design. IEEE Transactions on Vehicular Technology. 2018;67:3635-3639. DOI: 10.1109/ TVT.2017.2776327

5. Kim J, Meng F, Chen P, Egilmez H, Bethanabhotla D, Molisch A, et al. Demo: Adaptive video streaming for device-todevice mobile platforms. In: Proceedings of the ACM International Conference on Mobile Computing and Networking (MobiCom ‘13), 30 September–4 October, 2013; Miami, FL, USA: IEEE; 2013

6. Koo J, Yi J, Kim J, Hoque M, Choi S. REQUEST: Seamless dynamic adaptive streaming over HTTP for multi-homed smartphone under resource constraints. In: Proceedings of the ACM International Conference on Multimedia (MM ‘17), 23–27 October, 2017; Mountain View, CA, USA: IEEE; 2017

7. Koo J, Yi J, Kim J, Hoque M, Choi S. Seamless dynamic adaptive constraints. IEEE Transactions on Mobile Computing. 2019;18:1647-1660. DOI: 10.1109/ TMC.2018.2863234

8. Neely M. Energy optimal control for time varying wireless networks. IEEE Transactions on Information Theory. 2006;52:2915-2934. DOI: 10.1109/ TIT.2006.876219

9. Kim J, Mo YJ, Lee W, Nyang D. Dynamic security-level maximization for stabilized parallel deep learning architectures in surveillance applications. In: Proceedings of the IEEE Symposium on Privacy-Aware Computing (PAC ‘07); 1–3 August, 2017; Washington DC, USA: IEEE; 2017. pp. 192-193

10. # framework via Lyapunov optimization. In: Proceedings of ACM Symposium on Operating Systems Principles (SOSP) AI Systems Workshop (AISys‘17), 28 October, 2017; Shanghai, China: ACM; 2017

11. Neely M, Supittayapornpong S. Dynamic Markov decision policies for delay constrained wireless scheduling. IEEE Transactions on Automatic Control. 2013;58:1948-1961. DOI: 10.1109/TAC.2013.2256682

12. Neely M. Stock market trading via stochastic network optimization. In: Proceedings of IEEE Conference on Decision and Control (CDC ‘10), 15–17 December, 2010; Atlanta, GA, USA: IEEE; 2010

13. # energy allocation to delay tolerant consumers. In: Proceedings of IEEE International Conference on Smart Grid Communication (SmartGridComm ‘10), 4–6 October, 2010; Gaithersburg, MD, USA: IEEE; 2010

![Image 408](img/index-98_1.png)

![Image 409](img/index-98_2.png)

![Image 410](img/index-98_3.png)

# CHAPTER 4 DEEP LEARNING FOR HYPERSPECTRAL DATA CLASSIFICATION THROUGH EXPONENTIAL MOMENTUM DEEP CONVOLUTION NEURAL NETWORKS

Qi Yue1,2,3 and Caiwen Ma1

1Xi’an Institute of Optics and Precision Mechanics, CAS, Xi’an 710119, China

2University of Chinese Academy of Sciences, Beijing 100039, China

3Xi’an University of Posts and Telecommunications, Xi’an 710121, China

## ABSTRACT

Classification is a hot topic in hyperspectral remote sensing community. In the last decades, numerous efforts have been concentrated on the classification problem. Most of the existing studies and research efforts are following the conventional pattern recognition paradigm, which is based on complex handcrafted features. However, it is rarely known which features are important for the problem. In this paper, a new classification skeleton based on deep machine learning is proposed for hyperspectral data. The proposed classification framework, which is composed of exponential momentum deep convolution neural network and support vector machine (SVM), can hierarchically construct high-level spectral-spatial features in an automated way. Experimental results and quantitative validation on widely used datasets showcase the potential of the developed approach for accurate hyperspectral data classification.

**Citation:** through Exponential Momentum Deep Convolution Neural Networks”, Journal of Sensors, vol. 2016, Article ID 3150632, 8 pages, 2016. https://doi.org/10.1155/2016/3150632.

**Copyright:** © 2016 by Authors. This is an open access article distributed under the Creative Commons Attribution License, which permits unrestricted use, distribution, and reproduction in any medium, provided the original work is properly cited.

![Image 414](img/index-100_1.png)

![Image 415](img/index-100_2.png)

![Image 416](img/index-100_3.png)

## INTRODUCTION

Recent advances in optics and photonics have allowed the development of hyperspectral data detection and classification, which is widely used in agriculture [1], surveillance [2], environmental sciences [3, 4], astronomy [5, 6], and mineralogy [7]. In the past decades, hyperspectral data classification methods have been a hot research topic. A lot of classical classification algorithms, such as *k*-nearest neighbors, maximum likelihood, parallelepiped classification, minimum distance, and logistic regression (LR) [8, 9], have been proposed. However, there are several critical problems in the classification of hyperspectral data: (1) high dimensional data, which would lead to curse of dimensionality; (2) limited number of labeled training samples, which would lead to Hughes effect; (3) large spatial variability of spectral signature [10].

data, follows the conventional paradigm of pattern recognition and complex

Classical feature extraction methods include the following: principle component analysis, singular value decomposition, projection pursuit, self-organizing map, and fusion feature extraction method. Many of these methods extract features in a shallow manner, which do not hierarchically extract deep features automatically. In contrast, the deep machine learning framework can extract high-level abstract features, which has rotation, scaling, and translation invariance characteristics [11, 12].
