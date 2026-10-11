

“Is Art”是一个以太坊智能合约，其中包含一个断言：它“是”艺术，或者它“不是”艺术。任何人都可以向该智能合约发送一笔以太坊交易，指示其提名自己为艺术（或非艺术）。一个连接到以太坊网络的网页向任何能够访问该合约的人显示该断言的状态，并为他们提供一个方便的界面来在各状态间切换。当他们这样做时，这将成为一个由以太坊区块链保障的事实，其算力强度达每天数百万美元。

这采用了观念艺术的非物质化（不以固定物理形式呈现的艺术）和提名（某物之所以是艺术，是因为有人或某物说它是）理念，并将它们与网络艺术中存在于网络协议内部或干扰网络协议的交互式艺术品理念相结合。谁切换了合约的艺术状态，该状态就将由其不受阻碍地设定，直到下一个人发送交易来更改它。应该使用一个更理性的系统（且不应简化为单纯的资本）——竞价、投票或预测市场。

杜尚式的通过艺术提名进行审美质变的策略早已玩腻了。它是一个艺术史现成品，就像一个仅包含单个布尔位状态的智能合约一样基础。这种提名与信息的结合唤起了观念艺术和网络艺术。

20世纪60年代末的观念艺术和20世纪90年代中期的网络艺术，对于思考区块链和智能合约是有益的灵感来源。这些艺术运动与其时代的通信、法律和商业体系处于批判性的张力关系中。每一种都将无根信息——无论是关于感官数据还是网络消息——视为艺术的关键主题和一个潜在的新艺术世界。它们的承诺及其最终被现有艺术世界收编的命运，与区块链的历史经验相呼应。将二者结合在一起，艺术史与当代技术（或其受众）可以相互激活并相互质询。

这一切是否足以判定该合约是或不是艺术？该主张究竟在何处、以何种方式被真正提出并确定？这与此类艺术品的历史范例有何关联？又与存储在其他智能合约中的其他事实主张有何关联？

# Art Is

## 2014, 2017 Ethereum DApp

![](image/art-is-2.0.png)

一个允许任何人定义什么是艺术的合约。它包含一组关于艺术的十二个陈述。它们被编码为十六进制值，这些值被解释为简单版“国际艺术英语”中的句子，并由UI显示。

```
{  ;; 常量值  ;; 价格基数 (wei)，每个定义翻倍，最多至 DEFS-COUNT
  (def ‘PRICE-BASE 10)
  ;; 将索引加到价格基数指数上
  (def ‘PRICE-FACTOR-ADD 10)
  ;; 定义的数量
  (def ‘DEFS-COUNT 12)
  ;; 定义的取值范围
  (def ‘DEF-MIN 0x1)
  (def ‘DEF-MAX 0x0F0F0F0F)
  ;; 存储位置
  (def ‘artist 0x10)
  (def ‘defs-base 0x100)
  (def ‘theorists-base 0x200)
  ;; 状态
  ;; 合约所有者/收款人
  [[artist]] (caller)
  (return
    0x0
    (lll
      {
      [action] (calldataload 0)
        (when (= @action “set”)
          {
          [index] (calldataload 32)
          [definition] (calldataload 64)
          [price] (exp PRICE-BASE (+ @index 1 PRICE-FACTOR-ADD))
          ;; 如果索引在范围内且调用者支付了足够的费用来设置它
          (when (&& (>= @definition DEF-MIN)
                    (<= @definition DEF-MAX)
                    (< @index DEFS-COUNT)
                    (= (callvalue) @price))
            {
            ;; 更新定义
            [[(+ defs-base @index)]] @definition
            [[(+ theorists-base @index)]] (caller)
            (- (gas) 100) @@artist @price 0 0 0 0
            })
          })
      }
      0x0)) }
```

# MYSOUL

## 2014 Counterparty 和 Dogeparty 资产

![](image/mysoul-counterparty.png)![](image/mysoul-dogeparty.png)

我已将我的灵魂放上区块链，将其表示为一种加密资产代币。

`MYSOUL` 代币作为 Dogeparty 资产存在于 Dogecoin 区块链上。

