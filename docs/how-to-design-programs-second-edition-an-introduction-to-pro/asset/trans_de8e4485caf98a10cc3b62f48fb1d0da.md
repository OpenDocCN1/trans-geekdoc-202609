

The stepper displays functions as \lambda expressions; see chapter 17.

## 15 设计抽象

本质上，抽象就是将具体的事物转化为参数。在前一节中我们多次这样做。要抽象相似的函数定义，你需要添加参数，用这些参数替换定义中的具体值。要抽象相似的数据定义，你需要创建参数化的数据定义。当你接触其他编程语言时，你会发现它们的抽象机制也需要引入参数，尽管这些参数可能不是函数参数。

### 15.1 从示例中抽象

当你最初学习加法时，你使用的是具体的例子。你的父母可能教过你用手指来加两个小数。后来，你学习了如何加两个任意的数字；这时你接触到了第一种抽象。更晚些时候，你学习了如何编写表达式，将摄氏温度转换为华氏温度，或计算汽车在给定速度和时间下行驶的距离。简而言之，你从非常具体的例子进入了抽象关系。

本节介绍了从示例中创建抽象的设计食谱。如前一节所示，创建抽象很容易。我们将困难的部分留到下一节，届时我们将向你展示如何查找和使用现有的抽象。

回顾第 14 章的要点。我们从两个具体的定义开始；我们比较它们；我们标记差异；然后我们进行抽象。创建抽象大致就是这些：

- 1. 第 1 步是比较两个项目的相似之处。

当你发现两个函数定义几乎相同，除了名称和对应位置的一些值之外，就比较它们并标记差异。如果两个定义在不止一个地方不同，请用一行线连接对应的差异。

> 该食谱针对非值抽象需要进行重大修改。

图 90 显示了一对相似的函数定义。这两个函数将一个函数应用于列表中的每个项目。它们仅在应用于每个项目的函数上有所不同。两个高亮强调了这一基本差异。它们还在两个非基本方面不同：函数的名称和参数的名称。

```
; List-of-numbers -> List-of-numbers
; converts a list of Celsius
; temperatures to Fahrenheit
(define (cf* l)
  (cond
    [(empty? l) '()]
    [else
     (cons
      (C2F (first l))
      (cf* (rest l)))])

; Number -> Number
; converts one Celsius
; temperature to Fahrenheit
(define (C2F c)
  (+ (* 9/5 c) 32))

; Inventory -> List-of-strings
; extracts the names of
; toys from an inventory
(define (names i)
  (cond
    [(empty? i) '()]
    [else
     (cons
      (IR-name (first i))
      (names (rest i)))]))

(define-struct IR
    [name price])
; An IR is a structure:
;   (make-IR String Number)
; An Inventory is one of:
; -- '()
; -- (cons IR Inventory)
```

图 90：一对相似的函数

- 2. 接下来我们进行抽象。要*抽象*意味着将对应代码高亮的内容替换为新名称，并将这些名称添加到参数列表中。对于我们的运行示例，在用 g 替换差异后，我们得到以下一对函数；参见图 91。这一初步变化消除了基本差异。现在每个函数都遍历列表，并将某个给定函数应用于每个项目。

```
(define (cf* l g)
  (cond
    [(empty? l) '()]
    [else
     (cons
      (g (first l))
      (cf* (rest l) g))])

(define (map1 k g)
  (cond
    [(empty? k) '()]
    [else
     (cons
      (g (first k))
      (map1 (rest k) g))])

(define (names i g)
  (cond
    [(empty? i) '()]
    [else
     (cons
      (g (first i))
      (names (rest i) g))])
```

图 91：抽象后的同一对相似函数

非基本差异——函数的名称和偶尔某些参数的名称——很容易消除。的确，如果你探索过 DrRacket，你就会知道 check syntax 允许你系统且轻松地完成此操作；参见图 91 底部。我们选择使用 map1 作为函数名，k 作为列表参数名。无论你选择什么名称，结果都是两个相同的函数定义。

