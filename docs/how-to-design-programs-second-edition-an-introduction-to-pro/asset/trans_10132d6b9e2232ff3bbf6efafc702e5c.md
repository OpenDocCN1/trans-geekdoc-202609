

Can DNAprefix 或 DNAdelta 可以简化吗？

**练习 401。** 设计 sexp=？，一个用于判断两个 S-表达式是否相等的函数。为方便起见，这里以简化形式给出数据定义：

```
; An S-expr (S-expression) is one of:
; -- Atom
; -- [List-of S-expr]
;
; An Atom is one of:
; -- Number
; -- String
; -- Symbol
```

每当你使用 check-expect 时，它会使用类似 sexp=? 的函数来检查两个任意值是否相等。如果不相等，检查就会失败，check-expect 会据此报告。

**练习 402。** 重读练习 354。解释我们提示你先将给定表达式视为原子值的理由。

## 23.7 项目：数据库

许多软件应用程序使用数据库来跟踪数据。粗略地说，数据库是一个带有明确说明的组织规则的表格。前者是 *内容*；后者称为 *模式*。图 137 显示了两个示例。每个表由两部分组成：线上方的模式和线下方的内容。

![](img/19fbe4068996ced0ce42cec7fb82a834_741_0.png)

图 137：作为表格的数据库

*本章汇集了本书四个部分的知识。*

让我们关注左边的表格。它有三列和四行。每列都附带一条两部分的规则：

- 1. 最左边一列的规则规定该列的标签为“Name”，且该列中的每个数据均为 String；
- 2. 中间一列标记为“Age”，包含 Integer；以及
- 3. 最右边一列的标签为“Present”；其值为 Boolean。

停顿！用同样的方式解释右边的表格。

计算机科学家将这些表视为 *关系*。模式引入了术语，用于引用关系中的列以及行中的单个单元格。每一行关联固定数量的值；所有行的集合构成整个关系。按照这种术语，图 137 中左侧表格的第一行将 "Alice" 与 35 和 #true 关联。此外，行中的第一个单元格称为“Name”单元格，第二个称为“Age”单元格，第三个称为“Present”单元格。

在本节中，我们通过结构体和列表来表示数据库：

```
(define-struct db [schema content])
; A DB is a structure: (make-db Schema Content)
; A Schema is a [List-of Spec]
; A Spec is a [List Label Predicate]
; A Label is a String
; A Predicate is a [Any -> Boolean]

; A (piece of) Content is a [List-of Row]
; A Row is a [List-of Cell]
; A Cell is Any
; **constraint** cells do not contain functions

; **integrity constraint** In (make-db sch con),
; for every row in con,
; (I1) its length is the same as sch's, and
; (I2) its ith Cell satisfies the ith Predicate in sch
```

停顿！将图 137 中的数据库翻译成所选的数据表示形式。注意，表格中的内容已经使用了 ISL+ 数据。

图 138 展示了如何在 DB 中表示这两个表格。其左侧表示图 137 左侧表格的模式、内容和数据库；其右侧对应右侧表格。为简洁起见，示例使用了准引用和取消引用符号。请回顾，它允许在其他情况下被引用的列表中包含诸如 boolean? 之类的值。如果你对这种符号感到不适，请使用 list 重新编写这些示例。

```
(define school-schema
 '(("Name" ,string?)
   ("Age" ,integer?)
   ("Present" ,boolean?)))

(define school-content
 '(("Alice" 35 #true)
   ("Bob" 25 #false)
   ("Carol" 30 #true)
   ("Dave" 32 #false)))

(define school-db
 (make-db school-schema
   school-content))
```

```
(define presence-schema
 '(("Present" ,boolean?)
   ("Description" ,string?)))

(define presence-content
 '((#true "presence")
   (#false "absence")))

(define presence-db
 (make-db presence-schema
   presence-content))
```

图 138：作为 ISL+ 数据的数据库

**练习 403。** Spec 将 Label 和 Predicate 组合成一个列表。虽然这可以接受，但此选择违背了我们针对固定数量信息片段使用结构体类型的准则。

这里是替代的数据表示形式：

```
(define-struct spec [label predicate])
; Spec is a structure: (make-spec Label Predicate)
```

使用此替代定义来表示图 137 中的数据库。

### 完整性检查

数据库的使用高度依赖于其完整性。这里的“完整性”指的是数据定义中的约束 (I1) 和 (I2)。检查数据库完整性显然是一个函数的任务：

