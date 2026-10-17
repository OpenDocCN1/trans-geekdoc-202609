
**知情同意声明：** 不适用。

**数据可用性声明：** 不适用。

**利益冲突：** 作者声明不存在利益冲突。

## 参考文献

1. Kolodzy, P. *Spectrum Policy Task Force Report*; FCC ET Docket No. 02-155; 美国联邦通信委员会：华盛顿特区，美国，2002；第 40 卷，第 147–158 页。

2. Kiftaro, F.; El-Tarhouni, M.; Assaleh, K. UHF Spectrum Occupancy Measurements in Sharjah—UAE. 在 *2017 年第九届 IEEE-GCC 会议及展览（GCCCE）*，巴林麦纳麦，2017 年 5 月 8–11 日。

3. Yu, X.; Kong, M.; Li, X. Spectrum occupancy in the 87.5–108 MHz band: Measurement and analysis. 在 *2017 年第二届 IEEE 先进信息技术、电子和自动控制会议（IAEAC）*，中国重庆，2017 年 3 月 25–26 日。

4. Ramírez, D.; Cardenas-Juarez, M.; Pineda-Rico, U. Spectrum Occupancy Measurements in the Sub-6 GHz Band for Smart Spectrum Applications. 在 *2018 年 IEEE 第十届拉丁美洲通信会议（LATICOM）*，墨西哥瓜达拉哈拉，2018 年 11 月 14–16 日。

5. Engiz, B.K.; Rajab, Y.A. Investigation of Spectrum Occupancy in GSM Band in Samsun, Turkey. 在 *2019 年第六届电气和电子工程国际会议（ICEEE）*，土耳其伊斯坦布尔，2019 年 4 月 16–17 日。

6. Zulfiqar, M.D.; Ismail, K.; Hassan, N.U. Radio Spectrum Occupancy Measurement from 30MHz-1030MHz in Pakistan. 在 *2019 年英国/中国新兴技术会议（UCET）*，英国格拉斯哥，2019 年 8 月 21–22 日。

7. Tandra, R.; Sahai, A. Fundamental limits on detection in low SNR under noise uncertainty. 在 *2005 年无线网络、通信和移动计算国际会议*，美国夏威夷毛伊岛，2005 年 6 月 13–16 日。

8. Mitola, J.; Maguire, G.Q. Cognitive radio: Making software radios more personal. *IEEE Pers. Commun.* **1999**, *6*, 13–18. [CrossRef]

9. Woods, T.; Furman, S. All-Domain Spectrum Software and Control via Hierarchical Dynamic Spectrum Sharing with Implemented Dynamic Spectrum Access Toolchain. 在 *2021 年 IEEE 军事通信会议（MILCOM 2021）*，美国加州圣地亚哥，2021 年 11 月 29 日至 12 月 2 日。

10. Madhavan, A.; Govindarajan, Y. Wideband Spectrum Sensing in Dynamic Spectrum Access Systems Using Bayesian Learning. *J. Phys. Conf. Ser.* **2021**, *1964*, 62067–62075. [CrossRef]

# 文章

# 基于数学形态学分形维度的模拟电路软故障诊断方法研究

卢新苗<sup>1,*</sup>，杨春芳<sup>1</sup>，吴琼<sup>1,2</sup>，王佳旭<sup>1</sup>，卢子涵<sup>1</sup>，孙帅<sup>1</sup>，刘恺毅<sup>3</sup>，邵丹<sup>4</sup>

- <sup>1</sup> 哈尔滨理工大学 测量与控制技术通信工程学院，哈尔滨 150080，中国
- <sup>2</sup> 黑龙江省网络空间研究中心，哈尔滨 150090，中国
- <sup>3</sup> 哈尔滨气象局，哈尔滨 150028，中国
- <sup>4</sup> 哈尔滨科技职业学院，哈尔滨 150399，中国
- \* 通讯作者邮箱：lxinmiao0611@hrbust.edu.cn；电话：+86-187-0462-8841

