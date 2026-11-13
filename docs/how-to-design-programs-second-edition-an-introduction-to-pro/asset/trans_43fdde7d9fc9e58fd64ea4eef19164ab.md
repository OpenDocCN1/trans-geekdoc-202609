
这个特殊值。

我们的实验得出两个结论。首先，我们寻找的**不是**描述如何生成子结构实例的数据定义，而是描述如何表示家谱的数据定义。其次，该数据定义包含两个子句，一个用于描述未知家谱的变体，另一个用于描述已知家谱：

```
(define-struct no-parent [])
(define-struct child [father mother name date eyes])
; An FT (short for *family tree*) is one of:
; -- (make-no-parent)
; -- (make-child FT FT String N String)
```

由于“无父母”树将在我们的程序中频繁出现，我们将 NP 定义为简写形式，并对数据定义做了一点修改：

```
(define NP (make-no-parent))
; An FT is one of:
; -- NP ;
; -- (make-child FT FT String N String)
```

按照第 9 章的设计配方，我们使用数据定义来创建家谱示例。具体来说，我们将图 111 中的家谱翻译成我们的数据表示。Carl 的信息很容易翻译成数据：

```
(make-child NP NP "Carl" 1926 "green")
```

Bettina 和 Fred 使用类似的 child 实例表示。Adam 的情况需要嵌套子项，一个是 Carl，一个是 Bettina：

```
(make-child (make-child NP NP "Carl" 1926 "green")
                (make-child NP NP "Bettina" 1926 "green")
                "Adam"
                1950
                "hazel")
```

由于 Carl 和 Bettina 的记录也用于构建 Dave 和 Eva 的记录，因此最好引入命名特定 child 实例的定义，并在其他地方使用变量名。图 112 说明了这种方法，用于图 111 中家谱的完整数据表示。请仔细观察；该树将作为后续设计练习的运行示例。

```
; Oldest Generation:
(define Carl (make-child NP NP "Carl" 1926 "green"))
(define Bettina (make-child NP NP "Bettina" 1926 "green"))

; Middle Generation:
(define Adam (make-child Carl Bettina "Adam" 1950 "hazel"))
(define Dave (make-child Carl Bettina "Dave" 1955 "black"))
(define Eva (make-child Carl Bettina "Eva" 1965 "blue"))
(define Fred (make-child NP NP "Fred" 1966 "pink"))

; Youngest Generation:
(define Gustav (make-child Fred Eva "Gustav" 1988 "brown"))
```

图 112：示例家谱的数据表示

与其直接设计针对家谱的具体函数，不如先看看这种函数的通用组织方式。也就是说，在没有具体任务的情况下，尽可能地按照设计配方进行。我们从头部材料开始，即配方的第 2 步：

```
; FT -> ???
; ...
(define (fun-FT an-ftree) ...)
```

尽管我们没有说明函数的用途，但我们知道它接受一个家谱，并且这种形式的数据是主要输入。签名中的“???”表示我们不知道函数会产生什么类型的数据；“...”提醒我们不知道它的用途。

缺乏用途意味着我们无法编造功能示例。尽管如此，我们可以利用 FT 数据定义的组织方式来设计模板。由于它包含两个子句，因此模板必须包含一个带有两个子句的 cond 表达式：

```
(define (fun-FT an-ftree)
(cond
[(no-parent? an-ftree) ...]
[else ...]))
```

如果 fun-FT 的参数满足 no-parent?，则该结构不包含其他数据，因此第一个子句是完整的。对于第二个子句，输入包含五个数据项，我们在模板中使用五个选择器来表示它们：

```
; FT -> ???
(define (fun-FT an-ftree)
(cond
[(no-parent? an-ftree) ...]
[else (... (child-father an-ftree) ...
... (child-mother an-ftree) ...
... (child-name an-ftree) ...
... (child-date an-ftree) ...
... (child-eyes an-ftree) ...)]))
```

