

此时，我们已经可以看出，手头的任务不需要递归。因此，我们切换到设计配方的第五步。很明显，如果给定的 X 表达式仅带有一个名称，则没有属性。在第二个子句中，问题是列表中的第一项是属性列表还是仅仅是一个 Xexpr.v2。因为这听起来很复杂，我们许个愿：

```
; [List-of Attribute] or Xexpr.v2 -> ???
; determines whether x is an element of [List-of Attribute]
; #false otherwise
(define (list-of-attributes? x)
  #false)
```

有了这个函数，完成 xexpr-attr 就变得很简单；参见图 126。如果第一项是属性列表，函数就返回它；否则没有属性。

```
(define (xexpr-attr xe)
  (local ((define optional-loa+content (rest xe)))
    (cond
      [(empty? optional-loa+content) '()]
      [else
       (local ((define loa-or-x
                 (first optional-loa+content)))
         (if (list-of-attributes? loa-or-x)
             loa-or-x
             '())))]))
```

图 126: xexpr-attr 的完整定义

对于 list-of-attributes? 的设计，我们以同样的方式进行，得到这个定义：

```
; [List-of Attribute] or Xexpr.v2 -> Boolean
; is x a list of attributes
(define (list-of-attributes? x)
  (cond
    [(empty? x) #true]
    [else
     (local ((define possible-attribute (first x))))
     (cons? possible-attribute)])))
```

我们跳过设计过程的细节，因为它们不值得一提。值得注意的是，**值得一提的是**这个函数的签名。它不是指定单一的数据定义作为可能的输入，而是将两个数据定义用英文单词“or”分隔组合在一起。在 ISL+ 中，这种带有明确含义的非正式签名在某些情况下是可以接受的。

**练习 366。** 设计 xexpr-name 和 xexpr-content。▪

**练习 367。** 设计配方要求在 xexpr-attr 的模板中加入自引用。将此自引用添加到模板中，然后解释为什么最终的解析函数不包含它。▪

**练习 368。** 制定一个数据定义，以替代 list-of-attributes? 函数定义中非正式的“or”签名。▪

**练习 369。** 设计 find-attr。该函数接收一个属性列表和一个符号。如果属性列表将符号与字符串关联，则函数检索该字符串；否则返回 #false。查找 assq 并使用它来定义该函数。▪

在本章的其余部分，Xexpr 指的是 Xexpr.v2。此外，我们假设 xexpr-name、xexpr-attr 和 xexpr-content 已经定义。最后，我们使用练习 369 中的 find-attr 来检索属性值。

## 22.2 渲染 XML 枚举

XML 实际上是一种语言**家族**。人们为特定的通信渠道定义方言。例如，XHTML 是以 XML 格式发送 Web 内容的语言。在本节中，我们将说明如何为一小段 XHTML 设计渲染函数，具体来说，就是本章开头的枚举。

`ul` 标签包围所谓的无序 HTML 列表。列表中的每个项目都带有 `li` 标签，它通常包含单词，但也可能包含其他元素，甚至是枚举。所谓“无序” HTML 是指每个项目都应使用前导项目符号而不是数字来渲染。

由于 Xexpr 本身不带普通字符串，在子集中如何表示 XHTML 枚举并不立刻显而易见。一种选择是进一步细化数据表示，使 Xexpr 可以是一个 String。另一种选择是引用文本表示：

```
; An XWord is 'word ((text String))).
```

在这里，我们使用第二种选择；Racket（教学语言所源自的语言）提供了将 String 包含在 Xexpr 中的库。

**练习 370。** 为 XWord 拟定三个示例。设计 `word?`，用于检查某个 ISL+ 值是否属于 XWord，以及 `word-text`，用于提取 XWord 实例中唯一属性的值。▪

**练习 371。** 细化 Xexpr 的定义，以便可以表示纯字符串的 XML 元素，包括枚举中的项目。▪

给定单词的表示，以 XHTML 风格表示单词枚举是简单的：

```
; An XEnum.v1 is one of:
; -- (cons 'ul [List-of XItem.v1])
; -- (cons 'ul (cons Attributes [List-of XItem.v1]))
; An XItem.v1 is one of:
; -- (cons 'li (cons XWord '()))
; -- (cons 'li (cons Attributes (cons XWord '())))
```

