
我们从一副牌中取出九张黑桃和一张红心。我和我的朋友安迪坐下来。我们洗牌，然后我的朋友发给我一张牌。如果是红心，我就赢了！如果不是，安迪赢。这个设置给我们一个游戏，马克获胜的概率是10%，即1:9的赔率——加油，我！如果我们想要一个公平的结果，安迪和我应该愿意在这个简单的游戏上冒多少钱的风险？从长远来看，我们双方期望赢得相同金额的盈亏平衡点在哪里？注意，我们讨论的是多次玩这个游戏以减少随机变异的影响。如果我们只玩一轮，只有一个人会赢那一轮——可能是安迪！如果我们玩100次，我们预计会看到更接近安迪赢90-10的分布。不过没有保证。

为了找出盈亏平衡点，让我们从一些具体数字开始。这里有一个例子，我们双方都下注10美元。

马克收益 = (.1 × +10) + (.9 × −10) = 1 − 9 = −8  
安迪收益 = (.9 × +10) + (.1 × −10) = 9 − 1 = 8

为了计算收益，我们考虑了两种可能的结果——赢和输——并将(1)这两种结果的概率和(2)这两种结果的货币结果用——嗒哒！——点积组合起来。用数学方式写出来就是 ∑_outcome p_outcome v_outcome，其中 p 和 v 分别是每个结果的概率和美元价值。这个特殊的点积称为某人参与游戏时的期望收益。

注意，由于没有钱消失，这是一个真正的零和游戏，我们的总收益必须平衡到零。所以，如果我们双方冒相等的金额——每人10美元——我，马克，真的会亏钱。让我们再做一次合理性检查——这些数字有意义吗？记住，我赢的赔率只有1:9。遗憾的是，我获胜的机会并不大。为了平衡，我应该比安迪下注更少的钱，因为我赢的概率更低。下注的盈亏平衡点是多少？我们可以用代数来计算答案，但让我们用一些代码来做实验。我们将查看从1美元到11美元、步长为2美元的赌注对，并计算马克的收益。

我们将使用两个辅助函数：

In [19]:

```
def simple_argmax(arr):
    ' helper to convert np.argmax into something usable '
    return np.array(np.unravel_index(np.argmax(arr),
                     arr.shape))

def df_names(df, idxs):
    ' helper to convert number of index/column labels '
    r,c = idxs
    return df.index[r], df.columns[c]
```

然后，我们将为几种下注组合创建一个结果表格：

In [20]:
base_bets = np.arange(1,12,2)
mark_bet, andy_bet = np.meshgrid(base_bets, base_bets)

mark_winnings = .1 * andy_bet + .9 * -mark_bet

df = pd.DataFrame(mark_winnings,
                index =base_bets,
                columns=base_bets)
df.index.name = "Andy Bet"
df.columns.name = "Mark Bet"

print("Best Betting Scenario (for Mark) for These Values:")
print("(Andy, Mark):", df_names(df, simple_argmax(mark_winnings)))

display(df)

最佳下注情景（对马克而言）对于这些值：
(安迪, 马克): (11, 1)

| 马克下注 | 1 | 3 | 5 | 7 | 9 | 11 |
|---|---|---|---|---|---|---|
| 安迪下注 |  |  |  |  |  |  |
| 1 | -0.8000 | -2.6000 | -4.4000 | -6.2000 | -8.0000 | -9.8000 |
| 3 | -0.6000 | -2.4000 | -4.2000 | -6.0000 | -7.8000 | -9.6000 |
| 5 | -0.4000 | -2.2000 | -4.0000 | -5.8000 | -7.6000 | -9.4000 |
| 7 | -0.2000 | -2.0000 | -3.8000 | -5.6000 | -7.4000 | -9.2000 |
| 9 | 0.0000 | -1.8000 | -3.6000 | -5.4000 | -7.2000 | -9.0000 |
| 11 | 0.2000 | -1.6000 | -3.4000 | -5.2000 | -7.0000 | -8.8000 |

这很有意思。回想我们上面的讨论：如果我的整体期望收益为零，安迪的也是。对我来说最好的结果，毫不意外，是表格的左下角。它发生在我下注1美元而安迪下注11美元时。那是我最低的下注，也是安迪最高的下注。现在，如果安迪愿意玩一个我下注1美元、他下注99美元的游戏，情况对我来说就大不相同了。我赢的次数是10%，所以我的期望是 .1 × $99 + .9 × −$1 = 9。如果我们用这些赌注多次玩这个游戏，我就会开始占上风。老马克的前景看好。那盈亏平衡点呢？那就是我们双方的收益相同，$0.00。它靠近左下角：我下注1美元，安迪下注9美元。这和我获胜的赔率1:9一致。盈亏平衡点就是你的下注金额等于你获胜赔率的地方。安迪是9:1的热门：马克每下注1美元，他就下注9美元。我是1:9的冷门。安迪每下注9美元，我只下注1美元。

