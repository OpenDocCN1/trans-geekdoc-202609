
它指示模型执行的准确预测的百分比。它具体评估分类器正确区分正例或负例的能力。精确率（Precision）是通过将准确预测的正例数除以所有预测的总数（包括正确和错误的分类）来计算得出。

$$Precision = \frac{TP}{TP + FP}$$  

### Recall

它表示模型成功识别出的正例的百分比。它量化分类器有效定位所有属于指定目标类别的实例的能力。召回率（Recall）通过将目标类别的正确预测数除以所有预测的总数（包括准确和不准确的分类）来计算。

$$Recall: \frac{TP}{TP + FN}$$  

### F1-score

它表示准确的正预测所占的比例。该指标由精确率（Precision）和召回率（Recall）结合计算得出，范围从 1.0（最佳表现）到 0.0（最差表现）。由于 F1-score 同时考虑精确率和召回率，它比单纯的准确率更具信息性。在评估和比较分类器模型时，建议使用 F1-score 的加权平均值，而不是仅依赖整体准确率。

$$F1 - score = \frac{2 \ast Precision \cdot Recall}{Prectsion + Recall}$$  

### Support

它指实际数据集中特定类别的出现频率。它是衡量训练数据分布是否均匀或不均匀的指标。支持（Support）的差异可能暗示分类器报告的指标可能不够可靠。需要注意的是，Support 在不同模型中保持一致，其主要作用是辅助分析测试方法。

## VII. Discussion

农业部门在推动国家经济发展方面发挥着关键作用。为提升该部门的盈利能力和生产力，有必要探索创新解决方案。本文在研究论文中介绍了一种基于机器学习技术的作物推荐系统。该系统旨在帮助农民根据土壤属性和天气条件的复杂交互，做出准确的作物品种选择决策。

## VIII. Conclusion

本研究论文介绍了一种面向农民的作物推荐系统，旨在通过预测分析帮助农民做出最佳作物选择。该系统考虑了关键参数，包括土壤特性（NPK 含量、pH 值和湿度）以及气象因素（温度和降雨量）。在开发该系统时，采用了机器学习方法，包括 LR（逻辑回归）、DT（决策树）、RF（随机森林）以及 LightGBM。这些算法均在收集的数据集上进行了应用。数据集在预处理后呈现正态分布，几乎没有异常值，相关分析在预处理步骤之后完成。LightGBM 和 RF 在各类算法中表现出最高的准确率。展望未来，通过持续更新数据集，使系统与农业条件的演变保持同步，可进一步提升系统性能；此外，系统的范围还可以扩展以纳入作物病害检测功能，从而帮助农民在农业领域实现更大收益。

## References

