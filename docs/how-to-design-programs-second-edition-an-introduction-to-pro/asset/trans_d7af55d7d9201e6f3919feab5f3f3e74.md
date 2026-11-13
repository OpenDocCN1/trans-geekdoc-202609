

(check-expect
(wage*.v2
(cons (make-work "Robby" 11.95 39) '(()))
(cons (* 11.95 39) '(())))

这只是为了让你为其他编程语言做好准备。再说，以这种风格写下示例也意味着你确实已经弄清楚如何计算工资了。结束

从这里开始，我们进入模板的开发。如果你使用模板问题，你很快就能得到这样多：

```
(define (wage*.v2 an-low)
(cond
[(empty? an-low) ...]
[(cons? an-low)
(... (first an-low) ...
... (wage*.v2 (rest an-low)) ...)]))
```

因为数据定义由两个子句组成，因为它在第一个子句中引入了 '()，在第二个子句中引入了 consed 结构，等等。但你也意识到，你对输入的了解比这个模板表达的还要多。例如，你知道 (first an-low) 从给定列表中提取一个包含三个字段的结构。这似乎暗示在模板中添加三个更多的表达式：

```
(define (wage*.v2 an-low)
(cond
[(empty? an-low) ...]
[(cons? an-low)
(... (first an-low) ...
... ... (work-employee (first an-low)) ...
... ... (work-rate (first an-low)) ...
... ... (work-hours (first an-low)) ...
(wage*.v2 (rest an-low)) ...)]))
```

此模板列出了所有可能感兴趣的数据。

在这里，我们采用不同的策略。具体来说，我们建议在你为引用其他数据定义的数据定义开发模板时，创建并引用一个单独的函数模板：

```
(define (wage*.v2 an-low)
 (cond
  [(empty? an-low) ...]
  [(cons? an-low)
   (... (for-work (first an-low))
    ... (wage*.v2 (rest an-low)) ...)]))
```

```
; Work -> ???
; a template for processing elements of Work
(define (for-work w)
  (... (work-employee w) ...
   ... (work-rate w) ...
   ... (work-hours w) ...)))
```

将模板拆分后，工作会自然地划分到函数中和函数之间；它们都不会变得太大，并且都与特定的数据定义相关联。

最后，你准备好编程了。和往常一样，你从看起来简单的情况开始，即这里的第一个 cond 行。如果将 wage*.v2 应用于 '()，你期望得到 '() 返回，这就解决了。接下来，你移到第二行，并提醒自己这些表达式计算什么：

- 1. `(first an-low)` 从列表中提取第一个工作结构；
- 2. `(for-work ...)` 表示你希望设计一个处理工作结构的函数；
- 3. `(rest an-low)` 提取给定列表的其余部分；以及
- 4. `(wage*.v2 (rest an-low))` 根据函数的目的说明，确定除第一个工作记录之外的所有工作记录的工资列表。

如果你在这里卡住了，请使用图 54 中的表格方法。

如果你完全理解，你会发现将这两个表达式 cons 在一起就足够了：

```
... (cons (for-work (first an-low))
           (wage*.v2 (rest an-low))) ...
```

假设 for-work 计算第一个工作记录的工资。简而言之，你已经通过将另一个条目添加到你的函数愿望列表中来完成该函数。

由于 for-work 只是一个占位符名称，而且对于这个函数来说是个糟糕的名称，让我们将该函数命名为 wage.v2，并写下它的完整愿望列表条目：

```
; Work -> Number
; computes the wage for the given work record w
(define (wage.v2 w)
  0)
```

这种类型函数的设计在第 I 部分中已详细介绍，因此此处不需要任何额外说明。图 65 显示了开发 wage 和 wage*.v2 的最终结果。

```
; Low -> List-of-numbers
; computes the weekly wages for all weekly work records
(check-expect
 (wage*.v2 (cons (make-work "Robby" 11.95 39) '()))
 (cons (* 11.95 39) '()))

(define (wage*.v2 an-low)
  (cond
    [(empty? an-low) '()]
    [(cons? an-low) (cons (wage.v2 (first an-low))
                          (wage*.v2 (rest an-low)))])

; Work -> Number
; computes the wage for the given work record w
(define (wage.v2 w)
  (* (work-rate w) (work-hours w)))
```

## 图 65：从工作记录计算工资

### 练习 166.

wage*.v2 函数使用一份工作记录列表并生成一份数字列表。当然，函数也可能生成结构列表。

为支票开发一种数据表示。假设支票包含两个独特的信息片段：员工姓名和金额。然后设计函数 wage*.v3。它使用一份工作记录列表，并从中计算出一份支票列表，每条记录一张。

实际上，支票还包含员工编号。为员工信息开发一种数据表示，并更改工作记录的数据定义，使其使用员工信息而不是仅用字符串表示员工姓名。同样，更改支票的数据表示，使其也包含员工的姓名和编号。最后，设计 wage*.v4，一个将修订后的工作记录列表映射到修订后的支票列表的函数。

### 关于迭代细化的说明

本练习演示了任务的 *迭代细化*。我们没有使用包含所有相关信息的数据表示，而是从支票的简化表示开始，逐步使表示变得现实。对于这个简单的程序，细化是大材小用；以后我们会遇到这种情况，迭代细化不仅是一种选择，更是一种必要。

### 练习 167.

设计函数 sum，它使用一份 Posns 列表并生成所有 x 坐标的总和。

### 练习 168.

设计函数 translate。它使用并生成 Posns 列表。对于前者中的每个 `(make-posn x y)`，后者包含 `(make-posn x (+ y 1))`。我们从几何学中借用“translate”一词，在几何学中，沿直线将点移动固定距离称为 *平移*。

### 练习 169.

设计函数 legal。与练习 168 中的 translate 类似，该函数使用并生成一份 Posns 列表。结果包含所有 x 坐标在 0 到 100 之间且 y 坐标在 0 到 200 之间的 Posns。

### 练习 170.

以下是表示电话号码的一种方式：

```
(define-struct phone [area switch four])
; A Phone is a structure:
; (make-phone Three Three Four)
; A Three is a Number between 100 and 999.
; A Four is a Number between 1000 and 9999.
```

设计函数 replace。它使用并生成一份 Phones 列表。它将所有出现的区号 713 替换为 281。

## 10.3 列表嵌套列表、文件

第 2 章介绍了 read-file，这是一个将整个文本文件作为字符串读取的函数。换句话说，read-file 的创建者选择将文本文件表示为字符串，该函数为特定文件（由名称指定）创建数据表示。然而，文本文件并不是简单的长文本或字符串。它们被组织成行和单词、行和单元格，以及许多其他方式。简而言之，将文件内容表示为普通字符串在偶尔可能有效，但通常是个糟糕的选择。

```
Add (require 2htdp/batch-io) to your definitions area.
```

为具体起见，请查看图 66 中的示例文件。它包含 Piet Hein 的一首诗，由许多行和单词组成。当你使用程序时

```
(read-file "ttt.txt")
```

![](img/19fbe4068996ced0ce42cec7fb82a834_385_0.png)

图 66：事情需要时间

要将此文件转换为 BSL 字符串，你会得到这个：

```
"TTT \n \n Put up in a place\where ...."
```

其中字符串内的 "\n" 表示换行符。

正如你可能猜到的那样，省略号实际上并不是结果的一部分。

虽然确实可以使用字符串的原始操作（例如 explode）拆分此字符串，但大多数编程语言——包括 BSL——都支持多种不同的文件表示，以及从现有文件创建此类表示的函数：

- 表示此文件的一种方式是将其作为行列表，其中每行表示为一个字符串：

```
(cons "TTT"
  (cons ""
    (cons "Put up in a place"
      (cons ...
        '())))))
```

这里列表的第二个项目是空字符串，因为文件包含一个空行。

- 另一种方式是使用单词列表，同样每个单词表示为一个字符串：

```
(cons "TTT"
  (cons "Put"
    (cons "up"
      (cons "in"
        (cons ...
          '())))))
```

注意，使用这种表示时，空的第二行消失了。毕竟，空行上没有单词。

- 第三种表示依赖于单词的列表的列表：

