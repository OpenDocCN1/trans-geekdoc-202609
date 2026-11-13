

这里有一个问题陈述，用来设置一些上下文：

**示例问题** 你的团队正在设计一个交互式游戏程序，在 100 × 100 画布上移动一个红点，并允许玩家使用鼠标重置该点。以下是你们目前的进度：

```
(define MTS (empty-scene 100 100))
(define DOT (circle 3 "solid" "red"))
```

```
; A Posn represents the state of the world.
```

```
; Posn -> Posn
(define (main p0)
  (big-bang p0
    [on-tick x+]
    [on-mouse reset-dot]
    [to-draw scene+dot])))
```

你的任务是设计 scene+dot，该函数在指定位置在空画布上添加一个红点。

问题上下文规定了你的函数的签名：

```
; Posn -> Image
; adds a red spot to MTS at p
(define (scene+dot p) MTS)
```

添加目的陈述很简单。如第 3.1 章所述，它使用函数的参数来表达函数计算的内容。

现在我们列举几个示例并将其制定为测试：

```
(check-expect (scene+dot (make-posn 10 20))
              (place-image DOT 10 20 MTS))
(check-expect (scene+dot (make-posn 88 73))
              (place-image DOT 88 73 MTS))
```

鉴于函数消耗一个 Posn，我们知道该函数可以提取 x 和 y 字段的值：

```
(define (scene+dot p)
  (... (posn-x p) ... (posn-y p) ...))
```

一旦我们在函数体中看到这些额外的部分，定义的其余部分就很简单了。使用 `place-image`，该函数将 DOT 放入 MTS 中，位于 p 包含的坐标处：

```
(define (scene+dot p)
  (place-image DOT (posn-x p) (posn-y p) MTS))
```

函数可以产生结构。让我们回到上面的示例问题，因为它正好包含这样的任务：

**示例问题** 一位同事被要求定义 `x+`，这是一个消耗一个 Posn 并将 x 坐标增加 3 的函数。

请回顾，`x+` 函数处理时钟滴答。

我们可以借用 `scene+dot` 设计的前几个步骤：

```
; Posn -> Posn
; increases the x-coordinate of p by 3
(check-expect (x+ (make-posn 10 0)) (make-posn 13 0))
(define (x+ p)
  (... (posn-x p) ... (posn-y p) ...))
```

签名、目的和示例均源自问题陈述。与其说是一个带有默认结果的函数头，不如说我们的草图包含两个 Posn 的选择器表达式。毕竟，结果的信息必须来自输入，而输入是一个包含两个值的结构。

现在完成定义很容易。由于期望的结果是一个 Posn，该函数使用 `make-posn` 将各部分组合起来：

```
(define (x+ p)
  (make-posn (+ (posn-x p) 3) (posn-y p)))
```

**练习 73.** 设计函数 `posn-up-x`，它消耗一个 Posn `p` 和一个 Number n。它生成一个与 p 相同但 x 字段为 n 的 Posn。

一个巧妙的观察是，我们可以使用 posn-up-x 来定义 x+：

```
(define (x+ p)
   (posn-up-x p (+ (posn-x p) 3)))
```

**注意** 诸如 posn-up-x 之类的函数通常被称为 *更新器* 或 *函数设置器*。当你编写大型程序时，它们非常有用。

函数也可以从原子数据生成实例。虽然 make-posn 是一个内置原语，可以做到这一点，但我们的示例问题提供了另一个合适的说明：

**示例问题** 另一位同事被指派设计 reset-dot，这是一个在鼠标单击时重置点的函数。

要解决这个问题，你需要回顾第 3.6 章的知识：鼠标事件处理程序消耗四个值：世界的当前状态、鼠标单击的 x 和 y 坐标，以及一个 MouseEvt。

将示例问题的知识添加到程序设计配方中，我们得到了一个签名、一个目的陈述和一个函数头：

```
; Posn Number Number MouseEvt -> Posn
; for mouse clicks, (make-posn x y); otherwise p
(define (reset-dot p x y me) p)
```

鼠标事件处理程序的示例需要一个 Posn、两个数字和一个 MouseEvt，它只是一种特殊的 String。例如，鼠标单击由两个字符串之一表示："button-down" 和 "button-up"。前者表示用户单击了鼠标按钮，后者表示释放按钮。牢记这一点，这里有两个示例，你或许希望研究和理解：

