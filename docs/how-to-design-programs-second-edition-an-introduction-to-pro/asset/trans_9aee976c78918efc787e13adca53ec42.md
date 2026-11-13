

![](img/19fbe4068996ced0ce42cec7fb82a834_211_0.png)

在这种情况下，外部框包含两个框，每个字段一个。

### 练习 69. 为练习 65 的解答绘制框表示。

在此意象的语境下，选择器就像一把钥匙。它为某种特定的箱子打开一个特定的隔层，从而使持有者能够提取其内容。因此，对上述 p1 应用 entry-name 会产生一个字符串：

```
> (entry-name p1)
"Al Abe"
```

但是，对 posn 结构应用 entry-name 会报错：

```
> (entry-name (make-posn 42 5))
entry-name:expects an entry, given (posn 42 5)
```

如果隔层包含一个箱子，可能需要连续使用两个选择器才能得到所需的数字：

```
> (ball-velocity ball1)
(make-vel -10 5)
```

对 ball1 应用 ball-velocity 提取速度字段的值，它是 vel 的一个实例。要获取沿 x 轴的速度，我们将一个选择器应用到第一次选择的结果上：

```
> (vel-deltax (ball-velocity ball1))
-10
```

因为内部表达式从 ball1 中提取速度，外部表达式提取 deltax 字段的值，在此例中为 -10。

这些交互还表明，结构实例也是值。DrRacket 会像处理数字等普通值一样，按输入的方式原样打印它们：

```
> (make-vel -10 5)
(make-vel -10 5)
> (make-entry "Tara Harp" "666-7770" "th@smlu.edu")
(make-entry "Tara Harp" "666-7770" "th@smlu.edu")
> (make-centry
"Shriram Fisler"
(make-phone 207 "363-2421")
(make-phone 101 "776-1099")
(make-phone 208 "112-9981"))
(make-centry ...)
```

别急！在家尝试最后这一条交互，以便你能看到正确的结果。

一般来说，结构类型定义不仅会创建新函数和新的值创建方式，还会将新的计算法则添加到 DrRacket 的知识库中。这些法则概括了第 5.2 节中 posn 结构的法则，最好通过示例来理解。

当 DrRacket 遇到具有两个字段的结构类型定义时，

```
(define-struct ball [location velocity])
```

它会引入两条法则，每个选择器一条：

```
(ball-location (make-ball 10 v0)) == 10
(ball-velocity (make-ball 10 v0)) == v0
```

对于不同的结构类型定义，它会引入类似的法则。因此，

```
(define-struct vel [deltax deltay])
```

DrRacket 将这两条法则添加到其知识库中：

```
(vel-deltax (make-vel dx0 dy0)) == dx0
(vel-deltay (make-vel dx0 dy0)) == dy0
```

利用这些法则，我们现在可以解释上面的交互：

```
(vel-deltax (ball-velocity ball1))
== ; DrRacket replaces ball1 with its value
(vel-deltax
(ball-velocity
  (make-ball (make-posn 30 40) (make-vel -10 5))))
== ; DrRacket uses the law for ball-velocity
(vel-deltax (make-vel -10 5))
== ; DrRacket uses the law for vel-deltax
-10
```

### 练习 70. 阐述这些结构类型定义的法则：

```
(define-struct centry [name home office cell])
(define-struct phone [area number])
```

使用 DrRacket 的单步执行器确认该表达式的值为 101：

```
(phone-area
  (centry-office
    (make-centry "Shriram Fisler"
      (make-phone 207 "363-2421")
      (make-phone 101 "776-1099"))
    (make-phone 208 "112-9981"))))
```

谓词是我们必须讨论的最后一个概念，以便理解结构类型定义。如上文所述，每个结构类型定义会引入一个新的谓词。DrRacket 使用这些谓词来发现选择器是否作用于正确类型的值；下一章将详细解释这一概念。这里我们只想说明，这些谓词就像“算术”中的谓词一样。number? 识别数字，string? 识别字符串，而 posn? 和 entry? 等谓词则识别 posn 结构和 entry 结构。我们可以通过交互区的实验来验证我们对它们工作原理的理解。假设定义区包含以下定义：

```
(define ap (make-posn 7 0))

(define pl (make-entry "Al Abe" "666-7771" "lee@x.me"))
```

