
当用户从 `combo1` 中选择一个项目时，将触发 `choose_combobox1()` 函数。该函数将负责处理用户的选择，并根据所选项目执行相关操作或显示相关信息。

以这种方式将事件绑定到控件是 GUI 应用程序中的常见做法，旨在使界面具有响应性和交互性。在该特定案例中，这表明代码旨在动态响应用户从下拉框中的选择，从而增强用户体验，并允许与应用程序进行更多样化的交互。

然后，在 `Main_Class` 中定义一个名为 `choose_combobox1()` 的新方法：

```python
def choose_combobox1(self, event):
    chosen = self.obj_window.combo1.get()
    self.obj_plot.choose_category(self.df_dummy, chosen,
                                  self.obj_window.figure1, self.obj_window.canvas1,
                                  self.obj_window.figure2, self.obj_window.canvas2)
```

此代码定义了 `choose_combobox1()` 函数，当在 `combo1` tkinter `Combobox` 控件中选择项目时将触发该函数。

以下是该函数功能的细分说明：

1.  `chosen = self.obj_window.combo1.get()`：它从 `combo1` `Combobox` 中检索当前选定的项目，并将其存储在 `chosen` 变量中。

2.  `self.obj_plot.choose_category(self.df_dummy, chosen, self.obj_window.figure1, self.obj_window.canvas1, self.obj_window.figure2, self.obj_window.canvas2)`：它调用 `self.obj_plot` 对象（`Helper_Plot` 类的实例）的 `choose_category` 方法，并向其传递多个参数：

    *   `self.df_dummy`：包含分类数据的 DataFrame。

    *   `chosen`：从 `combo1` 中选定的项目。

    *   `self.obj_window.figure1` 和 `self.obj_window.canvas1`：应用程序第一绘图区域的 Figure 和 Canvas 对象。

    *   `self.obj_window.figure2` 和 `self.obj_window.canvas2`：应用程序第二绘图区域的 Figure 和 Canvas 对象。

此函数的目的是响应用户从 `combo1` 中的选择，并根据所选项目触发相应的绘图或可视化操作。`Helper_Plot` 类中的 `choose_category()` 方法将根据所选类别确定生成哪种特定可视化。这种方法使应用程序具有交互性，允许用户根据其选择探索不同的可视化。

然后，在 `Helper_Plot` 类中定义一个名为 `choose_category()` 的新方法：

```python
def choose_category(self, df, chosen, figure1, canvas1, figure2, canvas2):
    if chosen == "Categorized Income versus Response":
        self.dist_one_vs_another_plot(df, "Income", "Response", figure1, canvas1, chosen)
```

此函数接收多个参数，包括一个 DataFrame（`df`）、一个字符串 `chosen` 以及四个与绘图相关的对象（`figure1`、`canvas1`、`figure2`、`canvas2`）。其目的是根据用户从 `chosen` 变量中选择的内容，启用不同可视化的选择。

![Image](img/image22.png)

**图 20** 分类收入与响应的分布

在该特定代码块中，有一个单一的条件分支，检查 `chosen` 的值是否等于 "Categorized Income versus Response"。如果满足此条件，它将调用 `dist_one_vs_another_plot()` 函数以创建特定类型的图表。该可视化的目的是比较客户的分类收入水平（"Income"）与其响应行为（"Response"）。这种比较有助于分析不同收入类别与客户响应的关联，这对于理解客户行为并相应地定制营销策略或产品供给至关重要。结果如图 20 所示。

### 分类总购买量与分类收入的分布

将此代码添加到 `Helper_Plot` 类中 `choose_category()` 方法的末尾：

```python
if chosen == "Categorized Total Purchase versus Categorized Income":
    self.dist_one_vs_another_plot(df, "Num_TotalPurchases", "Income", figure2, canvas2, chosen)
```

此代码旨在在应用程序中启用交互式数据探索功能。当用户选择此特定选项时，代码将生成一种特定类型的图表，以可视化方式展示分类总购买量与分类收入之间的关系。这有助于用户深入了解数据集中这两个变量的相关性，从而支持数据驱动的决策和探索。结果如图 21 所示。

![Image](img/image23.png)

**图 21** 分类总购买量与分类收入的分布

### 分类最近购买间隔与分类总购买量的分布

