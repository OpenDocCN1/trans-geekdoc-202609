


> (big-bang 100 [to-draw number->square])

会出现一个单独的窗口，它显示一个 100 × 100 的红色正方形。此外，DrRacket 交互区域不会显示另一个提示符；程序似乎一直在运行，情况确实如此。要停止程序，请单击 DrRacket 的 STOP 按钮或窗口的 CLOSE 按钮：

```
> (big-bang 100 [to-draw number->square])
100
```

当 DrRacket 停止对 big-bang 表达式的求值时，它会返回当前状态，在本例中即初始状态：100。

这是一个更有趣的 big-bang 表达式：

```
> (big-bang 100
[to-draw number->square]
[on-tick sub1]
[stop-when zero?]))
```

这个 big-bang 表达式在前一个表达式的基础上添加了两个可选子句：on-tick 子句告诉 DrRacket 如何处理时钟滴答，而 stop-when 子句说明何时停止程序。我们按如下方式读取它，以 100 作为初始状态：

- 1. 每次时钟滴答时，从当前状态减去 1；
- 2. 然后检查 zero? 对新状态是否为真，如果是则停止；并且
- 3. 每次事件处理程序返回一个值时，使用 number->square 将其呈现为图像。

现在按下 "return" 键并观察发生的事情。最终表达式的求值终止，DrRacket 显示 0。

big-bang 表达式会跟踪当前状态。最初，该状态为 100。每次时钟滴答时，它会调用时钟滴答处理程序并得到一个新状态。因此，big-bang 的状态按如下方式变化：

```
100, 99, 98,..., 2, 1, 0
```

当状态值变为 0 时，求值完成。对于其他每个状态——从 100 到 1——big-bang 将状态转换为图像，使用 number->square，如 to-draw 子句所指示的。因此，窗口显示一个红色正方形，在 100 个时钟滴答内从 100 × 100 像素缩小到 1 × 1 像素。

让我们添加一个处理键盘事件的子句。首先，我们需要一个函数，它使用当前状态和描述键盘事件的字符串，然后返回一个新状态：

```
(define (reset s ke)
  100)
```

此函数丢弃其参数并返回 100，即我们希望修改的 big-bang 表达式的初始状态。其次，我们向 big-bang 表达式添加一个 on-key 子句：

```
> (big-bang 100
[to-draw number->square]
[on-tick sub1]
[stop-when zero?]
[on-key reset])
```

停止！解释当你按下 "return"、数到 10，最后按下 "a" 时会发生什么。

你会看到，红色正方形以每个时钟滴答一个像素的速度缩小。但是，一旦你按下 "a" 键，红色正方形就会重新膨胀到全尺寸，因为 reset 被对当前正方形长度和 "a" 调用，并返回 100。这个数字变成 big-bang 的新状态，number->square 将其呈现为全尺寸红色正方形。

为了一般性地理解 big-bang 表达式的求值，让我们看一个示意图版本：

```
(big-bang cw0
[on-tick tock]
[on-key ke-h]
[on-mouse me-h]
[to-draw render]
[stop-when end?]
...)
```

这个 big-bang 表达式指定了三个事件处理程序——tock、ke-h 和 me-h——以及一个 stop-when 子句。

这个 big-bang 表达式的求值从 cw0 开始，cw0 通常是一个表达式。DrRacket，我们的操作系统，将 cw0 的值安装为当前状态。它使用 render 将当前状态转换为图像，然后在单独的窗口中显示该图像。确实，render 是 big-bang 表达式向世界呈现数据的 **唯一** 方式。

事件的处理方式如下：

- 每次时钟滴答时，DrRacket 将 tock 应用于 big-bang 的当前状态并收到响应值；big-bang 将此返回值视为下一个当前状态。

- 每次按下键时，DrRacket 将 ke-h 应用于 big-bang 的当前状态和代表键的字符串；例如，按下 "a" 键用 "a" 表示，左箭头键用 "left" 表示。当 ke-h 返回一个值时，big-bang 将其视为下一个当前状态。

