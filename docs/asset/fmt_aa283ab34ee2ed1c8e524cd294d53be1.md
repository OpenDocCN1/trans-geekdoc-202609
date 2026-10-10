
![](img/1f35685e7cacbaf02cbf5bba7a561027_116_1.png)

**图 5.5** 检测时间的分布。

整体检测时间保持在适当的毫秒级范围内，这表明系统能够快速处理事件。此外，即使检测时间存在波动，最高 1.0 ms 的上限也反映了其实时响应能力。系统处理海量数据并持续保持最小检测时间线的能力，与实时监控的研究目标一致。结果中所示的这种一致性能提升了系统的可靠性。

### 表 5.4 RF（随机森林）分类报告

| 指标 | 精确率 (Precision) | 召回率 (Recall) | F1 分数 | 支持数 (Support) |
|---|---|---|---|---|
| 良性 (0) | 0.97 | 0.99 | 0.98 | 3760 |
| 攻击 (1) | 0.96 | 0.94 | 0.95 | 6240 |
| 准确率 | | | | 10000 |
| 宏平均 (Macro Avg) | 0.97 | 0.97 | 0.97 | 10000 |
| 加权平均 (Weighted Avg) | 0.97 | 0.96 | 0.96 | 10000 |

精确率：随机森林模型具有高精确率，特别是对于良性 (0)，这意味着它在实际为攻击时，很少将其预测为良性。

召回率：它很好地捕捉了良性样本 (99%)，但漏掉了一些攻击（攻击 (1) 的召回率为 94%）。该模型对良性案例敏感，确保了正常流量很少被标记为攻击。

### 表 5.5 XGBoost 分类报告

| 指标 | 精确率 (Precision) | 召回率 (Recall) | F1 分数 | 支持数 (Support) |
|---|---|---|---|---|
| 良性 (0) | 0.98 | 0.98 | 0.98 | 3760 |
| 攻击 (1) | 0.95 | 0.96 | 0.95 | 6240 |
| 准确率 | | | | 10000 |
| 宏平均 (Macro Avg) | 0.96 | 0.97 | 0.96 | 10000 |
| 加权平均 (Weighted Avg) | 0.97 | 0.97 | 0.97 | 10000 |

精确率：XGBoost 优先考虑了良性 (0) 和攻击 (1) 的精确率，能够以极少的误报略好地识别真实攻击。

召回率：它对两类类别保持了平衡的召回率，确保攻击和良性流量都能被准确标记。

图 5.5 展示了检测时间的频率分布，范围从 0.0 ms 的最小时间到 0.999 ms 的最大时间，平均检测时间为 0.514 ms。这里的重要发现是突显了监控系统检测事件的效率。对于 10,000 个事件的数据集，低检测得分也反映了系统的扩展性，表明其能够高效地处理大规模工作负载。这一评估描述了系统检测机制的稳健性。即使事件中还包含高密度流量流（如 DDoS 模拟），系统仍然可以在不产生性能下降的情况下处理这些情况。

- RF – 表 5.4 展示了 RF 的分类报告。
- XGBoost – 表 5.5 展示了 XGBoost 的分类报告。

### 表 5.6 模型间的主要差异

| 特性 | 随机森林 (Random Forest) | XGBoost |
|---|---|---|
| 优势 | 对良性场景敏感（对正常流量的误报率低）。 | 攻击与良性检测之间平衡良好。 |
| 整体准确率 | 96% | 97% |

### 标签分布：DDoS 与良性

![](img/1f35685e7cacbaf02cbf5bba7a561027_118_0.png)

**图 5.6** 标签分布：DDoS 与良性。

表 5.6 显示了模型之间的主要差异。

### 5.6.3 检测事件分布（机器学习预测）

图 5.6 的饼图描述了基于机器学习预测的检测事件分布。这些预测来源于不同时间段的数据集，确保了在反映实时日志分析的动态输入数据时保持准确性，这与训练模型时静态数据集不同。该图显示了机器学习模型的准确发现，即考虑到 DDoS 攻击产生的巨大流量，DDoS 占了所分析总日志的 37.5%，而 62.5% 被归类为良性。这种视觉化展示了机器学习模型的能力，证明了它如何在模拟物联网网络中区分恶意流量和正常流量。良性流量和攻击流量的使用使得数据集更加平衡，避免了结果过于乐观。这种平衡验证了模型的稳健性，证实了其在处理大量良性流量的同时，能够准确检测 DDoS 攻击。该图还突显了模型跨不同数据集（实时日志）的适应能力。

