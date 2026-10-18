

# 数据可视化图表类型

不同的圆代表特定区域的案例区域。如果发现大圆，则称为红色区域；中等圆为橙色区域；小圆代表绿色区域。散点图存在几种条件（最佳拟合线、插值、相关性）([Figure 12.11](#c12.xhtml#fig12-11))。

## d. 多维图表

多维图表将一个维度表示为点，两个维度表示为对象或图形，三个维度表示为 3D 对象或图形。一些示例如下：

![Figure 12.12 Death rate of Maharashtra in metro cities \[16\].](images/fig12-12.jpg)

[**Figure 12.12**](#c12.xhtml#rfig12-12) Death rate of Maharashtra in metro cities \[16\].

### 1) 饼图

饼图通过将圆隔离为比较扇区来帮助显示类别之间的大小和比例。每条弧长表示每个组的比例，而整个圆代表等于 100% 的数据总量 ([Figure 12.12](#c12.xhtml#fig12-12))。

算法：

1. 搜索所有模块的中间角度。
2. 绘制任意范围的圆。
3. 绘制水平范围。
4. 从水平范围开始，绘制与各模块对应值的中间角度的半径。
5. 对所有组件重复所有过程。
6. 这些半径将整个圆隔离为各个扇区。

### 2) 直方图

直方图是表示数据集可能性分布的图表。直方图有垂直条的类别，每个条代表一个单独值或变量的限制值。条的高度指示不同值或值范围的发生次数或机会。

类别如下：类别 1（正常症状）、类别 2（中度症状）、类别 3（严重病例）和类别 4（呼吸机）。

算法：

Step 1: 计算累积频率分布 [Figure (12.13)](#c12.xhtml#fig12-13)。

![Figure 12.13 Most case in March-April (Mumbai) \[16\].](images/fig12-13.jpg)

[**Figure 12.13**](#c12.xhtml#rfig12-13) Most case in March-April (Mumbai) \[16\].

Step 2: 与均衡直方图的 CuF 进行比较。

Step 3: 设计映射。

Step 4: 新直方图将显示 \[9\]。

### 3) 热图

热图是一种在温暖和冰冷区域中运用冷热系统来想象访客性能数据的方式。深色代表访客交互最大的区域，红色覆盖交互最大的区域，冷色指定访客交互最小的区域。

示例：进一步位置的天气预测 ([Figure 12.14](#c12.xhtml#fig12-14))。

算法：

计算每个容器值范围（下限和上限）有两个程序。

实现以下步骤以计算范围：

1. 通过将总进程案例数除以总容器数来计算容器大小。总容器数始终为九。
2. 分析每个容器值的范围（下限和上限）。

![Figure 12.14 Weather prediction \[16\].](images/fig12-14.jpg)

[**Figure 12.14**](#c12.xhtml#rfig12-14) Weather prediction \[16\].

第一个容器（索引为零的容器）的范围将大于零且小于 2。第二个容器（索引为一的容器）的范围将大于 2 且小于 4 ([Figure 12.15](#c12.xhtml#fig12-15))。

### 4) 树形图

树形图是分类数据的可视化。它们由大小与等效数据值成比例的嵌套矩形序列组成。树的一个分支是大矩形，它被分割为较小的矩形，表示该分支中每个节点的维度 \[7, 8\]。

算法：

1. 取矩形 R，选择枢轴 P 和具有特定区域的有序列表。
2. 将 R 分为四个矩形。
3. 将列表分为三个段，以放置在 r1、r2 和 r3 中。
4. 如果项目数小于或等于 4，则将它们放置在枢轴上。
5. 选择合适的枢轴：

    1. 按大小选择枢轴。
    2. 按中间值选择枢轴。
    3. 按分割大小选择枢轴。

6. L1 包含索引小于 P 的项目，L2 包含索引小于 L3 中项目的项目，且 RP 的特征分数尽可能接近 1。
7. 选择特征分数接近 1 的最佳设计。

![Figure 12.15 Major cases in three states of India \[16\].](images/fig12-15.jpg)

[**Figure 12.15**](#c12.xhtml#rfig12-15) Major cases in three states of India \[16\].

### 5) 蜘蛛图

蜘蛛图是一种图形方法，用于在三个或多个可测量变量表示在从相同点开放的轴上的 2D 图表中演示一个或多个变量数据。它也被称为网状图和雷达图 [Figure (12.16)](#c12.xhtml#fig12-16)。

算法：

1. 沿每个轴绘制一个点，然后使用不同形状的形式将它们连接起来。
2. 搜索哪个类别轴代表。
3. 检查围绕圆阅读时类别如何相互关联。
4. 零是每个轴圆的中心。

## a. 树/网络图

树图是设想树状图层次结构的不同方式，同时通过区域大小显示每个组的度量。树图总结每个数据，使用户能够快速连接信息。

## b. 树状图

树状图是显示对象之间层次连接的图表。树状图的目的是找出将项目分配到组的最佳方式。树状图由一组分解为较小分支的分支组成。

![Figure 12.16 Covid cases in Mumbai and Pune (March-July) \[9\]. We can say that two region of Maharashtra Mumbai and Pune patients count from April to June 2020. We can also see that how rapidly patients is increased \[16\].](images/fig12-16.jpg)

[**Figure 12.16**](#c12.xhtml#rfig12-16) Covid cases in Mumbai and Pune (March-July) \[9\]. We can say that two region of Maharashtra Mumbai and Pune patients count from April to June 2020. We can also see that how rapidly patients is increased \[16\].

算法：

1. 我们将所有点分配到特定组（簇）。例如，不同大小的点将显示不同的组（簇）。
2. 我们搜索邻接矩阵中最小的距离，并将距离最小的点连接起来，然后更改邻接矩阵。
3. 我们将重复该过程，直到只剩下一个单一簇。

## d. 双曲树图

双曲树是一种强调框架可视化技术：它在小区域提供全面视图，同时仍然提供整个结构的概述。这是通过首先以统一的方式将层次结构作为非欧几里得双曲平面上的树进行布局来实现的。

将根节点视为第一个公共传播国家，最后节点代表世界上最后一名感染患者。在 [Figure 12.17](#c12.xhtml#fig12-17) 中，我们可以看到蓝色三角形作为根节点，其他节点作为最后的叶节点。

算法：

Step-1: 将 S 分配为包含数据集的树的根节点。

Step-2: 使用属性选择度量 (ASM) 在数据集中搜索最佳特征。

Step-3: 将 S 分配为包含最佳特征可能值的子组。

Step-4: 生成包含最佳特征的决策树节点。

Step-5: 定期使用 Step-3 形成的信息子组生成新的决策树。保持此过程，直到触及无法进一步建立节点的阶段，称为叶节点。

我们已经了解了不同的大数据可视化技术。今天，有不同的数据可视化工具供公司用于制作数据演示。

1. Fusion Charts Suite XT
2. QlikView
3. Tiblo Specific
4. Watson Analytics
5. Sisense
6. Tableau

