
本研究在使用深度学习（DL）架构作为基础，对抑郁和正常个体的音频记录进行评估。利用隐私保护的联邦学习（FL）系统，音频波形被分布在四个客户端上，用于IID（独立同分布）环境。经常用于识别抑郁的声学描述符是梅尔频率 cepstral 系数（MFCC）。因此，从音频数据集中使用MFCC提取了162个特征。

为了在多种场景下实现最高性能，DL算法在预处理信息后被实现到音频文件中。为分类抑郁和非抑郁参与者，实现了LSTM、CNN和Bi-LSTM等DL算法。此外，这些算法用于构建基础模型并找出最适合联邦学习的算法。

[Table 71.1](#ch71.xhtml#tab71_1) 和 [Figure 71.2](#ch71.xhtml#fig71_2) 展示了基础DL模型算法的结果，其中使用CNN、LSTM和Bi-LSTM进行验证后，准确率分别达到85%、89%和91%。因此，Bi-LSTM算法以91%的最高验证准确率超越了其他算法。

[Table 71.1 Training and validation results of DL models for depression detection](#ch71.xhtml#R_tab71_1)

| 参数 || Bi LSTM || CNN || LSTM |
| --- | --- | --- | --- |
| 准确率 || 99.08333 || 99.66667 || 99.33333 |
| 验证准确率 || 91 || 85 || 89 |
| 准确度 || 99.08333 || 99.66667 || 99.33333 |
| 验证精度 || 91 || 85 || 89 |
| 召回率 || 99.08333 || 99.66667 || 99.33333 |
| 验证召回率 || 91 || 85 || 89 |
| 损失 || 0.032376 || 0.012926 || 0.015737 |
| 验证损失 || 0.349078 || 0.439554 || 0.347897 |

![Figure 71.2 Training and validation accuracy and loss results for depression detection using Bi-LSTM, CNN and LSTM algorithms](images/fig71_2_C.jpg)

[Figure 71.2 Training and validation accuracy and loss results for depression detection using Bi-LSTM, CNN and LSTM algorithms](#ch71.xhtml#R_fig71_2)

FL方法与Bi-LSTM方法相结合，用于分析IID数据以诊断抑郁患者，同时保护其隐私。对于4个客户端，训练和验证集以IID数据划分。进一步，所有客户端数据在服务器端测试，以聚合所有客户端模型。最终，服务器开发的模型在所有客户端站点更新。

根据 [Table 71.2](#ch71.xhtml#tab71_2) 和 [Figure 71.3](#ch71.xhtml#fig71_3)、[Figure 71.4](#ch71.xhtml#fig71_4) 和 [Figure 71.5](#ch71.xhtml#fig71_5)，隐私保护FL模型在客户端站点对IID数据的训练准确率达到94.25%。此外，客户端站点对IID数据的验证准确率略低，为85.66%，而服务器站点对IID数据的验证准确率为86.66%。尽管FL模型在隐私保护系统中准确率略低于DL模型，但它是必需的，因为医院数据是私密的，许多患者不愿意透露信息，因此FL是构建安全诊断系统的最佳方式。

[Table 71.2 Training and validation results of FL models for depression detection using IID data](#ch71.xhtml#R_tab71_2)

| 参数 || 客户端IID训练 || 客户端IID验证 || 服务器IID验证 |
| --- | --- | --- | --- |
| 准确率 || 94.25 || 85.66667 || 86.66667 |
| 准确度 || 94.25 || 85.66667 || 86.66667 |
| 召回率 || 94.25 || 85.66667 || 86.66667 |
| 损失 || 0.160396 || 0.356732 || 0.32788 |

![Figure 71.3 Client training results for depression detection using IID data](images/fig71_3_C.jpg)

[Figure 71.3 Client training results for depression detection using IID data](#ch71.xhtml#R_fig71_3)

![Figure 71.4 Client validation results for depression detection using IID data](images/fig71_4_C.jpg)

[Figure 71.4 Client validation results for depression detection using IID data](#ch71.xhtml#R_fig71_4)

![Figure 71.5 Server validation results for depression detection using IID data](images/fig71_5_C.jpg)

[Figure 71.5 Server validation results for depression detection using IID data](#ch71.xhtml#R_fig71_5)

本文在本文中，我们介绍了一个系统，用于从音频数据中识别和分类抑郁和健康个体。自动诊断系统的创建将帮助临床医生快速诊断抑郁。因此，我们首先使用CNN、LSTM和Bi-LSTM算法构建了基础DL模型，其中Bi-LSTM在验证准确率最高，达91%。随后，提出了一种基于音频数据集的隐私保护联邦学习（FL）基于抑郁检测框架。因此，建议的FL框架在训练IID数据时达到94.25%的准确率，在客户端站点验证时为85.66%，在服务器站点验证时为86.66%。因此，未来该方法可以应用于多种数据集，以检验其可靠性和稳健性。

## 参考文献

*   [Adarsh, V., P. Arun Kumar, V. Lavanya, and G. R. Gangadharan](#ch71.xhtml#R_ref71_1). (2023). Fair and explainable depression detection in social media. Information Processing & Management, 60(1): 103168 [https://doi.org/10.1016/j.ipm.2022.103168](https://dx.doi.org/10.1016/j.ipm.2022.103168)

*   [Cai, Hanshu, Yiwen Gao, Shuting Sun, Na Li, Fuze Tian, Han Xiao, Jianxiu Li et al.](#ch71.xhtml#R_ref71_2) (2020). Modma dataset: a multi-modal open dataset for mental-disorder analysis. arXiv preprint arXiv:2002.09283 [https://doi.org/10.48550/arXiv.2002.09283](https://dx.doi.org/10.48550/arXiv.2002.09283).

*   [Cai, Hanshu, Jiashuo Han, Yunfei Chen, Xiaocong Sha, Ziyang Wang, Bin Hu, Jing Yang et al.](#ch71.xhtml#R_ref71_3) (2018). A pervasive approach to EEG-based depression detection. Complexity 2018: 1–13.

*   [Cui, Y., Li, Z., Liu, L., Zhang, J., and Liu, J.](#ch71.xhtml#R_ref71_4) (2022). Privacy-preserving speech-based depression diagnosis via federated learning. Proc. Ann. Int. Conf. IEEE Engg. Med. Biol. Ssc. EMBS, 1371–1374. Institute of Electrical and Electronics Engineers Inc. [https://doi.org/10.1109/EMBC48229.2022.9871861](https://dx.doi.org/10.1109/EMBC48229.2022.9871861).

*   [Elbeltagi, A., Aslam, M. R., Malik, A., Mehdinejadiani, B., Srivastava, A., Bhatia, A. S., and Deng, J.](#ch71.xhtml#R_ref71_5) (2020). The impact of climate changes on the water footprint of wheat and maize production in the Nile delta, Egypt. Sci. Total Environ., 743, 140770. [https://doi.org/10.1016/j.scitotenv.2020.140770](https://doi.org/10.1016/j.scitotenv.2020.140770).

*   [Fan, Z., Su, J., Gao, K., Peng, L., Qin, J., Shen, H., Hu, D., and Zeng, L.-L.](#ch71.xhtml#R_ref71_6) (2021). Federated learning on structural brain MRI scans for the diagnostic classification of major depression. Biol. Psych., 89(9), S183. [www.sobp.org/journal](https://dx.doi.org/www.sobp.org/journal).

*   [Gupta, Chetna, and Vikas Khullar](#ch71.xhtml#R_ref71_7). (2022). Contemporary Intelligent Technologies for Electroencephalogram-Based Brain Computer Interface. In 2022 10th International Conference on Reliability, Infocom Technologies and Optimization (Trends and Future Directions) (ICRITO), 1–6. IEEE.

*   [Khullar, Vikas, Raj Gaurang Tiwari, Ambuj Kumar Agarwal, and Soumi Dutta](#ch71.xhtml#R_ref71_8). (2022). Physiological signals based anxiety detection using ensemble machine learning. In Cyber Intelligence and Information Retrieval: Proceedings of CIIR 2021, 597–608. Springer Singapore.

*   [Khullar, Vikas, and Harjit Pal Singh](#ch71.xhtml#R_ref71_9). (2022). Privacy protected internet of unmanned aerial vehicles for disastrous site identification. Concurrency and computation: practice and experience. 34(19): e7040 [https://doi.org/10.1002/cpe.7040](https://doi.org/10.1002/cpe.7040).

