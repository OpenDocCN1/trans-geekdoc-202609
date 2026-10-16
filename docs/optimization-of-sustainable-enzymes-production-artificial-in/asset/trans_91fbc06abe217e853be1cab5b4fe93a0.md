
## 5.12 ANN在发酵放大中的作用

数据统计工具的数据被用于大型发酵罐的开发，以准确预测影响产量的变量。来自生物传感器的离散信号以及变量对产量的非线性影响常常使得对发酵过程的控制变得困难。一项研究采用了ANN，该ANN评估生物传感器测量以控制酒精 fed-batch 发酵（[Ferreira et al. 2001](#ch5.xhtml#ref5_16)）。研究中使用了多层神经网络。输入层有两个神经元，输出层有一个神经元，隐藏层的神经元数量在 2 到 5 之间变化。底物浓度是受控变量，进料流量是被操控的变量。尽管网络的性能优于实验数据，但这仍可视为在工业中使用 ANN 控制生物传感器的第一步。[Zhang et al. (2020)](#ch5.xhtml#ref5_56) 成功构建了一个基于 ANN 的 *Clostridium butyricum* 1,3-丙二醇发酵过程的强健软传感器。深度 ANN 等先进的神经网络能够识别非线性和高度复杂、显而易见、隐蔽的过程参数之间的关系，并据此设计过程模型。由于生物传感器和其他系统的使用，它们能够通过预测生理漂移及其对产量和质量的影响，以及相应调整设定点和过程剖面，对过程偏差作出即时的短期响应（[Schmidt 2005](#ch5.xhtml#ref5_39)）。因此，神经网络工具可用于优化过程控制，并识别适合的工艺放大优化策略。它也是一种基于数据的算法，能够以任意精度逼近合理的函数。ANN 不需要事先了解变量之间的复杂关系，而是通过学习改变其结构，利用人工神经元的相互连接网络（[Geyikçi et al. 2012](#ch5.xhtml#ref5_18)），而在 RSM 中则是对因变量与自变量之间的未知形式进行逼近。统计模型的决定系数（R²）用于说明统计模型的整体效率。一个良好的模型应具有 R² 值小于 1。在 RSM 中，添加变量会使 R² 值提升，但不考虑其统计显著性，这限制了可测试的变量数量及其形式。RSM 主要用于在考虑显著参数后，找到最大或最小响应及其对应的最佳条件（[Nair et al. 2014](#ch5.xhtml#ref5_32)）。相反，ANN 利用所有数据点得到响应值，对数据的数量和形式更具灵活性（[Bezerra et al. 2008](#ch5.xhtml#ref5_5)）。已编译了一份比较 RSM 与 ANN 效率的重要出版物列表，见 [Table 5.2](#ch5.xhtml#table5_2)。

[Table 5.2 Summary of Publications that Compares Improvement in Production Using RSM and ANN](#ch5.xhtml#R_table5_2)

| Sl No. || Aim of the Study || Determination Coefficient (R²) RSM || Determination Coefficient (R²) ANN || Reference |
| --- | --- | --- | --- | --- |
| 1) || Analysis of heavy metal contamination || 0.67 || 0.89 || [Geyikçi et al. (2012)](#ch5.xhtml#ref5_18) |
| 2) || Extraction of Oleonolic acid from *Ocimum sanctum* || 0.91 || 0.94 || Khamparia et al. (2020) |
| 3) || Compressive strength of recycled concrete aggregates || 0.98 || 0.99 || Hammoudi et al. (2019) |
| 4) || Alkylbenzene synthesis over H14\[NaP5W30O110\]/SiO2 catalyst || 0.92 || 0.99 || Hafizi et al. (2013) |
| 5) || Extraction of artemisinin from *Artemisia annua* || 0.90 || 0.99 || Pilkington, Preston, and Gomes (2014) |
| 6) || Modeling of waste coconut oil ethyl esters production || 0.95 || 0.99 || Samuel and Okwu (2019) |
| 7) || Fluid extraction of phytochemicals from *Terminalia chebula* pulp || 0.997 || 0.998 || Jha and Sit (2021) |
| 8) || Production of bioethanol from pumpkin peel wastes || 0.97 || 0.99 || Chouaibi et al. (2020) |
| 9) || Optimization of gypsum-bonded fiberboards || 0.90 || 0.98 || Nazerian et al. (2018) |
| 10) || Optimization of Aegle marmelos Oil Extraction for Biodiesel Production || 0.97 || 0.99 || Selvan et al. (2018) |

