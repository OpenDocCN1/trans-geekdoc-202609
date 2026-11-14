

| 模型 | 准确率 (%) |
| :--- | :--- |
| FNN | 97.00% |
| BiLSTM | 96.12% |
| XGBoost | 81.01% |
| RF | 80.20% |
| SVM | 79.80% |
| LightGBM | 77.81% |
| LR | 77.65% |
| DT | 77.62% |

图 12：各模型的分类准确率。基于神经网络的方法显著优于传统机器学习模型，FNN 达到最高测试准确率（97%），其次是 BiLSTM（96.12%）。

## 5 结论

在本工作中，我们利用商业智能手表收集的各类生理数据，分析并预测了情绪状态。我们使用了 LifeSnaps 公共数据集，该数据集包含了 71 名来自不同人口统计区域的志愿者在 2021 年 5 月至 2022 年 1 月期间，使用商用 Fitbit Sense 智能手表收集的生理传感器数据和心理调查数据。我们分析了该数据集，并基于生理数据与自我报告情绪状态之间进行了相关性研究，以验证本研究的可行性。从相关性来看，我们发现 bpm、resting hr、filteredDemographicVO2max 和 calories 与情绪的相关性较高。我们根据相关性强度调整了权重。我们应用了六种不同的 ML 算法（SVM、LR、DT、LightGBM、XGBoost 和 RF），并使用 RF 达到了最高准确率 78.75%。随后，我们使用了信号域特征，并利用递归特征消除法配合两种拟议方法（基于选择性特征的方法和基于整体特征的方法），为分类模型选择最优特征。我们发现，在 164 个特征中，96 个特征最适合分类模型，基于这些特征，我们的预测准确率从 78.75% 提高到了 81.01%。接下来，我们应用基于神经网络的方法预测情绪，并使用深度神经网络达到了最高准确率 97%。因此，我们的拟议方法系统地帮助去除了无关和冗余特征。我们的研究表明，商用智能手表可以利用智能手表监测个人的情绪状态。

未来，我们将评估拟议方法是否能在商用智能手表上有效工作以监测心理健康。其次，由于大多数现实世界数据集都包含缺失或噪声数据，我们将开发一种改进算法来准确处理缺失和噪声数据。

## References

