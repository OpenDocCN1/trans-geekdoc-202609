

根据对扰动的测量，动态修改控制器的参数。采取了以下措施。

1. 通过优化过程计算了适用于各种场景的线性控制器。
2. 开发了非线性补偿器，以适应不同的发动机转速值 ($N_{\text{engine}}$)。
3. 为了建立稳定性，成功解决了一个名为 LMI 的数学问题。
4. 所构建的控制器还提供了对调度机制的全面阐述，从而促进了工业环境中系统优化的过程。控制系统的评估以对比形式展示在图 2.7 中。

![](img/e9de70cd491e84262133af63cb33d500_49_0.png)

**图 2.7** 控制系统的对比评估。

该图表描绘了一条代表参考值的实线，一条代表具有前馈作用的线性控制器的虚线，以及一条代表模糊控制器的点线。显而易见，模糊控制器有效地减少了系统的超调量（O.S.）和调节时间。

## 关键词

- 模糊逻辑
- 无级变速箱
- 模糊控制器
- 模糊推理系统
- 非线性补偿器

## 参考文献

1. Grace. (1992). Optimization Toolbox—For use with MATLAB. Mathworks, Inc.
2. Isidori. (1989). Nonlinear Control Systems—An Introduction, 2nd edn. Springer-Verlag.
3. Peña Reyes, C. A. (2002). Cooevolutionary fuzzy modeling. PhD thesis, Ecole Polytechnique Fédérale de Lausanne.
4. von Alstroek. (1995). Fuzzy logic applications in Europe. Industrial Applications of Fuzzy Logic and Intelligent System, IEEE Press.
5. Broadbent. (1975). The magic number seven after fifteen years. Studies in Long Term Memory, Addison Wesley: USA.
6. Clarke, D., Mohtadi, C., & Tuffs, P. (1987). Generalized predictive control-parts i–ii. Automatica, 23, 137–160.
7. Drankov, D., Hellendoorn, H., & Reinfrank, M. (1993). An Introduction to Fuzzy Control. Springer-Verlag.
8. Goldberg, D. E. (1989). Genetic Algorithms in Search, Optimization and Machine Learning, Addison Wesley: USA.
9. Camacho, C. B. (1995). Model Predictive Control in the Process Industry. Springer-Verlag: London.
10. Gustafson, E., & Kessel, W. (1979). Fuzzy clustering with fuzzy covariance matrix. In: Proc. IEEE Control Decision Conference, pp. 761–766.
11. Ecole Nationale Supérieure de Techniques Avancées (ENSTA), Optimization and Control Group: (1998), LMITOOL-2.0 package.
12. Allgöwer, T. B., Qin, J., Rawlings, J., & Wright, S. (1999). Nonlinear predictive control and moving horizon estimation– an introductory overview. Advances in Control—Highlights of ECC’99. Springer-Verlag.
13. Box, G. J. (1970). Time Series Analysis, Forecasting and Control. Holden Day: San Francisco, CA.
14. Goodwin, G., & Sin, K. (1984). Adaptive Filtering Prediction and Control. Prentice Hall: Englewood Cliffs, NJ.
15. Lightbody, G., & Irwin, G. (1997). Nonlinear control structures based on embedded neural system models. *IEEE Transactions on Neural Networks and Learning Systems*, 8, 553–567.
16. Akaïke. (1974). A new look at the statistical model identification. *IEEE Transactions on Automatic Control*, 19, 716–723.
17. Ying, H. (1998). The Takagi–sugeno fuzzy controllers using the simplified linear control rules are the nonlinear variable gain controller. *Automatica*, 34(2), 157–167.
18. Abonyi, H. A., Nagy, L., & Széifert, F. Inverse fuzzy-process-model based direct adaptive control. URL citeeear.nj.nec.com/abonyi99inverse.html.
19. Bezdek. (1976). A physical interpretation of fuzzy data. *IEEE Transactions on Systems, Man, and Cybernetics 6*(5), 387–389.
20. Espinosa, J., & Vandewalle, J. (1998). Fuzzy modeling and identification, using afreli and fuzion algorithms. In: *Proceedings of the 5th. International Conference on Soft Computing IIZUKA-98 Iizuka, Japan*, pp. 535–540.
21. Espinosa, J., & Vandewalle, J. (1998). Fuzzy modeling with linguistic integrity. In: *Proceedings of the International Workshop on Advanced Black Box Techniques for Nonlinear Modeling Leuven, Belgium*, pp. 197–202.
22. Espinosa, J., & Vandewalle, J. (1998). Predictive control using fuzzy models applied to a steam generating unit. In: Ruan, D., Abderrahim, H. A., D’hondt, P., & Kerre, E. (Eds.), *Fuzzy Logic and Intelligent Technologies for Nuclear Science and Industry*. World Scientific: Singapore.
23. Espinosa, J., & Vandewalle, J. (1999). Constrained predictive control using fuzzy models. In: *Proceedings of the Eight International Fuzzy Systems Association World Congress (IFSA-99) Taiwan*, pp. 649–654.
24. Espinosa, J., & Vandewalle, J. (1999). Predictive control using fuzzy models. In: Roy, R., Furuhashi, T., & Chawdhry, P. (Eds.), *Advances in Soft Computing Engineering Design and Manufacturing*. Springer-Verlag: London.
25. Espinosa, J., & Vandewalle, J. (2000). Constructing fuzzy models with linguistic integrity-afredl algorithm. *IEEE Transactions on Fuzzy Systems*, 8(5), 591–600.
26. Espinosa, J., & Vandevvalle, J. (2003). Extracting linguistic fuzzy models from numerical data-afreli algorithm. In: Cassillas, J., Cordon, O., Herrera, F., & Magdalena, L. (Eds.), *Interpretable Issues in Fuzzy Modeling*. Springer-Verlag: London.
27. Espinosa, J., Hadjili, M., Wertz, V., & Vandewalle, J. (1999). Predictive control using fuzzy models-comparative study. *Proceedings of the European Control Conference-99*.
28. Rawlings, J. (1999). Tutorial: Model predictive control technology. In: *Proceedings of the ACC San Diego, CA*.
29. Richalet, J. (1993). Industrial applications of model-based predictive control. *Automatica*, 29, 1251–1274.
30. Sjberg, J., Zhang, Q., Ljung, L., Benveniste, A., Delyon, B., Glorermec, P., Hjalmarsson, J., & Juditsky, A. (1995). Nonlinear black-box modeling in system identification: A unified overview. *Automatica*, 31, 1691–1724.