**摘要：** 传统的电路故障特征提取方法难以准确区分非线性模拟电路故障，且故障率高、诊断成本大。为了解决这一问题，本文提出了一种基于变分模态分解（`VMD`）的数学形态学分形维度（`MMFD`）方法，用于模拟电路软故障的特征提取。首先，将信号分解为变分模态以抑制环境噪声的影响，获得多个具有不同中心频率的高维特征模态函数。计算信号分形信息分量（`IMF`）的分形维度，然后使用核主成分分析（`KPICA`）去除数据中的重叠和冗余部分。将获得的故障集作为判断电路工作状态和故障类型的依据。模拟电路的实验结果表明，该方法可以有效用于电路故障诊断。

**关键词：** 数学形态学分形维度；核主成分分析；变分模态分解；特征提取

## 1. 引言

在日常生活和生产中，电路可分为模拟电路和数字电路两种类型。虽然模拟电路通常占电路组件的 20% 以下，但 80% 的故障是由模拟电路引起的 [1]。模拟电路的故障类型可分为软故障和硬故障。硬故障是指电子电路中的开路、短路等灾难性故障，易于识别。软故障是指元器件的数值发生变化，且数值偏差超过允许范围 [2]。当出现软故障时，电路仍可能正常工作，但如果不及时更换元器件，软故障将升级为硬故障，这将对整个电路造成重大损害 [3]，甚至危及人们的人身安全。

许多学者针对模拟电路识别提出了多种特征提取方法。模拟电路常见的故障特征提取方法包括主成分分析 [4]、因子分析 [5,6] 以及其他线性提取方法。这些方法对线性电路相对有效，但日常生活中的大多数电路具有非线性特征。上述方法无法反映信号的平稳性特点，导致提取的故障特征可分性低，因此在故障模式识别中存在较大的分类误差。因此，早期的软故障研究主要引入模糊算法、小波理论等手段来确定实际工作状态 [7]。虽然这些算法提高了故障诊断的效果，但某些算法在分析故障特征时会受到电路状态的严重影响，导致性能不稳定。为了解决这一问题，在

## 参考文献

