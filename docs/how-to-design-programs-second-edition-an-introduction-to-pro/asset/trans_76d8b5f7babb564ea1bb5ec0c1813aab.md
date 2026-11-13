
包含任何行。第二个子句的答案必须将 (first-line afile) 的值 cons 到 (file->list-of-lines (remove-first-line afile)) 的值上，因为第一个表达式计算第一行，第二个表达式计算其余行。最后，辅助函数以结构递归的方式遍历其输入；它们的开发是一个简单的练习。图 160 展示了完整的程序代码。

```
; File -> [List-of Line]
; converts a file into a list of lines
(define (file->list-of-lines afile)
  (cond
    [(empty? afile) '()]
    [else
     (cons (first-line afile)
           (file->list-of-lines (remove-first-line afile)))]))
; File -> Line
(define (first-line afile)
  (cond
    [(empty? afile) '()]
    [(string=? (first afile) NEWLINE) '()]
    [else (cons (first afile) (first-line (rest afile)))]))
; File -> Line
(define (remove-first-line afile)
  (cond
    [(empty? afile) '()]
    [(string=? (first afile) NEWLINE) (rest afile)]
    [else (remove-first-line (rest afile))]))
(define NEWLINE "\\n") ; the 1String
```

## 图 160：将文件转换为行列表

下面展示 file->list-of-lines 如何处理第二个测试：

```
(file->list-of-lines
(list "a" "b" "c" "\\n" "d" "e" "\\n" "f" "g" "h" "\\n"))
```

```
(cons
  (list "a" "b" "c")
  (file->list-of-lines
   (list "d" "e" "\\n" "f" "g" "h" "\\n"))))
```

```
(cons
  (list "a" "b" "c")
  (cons (list "d" "e")
        (file->list-of-lines
         (list "f" "g" "h" "\\n")))))
```

```
(cons (list "a" "b" "c")
      (cons (list "d" "e")
            (cons (list "f" "g" "h")
                  (file->list-of-lines '())))))
```

```
(cons (list "a" "b" "c")
      (cons (list "d" "e")
            (cons (list "f" "g" "h")
                  '()))))
```

这次求值再次提醒我们，file->list-of-lines 递归调用的参数几乎从来不是给定文件的其余部分。它也说明了为什么这种生成递归对于任何给定的 File 都保证终止。每次递归调用都消耗一个比给定列表更短的列表，这意味着当过程到达 '() 时递归过程停止。

**练习 452.** `first-line` 和 `remove-first-line` 都缺少用途说明。请阐述合适的说明。

**练习 453.** 设计函数 `tokenize`。它将一个 Line 转换为一组 tokens。这里的 token 是一个 1String，或者仅由小写字母组成且不包含其他内容的 String。也就是说，所有空白 1Strings 都会被丢弃；所有其他非字母字符保持不变；所有连续的字母都被捆绑成“单词”。**提示** 查阅 string-whitespace? 函数。

**练习 454.** 设计 `create-matrix`。该函数消费一个数字 `n` 和一个包含 $n^2$ 个数字的列表。它生成一个 $n \times n$ 矩阵，例如：

```
(check-expect
 (create-matrix 2 (list 1 2 3 4))
 (list (list 1 2)
   (list 3 4)))
```

编造第二个示例。

## 28 数学示例

许多数学问题的解决方案都采用生成递归。未来的程序员必须了解此类解决方案，原因有二。一方面，相当多的编程任务本质上就是将这类数学思想转化为程序。另一方面，通过此类数学问题的练习，往往能为算法设计提供灵感。本章讨论三个此类问题。

### 28.1 牛顿法

第 27.2 节介绍了一种寻找数学函数根的方法。正如同一节中的练习所概述的，该方法自然地推广到计算问题，例如在表格、向量和数组中查找特定值。在数学应用中，程序员倾向于采用源自解析数学的方法。其中一个突出的方法源自牛顿。类似于二分查找，所谓的牛顿法反复改进对根的近似，直到它“足够接近”。从一个猜测开始，比如说 r1，该过程的本质是在 r1 处构造 f 的切线并确定其根。虽然切线近似函数，但确定其根也是直接的。通过充分重复此过程，算法可以找到一个根 r，使得 (f r) 足够接近 0。