# Taylor & Francis

Taylor & Francis Group
http://taylorandfrancis.com

![](img/e9de70cd491e84262133af63cb33d500_52_0.png)

## 机器学习与 AI 中的模糊逻辑：综合综述

S. LINGESWARI 和 T. REVATHI

*印度泰米尔纳德邦埃罗德 P.K.R. 艺术学院*

### 摘要

模糊逻辑是由 Lotfi Zadeh 在 20 世纪 60 年代引入的一种数学框架，它在人工智能（AI）和机器学习（ML）的各个领域中找到了深远的应用。本摘要探讨了模糊逻辑在增强 AI 和 ML 应用能力以及解决其面临的挑战方面的作用。模糊逻辑处理不确定性和不精确性，为建模复杂的现实世界现象、人类推理和决策过程提供了有价值的方法 [1]。在此背景下，我们讨论了将模糊逻辑融入 AI 和 ML 系统的关键应用、方法和优势。模糊逻辑脱颖而出的主要领域之一是处理数据中的不确定性和模糊性。在 AI 和 ML 中，数据往往是不完整或不精确的，这使得传统的二值逻辑不再适用。模糊逻辑提供了一套框架来表示和推理模糊信息，从而使 AI 系统能够做出更细微的决策 [4]。这在自然语言处理、情感分析和专家系统等领域的应用中尤为有用。此外，模糊逻辑在模糊推理系统（FIS）的开发中不可或缺，FIS 在 AI 和 ML 应用中得到广泛使用。FIS 可以建模输入和输出之间的复杂关系，使其适用于控制系统、预测和模式识别等任务。它们在自动驾驶车辆等应用中特别有用，因为实时决策依赖于对多样化和动态传感器数据的解释 [10]。在机器学习的背景下，已经开发了模糊聚类和模糊分类算法，以处理具有重叠或不确定边界的数据集。这些算法，如模糊 c 均值和模糊决策树，已应用于图像分割、医学诊断和推荐系统等领域。它们允许对数据点进行更细致的分类，提高了 ML 模型的准确性和可解释性。模糊逻辑在基于规则的系统中也起着关键作用，这对于 AI 中的专家系统和知识表示至关重要。模糊规则捕捉人类专业知识，可用于构建模拟人类决策的系统。这些系统在医学诊断、金融风险工业过程控制等应用中很有价值。总之，模糊逻辑继续成为 AI 和 ML 应用中的宝贵工具，提供了一种处理数据中不确定性、不精确性和复杂关系以及决策的手段。通过采用模糊逻辑，AI 和 ML 系统可以实现更大的鲁棒性、适应性和类似人类的推理能力，为跨各行业广泛的现实世界应用打开大门。本摘要提供了对模糊逻辑在推动 AI 和 ML 进步方面的多方面贡献的一瞥。

### 3.1 模糊逻辑简介

模糊逻辑是一种数学框架和一种多值逻辑形式，处理数据和决策中的不确定性、不精确性和模糊性 [1]。与基于“真”或“假”值（0 或 1）的经典二值逻辑不同，模糊逻辑允许表示部分真理和在集合中的成员资格程度，使其成为各个领域（包括人工智能（AI）、控制系统和决策）的宝贵工具。它由 Lotfi Zadeh 在 20 世纪 60 年代开发，作为一种在不确定性下建模和表示类似人类推理的方法。

### 3.2 模糊逻辑的组成部分

#### 3.2.1 模糊集

模糊集是模糊逻辑中的一个基本概念，它允许我们表示并处理不确定性和不精确性。与经典集合不同，在经典集合中，一个元素要么是成员（成员资格度为 1），要么不是成员

