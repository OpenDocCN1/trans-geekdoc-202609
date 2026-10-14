

# 基于机器学习的策略在 BackTrader 中的实现

基于机器学习的策略编码方法不同于传统方法（如 `Moving Average Crossover` 移动平均线交叉）。我们不再编码具体的交易规则，而是获得一个预测向量，范围从简单的买入或卖出信号到更复杂的方案，这些都必须在 BackTrader 模拟环境中被解读并转化为可执行的订单。这种转变强调了算法的预测输出作为交易决策背后的驱动力。

与这一点相关的要素（从预测到订单）属于我们在本节开头给出的分步指南中的第 2 阶段（定义策略）。稍后我们将详细介绍这一点并编写相应的代码。

## 导入库并设置

让我们从导入和安装必要库的第一步开始。首先是 BackTrader：

```bash
pip install -q backtrader[plotting]
```

```python
import numpy as np
import pandas as pd
import yfinance as yf
import matplotlib.pyplot as plt
```

我们使用宝洁公司（PG）连续十天的日线数据初始化数据源（`df`）。为了演示基于机器学习的交易策略回测，我们使用随机数生成器（`np.random.choice`）模拟预测。虽然这些虚拟预测用于演示回测流程，但它们可以被机器学习模型的预测所替代：

```python
symbol = 'PG'
ticker = yf.Ticker(symbol)
df = ticker.history(period='10d', interval='1d')

# 模拟预测，倾向于 70% 的概率为 '1'（'买入'）和 30% 的概率为 '-1'（'卖出'）
pred_dumb = np.random.choice([-1, 1], size=df.shape[0], p=[0.3, 0.7])

# 在数据框中插入新列以跟踪预测
df['custom'] = pred_dumb
```

此时，我们拥有了价格以及与之对应的买入/卖出决策。

## 在事件驱动环境中定义策略

在 BackTrader 中创建 `bt.Strategy` 的子类。这是你定义参数、初始化指标和设置交易逻辑的地方。

以下是一个名为 `CustomSignalStrategy` 的示例，包含当需要时管理订单流（发送和接收后续通知）所需的基本方法：

```python
# 定义自定义策略
class CustomSignalStrategy(bt.Strategy):

    def __init__(self):
        # 策略开始时调用一次，用于声明指标和变量
        pass

    def log(self, txt, dt=None):
        # 实用方法，使用可选的日期时间（dt）戳记录给定文本
        pass

    def next(self):
        # 数据集中每个数据点（K线）调用一次。这是执行主要策略逻辑的地方。
        pass

    def notify_order(self, order):
        # 每当订单状态发生变化时调用。可用于订单确认、取消或拒绝。
        pass
```

剩下的就是用我们想要回测的交易系统特有的逻辑，填充并完成这些方法（`__init__`、`log`、`notify_order` 和 `next`）的代码。我们将为每个方法逐一完成。

`__init__` 方法负责处理机器学习算法提供的预测，作为初步设置。它访问位于 `self.datas[0].custom` 中的策略（买入/卖出）信号。变量 `custom_signal` 随后被设置为引用最新的信号（队列最前端）：

```python
def __init__(self):
    # 'custom' 信号 <- 预测
    self.custom_signal = self.datas[0].custom
```

`log` 函数负责在每次执行时显示一个日期（`dt`）和一段文本（`txt` 参数）：

```python
def log(self, txt, dt=None):
    ''' 日志记录函数 '''
    dt = dt or self.datas[0].datetime.date(0)
    print('%s, %s' % (dt.isoformat(), txt))
```

## 设置交易逻辑

在事件驱动编程框架内，我们编写由特定事件触发的方法。操作流程由这些事件的顺序引导。对于 `next` 方法，相关事件是新 K 线或价格更新的到来。

以下方法会为数据集中的每个数据点调用，这是策略核心逻辑展开的关键时刻。在这里，我们根据从 `self.custom_signal` 接收到的信号，管理并发送交易订单，区分买入和卖出类型。

提供的代码片段展示了如何根据传入信号执行买入或卖出订单：

```python
def next(self):
    # 逻辑：金字塔式加仓
    if self.custom_signal[0] == 1:
        self.buy()
    elif self.custom_signal[0] == -1:
        self.sell()
```

交易策略种类繁多。其中一个例子是反转策略，即每当信号发生变化时，持仓在多头和空头之间交替，同时保持目标金融工具数量不变。

BackTrader 通过 `order_target_size` 方法简化了这一过程，该方法允许交易者轻松设置固定仓位大小。该方法属于功能多样的 `order_target_xxx` 系列，允许交易者以多种方式定义其期望的投资组合目标：

- `order_target_size`：特定资产的股份或合约数量。
- `order_target_value`：资产在投资组合中的货币价值。
- `order_target_percentage`：分配给资产的当前投资组合价值的百分比。

```python
def next(self):
    if self.custom_signal[0] == 1:
        self.order = self.order_target_size(target=1)
    elif self.custom_signal[0] == -1:
        self.order = self.order_target_size(target=-1)
```

最后，关于策略实现，我们应该提及 `notify_order` 方法。在 BackTrader 中，`notify_order()` 方法用于拦截有关订单状态的消息。当下达订单时，它会在其生命周期中经历多个状态（如 Created 已创建、Submitted 已提交、Accepted 已接受），`notify_order()` 会在每次状态变化时提供更新。

`notify_order()` 用于在订单状态变化时采取适当行动，例如记录事件、更新策略状态，或处理订单完成或失败的情况。它是 BackTrader 策略逻辑的重要组成部分，使开发者能够管理订单流并根据需要响应事件：

```python
def notify_order(self, order):
    if order.status in [order.Submitted, order.Accepted]:
        # 买入/卖出订单已提交/被经纪商接受 - 无需操作
        return

    # 检查订单是否已完成
    if order.status in [order.Completed]:
        if order.isbuy():
            self.log('BUY EXECUTED, Price: %.2f, Size: %d' % (order.executed.price, self.getposition().size))
        elif order.issell():
            self.log('SELL EXECUTED, Price: %.2f, Size: %d' % (order.executed.price, self.getposition().size))
        self.bar_executed = len(self)

    # 注意：如果现金不足，经纪商可能会拒绝订单
    elif order.status in [order.Canceled, order.Margin, order.Rejected]:
        self.log('Order Canceled/Margin/Rejected')

    # 记录：无挂单
    self.order = None
```

## 创建 Cerebro 引擎

以下代码（`init_cerebro_before_run`）作为设置 BackTrader "Cerebro" 引擎的核对清单，确保从数据集成到执行细节的所有必要组件都已正确配置。

这种准备对于随后将数据和策略（`CustomSignalStrategy`）添加到引擎中、进入执行阶段至关重要：

```python
# 子类化 PandasData 数据源以将 'custom' 作为额外行包含在内
class CustomPandasData(bt.feeds.PandasData):
    lines = ('custom',)
    params = (('custom', -1),)

cash = 100000

def init_cerebro_before_run():
    # 使用自定义数据源将数据加载到 BackTrader
    data = CustomPandasData(dataname=df)

    # 创建一个新的 Cerebro 引擎
    cerebro = bt.Cerebro()

    # 在开盘/收盘时开仓/平仓（信号后的下一根 K 线）
    cerebro.cheat_on_close = False

    # 向引擎添加数据源
    cerebro.adddata(data)

    # 向引擎添加策略
    cerebro.addstrategy(CustomSignalStrategy)
```