我将其分成了 100 个单位。这比用单个代币代表灵魂并将其转移给单一所有者更高效，因为市场内的竞争将同时降低成本，并比垄断更有效地配置这一资源。

为了让我的灵魂所有权更易获得，我还在 Bitcoin 区块链上用 Counterparty 创建了一个 `MYSOUL` 资产。

这也被分成了 100 个单位。Counterparty 的交易费用比 Dogeparty 高，但使用更广泛，所以同时拥有这两种选择是好的。

请注意，我的妻子不允许我出售任何代币，因为她相当合理地断言，如果我的灵魂属于谁，那也是属于她的。

# Dogecode

## 2014 Python 代码和 Dogeparty 代币

![dogecode](image/dogecode.jpg)

加密资产代币可以代表各种事物。

包括计算机程序。

Dogecode 接收 Brainfuck 编程语言（因其编码简单而被选中）编写的计算机程序：

```
++++++++[>++++[>++>+++>+++>+<<<<-]>+>+>->>+[<]<-]>>.>---.+++++++..+++.>>.<-.<.+++.------.--------.>>+.>++.
```

并使用 `dcc` 将它们转换为代币数量的 CSV 文件：

```
INCB,8
JFOR,1
INCP,1
INCB,4
JFOR,1
INCP,1
INCB,2
INCP,1
INCB,3
INCP,1
...
```

随后，这些代币通过 `dcsend` 作为一系列代币转账交易发送到一个 Dogeparty 地址（缓慢地）：

```
Sending lots of tokens. Make sure you really want to do this.
Waiting for token state to synch
Row 1: INCB,8
Waiting for token state to synch...........
Row 2: JFOR,1
Waiting for token state to synch.............
Row 3: INCP,1
Waiting for token state to synch........
Row 4: INCB,4
Waiting for token state to synch..................
Row 5: JFOR,1
Waiting for token state to synch.......................
Row 6: INCP,1
Waiting for token state to synch.......................
Row 7: INCB,2
Waiting for token state to synch......
Row 8: INCP,1
Waiting for token state to synch......
Row 9: INCB,3
Waiting for token state to synch......
```

这些交易将程序编码在该地址上，随后可使用 `dcrun` 获取并运行：

```
> dcrun -u rpcuser -w rpcpassword \
 DCvDS9g9VUZ94MSLbWi4zWRtxHrXeEctZ3
Hello World!
```

还有一个更易用的运行器，它使用 dogepartychain.info 的 API，而不需要运行本地的 dogepartyd 实例，它将获取在指定地址 (DCvD…) 处编码为 Dogeparty 代币的程序并在本地运行它：

```
> dcrunw DCvDS9g9VUZ94MSLbWi4zWRtxHrXeEctZ3
Hello World!
```

以下是一些可供尝试的地址：

`DCvDS9g9VUZ94MSLbWi4zWRtxHrXeEctZ3`

`DFZkhTXwAWW7PqBvVkohCFWobipqw3xmAn`

`DFibwNZvuJaHM9bD6x1WA63urkHiE4tWzF`

`DQuineX1BTF4ZD6DQxxsbUgVttmR4LvrdY`

### 警告

编写和上传 Dogecode 程序时请小心。您有责任确保程序按预期运行，并将正确的代币发送到正确的地址。任何错误都将伴随损失和遗憾。

## Dogecode 白皮书 v0.1

### 概述

Dogecode 是一种使用 Dogeparty 代币序列来表示计算机程序的系统，旨在通过 Dogecoin 区块链存储、发送和执行其代码。

### 代币

程序的编码是 “Brainfuck” 编程语言的一个微小变体，因其极简主义而被选中。[1](#60-Dogecode.xhtml#footnote-003)

Brainfuck 编程语言中的每个命令都由一个不可分割的 Dogeparty 资产表示。

程序中单次出现的命令由发送单个代币表示，例如 `+` 由发送 1 个 `INCB` 代币表示。

多次出现的命令由在单次转账中发送多个代币表示，例如 `+++++` 由发送 5 个 `INCB` 代币表示。