- 11. Toma, O.H.; Lopez-Benitez, M. 协作频谱感知：最小干扰和最大利用率的新方法。载于 *2021 IEEE 国际通信研讨会论文集（ICC Workshops）*，加拿大魁北克蒙特利尔，2021年6月14–23日。
- 12. Solanki, S.; Dhehbar, V. 使用 CNN-RNN 和迁移学习进行认知无线电频谱感知。*IEEE Access* 2022, 10, 113482–113492. [交叉引用]
- 13. Huang, P.; Liu, C.J. 基于部分周期性模式挖掘的无线频谱占用预测。*IEEE 并行与分布系统汇刊* 2014, 25, 1925–1934. [交叉引用]
- 14. Saad, A.; Staehle, B.; Knorr, R. 用于工业认知无线电的基于隐马尔可夫模型的频谱预测。载于 *2016 IEEE 第 12 届无线和移动通信、网络与通信国际会议（WiMob）*，美国纽约，2016年10月17–19日。
- 15. Wu, J.W.; Li, Y. 基于密度聚类的 HMM 协作频谱预测算法。*计算机应用期刊* 2018, 45, 129–134. [交叉引用]
- 16. Liu, X.N.; Shi, R. 基于分段马尔可夫模型的频谱占用预测方法。*无线电工程* 2020, 50, 690–695。
- 17. Wang, D.; Cao, P. 基于隐马尔可夫模型的高频认知频点选择机制。*计算机测量与控制* 2021, 36, 1179–1182。
- 18. Lin, G.; Cheng, Y.P. HF 信道估计中三态 HMM 的性能分析。*通信技术* 2016, 49, 286–292。
- 19. Chauhan, P.; Deka, S.K. 面向能量受限认知无线电网络的协作频谱预测驱动感知。*IEEE Access* 2021, 10, 26107–26118. [交叉引用]
- 20. Zhao, J.L.; Wang, M.W.; Yan, J.S. 基于神经网络的认知无线电频谱预测。载于 *2011 国际电子、通信与控制会议（ICECC）*，中国宁波，2011年9月9–11日。
- 21. He, Y.; Meng, Z. 基于 BP 神经网络算法的求解平面问题的差分自动法动态评估模型。*物理学 A：统计力学及其应用* 2020, 556, 1–11. [交叉引用]
- 22. Tang, Z.; Li, S. 用于认知无线电多时隙频谱预测的深度循环神经网络。*KSII 互联网与信息系统汇刊* 2017, 11, 3029–3045。
- 23. Yu, L.; Chen, J.; Ding, G. 基于长短期记忆（LSTM）的频谱预测。载于 *2017 第 3 届 IEEE 计算机与通信国际会议（ICCC）*，中国成都，2017年12月13–16日。
- 24. Yu, L.; Chen, J. 基于田口方法与深度长短期记忆（LSTM）的频谱预测。*IEEE Access* 2018, 6, 45923–45933. [交叉引用]
- 25. Chen, A.M.; Zhang, C.Y. 基于长短期记忆网络的 UAV 认知无线电频谱预测。*国外电子测量技术* 2021, 40, 37–43。
- 26. Shawel, B.S.; Woldegebraiel, D.H.; Pollin, S. 用于动态频谱接入的基于卷积 LSTM 的长期频谱预测。载于 *2019 第 27 届欧洲信号处理会议（EUSIPCO）*，西班牙拉科鲁尼亚，2019年9月2–6日。
- 27. Li, X.; Liu, Z.C. 用于时空谱数据频谱预测的深度学习方法。*IEEE 通信快报* 2021, 25, 1216–1220. [交叉引用]
- 28. Yang, C.; Peng, T.; Zuo, P. 突发频段的频谱预测方法。载于 *2021 IEEE 无线通信与网络会议研讨会（WCNCW）*，中国南京，2021年3月29日。
- 29. Gao, Y.L.; Zhao, C.Y.; Fu, N. 多通道多步联合频谱预测算法。载于 *2021 IEEE 第 94 届车辆技术会议（VTC2021-Fall）*，美国俄克拉荷马州诺曼，2021年9月27–30日。
- 30. Huang, Q.Y. 基于 LSTM 神经网络的认知无线电频谱预测研究。硕士学位论文，哈尔滨工业大学，中国哈尔滨，2020年6月。
- 31. Radhakrishnan, N.; Kandeepan, S. 基于长短期记忆的马尔可夫频谱预测性能分析。*IEEE Access* 2021, 9, 149582–149595. [交叉引用]
- 32. Aygul, M.A.; Nazzal, M. 利用复合 2D-LSTM 模型利用多维相关性实现高效的频谱占用预测。*传感器* 2021, 21, 135. [交叉引用] [PubMed]
- 33. Radhakrishnan, N.; Kandeepan, S. 基于长短期记忆的马尔可夫频谱预测的快速学习改进初始化方法。*IEEE 认知通信与网络汇刊* 2021, 7, 729–738. [交叉引用]
- 34. Radhakrishnan, N.; Kandeepan, S.; Yu, X.H. 使用 LSTM 的基于软融合的协作频谱预测。载于 *第 15 届信号处理与通信系统国际会议（ICSPCS）*，澳大利亚悉尼，2021年12月13–15日。
- 35. Hoecheri, S.; Schmidhuber, J. 长短期记忆。*神经计算* 1997, 9, 1735–1780. [交叉引用] [PubMed]
- 36. Pezeshik, M. 使用门控循环神经网络进行序列建模。*计算机科学* 2015, 9, 1–7。

**免责声明/出版商声明：** 所有出版物中包含的观点、立场和数据仅为个别作者和贡献者所有，不代表 MDPI 和/或编辑的立场。MDPI 和/或编辑不对内容中提及的任何观点、方法、说明或产品可能造成的任何人身伤害或财产损失承担责任。

## 2. 变分模态分解

近年来，一些学者将数学形态学与小波相结合，提出了一种新的非线性小波形态小波。文献 [8] 将形态小波应用于电力扰动检测，并成功识别了电力传输过程中的不良状态。例如，庄宁 [9] 等人将分形维数与 `EMD`（经验模态分解）相结合，以提取脑电信号的特征，从而识别不同的情绪表现。郑志 [10] 等人将 `LMD`（局部均值分解）分解方法与广义分形维数相结合，以识别齿轮故障。然而，实际测量信号通常伴随着异常事件，例如噪声干扰和间歇性信号，这会导致模态混叠，并极大地影响后续的故障诊断率。同时，计算分形维数的一种常用方法是覆盖法（盒计数法）。该方法存在不可避免的缺点。由于该方法本身使用规则网格划分方法，因此在某些情况下分形维数的估计非常不稳定 [11]。