## 5.13 结论

过去二十年，机器学习、人工神经网络（ANN）等技术的进步使得建模和优化的传统方法面临颠覆性挑战。响应面方法（RSM）是一种 widely 使用的优化工具，已被多个行业采用以优化并提升生产。RSM 是一个能够根据变量组合预测响应的优秀系统。对实验及前人研究的深入了解有助于最大化 RSM 方法的有效性。ANN、遗传算法等正在吸引大量研究者和科学家的关注。这类高级方法不依赖过程先验知识，而是通过构建所有可能数据点之间的连接来获得输出。诸如粒子群优化（PSO）等先进技术前景广阔，其目标是实现完全自适应、无需参数调制的优化器。此类技术在迭代过程中会调节参数并选择显著参数。通过将机器知识应用于酶的生产，未来可显著降低成本、步骤数量，从而提升规模化生产的可行性。

## References

*   [Abiodun, Oludare Isaac, Aman Jantan, Abiodun Esther Omolara, Kemi Victoria Dada, Nachaat AbdElatif Mohamed, and Humaira Arshad](#ch5.xhtml#R_ref5_1). 2018. “State-of-the-Art in Artificial Neural Network Applications: A Survey.” Heliyon 4 (11). Elsevier: e00938.

*   [Asmani, Katia Louiza, Khelifa Bouacem, Akli Ouelhadj, Merzouk Yahiaoui, Sofiane Bechami, Sondes Mechri, Fadoua Jabeur, Kahina Taleb-Ait Menguellet, and Bassem Jaouadi](#ch5.xhtml#R_ref5_2). 2020. “Biochemical and Molecular Characterization of an Acido-Thermostable Endo-Chitinase from *Bacillus Altitudinis* KA15 for Industrial Degradation of Chitinous Waste.” Carbohydrate Research 495 (September). Elsevier Ltd. doi:[10.1016/j.carres.2020.108089](http://dx.doi.org/10.1016/j.carres.2020.108089).

*   [Ba, Deniz, and Ismail H. Boyaci](#ch5.xhtml#R_ref5_3). 2007. “Modeling and Optimization I: Usability of Response Surface Methodology.” Journal of Food Engineering 78 (3). Elsevier Ltd: 836–845. doi:[10.1016/j.jfoodeng.2005.11.024](http://dx.doi.org/10.1016/j.jfoodeng.2005.11.024).

*   [Beg, Qasim Khalil, R. K. Saxena, and Rani Gupta](#ch5.xhtml#R_ref5_4). 2002. “Kinetic Constants Determination for an Alkaline Protease from *Bacillus Mojavensis* Using Response Surface Methodology.” Biotechnology and Bioengineering 78 (3): 289–295. doi:[10.1002/bit.10203](http://dx.doi.org/10.1002/bit.10203).

*   [Bezerra, Marcos Almeida, Ricardo Erthal Santelli, Eliane Padua Oliveira, Leonardo Silveira Villar, and Luciane Amélia Escaleira](#ch5.xhtml#R_ref5_5). 2008. “Response Surface Methodology (RSM) as a Tool for Optimization in Analytical Chemistry.” Talanta. Elsevier. doi:[10.1016/j.talanta.2008.05.019](http://dx.doi.org/10.1016/j.talanta.2008.05.019).

*   [Bottou, Léon, Frank E. Curtis, and Jorge Nocedal](#ch5.xhtml#R_ref5_6). 2018. “Optimization Methods for Large-Scale Machine Learning.” Siam Review 60 (2). SIAM: 223–311.
