

(define (integrity-check.v2 db)
  (local ((define schema (db-schema db))
          ; Row -> Boolean
          ; does row satisfy (I1) and (I2)
          (define (row-integrity-check row)
            (and (= (length row) (length schema))
                 (andmap (lambda (s c) [(second s) c])
                         schema
                         row))))
  (andmap row-integrity-check (db-content db))))

我们知道第 16.2 章中，提升这样的表达式可能会缩短运行完整性检查所需的时间。就像图 100 中 `inf` 的定义一样，`integrity-check` 的原始版本为每个单独的行都从 db 中提取 schema，尽管它显然保持不变。

**术语** Computer scientists speak of “hoisting an expression.” In a similar vein, the `row-integrity-check` function determines the length of db’s schema every single time it is called. The result is always the same. Hence, if we are interested in improving the performance of this function, we can use a `local` definition to name the width of the database content once and for all. 图 139 displays the result of hoisting (`length schema`) out of the `row-integrity-check`. For readability, this final definition also names the content field of db.

(define (integrity-check.v3 db)
  (local ((define schema (db-schema db))
          (define content (db-content db))
          (define width (length schema))
          ; Row -> Boolean
          ; does row satisfy (I1) and (I2)
          (define (row-integrity-check row)
            (and (= (length row) width)
                 (andmap (lambda (s c) [(second s) c])
                         schema
                         row))))
  (andmap row-integrity-check content)))

### 图 139：系统表达式提升的结果

## 投影与选择

程序需要从数据库中提取数据。

一种提取是 *选择* 内容，如第 12.2 章所述。另一种提取生成一个缩减的数据库；它被称为 *投影*。更具体地说，投影通过仅保留给定数据库中的某些列来构建一个数据库。

投影的描述暗示了以下内容：

(define (project db labels) (make-db '() '()))

鉴于投影的复杂性，最好先通过一个示例来讲解。假设我们希望消除图 137 左侧数据库中的 age 列。以下是这种转换在表格中的样子：

| 姓名 字符串 | 年龄 整数 | 在场 布尔值 | 姓名 字符串 | 在场 布尔值 |
|---|---|---|---|---|
| "Alice" | 35 | #true | "Alice" | #true |
| "Bob" | 25 | #false | "Bob" | #false |
| "Carol" | 30 | #true | "Carol" | #true |
| "Dave" | 32 | #false | "Dave" | #false |

一种自然的方式将示例表述为测试，复用图 138：

(define projected-content
   (("Alice" #true)
     ("Bob" #false)
     ("Carol" #true)
     ("Dave" #false)))

(define projected-schema
   (("Name" ,string?) ("Present" ,boolean?)))

(define projected-db
   (make-db projected-schema projected-content))
; Stop! Read this test carefully. What's wrong?
(check-expect (project school-db '("Name" "Present"))
   projected-db)

如果在 DrRacket 中运行上述代码，你会得到错误消息

等式的第一个参数不能是一个函数

在 DrRacket 甚至能判断测试是否成功之前。回想第 14.4 章，函数是无限大的对象，不可能确保两个函数在应用于相同参数时总是产生相同的结果。因此我们削弱了测试用例：

(check-expect
   (db-content (project school-db '("Name" "Present")))
   projected-content)

对于模板，我们再次复用现有的抽象；参见图 140。`local` 表达式定义了两个函数：一个用于与 `filter` 配合以缩小给定数据库的架构，另一个用于与 `map` 配合以精简内容。此外，该函数再次从给定数据库中提取并命名架构和内容。

(define (project db labels)
  (local ((define schema (db-schema db))
           (define content (db-content db))
           ; Spec -> Boolean
           ; does this spec belong to the new schema
           (define (keep? c) ....))
           ; Row -> Row
           ; retains those columns whose name is in
  labels
           (define (row-project row) ....))
     (make-db (filter keep? schema)
              (map row-project content))))

### 图 140：project 的模板

在转到愿望列表之前，让我们退后一步，研究采用两次现有抽象重用的决定。签名告诉我们该函数消费一个结构并产生一个 DB 的元素，因此

(local ((define schema (db-schema db))
         (define content (db-content db))))
(make-db ... schema ...
     ... content ...))

is clearly called for. It is also straightforward to see that the new schema is created from the old schema and the new content from the old content. Furthermore, the purpose statement of project calls for the retention of only those labels that are mentioned in the second argument. Hence, the filter function correctly narrows down the given schema. In contrast, the rows per se stay except that each of them loses some cells. Thus, map is the proper way of processing content.

现在我们可以转向两个辅助函数的设计。keep? 的设计很简单。以下是完整的定义：

(define (keep? c)
  (member? (first c) labels))

该函数作用于 Spec，Spec 将一个 Label 和一个 Predicate 组合在一个列表中。如果前者属于 labels，则保留给定的 Spec。

对于 row-project 的设计，目标是保留 content 中每个 Row 中那些名称属于给定 labels 的 Cell。让我们分析上面的示例。这四行是：

(list "Alice" 35 #true)
(list "Bob"   25 #false)
(list "Carol" 30 #true)
(list "Dave"  32 #false)

这些行中的每一行都与 school-schema 一样长：

(list "Name" "Age" "Present")

架构中的名称决定了给定行中单元格的名称。因此，row-project 必须保留每行的第一个和第三个单元格，因为它们的名称在给定的 labels 中。

由于 Row 是递归定义的，单元格内容及其名称之间的这种匹配过程需要一个递归辅助函数，row-project 可以将其应用于单元格的内容和标签。让我们将其指定为一个愿望：

; Row [List-of Label] -> Row
; retains those cells whose corresponding element
; in names is also in labels
(define (row-filter row names) '(()))
Using this wish, row-project 是一行代码：

(define (row-project row)
  (row-filter row (map first schema)))

map 表达式提取单元格的名称，并将这些名称交给 row-filter 以提取匹配的单元格。

### 练习 405. 设计函数 row-filter。根据 project 的示例为 row-filter 构造示例。

假设 给定的数据库通过完整性检查，这意味着每行的长度都与架构一样长，因此其名称列表也是如此。

图 141 将所有部分组合在一起。函数 project 带有后缀 .v1，因为它需要一些改进。以下练习要求你实现其中一些。

(define (project.v1 db labels)
  (local ((define schema  (db-schema db))
          (define content (db-content db)))

  ; Spec -> Boolean
  ; does this column belong to the new schema
  (define (keep? c)
    (member? (first c) labels))

  ; Row -> Row
  ; retains those columns whose name is in labels
  (define (row-project row)
    (row-filter row (map first schema)))

  ; Row [List-of Label] -> Row
  ; retains those cells whose name is in labels
  (define (row-filter row names)
    (cond
      [(empty? names) '()]
      [else
       (if (member? (first names) labels)
           (cons (first row)
                 (row-filter (rest row) (rest names)))
           (row-filter (rest row) (rest names)))]))

  (make-db (filter keep? schema)
           (map row-project content))))

### 图 141：数据库投影

### 练习 406. row-project 函数为数据库内容中的每一行重新计算标签。结果会随函数调用而有所不同吗？如果没有，请提升该表达式。

### 练习 407. 使用 foldr 重新设计 row-filter。完成后，你可以将 row-project 和 row-filter 合并为一个函数。提示 ISL+ 中的 foldr 函数可能会消耗两个列表并并行处理它们。

最后的观察是，row-project 检查每个单元格中标签在 labels 中的成员资格。对于不同行中同一列的单元格，结果将是相同的。因此，将此计算从函数中提升出来也是有意义的。

