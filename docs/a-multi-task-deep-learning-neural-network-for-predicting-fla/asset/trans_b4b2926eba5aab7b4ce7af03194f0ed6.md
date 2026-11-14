

成功地应用于构建一个新的多任务模型，用于同时预测四个与易燃性相关的性质，并具有良好的准确性。与偏最小二乘法（PLS）的多任务学习技术相比，所提出的MDNN不要求训练集中的每个分子都具有一整套性质。因此，所提出的MDNN可以应用于更多样本，并提供更准确的预测。所提方法可以解决基于描述符的QSPR建模中的挑战，例如，为性质相关性开发合适的描述符、描述符的选择以及相关性分析。由于MDNN使用2D结构（SMILES）而非3D结构，因此在属性预测之前无需进行3D结构测定或预测，就可以更轻松地对先前未知的化合物进行大规模筛选。为避免使用深度学习模型所带来的风险，将异常值识别和AD确定引入MDNN模型的评估中。采用残差ECDF来识别这些异常值。本研究表明，基于PCA的AD分析和凸包计算，可以在潜在化学空间中观察异常值的位置。结果表明，在从训练集和验证集中剔除异常值后，AD变窄了。还可以发现，测试集中包含的一些化合物出现在AD之外。剔除异常值不一定能提高MDNN的预测能力。所提方法可以识别化合物的性质是在深度学习模型的AD内部还是外部进行估计。我们的策略可以为使用多任务深度学习建模具有多个性质输出的QSPR开辟新途径。这可以作为绿色化学数据驱动虚拟筛选的有前途工具。

## 利益冲突

无需声明任何利益冲突。

## 致谢

我们谨感谢以下机构提供的经费支持：中国自然科学基金（编号：21878028）；北京市科学技术领军人才培养工程（编号：Z171100001117154）；中国大陆、台湾和澳门大学联合监督方案——其他中国大陆、台湾和澳门大学（编号：SB2S）。

## 注释与参考文献