- 每次鼠标进入窗口、离开窗口、移动或被单击时，DrRacket 将 me-h 应用于 big-bang 的当前状态、事件的 x 和 y 坐标以及代表发生的鼠标事件类型的字符串；例如，单击鼠标按钮用 "button-down" 表示。当 me-h 返回一个值时，big-bang 将其视为下一个当前状态。

所有事件按顺序处理；如果两个事件似乎同时发生，DrRacket 充当打破平局者，并按某种顺序排列它们。

处理完事件后，big-bang 同时使用 end? 和 render 来检查当前状态：

- (end? cw) 生成一个布尔值。如果为 #true，big-bang 立即停止计算。否则，它继续执行。

- (render cw) 预期生成一个图像，big-bang 在单独的窗口中显示此图像。

图 13 中的表格简洁地总结了这个过程。在第一行中，它列出了当前状态的名称。第二行列举了 DrRacket 遇到的事件的名称：e0、e1，等等。每个 ei 可能是时钟滴答、键盘按键或鼠标事件。接下来的三行指定了处理事件的结果：

- 如果 e0 是时钟滴答，big-bang 求值 (tock cw0) 以生成 cw1。
- 如果 e0 是键盘事件，则求值 (ke-h cw0 e0) 并生成 cw1。处理程序必须应用于事件本身，因为一般来说，程序会对每个键做出不同反应。
- 如果 e0 是鼠标事件，big-bang 运行 (me-h cw0 e0 ...) 以获得 cw1。这个调用是一个草图，因为鼠标事件 e0 实际上与几个数据片段相关联——其性质和坐标——我们只是想表示这么多。
- 最后，render 将当前状态转换为图像，由最后一行指示。DrRacket 在单独的窗口中显示这些图像。

| 当前状态 | cw0 | cw1 | ... |
|---|---|---|---|
| 事件 | e0 | e1 | ... |
| 时钟滴答时 | (tock cw0) | (tock cw1) | ... |
| 按键时 | (ke-h cw0 e0) | (ke-h cw1 e1) | ... |
| 鼠标事件时 | (me-h cw0 e0 ...) | (me-h cw1 e1 ...) | ... |
| 其图像 | (render cw0) | (render cw1) | ... |

图 13：big-bang 的工作原理

cw1 下方的列显示如何生成 cw2，具体取决于 e1 发生的事件类型。

让我们用具体的事件序列来解释这个表格：用户按下 "a" 键，然后时钟滴答，最后用户单击鼠标在位置 (90,100) 触发 "button down" 事件。然后，用 Racket 表示法：

- 1. cw1 是 (ke-h cw0 "a") 的结果；
- 2. cw2 是 (tock cw1) 的结果；并且
- 3. cw3 是 (me-h cw2 90 100 "button-down") 的结果。

我们实际上可以将这三个步骤表示为三个定义的序列：

```
(define cw1 (ke-h cw0 "a"))
(define cw2 (tock cw1))
(define cw3 (me-h cw2 "button-down" 90 100))
```

停止！big-bang 如何显示这三个状态中的每一个？

现在让我们考虑三个时钟滴答的序列。在这种情况下，

- 1. cw1 是 (tock cw0) 的结果；
- 2. cw2 是 (tock cw1) 的结果；并且
- 3. cw3 是 (tock cw2) 的结果。

或者，用 BSL 重新表述：

```
(define cw1 (tock cw0))
(define cw2 (tock cw1))
(define cw3 (tock cw2))
```

确实，我们也可以通过单个表达式确定 cw3：

```
(tock (tock (tock cw0)))
```

这确定了 big-bang 在三个时钟滴答后计算的状态。停止！将第一个事件序列重新表述为表达式。

简而言之，事件序列确定 big-bang 按什么顺序概念性地遍历上述可能状态表，以到达每个时间段的当前状态。当然，big-bang 不会触碰当前状态；它只是保护它，并在需要时将其传递给事件处理程序和其他函数。

从这里开始，定义第一个交互程序非常简单。请参见图 14。该程序由两个常量定义组成，后跟三个函数定义：main，启动 big-bang 交互程序；place-dot-at，将当前状态转换为图像；以及 stop，丢弃其输入并生成 0。