这是关于下注的最后一个要点。如果两个玩家获胜概率相等，那么每个概率都是0.5。这对应于1:1的赔率，我们写作 odds = 1。这些值是胜负之间的临界点。更高的值(.75，赔率3:1)使一个事件或赢家更有可能，而另一个则更不可能。

## 8.4.2 概率、赔率和对数赔率

希望你现在对赔率如何运作有了一些理解。早些时候，我提到我们关心对数赔率。我马上会解释原因。让我们开始创建一个表，列出一些概率值及其对应的赔率和对数赔率。对数赔率实际上就是：对赔率值应用数学对数：log(odds)。

In [21]:

```
tail_probs = [0.0, .001, .01, .05, .10, .25, 1.0/3.0]

lwr_probs = np.array(tail_probs)
upr_probs = 1-lwr_probs[::-1]
cent_prob = np.array([.5])

probs = np.concatenate([lwr_probs, cent_prob, upr_probs])

# much better than geterr/seterr/seterr
with np.errstate(divide='ignore'):
    odds     = probs / (1-probs)
    log_odds = np.log(odds)

index=["{:4.1f}%".format(p) for p in np.round(probs,3)*100]

polo_dict = co.OrderedDict([("Prob(E)",     probs),
                           ("Odds(E:not E)", odds),
                           ("Log-Odds",      log_odds)])
polo_df = pd.DataFrame(polo_dict, index=index)
polo_df.index.name="Pct(%)"
polo_df
```

Out[21]:

| 百分比(%) | 概率(E) | 赔率(E:非E) | 对数赔率 |
|---|---|---|---|
| 0.0% | 0.0000 | 0.0000 | -inf |
| 0.1% | 0.0010 | 0.0010 | -6.9068 |
| 1.0% | 0.0100 | 0.0101 | -4.5951 |
| 5.0% | 0.0500 | 0.0526 | -2.9444 |
| 10.0% | 0.1000 | 0.1111 | -2.1972 |
| 25.0% | 0.2500 | 0.3333 | -1.0986 |
| 33.3% | 0.3333 | 0.5000 | -0.6931 |
| 50.0% | 0.5000 | 1.0000 | 0.0000 |
| 66.7% | 0.6667 | 2.0000 | 0.6931 |
| 75.0% | 0.7500 | 3.0000 | 1.0986 |
| 90.0% | 0.9000 | 9.0000 | 2.1972 |
| 95.0% | 0.9500 | 19.0000 | 2.9444 |
| 99.0% | 0.9900 | 99.0000 | 4.5951 |
| 99.9% | 0.9990 | 999.0000 | 6.9068 |
| 100.0% | 1.0000 | inf | inf |

如果你喜欢图形化视图，让我们看看概率和赔率（以分数表示）之间的关系：

In [22]:

```
def helper(ax,x,y,x_name,y_name):
    ax.plot(x,y, 'r--o')
    ax.set_xlabel(x_name)
    ax.set_ylabel(y_name)

# note, we trim the values above 90% [index -5] b/c
# the scale of the plots gets too compressed
# (huh, log-scale takes care of that! funny ....)
fig, (ax0, ax1) = plt.subplots(1,2, figsize=(9,3))
helper(ax0, probs[:-5], odds[:-5], 'probability', 'odds')
helper(ax1, odds[:-5], probs[:-5], 'odds', 'probability')
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_292_0.png)

以及概率和对数赔率之间的关系：

In [23]:

```python
fig, (ax0, ax1) = plt.subplots(1,2, figsize=(9,3))
helper(ax0, probs, log_odds, 'probability', 'log-odds')
helper(ax1, log_odds, probs, 'log-odds', 'probability')
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_292_1.png)

如果你看表格的第一行和最后一行，你可以看到每个概率、赔率和对数赔率的极端值。最小和最大概率对应于不可能或必然的事件。当然，我们知道很少有这样的事情。（你现在可以冥想不可能性的不可能性，然后回到你快乐的地方。）

以下是值的范围：

In [24]:

```python
pd.DataFrame([polo_df.min(axis=0),
              polo_df.max(axis=0)], index=['min', 'max']).T
```
