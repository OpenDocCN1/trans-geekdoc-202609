

# 利用机器学习的元策略

元策略在机器学习领域内，指向一种被称为元学习的实践。这一概念也称为“学会学习”，是机器学习的一个小众子集。元学习的威力在于其能够根据实验获得的结果，通过修改学习算法的特定方面来提升该算法的性能。

元学习真正的卓越之处在于其能够用数据驱动方式学习得出的方法论，来替代人工设计的算法。

因此，当应用于交易策略时，元学习呈现为元策略的形式。该框架的作用是利用机器学习不仅优化，而且根据不断变化的市场动态来调整交易策略。这转化为一种适应性强且灵活的算法交易方法，能够与市场同步演进。

实际上，元策略有潜力从我们现有的交易策略中榨取更大的价值。由元学习驱动的交易元策略，是一种基于策略表现和不断变化的市场条件来优化和演进交易算法的动态方法。

其核心在于，元学习是一个使模型能够从过去经验中学习的过程。这意味着它不仅分析输入数据，还分析自身的表现，并根据获得的洞察调整其算法。当应用于交易系统时，这一概念演变为元策略。

## 元策略实战

其工作原理如下：元策略不使用基于预定义规则运行的静态交易算法，而是使用一个学习算法。该学习算法评估交易策略在不同市场场景下的表现，了解其优势和劣势。然后根据这些习得的知识调整交易策略，使其更加稳健有效。

例如，一种交易策略可能在高波动时期表现良好，但在低波动时期却举步维艰。利用元学习的元策略会识别出这种模式并调整策略，或许通过在低波动时期减小仓位或改变进出场点位。

以这种方式，元策略可以持续优化交易系统，随着时间的推移并在各种市场条件下提升其性能。它们代表了算法交易的下一个层级，在那里交易系统不仅是自动化的，而且是自我改进和自适应的。

### 元交易策略

让我们通过一个具体例子来尝试编写一个旨在补充现有策略的元策略。为此，让我们采用通过检测超买和超卖股票来回归均值的策略。我们在上一节中描述了该原则。

结合元学习的策略思路：

1.  检查策略的盈亏是否可以作为策略输入数据的函数进行预测。
2.  如果可以，我们将在交易前预测盈亏的符号，仅发送有希望的交易（即预测盈亏为正的交易）。

为实现这一点，元策略仅需对初始策略进行微小修改。

元策略以描述我们试图增强的策略的数据作为输入。这些数据如下：

- 策略的表现（盈亏）

![](images/Figure_1.8.jpg)

被分析策略的输入数据。

以下是计算机代码所需的步骤：

1.  我们需要保留每个周期的盈亏记录（`ar_pnl` 数组）。

```
# agregated PnL for each specific period :
ar_pnl = pd.DataFrame(np.zeros(len(ranked_ret.index)) , index = ranked_ret.index , columns=["agg_pnl"] )
```

2.  我们用每个周期的盈亏填充此表。

```
# Calculate transaction cost
# transaction cost in basis point:
# transaction_cost_amount = (open_price + close_price) * quantity * transaction_cost
# transaction cost per share (broker fee : minimum 1$):
transaction_cost_amount = max(quantity * transaction_cost , 1)
profit_loss = (close_price - open_price) * quantity - transaction_cost_amount
# apply stop loss
profit_loss = np.max([profit_loss , stp_loss])
lst_pnl.append(profit_loss)
total_profit_loss = total_profit_loss + profit_loss
ar_pnl['agg_pnl'].loc[date] = ar_pnl['agg_pnl'].loc[date] + profit_loss
```

3.  接下来，我们获取策略的特征（`X`），即收益率和这些收益率的排名（根据收益率大小分配给每个资产的排名）。

```
# features : we merge the ranked returns and array of returns
X = pd.concat([ret , ranked_ret] , axis =1)
```

4.  目标是学会预测。这是一个二元目标（`y`），取决于产生的盈亏是否为正。

```
# target : agregated PnL for each specific period -> ar_pnl
y = np.sign(ar_pnl.shift(-1))
# binary sign is either 1 or -1 not 0
y[y == 0] = -1
# last period, zero to clean missing value
y.iloc[-1] = -1
y = np.ravel(y)
```

5.  学习阶段：

```
# Split the data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y , test_size =0.025,shuffle = False)
clf = RandomForestClassifier()
clf.fit(X_train , y_train)
```

以下是与预测盈亏符号相关的指标：

| | precision | recall | f1-score | support |
|---|---|---|---|---|
| -1.0 | 0.40 | 0.61 | 0.48 | 36 |
| 1.0 | 0.67 | 0.46 | 0.54 | 61 |
| accuracy | | | 0.52 | 97 |
| macro avg | 0.53 | 0.54 | 0.51 | 97 |
| weighted avg | 0.57 | 0.52 | 0.52 | 97 |

该算法为正类别（+1：正盈亏）找到了预测模式。正确预测与错误预测的比率等于 2/3 (0.67)，这高于平均水平，当然也高于随机预测。

剩下的就是接入由元规则形成的过滤器。

在每笔交易前，我们检查该交易是否有机会产生正利润。具体操作如下：将即将进行的交易信息发送给与训练好的算法关联的预测函数（`predict_proba`）。该函数返回该交易产生利润的概率。该概率充当交易过滤器（元规则），仅允许具有盈利潜力的交易通过。我们仅发送超过 50% 阈值（产生正利润的概率）的盈亏：

```
# open a trade if the ML model allows it ....
if clf.predict_proba(pd.DataFrame(X.loc[date].values.reshape(1,-1) , columns=X.columns))[0,1] > 0.5:
    print("ML OK for this trade")
    lst_pnl_meta_strat.append(profit_loss)
else:
    lst_pnl_meta_strat.append(0)
```

同时，我们记录未经过元规则过滤的策略盈亏（非元曲线）。我们在下图中得到了这两条权益曲线：

![](images/fig-1-9.png)

元规则生效了。经过过滤的策略回撤更低，利润更高。两条曲线的差异并不惊人，但再次强调，这里并未寻找最优参数或进行微调。

## 结论

