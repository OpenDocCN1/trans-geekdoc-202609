

```
; Missile Image -> Image
; adds m to the given image im
(define (missile-render m im) im)
```

与上文一样，注释详细描述了我们想要的内容。

```
; SIGS -> Image
; renders the given game state on top of BACKGROUND
; for examples see figure 32
(define (si-render s)
  (cond
    [(aim? s)
     (tank-render (aim-tank s)
                  (ufo-render (aim-ufo s) BACKGROUND))]
    [(fired? s)
     (tank-render (fired-tank s)
                  (ufo-render (fired-ufo s)
                              (missile-render (fired-missile s)
                                              BACKGROUND)))]))
```

### 图 33：完整的渲染函数

**练习 97.** 设计函数 tank-render、ufo-render 和 missile-render。比较以下表达式：

```
(tank-render
 (fired-tank s)
 (ufo-render (fired-ufo s)
             (missile-render (fired-missile s)
                             BACKGROUND)))
```

与以下表达式：

```
(ufo-render
 (fired-ufo s)
 (tank-render (fired-tank s)
              (missile-render (fired-missile s)
                              BACKGROUND)))
```

这两个表达式在什么条件下会产生相同的结果？

练习 98. 设计函数 si-game-over？，用作 stop-when 处理程序。如果 UFO 降落或导弹击中 UFO，游戏停止。对于这两个条件，我们建议检查一个对象与另一个对象的接近程度。

stop-when 子句允许一个可选的第二个子表达式，即渲染游戏最终状态的函数。设计 si-render-final，并将其用作练习 100 中主函数 stop-when 子句的第二部分。

练习 99. 设计 si-move。该函数在每个时钟滴答时被调用，以确定对象现在移动到哪个位置。因此，它接收一个 SIGS 元素并生成另一个。

移动坦克和导弹（如果有的话）相对简单。它们以恒定速度沿直线移动。移动 UFO 需要向左或向右进行小幅度随机跳跃。由于您从未处理过生成随机数的函数，本练习的其余部分是一段关于如何处理此问题的较长提示。

BSL 自带一个生成随机数的函数。引入这个函数说明了为什么在设计过程中签名和目的说明起着如此重要的作用。以下是您需要的函数的相关材料：

```
; Number -> Number
; produces a number in the interval [0,n),
; possibly a different one each time it is called
(define (random n) ...)
```

既然签名和目的说明精确地描述了函数计算的内容，您现在可以在 DrRacket 的交互区域尝试 random。

停止！去做！

如果 random 几乎每次被调用时都产生不同的数字，那么测试使用 random 的函数就很困难。首先，将 si-move 及其适当功能分为两部分：

> 您必须使用 random 这一想法属于 BSL 知识，而不是您必须掌握的设计技能的一部分，这就是为什么我们提供这个提示。此外，random 是第一个也是唯一一个不是数学函数的 BSL 原语。编程中的函数受到数学函数的启发，但它们并不是相同的概念。

```
(define (si-move w)
  (si-move-proper w (random ...)))

; SIGS Number -> SIGS
; moves the space-invader objects predictably by delta
(define (si-move-proper w delta)
  w)
```

通过此定义，您将随机数的生成与移动游戏对象的行为分开了。虽然 random 每次被调用时可能产生不同的结果，但 si-move-proper 可以针对特定的数值输入进行测试，因此在给定相同输入时保证返回相同的结果。简而言之，大部分代码仍然可以测试。

与其直接调用 random，您可能希望设计一个为 UFO 创建随机 x 坐标的函数。考虑使用 BSL 测试框架中的 check-random 来测试这样的函数。

**练习 100.** 设计函数 si-control，它充当键盘事件处理程序。作为这样一个函数，它接收一个游戏状态和一个 KeyEvent，并生成一个新的游戏状态。它响应三个不同的按键：

- 按下左箭头键可确保坦克向左移动；
- 按下右箭头键可确保坦克向右移动；以及
- 按下空格键在导弹尚未发射时发射导弹。

一旦有了这个函数，您就可以定义 si-main 函数，它使用 big-bang 启动游戏窗口。祝您愉快！

数据表示很少是唯一的。例如，我们可以使用一个结构类型来表示太空侵略者游戏的状态：

```
(define-struct sigs [ufo tank missile])
; A SIGS.v2 (short for SIGS version 2) is a structure:
; (make-sigs UFO Tank MissileOrNot)
; **interpretation** represents the complete state of a
; space invader game
```

