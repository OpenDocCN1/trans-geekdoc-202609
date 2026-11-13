
## 22.1 将 XML 作为 S 表达式

最基本的 XML 数据片段如下：

```xml
<machine> </machine>
```

它被称为*元素*，“machine”是元素的名称。元素的两个部分就像括号，界定了元素的*内容*。当两部分之间除了空白字符外没有内容时，XML 允许使用简写：

```xml
<machine />
```

但，就我们在此关心的范围而言，这种简写与明确括号化的版本等价。

> *Racket 的 xml 库同时使用结构和 S 表达式来表示 XML。*

从 S 表达式的角度看，XML 元素是一对带有**名称**的括号，用于包围一些内容。的确，用 S 表达式表示上述内容非常自然：

```lisp
'(machine)
```

此数据片段拥有开括号和闭括号，并留有用于嵌入内容的空间。

下面是一段带有内容的 XML 数据：

```xml
<machine><action ></machine>
```

请记住，`<action />` 部分是一种简写，意味着我们实际上是在看这段数据：

```xml
<machine><action></action></machine>
```

一般而言，XML 元素的内容是一系列 XML 元素：

```xml
<machine><action /></action><action ></machine>
```

停止！在继续之前，先展开 `<action />` 的简写。

S 表达式表示仍然很简单。这是第一个：

```lisp
'(machine (action))
```

这是第二个的表示：

```lisp
'(machine (action) (action) (action))
```

当你看到一段 XML 数据，其内容为三个 <action /> 元素的序列时，你会意识到可能希望将这些元素相互区分。为此，XML 元素带有属性。例如：

```xml
<machine initial="red"/></machine>
```

这是“machine”元素，配备了一个名为“initial”、值为“red”（带字符串引号）的属性。

下面是一个复杂的 XML 元素，其中嵌套元素也带有属性：

```xml
<machine initial="red">
    <action state="red" next="green" />
    <action state="green" next="yellow" />
    <action state="yellow" next="red" />
</machine>
```

我们使用空格、缩进和换行符来使元素易于阅读，但这些空白字符在此处的 XML 数据中没有任何含义。

> XML 比 S 表达式年轻 40 年。

自然，这些“machine”元素的 S 表达式与其 XML 表亲非常相似：

```scheme
'(machine ((initial "red")))
```

要为元素添加属性，我们使用一个列表的列表，其中后者中的每个列表包含两个项目：一个符号和一个字符串。符号表示属性的名称，字符串表示其值。这一想法自然也适用于复杂形式的 XML 数据：

```scheme
'(machine ((initial "red"))
 (action ((state "red") (next "green")))
 (action ((state "green") (next "yellow")))
 (action ((state "yellow") (next "red"))))
```

目前请注意，属性由两个开括号标记，而其余的（XML 元素表示）列表有一个开括号。

你可能还记得间奏曲 2 中的想法，它使用 S 表达式来表示 XHTML，这是 XML 的一种特殊方言。特别是，间奏曲展示了程序员如何轻松地编写非平凡的 XML 数据，甚至使用反引号和取消引号来编写 XML 表示的模板。当然，第 21.1 章指出，你需要一个解析器来确定给定的 S 表达式是否是 XML 数据的表示，而解析器是一种复杂且不寻常的函数。

尽管如此，我们选择基于 S 表达式的 XML 表示，以便在实践中展示这一古老而富有诗意的想法的实用性。我们循序渐进地制定数据定义，运用迭代细化。下面是第一次尝试：

```scheme
; An Xexpr.v0 (short for X-expression) is a one-item list:
;   (cons Symbol '())
```

这是本节开头提到的“带名称的括号”想法。为该元素表示添加内容很简单：

```scheme
; An Xexpr.v1 is a list:
;   (cons Symbol [List-of Xexpr.v1])
```

符号名称成为列表的第一个项目，列表的其余部分由 XML 元素代表组成。

最后的细化步骤是添加属性。由于 XML 元素中的属性是可选的，修订后的数据定义包含两个子句：

```scheme
; An Xexpr.v2 is a list:
; -- (cons Symbol Body)
; -- (cons Symbol (cons [List-of Attribute] Body))
; where Body is short for [List-of Xexpr.v2]
; An Attribute is a list of two items:
;  (cons Symbol (cons String '()))
```