```
(check-expect
 (reset-dot (make-posn 10 20) 29 31 "button-down")
 (make-posn 29 31))
(check-expect
 (reset-dot (make-posn 10 20) 29 31 "button-up")
 (make-posn 10 20))
```

虽然该函数只消耗原子形式的数据，但其目的陈述和示例表明，它区分了两种 MouseEvt："button-down" 和其他所有情况。这种情况分支暗示使用 cond 表达式：

```
(define (reset-dot p x y me)
  (cond
    [(mouse=? "button-down" me) (... p ... x y ...)]
    [else (... p ... x y ...)]))
```

遵循设计配方，这个骨架提及了参数，以提醒你可用的数据。

剩下的部分同样简单，因为目的陈述本身规定了函数在两种情况下分别计算什么：

```
(define (reset-dot p x y me)
  (cond
    [(mouse=? me "button-down") (make-posn x y)]
    [else p]))
```

如上所述，我们本可以提及 make-posn 创建 Posn 实例，但你已知晓此点，我们无需不断提醒你。

**练习 74.** 将所有相关的常量和函数定义复制到 DrRacket 的定义区中。添加测试并确保它们通过。然后运行程序，使用鼠标放置红点。

许多程序处理嵌套结构。我们用世界程序中的另一段小代码来说明这一点：

**示例问题** 你的团队正在设计一个游戏程序，用于跟踪一个以变化速度在画布上移动的对象。所选的数据表示需要两个数据定义：

```
(define-struct ufo [loc vel])
; A UFO is a structure:
; (make-ufo Posn Vel)
; **interpretation** (make-ufo p v) is at location
; p moving at velocity v
```

你的任务是开发 ufo-move-1。该函数计算给定 UFO 在一个时钟滴答之后的位置。

让我们先举几个例子，稍微探索一下数据定义：

```
(define v1 (make-vel 8 -3))
(define v2 (make-vel -5 -3))

(define p1 (make-posn 22 80))
(define p2 (make-posn 30 77))

(define u1 (make-ufo p1 v1))
(define u2 (make-ufo p1 v2))
(define u3 (make-ufo p2 v1))
(define u4 (make-ufo p2 v2))
```

前四个是 Vel 和 Posn 的元素。后四个以所有可能的组合组合了前四个。

接下来我们写下签名、目的、一些示例和一个函数头：

```
; UFO -> UFO
; determines where u moves in one clock tick;
; leaves the velocity as is

(check-expect (ufo-move-1 u1) u3)
(check-expect (ufo-move-1 u2)
              (make-ufo (make-posn 17 77) v2))

(define (ufo-move-1 u) u)
```

对于函数示例，我们使用数据示例 **和** 我们对位置和速度的领域知识。具体来说，我们知道一辆以每小时 60 英里向北和每小时 10 英里向西行驶的车辆，在开车一小时后将到达起点以北 60 英里和以西 10 英里的地方。
开车两小时后，它将到达起点以北 120 英里和以西 20 英里的地方。

与往常一样，一个消耗结构实例的函数可以（并且可能必须）从结构中提取信息来计算其结果。因此，我们再次在函数定义中添加选择器表达式：

```
(define (ufo-move-1 u)
 (... (ufo-loc u) ... (ufo-vel u) ...))
```

**注意** 选择器表达式提出了一个问题：我们是否需要进一步完善这个草图。毕竟，这两个表达式分别提取 Posn 和 Vel 的实例。这两个也是结构实例，我们可以再次从中提取值。结果骨架如下所示：

```
; UFO -> UFO
(define (ufo-move-1 u)
 (... (posn-x (ufo-loc u)) ...
 ... (posn-y (ufo-loc u)) ...
 ... (vel-deltax (ufo-vel u)) ...
 ... (vel-deltay (ufo-vel u)) ...))
```

然而，这样做显然会使草图看起来相当复杂。对于真正现实的程序，将此想法贯彻到底将创造极其复杂的程序大纲。更一般地说，

*如果函数处理嵌套结构，请为每个嵌套层级开发一个函数。*

在书的第二部分，这条准则变得更加重要，我们对其进行了细化。**结束**

在这里，我们关注如何将给定的 Posn 和给定的 Vel 组合起来，以得到 UFO 的下一个位置——因为这是我们的物理知识告诉我们的。具体来说，它说要将两者“相加”，这里的“相加”不能指通常应用于数字的运算。因此，让我们想象我们有一个将 Vel 添加到 Posn 的函数：

