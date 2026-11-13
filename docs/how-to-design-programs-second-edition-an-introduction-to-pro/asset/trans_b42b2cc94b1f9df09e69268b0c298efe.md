

产品，和字符串。所有 for 循环在循环体中绑定其子句的变量；`for*` 变体也在后续子句中绑定变量。以下两个近乎相同的代码片段说明了这两个作用域规则之间的区别：

```scheme
(define width 20)
(for/list ([width 10]
          [height width])
  (list width height))
```

```scheme
(define width 20)
(for*/list ([width 10]
            [height width])
  (list width height))
```

Racket 对这些循环的版本提供了比这里展示的更多功能，而且该语言有比这里更多的循环。

语法上的区别是，左边使用 `for/list`，右边使用 `for*/list`。从作用域角度看，正如箭头所示，两者差异很大。虽然两段都引入了循环变量 `width` 和 `height`，但左边使用外部定义的变量作为 `height` 的初始值，而右边使用第一个循环变量。

从语义上看，`for/list` 表达式会对其子句中的表达式求值，以生成值序列。如果子句表达式求值为

- 一个列表，其项构成序列值；
- 一个自然数 `n`，序列由 0, 1, ..., (- n 1) 组成；以及
- 一个字符串，其单字符字符串是序列项。

接下来，`for/list` 用生成的序列值依次绑定循环变量来求值循环体。最后，它将循环体的值收集到一个列表中。`for/list` 表达式的求值在最短序列耗尽时停止。

术语 对循环体的每次求值称为一次迭代。同样，可以说循环遍历其循环变量的值。

根据这个解释，我们可以轻松生成从 0 到 9 的列表：

```scheme
> (for/list ([i 10])
  i)
(list 0 1 2 3 4 5 6 7 8 9)
```

这相当于一个 `build-list` 循环：

```scheme
> (build-list 10 (lambda (i) i))
(list 0 1 2 3 4 5 6 7 8 9)
```

第二个示例将两个序列「拉链」在一起：

```scheme
> (for/list ([i 2] [j '(a b)])
  (list i j))
(list (list 0 'a) (list 1 'b))
```

为了再次进行比较，这里是使用纯 ISL+ 的相同表达式：

```scheme
> (local ((define i-s (build-list 2 (lambda (i) i)))
         (define j-s '(a b)))
    (map list i-s j-s))
(list (list 0 'a) (list 1 'b))
```

最后一个示例强调使用 `for/list` 进行设计：

### 示例问题

设计 `enumerate`。该函数接收一个列表，并生成一个与相同项配对的相对索引列表。

停止！使用 ISL+ 的抽象，系统地设计这个函数。使用 `for/list`，这个问题有一个直接的解决方案：

```scheme
; [List-of X] -> [List-of [List N X]]
; pairs each item in lx with its index
(check-expect
 (enumerate '(a b c)) '((1 a) (2 b) (3 c)))
(define (enumerate lx)
  (for/list ([x lx] [ith (length lx)])
    (list (+ ith 1) x)))
```

函数体使用 `for/list` 遍历给定列表和一个从 0 到 `(length lx)`（减 1）的数字列表；循环体将索引（加 1）与列表项相结合。

从语义上看，`for*/list` 以嵌套方式遍历序列，而 `for/list` 则并行遍历它们。也就是说，`for*/list` 表达式基本上展开为循环嵌套：

```scheme
(for*/list ([i 2] [j '(a b)])
  ...)
```

是以下内容的简写：

```scheme
(for/list ([i 2])
  (for/list ([j '(a b)])
    ...))
```

此外，`for*/list` 通过使用 `foldl` 和 `append` 将嵌套列表连接起来，收集成一个 **单一** 列表。

## 练习 304.

求值

```scheme
(for/list ([i 2] [j '(a b)]) (list i j))
```

和

```scheme
(for*/list ([i 2] [j '(a b)]) (list i j))
```

在 DrRacket 的交互区中。

让我们继续探索，将 `for/list` 和 `for*/list` 之间的作用域差异转化为语义差异：

```scheme
> (define width 2)
> (for/list ([width 3][height width])
   (list width height))
(list (list 0 0) (list 1 1))
> (for*/list ([width 3][height width])
   (list width height))
(list (list 1 0) (list 2 0) (list 2 1))
```

