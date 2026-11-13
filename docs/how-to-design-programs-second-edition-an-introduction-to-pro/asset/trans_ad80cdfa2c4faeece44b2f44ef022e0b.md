

(define-struct with [lft info rght])
(define-struct binary [lft rgt])

假设函数消耗一个 LOD 和一个 TID，你应该构建的表格形状如下：

| | (empty? l) | (cons? l) |
|---|---|---|
| (symbol? t) | | |
| (binary? t) | | |
| (with? t) | | |

沿水平方向，我们枚举识别第一个参数（此处为 LOD）子类的条件；沿垂直方向，我们枚举第二个参数 TID 的条件。

该表格指导函数示例和函数模板的开发。如所述，示例必须覆盖所有可能的情况；也就是说，表格中的每个单元格至少应有一个示例。同样，模板必须为每个单元格包含一个 cond 子句；其条件将水平和垂直条件组合在一个 and 表达式中。每个 cond 子句反过来必须包含两个参数的所有可行选择器表达式。如果其中一个参数是原子，则无需选择器表达式。最后，你需要了解可行的自然递归。一般而言，所有可能的选择器表达式组合（以及可选的原子参数）都是自然递归的候选项。因为我们无法知道哪些是必要的、哪些不是，所以我们在编码步骤中牢记它们。

总之，多参数函数的设计只是旧设计配方主题的一个变体。关键思想是将数据定义转换为一个表格，展示所有可行且有趣的组合。函数示例和模板的开发尽可能地利用该表格。

## 23.6 手指练习：两个输入

- **练习 393.** 图 62 展示了有限集的两个数据定义。为你选择的有限集表示设计 union 函数。它消耗两个集合，并产生一个包含两者元素的集合。

  为相同的集合表示设计 intersect 函数。它消耗两个集合，并产生恰好包含在两个集合中都出现的元素的集合。

- **练习 394.** 设计 merge 函数。该函数消耗两个按升序排列的数字列表。它产生一个包含两个输入列表上所有数字的单一排序数字列表。一个数字在输出中出现的次数等于它在两个输入列表中出现的次数之和。

- **练习 395.** 设计 take 函数。它消耗一个列表 l 和一个自然数 n。它产生 l 中的前 n 个项，或者如果 l 太短则产生 l 中的所有项。

  设计 drop 函数。它消耗一个列表 l 和一个自然数 n。其结果是移除了前 n 个项的 l，或者如果 l 太短则产生 '()'。

- **练习 396.** 猜词游戏是一款广为人知的猜词游戏。一名玩家选出一个单词，另一名玩家会被告知该单词包含多少个字母。后者选出一个字母，并询问第一名玩家该字母是否以及在所选单词的哪个位置出现。游戏在商定好的时间或轮数结束后结束。

  图 136 展示了限时版本的游戏精髓。有关 checked-compare 为何在本地定义，请参见第 16.3 节。

```
; An HM-Word is a [List-of Letter or "_"]
; interpretation "_" represents a letter to be guessed

; HM-Word N -> String
; runs a simplistic hangman game, produces the current state
(define (play the-pick time-limit)
  (local ((define the-word (explode the-pick))
          (define the-guess (make-list (length the-word) "_"))
          ; HM-Word -> HM-Word
          (define (do-nothing s) s)
          ; HM-Word KeyEvent -> HM-Word
          (define (checked-compare current-status ke)
            (if (member? ke LETTERS)
                (compare-word current-status ke)
                current-status)))

  (implode
    (big-bang the-guess ; HM-Word
              [to-draw render-word]
              [on-tick do-nothing 1 time-limit]
              [on-key checked-compare])))

; HM-Word -> Image
(define (render-word w)
  (text (implode w) 22 "black"))
```

### 图 136：简单的猜词游戏

本练习的目标是设计 compare-word，即核心函数。它消耗要猜的单词、一个表示猜测玩家已发现多少/少的单词 s，以及当前猜测。该函数产生 s，并将其中猜测揭示出字母的所有 "_" 替换为该字母。

