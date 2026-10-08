

![](img/601340ca744b738277eef45ff127492a_82_0.png)

图 A.2. 基于 EDA 的特征提取。

## 附录 B.2. 频域

从 TEB 计算的频率特征与从 ECG 计算的特征相似。因此计算了原始信号的 PSD 以及信号的滤波版本。同样，除了标准参数外，还评估了功率比。

## 附录 B.3. 混合域

考虑的特征是 CCV 混合域参数（在这种情况下，使用平均 BR 来最小能量平方根）。

## 附录 C. 来自 EDA 信号的特征

用于从 EDA 信号提取最相关信息的结构与 ECG 信号和 TEB 信号中描述的结构相似。

图 A3 显示了从 EDA 信号获得的测量值以及提取特征的过程。总共，我们获得了 62 个时间特征和 42 个频率特征。考虑到 EDA 同时在手和手臂上记录（如上所述），我们从手臂 EDA 获得了 104 个特征，从手部 EDA 获得了 104 个特征。

### 附录 C.1. 时域

我们获得了四个时域测量值：

- EDA-Original：对 EDA-Original 信号计算 13 个 SSSP 和上述基准参数。还通过测量计算了面积，并使用单位间距的梯形法对时间段进行近似积分。
- EDA-LF：使用截止频率为 0.2 Hz 的 20 阶低通 FIR 滤波器（LF块）对原始信号进行滤波 [41]。评估了 13 个 SSSP 和基准参数。
- EDA-HF：使用互补滤波器获取高频分量（截止频率为 0.2Hz 的 20 阶高通滤波器），并在获得的 EDA-HF 测量值上评估与 FDA-LF 测量相同的参数。
- EDA-Processed：工作 [26] 显示了处理 EDA 信号以检测皮肤电导反应（SCR）的步骤。该过程包括去均值、重采样为 20 Hz、时间差分以及使用 20 阶 Bartlett 窗滤波。从处理后的 EDA 测量值中，从 SSSP 和基准参数以及一些特定参数中提取了典型参数。
- Zero Crossing (ZC)：正 Z (PZC) 和负 Z (NZC) 对当前应用很有意义 [26,41]。
- 负样本比例或比例 (PNS)，评估方法为负样本数与总样本数之比 [41]。
- 分析了处理后 EDA 信号中的 SCR 零交叉点。SCR 发生时的信号幅和分析窗口内的发生次数用作参数 [26,42,54,91]。SCR 是通过首次连续的零交叉点（从负到正，再从正到负）确定的。

### 附录 C.2. 频域

从 EDA-Original、EDA-LF 和 EDA-HF 中提取 PSD，并使用 Welch 重叠段估计器将其作为频谱测量值。从中计算了 SSSP 和基准参数。

# 参考文献