要理解第一个交互，请记住 `for/list` 并行遍历两个序列，并在较短的序列耗尽时停止。这里，两个序列是

| width | = | 0, 1, 2 |
| height | = | 0, 1 |
| body | = | (list 0 0) (list 1 1) |

前两行显示两个循环变量的值，它们同步变化。最后一行显示每次迭代的结果，这解释了第一个结果以及不包含 2 的对的缺失。

现在将这种情况与 `for*/list` 进行对比：

| width | = | 0 | 1 | 2 |
| height | = | 0 | | 0, 1 |
| body | = | | (list 1 0) | (list 2 0) (list 2 1) |

虽然第一行与 `for/list` 的情况类似，但第二行现在在其单元格中显示数字序列。`for*/list` 的隐式嵌套意味着每次迭代都会为特定的 `width` 值重新计算 `height`，从而创建一个独特的 `height` 值 **序列**。这解释了为什么 `height` 值的第一个单元格是空的；毕竟，在 0（包含）和 0（不包含）之间没有自然数字。最后，每个嵌套的 `for` 循环都会生成一对序列，这些序列被收集成一个单一的对列表。

这里有一个问题，说明了 `for*/list` 在上下文中的这种用法：

### 示例问题

设计 `cross`。该函数接收两个列表 `l1` 和 `l2`，并生成这些列表中所有项的对。

停止！花点时间设计该函数，使用现有的抽象。在设计 `cross` 时，您会使用这样的表格：

| cross | 'a | 'b | 'c |
|---|---|---|---|
| 1 | (list 'a 1) | (list 'b 1) | (list 'c 1) |
| 2 | (list 'a 2) | (list 'b 2) | (list 'c 2) |

第一行显示给定的 `l1`，而最左列显示 `l2`。表格中的每个单元格对应一个要生成的对。

由于 `for*/list` 的目的是枚举所有这样的对，因此通过 `for*/list` 定义 `cross` 很简单：

```scheme
; [List-of X] [List-of Y] -> [List-of [List X Y]]
; generates all pairs of items from `l1` and `l2`
(check-satisfied (cross '(a b c) '(1 2))
                 (lambda (c) (= (length c) 6)))
```

```scheme
(define (cross l1 l2)
  (for*/list ([x1 l1][x2 l2])
    (list x1 x2)))
```

我们使用 `check-satisfied` 而不是 `check-expect`，因为我们不希望预测 `for*/list` 生成对的精确顺序。

注意，图 108 展示了 `for*/list` 的另一个上下文用法。它显示了为给定列表中的字母创建所有可能重排的扩展设计问题的紧凑解决方案。

```scheme
; [List-of X] -> [List-of [List-of X]]
; creates a list of all rearrangements of the items in w
(define (arrangements w)
  (cond
    [(empty? w) '(())]
    [else (for*/list ([item w]
                      [arrangement-without-item
                       (arrangements (remove item w))])
            (cons item arrangement-without-item))])

; [List-of X] -> Boolean
(define (all-words-from-rat? w)
  (and (member? (explode "rat") w)
       (member? (explode "art") w)
       (member? (explode "tar") w)))

(check-satisfied (arrangements '("r" "a" "t"))
                 all-words-from-rat?)
```

### 图 108：使用 `for*/list` 的紧凑排列定义

虽然第 12.4 章概述了这个复杂程序的正确设计，但图 108 使用 `for*/list` 和一种不寻常的递归的结合力量，将同一程序定义为一个五行函数定义。该图仅展示了这些抽象的威力；关于基础设计，请参见特别是练习 477。结束

> 我们感谢 Mark Engelberg 提出展示这种表达能力的建议。

`../list` 后缀明确表明循环表达式创建一个列表。此外，该库还带有 `for` 和 `for*x` 循环，它们都有同样富有暗示性的后缀：

- `.../and` 使用 `and` 收集所有迭代的值：

```scheme
> (for/and ([i 10]) (> (- 9 i) 0))
#false
> (for/and ([i 10]) (if (>= i 0) i #false))
9
```

从实际角度看，该循环返回最后生成的值或 `#false`。

- `.../or` 与 `.../and` 类似，但使用 `or` 而不是 `and`：

