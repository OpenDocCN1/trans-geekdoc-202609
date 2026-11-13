
第 2 步：导航到 PCA 选项以查看此分析的结果。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_222_0.png)

第 3 步：可视化此 PCA 分析的结果。如您所见，前两个主成分解释了该数据集中约 50% 的信息。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_222_1.png)

第 4 步：选择“下载可操作模型”将此模型下载至您选择的编程语言。此处，我们使用 Python。

Python 代码：

```
# Requires BigML Python bindings
# Install via: pip install bigml
# or clone it:
# git clone https://github.com/bigmlcom/python.git

from bigml.pca import PCA
from bigml.api import BigML

# Downloads and generates a local version of the PCA,
# if it hasn't been downloaded previously.

pca = PCA('pca/62c6e79e8f679a6f64001537',
    api=BigML("mznaser",
        "33dcd88020b98f21a24f68ce3b9c943e6ab4e4b6",
        domain="bigml.io"))

# To project the PCA fill the desired input_data in the line below.
# Only the ID of the fields to project with are required.
input_data = {
    "maximum exposure temperature": 1,
    "silica fume/binder ratio": 1,
    "moisture content": 1,
    "characteristic distance": 1,
    "sand/binder ratio": 1,
    "heating rate": 1,
    "Water/binder ratio": 1,
    "aggregate/binder ratio": 1,
    "aggregate size": 1,
    "GGBES/binder ratio": 1,
    "s fiber diameter(mm)": 1,
    "pp fiber length (mm)": 1,
    "s fiber quantity (kg/m3)": 1,
    "PP fiber quantity (kg/m3)": 1,
    "pp fiber diameter(um)": 1,
    "FA/binder ratio": 1,
    "s fiber length (mm)": 1
}

pca.projection(input_data)
```

至此，我们使用 BigML 平台的示例结束。

## 6.1.2 DataRobot

根据 DataRobot，24

> "DataRobot 成立于 2012 年，旨在普及 AI 的使用。当前，DataRobot 是 AI 领域的云端领导者，其愿景是为所有用户、所有数据类型和所有环境提供统一平台，加速各组织将 AI 投入生产。"

DataRobot 是一家总部位于波士顿的数据科学公司，使用户能够在无需具备 ML（或编程）知识的情况下构建预测分析。此云端/在线平台25 利用自动化 ML 在短时间内构建并部署准确的预测模型。DataRobot 为包括土木与环境工程在内的各行各业提供独特且个性化的解决方案。该平台独特之处在于其包含属于不同编程语言的大量算法（即，不限于特定编程语言）。DataRobot 还集成了可解释 ML、可部署 ML、公平26 ML 和可信 ML 等，以及其他功能27（参见图 6.2）。最后，该平台不仅限于表格数据，还为用户提供使用计算机视觉工具的权限。DataRobot 设有内部学术支持计划，教职员工和学生可免费访问和使用其在线平台。他们还提供简短课程，向新用户介绍其平台。28 其 YouTube 频道也非常活跃，并不断更新有关 ML 以及 DataRobot 家族新成员的内容。

我将使用 DataRobot 展示三个不同的示例。

### 示例 1 [DataRobot，分类]：预测火灾引起的混凝土剥落。

所使用的数据集包含由叶海龙教授团队收集的 646 个测试样本[2-6]。该数据集包含 16 个特征和一个目标，通过两个标签（无剥落或剥落）描述剥落的发生情况。16 个自变量为：水胶比（%）、骨料胶比（%）、砂胶比（%）、升温率（°C/min）、含水率（%）、最大暴露温度（°C）、硅灰胶比（%）、骨料尺寸（mm）、GGBS 胶比（%）、FA 胶比（%）、PP 纤维用量（kg/m³）、PP 纤维直径（um）、PP 纤维长度（mm）、钢纤维用量（kg/m³）、钢纤维直径（mm）、钢纤维长度（mm）。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_224_0.png)

