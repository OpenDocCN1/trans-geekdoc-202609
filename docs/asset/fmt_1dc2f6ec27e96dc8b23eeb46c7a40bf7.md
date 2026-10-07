
Figure 30.4: Experimental results of closed loop power rate reaching law sliding mode controller for trajectory tracking.

$$F = \\left( - k\\overset{˙}{s} = - k \\middle| s \\middle| {}\_{\\infty}{sgn}(s) + \\frac{\\text{UA}\\left( {\\text{Tr} - \\text{Tj}\_{j}} \\right)}{\\text{mjCpj} - \\text{Td}\_{\\text{j}}} \\times \\frac{mj\\text{Cpj}}{\\text{Cpc}\\left( {T\_{j} - Tc} \\right)} \\right.$$

Figure 30.4 的轨迹跟踪响应在整个轨迹跟踪过程中出现了轻微振荡，并且冷却剂流量消耗很高。这表明 `SMC` 控制算法需要修订以改善闭环响应。

### 3.3. PI sliding surface

设计了切换控制律，其中滑模面被选为比例微分控制器，这消除了偏移并提供了良好的跟踪。由于间歇反应器的应用是跟踪温度，误差方程是滑模变量。幂次到达律被用作到达方程，以实现快速收敛。`PI` 控制器的方程为

`K = kpep + kpki∫epdt + P1(0)`

因此选择误差 `ep = Td - Tj`

代入 `PI` 方程，滑模面如下

$$\\overset{˙}{s} = kp\\left( {{\\overline{\\text{T}}}\_{\\text{d}} - {\\overset{˙}{\\text{T}}}\_{\\text{j}}} \\right) + \\text{kpki}\\left( {\\text{Td} - \\text{T}\_{\\text{j}}} \\right)$$

对滑模面求导，我们得到

$$\\overset{˙}{s} = kp(\\overset{˙}{T}d - \\overset{˙}{T}j) + kpki(Td - Tj)$$

为确保状态到达滑模面，等同于到达律方程

$$\\begin{array}{l} \\left. \\overset{˙}{\\text{s}} = - \\text{k} \\middle| \\text{s} \\middle| {}\_{\\infty}{sgn}(\\text{s}) \\right. \\\\ {\\overset{˙}{s} = kp\\left( {{\\overset{˙}{T}}\_{d} - \\left( U\_{A}\\left( {T\_{r} - T\_{j} - \\frac{FC\_{p}c\\left( {T\_{j} - T\_{c)}} \\right)}{m\_{j}C\_{pj}}} \\right) + kpk\_{i}\\left( {T\_{d} - T\_{i}} \\right) = - k \\middle| s \\middle| {}\_{\\alpha}{sgn}(s) \\right.} \\right.} \\\\ \\left. - k \\middle| s \\middle| {}\_{\\alpha}{sgn}(s) = kp{\\overset{˙}{T}}\_{d} - \\frac{kpU\_{A}\\left( {T\_{r} - T\_{i}} \\right)}{m\_{j}C\_{pj}} - \\frac{k\_{p}FC\_{pc}\\left( {T\_{j} - T\_{c}} \\right)}{m\_{j}C\_{pj}} + kpk\_{i}\\left( {T\_{d} - T\_{j}} \\right) \\right. \\\\ \\left. \\frac{k\_{p}FC\_{pc}\\left( {T\_{j} - T\_{c}} \\right)}{m\_{j}C\_{pj}} = kp{\\overset{˙}{T}}\_{d} - \\frac{kpU\_{A}\\left( {T\_{r} - T\_{i}} \\right)}{m\_{j}C\_{pj}} + kpk\_{i}\\left( {T\_{d} - T\_{i}} \\right) + - k \\middle| s \\middle| {}\_{\\alpha}{sgn}(s) \\right. \\\\ \\end{array}$$

整理项后得到控制律如下：

$$F = \\left( kp{\\overset{˙}{T}}\_{d} - \\frac{kpU\_{A}\\left( {T\_{r} - T\_{j}} \\right)}{m\_{j}C\_{pj}} + kpk\_{i}\\left( {T\_{d} - T\_{i}} \\right) + k \\middle| s \\middle| {}\_{\\alpha}{sgn}(s) \\right)\\left( \\frac{m\_{j}C\_{pj}}{k\_{p}C\_{pc}\\left( {T\_{j} - T\_{c}} \\right)} \\right)$$

Figure 30.5 显示了与之前另外两种 `SMC` 结果相比振荡减少的良好跟踪，之前的结果分别显示在 Figures 30.3 和 30.4 中。与其他两种 `SMC` 相比，冷却剂流量消耗也最优。

![Figure 30.5: Experimental results of closed loop PI sliding surface based sliding mode controller for trajectory tracking.](img/fig30_5_C.jpg)

Figure 30.5: Experimental results of closed loop PI sliding surface based sliding mode controller for trajectory tracking.

本文结果的改进可以与在同一间歇反应器装置上进行的常规 `PID` 控制器的实验结果进行比较。观察到 `NPID` [12, 13 and 14] 的控制信号与 Figure 30.3、Figure 30.4 和 Figure 30.5 所示的 `SMC` 实验结果相比振荡非常大。

### 3.4. Jetson board for control signal computation

目前作者正在使用 `Jetson` 开发套件与实时间歇反应器执行先进控制算法。需要使用电流-电压转换器和电压-电流转换器对传感器和执行器的信号进行适当的信号调理。`Jetson` 板没有模数转换器 (`ADC`)，因此需要使用额外的 `ADC` 来接口传感器和执行器信号。先进控制算法使用 `Python` 代码开发。`GPIO` 引脚需要为传感器和执行器信号接口进行配置。使用此 `Jetson` 的优势将增加控制信号的计算时间，以处理具有硬约束的高度非线性控制算法，并与间歇反应器接口 (Figure 30.6)。

![Figure 30.6: Jetson developer kit for control algorithm execution in advanced process control lab, MIT, Manipal for batch reactor.](img/fig30_6_C.jpg)

Figure 30.6: Jetson developer kit for control algorithm execution in advanced process control lab, MIT, Manipal for batch reactor.

## 4. Conclusions

在本文中，使用间歇反应器的非线性模型方程设计了一类 `SMC`。三种不同类型的控制器在实验装置上对温度进行了仿真和验证。实验结果表明，基于 `PI` 滑模面的 `SMC` 具有最小的被控变量作用，这意味着用于温度跟踪的冷却水量最少。另一方面，如果我们看跟踪误差，基本 `SMC` 有帮助，但在这种情况下没有获得最优控制信号。因此，基于跟踪误差或需要最优控制信号来决定控制算法的选择。

## 5. Acknowledgement

作者感谢 Manipal 高等教育学院 Manipal 提供的种子资金，用于间歇反应器冷却剂流量站的建立，资助编号：`00000220` 日期 `01/01/2020` 和资助编号：`00000860` 日期 `09/10/2023` 用于在间歇反应器上实施机器学习概念。

### References

1. Shettigar J. P., Lochan, K., Jeppu, G., Palanki, S., and Indiran, T. (2021). Development and validation of advanced nonlinear predictive control algorithms for trajectory tracking in batch polymerization. ACS Omega, 6, 22857–22865.

2. Shettigar J, P., Kumbhare, J., Yadav, E. S., and Indiran, T. (2022). Wiener neural network-based modeling and validation of generalized predictive control on a laboratory-scale batch reactor. ACS Omega, 7, 16341−16351.

3. Urmila, D. and Pahola, T. B. (2011). Optimal control of biodiesel production in a batch reactor Part II: Stochastic control. Fuels, 94, 218-226.

4. Palanki, S. (2005). Optimal operations of semi-batch processes with a single reaction. Int. J. Chem. React. Engg., 3(1), 1-9.

5. Arun Senthil, S. and Sundaramoorthy, S. (2018). 批式反应器温度最优进程跟踪的最优控制策略——目标函数选择的一些见解。IFAC Papers Online, 51(1), 112-117。

6. Billings, S. A. (2013). 非线性系统辨识：时域、频域和时空域的 NARMAX 方法。John Wiley & Sons。pp. 576。ISBN: 978-1-119-94359-4。

7. Yadav, E. S., Shettigar J.P., Poojary, S., Chokkadi, S., Jeppu, G., and Indiran, T. (2021). 试点工厂批式反应器的基于数据的建模及用于动态温度曲线跟踪的非线性模型预测控制器的验证。ACS Omega, 6, 16714–16721。

8. Narwekar, K. and Shah V. A. (2020). 使用滑模控制的温度控制：一种实验方法。载于：Tuba, M., Akashe, S., and Joshi, A. (eds) 信息与通信技术可持续发展。Advances in Intelligent Systems and Computing。Springer: Singapore, 933。

9. Narwekar, K. and Shah, V. A. (2018). 使用变结构控制的反应器温度控制。Int. J. Res. Anal. Rev., 5(3), 318-322。

10. Narwekar, K. and Shah, V. A. (2018). 使用滑模控制的耦合罐液位控制。Int. J. Res., 7(IX), 1025-1031。

11. Narwekar, K. and Shah, V. A. (2017). 使用滑模控制的化学批式反应器鲁棒温度控制。Int. J. Sci. Res. Manag. (IJSRM), 07, 6561-6568。

12. Mishra, S. R., Yadav, E. S., and Indiran, T. (2023, May). 实验室规模批式反应器加热系统上分程控制算法的验证。载于 AIP Conference Proceedings., 2752(1) 1-5。AIP Publishing。

13. Shettigar, J. P., Pai, A., Joshi, Y., Indiran, T., and Chokkadi, S. (2023). 实验室规模批式反应器上非线性 PID 控制器的验证。Comm. Comp. Inform. Sci., 1797, 47-59。

14. Bala Abhirami, M. and Thirunavukkarasu, I. (2023). 用于实验室规模批式反应器的基于最大灵敏度的 PID 控制器。Lec. Notes Elec. Engg., 957, 183-194。

# 31 使用数据科学的 3D 图像建模

Nishita Sharma, Divyanshi Mishra^(³¹)

Department of CSE, Dronacharya Group of Institution, Greater Noida, U. P., India

### Abstract

人们今天正在采用众多现代化策略并摒弃耗时繁琐的程序。本工作的目标是设计一个系统，该系统可以将纸上的图表或图形转换为可在数字环境中复制或更改的数字图像。时间是一个关键因素，无论是人类还是机器操作，在任何操作中都起着重要作用。人工智能（AI）、机器学习（M）、深度学习、视觉 API 等概念都可用于帮助系统直接设计任何图形或图表的图像，以便将其扫描图像的图像打印成 3D 建模图像。我们使用了深度神经网络，可以借助 TensorFlow 对其进行训练并用于各种任务。此模型中使用的其他技术有 RPN/OCR/GAN/VECTOR 成像和卷积神经网络（CNN），这些技术协同工作以检测、显示、生成、获取和提取以数字格式处理的數據。这些依赖项可能需要提供某些功能或使用特定程序功能。Recycler view 是一个用户界面元素，称为 recycler view，使我们能够制作可滚动列表。然后将使用软件的集成 3D 查看器预览我们的最终输出 3D 匹配图像。未来，该模型将能够自行掌握新技术、方法和模式，这将是 3D 图像建模领域的一项重大进步。

**关键词：** 数据科学、人工智能、机器学习和 3D 建模

### 1. Introduction

将手写件设计或使用数字格式是最受欢迎的活动之一。将物理图像转换为三维（3D）模型的概念使其易于使用和理解虚拟模型，具体取决于用户的需求。虽然可以将文本和图像传输到数字格式，但在将绘制的图形数字转换为 3D 模型方面仍有工作要做。在该领域，研究进行图像处理以从图像中提取有用信息、自动化与图像相关的流程，并使用卷积神经网络（CNN）根据图像数据进行预测。数据科学通过提供数据分析和图像操作的方法和资源，对数字 3D 图像建模做出了重大贡献，使用统计建模、机器学习算法和模式识别等技术。它能够进行特征提取、信号和维度增强、图像恢复和对象识别。

在先前的关于使用深度学习的文本到图像研究中，生成对抗网络（GAN）技术被用于图像生成和判别。结合自然语言工具包（NLTK），使用 GAN 生成了文本的数字 2D 图像，以便理解照片中文本的模式。使用提供的數據，图形用户界面（GUI）被用于为用户界面创建视觉上吸引人的窗口并更合适地显示照片\[1\]。然而，虽然该技术无法将单词转换为 3D 模型，但它只能提供用户提交的语言的 2D 表示。

另一项关于 2D-3D 图像转换的研究描述了如何使用不同的算法分析 2D 图像的深度维度，然后使用技术将其转换为 3D 模型。为了创建与给定的 2D 相似的图像，使用 KNN 搜索来区分相关和不相关的图像。维度、边缘和最近邻点已由深度融合与深度交叉偏差滤波引导，以创建 2D 照片的准确图像\[2\]。本文的目的是综合研究研究和数据科学算法，以便直接将文本转换为数字 3D 模型，并将物理绘制的图像转换为 3D 模型以便于理解和更用户友好的人机界面。在本文中，使用 TensorFlow 平台实现模型训练和跟踪以训练深度神经网络。除了矢量成像外，GAN 是用于生成逼真数据的另一种算法。此过程将手写输入转换为基于矢量的表示，这使得使用深度学习更易于操作和转换输入以数字创建 3D 模型。文本检测系统的重要部分使用诸如区域提议网络（RPN）和光学字符识别（OCR）之类的算法。OCR 可用于准确识别和伪装手写字符为数字表示。这两种算法可用于独立处理每个部分并生成高度准确和精确的 3D 模型。通过使用这些算法和技术，软件从原始手写输入创建的 3D 图像使用 3D 查看器和扫描仪显示以促进有效的人机界面。

## 2. Literature Review
