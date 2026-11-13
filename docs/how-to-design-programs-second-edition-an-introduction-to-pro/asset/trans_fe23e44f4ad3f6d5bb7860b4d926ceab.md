

> (opening "Matthew" "Fisler")
"Dear Matthew,"

更重要的是，计算定律解释了 DrRacket 如何确定此结果，以及你如何预测 DrRacket 的行为：

```
(opening "Matthew" "Fisler")
== ; DrRacket substitutes "Matthew" for first-name
(string-append "Dear " "Matthew" ",")
==
"Dear Matthew,"
```

由于 last-name 在 opening 的定义中未出现，将其替换为 "Fisler" 没有任何效果。

本书其余部分介绍了更多数据形式。为了解释对数据的操作，我们始终使用与此书中算术类似的定律。

> 最终你将遇到命令式操作，它们不组合或提取值，而是 **修改** 它们。要使用此类操作进行计算，你需要在算术和替换定律基础上添加一些定律。

### 练习 22.

对此程序片段使用 DrRacket 的单步调：

```
(define (distance-to-origin x y)
  (sqrt (+ (sqr x) (sqr y))))
(distance-to-origin 3 4)
```

该解释是否符合你的直觉？

### 练习 23.

"hello world" 中的第一个 1String 是 "h"。以下函数如何计算出此结果？

```
(define (string-first s)
  (substring s 0 1))
```

使用单步调验证你的想法。

### 练习 24.

以下是 ==> 的定义：

```
(define (==> x y)
  (or (not x) y))
```

