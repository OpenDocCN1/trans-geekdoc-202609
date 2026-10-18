

接下来，我们想要为 `LOs` 和 `MOs` 编写与 `OrderBook` 交互的方法。请注意，`Equation (10.1)`（新的 `Sell LO` 可能会移除 `OB` 上 `Buy LOs` 的开头部分）、`Equation (10.3)`（新的 `Buy LO` 可能会移除 `OB` 上 `Sell LOs` 的开头部分）、`Equation (10.5)`（`Sell MO` 移除 `OB` 上 `Buy LOs` 的开头部分）和 `Equation (10.7)`（`Buy MO` 移除 `OB` 上 `Sell LOs` 的开头部分）都执行一个共同的核心功能——它们会“侵蚀” `OB` 上（对侧）最重要的 `LOs`。因此，我们首先编写一个 `@staticmethod eat_book` 来实现这个共同功能。

`eat_book` 接收一个 `ps_pairs: PriceSizePairs`（代表 `OB` 的一侧）和要买卖的股数：`int` 作为输入。请注意 `eat_book` 的返回类型：`Tuple[DollarsAndShares, PriceSizePairs]`。返回的 `DollarsAndShares` 表示成交的美元金额和成交的股数（成交股数小于或等于输入股数）。返回的 `PriceSizePairs` 表示在成交的股数侵蚀了输入 `ps_pairs` 后，`ps_pairs` 的剩余部分。`eat_book` 首先会尽可能删除（即“吃掉”）`ps_pairs: PriceSizePairs` 数据结构的*开头*（基本上是将输入的股数与 `ps_pairs: PriceSizePairs` 输入开头处的适当股数进行匹配）。请注意，返回的 `PriceSizePairs` 是一个独立的数据结构，确保了输入 `ps_pairs: PriceSizePairs` 的不可变性。

![](images/comp10_2.jpg)

现在我们准备好编写方法 `sell_limit_order`，它以 `Sell LO Price` 和 `Sell LO shares` 作为输入。如下面的代码所示，首先它可能会移除（如果“交叉”）`OB` 上 `Buy LOs` 侧的适当股数（使用 `@staticmethod eat_book`），然后可能会在 `OB` 上 `Sell LOs` 侧的 `Sell LO Price` 处添加适当数量的股份。`sell_limit_order` 返回一个 `DollarsAndShares` 类型和 `OrderBook` 类型的对。返回的 `DollarsAndShares` 表示与 `OB` 上 `Buy LOs` 侧成交的美元金额和成交股数（成交股数小于或等于输入股数）。返回的 `OrderBook` 表示在可能侵蚀 `OB` 上 `Buy LOs` 侧，然后可能在 `OB` 上 `Sell LOs` 侧的 `Sell LO Price` 处添加一些股份后的新 `OB`。请注意，返回的 `OrderBook` 是一个新创建的数据结构，确保了 `self` 的不可变性。我们敦促您仔细阅读下面的代码，因为代码中处理了许多微妙的细节。

![](images/comp10_3.jpg)

接下来，我们编写更简单的方法 `sell_market_order`，它以要卖出的股数（作为市价单）作为输入。`sell_market_order` 与 `OB` 上 `Buy LOs` 侧的适当股数进行交易（从 `Buy LOs` 侧移除那么多股份）。它返回一个 `DollarsAndShares` 类型和 `OrderBook` 类型的对。返回的 `DollarsAndShares` 表示成交的美元金额和成交股数（成交股数小于或等于输入股数）。返回的 `OrderBook` 表示在成交的股数侵蚀了 `OB` 上 `Buy LOs` 侧后的 `OB` 剩余部分。请注意，返回的 `OrderBook` 是一个新创建的数据结构，确保了 `self` 的不可变性。

![](images/comp10_4.jpg)

我们不会在此列出方法 `buy_limit_order` 和 `buy_market_order`，因为它们完全类似（您可以在文件 `rl/chapter9/order_book.py` 中找到 `OrderBook` 的完整代码）。现在让我们通过创建一个示例 `OrderBook` 并提交一些 `LOs` 和 `MOs` 来与 `OrderBook` 交互，以测试这段代码。

![](images/comp10_5.jpg)

