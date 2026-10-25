

## 性能度量

![](img/be689ed28322f90f68916a35ce44e55d_268_0.png)

图 12.6 各种模型的性能度量。

在尽可能保持目标函数最小的同时 [40,41]。极端梯度提升决策树，即 XGBoost，是一个分类和回归树集成模型。为了预测输出，XGBoost 模型 [42,43] 从一组基学习器 xi = f1, f2, f3, fK 开始，其中 fK 是一个不同的树结构，K 是加法项的数量。在迭代 t 时，通过研究所有基学习器/函数并选择一个能减少损失的，可以降低目标函数。

数据集主要使用十倍交叉验证测试划分为测试集和训练集。数据集经过 ML 方法处理，并计算性能度量。

性能度量比较如图 12.6 所示。从图中可以推断，XGBoost 比其他模型更准确。XGBoost 的准确率最高，为 99%。SVM 和 NB 紧随其后，准确率均为 98%。然后 LR 为 97%，RF 为 96%，最后 DT 达到 94% 的准确率。

从这些结果可以推断，在其他五个模型中，XGBoost 表现良好。表 12.4 显示了模型执行所需的总时间。结果表明，XGBoost 的执行速度比其他模型快，耗时 0.010 秒。

表 12.4 执行时间比较

| 序号 | 算法 | 计算时间（秒） |
|---|---|---|
| 1 | XGBoost | 0.010 |
| 2 | LR | 0.064 |
| 3 | RF | 0.533 |
| 4 | DT | 0.354 |
| 5 | SVM | 0.328 |
| 6 | NB | 0.024 |

随机森林执行较慢，紧随随机森林之后，决策树执行时间为 0.354 秒[44]。

## 12.5 结论

本文提出了一种集成的 AI-SDN-IoMT 架构，用于预测患者中的 COVID-19。IoMT 设备中的传感器通过 SDN 网络与智能系统通信。为了预测疾病，构建了一个基于机器学习的预测模型。实现了不同的机器学习模型，XGBoost 在准确率、精确率、召回率、F1 分数和 ROC-AUC 分数等性能度量方面表现突出。此外，它的执行速度比其他技术更快。

未来我们将添加更多机器学习模型，并使用多准则决策来选择最佳模型。此外，我们还将探讨隐私和安全问题。

## 参考文献

