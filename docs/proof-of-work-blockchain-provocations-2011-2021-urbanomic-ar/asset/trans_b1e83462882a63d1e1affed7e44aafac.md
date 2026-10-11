
# 以太坊艺术市场

## 智能合约代码

```
{   (def ‘next-record 0x10)(def ‘RECORD-SIZE 64)   
;; 下一条记录的位置   
;; 这从 RipeMD 最大值的上方一个单元格开始   
[[next-record]] 0x10000000000000000000000000000000000000000   
(return   
   0x0   
   (lll {   
      ;; 动作   
      ;; 0 - 消息中的第一个单元格   
      [action] (calldataload 0)   
       (when (= @action “register”)   
         {   
         ;;TODO: 检查消息长度是否正确   
         ;;TODO: 检查摘要是否在范围内   
          ;; 艺术品摘要   
         [digest] (calldataload 32)   
         ;; 如果已注册，则不继续   
          (when @@ @digest   
            (return “Artwork already registered.”))   
         ;; 获取新记录的存储空间   
         [storage] @@next-record   
         ;; 存储摘要   
         [[@storage]] @digest   
         ;; 艺术家账户   
         [storage] (+ @storage 1)   
         [[@storage]] (caller)   
         ;; 艺术家转售百分比   
         [storage] (+ @storage 1)   
         [[@storage]] (calldataload 64)   
         ;; 艺术家是当前所有者   
         [storage] (+ @storage 1)   
         [[@storage]] (caller)   
         ;; 跳过购买者和价格   
         [storage] (+ @storage 3)   
         ;; 复制 URL 和描述   
         ;; 96 是 32 x 3 = 消息中的第 3 个单元格   
         [source] 96   
            (for [i] 6 (< @i 64) [i] (+ @i 1)   
               {   
               [[@storage]] (calldataload @source)   
               [storage] (+ @storage 1)   
               [source] (+ @source 32)   
               })   
         ;; 存储摘要到记录的链接   
         [[@digest]] @@next-record   
         ;; 增加下一条记录的位置   
         [[next-record]] (+ @@next-record RECORD-SIZE)   
         })   
      (when (= @action “offer”)   
         {   
         ;; TODO: 检查消息长度是否正确   
         ;; TODO: 检查摘要是否在范围内   
         ;; 获取摘要对应的艺术品记录存储位置，如果不存在则停止   
         ;; 32 = 消息中的第二个单元格   
         [storage] @@(calldataload 32)   
         (when (not @storage)   
            (return “Artwork not registered.”))   
         ;; 如果调用者是所有者   
         (when (= @@ (+ @storage 3) (caller))   
            {   
            ;; 报价主题   
            [[(+ @storage 4)]] (calldataload 64)   
            ;; 报价价格   
            [[(+ @storage 5)]] (calldataload 96)   
            })   
            })   
      (when (= @action “accept”)   
         {   
         ;;TODO: 检查摘要是否在范围内   
         ;;TODO: 对错误价格或买家的错误消息   
         ;; 获取摘要对应的艺术品记录存储位置，如果不存在则停止   
         ;; 32 = 消息中的第二个单元格   
         [storage] @@(calldataload 32)   
         (when (not @storage)   
            (return “Artwork not registered.”))   
         [buyer] @@(+ @storage 4)   
         [price] @@(+ @storage 5)   
         ;; 如果调用者是买家且付款正确   
         ;; 或者没有买家但付款正确且非零   
         (= @price (callvalue)))   
         (&&   
        (= @buyer 0)   
            (> @price 0)))   
            {   
            ;; 用于付款 
            ;; 以太坊不允许小数金额   
            ;; 提醒用户设置可被整除的价格   
            [hundredth] (/ @price 100)   
            [arr] @@(+ @storage 2)   
            ;; 支付给艺术家   
            (call (- (gas) 250) @@(+ @storage 1) (* @hundredth @arr) 0 0 0 0)   
            ;; 支付给所有者   
            (call (- (gas) 250) @@(+ @storage 3) (* @hundredth (- 100 @arr)) 0 0 0 0)   
            ;; 转移所有权   
            [[(+ @storage 3)]] (caller)   
            ;; 清除报价主题和价格   
            [[(+ @storage 4)]] 0   
            [[(+ @storage 5)]] 0   
            })   
         })   
         })   
      } 0x0))}
```

## UI 截图