**练习 363。** Xexpr.v2 的所有元素都以符号开头，但有些后面跟着属性列表，有些后面跟着仅包含 Xexpr.v2 的列表。重新表述 Xexpr.v2 的定义，以分离共同的开头并突出不同的结尾。

从 Xexpr.v2 中消除 List-of 的使用。

**练习 364。** 将此 XML 数据表示为 Xexpr.v2 元素：

- 1.<transition from="seen-e" to="seen-f" />
- 2.<ul><li><word /><word ><li><li><word ><li></ul>

哪个可以在 Xexpr.v0 或 Xexpr.v1 中表示？

**练习 365。** 将以下 Xexpr.v2 元素解释为 XML 数据：

- 1. '(server ((name "example.org")))
- 2. '(carcas (board (grass)) (player ((name "sam"))))
- 3. '(start)

哪些是 Xexpr.v0 或 Xexpr.v1 的元素？

粗略地说，X 表达式通过列表模拟结构。这种模拟对程序员来说很方便；它要求最少的键盘敲击。例如，如果 X 表达式不带属性列表，则直接省略。这种数据表示选择在手动编写此类表达式与自动处理它们之间存在权衡。处理后者问题的最佳方法是提供使 X 表达式看起来像结构的函数，尤其是访问准字段的函数：

- *xexpr-name*，它提取元素表示的标签；
- *xexpr-attr*，它提取属性列表；以及
- *xexpr-content*，它提取内容元素列表。

一旦有了这些函数，我们就可以使用列表来表示 XML，但它们表现得就像结构类型的实例一样。

这些函数解析 S 表达式，而解析器设计起来很棘手。因此，让我们仔细设计它们，先从一些数据示例开始：

```scheme
(define a0 '((initial "X")))
(define e0 '(machine))
(define e1 `(machine ,a0))
(define e2 '(machine (action)))
(define e3 '(machine () (action)))
(define e4 `(machine ,a0 (action) (action)))
```

第一个定义引入了一个属性列表，该列表在构建 X 表达式时被重复使用两次。e0 的定义提醒我们，X 表达式可能既不带属性也不带内容。你应该能够解释为什么 e2 和 e3 基本上是等价的。

接下来，我们制定签名、目的说明和标题：

```scheme
; Xexpr.v2 -> [List-of Attribute]
; retrieves the list of attributes of xe
(define (xexpr-attr xe) '())
```

这里我们专注于 xexpr-attr；另外两个留作练习。

编写函数示例需要决定如何从不带任何属性的 X 表达式中提取属性。尽管我们选择的表示完全省略了缺失的属性，但我们必须为基于结构的 XML 表示提供 '()。因此，该函数对此类 X 表达式生成 '()：

```scheme
(check-expect (expr-attr e0) '())
(check-expect (expr-attr e1) '((initial "X")))
(check-expect (expr-attr e2) '())
(check-expect (expr-attr e3) '())
(check-expect (expr-attr e4) '((initial "X")))
```

是时候开发模板了。由于 Xexpr.v2 的数据定义复杂，我们要逐步、循序渐进地进行。首先，尽管数据定义区分了两种 X 表达式，但两个子句都描述了通过将符号 cons 到列表上构建的数据。其次，区分两个子句的是列表的其余部分，尤其是属性列表的可选存在。让我们将这两点洞察转化为模板：

```scheme
(define (expr-attr xe)
  (local ((define optional-loa+content (rest xe))))
  (cond
    [(empty? optional-loa+content) ...]
    [else ...])))
```

local 定义去掉了 X 表达式的名称，留下列表的其余部分，该部分可能以属性列表开头，也可能不以属性列表开头。关键是这只是一个列表，两个 cond 子句表明了这一点。第三，这个列表不是通过自引用定义的，而是将一些属性可选地 cons 到一个可能为空的 X 表达式列表上。换句话说，我们仍然需要区分通常的两种情况并提取通常的部分：

```scheme
(define (expr-attr xe)
  (local ((define optional-loa+content (rest xe))))
  (cond
    [(empty? optional-loa+content) ...]
    [else (... (first optional-loa+content)
        ... (rest optional-loa+content) ...)])))
```