; A MissileOrNot 是以下之一：
; -- #false
; -- Posn
; **interpretation** #false 表示导弹在坦克中；
; Posn 表示导弹位于该位置

与游戏状态的第一种数据表示不同，这个第二个版本不区分导弹发射前和发射后。相反，每个状态都包含一些关于导弹的数据，尽管这部分数据可能只是 #false，表示导弹尚未发射。

因此，这种第二种状态数据表示的函数与第一种不同。特别是，接收 SIGS.v2 元素的函数不使用 cond 表达式，因为集合中只有一种元素。就设计方法而言，第 5.8 章中的结构设计配方就足够了。图 34 显示了为这种数据表示设计渲染函数的结果。

```
; SIGS.v2 -> Image
; renders the given game state on top of BACKGROUND
(define (si-render.v2 s)
  (tank-render
    (sigs-tank s)
    (ufo-render (sigs-ufo s)
      (missile-render.v2 (sigs-missile s)
                         BACKGROUND))))
```

### 图 34：再次渲染游戏状态

相比之下，使用 MissileOrNot 设计函数需要本节中的配方。让我们看看 missile-render.v2 的设计，它的工作是向图像添加导弹。以下是头部材料：

```
; MissileOrNot Image -> Image
; adds an image of missile m to scene s
(define (missile-render.v2 m s)
  s)
```

关于示例，我们必须至少考虑两种情况：一种是 m 为 #false，另一种是 m 为 Posn。在第一种情况下，导弹尚未发射，这意味着不应向给定场景添加导弹图像。在第二种情况下，导弹的位置已指定，导弹图像必须出现在该位置。图 35 通过两个不同的场景演示了该函数的工作原理。

![](img/19fbe4068996ced0ce42cec7fb82a834_255_0.png)

### 图 35：渲染太空侵略者游戏，附带坦克

**练习 101.** 将图 35 中的示例转换为测试用例。

现在我们准备开发模板了。因为主要参数（m）的数据定义是一个包含两个项目的枚举，函数体很可能由一个包含两个子句的 cond 表达式组成：

```
(define (missile-render.v2 m s)
  (cond
    [(boolean? m) ...]
    [(posn? m) ...]))
```

再次遵循数据定义，第一个 cond 子句检查 m 是否为布尔值，第二个子句检查它是否为 Posn 元素。如果有人不小心将 missile-render.v2 应用于 #true 和某个图像，函数将使用第一个 cond 子句来计算结果。我们将在下文详述此类错误。

模板的第二步要求在所有处理结构的 cond 子句中包含选择器表达式。在我们的示例中，这适用于第二个子句，选择器表达式从给定的 Posn 中提取 x 和 y 坐标：

```
(define (missile-render.v2 m s)
  (cond
    [(boolean? m) ...]
    [(posn? m) (... (posn-x m) ... (posn-y m) ...)]))
```

将此模板与上面的 si-render 模板进行比较。后者的数据定义处理两种不同的结构类型，因此 si-render 的函数模板在两个 cond 子句中都包含选择器表达式。然而，MissileOrNot 的数据定义混合了纯值项目和描述结构的项目。这两种定义都完全没问题；关键在于遵循配方，并找到与数据定义相匹配的代码组织方式。

以下是完整的函数定义：

```
(define (missile-render.v2 m s)
  (cond
    [(boolean? m) s]
    [(posn? m) (place-image MISSILE (posn-x m) (posn-y m) s)]))
```

逐步进行此操作，您首先处理简单的子句；在这个函数中，这是第一个子句。由于它表示导弹尚未发射，函数返回给定的 s。对于第二个子句，您需要记住 (posn-x m) 和 (posn-y m) 选择导弹图像的坐标。该函数必须将 MISSILE 添加到 s，因此您必须找出原始操作和您自己的函数的最佳组合来组合这四个值。选择这种组合操作正是您作为程序员的创造性洞察力所在。

**练习 102.** 为完成第二个数据定义的游戏设计所有其他所需的函数。

**练习 103.** 为以下四种动物园动物开发数据表示：

- 蜘蛛，其相关属性是剩余腿的数量（我们假设蜘蛛在事故中可能会失去腿）以及运输所需的空间；
- 大象，其唯一属性是运输所需的空间；

