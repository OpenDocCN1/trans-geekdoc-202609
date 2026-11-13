

当 DrRacket 看到 (point-y (make-point 3 4 5)) 时，它将表达式替换为 4，而 (point-x (make-point (make-point 1 2 3) 4 5)) 求值为 (make-point 1 2 3)。

谓词 c? 可以应用于任何值。如果值属于 c 类型，它返回 #true，否则返回 #false。我们可以将两部分翻译为两个方程：

```
(c? (make-c v-1 ... v-n)) == #true
(c? v)          == #false
```

如果 v 是一个未使用 make-c 构造的值。同样，最好结合我们的示例来理解这些方程：

```
(point? (make-point u v w)) == #true
(point? x)                 == #false
```

如果 x 是一个值但不是点结构。

## 练习 125. 区分合法语句和非法语句：

- 1. (define-struct oops [])
- 2. (define-struct child [parents dob date])
- 3. (define-struct (child person) [dob date])

解释这些语句为何合法或非法。

## 练习 126. 在以下表达式中识别出值，假设定义区包含以下结构类型定义：

```
(define-struct point [x y z])
(define-struct none [])
```

- 1. (make-point 1 2 3)
- 2. (make-point (make-point 1 2 3) 4 5)
- 3. (make-point (+ 1 2) 3 4)
- 4. (make-none)
- 5. (make-point (point-x (make-point 1 2 3)) 4 5)

解释这些表达式为何是值或不是值。

## 练习 127. 假设程序包含

```
(define-struct ball [x y speed-x speed-y])
```

- 1. (number? (make-ball 1 2 3 4))
- 2. (ball-speed-y (make-ball (+ 1 2) (+ 3 3) 2 3))
- 3. (ball-y (make-ball (+ 1 2) (+ 3 3) 2 3))
- 4. (ball-x (make-posn 1 2))
- 5. (ball-speed-y 5)

在交互区和使用 stepper 验证你的预测。

## BSL 测试

图 43 展示了 BSL 的全部内容以及许多测试形式。

```
def-expr = definition
    | expr
    | test-case

definition = (define (name variable variable ...) expr)
    | (define name expr)
    | (define-struct name [name ...])

expr = (name expr expr ...)
    | (cond [expr expr] ... [expr expr])
    | (cond [expr expr] ... [else expr])
    | (and expr expr expr ...)
    | (or expr expr expr ...)
    | name
    | number
    | string
    | image

test-case = (check-expect expr expr)
    | (check-within expr expr expr)
    | (check-member-of expr expr ...)
    | (check-range expr expr expr)
    | (check-error expr)
    | (check-random expr expr)
    | (check-satisfied expr name)
```

图 43: BSL，完整语法

测试表达式的一般含义很容易解释。当你点击 RUN 按钮时，DrRacket 会收集所有测试表达式并将它们移到程序末尾，保留它们出现的顺序。然后它会对定义区的内容求值。每个测试会对其组成部分求值，然后通过某个谓词将它们与预期结果进行比较。除此之外，测试还会与 DrRacket 通信，以收集一些统计信息以及有关如何显示测试失败的信息。

### 练习 128. 将以下测试复制到 DrRacket 的定义区中：

```
(check-member-of "green" "red" "yellow" "grey")
(check-within (make-posn #i1.0 #i1.1)
  (make-posn #i0.9 #i1.2) 0.01)
(check-range #i0.9 #i0.6 #i0.8)
(check-random (make-posn (random 3) (random 9))
  (make-posn (random 9) (random 3))))
(check-satisfied 4 odd?)
```

验证它们都会失败，并解释原因。

## BSL 错误消息

BSL 程序可能会发出多种语法错误。尽管我们专门为初学者（根据定义，他们会犯错误）开发了 BSL 及其错误报告系统，但错误消息需要一些时间来适应。

下面我们列举了你可能遇到的错误消息类型。清单中的每个条目由三部分组成：

- • 触发错误消息的代码片段；
- • 错误消息；以及
- • 包含修复错误建议的解释。

