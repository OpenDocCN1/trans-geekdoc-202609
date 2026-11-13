

```racket
; distances in terms of pixels
(define WIDTH 300)
(define HEIGHT 300)

; N -> [List-of Posn]
; generates n random Posns in [0,WIDTH) by [0,HEIGHT)
(check-satisfied (random-posns 3)
                 (n-inside-playground? 3))

(define (random-posns n)
  (build-list
   n
   (lambda (i)
     (make-posn (random WIDTH) (random HEIGHT)))))
```

定义 random-posns/bad，使其满足 n-inside-playground?，但不符合上述目的陈述所暗示的期望。注意：此规范是 **不完整的**。虽然 “partial” 这个词可能会浮现在脑海中，但计算机科学家将 “partial specification”这个短语保留用于另一个目的。

## 17.5 使用 lambda 进行表示

因为在 ISL+ 中函数是头等公民，我们可以将其视为另一种形式的数据，并用于数据表示。本节对这一想法有所介绍；接下来的几章并不依赖它。其标题使用 “abstracting”，因为人们认为使用函数的数据表示是抽象的。

一如既往，我们从一个代表性问题开始：

**示例问题** 海军战略家将舰队表示为矩形（舰船本身）和圆形（其武器的打击范围）。舰队的覆盖范围是所有这些形状的组合。为矩形、圆形和形状组合设计一种数据表示。然后设计一个函数，用于判断某个点是否位于某个形状内。

> 此问题也可通过自指数据表示来解决，即一个形状是圆形、矩形或两个形状的组合。有关此设计选择，请参见本书的下一部分。

此问题伴随着各种具体的解释，此处不再赘述。20 世纪 90 年代中期，耶鲁大学受美国国防部委托举办的一场编程比赛的主题就是此问题的一个稍复杂版本。

一种数学方法将形状视为点上的谓词。也就是说，形状是一个将笛卡尔点映射到布尔值的函数。让我们将这些英文单词翻译成数据定义：

```
; A Shape is a function:
; [Posn -> Boolean]
; interpretation if s is a shape and p a Posn, (s p)
; produces #true if p is in s, #false otherwise
```

其解释部分很详尽，因为这种数据表示如此不寻常。如此不寻常的表示需要立即通过示例进行探索。然而，我们暂时推迟这一步，转而定义一个检查点是否在某个形状内的函数：

```
; Shape Posn -> Boolean
(define (inside? s p)
 (s p))
```

由于给定的解释，这样做很直接。结果证明，这比创建示例更简单，而且，令人惊讶的是，该函数对于制定数据示例很有帮助。

停下！解释 inside? 如何工作以及为什么有效。

现在让我们回到 Shape 元素的问题。以下是该类的一个简单元素：

```
; Posn -> Boolean
(lambda (p) (and (= (posn-x p) 3) (= (posn-y p) 4)))
```

如所要求，它消耗一个 Posn p，其主体将 p 的坐标与点 (3,4) 的坐标进行比较，这意味着该函数表示一个单点。虽然将点作为 Shape 的数据表示看似荒谬，但它暗示了我们如何定义创建 Shape 元素的函数：

```
; Number Number -> Shape
(define (mk-point x y)
(lambda (p)
 (and (= (posn-x p) x) (= (posn-y p) y))))
(define a-sample-shape (mk-point 3 4))
```

我们使用 “mk” 是因为此函数不是一个普通的构造函数。

再次停下！让自己相信最后一行创建了 (3,4) 的数据表示。考虑使用 DrRacket 的 stepper。

如果我们要 **设计** 这样的函数，我们将制定一个目的陈述并提供一些示例。就目的而言，我们可以采用明显的说法：

```
; creates a representation for a point at (x,y)
```

或者，更简洁且更恰当地说，

```
; represents a point at (x,y)
```

对于示例，我们希望采用 Shape 的解释。例如，(mk-point 3 4) 应该求值为一个函数，该函数仅在给定 (make-posn 3 4) 时返回 #true。使用 inside?，我们可以通过测试来表达此声明：

