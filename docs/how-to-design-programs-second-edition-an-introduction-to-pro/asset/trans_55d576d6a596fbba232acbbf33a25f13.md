

## Exercise 440. 将 gcd-generative 复制到 DrRacket 的定义区并求值

```
(time (gcd-generative 101135853 45014640))
```

在交互区中。

你现在可能认为生成递归设计已经找到了 gcd 问题的一个更快速的解决方案，并可能得出结论认为生成递归总是正确的做法。这个判断过于仓促，原因有三。第一，即使设计良好的算法，也不总是比等价的结构递归函数更快。例如，quick-sort< 只在列表较大时才有优势；对于较小的列表，标准 sort< 函数更快。更糟糕的是，设计糟糕的算法会严重影响程序的性能。第二，使用结构递归的配方设计函数通常更容易。相反，设计算法需要一个如何生成新问题的想法，这一步往往需要深刻的洞察。最后，阅读函数的程序员可以轻松理解结构递归函数，即使没有太多文档。然而，算法的生成步骤基于“顿悟！”如果没有良好的解释，未来的读者（包括你早期的自己）也很难理解。

经验表明，程序中的大多数函数都采用结构设计；只有少数利用生成递归。当我们遇到一种设计既可以使用结构递归的配方，也可以使用生成递归的配方的情况时，最好的方法是先从结构版本开始。如果结果对于手头的任务来说太慢——且只有在这种情况下——才是探索使用生成递归的时候。

## Exercise 441. 求值

```
(quick-sort< (list 1 2 3 4 5 6 7 8 9 10 11 12 13 14))
```

手动求值。只显示引入对 quick-sort< 的新递归调用的那些行。需要多少次对 quick-sort< 的递归应用？需要多少次对 append 函数的递归应用？针对长度为 n 的列表，提出一个一般规则。

求值

```
(quick-sort< (list 1 2 3 4 5 6 7 8 9 10 11 12 13 14))
```

手动求值。需要多少次对 quick-sort< 的递归应用？需要多少次对 append 的递归应用？这是否与练习的第一部分相矛盾？◾

## Exercise 442. 将 sort< 和 quick-sort< 添加到定义区。对函数运行测试，以确保它们在基本示例上工作。还要开发 create-tests，一个随机生成大型测试用例的函数。然后探索它们在各种列表上的运行速度。

实验是否证实了这样的说法：对于短列表，普通的 sort< 函数通常优于 quick-sort<，反之亦然？

确定交叉点。利用它构建一个 clever-sort 函数，该函数对大列表的行为类似于 quick-sort<，对低于此交叉点的列表的行为类似于 sort<。与练习 427 进行比较。◾

## Exercise 443. 鉴于 gcd-structural 的头部材料，设计配方的天真使用可能会使用以下模板或其变体：

```
(define (gcd-structural n m)
(cond
[ (and (= n 1) (= m 1)) ... ]
[ (and (> n 1) (= m 1)) ... ]
[ (and (= n 1) (> m 1)) ... ]
[else
(... (gcd-structural (sub1 n) (sub1 m)) ...
... (gcd-structural (sub1 n) m) ...
... (gcd-structural n (sub1 m)) ... )]))
```

为什么用这种策略无法找到除数？◾

## Exercise 444. 练习 443 意味着 gcd-structural 的设计需要一些规划和一种基于组合的设计方法。

> 理想情况下，你应该使用集合而不是列表。

“最大公约数”的本身解释就暗示了一种两阶段方法。首先设计一个可以计算自然数的除数列表的函数。其次，设计一个函数，从 n 的除数列表和 m 的除数列表中选出最大的公共数。整体函数看起来会像这样：

```
(define (gcd-structural S L)
  (largest-common (divisors S S) (divisors S L)))
```

```
; N[>= 1] N[>= 1] -> [List-of N]
; computes the divisors of 1 smaller or equal to k
(define (divisors k l)
  '())
```

```
; [List-of N] [List-of N] -> N
; finds the largest number common to both k and l
(define (largest-common k l)
  1)
```

你认为 divisors 为什么要消耗两个数字？为什么它在两次使用中都将 s 作为第一个参数？

## 27 变奏曲

算法的设计始于对一种过程的非正式描述，该过程创建一个比给定问题更容易求解的问题，并且其解决方案有助于解决给定问题。想出这种想法需要灵感、对应用领域的深入以及对多种不同示例的经验。

