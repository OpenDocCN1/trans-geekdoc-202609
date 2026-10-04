

在 [表 8.3](#ch8.xhtml#tab8_3) 中，研究人员展示了每种 ML 方法的性能指标。这些数值来自我们的实验，已证明算法在解决给定问题方面的有效性。显而易见，集成的 `SVM-GA` 方法表现最佳，准确率、精确率和 AUC 分数均最高。

[表 8.3：模型比较](#ch8.xhtml#R_tab8_3)

| Model comparison | | Accuracy (%) | | Precision (%) | | Recall (%) | | AUC score (%) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| SVM | | 75 | | 80 | | 80 | | 81 |
| --- | --- | --- | --- | --- | --- |
| RF | | 72 | | 77 | | 78 | | 81 |
| KNN | | 66 | | 70 | | 75 | | 72 |
| DT | | 74 | | 75 | | 83 | | 74 |
| ETC | | 74 | | 80 | | 79 | | 80 |
| NB | | 76 | | 79 | | 83 | | 83 |
| XG boost | | 68 | | 70 | | 78 | | 77 |
| Gradient boosting | | 74 | | 77 | | 81 | | 81 |
| **SVM-GA** | | **79.87** | | **91.91** | | 79.82 | | **84.53** |

## 5. Discussion

实验研究采用了九种不同的 ML 算法，包括 `SVM`、`RF`、`KNN`、`DT`、`NB`、额外树分类器、XG boost、梯度提升以及新颖的 `SVM-GA`。研究使用了 PIDD 数据集作为所有分类器的共同基础。执行了全面的预处理步骤以消除数据集中的空值，确保数据完整性。

为了稳健地评估模型性能，数据集已被细致地划分为两部分：80% 的训练数据集和单独的 20% 测试数据集。各种 ML 算法已一致应用于同一数据集，研究人员专注于工程化特征以评估其预测能力。研究人员进行了彻底的评估，利用准确率、精确率、召回率和 AUC 等关键性能指标，对每种算法的有效性进行全面评估。本研究的重点发现表明，创新的集成 `SVM-GA` 方法优于传统算法，表现出明显更高的识别性能。具体而言，该框架实现了令人印象深刻的平均 AUC 84.53%，超过了传统算法的性能。

## 6. Conclusions

将提出的 `SVM-GA` 模型应用于 PIDD 数据集证明了其在以高准确率、精确率、召回率和 AUC 对糖尿病进行分类和预测方面的有效性，优于 `LR`、`DT` 等传统 ML 模型。这凸显了集成 SVM 和 GA 算法以获得更好结果的潜力。所提出的方法有望为医疗专业人员在糖尿病预测和识别高风险患者方面提供帮助，实现早期诊断和经济有效的治疗。需要注意的是，模型准确性取决于数据集质量、大小和超参数调优。这些发现还表明了在预测其他疾病方面的未来应用，并呼吁进一步的研究和算法探索，包括集成模型，以提高准确性。探索更广泛的医疗应用，完善模型，并研究替代算法和集成方法以提高预测准确性。

## Acknowledgement

作者衷心感谢信息技术系的研究学者、教师和主管部门在研究中给予的合作。

## References

1. [Almutairi, E. S., Abbod, M. F., Almutairi, E. S., and Abbod, M. F.](#ch8.xhtml#R_ref8_1) (2023). Machine learning methods for diabetes prevalence classification in Saudi Arabia. Modelling, 4(1), 37–55. doi:[10.3390/MODELLING4010004](http://dx.doi.org/10.3390/MODELLING4010004).

2. [Aung, Y. Y. M., Wong, D. C. S., and Ting, D. S. W.](#ch8.xhtml#R_ref8_2) (2021). The promise of artificial intelligence: A review of the opportunities and challenges of artificial intelligence in healthcare. Br. Med. Bul., 139(1), 4–15. doi:[10.1093/BMB/LDAB016](http://dx.doi.org/10.1093/BMB/LDAB016).

3. [Chang, V., Bailey, J., Xu, Q. A., and Sun, Z.](#ch8.xhtml#R_ref8_3) (2023). Pima Indians diabetes mellitus classification based on machine learning (ML) algorithms. Neural Comput. Appl., 35(22), 16157–16173. doi:[10.1007/s00521-022-07049-z](http://dx.doi.org/10.1007/s00521-022-07049-z).

4. [Chauhan, T., Rawat, S., Malik, S., and Singh, P.](#ch8.xhtml#R_ref8_4) (2021). Supervised and unsupervised machine learning based review on diabetes care. 2021 7th Int. Conf. Adv. Comput. Comm. Sys. ICACCS, 581–585. doi:[10.1109/ICACCS51430.2021.9442021](http://dx.doi.org/10.1109/ICACCS51430.2021.9442021).

5. [Chen, W., Chen, S., Zhang, H., and Wu, T.](#ch8.xhtml#R_ref8_5) (2018). A hybrid prediction model for type 2 diabetes using K-means and decision tree. Proc. IEEE Int. Conf. Softw. Engg. Ser. Sci., 386–390. doi:[10.1109/ICSESS.2017.8342938](http://dx.doi.org/10.1109/ICSESS.2017.8342938).

6. [Dahiwade, D., Patle, G., and Meshram, E.](#ch8.xhtml#R_ref8_6) (2019). Designing disease prediction model using machine learning approach. Proc. 3rd Int. Conf. Comput. Methodol. Comm., doi:[10.1109/ICCMC.2019.8819782](http://dx.doi.org/10.1109/ICCMC.2019.8819782).

7. [“Diabetes.”](#ch8.xhtml#R_ref8_7) 2023. Accessed October 9. [https://www.who.int/news-room/fact-sheets/detail/diabetes](https://www.who.int).

8. [“Diabetes Dataset.”](#ch8.xhtml#R_ref8_8) 2023. Accessed October 9. [https://www.kaggle.com/datasets/mathchi/diabetes-data-set](https://www.kaggle.com).

9. [Doğru, A., Buyrukoğlu, S., and Arı, M.](#ch8.xhtml#R_ref8_9) (2023). A hybrid super ensemble learning model for the early-stage prediction of diabetes risk. Med. Biol. Engg. Comput., 61(3). doi:[10.1007/s11517-022-02749-z](http://dx.doi.org/10.1007/s11517-022-02749-z).

10. [Febrian, M. E., Ferdinan, X. F., Sendani, G. P., Suryanigrum, K. M., and Yunanda, R.](#ch8.xhtml#R_ref8_10) (2022). Diabetes prediction using supervised machine learning. Proc. Comp. Sci., 216. doi:[10.1016/j.procs.2022.12.107](http://dx.doi.org/10.1016/j.procs.2022.12.107).

11. [Ganie, S. M. and Malik, M. B.](#ch8.xhtml#R_ref8_11) (2022). An ensemble machine learning approach for predicting type-II diabetes mellitus based on lifestyle indicators. Healthcare Analyt., 2. doi:[10.1016/j.health.2022.100092](http://dx.doi.org/10.1016/j.health.2022.100092).

12. [Gotlieb, N., Azhie, A., Sharma, D., Spann, A., Suo, N. J., Tran, J., Orchanian-Cheff, A., et al.](#ch8.xhtml#R_ref8_12) (2022). The promise of machine learning applications in solid organ transplantation. NPJ Dig. Med., 5(1), 1–13. doi:[10.1038/s41746-022-00637-2](http://dx.doi.org/10.1038/s41746-022-00637-2).

13. [Injadat, M. N., Moubayed, A., Nassif, A. B., and Shami, A.](#ch8.xhtml#R_ref8_13) (2021). Machine learning towards intelligent systems: Applications, challenges, and opportunities. Artif. Intel. Rev., 54(5), 3299–3348. doi:[10.1007/s10462-020-09948-w](http://dx.doi.org/10.1007/s10462-020-09948-w).

14. [Khan, A., Uddin, S., and Uma, S.](#ch8.xhtml#R_ref8_14) (2019). Chronic disease prediction using administrative data and graph theory: The case of type 2 diabetes. Exp. Sys. Appl., 136. doi:[10.1016/j.eswa.2019.05.048](http://dx.doi.org/10.1016/j.eswa.2019.05.048).

15. [Kumar, P. S. and Pranavi, S.](#ch8.xhtml#R_ref8_15) (2018). Performance analysis of machine learning algorithms on diabetes dataset using big data analytics. 2017 Int. Conf. Infocom Technol. Unmanned Sys. Trends Fut. Dir., 508–513. doi:[10.1109/ICTUS.2017.8286062](http://dx.doi.org/10.1109/ICTUS.2017.8286062).

16. [Kyrou, I., Tsigos, C., Mavrogianni, C., Cardon, C., Stappen, V. V., Latomme, J., Kivelä, J., et al.](#ch8.xhtml#R_ref8_16) (2020). Sociodemographic and lifestyle-related risk factors for identifying vulnerable groups for type 2 diabetes: A narrative review with emphasis on data from Europe. BMC Endocr. Disord., 20(1), 1–13. doi:[10.1186/S12902-019-0463-3](http://dx.doi.org/10.1186/S12902-019-0463-3).

