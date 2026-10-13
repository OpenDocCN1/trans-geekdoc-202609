
# Julia 数组切片、视图与广播操作

## 数组切片与内存分配

```julia
julia> b = a[1:2, :]
2×3 Matrix{Int64}:
 1  4  7
 2  5  8

julia> b[1, 2] = 10
10

julia> b
2×3 Matrix{Int64}:
 1  10  7
 2   5  8

julia> a
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9
```

使用索引进行切片操作会分配新数组。如上所示，修改数组 `b` 不会影响数组 `a` 中的数据。这会导致大量内存分配，并可能碎片化应用程序内存池。其次，非增值分配会影响性能。让我们重写该示例：

## 使用 `@view` 宏创建视图

```julia
julia> v = @view a[1:2, :]
2×3 view(::Matrix{Int64}, 1:2, :) with eltype Int64:
 1  4  7
 2  5  8

julia> v[1, 2] = 10
10

julia> v
2×3 view(::Matrix{Int64}, 1:2, :) with eltype Int64:
 1  10  7
 2   5  8
```

宏 `@view`（我们将在后续章节讨论宏）在引用数组 `a` 的相同对象的同时，在数组周围创建一个视图。由于视图没有自己的数据，修改视图也会导致底层容器数组中的数据被修改。

```julia
julia> a
3×3 Matrix{Int64}:
 1  10  7
 2   5  8
 3   6  9
```

## 矩阵运算

让我们看一些矩阵运算。

```julia
julia> a = reshape(collect(1:9), 3, 3)
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9

julia> b = reshape(collect(9:-1:1), 3, 3)
3×3 Matrix{Int64}:
 9  6  3
 8  5  2
 7  4  1

julia> a + b
3×3 Matrix{Int64}:
 10  10  10
 10  10  10
 10  10  10
```

数组 `a` 的每个元素都与数组 `b` 的对应元素相加，最终结果是一个与输入数组维度相同的数组。这之所以可行，是因为对于矩阵或数组，运算符 `+` 被定义为逐元素操作。让我们看看乘法运算或运算符 `*`。

```julia
julia> a * b
3×3 Matrix{Int64}:
  90  54  18
 114  69  24
 138  84  30
```

返回的结果不是逐元素乘法，而是矩阵乘法，也称为**数组内积**。如果我们要对数组进行逐元素操作，可以使用 `broadcast` 方法。

```julia
julia> broadcast(*, a, b)
3×3 Matrix{Int64}:
  9  24  21
 16  25  16
 21  24   9
```

同样的操作也可以用内联点号语法（`.*`）表示。

```julia
julia> a .* b
3×3 Matrix{Int64}:
  9  24  21
 16  25  16
 21  24   9
```

如果数组 `a` 和 `b` 大小不同会怎样？它们能在元素层面交互吗？保持 `a` 不变，让我们把 `b` 变成行向量和列向量并观察结果。

```julia
julia> a = reshape(collect(1:9), 3, 3)
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9

julia> b = [1 2 3]
1×3 Matrix{Int64}:
 1  2  3

julia> a .+ b
3×3 Matrix{Int64}:
 2  6  10
 3  7  11
 4  8  12
```

同样地，当 `b` 是列向量时：

```julia
julia> b = [1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> a .+ b
3×3 Matrix{Int64}:
 2  5  8
 4  7  10
 6  9  12
```

当其中一个数组是行向量或列向量时，如果维度在该方向上与另一个向量匹配，它们会沿着向量长度进行广播。虽然是在数组上下文中讨论的，但广播可以应用于任何集合类型。以下示例展示了跨集合的字符串逐元素连接。

```julia
julia> broadcast(string, ("one","two","three","four"), ": ", 1:4)
4-element Vector{String}:
 "one: 1"
 "two: 2"
 "three: 3"
 "four: 4"
```

```julia
# 你可以将前面的示例写为：
# string.(("one","two","three","four"), ": ", 1:4)
# string 后面的点号 (.) 会调用 broadcast 方法。
```

`": "` 只有一个条目，它重复 4 次以便与其他被广播的集合保持一致的映射。

## `broadcast` 与 `repeat` 的对比

有人可能会想，`broadcast` 的效果可以用 `repeat` 轻松模拟。`repeat` 接受数组的元素，并沿指定的各个维度重复它们。

```julia
julia> v = [1, 2]
2-element Vector{Int64}:
 1
 2

julia> repeat(v, 2, 3)  # 在维度 1 重复两次，维度 2 重复三次
4×3 Matrix{Int64}:
 1  1  1
 2  2  2
 1  1  1
 2  2  2
```

这种说法不完全错。然而，每次调用 `repeat` 都会分配数组，并带来性能惩罚。`broadcast` 消除了这种额外分配的需求。

```julia
julia> a + repeat(b, 1, 3)
3×3 Matrix{Int64}:
 2  5  8
 4  7  10
 6  9  12
```

## `map` 与 `broadcast` 的区别

在讨论 `broadcast` 时，重新审视我们之前讨论的 `map` 函数是有价值的。与 `broadcast` 在需要时重复元素不同，`map` 函数执行一对一映射。如下例所示，`map` 函数只返回一个长度为 3 的数组，匹配 `a` 和 `b` 的最小维度。

```julia
julia> a
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9

julia> b
3-element Vector{Int64}:
 1
 2
 3

julia> map(+, a, b)
3-element Vector{Int64}:
 2
 4
 6
```

## 数组归约操作

数组上的归约操作类似于汇总。类似于数据库聚合和 `GROUP BY` 子句，可以沿行和列对数组进行聚合。将数组元素映射到特定函数并按行和列归约结果是相当常见的结果。就像 `broadcast`、`map` 和 `reduce` 方法一样，确保中间分配最小化。