针对上述问题，本文提出了一种基于变分模态分解（`VMD`）计算数学形态学分形维数（`VMD-MMFD-KPCA`）的方法。利用信号的变分模态分解（`VMD`），最大程度地消除信号中的干扰信息，以解决传统 `EMD` 分解的模态混叠问题。在使用形态学分形维数计算信号维数时，避免了传统盒维数估计的不稳定性，包括有效区分不同的故障类型。在此基础上，引入 `KPCA` 降维方法，降低通过维数计算的高维数据的维度，消除样本中的冗余和重复，为后续故障诊断提供数据依据。与传统的故障诊断方法相比，该方法在特征提取和诊断方面表现出更好的性能。最后，通过仿真电路证明了该方法的有效性。

`VMD` 分解是一种非递归信号分解算法。通过对信号进行自适应分解，获得不同频带中的本征模态函数（`IMF`）。在求解模态函数的过程中，使用图像延拓来避免 `EMD`（经验模态分解）等其他分解方法中的端点效应。`VMD` 对非线性故障信号的处理有助于提取后续故障信号的特征。分解后的 `IMF` 具有独立的中心频率和稀疏性，在参数适当时可以有效避免模态混叠。

- (1) 为了获得单向频谱，使用希尔伯特变换分析和计算每个模态信号，然后使用频率平移法将模态频谱移动到基带：

$$
\left[ \left( \delta(t) + \frac{j}{\pi t} \right) * v_{k}(t) \right] e^{j \omega_{k} t}
$$

`δ(t)` 是狄拉克函数；`v_k` 和 `ω_k` 分别是分解的第一个 `IMF` 分量及其中心频率。

- (2) 通过梯度的平方范数估计带宽，约束表达式为：

$$
\begin{gathered}
\min _{\left\{v_{k}\right\},\left\{\omega_{k}\right\}} \sum_{k=1}^{K}\left\|\partial_{t}\left[\left(\delta(t)+\frac{1}{\pi t}\right) * v_{k}(t)\right] e^{-j \omega_{k} t}\right\|_{2}^{2} \\
s.t. \quad \sum_{k=1}^{K} v_{k}(t)=f(t)
\end{gathered}
$$

`∂_t` 是梯度计算，`*` 是卷积运算符号。

- (3) 为了更高效地获得最优解，使用拉格朗日算子 `τ(t)` 和惩罚因子 `α` 将约束问题转化为无约束问题。展开的拉格朗日函数表达式为：

$$
L(\{v_k\}, \{\omega_k\}, \tau) = \alpha \sum_{k=1}^{K} \left\| \partial_{\mathbf{l}} \left( \delta(t) + \frac{j}{\pi t} * v_k(t) \right) e^{-j \omega_k t} \right\|_2^2 + \left\| f(t) - \sum_{k=1}^{K} v_k(t) \right\|_2^2 + \left[ \tau(t), f(t) - \sum_{k=1}^{K} v_k(t) \right] \tag{3}
$$

- (4) 使用交替方向乘子法迭代更新每个模态分量和中心频率，获得无约束函数的鞍点，即为该问题的最佳解。`v̂_l`, `ω_k`, `τ` 的迭代更新表达式如下：

$$
\hat{v}_k^{n+1}(\omega) = \frac{\hat{f}(\omega) - \sum_{i \neq k} \hat{v}_i(\omega) + \frac{\hat{\tau}(\omega)}{2}}{1 + 2\alpha(\omega - \omega_k)^2} \tag{4}
$$

$$
\omega_k^{n+1} = \frac{\int_{0}^{\infty} \omega |\hat{\partial}_k(\omega)|^2 d\omega}{\int_{0}^{\infty} |\hat{\partial}_k(\omega)|^2 d\omega} \tag{5}
$$

$$
\hat{\tau}^{n+1}(\omega) = \hat{\tau}^n(\omega) + \gamma \left[ \hat{f}(\omega) - \sum_{k=1}^{K} \hat{v}_k^{n+1}(\omega) \right] \tag{6}
$$

在公式 (6) 中，`n` 是迭代次数，`γ` 是噪声容忍参数。

- (5) 判断迭代终止条件。
