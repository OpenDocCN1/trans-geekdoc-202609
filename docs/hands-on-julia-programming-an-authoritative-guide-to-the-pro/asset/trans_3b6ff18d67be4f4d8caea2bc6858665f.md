

## Julia 代码示例：`attacks_with_reason` 函数

```julia
julia> function attacks_with_reason(x1, y1, x2, y2)
           if x1 == x2
               return true, :x
           elseif y1 == y2
               return true, :y
           elseif x1 - y1 == x2 - y2
               return true, :diag
           elseif x1 + y1 == x2 + y2
               return true, :xdiag
           else
               return false, :na
           end
       end
attacks_with_reason (generic function with 1 method)

julia> attacks_with_reason(1, 2, 3, 4)
(true, :diag)

julia> attacks_with_reason(1, 2, 3, 1)
(false, :na)

julia> attacks_with_reason(1, 2, 3, 2)
(true, :y)

julia> attacks_with_reason(1, 2, 2, 1)
(true, :xdiag)
```

# 递归与 N 皇后问题

递归是函数式编程中常用的编程范式，在 Julia 中同样流行。在递归编程中，遵循以下过程：

1. 函数应针对问题的一个子集调用自身。
2. 必须有一个确定的终止条件，使递归停止。
3. 结果需聚合以呈现输出。

我们将把所有这些条件应用于开发 8 皇后谜题的解决方案。到目前为止，我们已经找到了一种判断一个皇后是否攻击另一个皇后的机制。我们将通过从上到下逐行递归地添加皇后来解决该问题。假设我们考虑一个 8×8 的棋盘。

1. 我们将考虑第 8 行，并从第 1 列开始在第 8 行放置一个皇后。
2. 然后我们将皇后放在第 7 行。
    1. 我们从第 1 列开始不断增加列号，以便在某一列放置皇后，使其不攻击其他皇后。我们将使用之前开发的 `attacks` 函数来实现这一点。
    2. 如果可以放置皇后，则放置它，并递归调用函数以检查是否可以在第 6 行放置皇后，依此类推，直到第 5 行、第 4 行，直到到达第 1 行。
    3. 如果无法放置皇后，则跳过该行。
        同样，我们继续将皇后添加到第 5 行、第 4 行等，直到到达第 1 行。
3. 如果我们能在第 1 行成功添加皇后，则返回 0。
4. 如果我们无法在某一行添加皇后，则返回 -1。
5. 当我们无法在某一行添加皇后时，我们回溯，尝试在前一行的不同位置添加皇后，并重复该过程。
6. Julia 的 `varargs` 函数作为递归方法非常有用，因为它提供了一种自然的机制来跟踪所有已添加的列。

该方法不局限于标准棋盘上的 8 皇后问题，也可用于任意大小的棋盘，即 N 皇后问题。

## 核心实现代码

```julia
julia> attacks(x1, y1, x2, y2) =
           (x1 == x2 || y1 == y2 || x1 - y1 == x2 - y2 ||
            x1 + y1 == x2 + y2)
attacks (generic function with 1 method)

julia> function queens(N, xs…)
           lxs = length(xs)
           c = N - lxs                                              ## Step 6
           if c == 0                                                ## Step 3
               println("Final Positions: ", reverse(xs))
               return 0
           end
           for i = 1:N                                              ## Step 1 & 2
               res = false                                          ## Step 2(a)
               for j = 1:lxs
                   res = res || attacks(xs[j], N - j + 1, i, c)
               end
               res && continue
               v = queens(N, xs…, i)                                ## Step 2(c)
               v < 0 || return v
           end
           return -1                                                ## Step 4
       end
queens (generic function with 1 method)
```

## 运行示例

```julia
julia> queens(8)
Final Positions: (4, 2, 7, 3, 6, 8, 5, 1)
0
```

为了观察 `varargs` 作为递归一部分的行为，可以在函数开头添加一条 `println` 语句。

```julia
julia> function queens(N, xs…)
           println(xs)
           lxs = length(xs)
           c = N - lxs
           …
       end
```

`queens(8)` 的输出如下：

```julia
julia> queens(8)
()
(1,)
(1, 3)
(1, 3, 5)
(1, 3, 5, 2)
(1, 3, 5, 2, 4)
(1, 3, 5, 2, 8)
(1, 3, 5, 7)
…
(1, 5, 7, 2)
(1, 5, 7, 2, 4)
(1, 5, 7, 2, 4, 8)
(1, 5, 7, 2, 6)
(1, 5, 7, 2, 6, 3)
(1, 5, 7, 2, 6, 8)
(1, 5, 8)
(1, 5, 8, 2)
(1, 5, 8, 2, 4)
(1, 5, 8, 2, 4, 7)
(1, 5, 8, 2, 4, 7, 3)
(1, 5, 8, 2, 7)
(1, 5, 8, 2, 7, 3)
(1, 5, 8, 2, 7, 3, 6)
(1, 5, 8, 6)
(1, 5, 8, 6, 3)
(1, 5, 8, 6, 3, 7)
(1, 5, 8, 6, 3, 7, 2)
(1, 5, 8, 6, 3, 7, 2, 4)
Final Positions: (4, 2, 7, 3, 6, 8, 5, 1)
0
```

![图 4.2：代码输出的解决方案](n4upl4fndqn.jpeg)

**图 4.2：** 代码输出的解决方案

# 累积和计算

让我们看看为任意自然数计算累积和的代码。

