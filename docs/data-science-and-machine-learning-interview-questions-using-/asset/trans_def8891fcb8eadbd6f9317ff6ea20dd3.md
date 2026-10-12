
上述过程重复进行，直到达到所需的准确性，或无法再进行改进。

以下是 Ada Boosting 的代码：

```python
from sklearn.ensemble import AdaBoostClassifier

booster = AdaBoostClassifier()
n_estimators = 50  # 默认值
base_estimator = DecisionTreeClassifier  # 默认值
booster.fit(x_train, y_train)
booster.predict(x_test)
```

### Q20: 解释梯度提升？

**答：** 梯度提升利用训练好的序列模型。它使用梯度下降函数，该函数计算给定函数的局部最小值。因此，我们试图为损失函数找到局部最小值函数。

该过程是构建新的学习器，也称为基学习器，它们可以与损失函数的负梯度下降相关联：

```python
from sklearn.ensemble import GradientBoostingClassifier  # 用于分类
# from sklearn.ensemble import GradientBoostingRegressor  # 用于回归

classifier = GradientBoostingClassifier(n_estimators, learning_rate, max_depth)
classifier.fit(X_train, y_train)
```

*   **`n_estimators`：** 表示弱学习器的数量
*   **`learning_rate`：** 决定弱学习器在最终组合中的贡献
*   **`max_depth`：** 单个回归估计器的最大深度。这限制了树中的节点数量。

### Q21: 解释 XGBoost？

**答：** **XGBoost**，也称为极端梯度提升，是一组用于开发快速且高性能梯度提升树模型的算法/库。

它利用梯度提升框架。

部分特性包括：

*   自动处理缺失数据值。
*   可并行化树的构建。
*   利用损失函数的二阶偏导数。这是与其他梯度算法的主要区别。其他算法使用一阶导数的损失函数，而 XGB 使用二阶导数，这也给出了梯度的方向。
*   使用先进的正则化技术。

示例片段：

```python
import pandas as pd
from xgboost import XGBClassifier
from sklearn.metrics import accuracy_score

model = XGBClassifier()
model.fit(x, y)
predict_train = model.predict(test_x)
accuracy_train = accuracy_score(train_y, predict_train)
```

### Q22: 解释 Bagging 和 Boosting 的区别/相似之处？

**答：** **相似之处：**

*   两者都属于称为集成学习的算法方法，即从 N 个分类器中生成/获得 1 个学习器。
*   两者都通过将原始数据集划分为较小的单元来工作。
*   都考虑输出的平均值。
*   两者都试图提高性能。

下表显示了区别：

![Bagging 和 Boosting 的区别](OEBPS/images/p119.jpg)

### Q23: 编写一个使用 TensorFlow 和 Keras 进行神经网络操作的小片段？

**答：**

![使用 TensorFlow 和 Keras 的神经网络代码片段](OEBPS/images/146.jpg)

# 第 6 章

# 值得记忆的 Matplotlib 示例

***注意：** [Q: 问题编号 和 Ans: 答案]*

### Q1: 解释如何绘制条形图。

**答：**

![条形图示例 1](OEBPS/images/149.jpg) ![条形图示例 2](OEBPS/images/150.jpg)

### Q2: 如何绘制直方图？

**答：**

![直方图示例 1](OEBPS/images/151.jpg) ![直方图示例 2](OEBPS/images/152.jpg)

### Q3: 如何绘制折线图？

**答：**

```python
import numpy as np
from matplotlib import pyplot as plt
from matplotlib.backends.backend_pdf import PdfPages
```

![折线图示例 1](OEBPS/images/153.jpg) ![折线图示例 2](OEBPS/images/154.jpg)

### Q4: 绘制饼图。

**答：**

![饼图示例 1](OEBPS/images/155.jpg) ![饼图示例 2](OEBPS/images/156.jpg)

### Q5: 如何在折线图上打印直线方程？

**答：** 使用以下代码片段即可实现：

```python
plt.title('$y= slope * x + intercept')
```

![直线方程示例](OEBPS/images/157.jpg)

### Q6: 绘制散点图。

**答：**

![散点图示例 1](OEBPS/images/158.jpg) ![散点图示例 2](OEBPS/images/159.jpg)

# 第 7 章

# Excel 表格统计

***注意：** [Q: 问题编号 和 Ans: 答案]*

### Q1: Excel 是否支持统计功能？

**答：** 是的，Excel 表格通过一些加载项（如 `Analysis Tool pack`）提供了大量的统计支持。要启用此分析工具库，请选择 Excel 选项，然后转到加载项选项并启用 `AnalysisToolPak`。

![启用 Analysis ToolPak](OEBPS/images/160.jpg)

完成后，数据分析选项在 Excel 的“数据”选项卡中启用，可以在 **数据** 选项卡下看到，如下图所示：

![数据分析选项卡](OEBPS/images/161.jpg)

### Q2: 使用 Excel 计算相关性。

**答：** 可以借助 Analysis Toolpak 的 `CORREL` 函数轻松找到相关性。

选择 **数据分析** → 选择 **相关性** 作为选项。

![选择相关性](OEBPS/images/162.jpg)

从数据分析中选择 **相关性** 后，选择相应的输入字段，并通过设置 **输出选项** 下的 **输出区域** 将输出值设置为在 Excel 表格上显示：

![相关性输出选项](OEBPS/images/163.jpg)

点击 **确定** 后，协方差的结果可以在 Excel 表格上找到。

### Q3: 如何在 Excel 中获取直方图？

**答：** 在 Excel 中获取直方图通常需要数值和对应的分箱。分箱代表计算频率的范围。

从 **数据分析** → 选择 **直方图** 功能 → 我们可以选择输入范围和分箱范围：

![直方图对话框 1](OEBPS/images/164.jpg) ![直方图对话框 2](OEBPS/images/165.jpg) ![直方图对话框 3](OEBPS/images/166.jpg)

### Q4: 解释如何使用 Excel 获取描述性统计。

**答：** 要获取 **描述性统计**，请选择 **数据分析** ⇒ 选择 **描述性统计** ⇒ 然后选择您需要的不同统计项。

![描述性统计 1](OEBPS/images/167.jpg) ![描述性统计 2](OEBPS/images/168.jpg) ![描述性统计 3](OEBPS/images/169.jpg)

### Q5: 解释如何在 Excel 中执行方差分析 (Anova)？

**答：** 要执行 **Anova**，请选择 **数据分析** ⇒ **Anova: 单因素**

![Anova 选择](OEBPS/images/170.jpg)

选择相应的输入和输出值：

![Anova 输入 1](OEBPS/images/171.jpg) ![Anova 输入 2](OEBPS/images/172.jpg)

根据 F 值和 F 临界值，我们可以得出是拒绝还是接受原假设。

### Q6: 解释如何在 Excel 中执行秩和百分位数。

**答：** 从 **数据分析** → 选择 **秩和百分位数**：

![秩和百分位数选择](OEBPS/images/173.jpg)

选择输入和输出范围以获取答案：

![秩和百分位数结果](OEBPS/images/174.jpg)