*   [Chavva, Mr Konda Reddy](#ch7.xhtml#R_ref7_1). India at a glance. n.d. [https://www.fao.org/india/fao-in-india/india-at-a-glance/en/](https://www.fao.org) (accessed june 15, 2023).

*   [Gera, T., Singh, J., Mehbodniya, A., Webber, J. L., Shabaz, M., and Thakur, D.](#ch7.xhtml#R_ref7_2) (2021). Dominant feature selection and machine learning-based hybrid approach to analyze android ransomware. Sec. Comm. Netw., 2021, 1–22.

*   [Affarirs, M. O. H.](#ch7.xhtml#R_ref7_3) NCRB on data portal. \[Online\]. Available: [https://data.gov.in/search?title=suicide](https://data.gov.in).

*   [Pande, Shilpa Mangesh, Prem Kumar Ramesh, Anmol Anmol, B. R., Aishwarya, Karuna Rohilla, and Kumar Shaurya](#ch7.xhtml#R_ref7_4). (2021). Crop recommender system using machine learning approach. In 2021 5th international conference on computing methodologies and communication (ICCMC), 1066–1071. IEEE.

*   [António Monteiro, S. S. P. G.](#ch7.xhtml#R_ref7_5) (2021). Precision agriculture for crop and livestock. MDPI/Animals, 1–18.

*   Meshram, Vishal, Kailas Patil, Vidula Meshram, Dinesh Hanchate, and S. D. Ramkteke. (2021). Machine learning in agriculture domain: A state-of-art survey. Artificial Intelligence in the Life Sciences, 1, 1–11. doi: [https://doi.org/10.1016/j.ailsci.2021.10001](https://doi.org/10.1016/j.ailsci.2021.10001).

*   [Sharma, Pinkashia, and Jaiteg Singh](#ch7.xhtml#R_ref7_7). (2018). Machine learning based effort estimation using standardization. In 2018 International Conference on Computing, Power and Communication Technologies (GUCON), 716–720. IEEE.

*   Pudumalar, S., E. Ramanujam, R. Harine Rajashree, C. Kavya, T. Kiruthika, and J. Nisha. (2017). Crop recommendation system for precision agriculture. In 2016 Eighth International Conference on Advanced Computing (ICoAC), 32–36. IEEE.

*   [Jijo, B. T. and Abdulazeez, A. M.](#ch7.xhtml#R_ref7_9) (2021). Classification based on decision tree algorithm for machine learning. J. Appl. Sci. Technol. Trends, 02(1), 20–28.

*   [Rymarczyk, T., Kozlowski, E., Klosowski, G., and Niderla, K.](#ch7.xhtml#R_ref7_10) (2019). Logistic regression for machine learning in process tomography. Sensors, 1–19.

*   [Dabiri, Hamed, Visar Farhangi, Mohammad Javad Moradi, Mehdi Zadehmohamad, and Moses Karakouzian](#ch7.xhtml#R_ref7_11). (2022). Applications of Decision Tree and Random Forest as Tree-Based Machine Learning Techniques for Analyzing the Ultimate Strain of Spliced and Non-Spliced Reinforcement Bars. Applied Sciences. 12(10), 4851. 1–13 doi: [https://doi.org/10.3390/app12104851](https://doi.org/10.3390/app12104851).

*   [Tang, Mingzhu, Qi Zhao, Steven X. Ding, Huawei Wu, Linlin Li, Wen Long, and Bin Huang](#ch7.xhtml#R_ref7_12). (2020). An improved lightGBM algorithm for online fault detection of wind turbine gearboxes. Energies, 13(4): 807. 1–16. doi: [https://doi.org/10.3390/en13040807](https://doi.org/10.3390/en13040807).

*   [Raja, S. Kanaga Suba, R. Rishi, E. Sundaresan, and V. Srijit](#ch7.xhtml#R_ref7_13). (2017). Demand based crop recommender system for farmers. In 2017 IEEE Technological Innovations in ICT for Agriculture and Rural Development (TIAR), 194–199. IEEE. doi: [10.1109/TIAR.2017.8273714](http://dx.doi.org/10.1109/TIAR.2017.8273714).

*   [Doshi, Zeel, Subhash Nadkarni, Rashi Agrawal, and Neepa Shah](#ch7.xhtml#R_ref7_14). (2018). AgroConsultant: intelligent crop recommendation system using machine learning algorithms. In 2018 Fourth International Conference on Computing Communication Control and Automation (ICCUBEA), 1–6. IEEE. doi: [10.1109/ICCUBEA.2018.8697349](http://dx.doi.org/10.1109/ICCUBEA.2018.8697349).

*   [Kulkarni, Nidhi H., G. N. Srinivasan, B. M. Sagar, and N. K. Cauvery](#ch7.xhtml#R_ref7_15). (2018). Improving crop productivity through a crop recommendation system using ensembling technique. In 2018 3rd International Conference on Computational Systems and Information Technology for Sustainable Solutions (CSITSS), 114–119. IEEE. doi: [10.1109/CSITSS.2018.876879](http://dx.doi.org/10.1109/CSITSS.2018.876879).

*   Priyadharshini, A., Swapneel Chakraborty, Aayush Kumar, and Omen Rajendra Pooniwala. (2021). Intelligent crop recommendation system using machine learning. In 2021 5th international conference on computing methodologies and communication (ICCMC), 843–848. IEEE. doi: [10.1109/ICCMC51019.2021.941837](http://dx.doi.org/10.1109/ICCMC51019.2021.941837).

