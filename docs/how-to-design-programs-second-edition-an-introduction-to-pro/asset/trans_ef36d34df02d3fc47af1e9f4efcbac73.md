

```
(define (height.v2 abt0)
 (local (; Tree -> N
          ; measures the height of abt
          ; accumulator ...
         (define (height/a abt a)
           (cond
             [(empty? abt) ...]
             [else
              (... (height/a (node-left abt)
                             ... a ...) ...)
              ... (height/a (node-right abt)
                            ... a ...) ...]]))
   (height/a abt0 ...)))
```

始终如一，问题是确定累加器代表什么知识。一个明显的选择是已遍历的分支数：

a 是从 abt0 到 abt 所需的步骤数。

用图形示例来说明这个累加器不变式最为合适。再看一眼图 184。最底部的树带有两个注释，每个都指向一棵子树：

- 1. 如果 abt0 是完整树且 abt 是被带圈的 1 指向的子树，累加器的值必须为 1，因为从 abt 的根到 abt0 的根正好需要一步。

- 2. 出于同样的理由，对于标记为 2 的子树，累加器为 2，因为到达这个位置需要两步。

与前两个示例一样，不变式基本上规定了如何遵循累加器设计配方的其余部分：a 的初始值为 0；更新操作是 add1；基本情况使用累积的知识，直接返回它。将其转换为代码会产生以下骨架定义：

```
(define (height.v2 abt0)
  (local (; Tree N -> N
          ; measures the height of abt
          ; accumulator a is the number of steps
          ; it takes to reach abt from abt0
          (define (height/a abt a)
            (cond
              [(empty? abt) a]
              [else
               (... (height/a (node-left abt)
                              (+ a 1)) ...
               ... (height/a (node-right abt)
                             (+ a 1)) ...]]))
  (height/a abt0 0)))
```

但是，与前两个示例不同，a 不是最终结果。在第二个 cond 分句中，两个递归调用产生两个值。结构化函数的设计配方规定，我们需要将这些值组合起来，以此为情况制定答案；上面的省略号表示我们仍需选择一个操作来组合这些值。

遵循设计配方还告诉我们，需要解释这两个值以找到合适的函数。根据 height/a 的目的说明，第一个值是左子树的高度，第二个值是右子树的高度。鉴于我们关心的是 abt 本身的高度，而高度是到达叶节点所需的最大步数，我们使用 max 函数来选择合适的那个；完整定义请参见图 185。

```
; Tree -> N
; measures the height of abt0
(check-expect (height.v2 example) 3)
(define (height.v2 abt0)
  (local (; Tree N -> N
          ; measures the height of abt
          ; accumulator a is the number of steps
          ; it takes to reach abt from abt0
          (define (height/a abt a)
            (cond
              [(empty? abt) a]
              [else
               (max
                (height/a (node-left abt) (+ a 1))
                (height/a (node-right abt) (+ a 1)))]))
              (height/a abt0 0)))
```

## 图 185：采用累加器样式的 *高度* 版本

**关于另一种设计的说明** 除了计算到达节点所需的步骤数之外，累加器函数还可以保存迄今遇到的最大高度。以下是该设计思路的累加器说明：

第一个累加器表示从 abt0 的根到 abt 所需的步骤数。第二个累加器表示 abt0 中严格位于 abt 左侧的部分的高度。

显然，此说明假设了一个带有两个累加器参数的模板，这是我们之前未曾遇到过的：

```
... ; Tree N N -> N
; measures the height of abt
; accumulator s is the number of steps
; it takes to reach abt from abt0
; accumulator m is the maximal height of
; the part of abt0 that is to the left of abt
(define (h/a abt s m)
(cond
[(empty? abt) ...]
[else
(... (h/a (node-left abt)
... s ... ... m ...) ...]
... (h/a (node-right abt)
... s ... ... m ...) ...)]))
```

练习 498. 完成 height.v3。提示 图 184 中最底部的树在标记为 1 的子树左侧不包含子树。它在标记为 2 的子树左侧的树部分中包含一条从根到叶子的完整路径；这条路径由两步组成。

与第一个设计相比，第二个设计具有更复杂的累加器不变式。因此，其实现需要更加小心。同时，它没有任何明显的优势。

我们的观点是，不同的累加器不变式会产生不同的变体。您可以遵循相同的设计配方，系统地设计这两个变体。当您拥有完整的函数定义后，可以比较和对比结果，然后根据证据决定保留哪一个。结束

练习 499. 设计 product 的累加器样式版本，该函数计算数字列表的乘积。在制定累加器不变式并请他人检查后停止。

product 的性能为 O(n)，其中 n 是列表的长度。累加器版本能改进这一点吗？

练习 500. 设计 how-many 的累加器样式版本，该函数确定列表中的项目数量。在制定不变式并请他人检查后停止。

how-many 的性能为 O(n)，其中 n 是列表的长度。累加器版本能改进这一点吗？

当您手动求值 (how-many some-non-empty-list) 时，当函数到达 '() 时，n 个 add1 调用处于挂起状态——n 是列表中的项目数。计算机科学家有时说 how-many 需要 O(n) 空间来表示这些挂起的函数调用。累加器能减少计算结果所需的空间吗？

## 练习 501. 设计 add-to-pi 的累加器样式版本。该函数将自然数加到 pi 上，且不使用 +：

```
; N -> Number
; adds n to pi without using +
(check-within (add-to-pi 2) (+ 2 pi) 0.001)
(define (add-to-pi n)
  (cond
    [(zero? n) pi]
    [else (add1 (add-to-pi (sub1 n)))]))
```

在制定累加器不变式并请他人检查后停止。

## 练习 502. 设计函数 palindrome，它接受一个非空列表，通过围绕最后一项镜像列表来构造回文。当给定 (explode "abc") 时，它会生成 (explode "abcba")。

提示 以下是通过函数组合设计的解决方案：

```
; [NEList-of 1String] -> [NEList-of 1String]
; creates a palindrome from s0
(check-expect
 (mirror (explode "abc")) (explode "abcba"))
(define (mirror s0)
  (append (all-but-last s0)
          (list (last s0))
          (reverse (all-but-last s0))))
```

参见第 11.4 章了解 last；以类似的方式设计 all-but-last。

此解决方案遍历 s0 四次：

- 1. 通过 all-but-last，
- 2. 通过 last，
- 3. 再次通过 all-but-last，以及
- 4. 通过 reverse，这是 ISL+ 中 invert 的版本。

即使为 all-but-last 的结果设置局部定义，该函数仍需要三次遍历。虽然这些遍历不是“堆叠”的，因此对函数性能没有灾难性影响，但累加器版本可以通过单次遍历计算出相同的结果。

**练习 503** 练习 467 隐含地要求设计一个函数，该函数旋转一个矩阵，直到第一行的第一个系数不同于 0。在练习 467 的上下文中，该解决方案要求一个生成递归函数，当在第一个位置遇到 0 时，它通过将第一行移到末尾来创建一个新矩阵。以下是解决方案：

```
; Matrix -> Matrix
; finds a row that doesn’t start with 0 and
; uses it as the first one
; **generative** moves the first row to last place
; **no termination** if all rows start with 0
(check-expect (rotate-until.v2 '((0 4 5) (1 2 3)))
               '((1 2 3) (0 4 5)))

(define (rotate M)
  (cond
    [(not (= (first (first M)) 0)) M]
    [else
     (rotate (append (rest M) (list (first M))))]))
```

停止！修改此函数，以便当所有行都以 0 开头时发出错误。

如果您在大规模的 Matrix 实例上测量此函数，您会得到一个令人惊讶的结果：

