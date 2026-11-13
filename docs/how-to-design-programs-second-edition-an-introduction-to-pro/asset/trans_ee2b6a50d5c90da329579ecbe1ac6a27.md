

- 3. `(insert n (rest alon))` 从 n 和 `(rest alon)` 中的数字生成一个排序后的列表。

问题是如何将这些数据片段组合起来以得到最终答案。让我们通过一些示例来具体化这一切：

```
(insert 7 (list 6 5 4))
```

这里 n 是 7，且大于第二个输入中的任何数字。我们只需查看列表的第一个元素即可知道这一点。它是 6，但因为列表已排序，列表中的所有其他数字都比 6 更小。因此，只需将 7 cons 到 (list 6 5 4) 即可。

相比之下，当应用类似于：

```
(insert 0 (list 6 2 1 -1))
```

n 确实必须插入到列表的其余部分中。更具体地说，(first alon) 是 6；(rest alon) 是 (list 2 1 -1)；根据目的说明，(insert n (rest alon)) 生成 (list 2 1 0 -1)。通过将 6 重新添加到该最后列表上，我们得到了 (insert 0 (list 6 2 1 -1)) 所需的答案。

要获得完整的函数定义，必须对这些示例进行泛化。用例分析表明一个嵌套条件表达式，用于判断 n 是否大于（或等于）(first alon)：

- 如果是，那么 alon 中的所有项都比 n 小，因为 alon 已经排序。在这种情况下的答案是 (cons n alon)。

- 然而，如果 n 小于 (first alon)，那么函数尚未找到将 n 插入 alon 的适当位置。结果的第一个项必须是 (first alon)，并且必须将 n 插入到 (rest alon)。在这种情况下的最终结果是

```
(cons (first alon) (insert n (rest alon)))
```

因为这个列表包含 n 和 alon 的所有项，且按排序顺序排列——这正是我们需要的。

将此讨论转译为 BSL+ 需要针对这种情况使用 if 表达式。条件是 (>= n (first alon))，两个分支的表达式已经拟定。

图 72 包含完整的排序程序。将其复制到 DrRacket 的定义区中，重新添加测试用例并测试程序。现在所有测试都应通过，并且它们应覆盖所有表达式。

```
; List-of-numbers -> List-of-numbers
; produces a sorted version of l
(define (sort> l)
 (cond
  [(empty? l) '()]
  [(cons? l) (insert (first l) (sort> (rest l)))]))

; Number List-of-numbers -> List-of-numbers
; inserts n into the sorted list of numbers l
(define (insert n l)
 (cond
  [(empty? l) (cons n '())]
  [else (if (>= n (first l))
   (cons n l)
   (cons (first l) (insert n (rest l)))))]))
```

## 图 72：对数字列表进行排序

**术语** 这种特定的排序程序在编程文献中称为*插入排序*。稍后我们将学习对列表进行排序的替代方法，采用完全不同的设计策略。

## 练习 186. 再次审视间奏曲 1，即介绍 BSL 及其测试表述方式的那个间奏曲。后者之一是 check-satisfied，用于判断一个表达式是否满足某个属性。使用练习 145 中的 sorted>？来重新使用 check-satisfied 表述 sort> 的测试。

```
; List-of-numbers -> List-of-numbers
; produces a sorted version of l
(define (sort>/bad l)
(list 9 8 7 6 5 4 3 2 1 0))
```

你能拟定一个测试用例来表明 sort>/bad **不是**一个排序函数吗？你能使用 check-satisfied 来拟定这个测试用例吗？

注释 (1) 这里可能会让你惊讶的是，我们定义了一个函数来创建测试。在现实世界中，这一步很常见，有时你确实需要为测试设计函数——连同它们自己的测试等。 (2) 使用 check-satisfied 表述测试有时比使用 check-expect（或其他形式）更容易，而且也更通用一些。当谓词完全描述了函数所有可能输入和输出之间的关系时，计算机科学家称其为规范。第 17.4 节解释了如何完全指定 sort>。

## 练习 187. 设计一个按分数对游戏玩家列表进行排序的程序：

```
(define-struct gp [name score])
; A GamePlayer is a structure:
;   (make-gp String Number)
; interpretation (make-gp p s) represents player p who
; scored a maximum of s points
```

**提示** 拟定一个比较两个 GamePlayer 元素的函数。