上面的代码在价格范围 `[91, 114]` 内创建了一个 `OrderBook`，买卖价差为 `5`。[Figure 10.2](#chapter10.xhtml#fig10_2) 直观地描绘了这个 `OrderBook`。

![Figure 10.2 Starting Order Book](images/fig10_2.jpg)

[Figure 10.2](#chapter10.xhtml#b10fig10_2) 初始订单簿

让我们提交一个 `Sell LO`，表示我们希望以大于或等于 `107` 的价格卖出 `40` 股。我们的 `Sell LO` 应该直接添加到 `OB` 的 `Sell LOs` 侧。

![](images/comp10_6.jpg)

新的 `OrderBook ob1` 在价格水平 `107` 处增加了 `40` 股，如 [Figure 10.3](#chapter10.xhtml#fig10_3) 所示。

![Figure 10.3 Order Book after Sell LO](images/fig10_3.jpg)

[Figure 10.3](#chapter10.xhtml#b10fig10_3) 卖出限价单后的订单簿

现在让我们提交一个 `Sell MO`，表示我们希望以“最佳价格”卖出 `120` 股。我们的 `Sell MO` 应该以 `100` 和 `99` 的“最佳价格”与 `120` 股进行交易（因为 `OB` 在 `100` 的价格上没有足够的 `Buy LO` 股份）。

![](images/comp10_7.jpg)

新的 `OrderBook ob2` 在 `OB` 的 `Buy LOs` 侧减少了 `120` 股，如 [Figure 10.4](#chapter10.xhtml#fig10_4) 所示。

![Figure 10.4 Order Book after Sell MO](images/fig10_4.jpg)

[Figure 10.4](#chapter10.xhtml#b10fig10_4) 卖出市价单后的订单簿

现在让我们提交一个 `Buy LO`，表示我们希望以小于或等于 `100` 的价格买入 `80` 股。我们的 `Buy LO` 应该添加到 `OB` 的 `Buy LOs` 侧。

![](images/comp10_8.jpg)

新的 `OrderBook ob3` 在价格水平 `100` 处重新引入了一个 `Buy LO`（现在有 `80` 股），如 [Figure 10.5](#chapter10.xhtml#fig10_5) 所示。

![Figure 10.5 Order Book after Buy LO](images/fig10_5.jpg)

[Figure 10.5](#chapter10.xhtml#b10fig10_5) 买入限价单后的订单簿

现在让我们提交一个 `Sell LO`，表示我们希望以大于或等于 `104` 的价格卖出 `60` 股。我们的 `Sell LO` 应该添加到 `OB` 的 `Sell LOs` 侧。

![](images/comp10_9.jpg)

新的 `OrderBook ob4` 在价格 `104` 处引入了一个带有 `60` 股的 `Sell LO`，如 [Figure 10.6](#chapter10.xhtml#fig10_6) 所示。

![Figure 10.6 Order Book after 2nd Sell LO](images/fig10_6.jpg)

[Figure 10.6](#chapter10.xhtml#b10fig10_6) 第二次卖出限价单后的订单簿

现在让我们提交一个 `Buy MO`，表示我们希望以“最佳价格”买入 `150` 股。我们的 `Buy MO` 应该在 `OB` 的 `Sell LOs` 侧以“最佳价格”与 `150` 股进行交易。

![](images/comp10_10.jpg)

新的 `OrderBook ob5` 在 `OB` 的 `Sell LOs` 侧减少了 `150` 股，清空了价格水平 `104` 的所有股份，并几乎清空了价格水平 `105` 的所有股份，如 [Figure 10.7](#chapter10.xhtml#fig10_7) 所示。

![Figure 10.7 Order Book after Buy MO](images/fig10_7.jpg)

[Figure 10.7](#chapter10.xhtml#b10fig10_7) 买入市价单后的订单簿

这对我们的代码进行了良好的测试（交易按我们期望的方式运行），我们鼓励您编写更多此类代码来与 `OrderBook` 交互，并绘制 `OrderBook` 演变的图表，这将有助于培养更强的直觉并内化我们上面学到的概念。上面的所有代码都在文件 `rl/chapter9/order_book.py` 中。

现在我们准备好开始处理大规模市价单最优执行的问题。

## 10.2 市价单最优执行