> 牛顿证明了这一事实。

显然，这个过程依赖于关于切线的两个领域知识：它们的斜率和根。非正式地说，f 在某点 r1 处的切线是经过点 (r1, f (r1)) 并与 f 具有相同斜率的直线。获得切线斜率的一种数学方法是在 x 轴上选取两个彼此靠近且距 r1 等距的点，并使用 f 在该两点处确定的直线的斜率。惯例是选择一个很小的数 ε，并使用 r1 + ε 和 r1 - ε。也就是说，这些点是 (r1 - ε, f(r1 - ε)) 和 (r1 + ε, f(r1 + ε))，它们确定了一条直线和一个斜率：

```
slope(f, r_1) = \frac{f(r_1+\epsilon)-f(r_1-\epsilon)}{(r_1+\epsilon)-(r_1-\epsilon)} = \frac{1}{2\epsilon} \cdot (f(r_1 + \epsilon) - f(r_1 - \epsilon))
```

**练习 455.** 将此数学公式翻译为 ISL+ 函数 slope，该函数将函数 f 和数字 r1 映射到 f 在 r1 处的斜率。假设 ε 是全局常量。对于你的示例，使用你能算出确切斜率的函数，比如说，水平线、线性函数，以及如果你了解一些微积分，或许还有多项式。

第二个领域知识涉及切线的根，它只是一条直线或一个线性函数。切线经过 (r1, f (r1)) 并具有上述斜率。从数学上讲，它定义为

tangent(x) = slope(f, r₁) · (x - r₁) + f(r₁)

查找 tangent 的根意味着找到一个值 root-of-tangent，使得 tangent(root-of-tangent) 等于 0：

0 = slope(f, r₁) · (root-of-tangent - r₁) + f(r₁) .

我们可以以直接的方式求解此方程：

root-of-tangent = r₁ - \frac{f(r₁)}{slope(f, r₁)} .

**练习 456.** 设计 root-of-tangent，这是一个将 f 和 r1 映射到经过 (r1,(f r1)) 的切线根的函数。

现在我们可以使用设计食谱将牛顿过程的描述翻译为 ISL+ 程序。该函数——让我们以它的发明者之名称其为 newton——消费一个函数 f 和一个数字 r1：

```
; [Number -> Number] Number -> Number
; finds a number r such that (f r) is small
; generative repeatedly generates improved guesses
(define (newton f r1) 1.0)
```

对于 newton 的模板，我们转向生成递归设计食谱的核心四个问题：

- 1. 如果 (f r1) 足够接近 0，则问题已解决。接近 0 可能意味着 (f r1) 是一个很小的正数或很小的负数。因此我们检查其绝对值：
  (<= (abs (f r1)) )

- 2. 解是 r1。

- 3. 该算法的生成步骤包括查找 f 在 r1 处的切线的根，这会生成下一个猜测。通过将 newton 应用于 f 和这个新猜测，我们恢复该过程。

- 4. 递归的答案也是原问题的答案。

图 161 显示了 newton。它包含两个测试，这些测试源自第 27.2 节中针对 find-root 的测试。毕竟，这两个函数都在搜索函数的根，而 poly 有两个已知的根。

```
; [Number -> Number] Number -> Number
; finds a number r such that (<= (abs (f r)) ε)
(check-within (newton poly 1) 2 ε)
(check-within (newton poly 3 .5) 4 ε)

(define (newton f r1)
  (cond
    [(<= (abs (f r1)) ε) r1]
    [else (newton f (root-of-tangent f r1))]))

; see exercise 455
(define (slope f r) ...)

; see exercise 456
(define (root-of-tangent f r) ...)
```

## 图 161：牛顿过程

我们还没有完成 newton 的设计。设计食谱的新第七步要求调查函数的终止行为。对于 newton，问题出现在 poly 上：

```
; Number -> Number
(define (poly x) (* (- x 2) (- x 4)))
```

如前所述，它的根是 2 和 4。图 162 中 poly 的图表证实了这些根，并且还显示在两个根之间函数会趋于平坦。对于喜欢数学的人来说，这种形状引发了一个问题：当初始猜测为 3 时，newton 计算出什么：

```
> (poly 3)
-1
```