1. Rueda, F.M.; Lüdtke, S.; Schröder, M.; Yordanova, K.; Kirste, T.; Fink, G. Combining Symbolic Reasoning and Deep Learning for Human Activity Recognition. In Proceedings of the 2019 IEEE International Conference on Pervasive Computing and Communications Workshops (PerCom Workshops), Kyoto, Japan, 11-15 March 2019, pp. 22–27.
2. Chen, LM.; Nugent, C. Sensor-Based Activity Recognition Review. In Human Activity Recognition and Behaviour Analysis; Springer: Cham, Germany, 2019, pp. 23–47.
3. Tapia, E.; Intl, S.; Larson, K. Activity recognition in the home using ubiquitous sensors. In Proceedings of the International Conference on Pervasive Computing, Linz and Vienna, 21–23 April 2004.
4. Kim, E.; Dae, S.; Cook. Human activity recognition and pattern discovery. IEEE Peruasive Comput. 2010, 9, 48–53.
5. Bao, L.; Intse, S. Activity recognition from non-annotated annotation. In Proceedings of the International Conference on Pervasive Computing, Linz and Vienna.
6. Handley, T.; Lewin, J.; Perkins, D.; Kelly, B. Self-recognition of mental health problems in a rural setting. Aust. J. Health Research 2019, 28, 173–180.
7. del Miljan, R.; Jordanova, M.; Miccinotti, F.; Varta, M.; Heikkonen, J.; Babifon, F. A local neural classifier associated to stress. IEEE Neural Networks 2002, 12, 678–686.
8. Holings, K.; Dato, Y.; Rothholtz, J. Emotion recognition using brain activity. In Proceedings of the 9th International Conference on Computer Systems and Workshop for PhD Students, Gabrovo, Bulgaria, 12–13 June 2006.
9. Cloete, T.; Scheffer, C. Benchmarking of a full-body inertial motion system for gait. In Proceedings of the 30th Annual International Conference on Engineering and Biology Society, Vancouver, Canada, 20–25 August 2008, pp. 4570–4582.
10. Fong, D.; Chang, Y. The use of wearable sensors in lower limb movements: a systematic review. Sensors 2020, 10, 11556–11565.
11. Kwasnij, J.; Weiss, G.; Moore, S. Activity recognition using cell phone accelerometers. ACM SIG Electronics Newsletter.2011, 12–78.
12. Mshali, H.; Jemouna, T.; Mooney, G.; Magoni, D. A survey on health monitoring for smart homes. Int. J. Erg. 2019, 66, 26–56.
13. Albanie, S.; Nagrani, A.; Vedaldi, A.; Zisserman, A. Emotion Recognition Using Cross-Modal Transfer in the Wild. Available online: https://arxiv.org/abs/1808.0561 (accessed on 12 December 2019).
14. Wang, S.; Phillips, P.; Dong, Z.; Zhang, Y. Intelligent facial recognition based on stationary wavelet transform. Neurocomputing 2018, 666–676.
15. Mohino, I.; Goni, M.; Alvarez, L.; Gil-Pita, R. Detection of emotions and stress through speech analysis. In Proceedings of the Signal Processing Conference, Innsbruck, 12–14 February 2013.
16. Busco, C.; Deng, Z.; Yildirim, S.; Bulut, M.; Lee, C.; Kazemazed, A.; Neumann, U.; Narayanan, S. Analysis of emotion recognition using facial expressions, speech and multimodal information. In Proceedings of the 6th International Conference on Multimodal Interfaces, College, PA, USA, 205–217 13 October 2004.
17. Wei, D.; Nagai, Y.; Jin, J.; Kano. Designing comfortable smart for infants. Int. J. Smart City Creativity 2019, 31, 116–128.
18. Jitta, S.; Murakaran, M.; Rajagan, R.; Wei, K. Psychological factors based human emotion recognition: A Review. In Proceedings of the 7th International Conference on Signal Processing and Interfaces, Penang, Malaysia, 4–6 March 2011, pp. 410–415.
19. Fratiadis, Z.; Danakis, A.K. EEG pattern recognition system for emotion detection. IEEE Trans. Comput. 2012, 3, 102–115.
20. Rittany, K.; Muktamov, A. Emotion recognition for service robots in the intelligent world using daily life. Adj. Comput. Intell. Intell. 2011, 15, 58–591.
21. Lara, O.D.; Madrid, M. A study on emotion recognition using wearable sensors using short-term spectrum analysis of heart variability. Surya. 2013, 1192–1209.
22. Neuman, S.; Waldstein, S. Stress induced cardiovascular response during emotional activation as a function of affective valence and gender. J. Psychosom. 2001, 50, 245–253.
23. Mohino-Herrans, I.; Gil-Pita, R.; Ferrari, J.; Rosa-Zuera, M.; Seanne, F. Assessment of mental, and physical stress through analysis of physiological signals. Sensors 2015, 15, 25607–25627.
24. Kim, K.H.; Bang, S.; Kim, Y. Emotion recognition using short-term monitoring of physiological signals. Mon. Biol. Eng. 2004, 42, 419–427.
25. Prochakov, D. Emotional Intelligence in Psychology Research; Pedersen: Amsterdam, 2012.
26. Drachenbach, A.; Lee, E.; Yannakakis, G. Correlation between heart rate, electroderm activity and experience in first-person shooter games. In Proceedings of the 5th ACM SIG Conference on Video Games, Los Angeles, USA, 28–29 July 2010: pp. 49–54.
27. Nowacki, J.; Luft, E. Changes in electrodell activity as a function of students' anxiety. Ind. Diff. 1987, 8, 615–626.
28. Bellman, R. Dynamic Programming: University Press: Princeton, NJ, 1957.
29. Myers, K.; Bello-Espinoza, L.; Lemones, J.; Zuberi, S.; Clegg, J.; Gray, R.; Sadler, L.; Buchhalter, J.; Scheffer. Heart rate variability: a biomarker of stress under unexpected death in epilepsy. Epile 2018, 59, 1372–1380.
30. Cai, J.; Liu, Y.; Han, M. Research on emotion recognition using EEG. In Proceedings of the 2009 International Conference on Information Technology and Computer Science, Kiev, Ukraine, 25–26 June 2009, pp. 497–500.
31. Rumpa, L.; Dibasa, A.; Attamani, M.; Sampelawang, P.; Purnomo, M.H.; Palleng, S. Analysis of Human Heart Rate using Sad Video Imagery with Heart Rate Variability Indices (HRVI). In Proceedings of the 2018 International Conference on Computer Engineering, Network and Intelligent Multimedia (CENIM), Surabaya, Indonesia, 26–27 November 2018: pp. 25–28.
32. Malik, M.; Berger, J.T.; Hamm, A.J.; Klein, R.E.; Rianelli, M.; Moss, A.; Schwartz, P.J. Heart rate variability: Standards of measurement, physiological interpretation, and clinical use. Eur Heart J. 19, 1754–3761.
33. Cripps, T.; Malik, M.; Farrell, T.; Kahn, C. Prognostic value of reduced heart rate variability after myocardial infarction: clinical evaluation of a new method. Br Heart J. 1991, 65, 14–39.