使用单步调确定 (==> #true #false) 的值。

### 练习 25.

查看此尝试解决练习 17 的方案：

```
(define (image-classify img)
  (cond
    [(>= (image-height img) (image-width img)) "tall"]
    [(= (image-height img) (image-width img)) "square"]
    [(<= (image-height img) (image-width img)) "wide"]))
```

单步调试一个应用是否暗示了修复方法？

### 练习 26.

你预期此程序的值是什么：

```
(define (string-insert s i)
  (string-append (substring s 0 i)
                 "_"
                 (substring s i)))

(string-insert "helloworld" 6)
```

使用 DrRacket 及其单步调确认你的预期。

## 2.3 组合函数

程序很少仅由一个函数定义组成。通常，程序由一个 *主* 定义和若干其他函数组成，并将一个函数应用的结果转化为另一个函数的输入。借用代数中的类比，我们将这种定义函数的方式称为 *组合*，并称这些附加函数为 *辅助函数* 或 *辅助函数*。

请考虑图 12 中用于填写信件模板的程序。它由四个函数组成。第一个是主函数，它根据收件人的姓和名以及签名生成一封完整的信件。主函数引用三个辅助函数来生成信件的三个部分——开头、正文和结尾——并使用 string-append 按正确顺序组合结果。

```
(define (letter fst lst signature-name)
  (string-append
   (opening fst)
   "\n\n"
   (body fst lst)
   "\n\n"
   (closing signature-name)))

(define (opening fst)
  (string-append "Dear " fst ","))

(define (body fst lst)
  (string-append
   "We have discovered that all people with the" "\n"
   "last name " lst " have won our lottery. So, " "\n"
   fst ", " "hurry and pick up your prize."))

(define (closing signature-name)
  (string-append
   "Sincerely,"
   "\n\n"
   signature-name
   "\n"))
```

图 12：批处理程序

停止！将这些定义输入 DrRacket 的定义区域，点击 *运行*，并在交互区域对这些表达式求值：

```
> (letter "Matthew" "Fisler" "Felleisen")
"Dear Matthew,\n\nWe have discovered that ...\n"
> (letter "Kathi" "Felleisen" "Findler")
"Dear Kathi,\n\nWe have discovered that ...\n"
```

**旁注** 结果是一个包含 "\n" 的长字符串，当字符串被 **打印** 时，"\n" 表示换行。现在将 `(require 2htdp/batch-io)` 添加到你的程序中，这将向程序添加函数 `write-file`；它允许你将此字符串 **打印** 到控制台：

```
> (write-file 'stdout (letter "Matt" "Fiss" "Fell"))
Dear Matt,

We have discovered that all people with the
last name Fiss have won our lottery. So,
Matt, hurry and pick up your prize.

Sincerely,

Fell
'stdout
```

目前可以将 'stdout 视为一个字符串。

第 2.5 章详细解释了此类批处理程序。**结束**

一般来说，当问题涉及不同的计算任务时，程序应由每个任务一个函数以及一个将所有内容组合在一起的主函数组成。我们将这一想法概括为一句简单的口号：

*每个任务定义一个函数。*

遵循此口号的优势在于，你会得到相当小的函数，每个函数都易于理解，其组合也易于理解。一旦你学会设计函数，就会发现让小函数正确运行比让大函数正确运行要容易得多。更好的是，如果由于问题描述的变更而需要修改程序的一部分，当程序被组织为小函数的集合而非单一的大型单体块时，查找相关部分通常要容易得多。

以下是通过一个示例问题来说明这一点的小例子：

**示例问题** 一个小城镇中垄断电影院的业主在设定票价方面拥有完全的自由。他收费越高，能负担得起票的人就越少。他收费越低，运行一场演出的成本就越高，因为上座率上升了。在最近的一项实验中，业主确定了票价与平均上座率之间的关系。

当票价为每张 $5.00 时，有 120 人观看一场演出。票价每变化 10 美分，平均上座率就会变化 15 人。也就是说，如果业主收取 $5.10，平均约有 105 人观看；如果票价降至 $4.90，平均上座率会增加到 135 人。让我们将此想法转化为数学公式：

avg. attendance = 120 people − $(change in price) / $0.10 · 15 people

停止！在继续之前，请解释一下减号。

不幸的是，上座率增加也带来了更高的成本。每场演出对业主来说固定成本为 $180，外加每位观众 $0.04 的可变成本。

业主希望了解利润与票价之间的确切关系，以便最大化利润。

任务很明确，但如何着手却不明确。此时此刻，我们只能说几个数量相互依赖。

当面对这种情况时，最好逐一梳理各种依赖关系：

- 1. 问题描述规定了观众人数如何依赖于票价。计算此人数显然是一个独立任务，因此值得有自己的函数定义：

```
(define (attendees ticket-price)
  (- 120 (* (- ticket-price 5.0) (/ 15 0.1))))
```

- 2. *revenue* 完全由门票销售产生，这意味着它正好是票价与观众人数的乘积：

```
(define (revenue ticket-price)
  (* ticket-price (attendees ticket-price)))
```

- 3. *cost* 由两部分组成：固定部分（$180）和依赖于观众人数的可变部分。鉴于观众人数是票价的函数，计算演出成本的函数也必须消耗票价，以便能够复用 attendees 函数：

```
(define (cost ticket-price)
  (+ 180 (* 0.04 (attendees ticket-price))))
```

- 4. 最后，*profit* 是给定票价下的收入与成本之差：

```
(define (profit ticket-price)
  (- (revenue ticket-price)
     (cost ticket-price)))
```

BSL 中对 profit 的定义直接遵循了非正式问题描述的建议。

计算利润仅需要这四个函数，我们现在可以使用 profit 函数来确定一个良好的票价。

### 练习 27.

我们对示例问题的解决方案在函数中间包含几个常量。如“一个程序，多个定义”已指出的那样，最好给这些常量命名，以便未来的读者了解这些数字的来源。将 DrRacket 定义区域中的所有定义收集起来，并更改它们，使所有魔法数字都重构为常量定义。

### 练习 28.

确定这些票价（$1、$2、$3、$4 和 $5）下的潜在利润。哪个票价能最大化电影院的利润？确定