本章介绍了几个算法的示例。有些直接取自数学，这是许多想法的来源；其他则来自计算环境。第一个示例是我们原则的图形说明：西尔宾斯基三角形。第二个示例用寻找函数根的简单数学例子解释了分治原则。然后它展示了如何将这个想法转化为搜索序列的快速算法，这是一个广泛使用的应用。第三部分涉及 1Strings 序列的“解析”，这也是现实世界编程中的常见问题。

### 27.1 分形，初步尝试

分形在计算几何中扮演着重要角色。Flake 在 *自然的计算之美* (The MIT Press, 1998) 中写道：“几何可以扩展到考虑具有分数维度的对象。这些被称为 *分形* 的对象，非常接近于捕捉自然界中发现的形式的丰富性和多样性。分形在多个……尺度上具有结构自相似性，这意味着一个分形的碎片通常看起来就像整体。”

图 156 显示了一个分形图形的示例，称为西尔宾斯基三角形。基本形状是一个（等边）三角形，如中心所示。当这个三角形以三角形方式充分多次组合时，我们得到最左边的形状。

![](img/19fbe4068996ced0ce42cec7fb82a834_807_0.png)

图 156：西尔宾斯基三角形

图 156 中最右侧的图像解释了生成步骤。单独来看，它表示：给定一个三角形，找到每条边的中点并将它们相互连接。这一步产生四个三角形；对这三个外三角形中的每一个重复该过程，除非这些三角形太小。

> 我们要感谢 Marc Smith 提供这个解决方案。

另一种解释非常适合 2htdp/image 库中的形状组合函数，它基于从中心图像到右侧图像的过渡。通过将两个中心三角形并置，然后在它们上方放置一个副本，我们也得到了右侧的形状：

```
> (s-triangle 3)
```

![](img/19fbe4068996ced0ce42cec7fb82a834_808_0.png)

```
> (beside (s-triangle 3) (s-triangle 3))
```

![](img/19fbe4068996ced0ce42cec7fb82a834_808_1.png)

```
> (above (s-triangle 3)
(beside (s-triangle 3) (s-triangle 3)))
```

![](img/19fbe4068996ced0ce42cec7fb82a834_808_2.png)

本节使用替代描述来设计西尔宾斯基算法；第 34.3 章讨论第一种描述。鉴于目标是生成等边三角形的图像，我们用一个（正）数（即三角形边长）来编码问题。这个决定产生了签名、目的陈述和头部：

```
; Number -> Image
; creates Sierpinski triangle of size side
(define (sierpinski side)
(triangle side 'outline 'red))
```

现在是时候回答生成递归的四个问题了：

- 当给定的数字非常小，以至于在其中绘制三角形毫无意义时，问题是平凡的。
- 在这种情况下，生成一个三角形就足够了。
- 否则，算法必须生成大小为 side / 2 的西尔宾斯基三角形，因为将两个这样的三角形沿任何方向并置会产生大小为 side 的三角形。
- 如果 half-sized 是大小为 side / 2 的西尔宾斯基三角形，那么
  (above half-sized
   (beside half-sized half-sized))
  是大小为 side 的西尔宾斯基三角形。

有了这些答案，定义函数就很简单了。图 157 详细说明了具体细节。“平凡条件”转化为 (<= side SMALL)，其中 SMALL 是某个常量。对于平凡答案，函数返回给定大小的三角形。在递归情况下，一个局部表达式引入了 half-sized 名称，指大小为指定尺寸一半的西尔宾斯基三角形。一旦递归调用生成了小西尔宾斯基三角形，它就会通过 above 和 beside 组合这张图像。

```
(define SMALL 4) ; a size measure in terms of pixels

(define small-triangle (triangle SMALL 'outline 'red))

; Number -> Image
; generative creates Sierpinski Δ of size side by generating
; one for (/ side 2) and placing one copy above two copies

(check-expect (sierpinski SMALL) small-triangle)
(check-expect (sierpinski (* 2 SMALL))
 (above small-triangle
  (beside small-triangle small-triangle)))

(define (sierpinski side)
 (cond
  [(<= side SMALL) (triangle side 'outline 'red)]
  [else
   (local ((define half-sized (sierpinski (/ side 2))))
    (above half-sized (beside half-sized half-sized)))])))
```

图 157：西尔宾斯基算法

该图还强调了另外两点。首先，目标陈述是

