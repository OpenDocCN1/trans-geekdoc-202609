
and an interval that contains both roots.

**练习 448。** 对于所有满足假设的（连续）f、left 和 right，`find-root` 算法都会终止。为什么？制定一个终止论证。

**提示** 假设 `find-root` 的参数描述了大小为 S1 的区间。在对 `find-root` 的第一次和第二次递归调用中，`left` 和 `right` 之间的距离有多大？经过多少步后，(- right left) 会小于或等于 ε？

**练习 449。** 如图 159 所示，`find-root` 为每个边界值计算两次 f 的值以生成下一个区间。使用 `local` 来避免这种重复计算。

此外，`find-root` 在跨递归调用时会重新计算边界值。例如，(`find-root` f `left` `right`) 计算 (`f` `left`)，如果 [`left`,`mid`] 被选为下一个区间，`find-root` 会再次计算 (`f` `left`)。引入一个辅助函数，它类似于 `find-root`，但在每个递归阶段不仅消耗 `left` 和 `right`，还消耗 (`f` `left`) 和 (`f` `right`)。

这种设计最多避免了多少次 (`f` `left`) 的重新计算？

**注意** 此辅助函数的两个附加参数在每个递归阶段都会变化，但这种变化与数值参数的变化相关。这些参数称为*累加器*，是第 VI 部分的主题。

**练习 450。** 如果每当 (< a b) 成立时 (<= (f a) (f b)) 也成立，则函数 f 是*单调递增*的。在假定给定函数不仅连续而且单调递增的情况下，简化 `find-root`。

**练习 451。** 表是一个包含两个字段的结构：自然数 VL 和一个函数 array，该函数消耗自然数，并对 0 到 VL 之间（不含 VL）的自然数产生答案：

```
(define-struct table [length array])
; A Table is a structure:
;   (make-table N [N -> Number])
```

> 许多编程语言，包括 Racket，都支持数组和向量，它们与表类似。

由于这种数据结构有些不同寻常，用示例来说明它至关重要：

示例：

```
(define table1 (make-table 3 (lambda (i) i)))
```

```
; N -> Number
(define (a2 i)
 (if (= i 0)
  pi
  (error "table2 is not defined for i != 0")))
```

```
(define table2 (make-table 1 a2))
```

这里 table1 的 array 函数定义的输入比其 length 字段允许的更多；table2 只针对一个输入（即 0）定义。最后，我们还定义了一个用于在表中查找值的有用函数：

```
; Table N -> Number
; looks up the ith value in array of t
(define (table-ref t i)
 ((table-array t) i))
```

表 t 的根是 (table-array t) 中接近 0 的一个数。根索引是一个自然数 i，使得 (table-ref t i) 是表 t 的根。如果 (table-ref t 0) 小于 (table-ref t 1)，(table-ref t 1) 小于 (table-ref t 2)，依此类推，则表 t 是单调递增的。

设计 find-linear。该函数消耗一个单调递增的表，并找到表中根的最小索引。使用 N 的结构化设计模板，从 0 到 1、2，依此类推，直到给定表的数组长度。这种根查找过程通常称为线性搜索。

设计 find-binary，它也查找单调递增表中根的最小索引，但使用生成递归来实现。与普通二分查找类似，该算法将区间缩小到最小可能的大小，然后选择索引。不要忘记制定终止论证。

提示 关键问题是表索引是自然数，而不是普通数字。因此，find 的区间边界参数必须是自然数。考虑这一观察如何改变 (1) 可平凡求解的问题实例的性质，(2) 中点计算，(3) 以及生成下一个区间的决定。为了具体化，想象一个有 1024 个槽位且根位于 1023 的表。在 find-linear 和 find-binary 中分别需要多少次 find 调用？■

## 27.3 一窥解析

如前文第 20 章所述，计算机自带文件，提供了一种永久内存形式。从我们的角度来看，文件只是 1Strings 的列表，不过被一个特殊字符串打断：

```
; A File is one of:
; -- '()
; -- (cons "\\n" File)
; -- (cons 1String File)
; interpretation represents the content of a file
; "\\n" is the newline character
```

> 确切的约定因操作系统而异，但就我们的目的而言，这无关紧要。

其理念是将 Files 分解为行，其中 "\\n" 表示所谓的换行符，指示一行的结束。在继续之前，我们也引入行的概念：

```
; A Line is a [List-of 1String].
```

许多函数需要将文件作为行列表来处理。read-lines（来自 2htdp/batch-io 库）就是其中之一。具体来说，该函数将文件

```
(list
 "h" "o" "w" " " "a" "r" "e" " " "y" "o" "u" "\\n"
 "d" "o" "i" "n" "g" "?" "\\n"
 "a" "n" "y" " " "p" "r" "o" "g" "r" "e" "s" "s" "?")
```

转换为一个包含三行的列表：

```
(list
 (list "h" "o" "w" " " "a" "r" "e" " " "y" "o" "u")
 (list "d" "o" "i" "n" "g" "?")
 (list "a" "n" "y" " " "p" "r" "o" "g" "r" "e"
 "s" "s" "?"))
```

同样，文件

```
(list "a" "b" "c" "\\n" "d" "e" "\\n" "f" "g" "h" "\\n")
```

也对应于一个包含三行的列表：

```
(list (list "a" "b" "c")
 (list "d" "e")
 (list "f" "g" "h"))
```

停止！针对这三种情况：'()、(list "\\n") 和 (list "\\n" "\\n")，行列表表示分别是什么？这些示例为什么是重要的测试用例？

将 1Strings 序列转换为行列表的问题称为解析问题。许多编程语言提供从文件中检索行、单词、数字和其他所谓标记的函数。但即使如此，程序通常还需要对这些标记进行进一步解析。本节展示了一种解析技术的概要。然而，解析非常复杂，而且对于创建完整的软件应用程序至关重要，以至于大多数本科课程都至少开设一门解析课程。所以不要以为掌握本节内容后，你就能妥善处理实际解析问题。

我们首先列出显而易见的内容——一个签名、一个目的说明、上面的示例之一和一个头部——用于将 File 转换为 Line 列表的函数：

```
; File -> [List-of Line]
; converts a file into a list of lines

(check-expect (file->list-of-lines
   (list "a" "b" "c" "\\n"
      "d" "e" "\\n"
      "f" "g" "h" "\\n"))
   (list (list "a" "b" "c")
      (list "d" "e")
      (list "f" "g" "h"))))

(define (file->list-of-lines afile) '())
```

基于我们对第 26.1 节的经验，描述解析过程也很容易：

- 1. 如果文件是 '()，问题可以平凡求解。
- 2. 在这种情况下，文件不包含任何行。
- 3. 否则，文件至少包含一个 "\\n" 或其他 1String。这些项目（一直到包括第一个 "\\n"，如果有的话）必须与 File 的其余部分分开。其余部分是 file->list-of-lines 可以解决的同类新问题。
- 4. 然后只需将初始段作为单一行 cons 到由 File 其余部分产生的 Lines 列表中即可。

这四个问题暗示了生成递归函数模板的直接实例化。由于从文件中分离初始段需要扫描任意长的 1Strings 列表，我们将两个辅助函数列入愿望清单：first-line，它收集所有 1Strings 直到（但不包括）第一个 "\\n" 出现或列表末尾；以及 remove-first-line，它移除 first-line 收集的完全相同的项目。

到这里，创建程序的其余部分就很容易了。在 file->list-of-lines 中，第一个子句的答案必须是 '()，因为空文件不包含
