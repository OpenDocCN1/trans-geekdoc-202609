
$RS_{2} = 12 \mathrm{~m}$. The communication radii assure that the nodes within the one-hop range can exchange information. The center $S_{i} = \left(x_{i}, y_{i}\right)$ of each circle represents the coordinates of a node. The area enclosed in the circle indicates the coverage of the WSN. The types and sensing radii of the mobile nodes are the same as those of the sensors with a sensing radius of $RS_{1}$. There are a total of 15 sensors. Simulation experiments were carried out to verify the proposed method. Figure 7 shows the coverage of the static nodes. The coverage was calculated to be 62.46%. There are 27 potential coverage holes in the detection area, which is larger than the number of mobile nodes that can be used.

![](img/e4200cc4308edaf8913e513b0f96dbb6_554_0.png)

The sizes of the coverage holes of the static nodes in Figure 7 are different. Our algorithm was adopted to simulate the patching of the coverage holes. The simulation results are shown in Figure 8. The calculated coverage rate was $79.13 \%$, which is $16.67 \%$ higher than the coverage rate before patching. The redundancy was $8.24 \%$. This means the coverage holes of the WSN have been well repaired, reflecting the effectiveness of our algorithm.

![](img/e4200cc4308edaf8913e513b0f96dbb6_554_1.png)

Using the same parameters, our algorithm was compared with VORCP [1] and VORPH [2] in terms of coverage and redundancy, with the goal of revealing the superiority of our algorithm intuitively.

Figure 9 shows the simulation results on patching the coverage holes in the scene of Figure 7, using VORCP. The coverage ($75.04 \%$) was $12.58 \%$ greater than that before patching. The redundancy was $10.54 \%$. Figure 10 shows the simulation results on patching the coverage holes in the scene of Figure 7, using VORPH. The coverage ($76.78 \%$) was $14.32 \%$ greater than that before patching. The redundancy was $11.13 \%$. Table 1 shows that our algorithm performed the best in hole patching and coverage enhancement, under the same environment. In addition, the redundancy after patching of our algorithm was lower than that of the other two algorithms. This fully demonstrates the superiority of our algorithm.

![](img/e4200cc4308edaf8913e513b0f96dbb6_555_0.png)

![](img/e4200cc4308edaf8913e513b0f96dbb6_555_1.png)

Table 1. Algorithm comparison.

| Algorithm | Coverage | Increased Coverage | Redundancy |
| :--- | :---: | :---: | :---: |
| VORCP | 75.04% | 12.58% | 10.54% |
| VORPH | 76.78% | 14.32% | 11.13% |
| Our Algorithm | 79.13% | 16.67% | 8.24% |

## 5. Conclusions

To solve the defects of traditional coverage hole patching algorithms, we proposed a coverage hole patching algorithm with priority mechanism in hybrid heterogeneous WSN environment. Specifically, we analyzed the network model and the hole positioning algorithm, and studied the coverage and priority of the coverage holes. Then, our algorithm was subjected to simulation and analysis, and compared with VORCP and VORPH. The results show that, in the hybrid heterogeneous WSN, our algorithm outperformed the traditional coverage hole patching algorithms in both coverage and redundancy.

Author Contributions: Conceptualization, X.L.; methodology, X.L.; software, Y.W.; validation, X.L., Q.W. and D.L.; writing—original draft preparation, C.Y., L.Z. and Y.Z.; writing—review and editing, Y.W.; project administration, X.L.; funding acquisition, X.L. All authors have read and agreed to the published version of the manuscript.

Funding: This research was funded by Heilongjiang Provincial Natural Science Foundation of China, grant number YQ2022F014.

Acknowledgments: The authors acknowledge Heilongjiang Provincial Natural Science Foundation of China (grant number YQ2022F014).

Conflicts of Interest: The authors declare no conflict of interest.

# References