```
; DB -> Boolean
; do all rows in db satisfy (I1) and (I2)
```

```
(check-expect (integrity-check school-db) #true)
(check-expect (integrity-check presence-db) #true)
```

```
(define (integrity-check db)
  #false)
```

两个约束的表述表明，某个函数必须对给定数据库内容中的每一行都产生 #true。将此想法用代码表达，需要对 db 的内容使用 andmap：

```
(define (integrity-check db)
  (local (; Row -> Boolean
          (define (row-integrity-check row)
            ...))
    (andmap row-integrity-check (db-content db))))
```

遵循使用现有抽象的设计食谱，模板通过局部定义引入辅助函数。

row-integrity-check 的设计始于以下内容：

```
; Row -> Boolean
; does row satisfy (I1) and (I2)
(define (row-integrity-check row)
  #false)
```

与往常一样，制定目的说明的目的是理解问题。这里指出，该函数检查 **两个** 条件。当涉及两个任务时，我们的设计准则要求编写函数并组合它们的结果：

```
(and (length-of-row-check row)
     (check-every-cell row))
```

将这些函数添加到你的愿望清单中；它们的名称传达了它们的目的。

在设计这些函数之前，我们必须思考是否可以组合现有的原语操作来计算所需的值。例如，我们知道 `(length row)` 计算 row 中有多少个单元格。再进一步，我们显然希望：

```
(= (length row) (length (db-schema db)))
```

此条件检查 row 的长度是否等于 db 模式的长度。

同样，check-every-cell 要求检查某个函数是否对行中的每个单元格都产生 #true。再一次，看起来可能需要 andmap：

```
(andmap cell-integrity-check row)
```

cell-integrity-check 的目的显然是检查约束 (I2)，即：

检查“第 i 个单元格是否满足 db 模式中的第 i 个谓词。”

现在我们卡住了，因为这个目的说明涉及给定单元格在 row 中的相对位置。然而，andmap 的要点是将 cell-integrity-check 一致地应用于每个单元格。

当你卡住时，必须通过示例来推演。对于辅助函数或局部函数，最好从主函数的示例中推导这些示例。integrity-check 的第一个示例断言 school-content 满足完整性约束。显然，school-content 中的所有行都与 school-schema 具有相同的长度。问题是，为什么诸如下面这样的行：

```
(list "Alice" 35 #true)
```

满足对应模式中的谓词：

```
(list (list "Name" string?) (list "Age" integer?) (list "Present" boolean?))
```

答案是，将三个谓词分别应用到相应单元格的所有三次应用均产生 true：

```
> (string? "Alice")
#true
> (integer? 35)
#true
> (boolean? #true)
#true
```

由此，只需一小步就可以看出，该函数必须并行处理这两个列表——db 的模式和给定的 row。

**练习 404。** 设计函数 andmap2。它接收一个从两个值到 Boolean 的函数 f 以及两个长度相同的列表。其结果也是一个 Boolean。具体来说，它将 f 应用于两个列表中对应值的配对，如果 f 始终产生 #true，则 andmap2 也产生 #true。否则，andmap2 产生 #false。简而言之，andmap2 类似于 andmap，但适用于两个列表。

停顿！在继续阅读前，先解决练习 404。

如果在 ISL+ 中有 andmap2，那么检查 row 上的第二个条件将变得简单：

```
(andmap2 (lambda (s c) [(second s) c])
  (db-schema db)
  row)
```

给定的函数接收 db 模式中的一个 Spec s，提取第二个位置的谓词，并将其应用于给定的单元格 c。无论谓词返回什么，都是 lambda 函数的结果。

再次停顿！解释 [(second s) c]。

事实证明，ISL+ 中的 andmap 已经类似于 andmap2：

```
(define (integrity-check db)
  (local (; Row -> Boolean
          ; does row satisfy (I1) and (I2)
          (define (row-integrity-check row)
            (and (= (length row)
                    (length (db-schema db)))
                 (andmap (lambda (s c) [(second s) c])
                         (db-schema db)
                         row))))
        (andmap row-integrity-check (db-content db))))
```

最后一次停顿！开发一个 integrity-check 必须失败的测试。

### 表达式提升说明

我们对 integrity-check 的定义存在多个问题，有些显而易见，有些不明显。显然，该函数提取了两次 db 的模式。借助现有的局部定义，可以引入一个定义来避免这种重复：