我们的示例很简单。在许多情况下，你会发现不止一对差异。关键是找到差异对。当你用纸和笔标记差异时，用一行线连接相关的框。然后每行引入一个额外的参数。别忘了更改函数的所有递归用法，以便额外的参数一同传递。

- 3. 现在我们必须验证新函数是原函数对的正确抽象。验证意味着 **测试**，这里意味着使用抽象来定义两个原始函数。

因此，假设一个原始函数称为 f-original，它消耗一个参数，而抽象函数称为 abstract。如果 f-original 与另一个具体函数在使用一个值（例如 val）方面不同，则以下函数定义

```
(define (f-from-abstract x)
  (abstract x val))
```

它引入了函数 f-from-abstract，该函数应与 f-original 等价。也就是说，对于每个合适的值 v，(f-from-abstract v) 应该产生与 (f-original v) 相同的答案。特别是，它必须对 f-original 的测试所使用的所有值都成立。因此，为 f-from-abstract 重新表述并重新运行那些测试，并确保它们成功。

让我们回到我们的运行示例：

```
; List-of-numbers -> List-of-numbers
(define (cf*-from-map1 l) (map1 l C2F))
```

```
; Inventory -> List-of-strings
(define (names-from-map1 i) (map1 i IR-name))
```

一个完整的示例将包含一些测试，因此我们可以假设 cf* 和 names 都带有一些测试：

```scheme
(check-expect (cf* (list 100 0 -40))
         (list 212 32 -40))

(check-expect (names
               (list
                (make-IR "doll" 21.0)
                (make-IR "bear" 13.0)))
              (list "doll" "bear"))
```

为了确保使用 map1 定义的函数正常工作，你可以复制测试并适当更改函数名：

```scheme
(check-expect
 (cf*-from-map1 (list 100 0 -40))
 (list 212 32 -40))

(check-expect
 (names-from-map1
  (list
   (make-IR "doll" 21.0)
   (make-IR "bear" 13.0)))
 (list "doll" "bear"))
```

- 4. 一个新抽象需要 **签名**，因为，如第 16 章所解释的，抽象的重用始于它们的签名。查找有用的签名是一个严肃的问题。目前我们使用运行示例来说明这一困难；第 15.2 节解决了该问题。

考虑 map1 的签名问题。一方面，如果你将 map1 视为 cf* 的抽象，你可能会认为它是

```scheme
; List-of-numbers [Number -> Number] -> List-of-numbers
```

即，原始签名扩展了用于函数的一部分：

```scheme
; [Number -> Number]
```

由于 map1 的额外参数是一个函数，使用函数签名来描述它不应令你感到惊讶。这个函数签名也很简单；它是所有从数字到数字的函数的一个“名称”。C2F 就是这样的函数，add1、sin 和 imag-part 也是。

另一方面，如果你将 map1 视为 names 的抽象，签名就截然不同了：

```scheme
; Inventory [IR -> String] -> List-of-strings
```

这次，额外的参数是 IR-name，它是一个选择器函数，消耗 IRs 并生成 Strings。但很明显，第二个签名在第一种情况下无用，反之亦然。为了同时适应这两种情况，map1 的签名必须表明 Number、IR 和 String 是巧合的。

关于签名，你现在可能很想使用 List-of。显然，写 [List-of IR] 比为 Inventory 拼写出数据定义要容易得多。所以，是的，目前，当一切都涉及列表时，我们使用 List-of，你也应该这样做。

一旦你抽象了两个函数，你应该检查抽象函数是否有其他用途。如果是这样，这个抽象就真正有用。以 map1 为例，可以轻松看出如何使用它为数字列表中的每个数字加 1：

```
; List-of-numbers -> List-of-numbers
(define (add1-to-each l)
  (map1 l add1))
```

同样，map1 也可以用于提取库存中每个项目的价格。当你能为新抽象想象出许多这样的用途时，将其添加到有用函数库中以备使用。当然，很可能其他人也想到了它，并且该函数已经是语言的一部分。对于像 map1 这样的函数，参见第 16 章。