将此代码添加到 `Helper_Plot` 类中 `choose_category()` 方法的末尾：

```python
if chosen == "Categorized Recency versus Categorized Total Purchase":
    self.dist_one_vs_another_plot(df, "Recency", "Num_TotalPurchases", figure1, canvas1, chosen)
```

此代码的目的是在用户从用户界面元素（下拉框或组合框）中选择 "Categorized Recency versus Categorized Total Purchase" 时创建特定的数据可视化。该可视化涉及比较两个分类变量："Categorized Recency"（分类最近购买间隔）和 "Categorized Total Purchase"（分类总购买量）。

生成的图表使观察者能够了解总购买量分布如何随不同的最近购买间隔类别而变化。例如，它有助于回答以下问题：

*   在过去 10 天内购买的客户是否更有可能落入特定的总购买量类别？
*   最近购买间隔如何影响总购买量的分布？

通过以可视化方式呈现这些信息，图表使识别数据中的趋势和模式变得更加容易，并能得出与这两个分类变量交互相关的洞察。结果如图 22 所示。

![Image](img/image24.png)

**图 22** 分类最近购买间隔与分类总购买量的分布

### 分类客户月份与分类客户年龄的分布

将此代码添加到 `Helper_Plot` 类中 `choose_category()` 方法的末尾：

```python
if chosen == "Categorized Customer Month versus Categorized Customer Age":
    self.dist_one_vs_another_plot(df, "Dt_Customer_Month", "Customer_Age", figure2, canvas2, chosen)
```

![Image](img/image25.png)

**图 23** 分类客户月份与分类客户年龄的分布

### 代码可视化目的与分析

#### 客户月份与年龄分布的可视化

代码旨在创建一个可视化图表，展示两个分类变量之间的关系：**"Categorized Customer Month"**（分类客户月份）和 **"Categorized Customer Age"**（分类客户年龄）。该可视化呈现为堆叠条形图，具体解读如下：

*   **X 轴（Categorized Customer Month）**：代表 "Customer Month" 的不同类别或区间。这些类别表示客户加入或使用服务/产品的不同月份或月份组。

*   **Y 轴（Count of Cases）**：代表每个 "Categorized Customer Month" 和 "Categorized Customer Age" 组合内的案例数或观测值。图中的每个堆叠条形代表这两个分类变量特定组合的案例数。

*   **堆叠条形**：X 轴上每个 "Categorized Customer Month" 类别均显示为一个堆叠条形。每个条形内部分为多个段，每段对应一个特定的 "Categorized Customer Age" 类别。每段的高度代表落入该特定月份与年龄组组合的案例数。

此类可视化有助于理解客户年龄分布在客户加入或使用产品/服务的不同月份/时期中的变化情况。它允许观察者探究特定月份是否吸引特定年龄组的客户，以及数据中是否存在与这两个分类变量相关的模式或趋势。

#### 分类购买黄金产品数量与分类收入的分布

##### 代码实现

在 `Helper_Plot` 类的 `choose_category()` 方法末尾添加以下代码：

```python
if chosen == "Categorized Amount of Gold Products versus Categorized Income":
    self.dist_one_vs_another_plot(df, "MntGoldProds", "Income", figure1, canvas1, chosen)
```

![Image](img/image26.png)

**Figure 24** The distribution of categorized amount of gold Products purchased versus categorized income

##### 可视化分析

该代码段用于生成堆叠条形图，以直观描绘两个不同变量间的关联：**"Categorized Amount of Gold Products"**（分类黄金产品购买量）和 **"Categorized Income"**（分类收入）。该可视化旨在提供关于客户收入水平与其在黄金产品上支出关系的洞察。

*   **X 轴**：代表黄金产品支出金额的各类别或区间，涵盖 "0-30"、"30-50"、"50-80" 等范围。

*   **Y 轴**：量化每个 "Categorized Amount of Gold Products" 与 "Categorized Income" 组合中的案例数或观测值。

*   **堆叠条形**：每个条形对应一个特定的 "Categorized Amount of Gold Products" 类别，展示该精确组合的案例数。条形由多个段组成，每段代表一个不同的 "Categorized Income" 类别。段的高度反映属于该特定黄金产品支出与收入类别组合的案例数。

