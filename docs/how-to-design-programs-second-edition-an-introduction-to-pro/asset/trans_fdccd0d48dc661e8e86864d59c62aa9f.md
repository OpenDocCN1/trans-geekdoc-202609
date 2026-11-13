

## 4.1 使用条件进行编程

回顾序言中对条件表达式的简要介绍。由于 cond 是本书中最复杂的表达式形式，让我们仔细看看它的一般结构：

```
(cond
[ConditionExpression1 ResultExpression1]
[ConditionExpression2 ResultExpression2]
...
[ConditionExpressionN ResultExpressionN])
```

> 方括号使 cond 行突出。用 (...) 代替 [...] 也是可以的。

cond 表达式以 (cond（其关键字）开头，以 ) 结尾。在关键字之后，程序员根据需要编写任意数量的 cond 行；每个 cond 行由两个表达式组成，用开括号和闭括号括起来：[ 和 ]。

cond 行也称为 cond 子句。

下面是一个使用条件表达式的函数定义示例：

```
(define (next traffic-light-state)
(cond
[(string=? "red" traffic-light-state) "green"]
[(string=? "green" traffic-light-state) "yellow"]
[(string=? "yellow" traffic-light-state) "red"]))
```

与序言中的数学示例一样，此示例说明了使用 cond 表达式的便利性。在许多问题情境中，函数必须区分几种不同的情况。使用 cond 表达式，您可以为每种可能性使用一行，从而提醒代码读者问题陈述中不同情况对应的代码。

实用性说明：将 cond 表达式与第 1.6 章中的 if 表达式进行对比。后者将一种情况与所有其他情况区分开来。因此，if 表达式不太适合多种情况的情境；它们最适合用于我们只想表达“二选一”的情况。因此，当我们希望提醒代码读者某些不同的情况直接来自数据定义时，我们总是使用 cond。对于其他代码片段，我们使用最方便的结构。

当 cond 表达式中的条件变得过于复杂时，您偶尔希望说些类似“在所有其他情况下”的话。对于这类问题，cond 表达式允许在最后一个 cond 行中使用 else 关键字：

```
(cond
 [ConditionExpression1 ResultExpression1]
 [ConditionExpression2 ResultExpression2]
 ...
 [else DefaultResultExpression]))
```

如果在其他 cond 行中错误地使用 else，DrRacket 中的 BSL 会发出错误信号：

```
> (cond
 [(> x 0) 10]
 [else 20]
 [(< x 10) 30])
cond:found an else clause that isn't the last clause in its cond expression
```

也就是说，BSL 会拒绝语法错误的短语，因为弄清楚这样的短语可能意味着什么毫无意义。

想象一下，设计一个函数，作为游戏程序的一部分，在游戏结束时计算某个奖项。以下是其头部：

```
; A PositiveNumber is a Number greater than/equal to 0.

; PositiveNumber -> String
; computes the reward level from the given score s
```

下面是两个并排比较的变体：

```
(define (reward s)
 (cond
   [(<= 0 s 10)
    "bronze"]
   [(and (< 10 s)
         (<= s 20))
    "silver"]
   [(< 20 s)
    "gold"]))
```

```
(define (reward s)
 (cond
   [(<= 0 s 10)
    "bronze"]
   [(and (< 10 s)
         (<= s 20))
    "silver"]
   [else
    "gold"]))
```

左侧变体使用带有三个完整条件的 cond；右侧，函数带有 else 子句。要为左侧函数制定最后一个条件，您必须计算 (< 20 s) 成立，因为

- s 属于 PositiveNumber
- (<= 0 s 10) 为 #false
- (and (< 10 s) (<= s 20)) 也求值为 #false。

虽然在这种情况下计算看起来很简单，但很容易犯小错误并将错误引入程序。因此，如果您知道希望在 cond 中获得所有先前条件的精确相反项（称为补码），则最好像右侧所示那样制定函数定义。

## 4.2 有条件地计算

从阅读“多种计算方式”和第 1.6 章中，您大致了解 DrRacket 如何计算条件表达式。让我们对 cond 表达式更精确地回顾这一理念。再看一下这个定义：

```
(define (reward s)
 (cond
  [(<= 0 s 10) "bronze"]
  [(and (< 10 s) (<= s 20)) "silver"]
  [else "gold"]))
```

该函数接收一个数值分数——一个正数——并生成一种颜色。

仅查看 cond 表达式，您无法预测将使用哪个 cond 子句。这正是函数的要点。函数处理许多不同的输入，例如 2、3、7、18、29。对于每个输入，它可能需要以不同方式进行处理。区分不同的输入类别正是 cond 表达式的目的。

例如：

```
(reward 3)
```

