

2. 使用解决这个一般问题的方案来解决原始问题。

我们从一般问题的陈述开始：

## 示例问题

设计一个函数，在给定场景中绘制给定点集之间的连接。

虽然 render-poly 的设计几乎解决了这个问题，但我们还是基本从头开始设计这个函数。首先，我们需要一个数据定义。除非我们至少有几个点，否则连接点没有意义。为了简单起见，我们要求至少有一个点：

```
; An NELoP is one of:
; -- (cons Posn '())
; -- (cons Posn NELoP)
```

其次，我们为“连接点”函数制定签名、目的说明和函数头：

```
; Image NELoP -> Image
; connects the dots in p by rendering lines in img
(define (connect-dots img p)
MT)
```

第三，我们将 render-poly 的示例改编为这个新函数。正如我们的失败分析所说，该函数将 p 上的第一个 Posn 连接到第二个，第二个连接到第三个，第三个连接到第四个，依此类推，一直到最后一个，最后一个不连接任何东西。下面是第一个示例（包含三个 Posn 的列表）的改编版本：

```
(check-expect (connect-dots MT triangle-p)
    (scene+line
    (scene+line MT 20 20 30 20 "red")
    20 10 20 20 "red"))
```

期望的值是一幅带有两条线的图像：一条从第一个 Posn 到第二个 Posn，另一条从第二个 Posn 到第三个 Posn。

### 练习 191

将 render-poly 函数的第二个示例改编为 connect-dots。

第四，我们使用处理非空列表的函数模板：

```
(define (connect-dots img p)
  (cond
    [(empty? (rest p)) (... (first p) ...)]
    [else (... (first p) ...
        ... (connect-dots img (rest p)) ...)]))
```

该模板有两个子句：一个用于只有一个 Posn 的列表，另一个用于包含多个元素的列表。由于两种情况都至少有一个 Posn，模板在两个子句中都包含 (first p)；第二个子句还包含 (connect-dots (rest p)) 以提醒我们数据定义第二个子句中的自引用。

第五步也是核心步骤，是将模板转换为函数定义。由于第一个子句最简单，我们先从它入手。正如我们之前所说，当给定列表只包含一个 Posn 时，不可能连接任何东西。因此，函数在第一个 cond 子句中直接返回 MT。对于第二个 cond 子句，让我们回顾一下模板表达式计算的内容：

- (first p) 提取第一个 Posn；
- (rest p) 从 p 中提取 NELoP；以及
- (connect-dots img (rest p)) 通过在 img 中渲染线条来连接 (rest p) 中的点。

从我们设计 render-poly 的第一次尝试中我们知道，connect-dots 需要在 (connect-dots img (rest p)) 的结果基础上添加一条线，即从 (first p) 到 (second p)。我们知道 p 包含第二个 Posn，因为否则 cond 的求值会选择第一个子句。

将一切整合在一起，我们得到如下定义：

```
(define (connect-dots img p)
  (cond
    [(empty? (rest p)) img]
    [else
     (render-line
      (connect-dots img (rest p))
      (first p)
      (second p))]))
```

这个定义看起来比 render-poly 有缺陷的版本更简单，尽管它比 render-poly 能够处理多出的两种 Posn 列表。

相反，我们说 connect-dots 泛化了 render-poly。后者的每个输入也是前者的输入。或者从数据定义的角度来说，每个 Polygon 也是一个 NELoP。但是，有许多 NELoP **不是** Polygon。确切地说，所有包含两个或一个元素的 Posn 列表都属于 NELoP，但不属于 Polygon。然而，你的关键洞察是，仅仅因为一个函数需要处理比另一个函数更多的输入，并 **不** 意味着前者比后者更复杂；泛化通常会简化函数定义。

> 这个论证是 **非正式** 的。如果你需要关于集合或函数之间关系的此类主张的 **正式** 论证，你将需要学习逻辑。的确，本书的设计过程深受逻辑影响，计算逻辑课程是一个自然的补充。一般而言，逻辑之于计算，正如分析之于工程。

如上所述，render-polygon 可以使用 connect-dots 连接给定 Polygon 的所有连续 Posn；为了完成任务，它还必须添加一条从第一个 Posn 到最后一个 Posn 的线。从代码角度来说，这只是意味着组合两个函数：connect-dots 和 render-line，但我们还需要一个从 Polygon 中提取最后一个 Posn 的函数。一旦我们得到这个愿望，render-poly 的定义就是一行代码：

```
; Image Polygon -> Image
; adds an image of p to img
(define (render-polygon img p)
  (render-line (connect-dots img p)
    (first p)
    (last p)))
```

为 `last` 制定愿望清单条目很简单：

```
; Polygon -> Posn
; extracts the last item from p
```

同样很明显，`last` 可能是一个通用有用的函数，我们最好为来自 NELoP 的输入来设计它：

```
; NELoP -> Posn
; extracts the last item from p
(define (last p)
  (first p))
```

停！为什么使用 `first` 来定义 `last` 的存根是可以接受的？

### 练习 192

论证在 Polygons 上使用 `last` 为何可以接受。同时论证为何你可以将 `connect-dots` 的模板改编为 `last`：

```
(define (last p)
  (cond
    [(empty? (rest p)) (... (first p) ...)]
    [else (... (first p) ... (last (rest p)) ...)]))
```

最后，为 `last` 开发示例，将它们转换为测试，并确保图 73 中 `last` 的定义在你的示例上能正常工作。

```
; Image Polygon -> Image
; adds an image of p to MT
(define (render-polygon img p)
  (render-line (connect-dots img p) (first p) (last p)))

; Image NELoP -> Image
; connects the Posns in p in an image
(define (connect-dots img p)
  (cond
    [(empty? (rest p)) MT]
    [else (render-line (connect-dots img (rest p))
           (first p)
           (second p))]))

; Image Posn Posn -> Image
; draws a red line from Posn p to Posn q into im
(define (render-line im p q)
  (scene+line
   im (posn-x p) (posn-y p) (posn-x q) (posn-y q) "red"))

; Polygon -> Posn
; extracts the last item from p
(define (last p)
  (cond
    [(empty? (rest (rest (rest p)))) (third p)]
    [else (last (rest p))]))
```

## 图 73：绘制多边形

总而言之，render-poly 的开发自然引导我们考虑连接一系列连续点的一般问题。我们可以通过定义一个将一般函数与其他辅助函数组合的函数来解决原始问题。因此，程序由一个相对简单的主函数——render-poly——和执行大部分工作的复杂辅助函数组成。你将反复看到，这种设计方法很常见，是设计和组织程序的好方法。

### 练习 193

定义 render-poly 的另外两个想法：

- render-poly 可以将 p 的最后一项 cons 到 p 上，然后调用 connect-dots。
- render-poly 可以通过一个在 Polygons 上工作的 add-at-end 版本，将 p 的第一项添加到 p 的末尾。

使用这两个想法定义 render-poly；确保两个定义都能通过测试用例。

### 练习 194

修改 connect-dots，使其额外接收一个 Posn，最后一个 Posn 将连接到该 Posn。然后修改 render-poly 以使用这个新版本的 connect-dots。

当然，像 last 这样的函数在功能齐全的编程语言中可用，类似 render-poly 的东西在 2htdp/image 库中也可用。如果你在想我们为什么刚刚设计了这些函数，请考虑本书和本节的标题。目标 **不** 是（仅仅）设计有用的函数，而是研究如何系统地设计代码。具体来说，本节是关于设计过程中的泛化思想；有关此思想的更多信息，请参见第三部分和第六部分。

