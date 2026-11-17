

为受PD影响的个体提高准确性，并推进个性化治疗方法。Ada Boost用于PD预测的最低准确率为83.495146。图17.8显示，ADA图表在预测PD方面的准确率为83.49%，显示出在智慧城市患者数据集预测中的更好性能。

![](img/96b9fa3db3bfeef3ca6e7362a69b2849_384_0.png)

图17.8 ADA Boost的混淆矩阵。

## 17.13 状态列的饼图分布

目标变量t表示PD的存在或不存在。值0表示不存在PD预测，而值1表示预测表明存在PD。这种二进制表示允许我们根据患PD的可能性对个人进行分类，从而使我们能够评估预测模型的有效性，并就疾病诊断和管理策略做出明智的决策。

图17.9表示，该饼图分布显示75.38%的人将受到PD影响，而未受此疾病影响的人将由值1%和24.62%表示，未受影响的值为0（表17.1）。

## 表17.1 各种机器学习算法比较表

| 使用的算法 | 准确率 (%) |
|---|---|
| XGBoost | 89.83 |
| 随机森林 | 93.71 |
| KNN | 98.30 |
| 决策树分类器 | 83.45 |
| SVM | 94.91 |
| 逻辑回归 | 74.57 |
| ADA Boost | 83.49 |

## 状态列的饼图分布

![](img/96b9fa3db3bfeef3ca6e7362a69b2849_385_0.png)

图17.9 状态列的饼图分布。

图17.10展示了一个比较图，将比较逻辑回归、决策树、随机森林、SVM、ADA Boost和KNN等算法，并将其准确率绘制在此比较图中。

![](img/96b9fa3db3bfeef3ca6e7362a69b2849_386_0.png)

图17.10 比较图。

## 17.14 结论

在智慧城市中利用元音发音数据进行帕金森病（PD）分类的有效性得到成功验证，KNN模型达到了98.305%的高准确率。此外，SVM模型也取得了94.915%的优异准确率，且两种模型在结果中均未出现假阳性。但最高准确率是通过KNN算法实现的。值得注意的是，KNN模型在平衡数据集上表现异常出色，进一步巩固了其作为可靠且准确的PD预测技术的潜力。根据研究结果，KNN模型将被推荐用于对PD进展进行分类。其非侵入性、简单性和高准确率使其成为为全球PD患者提供长期缓解的可行方案。通过利用元音发音数据，医疗从业者可以将此方法作为早期检测和监测疾病的有力工具，从而促进及时干预和个性化治疗策略。展望未来，智慧城市中PD预测的前景充满巨大希望。随着技术和机器学习算法的进步，预测模型有潜力得到进一步改进和优化。后续研究可能集中于探索超越元音发音数据的其他特征和生物标志物，结合多模态数据融合技术以提高预测准确性。此外，可穿戴设备和远程监测技术的集成可能使PD症状的实时监测成为可能，促进主动医疗干预并改善患者预后。医疗专业人员、研究人员和技术开发人员之间的合作将在推动创新和促进PD预测领域发展方面发挥关键作用。总之，本研究强调了利用机器学习方法（如KNN和SVM）使用元音发音数据进行PD分类的重要性。通过挖掘数据驱动方法的潜力，我们可以在早期诊断、量身定制的治疗以及提高PD受影响者生活质量方面取得显著进展。

## 参考文献

