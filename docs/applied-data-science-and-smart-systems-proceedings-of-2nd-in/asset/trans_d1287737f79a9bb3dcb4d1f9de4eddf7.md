
它是通过对这种基于频率的方法进行研究，本文旨在在电动汽车（EV）背景下解决减振器性能优化的挑战（`[Tiwari et al., 2020](#ch43.xhtml#ref43_5)`）。通过利用电动减振器的内在特性，这项研究旨在阐明提升车辆稳定性和提供更精细驾驶体验的道路（`Faheem et al., 2016`）（`[Figure 43.1](#ch43.xhtml#fig43_1)`）。

![Figure 43.1 Electric shock absorbers](images/fig43_1_B.jpg)

[Figure 43.1 Electric shock absorbers](#ch43.xhtml#R_fig43_1)

## 相关工作

使用可变输出电动减振器的想法是文献综述的主要议题。文章讨论了减振对舒适性和稳定性的重要性，尤其是在电动汽车中。文章强调了使用可调减振比的电动减振器以提升车辆动力学并减少振动。

电动减振器很重要。文章在评估的开头就讨论了减振器在现代汽车中的重要性，特别关注它们如何减少传动系统振动并改善驾乘质量。虽然可变输出减振器是高端汽车的特征，但文章指出传统减振器（固定输出）的局限性（`[Fateh et al., 2009](#ch43.xhtml#ref43_8)`）。

### 可变输出电动减振器的概念

本文提出了适用于各类汽车的可变输出电动减振器的设想。通过在行驶过程中调节阻尼比，这些电动减振器旨在提高稳定性并降低行驶频率（`[Amar et al., 2011](#ch43.xhtml#ref43_10)`）。

### 电动减振器的设计与控制

文献综述详细阐述了电动减振器的设计与控制方法。它描述了将传统减振器内置的阀门（shimequipped damping valve）替换为电机控制的旋转阀的方案。研究指出，通过旋转阀来调节阻尼比，可以调节前后轮的行驶频率并提升车辆动力学（`[Guo et al., 2004](#ch43.xhtml#ref43_10)`）。

频率响应技术被列为调节电动减振器阻尼比的有效策略。通过频率响应技术，可以使用频率响应图（Bode graphs）和 PID 控制器根据所需的行驶频率调节阻尼比。此外，`[Gupta et al., 2006](#ch43.xhtml#ref43_11)` 提到使用红外传感器来测量输入负载或扰动。

### 分析与仿真

研究利用 Simulink 和 MATLAB 对电动减振器模型进行理论分析与仿真。系统采用二阶方程表示，并为深入研究构建了若干子系统（`[Hrovat et al., 1997](#ch43.xhtml#ref43_12)`）。

### 结果与结论

分析结果在文献综述中展示，验证了该方法的有效性，通过展示阻尼频率随阀旋转的变化。

### 特性与结论

可变输出电动减振器提供了类似豪华车的阻尼控制功能。本文结论认为，通过电机控制的阀门动态调节悬挂，可以显著降低振动并提升车辆舒适性和稳定性（`[Raman et al., 2017](#ch43.xhtml#ref43_14)`）。

参考文献列出了相关研究和论文，包括电磁减振器（`www.audi-technology`）、基于 IMCPID 的稳健 PID 控制器设计方法（`[Shams et al., 2007](#ch43.xhtml#ref43_2)`）以及用于质量改进的测试机（`www.popularmechanics.com`）。

总体而言，文献综述有效地介绍了主题，讨论了电动减振器的概念，展示了控制策略，并提供了该领域相关研究的见解。最后总结了可变输出电动减振器在车辆广泛应用中的潜在特性和益处。

## 阻尼控制

减振器的阻尼通过内置阀门（`Irmscher et al., 2015`）控制，阀门中的挡片（shims）位于阀顶和阀底，具有类似弹簧的刚性特性。挡片是减振器阻尼的主要原因。在本电动减振器中，挡片被电机控制的阀取代。

阀由两部分组成：固定部分和旋转部分（`[Lee et al., 2008](#ch43.xhtml#ref43_16)`；`[Thakur et al., 2021](#ch43.xhtml#ref43_6)`），旋转阀通过内轴与电机连接并受控，固定阀则与轴连接滑动于腔体内。当上阀旋转时，孔的直径会减小，如`[Figure 43.2](#ch43.xhtml#fig43_2)`所示，孔径变化会导致阻尼比变化。本文仅展示了阀的基本示意图，但良好的阀技术可以使阻尼更有效且更持久。在假设所需行驶频率并绘制频率响应图（bode plot）时，可先估计传递函数，再借助扰动 PID 控制器对阀进行控制（`[Milliken et al., 1995](#ch43.xhtml#ref43_17)`）（`[Figure 43.3](#ch43.xhtml#fig43_3)`）。

![Figure 43.2  Valve before rotation](images/fig43_2_B.jpg)

[Figure 43.2  Valve before rotation](#ch43.xhtml#R_fig43_2)

![Figure 43.3 Valve after rotation](images/fig43_3_B.jpg)

[Figure 43.3 Valve after rotation](#ch43.xhtml#R_fig43_3)

### 行驶控制

每辆车的悬挂设计决定其行驶频率，行驶频率在车辆稳定性中扮演重要角色，精确的行驶频率决定了驾乘舒适度（`[Tran et al., 2022](#ch43.xhtml#ref43_18)`）（`[Figure 43.4](#ch43.xhtml#fig43_4)`）。

![Figure 43.4 Ride frequency estimation](images/fig43_4_C.jpg)

[Figure 43.4 Ride frequency estimation](#ch43.xhtml#R_fig43_4)

通过调节阀的旋转，可控制前后轮的行驶频率。当前后轮之间的延迟减小时，阻尼也相应增加，这可以使车辆动态表现更佳（`[Figure 43.5](#ch43.xhtml#fig43_5)`）。

![Figure 43.5 Controller](images/fig43_5_C.jpg)

[Figure 43.5 Controller](#ch43.xhtml#R_fig43_5)

此外，在设计 PID 控制器时，考虑了车辆的各种动态，以确保在动态工况下性能平稳有效。

### 基础

Matlab 是主要的分析软件之一，可用于高精度理论分析。本文在此使用 Simulink 作为 Matlab 的基础，用于分析模型（Matlab 中的一个工具）。

(1)  

$$\text{m}\\ddot{y} + \\text{b}\\dot{y} + \\text{ky} = \\text{u}$$  

该系统为二阶系统，意味着包含两个积分器。

(2)  

$$x_{1}(t) = y(t)$$  

(3)  

$$x_{2}(t) = \\dot{y}(t)$$  

(4)  

$$\dot{x}_{1} = x_{2}$$  

(5)  

$$\dot{x}_{2} = \\frac{1}{\\text{m}}\\left(-\\text{ky} - \\text{b}\\dot{y}\\right) + \\frac{1}{\\text{μ}}\\text{ (typo in original, kept as is) }$$  

输出方程  

(6)  

$$y = x_{1}$$  

利用这些方程，MATLAB 模型被构建并分解为多个子系统以便进一步分析（`[Figure 43.6](#ch43.xhtml#fig43_6)`）。

![Figure 43.6 Circuit diagram](images/fig43_6_B.jpg)

[Figure 43.6 Circuit diagram](#ch43.xhtml#R_fig43_6)