- 1 F. A. Quintero, S. J. Patel, F. Muñoz and M. S. Mannan, Ind. Eng. Chem. Res., 2012, 51, 16101–16115.
- 2 A. S. Hukkerikar, B. Sarup, A. T. Kate, J. Abildskov, G. Sin and R. Gani, Fluid Phase Equilib., 2012, 321, 25–43.
- 3 J. Frutiger, C. Marcarie, J. Abildskov and G. Sin, J. Hazard. Mater., 2016, 318, 783–793.
- 4 Y. Pan, J. Jiang, R. Wang, H. Cao and J. Zhao, QSAR Comb. Sci., 2008, 27, 1013–1019.
- 5 S. J. Patel, D. Ng and M. S. Mannan, Ind. Eng. Chem. Res., 2009, 48, 7378–7387.
- 6 A. R. Katritzky, R. Petrukhin, R. Jain and M. Karelson, J. Chem. Inf. Comput. Sci., 2001, 41, 1521–1530.
- 7 F. Gharagheizi, J. Hazard. Mater., 2009, 169, 217–220.
- 8 C. Nieto-Draghi, G. Fayet, B. Creton, X. Rozanska, P. Roteureau, J. C. de Hemptinne, P. Ungerer, B. Rousseau and C. Adamo, Chem. Rev., 2015, 115, 13093–13164.
- 9 Z. Jiao, H. U. Escobar-Hernandez, T. Parker and Q. Wang, Process Saf. Environ. Prot., 2019, 129, 280–290.
- 10 F. Gharagheizi, M. H. Keshavarz and M. Sattari, J. Therm. Anal. Calorim., 2012, 110, 1005–1012.
- 11 F. Gharagheizi, J. Hazard. Mater., 2009, 167, 507–510.
- 12 Y. Pan, J. Jiang, R. Wang, H. Cao and Y. Cui, Ind. Eng. Chem. Res., 2009, 48, 5064–5069.
- 13 J. A. Lazús, Thermochim. Acta, 2011, 512, 150–156.
- 14 J. Frutiger, C. Marcarie, J. Abildskov and G. Sin, J. Chem. Eng. Data, 2015, 61, 602–613.
- 15 J. Frutiger, J. Abildskov and G. Sin, 收录于第12届国际工艺系统工程研讨会和第25届欧洲计算机辅助工艺工程研讨会，2015年，DOI: 10.1016/b978-0-444-63578-5.50079-7，第503–508页。
- 16 J. Jaworska, N. Nikolova-Jeliazkova and T. Aldenberg, ATLA. Altern. Lab. Anim., 2005, 33, 445–459.
- 17 A. S. Hukkerikar, S. Kalakul, B. Sarup, D. M. Young, G. Sin and R. Gani, J. Chem. Inf. Model., 2012, 52, 2823–2839.
- 18 J. C. Dearden, P. Roteureau and G. Fayet, SAR QSAR Environ. Res., 2013, 24, 279–318.
- 19 S. Kim and K. H. Cho, Bull. Korean Chem. Soc., 2018, 40, 39–44.
- 20 A. Racz, D. Bajusz and K. Heberger, Mol. Inf., 2019, 38, e1800154.
- 21 T. Suzuki, K. Ohtaguchi and K. Koide, J. Chem. Eng. Jpn., 1991, 24, 258–261.
- 22 A. Alibakhshi, H. Mirshahvalad and S. Alibakhshi, Process Saf. Environ. Prot., 2017, 105, 127–133.
- 23 T. A. Albahri and R. S. George, Ind. Eng. Chem. Res., 2003, 42, 5708–5714.
- 24 T. Suzuki, Fire Mater., 1994, 18, 81–88.
- 25 A. A. Shimy, Fire Technol., 1970, 6, 135–139.
- 26 T. A. Albahri, Chem. Eng. Sci., 2003, 58, 3629–3641.
- 27 F. Gharagheizi, J. Hazard. Mater., 2009, 170, 595–604.
- 28 F. Gharagheizi, Energy Fuels, 2008, 22, 3037–3039.
- 29 M. Bagheri, M. Rajabi, M. Mirbagheri and M. Amin, J. Loss Prev. Process Ind., 2012, 25, 373–382.
- 30 M. S. High and R. P. Danner, Ind. Eng. Chem. Res., 1987, 26, 1395–1399.
- 31 J. R. Rowley, R. L. Rowley and W. V. Wilding, J. Hazard. Mater., 2011, 186, 551–557.
- 32 G. B. Goh, N. O. Hodas and A. Vishnu, J. Comput. Chem., 2017, 38, 1291–1307.
- 33 Z. Cang and G. W. Wei, PLoS Comput. Biol., 2017, 13, e1005690.
- 34 S. K. Chakravarti and S. R. M. Alla, Front. Artif. Intell., 2019, 2, 17.
- 35 Z. Wang, Y. Su, W. Shen, S. Jin, J. H. Clark, J. Ren and X. Zhang, Green Chem., 2019, 21, 4555–4565.
- 36 A. Mayr, G. Klambauer, T. Unterthiner and S. Hochreiter, Front. Environ. Sci., 2016, 3, 80.
- 37 G. B. Goh, C. Siegel, A. Vishnu, N. O. Hodas and N. Baker, 2017, ARXIV, 1706, 06689.
- 38 G. B. Goh, N. O. Hodas, C. Siegel and A. Vishnu, 2017, arXiv, 1712, 02034.
- 39 A. Lusci, G. Pollastri and P. Baldi, J. Chem. Inf. Model., 2013, 53, 1563–1575.
- 40 Y. Su, Z. Wang, S. Jin, W. Shen, J. Ren and M. R. Eden, AIChE J., 2019, 65, e16678.
- 41 R. Gomez-Bombarelli, J. N. Wei, D. Duvenaud, J. M. Hernandez-Lobato, B. Sanchez-Lengeling, D. Sheberla, J. Aguilera-Iparraguirre, T. D. Hirzel, R. P. Adams and A. Aspuru-Guzik, ACS Cent. Sci., 2018, 4, 268–276.
- 42 B. Saha, S. Gupta, D. Phung and S. Venkatesh, 知识与信息系统，2015年，vol. 46，第315–342页。
- 43 R. A. Caruana, 收录于《机器学习论文集1993》，Morgan Kaufmann，1993年，第41–48页。
- 44 J. Wenzel, H. Matter and F. Schmidt, J. Chem. Inf. Model., 2019, 59, 1253–1268.
- 45 A. Varnek, C. Gaudin, G. Marcou, I. Baskin, A. K. Pandey and I. V. Tetko, J. Chem. Inf. Model., 2009, 49, 133–144.
- 46 K. S. Tai, R. Socher and C. D. Manning, 第53届计算语言学协会年会和第7届国际自然语言处理联合会议论文集，2015年。
- 47 J.-L. Faulon, M. J. Collins and R. D. Carr, J. Chem. Inf. Model., 2004, 44, 427–436.
- 48 M. Tomas, S. Ilya, C. Kai, C. Greg and D. Jeffrey, 部分在第26届神经信息处理系统国际会议论文集（第2卷，内华达州湖塔霍，2013年）中发表。
- 49 X. Glorot, A. Bordes and Y. Bengio, J. Mach. Learn. Res., 2011, 15, 315–323.
- 50 V. Subramanian, 《使用PyTorch的深度学习》，Packt Publishing Ltd.，伯明翰，2018年。
- 51 G. Landrum, 期刊，2019年，www.rdkit.org/docs/.
- 52 T. Mikolov, I. Sutskever, K. Chen, G. Corrado and J. Dean, 计算机科学，2013年，第1–9页。
- 53 M. Abadi, P. Barham, J. Chen, Z. Chen, A. Davis, J. Dean, M. Devin, S. Ghemawat, G. Irving, M. Isard, M. Kudlur, J. Levenberg, R. Monga, S. Moore, D. G. Murray, B. Steiner, P. Tucker, V. Vasudevan, P. Warden, M. Wicke, Y. Yu and X. Zheng, 第12届USENIX操作系统设计与实现研讨会论文集，萨凡纳，2016年。
- 54 D. Kingma and J. Ba, 计算机科学，2014年，第1–15页。
- 55 S. b. A. 物理性质设计学院，DIPPR 801项目 - 完整版，物理性质研究设计学院/AIChE，2019年。
- 56 S. Kim, J. Chen, T. Cheng, A. Gindulyte, J. He, S. He, Q. Li, B. A. Shoemaker, P. A. Thiessen, B. Yu, L. Zaslavsky, J. Zhang and E. E. Bolton, Nucleic Acids Res., 2019, 47, D1102–d1109.
- 57 J. Godwin, 《TensorFlow中的多任务学习（第1部分）》（访问日期：2020年5月16日）。
- 58 R. Cipolla, Y. Gal and A. Kendall, 2018年IEEE/CVF计算机视觉与模式识别会议，2018年，第7482–7491页。
- 59 N. Reimers and I. Gurevych, 计算机科学 - 计算与语言，2017年。
- 60 T. A. Albrahri, Process Saf. Environ. Prot., 2015, 93, 182–191.
- 61 Y. Pan, J. Jiang, R. Wang, H. Cao and J. Zhao, J. Hazard. Mater., 2008, 157, 510–517.
- 62 G. Domenico, M. Giuseppe Felice, C. Marco, C. Angelo and N. Orazio, Int. J. Quant. Struct.-Prop. Relat., 2016, 1, 45–63.
- 63 K. G. Joback and R. C. Reid, Chem. Eng. Commun., 1987, 57, 233–243.
- 64 A. Z. Mendiburu, J. A. de Carvalho and C. R. Coronado, Fuel, 2017, 188, 212–222.
- 65 N. Nikolova-Zeliaskova and J. Jaworska, ATLA, Altern. Lab. Anim., 2005, 33, 461–470.
- 66 F. Gharagheizi, R. F. Alamdari and M. T. Angaji, Energy Fuels, 2008, 22, 1628–1635.