考虑以下示例，这是你可能见过的 **最糟糕的错误消息**：

```
(define (absolute n)
(cond
 [< 0 (- n)]
 [else n]))
<: expected a function call, but there is no open parenthesis before this function
```

cond 表达式由关键字后跟任意长度的 cond 子句序列组成。每个子句又由两部分组成：条件和答案，两者都是表达式。在这个 absolute 的定义中，第一个子句以 < 开头，它本应是一个条件，但根据我们的定义，它甚至不是一个表达式。这让 BSL 困惑不已，以至于它没有“看到” < 左侧的左括号。修复方法是将 (< n 0) 用作条件。

函数定义中对 < 的高亮显示指向了错误。如果你点击 RUN，在定义下方可以看到 DrRacket 在交互窗口中呈现的错误消息。请研究右侧的错误解释，以了解如何处理这个有些自相矛盾的消息。现在请放心，没有其他错误消息比这个更晦涩难懂了。

因此，当出现错误且需要帮助时，请找到合适的图表，在条目中搜索匹配项，然后研究完整的条目。

### 关于 BSL 中函数应用的错误消息

假设定义区仅包含以下内容，除此之外别无他物：

```
; Number Number -> Number
; finds the average of x and y
(define (average x y)
 (/ (+ x y)
  2))
```

点击 RUN 按钮。现在你可能会遇到以下错误消息。

```
(f 1)
f: this function is
not defined
```

该应用将 f 命名为函数，但 f 未在定义区中定义。请定义该函数，或确保变量名拼写正确。

```
(1 3 "three" #true)
function call:
expected a function
after the open
parenthesis, but found
a number
```

左括号后面必须始终跟随一个关键字或函数名，而 1 两者都不是。函数名要么由 BSL 定义（例如 +），要么在定义区中定义（例如 average）。

```
(average 7)
average: expects 2
arguments, but found
only 1
```

这个函数调用将 average 应用于一个参数 7，尽管它的定义要求两个数字。

```
(average 1 2 3)      average: expects 2
                   arguments, but found 3
```

这里 average 应用于 **三个** 数字，而不是两个。

```
(make-posn 1)        make-posn: expects 2
                   arguments, but found
                   only 1
```

由 BSL 定义的函数也必须应用正确数量的参数。例如，make-posn 必须应用于两个参数。

### *关于 BSL 中错误数据的错误消息*

下面的错误场景再次假设定义区包含以下内容：

```
; Number Number -> Number
; find the average of x and y
(define (average x y) ...)
```

请记住，posn 是一个预定义的结构类型。

```
(posn-x #true)       posn-x: expects a
                   posn, given #true
```

函数必须应用于它所期望的参数。例如，posn-x 期望一个 posn 的实例。

```
(average "one" "two")  +: expects a number as
                        1st argument, given
                        "one"
```

一个定义为消耗两个数字的函数必须应用于两个数字；这里 average 被应用于字符串。只有当 average 将这些字符串应用到 + 时，才会触发错误消息。像所有原语操作一样，+ 是一个受检查的函数。

### 关于 BSL 中条件表达式的错误消息

这次我们期望定义区中有一个常量定义：

```
; N in [0,1,...10]
(define 0-to-9 (random 10))
```

```
(cond
((>= 0-to-9 5)))
```

cond: 预期一个包含问题和答案的子句，但发现一个只有一部分的子句

每个 cond 子句必须恰好包含两部分：条件和答案。这里 (>= 0-to-9 5) 显然意图作为条件；答案缺失。

```
(cond
[(>= 0-to-9 5)
"head"
"tail"])
```

cond: 预期一个包含问题和答案的子句，但发现一个包含 3 个部分的子句

在这种情况下，cond 子句包含三部分，这也违反了语法。虽然 (>= 0-to-9 5) 显然意图作为条件，但子句带有两个答案："head" 和 "tail"。请选一个，或从这两个字符串中创建一个单一值。

```
(cond)
```

cond: 预期 cond 之后有一个子句，但那里什么都没有