一旦你设计好了该函数，请像这样运行程序：

```
(define LOCATION "/usr/share/dict/words") ; on OS X
(define AS-LIST (read-lines LOCATION))
(define SIZE (length AS-LIST))
(play (list-ref AS-LIST (random SIZE)) 10)
```

请参见图 74 获取解释。欢迎按需享受并完善！▪

- **练习 397.** 在一家工厂里，员工到达时和离开时都要打卡。电子打卡卡包含员工编号，并记录每周工作的小时数。员工记录始终包含员工姓名、员工编号和薪资标准。

  设计 wages*.v3 函数。该函数消耗一个员工记录列表和一个打卡记录列表。它产生一个工资记录列表，包含员工姓名和每周工资。如果找不到某张打卡卡对应的员工记录，或反之，则函数会报错。

  **假设** 每个员工编号最多有一张打卡卡。

- **练习 398.** 线性组合是多个线性项的和，即变量和数字的乘积。在此语境中，后者称为系数。以下是一些示例：

  - 5 · x
  - 5 · x + 17 · y
  - 5 · x + 17 · y + 3 · z

  在所有示例中，x 的系数是 5，y 的系数是 17，z 的系数是 3。

  如果给定变量的值，我们可以确定多项式的值。例如，如果 x = 10，则 5 · x 的值为 50；如果 x = 10 且 y = 1，则 5 · x + 17 · y 的值为 67；如果 x = 10、y = 1 且 z = 2，则 5 · x + 17 · y + 3 · z 的值为 73。

  线性组合有多种不同的表示方式。例如，我们可以使用函数来表示它们。另一种表示方式是系数列表。上述组合将表示为：

  ```
  (list 5)
  (list 5 17)
  (list 5 17 3)
  ```

  这种表示选择假设变量的顺序固定。

  设计 value 函数。该函数消耗两个等长列表：一个线性组合和一个变量值列表。它为这些值产生组合的值。

- **练习 399.** Louise、Jane、Laura、Dana 和 Mary 决定举办一场抽奖，为每人分配一名礼物接收者。由于 Jane 是开发者，她们请她编写一个以公平方式执行此任务的程序。当然，程序不能将任何姐妹分配给她自己。

  以下是 Jane 程序的核心：

  ```
  ; [List-of String] -> [List-of String]
  ; picks a random non-identity arrangement of names
  (define (gift-pick names)
  (random-pick
  (non-same names (arrangements names)))
  ```

  ```
  ; [List-of String] -> [List-of [List-of String]]
  ; returns all possible permutations of names
  ; see exercise 213
  ```

  ```
  (define (arrangements names)
  ...)
  ```

  它消耗一个名称列表，并随机选择一个与原列表在任何位置都不一致的排列。

  你的任务是设计两个辅助函数：

  ```
  ; [NEList-of X] -> x
  ; returns a random item from the list
  ```

  ```
  (define (random-pick l)
  (first l))
  ```

  ```
  ; [List-of String] [List-of [List-of String]]
  ; ->
  ; [List-of [List-of String]]
  ; produces the list of those lists in ll that do
  ; not agree with names at any place
  ```

  ```
  (define (non-same-names ll)
  ll)
  ```

  请回顾 random 随机选取一个数字；参见练习 99。

- **练习 400.** 设计 DNAprefix 函数。该函数接受两个参数，均为 'a、'c、'g 和 't 符号的列表，这些符号出现在 DNA 描述中。第一个列表称为模式，第二个列表称为搜索字符串。如果模式与搜索字符串的初始部分相同，则函数返回 #true；否则返回 #false。

  还要设计 DNAdelta 函数。此函数类似于 DNAprefix，但返回模式之后搜索字符串中的第一个项目。如果列表相同且模式之后没有 DNA 字母，则函数报错。如果模式与搜索字符串的开头不匹配，则返回 #false。该函数不得遍历任一列表多次。