*   **图例与标题**：图表预期包含图例，以阐释各 "Categorized Income" 类别的颜色编码；标题为 "Categorized Amount of Gold Products versus Categorized Income"，简明传达图表重点。结果见图 24。

此类可视表现作为强大的探索性工具，支持检验数据中的潜在趋势或模式。它允许调查高收入人群是否比低收入人群在黄金产品上支出更多，并有助于识别不同收入群体在黄金产品支出行为上的差异。通过该可视化，可获得关于消费者偏好和行为的宝贵洞察，为市场营销或业务策略的数据驱动决策提供支持。

#### 分类购买鱼类产品数量与分类总消费额的分布

##### 代码实现

在 `Helper_Plot` 类的 `choose_category()` 方法末尾添加以下代码：

```python
if chosen == "Categorized Amount of Fish Products versus Categorized Total AmountSpent":
    self.dist_one_vs_another_plot(df, "MntFishProducts", "TotalAmount_Spent", figure2, canvas2, chosen)
```

##### 可视化分析

该代码负责生成直方图形式的可视化表示，对比两个不同变量：**"Categorized Amount of Fish Products"**（分类鱼类产品购买量）和 **"Categorized Total Amount Spent"**（分类总消费额）。该可视化旨在提供关于客户行为两个方面关系的洞察。

*   **X 轴**：划分代表鱼类产品支出金额的不同类别或区间，如 "0-10"、"10-20"、"20-40" 等。

*   **Y 轴**：量化落入每个 "Categorized Amount of Fish Products" 与 "Categorized Total Amount Spent" 组合内的案例数或观测值。

*   **条形**：每个条形对应一个特定的 "Categorized Amount of Fish Products" 类别，代表属于该两个分类变量特定组合的案例数。每个条形的高度反映该特定组合内的案例数。

该可视化旨在清晰简洁地概述鱼类产品支出与客户总消费额的关系。

![Image](img/image27.png)

**Figure 25** distribution of categorized amount of fish products purchased versus categorized total amount spent

直方图是可视化变量分布及关系的宝贵工具。在该特定情境下，该可视化支持快速评估：在鱼类产品上支出更多的客户是否倾向于拥有更高的总支出，或是否存在明显的支出行为模式。它还允许识别特定支出类别组合内的案例集中情况。通过创建此直方图，可深入了解客户偏好和消费习惯，这对营销策略和业务决策极具价值。

#### 分类购买肉类产品数量与分类近期度的分布

##### 代码实现

在 `Helper_Plot` 类的 `choose_category()` 方法末尾添加以下代码：

```python
if chosen == "Categorized Amount of Meat Products versus Categorized Recency":
    self.dist_one_vs_another_plot(df, "MntMeatProducts", "Recency", figure1, canvas1, chosen)
```

##### 可视化分析

该代码负责生成直方图形式的可视化表示，对比两个不同变量：**"Categorized Amount of Meat Products"**（分类肉类产品购买量）和 **"Categorized Recency"**（分类近期度）。该可视化旨在提供关于客户行为这两个方面关系的洞察。

*   **X 轴**：由代表肉类产品支出金额的不同类别或区间组成，如 "0-50"、"50-100"、"100-200" 等。

*   **Y 轴**：量化落入每个 "Categorized Amount of Meat Products" 与 "Categorized Recency" 组合内的案例数或观测值。

*   **条形**：每个条形对应一个特定的 "Categorized Amount of Meat Products" 类别，代表属于该两个分类变量特定组合的案例数。每个条形的高度反映该特定组合内的案例数。

该可视化旨在清晰简洁地概述肉类产品支出与客户互动近期度的关系。

##### 直方图

直方图是可视化变量分布及其相互关系的宝贵工具。在该特定场景下，此可视化能够快速评估：在肉类产品上花费更多的客户是否往往拥有更近期的互动，或者在支出行为与近期度方面是否存在明显模式。它还允许识别在特定支出类别与近期度区间组合内是否存在案例集中。通过创建该直方图，可以深入了解客户相对于其互动近期度的偏好和消费习惯，这对营销策略和商业决策极具价值。

![Image](img/image28.png)

**图 26** 分类肉类产品购买金额与分类近期度的分布

### 绘制相关性矩阵

在 `Helper_Plot` 类中添加一个名为 `plot_corr_mat()` 的新方法：