- [1] Prakash, J., Ali, T., Chaudhury, S. & Srivastava, K. (2023, Jul–Dec). 身心健康下降：快节奏城市化的后果. Industrial Psychiatry Journal, 32(2), 199–201.
- [2] Joormann, J. & Siemer, M. (2014). 情绪障碍中的情绪调节. 413–427.
- [3] Yfantidou, S., Karagianni, C., Efstathiou, S., Vakali, A., Palotti, J., Giakatos, D. P., Marchiori, T., Kazlouski, A., Ferrari, E. & Girdzijauskas, S. (2022). LifeSnaps：一套为期 4 个月的多模态数据集，捕捉我们在野外生活的不经意瞬间. Scientific Data, 9(1), 663.
- [4] Yu, F., Yu, C., Tian, Z., Liu, X., Cao, J., Liu, L., Du, C. & Jiang, M. (2024). 基于数字孪生技术的具有运动和情绪识别功能的智能可穿戴系统. IEEE Internet of Things Journal.
- [5] Qi, Y., Jia, W., Feng, L., Dai, Y., Tang, C., Zhou, F. & Gao, S. (2024). 基于压电触觉感知和随机森林技术的情绪识别方法. IEEE Transactions on Computational Social Systems.
- [6] Kwon, O. Y., Lee, S. H. & Park, K. R. (2021). 使用眼镜式可穿戴设备进行情绪识别. Sensors, 21(5), 1786.
- [7] Olsen, P. A., Kuerbis, A. & Muench, F. (2016). 基于智能手机的心理健康监测：精神科护理中移动感知应用的开发与可行性. Journal of Medical Internet Research, 18(6), e156.
- [8] Chow, P. I., Fua, K., Huang, Y., Bonelli, W., Xiong, H., Barnes, L. E. & Teachman, B. A. (2017). 利用移动感知测试大学生中抑郁、社交焦虑、状态情感和社会隔离的临床模型. Journal of Medical Internet Research, 19(3), e62.
- [9] Zhang, X., Li, W., Chen, X. & Lu, S. (2018). Moodxplorer：利用智能手机感知进行复合情绪检测的探索. Proceedings of the ACM on Interactive, Mobile, Wearable and Ubiquitous Technologies, 1(4), 1–30.
- [10] Ghosh, S., Hiwarte, K., Ganguly, N., Mitra, B. & De, P. (2019). 智能手机文本输入过程中的触摸交互情绪检测. International Journal of Human-Computer Studies, 130, 47–57.
- [11] Hashmi, M. F., Katiyar, S., Keskar, A. G., Bokde, N. D. & Geem, Z. W. (2020). 基于深度学习和 OVIS 方法的运动传感器人类活动识别. Sensors, 20(21), 6176.
- [12] Wu, C. H. & Yan, G. L. (2021). 利用数据增强和深度神经网络之间的竞争改进情绪识别. Sensors, 21(10), 3465.
- [13] Asare, K. O., Terhorst, Y., Vega, J., Peltonen, E., Lagerspetz, E. & Ferreira, D. (2021). 基于手机使用模式预测情绪. International Journal of Human-Computer Studies, 145, 102548.
- [14] Toshnazarov, K., Lee, U., Kim, B. H., Mishra, V., Najarro, L. A. C. & Noh, Y. (2024). Sosw：在野外使用现成智能手表进行压力感知. IEEE Internet of Things Journal.
- [15] Sultana, M., Al-Jefri, M. & Lee, J. (2020). 利用机器学习以及智能手机和智能手表数据检测情绪状态和转变：探索性研究. JMIR mHealth and uHealth, 8(9), e17818.
- [16] Wang, Z., Yu, Z., Zhao, B., Guo, B., Chen, C. & Yu, Z. (2020). EmotionSense：基于可穿戴智能设备的自适应情绪识别系统. ACM Transactions on Computing for Healthcare, 1(4), 1–17.
- [17] An, P., Zhu, J. S., Zhang, Z., Yin, Y., Ma, Q., Yan, C., Du, L. & Zhao, J. (2024). Emowear：探索智能手表语音消息交互中的情绪引导. Proceedings of the CHI Conference on Human Factors in Computing Systems, 1–16.
- [18] Shu, L., Yu, Y., Chen, W., Hua, H., Li, Q., Jin, J. & Xu, X. (2020). 使用智能手环心率数据进行可穿戴情绪识别. Sensors, 20(3), 718.
- [19] Fauzi, M. A. & Yang, B. (2021). 使用智能手表传感器和分类器集成对医院员工进行持续压力检测. pHealth 2021, 245–250.
- [20] Vaizman, Y., Ellis, K. & Lanckriet, G. (2018). Extrasensory 应用：带有丰富用户界面以自我报告行为的野外数据收集. CHI Conference on Human Factors in Computing Systems, 1–12.
- [21] Wang, J., Huang, Y., Song, S., Wang, B., Su, J. & Ding, J. 一种用于高级 EEG 情绪识别的新颖傅里叶邻接变换器. arXiv preprint arXiv:2503.13465, 2025.
- [22] Cruz-Vazquez, J. A., Montiel-Pérez, J. Y., Romo-Herrera, R. & Rubio-Espino, E. (2025). 使用高级变换和深度学习从 EEG 信号进行情绪识别. Mathematics, 13(2), 254.
- [23] Yang, S., Wang, W., Mao, P., Xu, L. & Feng, L. (2025). 基于 EEG 信号分数傅里叶变换的 DFRFT-ES 情绪识别模型. 第四届计算机视觉、应用与算法国际会议（CVAA 2024）. 13486, 50–55, 页.
- [24] Murauggapan, M. & Murauggapan, S. (2013). 使用快速傅里叶变换通过短时脑电图信号进行人类情绪识别. 在 2013 年 IEEE 第 9 届信号处理及其应用国际学术会议上（第 289–294 页）. IEEE.
- [25] Warburton, D. E. R., Jamnik, V. K., Bredin, S. S. D., McKenzie, D. C., Stone, J., Shephard, R. J. & Gledhill, N. 基于证据的体育活动许可风险评估与建议：PAR-Q+ 合作共识文件. (2011).
- [26] Mroczek, D. K., Ozer, D. J., Spiro, A. III & Kaiser, R. T. (1998). 评价五因素人格模型的测量. Assessment, 5(3), 287–301.
- [27] Donnellan, M. B., Oswald, F. L., Baird, B. M. & Lucas, R. E. (2006). Mini-IPIP 量表：微小而有效的五大人格因素测量. Psychological assessment, 18(2), 192.
- [28] Mláčik, B. & Goldberg, L. R. (2007). 跨文化人格量表分析：克罗地亚的 IPIP 五大人格因素标志. Journal of personality assessment, 88(2), 168–177.
- [29] Murcia, J., Gimeno, E. C. & Camacho, A. M. (2007). 在体能健身环境中测量自我决定动机：西班牙样本中 BREQ-2 的验证. The Journal of Sport Medicine and Physical Fitness, 47(3), 366–378.
- [30] Rodrigues, F., Macedo, R., Teixeira, D. S., Cid, L. & Monteiro, D. (2020). 运动与体育中的动机：BRSQ 与 BREQ 的比较. Quality & Quantity, 54(4), 1335–1350.
- [31] Spielberger, C. D., Sydeman, S. J., Owen, A. E. & Marsh, B. J. (1999). 使用状态-特质焦虑量表（STAI）和状态-特质愤怒表达量表（STAXI）测量焦虑和愤怒. Lawrence Erlbaum Associates Publishers.
- [32] Watson, D., Clark, L. A. & Tellegen, A. (1988). 正负情绪简易测量的开发与验证：PANAS 量表. Journal of Personality and Social Psychology, 54(6), 1063.
- [33] Sarmah, P. P., Paul, P. S. & Hazra, K. (2025). 基于商用智能手表预测情绪——大数据叙事. 2025 年 IEEE 技术与管理社会创新跨学科方法国际会议（IATMSI）, 3, 1–6. doi: 10.1109/IATMSI64286.2025.10984709.
- [34] Soni, S., Gupta, S. N., Devi, R. & Hazra, K. (2024). 使用基于规则的 NLP 从推特中提取信息以进行灾害损失评估. 在第 15 届计算、通信与网络技术国际会议（ICCCNT）论文集（第 1–6 页）. 印度卡马ンド. doi: 10.1109/ICCCNT61001.2024.10724068.