## 使用 AI 优化边缘和雾计算应用

该研究探索了使用自适应方法对云端环境进行监控以检测威胁。虽然该研究展示了混合系统的潜力，但也暴露了与研究相关的若干局限性。攻击场景是在受控环境中进行的，未能捕获实际环境中可能发生的所有攻击变体。

- 真实世界集成：尽管我们的系统设计为在真实世界条件下运行，但目前仅通过仿真实现，因此，通过真实网络流量日志来验证系统至关重要，以捕捉数据中的不可预测性和多样性。这可以通过与组织合作，从这些组织获取大量的真实日志来实现。
- 自适应学习模型：系统的未来发展可以通过集成自适应模型来实现，这些模型将根据不同的网络活动或攻击模式进行动态更新。这将使得系统在识别零日攻击方面更加可靠。
- 商业化潜力：所提出的框架足够健壮，通过开发用户友好界面并对系统进行商业化封装，可以部署在中小型企业，因为它可以为他们提供一种可靠、可扩展且具有成本效益的防御策略。

## 参考文献

- 1. Korkos, R. (2023) Powering the Growth of Cloud Computing: Infrastructure Challenges and Solutions. Available at: www.forbes.com/councils/forbestechcountil/2023/07/24/powering-the-growth-of-cloud-computing-infrastructure-challenges-solutions/ [Accessed 25 November 2024].
- 2. Ahmadi, S. (2024) ‘Network Intrusion Detection in Cloud Environments: A Comparative Analysis of Approaches’, International Journal of Advanced Computer Science and Applications (IJACSA), 15(3), 2024. http://dx.org/10.14569/IJACSA.2024.015301
- 3. Saed, M. S., Saurabh, R., Basheme, S. R. and Nazarov, A. N. (2022) ‘Machine Based Intrusion Detection System in Cloud Environment’, in 2022 International Conference on Information Technology and Nanotechnology (ITNT). Samara, Russia Federation, 23-27 May 2022, pp. 1–6. https://doi.org/10.1109/ITNT55410.2022.9846811
- 4. NCCS (2024) Traffic GeneratorDDoS Tool. Available at: https://nccs.gov.in/public/events/DDoS%20Presentation%2017092024.pdf [Accessed 15 October 2024].
- 5. Oracle (2023) Design Guidance for SIEM Integration. Available at: https://docs.oracle.com/en-us/iaas/Cloud-adoption-framework/siem-integration.html?u [Accessed 27 November 2024].
- 6. Proofpoint (2024) Community Alert: Ongoing Malicious Campaign Impacting Microsoft Azure Cloud Environments. Available at: https://www.proofpoint.com/us/blog/cloud-security/community-alerting-malicious-campaign-impacting-azure-cloud-environments [Accessed 25 November 2024].
- 7. Tuisime, E., Balan, T. C., Cofas, P. A., Cofas, D. T., and Rekeraho, A. (2023) ‘Enhancing Cloud Security–Proactive Threat Monitoring and Detection Using a SIEM-Based Approach’, Applied Sciences, 13(22), 12359. https://doi.org/10.3390/app132212359
- 8. González-Granadillo, G., González-Zarzosa, S. and Diaz, R. (2021) ‘Security Information and Event Management (SIEM): Analysis, Trends, and Usage in Critical Infrastructures’, Sensors, 21(14), 4759. https://doi.org/10.3390/s21144759
- 9. Lee, J.-H., Kim, Y. S., Kim, J. H. and Kim, I. K. (2017) ‘Toward the SIEM architecture for cloud-based security’, in 2017 IEEE Conference on Communications and Network Security (CNS). Las Vegas, NV, 09–11 October 2017, pp. 398–399. https://doi.org/10.1109/CNS.2017.822869
- 10. A, A., Erlangga, D., Mantoro, T. and Handayani, D. (2024) ‘Enhancing Security Information and Event Management (SIEM) by Incorporating Machine Learning for Cyber Attack’, in 2023 IEEE 9th International Conference on Computing, Engineering and Design (ICED). Kuala Lumpur, Malaysia, 07–08 November 2023, 102328
- 11. Innab, N., Atoum, I., Alghaday, F., Abu-Zanoona, M., Alrubayi, N. and Basudan, F. (2024) ‘Intrusion Detection Systems in Cloud Computing: Techniques and Opportunities’, in 2024 3rd International Conference on Computer Applications & IoT (ICAS). Riyadh, Saudi Arabia, 26–28 February 2024, pp. 1–5. https://doi.org/10.1109/ICCR6006.2024.1053293
- 12. Munshi, A., Alqani, N. and Abdullah Ali, M. (2020) ‘DDoS Attack on IoT Devices’, in 2020 3rd International Conference on Computer Applications & Security (ICAS). Riyadh, Saudi Arabia, 19–21 March 2020, pp. 1–5. https://doi.org/10.1109/ICAS45589.2020.3090681
- 13. Çakmak, S. D., Hustchenreuter, H., Mader, C. and Kemmerich, T. (2021) ‘DDoS Attack and Response using SIEM’, in 2021 IEEE International Conference on Communications (ICCW). Montreal, QC, 14–17 June 2021, pp. 1–6. https://doi.org/10.1109/ICCW5038.97619
- 14. Dhahir, S. (2024) ‘A Hybrid Approach for DDoS Detection in SDN’, Journal of Future Intelligence and Technologies, 1(2), 174–190.
- 15. Chen, Z., Jiang, F., Cheng, X., Liu, W. and Peng, J. (2018) ‘Configuring Rule of Intrusion Detection System in IoT’, in 2018 IEEE International Conference on Big Data (BigComp). Shanghai, China, 251–256. https://doi.org/10.1109/BigComp4763.8984
- 16. Rochim, F. R. and Sunartyas, S. U. (2021) ‘Design an Intrusion Detection System Raspberry Pi for Home Network’, in 2021 17th International Conference on Quality in Research (QIR). Depok, Indonesia, 43–48. https://doi.org/10.1109/QIR354.9761
- 17. Arifin, S. H., Chong, J. L. and Wahab, N. H. (2021) ‘Configuring Rule of Intrusion Detection System in Cloud’, in 26th IEEE Asia-Pacific Conference on Communications (APCC). Kuala Lumpur, Malaysia, 298–303. http://doi.org/10.1109/APCC4927.5
- 18. Yasar, K. (2022) Elastic Stack. Available at: www.techtarget.com/searchopt/definition/Elastic-Stack [Accessed 20 October 2024].
- 19. [OCR 中未提供第 19 项的内容，已合并序列流]
- 20. Waldorf, A. (2022) 'Microsoft DDoS attack disrupted cloud services', TechTarget, 31 July. Available at: www.techtarget.com/searchsecurity/news/36659923/Microsoft-confirms-DDoS-attack-disrupted-cloud-services [Accessed 25 November 2024].
- 21. Waleed, A., Jamali, A. and Masood, A. (2022) 'Which open-source IDS?, Suricata or Zeek', Computer Networks, 213, p. 109116. https://doi.org/10.1016/j.comnet.2022.109116