- 1. Yue, Y.G.; He, P. A comprehensive survey on the reliability of mobile wireless sensor networks: Taxonomy, challenges, and future directions. Inf. Fusion 2018, 44, 188–204. [CrossRef]
- 2. Joshitha, K.L.; Jayashri, S. A novel redundant hole identification and healing algorithm for a homogeneous distributed Wireless Sensor Network. Wirel. Pers. Commun. 2019, 4, 1261–1282. [CrossRef]
- 3. Etancelin, J.M.; Fabbrì, A.; Guinand, F. DACYCLEM: A decentralized algorithm for maximizing coverage and lifetime in a mobile wireless sensor network. Ad Hoc Netw. 2019, 87, 174–187. [CrossRef]
- 4. Xu, Y.; Ding, O.; Qu, R. Hybrid multiobjective evolutionary algorithms based on decomposition for wireless sensor network coverage optimization. Appl. Soft Comput. 2018, 68, 268–282. [CrossRef]
- 5. Fang, W.; Song, X.; Wu, X. Novel efficient deployment schemes for sensor coverage in mobile wireless sensor networks. Inf. Fusion 2018, 41, 25–36. [CrossRef]
- 6. SO-IN, C.; Nguyen, T.G.; Nguyen, N.G. An efficient coverage hole-healing algorithm for area-coverage improvements in mobile sensor networks. Peer-to-Peer Netw. Appl. 2019, 3, 541–552. [CrossRef]
- 7. Zhang, S.; Tang, Z.; Wang, D. Enhancing received signal strength-based localization through coverage hole detection and recovery. Sensors 2018, 18, 2075. [CrossRef] [PubMed]
- 8. Yu, Q.; Wang, W.D.; Li, L.J.; Qian, T. Improved Recovery Algorithms of Coverage Holes in Hybrid WSN. J. Unio. Electr. Sci. Technol. China 2017, 46, 534–539.
- 9. Zhou, F.; Guo, H.T.; Yang, Y. An Improved Virtual Force Relocation Coverage Enhancement Algorithm. J. Electron. Inf. Technol. 2020, 42, 2194–2200.
- 10. Cao, Y; Wang, Z.L. A repair algorithm for coverage hole in mobile WSNs. J. Terahertz Sci. Electron. Inf. Technol. 2021, 19, 145–149.
- 11. Hao, Z.J.; Xu, H.W.; Dang, X.C.; Duan, Y. A Dynamic Detection and Repair Algorithm for Three-Dimensional Coverage Holes in WSN. Comput. Eng. 2020, 46, 178–186.
- 12. Wu, Q. Research on Gap Fixing and Data Transmission Technology of Wireless Sensor Network for Harmful Gas Detection. Ph.D. Thesis, Harbin University of Science and Technology, Harbin, China, 2019.
- 13. Sirajuddin, M.; Rupa, C. Techniques for Enhancing the Performance of TCP in Wireless Networks. Artif. Intell. Evol. Algorithms Eng. Syst. 2015, 324, 159–167.
- 14. Sirajuddin, M.; Rupa, C.; Bhatia, S. Hybrid Cryptographic Scheme for Secure Communication in Mobile Ad Hoc Network-Based E-Healthcare System. Wirel. Commun. Mob. Comput. 2022, 2022, 9134036. [CrossRef]
- 15. Bharath, G.; Rupa, C.; Kartikik, M. Revelation of Geospatial Information using Augmented Reality. In Proceedings of the 2021 6th International Conference on Wireless Communications, Signal Processing and Networking (WiSPNET), Chennai, India, 25–27 March 2021.

# Research on Small Acceptance Domain Text Detection Algorithm Based on Attention Mechanism and Hybrid Feature Pyramid

Mingzhu Liu \*, Ben Li and Wei Zhang

The Higher Educational Key Laboratory for Measuring & Control Technology and Instrumentation of Heilongjiang Province, Harbin University of Science and Technology, Harbin 150080, China
\* Correspondence: Imz@hrbust.edu.cn

**Abstract:** In the traditional text detection process, the text area of the small receptive field in the video image is easily ignored, the features that can be extracted are few, and the calculation is large. These problems are not conducive to the recognition of text information. In this paper, a lightweight network structure on the basis of the EAST algorithm, the Convolution Block Attention Module (CBAM), is proposed. It is suitable for the spatial and channel hybrid attention module of text feature extraction of the natural scene video images. The improvised structure proposed in this paper can obtain deep network features of text and reduce the computation of text feature extraction. Additionally, a hybrid feature pyramid + BLSTM network is designed to improve the attention to the small acceptance domain text regions and the text sequence features of the region. The test results on the ICDAR2015 demonstrate that the improved construction can effectively boost the attention of small acceptance domain text regions and improve the sequence feature detection accuracy of small acceptance domain of long text regions without significantly increasing computation. At the same time, the proposed network constructions are superior to the traditional EAST algorithm and other improved algorithms in accuracy rate P, recall rate R, and F-value.

**Keywords:** lightweight network structure; hybrid feature pyramid; BLSTM network; acceptance domain; attention mechanism

## 1. Introduction

In the last several years, the evolution of cultural exchanges and network technology has become faster and faster, and considerable video resources, such as movies, documentaries, and various shows, have sprung up on the Internet and have begun to affect people's lives. Due to cultural differences and personal understanding differences, there are still many text messages that the audience has difficulty noticing and understanding, such as street signs, trademarks, and commodities in videos, even though there are subtitles in these videos. If this information can be extracted, recognized, and translated, it will be helpful for the audience to understand the video information. Therefore, text detection in natural scenes is of great research significance.

Directly applying target detection technology to natural scene text detection is the most direct way in early natural scene text detection. Among them, the representative ways are Faster-RCNN [1] and SSD [2]. However, Faster-RCNN and SSD still have low efficiency for long text and slanted text detection due to the complexity of natural scene text detection, such as different types, unfixed position and arrangement direction, and the diversity of size and shape [3]. Thus, researchers consider improving the construction of the original target detection algorithm, making it more suitable for natural scene text detection.

Methods of traditional text detection and some text detection methods based on deep learning mostly use multi-stage constructions. Each level needs to be adjusted