为了完整性，数据定义包括属性列表，尽管它们不影响渲染。

停！论证 XEnum.v1 的每个元素也属于 Xexpr。

以下是 XEnum.v1 的一个示例元素：

```
(define e0
  '(ul
    (li (word ((text "one"))))
    (li (word ((text "two"))))))
```

它对应于本章开头示例中的内部枚举。借助 *2htdp/image* 库的帮助来渲染它，应该得到如下图像：

![](img/19fbe4068996ced0ce42cec7fb82a834_701_0.png)

项目符号的半径和项目符号与文本之间的距离是审美问题；这里重要的是思路。

*我们在交互区开发了这些表达式。你会怎么做？*

要创建这种图像，你可能会使用这个 ISL+ 程序：

```
(define e0-rendered
  (above/align
   'left
   (beside/align 'center BT (text "one" 12 'black))
   (beside/align 'center BT (text "two" 12 'black))))
```

假设 BT 是项目符号的渲染结果。

现在让我们仔细设计这个函数。由于数据表示需要两个数据定义，设计配方告诉你必须并行设计两个函数。不过，再仔细看一下会发现，在这种情况下，第二个数据定义与第一个无关，这意味着我们可以单独处理它。

此外，XItem.v1 的定义包含两个子句，这意味着函数本身也应该包含两个子句的 cond。然而，将 XItem.v1 视为 Xexpr 的子语言的要点是，用 Xexpr 选择器函数的术语来思考这两个子句，特别是 expr-content。有了这个函数，我们就可以提取项目的文本部分，而不管它是否带有属性：

```
; XItem.v1 -> Image
; renders an item as a "word" prefixed by a bullet
(define (render-item1 i)
  (... (expr-content i) ...))
```

一般来说，expr-content 提取一个 Xexpr 列表；在这种情况下，列表恰好包含一个 XWord，而这个词包含一个文本：

```
(define (render-item1 i)
  (local ((define content (expr-content i))
          (define element (first content))
          (define a-word (word-text element)))
    (... a-word ...)))
```

提取出要在项目中渲染的文本后，问题就变成了将其渲染为文本并添加前导项目符号；参见上面的示例，了解如何发现这一最后一步。

**练习 372。** 在继续阅读之前，为 render-item1 的定义添加测试。确保以不依赖 BT 常量的方式来制定这些测试。然后解释函数的工作原理；请记住，目的说明解释了函数的作用。

现在我们可以专注于设计渲染枚举的函数。使用上面的示例，前两个设计步骤很容易：

```
; XEnum.v1 -> Image
; renders a simple enumeration as an image
(check-expect (render-enum1 e0) e0-rendered)
(define (render-enum1 xe) empty-image)
```

关键步骤是开发模板。根据数据定义，XEnum.v1 的一个元素包含一个有趣的数据，即（XML 元素的）表示。第一项始终是 'ul，因此无需提取它，第二个可选项是属性列表，我们忽略它。考虑到这一点，第一个模板草稿与 render-item1 的模板类似：

```
(define (render-enum1 xe)
  (... (xexpr-content xe) ...)) ; [List-of XItem.v1]
```

虽然面向数据的设计配方告诉你，每当遇到复杂的数据形式时都应该设计一个单独的函数，但第三部分中的基于抽象的设计配方告诉你，尽可能复用现有的抽象，例如来自图 95 和 96 的列表处理函数。鉴于 render-enum1 应该处理列表并从中创建单个图像，唯二符合要求的列表处理抽象是 foldr 和 fold1。如果你还研究它们的目的说明，你会看到一种与上面的 e0-rendered 示例类似的模式，尤其是 foldr。让我们尝试使用它，遵循复用设计配方：

```
(define (render-enum1 xe)
  (local ((define content (xexpr-content xe))
          ; XItem.v1 Image -> Image
          (define (deal-with-one item so-far)
            ...))
    (foldr deal-with-one empty-image content)))
```

从类型匹配来看，你还知道：

- foldr 的第一个参数必须是一个双参数函数；