图 6.2 DataRobot 平台截图（2022 年 7 月）。

25 基于云的平台意味着用户只需访问在线平台即可使用它（即，无需下载专用软件或购买硬件等）。

26 这是 DataRobot 最酷的功能之一——您可以在“高级选项”选项卡下的“偏差与公平”中找到它——在此功能中，模型旨在减轻其决策过程中的偏差和歧视。

27 例如可编辑的 ML 模型（可组合 ML）。

28 我非常喜欢这门特定的课程。此外，感谢 Katherine Kopp、Matt Charoenrath 和 William Disch 慷慨借给我他们的平台。

以下是执行此分类分析的步骤。我们将使用 XGBoost 算法。

### 第 1 步：上传数据集并将 Output 设为目标。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_225_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_225_1.png)

### 第 2 步：您会注意到 DataRobot 将此分析更改为分类。导航到 Show advanced options，然后进入 Additional，勾选 Search for interaction 并取消勾选 Create blenders from top models。请注意，0 = 无剥落，1 = 剥落。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_226_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_226_1.png)

### 第 3 步：进入建模模式并选择手动。启动分析。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_227_0.png)

### 第 4 步：要直观查看每个特征的分布。进入 Data 选项卡并选择一个特征（此处显示输出特征）。将弹出直方图。有关此特征的其他统计信息（如均值、标准差、中位数等）也会显示在一侧。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_227_1.png)

### 第 5 步：让我们来看一些关于数据的信息。在 Data 选项卡下导航到特征关联。您可以在右侧面板中看到前 10 强关联。您还可以在关联矩阵中选择任何圆点，以查看两个特征之间的关联程度。如您所见，DataRobot 根据关联强度将特征聚类为彩色分组。29

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_228_0.png)

### 第 6 步：进入 Repository 选项卡并选择 eXtreme Gradient Boosted Trees Classifier (BP40)。添加模型。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_228_1.png)

### 第 7 步：导航到 Leaderboard 选项卡。查看分析结果。下图显示了按 AUC 指标衡量的模型性能。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_229_0.png)

### 第 8 步：进入 Evaluate 选项卡，然后选择 ROC 曲线以显示 ROC 曲线和混淆矩阵。将数据选择更改为 Validation。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_229_1.png)

还记得在算法章节的某个脚注中，我提到过每个算法都有一组我们可以控制和微调的设置和参数吗？没错，DataRobot 使此调谐过程变得简单。要访问这些设置，请在 Evaluate 选项卡下导航到 Advanced Tuning。让我们将 learning_rate 更新为 0.02，将 tree_method 更新为 exact。然后，选择 Begin Tuning。比较默认模型和调谐后模型的结果。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_230_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_230_1.png)

30 每一步的收缩以最小化过拟合。

31 使用精确贪婪算法。

### 示例 1 [DataRobot，补充多类分类]：预测桥梁损坏。

在此补充示例中，我们将考察一个包含 135 座经历过一定程度火灾损坏（轻微、重大和倒塌）的国际桥梁的数据集。每起事件均按八个不同特征进行记录，即用于承重的结构体系 S 和建筑材料 M、桥梁跨度 L 和年龄 A、地理意义 G 以及车道数 N、火灾涉及的燃料类型 T 以及火灾发生地点的接近程度 C。如您所见，输入包含数值数据和类别数据。32

让我们使用 DataRobot 平台执行分析并上传数据集。将 Damage 选为目标。我们不会针对特定算法；相反，我们将使用 DataRobot 的 Autopilot33 模式。

### 第 1 步：导航到“启动”和“建模模式：Autopilot”。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_231_0.png)

### 第 2 步：查看特征的直方图（目标如下所示）。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_231_1.png)

32 我们无需操作输入。DataRobot 会自动完成此操作。

33 在此模式下，DataRobot 以竞争方式考察一系列算法，以得出并推荐性能最佳的模型。