您知道 DrRacket 在用参数替换形参后，用函数体替换函数应用。因此：

```
(reward 3) ; say 'equals'
==
(cond
 [(<= 0 3 10) "bronze"]
 [(and (< 10 3) (<= 3 20)) "silver"]
 [else "gold"]))
```

此时，DrRacket 一次计算一个条件。对于 **第一个** 求值为 #true 的条件，它继续处理结果表达式：

```
(reward 3)
==
(cond
 [(<= 0 3 10) "bronze"]
 [(and (< 10 3) (<= 3 20)) "silver"]
 [else "gold"])]
==
(cond
 [[#true "bronze"]
 [(and (< 10 3) (<= 3 20)) "silver"]
 [else "gold"])]
==
"bronze"
```

这里第一个条件成立，因为 3 在 0 和 10 之间。

下面是第二个示例：

```
(reward 21)
==
(cond
 [[(<= 0 21 10) "bronze"]
 [(and (< 10 21) (<= 21 20)) "silver"]
 [else "gold"])]
==
(cond
 [[#false "bronze"]
 [(and (< 10 21) (<= 21 20)) "silver"]
 [else "gold"])]
==
(cond
 [[(and (< 10 21) (<= 21 20)) "silver"]
 [else "gold"])]
```

请注意，这次第一个条件求值为 #false，如“多种计算方式”中所述，整个 cond 子句被丢弃。其余计算按预期进行：

```
(cond
 [(and (< 10 21) (<= 21 20)) "silver"]
 [else "gold"])]
==
(cond
 [[(and #true (<= 21 20)) "silver"]
 [else "gold"])]
==
(cond
 [(and #true #false) "silver"]
 [else "gold"])]
==
(cond
  [#false "silver"]
  [else "gold"]))
==
(cond
  [else "gold"]))
== "gold"
```

与第一个条件一样，第二个条件也求值为 #false，因此计算继续到第三个 cond 行。else 告诉 DrRacket 用该子句的答案替换整个 cond 表达式。

**练习 48。** 将 reward 的定义后跟 (reward 18) 输入到 DrRacket 的定义区域中，并使用步进器找出 DrRacket **如何** 计算函数应用。

**练习 49。** cond 表达式实际上只是一个表达式，因此可能出现在另一个表达式的中间：

```
(- 200 (cond [(> y 200) 0] [else y]))
```

使用步进器在 y 为 100 和 210 时求值该表达式。

嵌套 cond 表达式可以消除常见表达式。考虑图 20 中重复的火箭发射函数。cond 表达式的两个分支具有相同的形状，除了 ... 指出的部分之外：

```
(place-image ROCKET X ... MTSCN)
```

```
(define WIDTH 100)
(define HEIGHT 60)
(define MTSCN (empty-scene WIDTH HEIGHT))

(define ROCKET )
(define ROCKET-CENTER-TO-TOP
 (- HEIGHT (/ (image-height ROCKET) 2)))

(define (create-rocket-scene.v5 h)
 (cond
 [(<= h ROCKET-CENTER-TO-TOP)
 (place-image ROCKET 50 h MTSCN)]
 [(> h ROCKET-CENTER-TO-TOP)
 (place-image ROCKET 50 ROCKET-CENTER-TO-TOP MTSCN)]))
```

图 20：回顾“一个程序，多个定义”

重新制定 create-rocket-scene.v5 以使用嵌套表达式；结果函数只提到一次 place-image。

## 4.3 枚举

并非所有字符串都表示鼠标事件。如果您在上一节为 big-bang 引入 on-mouse 子句时查看了 HelpDesk，您会发现只有六个字符串用于通知程序鼠标事件：

```
; A MouseEvt is one of these Strings:
; -- "button-down"
; -- "button-up"
; -- "drag"
; -- "move"
; -- "enter"
; -- "leave"
```

这些字符串的解释非常直观。前两个字符串之一出现在计算机用户单击鼠标按钮或释放它时。相比之下，第三个和第四个是关于移动鼠标，同时可能按住鼠标按钮。最后，最后两个字符串表示鼠标移动到画布边缘的事件：要么从外部进入画布，要么离开画布。

更重要的是，用字符串表示鼠标事件的数据定义与我们迄今看到的数据定义截然不同。它称为 _枚举_，是一种列出每种可能性的数据表示。枚举很常见，这不足为奇。下面是一个简单示例：

```
; A TrafficLight is one of the following Strings:
; -- "red"
; -- "green"
; -- "yellow"
; interpretation the three strings represent the three
; possible states that a traffic light may assume
```

这是交通灯可以采用的状态的简化表示。与其他定义不同，此数据定义也使用略有不同的措辞来解释 TrafficLight 术语的含义，但这是一个无关紧要的差异。

