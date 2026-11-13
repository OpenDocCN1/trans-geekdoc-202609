
观念具有普遍适用性。

## 14 到处都是相似之处

如果你解决了第二部分中的（一些）练习，你就知道许多解决方案看起来都很相似。事实上，这些相似之处可能会诱使你复制一个问题的解决方案来创建下一个问题的解决方案。但你不得盗用代码，甚至包括你自己的代码。相反，你必须对相似的代码片段进行抽象，本章将教你如何进行抽象。

我们避免相似之处的方法特定于“中级学生语言”，简称 ISL。几乎所有其他编程语言都提供类似的方法；在面向对象语言中，你可能会发现额外的抽象机制。无论如何，这些机制共享本章中阐述的基本特征，因此这里解释的设计思想也适用于其他场景。

> 在 DrRacket 中，从“语言”菜单的“如何设计程序”子菜单中选择“中级学生”。

### 14.1 函数中的相似之处

设计食谱决定了函数的基本组织，因为模板是根据数据定义创建的，而不考虑函数的目的。因此，不奇怪的是，消耗同一种数据的函数看起来相似。

考虑图 86 中的两个函数，它们消耗字符串列表并查找特定字符串。左边的函数查找 "dog"，右边的查找 "cat"。这两个函数几乎无法区分。每个都消耗字符串列表；每个函数体都包含一个具有两个子句的 cond 表达式。如果输入是 '()，每个都生成 #false；每个都使用 or 表达式来确定第一个项目是否是所需的项目，如果不是，则使用递归在列表的其余部分中查找。唯一的区别是嵌套 cond 表达式比较中使用的字符串：contains-dog? 使用 "dog"，而 contains-cat? 使用 "cat"。为了突出差异，这两个字符串被阴影标记。

```scheme
; Los -> Boolean
; does l contain "dog"?
(define (contains-dog? l)
(cond
[(empty? l) #false]
[else
(or
(string=? (first l)
"dog")
(contains-dog?
(rest l)))]))

; Los -> Boolean
; does l contain "cat"?
(define (contains-cat? l)
(cond
[(empty? l) #false]
[else
(or
(string=? (first l)
"cat")
(contains-cat?
(rest l)))]))
```

图 86：两个相似的函数

优秀的程序员懒得定义几个密切相关的函数。相反，他们定义一个单一函数，该函数可以在字符串列表中同时查找 "dog" 和 "cat"。这个通用函数消耗一段额外的数据——要查找的字符串——除此之外与原始的两个函数完全一样：

```scheme
; String Los -> Boolean
; determines whether l contains the string s
(define (contains? s l)
  (cond
    [(empty? l) #false]
    [else (or (string=? (first l) s)
              (contains? s (rest l)))]))
```

如果你真的需要像 `contains-dog?` 这样的函数，你可以将其定义为一行函数，`contains-cat?` 函数也是如此。图 87 就是这样做的，你应该简要地将其与图 86 进行比较，以确保你理解我们是如何从那里到达这里的。但最重要的是，有了 `contains?`，在字符串列表中查找任何字符串都变得微不足道，而且不再需要定义像 `contains-dog?` 这样的专门函数。

![](img/19fbe4068996ced0ce42cec7fb82a834_499_0.png)

你刚刚目睹的东西被称为 _抽象_ ，或者更确切地说，是 _函数抽象_ 。对不同版本的函数进行抽象是消除程序中相似之处的一种方法，正如你将看到的，消除相似之处简化了长期保持程序完整性的过程。

> 计算机科学家从数学中借用“抽象”这一术语。在那里，“6”是一个抽象概念，因为它代表了枚举六件事物的**所有**方式。相比之下，“6 英寸”或“6 个鸡蛋”是具体用法。

**练习 235。** 使用 `contains?` 函数定义分别搜索 "atom"、"basic" 和 "zoo" 的函数。

**练习 236.** 为以下两个函数创建测试套件：

```scheme
; Lon -> Lon
; adds 1 to each item on l
(define (add1* l)
(cond
 [(empty? l) '()]
 [else
 (cons
  (add1 (first l))
  (add1* (rest l)))]))
```

```scheme
; Lon -> Lon
; adds 5 to each item on l
(define (plus5 l)
(cond
 [(empty? l) '()]
 [else
 (cons
  (+ (first l) 5)
  (plus5 (rest l)))]))
```

然后对它们进行抽象。根据抽象将上述两个函数定义为一行函数，并使用现有的测试套件确认修订后的定义工作正常。最后，设计一个函数，从给定列表中的每个数字减去 2。

### 14.2 不同的相似之处

在 `contains-dog?` 和 `contains-cat?` 函数的情况下，抽象看起来很容易。只需比较两个函数定义，用函数参数替换字面字符串，并快速检查使用抽象函数定义旧函数是否容易。这种抽象如此自然，以至于它在书前两部分中不费吹灰之力就出现了。

本节说明完全相同的原则如何产生一种强大的抽象形式。看看图 88。两个函数都消耗一个数字列表和一个阈值。左边的一个生成所有低于阈值的数字列表，而右边的一个生成所有高于阈值的数字列表。

```scheme
; Lon Number -> Lon
; select those numbers on l
; that are below t
(define (small l t)
  (cond
    [(empty? l) '()]
    [else
     (cond
       [(< (first l) t)
        (cons (first l)
              (small (rest l) t))]
       [else
        (small
         (rest l) t)]))])

; Lon Number -> Lon
; select those numbers on l
; that are above t
(define (large l t)
  (cond
    [(empty? l) '()]
    [else
     (cond
       [(> (first l) t)
        (cons (first l)
              (large (rest l) t))]
       [else
        (large
         (rest l) t)]))])
```

图 88：另外两个相似的函数

这两个函数只在一个地方不同：决定给定列表中的数字是否应成为结果一部分的比较运算符。左边的函数使用 <，右边的使用 >。除此之外，这两个函数看起来是一样的，不计函数名。

让我们遵循第一个示例，通过一个额外参数对这两个函数进行抽象。这次，额外参数表示比较运算符，而不是字符串：

```scheme
(define (extract R l t)
 (cond
  [(empty? l) '()]
  [else (cond
         [(R (first l) t)
          (cons (first l)
                (extract R (rest l) t))]
         [else
          (extract R (rest l) t)]]))
```

要应用这个新函数，我们必须提供三个参数：一个比较两个数字的函数 R、一个数字列表 l 和一个阈值 t。然后该函数提取 l 中所有使 (R i t) 求值为 #true 的项 i。

停！此时你应该问一下这个定义是否有意义。没有多费周折，我们创建了一个消耗函数的函数——这可能是你以前从未见过的东西。然而，事实证明，你的简单小教学语言 ISL 支持这类函数，定义此类函数是优秀程序员最强大的工具之一——即使是在似乎不提供函数消耗函数的语言中也是如此。

> 如果你修过微积分课程，你就接触过微分算符和不定积分。这两者都是消耗并产生函数的函数。但我们不假设你修过微积分课程。

测试表明，`(extract < l t)` 计算的结果与 `(small l t)` 相同：

```scheme
(check-expect (extract < '() 5) (small '() 5))
(check-expect (extract < '(3) 5) (small '(3) 5))
(check-expect (extract < '(1 6 4) 5)
             (small '(1 6 4) 5))
```

同样，`(extract > l t)` 产生与 `(large l t)` 相同的结果，这意味着你可以像这样定义原来的两个函数：