这是主 UI 的顶部和底部（使用 HTML 和 JavaScript 为 AlethZero 以太坊客户端实现）。

![UI 顶部和底部](image/140724_myers-Ethereum_art_market-01.jpg) ![UI 顶部和底部](image/140724_myers-Ethereum_art_market-03.jpg)

您可以输入一个 URL 并获取其加密哈希值。如果艺术品已注册，这将显示其详细信息。

![艺术品详情](image/140724_myers-Ethereum_art_market-02.jpg) ![注册表](image/registry5.jpg)

如果未注册，您可以对其进行注册。

![注册艺术品](image/140724_myers-Ethereum_art_market-05.jpg)

一旦您注册了艺术品，您就是它的艺术家，同时也拥有它。您可以将您拥有的任何艺术品挂牌出售。

![挂牌出售](image/140724_myers-Ethereum_art_market-06.jpg)

您可以接受销售报价，支付指定数量的以太币。

![接受销售](image/140724_myers-Ethereum_art_market-07.jpg)

UI 会警告您即将花费多少以太币。

![花费警告](image/140724_myers-Ethereum_art_market-08.jpg)

当您购买艺术品时，它会让您知道转移何时完成。

![转移完成](image/140724_myers-Ethereum_art_market-09.jpg)

这是一个同构数字艺术市场。与现有艺术市场相反，它完全公开透明。并且与许多司法管辖区不同，它以自愿的方式实施了有争议的“艺术家转售权”（方式类似于《艺术财产的社会生活》中建议的方式）。[4](#7-Ethereum-art-market.xhtml#footnote-143) 如果在现有艺术市场中进行实验难以实现，我们可以为新型艺术创建新市场。就像这个一样。

## 注释

[1](#7-Ethereum-art-market.xhtml#footnote-146-backlink) 参见“[艺术世界以太坊](#6-Artworld-ethereum.xhtml)”。

[2](#7-Ethereum-art-market.xhtml#footnote-145-backlink) A. Dash, ‘A Bitcoin for Digital Art’, medium.com, [<https://medium.com/message/a-bitcoin-for-digital-art-8c7db719e495>](https://medium.com/message/a-bitcoin-for-digital-art-8c7db719e495)。

[3](#7-Ethereum-art-market.xhtml#footnote-144-backlink) [<https://eth.wiki/>](https://eth.wiki/)。

[4](#7-Ethereum-art-market.xhtml#footnote-143-backlink) A. Whitaker, *The Social Life of Artistic Property*, [<https://www.thing.net/~rdom/ucsd/3somesPlus/sociallifeofartisticproperty.pdf>](https://www.thing.net/~rdom/ucsd/3somesPlus/sociallifeofartisticproperty.pdf)。

# 加密印记

## 2014

![印记](image/sigil.png)

加密哈希函数是一段计算机代码，它接收一段数据并生成一个（希望）唯一的短字符串来代表它。该字符串绝不会类似于输入数据，您也无法从中猜出输入数据。对于相同的数据，该函数始终输出相同的字符串，而更改数据将改变输出字符串。

例如，我可以在 UNIX 命令行上使用 `sha256` 函数为我的名字创建一个唯一的表示：

```
# echo rhea | sha256sum
2466a0da1499e193618f43b392a408b2101710fef023f8b01ec351ab393d9ea4 –
```

如果我再次执行此操作，会得到相同的结果：

```
# echo rhea | sha256sum
2466a0da1499e193618f43b392a408b2101710fef023f8b01ec351ab393d9ea4 –
```

但如果我只添加一个额外的字符，就会得到不同的结果：

```
# echo rheaM | sha256sum
aa0aaa2835c977137200480dae2672603eb368b80adaae4aef79a385c451ff95 –
```

重要的是，输入差异的大小对输出字符串之间的差异大小没有影响：

```
# echo rheaN | sha256sum
81744d575e87892fa40992b20a001036a871f7401839beed78aab114c2e00818 –
```

因此，加密哈希函数的输出为数据生成了身份标识，可用于唯一引用数据，但不会泄露数据内容。

哈希函数通过将数据馈送到复杂的数学变换中来实现这一点。这是一种在数学空间中的映射，它在隐藏内容的同时保持了身份和差异。

这非常像印记。

确实，如果知道制作印记所抽象的词语，人们可以在印记中识别出它们的痕迹。但这些痕迹是达到目的的手段，它们是产生一个引人注目且独特的新身份以供专注和投入的方式。

