
![图 8.13 线性信道通道 1 与 NL 1 或 NL 2 级联时的 BER 性能。](images/Fig08_13.jpg)

[`FIGURE 8.13`](#ch08.xhtml#f8_13b) 线性信道 [通道 1](#ch01.xhtml#c1) 与 NL 1 或 NL 2 级联时的 BER 性能。

## 8.6 结论

本章提出了一种基于小波神经网络的、用于噪声和非线性 ISI 信道的判决反馈均衡器。该均衡器在前向路径中包含小波神经网络和 FIR 滤波器，在后向路径中包含 FIR 滤波器。小波网络有助于处理具有高 EVR 和非线性函数的信道，而前向 FIR 滤波器适用于具有线性特性的信道。为缓解传统小波网络训练方法中解陷入局部极小值的问题，提出了一种基于 CSO 的 WNN 训练算法。最后，对基准线性信道和非线性信道进行了仿真研究，以评估均衡器在均方误差和误码率方面的性能。仿真还评估了均衡器在不同程度的 EVR 参数和信道 SNR 下的性能。结果表明，与文献中现有的方案相比，所提出方案的性能得到了显著改善。

本工作的一些可能未来扩展如下：

1. WNN 中需要优化的参数数量非常大。观察发现，在学习过程中只有少数平移和伸缩参数发生变化。作为未来工作，可以探索具有 wavenet 架构的 DFE，并比较各种参数初始化技术。

2. 具有判决反馈架构的神经网络均衡器的文献很少。此外，很少有作者探索使用元启发式优化算法训练基于 ANN 的 DFE。作为未来研究，可以探索为具有其他神经网络架构（如 RBF 和 FLNN）的 DFE 设计基于群优化的训练算法。

## 参考文献

* [Abdelaziz, A.Y. and](#ch08.xhtml#r8_1b) Ali, E.S. 2015. 基于 cuckoo 搜索算法的非线性互联电力系统负荷频率控制器设计。International Journal of Electrical Power & Energy Systems 73:632–643. doi:[10.1016/j.ijepes.2015.05.050](https://doi.org/10.1016/j.ijepes.2015.05.050).
* [Abiodun, O.I., Jantan,](#ch08.xhtml#r8_2b) A., Omolara, A. E., Dada, K.V., Mohamed, N. A. and Arshad, H. 2018. 人工神经网络应用的最新进展：综述。Heliyon 4, no. 11.doi:[10.1016/j.heliyon.2018.e00938](https://doi.org/10.1016/j.heliyon.2018.e00938).
* [Aboutaleb, A., Sayyafan,](#ch08.xhtml#r8_3b) A., Sivakumar, K., Belzer, B., Greaves, S., Chan, K. S. and Wood, R. 2020. 基于深度神经网络的多层磁记录检测和部分响应均衡。IEEE Transactions on Magnetics 57, no. 3. doi:[10.1109/TMAG.2020.3038435](https://doi.org/10.1109/TMAG.2020.3038435).
* [Ahmad, S. T.](#ch08.xhtml#r8_4b) and Kumar, K. P. 2016. 用于 16-QAM 相干光学 OFDM 的径向基函数神经网络非线性均衡器。IEEE Photonics Technology Letters 28, no. 22:2507–2510. doi:[10.1109/LPT.2016.2601901](https://doi.org/10.1109/LPT.2016.2601901).
* [Al-Awami, A. T.,](#ch08.xhtml#r8_5b) Zerguine, A., Cheded, L., Zidouri, A. and Saif, W. 2011. 一种用于自适应均衡的新型改进粒子群优化算法。Digital Signal Processing 21, no. 2:195–207. doi:[10.1016/j.dsp.2010.05.001](https://doi.org/10.1016/j.dsp.2010.05.001).
* [Alexandridis, A. K.](#ch08.xhtml#r8_6b) and Zapranis, A. D. 2013. 小波神经网络：实用指南。Neural Networks 42, 1–27. doi:[10.1016/j.neunet.2013.01.008](https://doi.org/10.1016/j.neunet.2013.01.008).
* [Al-Shaikhi, A. A.,](#ch08.xhtml#r8_7b) Khan, A. H., Al-Awami, A. T. and Zerguine, A. 2019. 一种用于自适应均衡的混合粒子群优化技术。Arabian Journal for Science and Engineering 44, no. 3:2177–2184. doi:[10.1007/s13369-018-3387-8](https://doi.org/10.1007/s13369-018-3387-8).
* [Al-Zubi, J. A.,](#ch08.xhtml#r8_8b) Bharathikannan, B., Tanwar, S., Manikandan, R., Khanna, A. and Thaventhiran, C. 2019. 用于肺癌疾病诊断的增强神经网络集成分类。Applied Soft Computing 80:579–591. doi:[10.1016/j.asoc.2019.04.031](https://doi.org/10.1016/j.asoc.2019.04.031).
* [Bauduin, M., Smerieri,](#ch08.xhtml#r8_9b) A., Massar, S. and Horlin, F. 2015, May. 使用回声状态网络对非线性卫星通信信道进行均衡。In 2015 IEEE 81st Vehicular Technology Conference (VTC Spring). IEEE. doi:[10.1109/VTCSpring.2015.7145827](https://doi.org/10.1109/VTCSpring.2015.7145827).
* [Beni, G. 2020.](#ch08.xhtml#r8_10b) 群智能。In Complex Social and Behavioral Systems: Game Theory and Agent-Based Models, 791–818. Springer, New York, NY. doi:[10.1007/978-1-0716-0368-0\_530](https://doi.org/10.1007/978-1-0716-0368-0_530).
* [Caciularu, A. and](#ch08.xhtml#r8_11b) Burshtein, D. 2020. 使用变分自编码器进行无监督的线性和非线性信道均衡与解码。IEEE Transactions on Cognitive Communications and Networking 6, no. 3:1003–1018. doi:[10.1109/TCCN.2020.2990773](https://doi.org/10.1109/TCCN.2020.2990773).
* [Chen, S., Gibson,](#ch08.xhtml#r8_12b) G. J., Cowan, C. F. N. and Grant, P. M. 1990. 使用多层感知器对有限非线性信道进行自适应均衡。Signal Processing 20, no. 2:107–119. doi:[10.1016/0165-1684(90)90122-F](https://doi.org/10.1016/0165-1684\(90\)90122-F).
* [Das, G., Panda,](#ch08.xhtml#r8_13b) S. and Padhy, S. K. 2018. 量子粒子群优化调谐人工神经网络均衡器。In Soft Computing: Theories and Applications, 579–585. Springer, Singapore. doi:[10.1007/978-981-10-5687-1\_52](https://doi.org/10.1007/978-981-10-5687-1_52).
* [Das, G., Pattnaik,](#ch08.xhtml#r8_14b) P. K. and Padhy, S.K. 2014. 用于非线性信道均衡的粒子群优化训练人工神经网络。Expert Systems with Applications 41, no. 7:3491–3496. doi:[10.1016/j.eswa.2013.10.053](https://doi.org/10.1016/j.eswa.2013.10.053).
* [Farsad, N. and](#ch08.xhtml#r8_15b) Goldsmith, A. 2018. 通信系统中数据序列的神经网络检测。IEEE Transactions on Signal Processing 66, no. 21:5663–5678. doi:[10.1109/TSP.2018.2868322](https://doi.org/10.1109/TSP.2018.2868322).
* [Goswami, J. C.](#ch08.xhtml#r8_16b) and Chan, A. K. 2011. 小波基础：理论、算法与应用（第 233 卷）。John Wiley & Sons, Hoboken, NJ.
* [Haykin, S. 2008.](#ch08.xhtml#r8_17b) 自适应滤波器理论。Pearson Education India, New Delhi.
* [Ingle, K. K.](#ch08.xhtml#r8_18b) and Jatoth, R. K., 2020. 一种用于非线性信道均衡的高效 JAYA 算法与 Lévy 飞行。Expert Systems with Applications, 145, 112970. doi:[10.1016/j.eswa.2019.112970](https://doi.org/10.1016/j.eswa.2019.112970).
* [Iqbal, N., Zerguine,](#ch08.xhtml#r8_19b) A. and Al-Dhahir, N. 2014. 用于上行 SC-FDMA 的粒子群优化自适应均衡。Electronics Letters 50, no. 6:469–471. doi:[10.1049/el.2013.4091](https://doi.org/10.1049/el.2013.4091).
* [Iqbal, N., Zerguine,](#ch08.xhtml#r8_20b) A. and Al-Dhahir, N. 2015. 使用粒子群优化的判决反馈均衡。Signal Processing 108, 1–12. doi:[10.1016/j.sigpro.2014.07.030](https://doi.org/10.1016/j.sigpro.2014.07.030).
* [Jarajreh, M. 2019.](#ch08.xhtml#r8_21b) 用于超高频谱效率光学快速 OFDM 信号的低复杂度人工神经网络均衡。Applied Sciences 9, no. 19. doi:[10.3390/app9194038](https://doi.org/10.3390/app9194038).