1. Sivachitra M., Vijayachitra S. 基于机器学习方法的帕金森病预测。2013年第五届国际先进计算会议（ICoAC），钦奈。
2. Tadse S., Jain Muskan, Pankaj Chandankhede 基于机器学习的帕金森病检测。2021年第五届国际智能计算与控制系统会议（ICICCS），马杜赖。IEEE。
3. Byeon H. 基于机器学习的帕金森病抑郁预测模型的开发。World J Psychiatry. 2020; 10(10): 234–244.
4. Boutet A., Madhavan R., Elias G.J.B., Joel S.E., Gramer R., Ranjan M., Paramanandam V., Xu D., Germann J., Loh A., et al. 利用功能性MRI和机器学习预测帕金森病最佳深脑刺激参数。Nat Commun. 2021;12(1):3043.
5. Dadu A., Satone V., Kaur R., Hashemi S.H., Leonard H., Iwaki H., Makarious M.B., Billingsley K.J., Bandres-Ciga S., Sargent L.J., et al. 利用机器学习在两个队列中识别和预测帕金森病亚型及进展。NPJ Parkinsons Dis. 2022;8(1):172.
6. Rastegar D.A., Ho N., Halliday G.M., Dzamko N. 利用机器学习（ML）和血清细胞因子预测帕金森病进展。NPJ Parkinsons Dis. 2019, 5:14.
7. Blauwendraat C., Bandres-Ciga S., Singleton A.B. 通过分析帕金森病患者的声音模式预测疾病进展。Lancet Neurol. 2017;16:860–862.
8. Das R. 各种多类分类方法用于诊断帕金森病的比较。Expert Syst. Appl. 2010;37:1568–1572.
9. Mall P.K., Yadav R.K., Rai A.K., Narayan V., Srivastava S. 利用机器学习技术预测帕金森病的早期预警信号。J. Pharm. Negat. Results 2023;14:2607–2615. 9p.
10. Rastegar D.A., Ho N., Halliday G.M., Dzamko N. 利用机器学习和血清细胞因子预测帕金森病进展。NPJ Park. Dis. 2019;5:14.
11. Agarwal A., Chandrayan S., Sahu S.S. 利用极端学习机和语音信号预测帕金森病。2016年国际电气、电子和优化技术会议（ICEEOT），钦奈，2016年。第3776–3779页。doi: 10.1109/ICEEOT.2016.7755419. https://colab.research.google.com/drive/1LuibQpCIK5PCaWpDSbT1jbrxGDCETb1QAagarwal
12. Miller D.B., O'Callaghan J.P. 帕金森病的生物标志物：现状与未来。Metabolism. 2015;64:S40–S46. doi: 10.1016/j.metabol.2014.10.030
13. Nilashi M., Abumalloh R.A., Minaei-Bidgoli B., Samad S., Ismail M.Y. "Machine Learning" 2022卷 | 文章ID 2793361来自'hindawi.com' 2022年2月3日发布。
14. Ahlrichs C., Lawo M. 机器学习中的帕金森病运动症状：综述。arXiv预印本 arXiv:1312.3825, 2013. doi: 10.5121/hiiij.2013.2401
15. Ahmadi S.A.A., Vivar G., Frei J., Nowoshilow S., Bardins S., Brandt T., Kraftczyk S. 迈向神经站立障碍的计算机化诊断：姿势图和摇摆的数据挖掘与机器学习。J. Neurol. 2019;266(Suppl 1):108–117. doi: 10.1007/s00415-019-09458-y
16. Jankovic J. 帕金森病：临床特征与诊断。J. Neurol. Neurosurg. Psychiatry. 2008;79:368–376. doi: 10.1136/jnnp.2007.131045
17. Dorsey E.R., Bloem B.R. 帕金森病大流行——行动呼吁。JAMA Neurol. 2018;75:9–10. doi: 10.1001/jamaneurol.2017.3299
18. de Lau L.M., Breteler M.M. 帕金森病流行病学。Lancet Neurol. 2006;5:525–535.
19. Rybicki B.A., Johnson C.C., Peterson E.L., Kortsha G.X., Gorell J.M. 家族帕金森病史及其对其他PD风险因素的影响。Neuroepidemiology. 1999;18:270–278. doi: 10.1159/000026222
20. Uitti R.J., Baba Y., Whaley N.R., Wszolek Z.K., Putzke J.D. 帕金森病：惯用手预测不对称性。Neurology. 2005;64:1925–1930. doi: 10.1212/01.WNL.0000163993.82388.C8
21. Bandres-Ciga S., Ahmed S., Sabir M.S., Blauwendraat C., Adarmes-Gómez A.D., Bernal-Bernal I., Bonilla-Toribio M., Buiza-Rueda D., Carrillo F., Carrión-Claro M., et al. 西班牙帕金森病的遗传结构：表征人群特异性风险、差异单倍型结构并提供病因学洞察。Mov. Disord. 2019;34:1851–1863. doi: 10.1002/mds.27864
22. Sreedevi B., Karthik D., Glory Thephoral J., Jeya Pandian M., Revathy G. 一种基于多层感知机和JRIP分类器的糖尿病预测新型神经网络模型。Pervasive Computing and Social Networking: ICPCSN 2022论文集。新加坡：Springer Nature Singapore，2022年。第345–351页。
23. Terrelonge M., Jr., Marder K.S., Weintraub D., Alcalay R.N. 新诊断帕金森病中脑脊液β-淀粉样蛋白1-42预测进展至认知障碍。J. Mol. Neurosci. 2016;58:88–92. doi: 10.1007/s12031-015-0647-x
24. Blauwendraat C., Heilbron K., Vallerga C.L., Bandres-Ciga S., von Coelln R.A.-O., Pihlstrøm L., Simón-Sánchez J., Schulte C.A.-O., Sharma M., Krohn L., et al. 帕金森病发病年龄全基因组关联研究：定义遗传率、遗传位点和α-突触核蛋白机制。Mov. Disord. 2019;34:866–875. doi: 10.1002/mds.27659
25. Nalls M.A., Blauwendraat C., Vallerga C.L., Heilbron K., Bandres-Ciga S., Chang D., Tan M., Kia D.A., Noyce A.J., Xue A., et al. 鉴定帕金森病的新风险位点、因果洞察和遗传风险：全基因组关联研究的元分析。Lancet Neurol. 2019;18:1091–1102.
26. Boutet A., Madhavan R., Elias G.J.B., Joel S.E., Gramer R., Ranjan M., Paramanandam V., Xu D., Germann J., Loh A., et al. 利用功能性MRI和机器学习预测帕金森病最佳深脑刺激参数。Nat. Commun. 2021;12:3043. doi: 10.1038/s41467-021-23311-9
27. Jankovic J. 帕金森病：临床特征与诊断。J. Neurol. Neurosurg. Psychiatry. 2008;79:368–376. doi: 10.1136/jnnp.2007.131045
28. Schrag A., Siddiqui U.F., Anastasiou Z., Weintraub D., Schott J.M. 患者中认知障碍预测的临床变量和生物标志物