## 练习 188. 设计一个按日期对电子邮件列表进行排序的程序：

```
(define-struct email [from date message])
; An Email Message is a structure:
;   (make-email String Number String)
; interpretation (make-email f d m) represents text m
; sent by f, d seconds after the beginning of time
```

还要开发一个按名称对电子邮件消息列表进行排序的程序。要按字母顺序比较两个字符串，请使用 string<?> 原语。

## 练习 189. 以下是函数 search：

```
; Number List-of-numbers -> Boolean
(define (search n alon)
(cond
[(empty? alon) #false]
[else (or (= (first alon) n)
(search n (rest alon)))]))
```

它确定某个数字是否出现在一个数字列表中。该函数可能需要遍历整个列表才能发现感兴趣的数字不在列表中。

开发函数 search-sorted，用于确定一个数字是否出现在排序后的数字列表中。该函数必须利用列表已排序的事实。

## 练习 190. 设计前缀函数 prefixes，它接受一个 1String 列表并生成所有前缀的列表。如果列表 p 和 l 在 p 的所有项上都相同，则列表 p 是 l 的前缀。例如，(list "a" "b" "c") 是其自身以及 (list "a" "b" "c" "d") 的前缀。

设计函数 suffixes，它接受一个 1String 列表并生成所有后缀。如果列表 s 和 l 从末尾开始在 s 的所有项上都相同，则列表 s 是 l 的后缀。例如，(list "b" "c" "d") 是其自身以及 (list "a" "b" "c" "d") 的后缀。

## 11.4 具有泛化作用的辅助函数

偶尔，辅助函数不仅仅是一个小的辅助函数，而是一个更一般问题的解决方案。当问题描述过于狭窄时，需要这样的辅助函数。当程序员执行设计配方的步骤时，他们可能会发现“自然”的解决方案是错误的。对这个有缺陷解决方案的分析可能会提出一个略有不同、但更一般的问题描述，以及一种将一般问题的解决方案应用于原始问题的简单方法。

> 保罗·C·费舍尔提出了这个问题。

我们用以下问题的解决方案来说明这个想法：

## 示例问题 设计一个将多边形添加到给定场景中的函数。

以防你不记得基本的几何（领域）知识，我们添加了一个（简化的）多边形定义：

多边形是一个平面图形，由至少三个点（不在一条直线上）通过三条直线边连接而成。

因此，多边形的一种自然数据表示是 Posn 列表。例如，以下两个定义

```
(define triangle-p
 (list
 (make-posn 20 10)
 (make-posn 20 20)
 (make-posn 30 20)))
(define square-p
 (list
 (make-posn 10 10)
 (make-posn 20 10)
 (make-posn 20 20)
 (make-posn 10 20)))
```

正如名称所言，分别引入了一个三角形和一个正方形。现在你可能会想如何将 '() 或 (list (make-posn 30 40)) 解释为多边形，答案是它们不描述多边形。因为多边形由至少三个点组成，多边形的良好数据表示是包含至少三个 Posn 的列表集合。

遵循非空温度列表（NEList-of-temperatures，第 9.2 章）的数据定义开发过程，为多边形制定数据表示很直接：

```
; A Polygon is one of:
; -- (list Posn Posn Posn)
; -- (cons Posn Polygon)
```

第一个子句说明三个 Posn 的列表是一个多边形，第二个子句说明将一个 Posn cons 到某个现有多边形上会创建另一个多边形。由于这是第一个在子句中使用 list 的数据定义，我们用 cons 将其拼写出来，只是为了确保你看到这种从缩写到长形式的转换：

```
; a Polygon is one of:
; -- (cons Posn (cons Posn (cons Posn '())))
; -- (cons Posn Polygon)
```

重点是，天真选择的数据表示——普通的 Posn 列表——可能无法正确表示预期的信息。在初始探索过程中修订数据定义是正常的；事实上，在设计过程的其余部分，这种修订有时会变得必要。但是，只要你坚持系统的方法，对数据定义的更改就可以自然地传播到设计的其余部分。

第二步需要函数的签名、目的说明和头部。由于问题说明只提到一项任务且未隐含其他任务，我们从一个函数开始：

```
(define MT (empty-scene 50 50))
```

```
; Image Polygon -> Image
; renders the given polygon p into img
(define (render-poly img p)
  img)
```