## 使用 ML 模型保障 IoT 系统安全

## 第六章：协作预测性维护的联邦机器学习算法聚合策略

预测性维护（PdM）是工业 4.0 的组成部分，自动化、数字化转型和物联网（IoT）是升级工业过程的关键。PdM 通过利用实时传感器数据、云计算和高级分析来实现自动化决策过程，从而消除了对事后性维护和手动指令的需求。工业 4.0 的目标包括开发无需人工干预即可智能运行的自优化系统，这与此高度契合。此外，IoT 设备集成的无缝连接使得预测模型能够持续评估设备状况并建议预防措施。

生态系统确保企业在不断变化的技术背景下保持其竞争力 [1]。

非计划停机是工业领域面临的一个严重问题，经常会导致巨大的财务损失、运营延迟和声誉损害。预测性维护（PdM）通过在潜在设备故障发生前对其进行处理来降低这些风险，从而节省大量资金。例如，研究表明，非计划停机每小时可能给企业带来高达 260,000 美元的损失，而能源部门的故障（包括停电或轮机故障）可能导致数百万美元的收入损失。运输行业的设备故障会导致服务延迟、增加维护成本并中断关键的供应链。PdM 不仅降低了这些成本，还通过延长机械寿命和减少不必要的维修，实现了资源分配的最大化。

由于企业优先考虑成本效益，PdM 的经济效益使其成为可持续运营至关重要的策略。PdM 被应用于许多行业，每个行业都有自己的需求和困难。支持 IoT 的风力发电机可以跟踪温度、转速和振动等变量，允许在可再生领域早期识别发电机问题或叶片疲劳。类似地，电网中支持 IoT 的变压器和变电站可以预测过热或与电压激增相关的故障，确保电力供应并缩短维护时间。
