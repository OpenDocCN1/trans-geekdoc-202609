
## 3.5 数值模拟器和机器学习计算时间

图 7.9 显示了使用 Intel core i5 – 11400H, 4.5 GHz 6Core, 和 16 GB of RAM 的 CMG 商用数值模拟器以及机器学习算法的模拟时间。可以看出，数值模拟执行所需运行时间很长。此外，模拟时间的显著减少表明机器学习代理模型（MARS 和 GMDH）的稳健性。此外，代理模型可以用作在所考虑的设计参数范围内 CO₂-LSWAG 的直接模拟的替代品。综上所述，使用 GPU（图形处理单元）可以进一步提高该机器学习算法的计算时间。与使用 GPU 相比，同时运行多次模拟时，该方法在速度和效率方面可能提供更大的益处。

![](img/80b94770dd572ad559c67fa9921bb887_169_0.png)

图 7.9. 机器学习和数值模型的模拟时间。

## 4. 结论

本研究解决的问题是对使用机器学习技术在碳酸盐岩储层中利用 CO₂-LSWAG 进行 EOR 的关注和研究不足。大多数 EOR 工艺中使用的水的质量和组成未得到充分考虑，且需要快速的计算方法来预测未来的采收率。我们使用了多相多组分流动方程、地球化学建模和组成模拟数据集来构建用于预测 CO₂-LSWAG EOR 在碳酸盐岩储层中石油采收率的代理模型。两种监督机器学习模型（MARS 和 GMDH）用于分析在各种低盐度条件下这些模拟生成的数据。本研究的结论如下：

- 1. 研究表明，在油田规模上实施 CO₂-LSWAG 可以通过主要减少粘性指进显著提高石油采收率。
- 2. 与用于 CO₂-LSWAG 石油采收率因子推导数学相关性的 MARS 预测模型相比，GMDH 模型给出了更好的测试预测结果。
- 3. 机器学习模型通过显著减少模拟时间并在不损害所需精度的情况下进行泛化，预测了商业模拟器的输出。
- 4. 建议根据当前研究在油田规模上实施 CO₂-LSWAG，以提高采收率同时降低运营成本。

## 致谢

我们对匿名审稿人表示感谢，他们宝贵的意见对本研究的成功做出了重大贡献。此外，我们对计算机建模集团（CMG）提供对完成本项目至关重要的商业软件表示感谢。最后，我们承认加纳塔夸矿业科技大学、GNPC 石油研究学院以及石油和天然气工程系提供的不可或缺的支持。

## 参考文献

Afzali, S., Rezaei, N. and Zendehboudi, S.A. 2018. 水交替气（WAG）注入提高采收率的综合综述. *Fuel* 227: 218–246. https://doi.org/10.1016/j.fuel.2018.04.015.

Ahmed, T. 2018. *储层工程手册* (第 4 版). Elsevier Inc.

Al-Abri, H., Pourasary, P., Mosavat, N. and Al Hadrami, H. 2019. LSWA CO₂ EOR 技术在砂岩中提高石油采收率性能的研究. *Petroleum* 5(1): 58–66. https://doi.org/10.1016/j.petlm.2018.07.003.

Alaidan, A. A. and Mamora, D. 2010. 通过降低水盐度提高碳酸盐岩岩心 Smart CO₂ 和 WACO₂ 效率. *于：加拿大非常规资源和国际石油会议.* https://doi.org/10.2118/137548-MS.

Aleidan, A. A. and Mamora, D. 2011. 高度非均质碳酸盐岩岩心中可混相 CO₂ 注入：实验和数值模拟研究. *于：SPE 中东石油和天然气展览会和会议.* https://doi.org/10.2118/141469-MS.

Aliyuda, K., Howell, J. and Humphrey, E. 2020. 地质变量对控制油藏性能的影响：机器学习技术的见解. *SPE Reservoir Evaluation & Engineering* 23(04): 1314–1327. https://doi.org/10.2118/201196-PA.

