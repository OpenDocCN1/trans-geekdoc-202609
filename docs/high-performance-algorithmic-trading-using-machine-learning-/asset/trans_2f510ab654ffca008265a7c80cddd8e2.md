
• 正相关（图中较大的“O”）：在货币背景下，较高的债券收益率会增强本国货币，因为它吸引寻求更高回报的外国投资，影响 `EURUSD` (`EURUSD=X_Close`) 和 `JPY` (`JPY=X_Close`) 等货币对。

我们的目标是利用这些宏观经济变量预测两天前的收益率（`ahead = 2`），并制定能够利用这些预测的交易策略：

```
ahead = 2

df['target'] = df['Close'].shift(-ahead)
```

## 手工算法作为基准

在本节中，我们旨在进行一项基础且稳健的基准测试，以比较 AutoML 和低代码 API 所有结果。我们的目标不是探索复杂方法以取得卓越成果，而是建立一个可靠的比较基准。这将使我们能够评估每种方法（AutoML 和低代码）的性能，并根据它们的相对优势和劣势做出明智决策。

此次比较的一个关键原则是奥卡姆剃刀原则，即除非更复杂的方法展现出明显优势，否则应优先选择更简单的模型。如果复杂的 AutoML 或低代码解决方案无法超越快速的基准回归，则不予考虑，因为其增加的复杂性无法证明其使用的合理性。这确保了模型选择在性能指标和计算效率之间取得平衡，保持了算法交易实用且有效的方法。

### LASSO

最小绝对收缩和选择算子（LASSO）算法因其内在的正则化能力，是基准测试的绝佳选择。通过引入正则化，L[3](#chap08.xhtml#footnote-071)￼ 允许选择一份简洁的重要特征清单，这有利于在使用线性算法的回归分析初期取得可靠结果：

```
from sklearn.linear_model import LassoCV
```

`X` 包含宏观经济特征，`y` 包含我们旨在学习预测的目标值：

```
y = df.pop('target')

X = df.copy()

X_train , X_test , y_train , y_test = train_test_split(X , y , shuffle = True)

rgr = LassoCV()

rgr.fit(X_train , y_train)
```

结果如下：

```
from sklearn.metrics import mean_squared_error

print('RMSE = ',np.sqrt(mean_squared_error(pred , y_test)))

print(np.round(rgr.score(X_test , y_test),3))
```

```
RMSE = 0.54

0.397
```

正如预期的那样，结果尚可但不算出色。指标损失均方根误差（RMSE）表明，收益率预测误差的标准差约为 0.54，这意味着例如实际收益率为 2.0 时，预测值可能在 1.54 到 2.54 之间。

关于 R2 分数，其范围为 -1 到 +1，+1 表示完美预测，分数越高越好。我们的分数约为 0.4，虽然不算灾难性，但明显低于最佳可能结果。

下图展示了预测值与真实值的对比：

![](images/fig-8-3.png)

紧贴完美拟合对角线的预测值通常表示与真实值高度一致。然而，在本例中，未观察到这种理想的一致性。

下图证实了这一点：

![](images/fig-8-4.png)

预测值遵循真实值的总体趋势，表明模型已捕捉到数据中的潜在模式。在接下来的章节中，我们将看到自动化方法（AutoML 和低代码）是否能提高这些预测的精度，并做得比我们简要分析更好。

## AutoML 的核心组件

让我们探讨如何自动处理机器学习项目的复杂任务（特征工程与选择、算法选择、超参数优化和模型评估），所采用的方法、其计算需求，以及结果与我们手动方法的对比。

### 特征工程与选择

特征工程涉及从原始数据创建新输入变量以提高模型预测能力。相比之下，特征选择侧重于选择最相关的特征以提高效率并减少过拟合。这些过程对构建高性能模型至关重要，因为它们决定了输入算法的信息内容。

关于特征工程与选择技术的详细探讨，[第 6 章](#chap06.xhtml)“利用特征提升模型能力”专门讨论此主题。在此，我们将使用自动化工具来简化流程，并将其与传统手动方法进行比较。

我们可以使用专为自动化特征工程设计的库来简化相关特征的创建。

#### 使用 Feature-engine 进行特征工程

我们从 Feature-engine[4](#chap08.xhtml#footnote-070) 开始，这是一个拥有多种转换器的 Python 库，用于为机器学习模型设计特征和选择特征。

以下命令安装该库：

```
!pip install -q feature-engine
```

其余代码很简单，本质上涉及选择一组特征子集（`variables=[...]`）并对其应用特定变换（`func = [...]`）。这些变换旨在通过创建捕捉数据关系和模式的新特征来提高预测能力。`MathFeatures` 对选定变量应用数学运算（如求和、乘积、平均值），而 `RelativeFeatures` 和 `CyclicalFeatures` 有助于捕捉数据中的相对变化和季节性模式。

以下代码演示了如何应用这些变换：

```
from feature_engine.creation import MathFeatures , RelativeFeatures , CyclicalFeatures

mf = MathFeatures(variables=['Open_ret', 'High_ret', 'Low_ret', 'Close_ret'] , func = ["sum","prod","mean"])
```

定义转换器（`mf`）后，将其应用于包含初始化阶段提供的指定特征集（`['Open_ret','High_ret','Low_ret','Close_ret']`）的 DataFrame（`df`）：

```
df_feat = mf.fit_transform(df)
```

指定的变换列（最后三列，`df_feat.iloc[:,-3:]`）通过 `pd.concat()` 与其余特征合并：

```
df = pd.concat([df , df_feat.iloc[:,-3:]] , axis = 1)
```

随后，对一组新特征应用额外的变换[5](#chap08.xhtml#footnote-069)，从而自动创建了数千个工程特征，本例中恰好为 1332 个：

```
df.info()
```

```
<class 'pandas.core.frame.DataFrame'>
DatetimeIndex: 2668 entries, 2010-01-05 to 2022-03-01
Columns: 1332 entries, Open to High_ret_add_High_ret
```

在本节中，我们使用 Feature-engine 自动化特征工程，利用数学变换从现有特征创建新特征。这些变换扩展了我们的数据集，以捕捉更多可提高预测性能的复杂关系。通过应用这些方法，我们生成了大量工程特征，为更高级的模型开发奠定了基础。

接下来，我们将探索 autofeat，另一个专为自动化特征工程和选择设计的强大库。虽然 Feature-engine 侧重于结构化变换，但 autofeat 将特征选择与工程相结合，通过自动识别最相关变量来帮助优化数据集。

#### 使用 autofeat 进行特征工程与选择

我们现在使用 autofeat[6](#chap08.xhtml#footnote-068)，一个同样致力于自动化特征工程和选择的库。我们在以下代码中安装 autofeat 库并进行初始化：

```
!pip3 install -q autofeat
```

我们使用要执行的特征工程步骤数（`feateng_steps`）初始化 autofeat 模型：

```
auto_feat = AutoFeatRegressor(verbose=1, feateng_steps = 1)
```