模板的最后一个补充涉及自引用。如果数据定义引用其自身，则函数可能会递归，模板会通过暗示性的自然递归来指示这一点。FT 的定义包含两个自引用，因此模板需要两个这样的递归：

```
; FT -> ???
(define (fun-FT an-ftree)
(cond
[(no-parent? an-ftree) ...]
[else (... (fun-FT (child-father an-ftree)) ...
... (fun-FT (child-mother an-ftree)) ...
... (child-name an-ftree) ...
... (child-date an-ftree) ...
... (child-eyes an-ftree) ...)]))
```

具体来说，fun-FT 被应用于第二个 cond 子句中父母的数据表示，因为数据定义的第二个子句包含相应的自引用。

现在让我们转到一个具体示例，即 blue-eyed-child? 函数。其目的是确定给定家谱中的任何 child 结构是否有蓝眼睛。你可以复制、粘贴并重命名 fun-FT 以获取其模板；我们将“???”替换为 Boolean 并添加一个目的声明：

```
; FT -> Boolean
; does an-ftree contain a child
; structure with "blue" in the eyes field
(define (blue-eyed-child? an-ftree)
  (cond
    [(no-parent? an-ftree) ...]
    [else (... (blue-eyed-child?
                 (child-father an-ftree)) ...
                 ... (blue-eyed-child?
                     (child-mother an-ftree)) ...
                 ... (child-name an-ftree) ...
                 ... (child-date an-ftree) ...
                 ... (child-eyes an-ftree) ...)]))
```

采用这种工作方式时，必须将模板的通用名称替换为特定名称。

按照我们的配方进行检查，我们意识到在进入定义步骤之前，需要回溯并开发一些示例。如果从家谱中的第一个人 Carl 开始，我们看到 Carl 的家谱中不包含眼睛颜色为"blue"的 child。具体来说，表示 Carl 的 child 说明眼睛颜色是"green"；鉴于 Carl 的祖先树是空的，它们不可能包含眼睛颜色为"blue"的 child：

```
(check-expect (blue-eyed-child? Carl) #false)
```

相反，Gustav 包含一个子 child Eva，她确实有蓝眼睛：

```
(check-expect (blue-eyed-child? Gustav) #true)
```

现在我们准备好定义实际函数了。该函数区分两种情况：一种是 no-parent，另一种是 child。对于第一种情况，即使我们没有编造任何示例，答案也应该很明显。因为给定的家谱根本不包含任何 child，因此不可能包含眼睛颜色为"blue"的 child。因此，第一个 cond 子句的结果是 #false。

对于第二个 cond 子句，设计需要更多的工作。再次遵循设计配方，我们先提醒自己模板中的表达式完成什么：

- 1. 根据函数的目的声明，
   (blue-eyed-child? (child-father an-ftree))
   确定父亲的 FT 中是否有 child 的眼睛颜色为"blue"；
- 2. 同样，(blue-eyed-child? (child-mother an-ftree)) 确定母亲的 FT 中是否有人有蓝眼睛；以及
- 3. 选择器表达式 (child-name an-ftree)、(child-date an-ftree) 和 (child-eyes an-ftree) 分别从给定的 child 结构中提取名称、出生日期和眼睛颜色。

现在我们只需要弄清楚如何组合这些表达式。

显然，如果 child 结构的眼睛字段包含"blue"，则函数的答案是 #true。接下来，涉及名称和出生日期的表达式无用，只剩下递归调用。如所述，(blue-eyed-child? (child-father an-ftree)) 遍历父亲一方的树，而家谱的母亲一方则使用 (blue-eyed-child? (child-mother an-ftree)) 进行处理。如果其中任何一个表达式返回 #true，则 an-ftree 包含眼睛颜色为"blue"的 child。

我们的分析表明，如果以下三个表达式之一为 #true，则结果应为 #true：

- (string=? (child-eyes an-ftree) "blue")
- (blue-eyed-child? (child-father an-ftree))
- (blue-eyed-child? (child-mother an-ftree))

这反过来意味着我们需要使用 or 组合这些表达式：