- 1. J. G. Ko, C. Lu, M. B. Srivastava, J. A. Stankovic, A. Terzis, and M. Welsh, “医疗保健中的无线传感器网络,” IEEE 学报, Vol. 98, No. 11, 2010 年 11 月, 10.1109/JPROC.2010.2065210.
- 2. M. M. Khan, S. Mehnaz, A. Saha, M. Nayem, and S. Bourouis, “基于 IoT 的 COVID-19 患者智能健康监测系统”, 计算与数学医学方法, Vol. 2021, 1–11, 2021, 10.1155/2021/8591036.
- 3. S. Vishnu, S. R. Jino Ramson, R. Jegan, “医疗物联网（IoMT）概述,” 2020 年第 5 届器件、电路与系统国际会议 (ICDCS), 2020.
- 4. M. W. Nadeem, H. G. Goh, V. Ponnusamy and Y. Aun, “使用机器学习技术的 SDN 中 DDoS 检测,” 计算机、材料与继续, Tech Science Press, Vol. 71, No. 1, 2022, DOI: 10.32604/cmc.2022.021669.
- 5. V. Juyal et al. “关于在延迟容忍网络中利用动态可信路由方案,” 无线个人通信, vol. 112, 1705–1718, 2020.
- 6. M. Pal, S. Parija, R. K. Mohapatra, S. Mishra, A. A. Rabaan, A. A. Mutair, S. Alhumaid, J. A. Al-Tawfiq, and K. Dhama, “基于 AI 的 IoT 中的基于症状的 COVID-19 预后：生物信息学方法”, 生物医学研究国际, Vol. 2022, 1–12, 2022, 10.1155/2022/3113119.
- 7. A. Raj, V. Sharma, and A. K. Shanu, “基于 IoT 的设备中联邦学习的安全和隐私技术比较分析,” 2022 年第 3 届计算、自动化与知识管理国际会议 (ICCAKM), 阿联酋迪拜, 2022, pp. 1–5, doi: 10.1109/ICCAKM54721.2022.9990152.
- 8. Jyval, V. et al., “延迟容忍网络路由解剖,” 2016 年 IEEE 计算智能与计算研究国际会议 (ICCIC), 金奈, 2016, pp. 1–4. doi: 10.1109/ICCIC.2016.7919724
- 9. M. Y. Shaheen, “医疗保健中的 AI：医学社会经济效益与挑战,” ScienceOpen 预印本, 2021, 10.14293/S2199-1006.1.SOR-.PPRQNI.v1.
- 10. R. C. Deo, “医学中的机器学习,” 循环, vol. 132, 1920–1930, 2015.
- 11. A. Agha, 人工智能的医学应用, 第 1 版. Taylor & Francis Group, 巴吞鲁日.
- 12. T. Keski-Filppula, M. Nikki, M. Haapea, N. Ramanauskas, O. Tervonen, “在芬兰奥卢初级保健环境中使用人工智能检测无显著发现的胸部 X 光,” arXiv, 2022, 10.48550/arXiv.2205.08123.
- 13. M. N. R. D. S. Murali and V. Sharma, “使用人工神经网络的 DGA 驱动僵尸网络性能分析,” 2022 年第 10 届可靠性、信息通信技术与优化国际会议 (趋势与未来方向) (ICRITO), 2022, pp. 1–6, doi: 10.1109/ICRITO56286.2022.9965044.
- 14. A. Maurya and V. Sharma, “使用 Keras 和 CNN 的面部情绪识别,” 2022 年第 2 届先进计算与工程创新技术国际会议 (ICACITE), 2022, pp. 2539–2543, doi: 10.1109/ICACITE53722.2022.9823480.
- 15. H. Y. R. Chiu, C. K. Hwang, S. Y. Chen et al., “新兴传染病领域响应的机器学习,” Sci Rep, vol. 12, 328, 2022. 10.1038/s41598-021-03687-w.
- 16. A. Bhargava, A. Bansal and V. Goyal, “基于机器学习的新型冠状病毒（COVID-19）疾病自动检测,” Multimed Tools Appl, vol. 81, 13731–13750, 2022, 10.1007/s11042-022-12508-9.
- 17. A. Pyrros, J. Rodriguez Fernandez, S. M. Borstelmamn, A. Flanders, D. Wenzke, et al., “用于从 COVID-19 胸部 X 光片中预测死亡率和合并症的深度学习、基于价值的护理模型验证,” PLOS 数字健康, vol. 1, no. 8, e0000057, 2022. 10.1371/journal.pdig.0000057.
- 18. S. V. Kogilavani, J. Prabhu, R. Sandhiya, M. S. Kumar, U. S. Subramaniam, A. Karthick, M. Muhibbullah, and S. B. S. Imam, “基于深度学习技术的肺 CT 扫描 COVID-19 检测”, 计算与数学医学方法, Vol. 2022, 1748-670X, 2022, 10.1155/2022/7672196.
- 19. V. Dwivedy, H. D. Shukla, and P. K. Roy, “LMNet: 用于 IoMT 环境中 COVID-19 检测的轻量多尺度卷积神经网络架构”, 计算机与电气工程, 2022, 108325, 10.1016/j.compeleceng.2022.108325.
- 20. E. Yildirim, M. Cicioğlu and A. Çalhan, “用于早期检测 COVID-19 的实时医疗物联网框架,” Neural Comput & Applic, 2022. 10.1007/s00521-022-07582-x.
- 21. X. Jiang, M. Coffee, A. Bari, J. Wang, X. Jiang et al., “面向数据驱动的冠状病毒临床严重程度预测的人工智能框架,” 计算机、材料与继续, vol. 63, no. 1, 537–551, 2020.
- 22. S. Singh, A. S. Nandan, G. Sikka, A. Malik, and A. Vidyarthi, “使用 IoMT 的疾病数据传输安全节能路由协议,” 计算机与电气工程, Vol. 101, 108113, 2022, 10.1016/j.compeleceng.2022.108113.
- 23. Beverly Park Woolf, 第 7 章 - 机器学习, 编辑: Beverly Park Woolf, 构建智能交互式导师, Morgan Kaufmann, 2009, pp. 221–297.
- 24. B. Ramasubramanian and G. Anitha, “糖尿病视网膜图像中新血管检测的高效方法,” Int. J. Eng. Innov. Technol, vol. 2, no. 3, pp. 240–244, 2012.
- 25. L. M. Koonin et al., “COVID-19 大流行期间远程医疗使用趋势 — 美国，2020 年 1 月 – 3 月”, Morb. Mortal. Wkly. Rep., Vol. 69, pp. 1595–1599, 2020.
- 26. A. A. Toor, M. Usman, F. M. Younas, A. C. Fong, S. A. Khan, S. Fong, “面向 IoMT 启用医疗系统的大规模电子健康数据流挖掘,” Sensors, vol. 20, no. 7, 2131, 2020. 10.3390/s20072131.

