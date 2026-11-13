

在这个时代，这只是一个练习。

## 练习 232

从以下表达式中消除 `quasiquote` 和 `unquote`，使它们改用 `list` 编写：

- `(1 "a" 2 #false 3 "c")`

- 这种表格状图形：

```
`(("alan" ,(* 2 500))
 ("barb" 2000)
 (,(string-append "carl" " , the great") 1500)
 ("dawn" 2300))`
```

- 和这个第二个网页：

```
`(html
 (head
  (title ,title))
 (body
  (h1 ,title)
  (p "A second web page")))`
```

其中 `(define title "ratings")`。

同时写下这些表达式产生的嵌套列表。

## 取消引用拼接

当准引用在短写形式的展开过程中遇到 `unquote` 时，两者相互抵消：

```
`(tr
 ,(make-row
  '(3 4 5)))
 is short for
 (list 'tr
  (make-row
   (list 3 4 5)))`
```

是简写形式

```
(list 'tr
  (make-row
   (list 3 4 5)))
```

因此，`make-row` 产生的任何内容都成为列表的第二项。特别是，如果 `make-row` 产生一个列表，这个列表就成为列表的第二项。如果 `make-row` 将给定的数字列表转换为字符串列表，那么结果是

```
(list 'tr (list "3" "4" "5"))
```

然而，在某些情况下，我们可能希望将这样的嵌套列表拼接到外层列表中，因此对于我们的运行示例，我们将得到

```
(list 'tr "3" "4" "5")
```

解决这个小问题的一种方法是求助于 cons。也就是说，将 cons 与 quote、准引用和 unquote 混合使用。毕竟，所有这些字符只是 consed 列表的简写形式。以下是我们示例中获得所需结果所需的内容：

```
(cons 'tr (make-row '(3 4 5)))
```

让自己相信结果是 (list 'tr "3" "4" "5")。

由于这种情况在实践中非常常见，BSL+ 支持另一种用于列表创建的简写机制：,@，也称为关键字形式的 unquote-splicing。使用此形式，可以轻松地将嵌套列表拼接到周围列表中。例如，

```
`(tr ,@(make-row '(3 4 5)))
```

转换为

```
(cons 'tr (make-row '(3 4 5)))
```

这正是我们示例所需要的。

现在考虑在我们的嵌套列表表示中创建 HTML 表的问题。这里是一个有两行、每行四个单元格的表：

```
' (table ((border "1"))
  (tr (td "1") (td "2") (td "3") (td "4"))
  (tr (td "2.8") (td "-1.1") (td "3.4") (td "1.3")))
```

第一个嵌套列表告诉 HTML 在表格中每个单元格周围绘制一个细边框；其他两个嵌套列表分别表示一行。

在实践中，你希望创建具有任意宽行和任意多行的此类表格。目前，我们只处理第一个问题，这需要一个将数字列表转换为 HTML 行的函数：

```
; List-of-numbers -> ... nested list ...
; creates a row for an HTML table from 1
(define (make-row l)
 (cond
  [(empty? l) '()]
  [else (cons (make-cell (first l))
              (make-row (rest l)))]))
```

```
; Number -> ... nested list ...
; creates a cell for an HTML table from a number
(define (make-cell n)
 `(td ,(number->string n))))
```

与其添加示例，不如在 DrRacket 的交互区中探索这些函数的行为：

```
> (make-cell 2)
(list 'td "2")
> (make-row '(1 2))
(list (list 'td "1") (list 'td "2"))
```

这些交互显示了表示单元格和行的列表的创建。

要将这些行列表转换为 HTML 表表示中的实际行，我们需要将它们拼接到以 'tr 开头的列表中：

```
; List-of-numbers List-of-numbers -> ... nested list ...
; creates an HTML table from two lists of numbers
(define (make-table row1 row2)
 `(table ((border "1"))
   (tr ,@(make-row row1))
   (tr ,@(make-row row2)))))
```

此函数消耗两个数字列表并创建 HTML 表表示。使用 make-row，它将列表转换为单元格表示的列表。使用 ,@，这些列表被拼接到表模板中：

```
> (make-table '(1 2 3 4 5) '(3.5 2.8 -1.1 3.4 1.3))
(list 'table (list (list 'border "1")) '....)
```

对 make-table 的这一应用说明了人们编写程序创建网页而不是手动制作网页的另一个原因。

> 这些点 *不是* 输出的一部分。

## 练习 233

开发仅使用 list 并产生相同值的以下表达式的替代方案：

- `(0,@'(1 2 3) 4)`

- 这种表格状图形：

```
`(("alan" ,(* 2 500))
 ("barb" 2000)
 (,(string-append "carl" " , the great") 1500)
 ("dawn" 2300))`
```

- 和这个第三个网页：

```
`(html
 (body
  (table ((border "1"))
  (tr ((width "200"))
  ,@(make-row '(1 2)))
  (tr ((width "200"))
  ,@(make-row '(99 65))))))`
```

其中 make-row 是上面的函数。

使用 check-expect 检查你的工作。

## 练习 234

创建函数 make-ranking，它消耗一个排名歌曲标题列表并产生 HTML 表的列表表示。考虑此示例：

```
(define one-list
  '("Asia: Heat of the Moment"
    "U2: One"
    "The White Stripes: Seven Nation Army"))
```

如果将 make-ranking 应用于 one-list 并在浏览器中显示生成的网页，你会看到类似于图 85 中的屏幕截图。

![](img/19fbe4068996ced0ce42cec7fb82a834_492_0.png)

图 85：使用 BSL+ 生成的网页

**提示** 虽然你可以设计一个从字符串列表中确定排名的函数，但我们希望你专注于表格的创建。因此，我们提供以下函数：

```
(define (ranking los)
  (reverse (add-ranks (reverse los))))

(define (add-ranks los)
  (cond
    [(empty? los) '()]
    [else (cons (list (length los) (first los))
                (add-ranks (rest los)))]))
```

在使用这些函数之前，为它们配备签名和目的说明。然后在 DrRacket 的交互区中探索它们的工作原理。第 VI 部分扩展了设计方法，提供了一种创建比 ranking 和 add-ranks 更简单的计算排名的函数的方法。▪

## 计划研究

![](img/19fbe4068996ced0ce42cec7fb82a834_494_0.png)

## III

### 摘要

我们的许多数据定义和函数定义看起来相似。例如，字符串列表的定义与数字列表的定义仅在两个地方不同：数据类的名称以及单词“String”和“Number”。同样，在字符串列表中查找特定字符串的函数与在数字列表中查找特定数字的函数几乎无法区分。

经验表明，这种相似性是有问题的。相似性之所以出现，是因为程序员——在身体上或在脑海中——复制代码。当程序员面临一个与另一个问题大致相似的问题时，他们会复制解决方案并修改新副本以解决新问题。你会在“真实”编程环境以及电子表格和数学建模的世界中发现这种行为。然而，复制代码意味着程序员也会复制错误，并且相同的修复可能需要应用到许多副本中。这也意味着，当底层数据定义被修订或扩展时，必须找到所有代码副本并以相应的方式修改它们。这个过程既昂贵又容易出错，给编程团队带来不必要的成本。

优秀的程序员会尽可能在编程语言允许的范围内消除相似性。“消除”意味着程序员写下程序的初稿，发现相似性（和其他问题），并摆脱它们。对于最后一步，他们要么进行抽象，要么使用现有的（抽象）函数。通常需要多次迭代这个过程才能使程序达到满意的状态。

> 程序就像一篇文章。第一个版本是草稿，而草稿需要编辑。

本部分的前半部分展示了如何在函数和数据定义上抽象相似性。程序员也将此过程的结果称为抽象，混淆了过程名称及其结果。本部分的后半部分是关于使用现有抽象和新语言元素来促进这一过程。虽然本部分的示例取自列表领域，但