```
(check-expect (inside? (mk-point 3 4) (make-posn 3 4))
#true)
(check-expect (inside? (mk-point 3 4) (make-posn 3 0))
#false)
```

简而言之，要创建点表示，我们定义一个类似构造函数的函数，它消耗点的两个坐标。而不是记录，此函数使用 lambda 构造另一个函数。它创建的函数消耗一个 Posn，并确定其 x 和 y 字段是否等于最初给定的坐标。

接下来，我们将此想法从简单的点推广到形状，比如说圆。在你的几何课程中，你学到圆是所有到圆心距离相同的点的集合——半径。对于圆内的点，距离小于或等于半径。因此，创建圆的 Shape 表示的函数必须消耗三个部分：圆心的两个坐标和半径：

```
; Number Number Number -> Shape
; creates a representation for a circle of radius r
;   located at (center-x, center-y)
(define (mk-circle center-x center-y r)
  ...)
```

与 mk-point 类似，它通过 lambda 生成一个函数。返回的函数确定给定的某个 Posn 是否在圆内。以下是一些示例，同样表述为测试：

```
(check-expect
(inside? (mk-circle 3 4 5) (make-posn 0 0)) #true)
(check-expect
(inside? (mk-circle 3 4 5) (make-posn 0 9)) #false)
(check-expect
(inside? (mk-circle 3 4 5) (make-posn -1 3)) #true)
```

原点，(make-posn 0 0)，距离圆心 (3,4) 正好五个单位；参见第 5.4 节。停下！解释其余示例。

**练习 296.** 使用圆规和铅笔绘图来检查测试。

从数学上讲，我们说 Posn p 在圆内，如果 p 与圆心之间的距离小于半径 r。让我们希望有合适的辅助函数，并写下我们现有的内容。

```
(define (mk-circle center-x center-y r)
; [Posn -> Boolean]
(lambda (p)
(<= (distance-between center-x center-y p) r)))
```

distance-between 函数是一个简单的练习。

**练习 297.** 设计函数 distance-between。它消耗两个数字和一个 Posn：x、y 和 p。该函数计算点 (x, y) 和 p 之间的距离。

**领域知识** (x₀, y₀) 和 (x₁, y₁) 之间的距离是

\(\sqrt{(x_0 - x_1)^2 + (y_0 - y_1)^2}\)

也就是说，(x₀ - x₁, y₀ - y₁) 到原点的距离。

矩形的数据表示以类似的方式表达：

```
; Number Number Number Number -> Shape
; represents a width by height rectangle whose
; upper-left corner is located at (ul-x, ul-y)
(check-expect (inside? (mk-rect 0 0 10 3)
                (make-posn 0 0))
        #true)
(check-expect (inside? (mk-rect 2 3 10 3)
                 (make-posn 4 5))
          #true)
; Stop! Formulate a negative test case.
(define (mk-rect ul-x ul-y width height)
         (lambda (p)
           (and (<= ul-x (posn-x p) (+ ul-x width))
                (<= ul-y (posn-y p) (+ ul-y height))))))
```

其构造函数接收四个数字：左上角的坐标、宽度和高度。结果同样是一个 lambda 表达式。与圆一样，此函数消耗一个 Posn 并生成一个布尔值，检查 Posn 的 x 和 y 字段是否在适当的区间内。

此时，我们只剩下一项任务，即设计一个将两个 Shape 表示映射到其组合的函数。签名和头部很容易：

```
; Shape Shape -> Shape
; combines two shapes into one
(define (mk-combination s1 s2)
  ; Posn -> Boolean
  (lambda (p)
    #false))
```

确实，即使是默认值也很简单。我们知道形状被表示为从 Posn 到 Boolean 的函数，因此我们写下一个 lambda，它消耗某个 Posn 并生成 #false，这意味着它表示没有点在组合中。