如果 posn? 是一个区分 posn 和所有其他值的谓词，我们应当期望它对数字返回 #false，对 ap 返回 #true：

```
> (posn? ap)
#true
> (posn? 42)
#false
> (posn? #true)
#false
> (posn? (make-posn 3 4))
#true
```

同样，entry? 区分 entry 结构和所有其他值：

```
> (entry? pl)
#true
> (entry? 42)
#false
> (entry? #true)
#false
```

一般来说，一个谓词正好识别那些使用同名构造函数构造的值。间奏曲 1 详细解释了这一法则，并将 BSL 的计算法则汇总在一个地方。

### 练习 71. 将以下内容放入 DrRacket 的定义区：

```
; distances in terms of pixels:
(define HEIGHT 200)
(define MIDDLE (quotient HEIGHT 2))
(define WIDTH 400)
(define CENTER (quotient WIDTH 2))

(define-struct game [left-player right-player ball])

(define game0
 (make-game MIDDLE MIDDLE (make-posn CENTER CENTER)))
```

点击 RUN 并求值以下表达式：

```
(game-ball game0)
(posn? (game-ball game0))
(game-left-player game0)
```

使用逐步计算来解释结果。使用 DrRacket 的单步执行器再次核对你的计算。

## 5.6 使用结构进行编程

正确的编程需要数据定义。随着结构类型定义的引入，数据定义变得有趣起来。请记住，数据定义提供了一种将信息表示为数据并将数据解释为信息的方式。对于结构类型，这需要描述哪种数据进入哪个字段。对于某些结构类型定义，制定这样的描述既简单又直观：

```
(define-struct posn [x y])
; A Posn is a structure:
;   (make-posn Number Number)
; interpretation a point x pixels from left, y from top
```

使用其他类型的数据来创建 posn 是没有意义的。同样，根据前一节中的用法，entry——即我们用于联系人列表的条目的结构类型定义——的所有字段显然都应该是字符串：

```
(define-struct entry [name phone email])
; An Entry is a structure:
;   (make-entry String String String)
; interpretation a contact's name, phone#, and email
```

对于 posn 和 entry，读者都能轻松在应用领域中解释这些结构的实例。

与这种简单性形成对比的是，ball 的结构类型定义显然允许至少两种不同的解释：

```
(define-struct ball [location velocity])
; A Ball-1d is a structure:
;   (make-ball Number Number)
; interpretation 1 distance to top and velocity
; interpretation 2 distance to left and velocity
```

无论在程序中使用哪一种，我们都必须始终如一地坚持使用它。然而，如第 5.4 节所示，也可以完全以不同的方式使用 ball 结构：

```
; A Ball-2d is a structure:
; (make-ball Posn Vel)
; interpretation a 2-dimensional position and velocity
```

```
(define-struct vel [deltax deltay])
```

```
; A Vel is a structure:
; (make-vel Number Number)
; interpretation (make-vel dx dy) means a velocity of
; dx pixels [per tick] along the horizontal and
; dy pixels [per tick] along the vertical direction
```

在这里，我们将 Ball-2d 命名为第二个数据集合，与 Ball-1d 不同，用于描述在世界画布上直线运动的球的数据表示。简言之，可以用两种不同的方式使用同一个结构类型。当然，在一个程序中，最好只使用一种方式；否则你是在给自己找麻烦。

此外，Ball-2d 引用了我们的另一个数据定义，即 Vel 的定义。虽然迄今为止的所有其他数据定义都引用了内置数据集合（Number、Boolean、String），但你的一个数据定义引用另一个数据定义是完全可以接受的，而且很常见。

### 练习 72. 为上面的 phone 结构类型定义制定一个数据定义，以容纳给定的示例。

接下来使用这个结构类型定义为电话号码制定一个数据定义：

```
(define-struct phone# [area switch num])
```

历史上，前三位数字构成区号，接下来的三位是你所在街区的电话交换机（交换局）代码，最后四位是该街区内的电话号码。尽可能精确地用区间描述三个字段的内容。

此时，你可能会想知道数据定义到底意味着什么。这个问题及其答案是下一节的主题。目前，我们说明如何使用数据定义进行程序设计。