Al-Jifri, M., Al-Attar, H. and Boukadi, F. 2021. 用于预测水驱非均质储层采收率因子的新代理模型. Journal of Petroleum Exploration and Production 11(3): 1443–1459. https://doi.org/10.1007/s13202-021-01095-4.

Alpak, F.O, Araya-Polo, M. and Onyearogu, K. 2019. 断层浊积岩储层的简化动态建模：用于勘探的采收率预测的深度学习方法. In: SPE Reservoir Evaluation & Engineering 22(04): 1240–55. https://doi.org/10.2118/197053-PA.

AlQuraishi, A.A. and Shokir, E.M. El-M. 2011. 可混相 CO2 驱的实验研究, Journal of Petroleum Science and Technology 29(19). https://doi.org/10.1080/10916461003662976.

AlQuraishi, A.A., Amao, A.M., Al-Zahrani, N.I., AlQarni, M.T. and AlShamrani, S.A. 2019. Berea 和 Bentheimer 砂岩中低盐度水和 CO2 可混相驱. Journal of King Saud University – Engineering Sciences 31(3): 286–295. https://doi.org/10.1016/j.jksues.2017.04.001.

Al-Shalabi, E.W., Sepehrnoori, K. and Pope, G. 2014. 注射低盐度水和二氧化碳对碳酸盐岩储层联合作用的地球化学研究. Energy Procedia 63: 7663–7676. https://doi.org/10.1016/j.egypro.2014.11.800.

Al-Shalabi, E., Sepehrnoori, K. and Pope, G. 2016. 碳酸盐岩岩心中低盐度水和二氧化碳联合作用的数值模拟. Journal of Petroleum Science and Engineering 137: 157–171. https://doi.org/10.1016/j.petrol.2015.11.021.

Amar, M.N., Ghafarokhi, A.J., Ng, C.S.W. and Zeraibi, N. 2021. 使用严格的软计算技术和受自然启发的算法对实际地质油田进行 WAG 优化. Journal of Petroleum Science and Engineering 206(109038): 1–13. https://doi.org/10.1016/j.petrol.2021.109038.

Belazreg, L. and Mahmood, S.M. 2020. 水交替气增量采收率因子预测及 WAG 先导试验经验教训. Journal of Petroleum Exploration and Production Technology 10: 249–269. https://doi.org/10.1007/s13202-019-0694-x.

Branson, E.T., Ju, B., Omisore, O.O., Wu, D., Aphu, E.S. and Liu, N. 2018a. 开发机器学习预测模型用于历史拟合致密气碳酸盐岩储层生产剖面. Journal of Geophysics and Engineering 15(5): 7–12. https://doi.org/10.1088/1742-2140/aaca44.

Branson, E.T., Ju, B., Omisore, B.O., Wu, D., Selase, A.E. and Liu, N. 2018b. 开发机器学习预测模型用于历史拟合致密气碳酸盐岩储层生产剖面. Journal of Geophysics and Engineering 15(5): 2235–2251.

Branson, E.T., Ju, B., Ziggah, Y.Y., Akwensi, P.H., Sun, Y., Wu, D. and Addo, B.J. 2019. 使用生产率、软计算和群体智能模型预测非常规储层水平气井产量递减. Natural Resources Research 28: 717–756.

Chen, Y., Zhu, Z., Lu, Y., Hu, C., Gao, F., Li, W., Sun, N. and Feng, T. 2020. 利用数据分析和基于神经网络的类比研究进行储层采收率估计. *于：SPE/IATMI 亚太石油天然气会议与展览.* https://doi.org/10.2118/196487-MS.

Christensen, J.R., Stenby, E.H. and Skauge, A. 1998. WAG 油田经验综述. *于：墨西哥国际石油会议和展览会论文集.* https://doi.org/10.2118/90589-MS.

Dang, C.T.Q, Nghiem, L.X, and Chen, Z. 2014. CO2 低盐度水交替气：一种提高采收率的新前景方法. *于：SPE 提高采收率研讨会，1–19.* https://doi.org/10.2118/169071-MS.

Farlow, S.J. 1984. GMDH 型算法建模中的自组织方法. New York: Marcel-Dekker. CRC Press.
