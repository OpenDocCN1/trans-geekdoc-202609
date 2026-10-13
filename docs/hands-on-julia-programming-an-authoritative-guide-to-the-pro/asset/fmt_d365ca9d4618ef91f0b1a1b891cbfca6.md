
# 索引表达式与维度

当索引表达式为向量或非标量时，会向输出引入额外的维度。以下是一些示例：

```
julia> a[1:2:3, 1:2:3, [1], [1]]
2×2×1×1 Array{Int64,4}:
[:, :, 1, 1] =
 1   9
 3  11
```

如前面的示例所示，创建的是一个 `2×2×1×1` 的数组，而不是 `2×2` 的数组。默认情况下，索引向量被假定为具有行向量的一维结构。

```
julia> a[1:2:3, [1; 3], 1, 1]
2×2 Matrix{Int64}:
 1   9
 3  11
julia> a[1:2:3, [1, 3], 1, 1]
2×2 Matrix{Int64}:
 1   9
 3  11
```

当索引不按行顺序排列时，输出将无法在此情况下合并为 `2×2` 矩阵：

```
julia> b = a[1:2:3, [1 3], 1, 1]
2×1×2 Array{Int64,3}:
[:, :, 1] =
 1
 3
[:, :, 2] =
 9
 11
```

生成了一个 `2×1×2` 的矩阵。同样，通过提供多维索引，可以创建更复杂的矩阵。

```
julia> a[:, [2], [1], [1]]
4×1×1×1 Array{Int64,4}:
[:, :, 1, 1] =
 5
 6
 7
 8
julia> a[[1 2; 3 4], [2], [1], [1]]
2×2×1×1×1 Array{Int64,5}:
[:, :, 1, 1, 1] =
 5  6
 7  8
```

这里，第一个索引中引入多维索引给矩阵增加了一个额外的维度。该矩阵具有 `2×2×1×1×1` 的维度。前两列是基于索引参数 `[1 2; 3 4]` 对 `a[:, [1], [1], [1]]` 的第 1 列进行重新排列得到的。

# 线性索引

我们在上一章讨论过，数组以行优先的方式存储在连续的内存位置中，索引作为底层数据的覆盖层进行操作。底层数据可以作为单个整数索引访问。这种索引方式称为 `linear indexing`（线性索引）。

```
julia> a = reshape(collect(1:6), (2, 3))
2×3 Matrix{Int64}:
 1  3  5
 2  4  6
julia> a[5]
5
julia> a[1, 3]
5
```

存在一个名为 `LinearIndices` 的类型，有助于创建这种映射。

```
julia> LinearIndices(a)
2×3 LinearIndices{2,Tuple{Base.OneTo{Int64},Base.OneTo{Int64}}}:
 1  3  5
 2  4  6
```

# 笛卡尔索引

笛卡尔索引是一个数字元组，作为数组的维度来表示一个元素。

```
julia> A = reshape(collect(1:6), 3, 2)
3×2 Matrix{Int64}:
 1  4
 2  5
 3  6
julia> ci = CartesianIndices(A)
3×2 CartesianIndices{2,Tuple{Base.OneTo{Int64},Base.OneTo{Int64}}}:
 CartesianIndex(1, 1)  CartesianIndex(1, 2)
 CartesianIndex(2, 1)  CartesianIndex(2, 2)
 CartesianIndex(3, 1)  CartesianIndex(3, 2)
```

使用笛卡尔索引还是线性索引取决于对象和数据的组织方式。随着我们查看视图和子数组，稍后将进一步回顾这些主题的细节。

# 布尔索引

布尔索引更像是作用于数据的过滤器。

```
julia> x = reshape(collect(1:16), 4, 4)
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16
julia> filter = map(ispow2, x)
4×4 Matrix{Bool}:
 1  0  0  0
 1  0  0  0
 0  0  0  0
 1  1  0  1
julia> x[filter]
5-element Vector{Int64}:
  1
  2
  4
  8
 16
```

虽然逻辑索引似乎仅用于选取过滤器值为 `true` 的特定值，但结合范围索引可以观察到有趣的变化。例如，以下示例完整选取了第 2 行和第 3 行。

```
julia> x[[false, true, true, false], :]
2×4 Matrix{Int64}:
 2  6  10  14
 3  7  11  15
```

# 赋值索引

我们处理的大多数索引示例都与从数组中提取信息有关，即所谓的 `l-valued expressions`（左值表达式）。然而，类似的表达式也可用于为数组元素赋值。

```
julia> a = reshape(collect(1:24), 4, 3, 2, 1);
julia> a[:, 2, 1, 1] = fill(25, 4)
4-element Vector{Int64}:
 25
 25
 25
 25
julia> a
4×3×2×1 Array{Int64,4}:
[:, :, 1, 1] =
 1  25   9
 2  25  10
 3  25  11
 4  25  12
[:, :, 2, 1] =
 13  17  21
 14  18  22
 15  19  23
 16  20  24
```

# `begin` 和 `end` 关键字索引

为了方便在集合中遍历，有时会使用 `begin` 和 `end` 等专用关键字作为索引。甚至可以将这些索引与某些数值运算结合使用。前面数组的元素可以按如下方式访问：

```
julia> a[begin, :, 2, 1], a[begin+1, :, 2, 1]
([13, 17, 21], [14, 18, 22])

julia> a[end, :, 2, 1], a[end-1, :, 2, 1]
([16, 20, 24], [15, 19, 23])
```

# 索引访问相关方法

以下方法针对数组或所有支持索引访问元素的集合（如 `Dict`）定义。

- `getindex(X, i)`：当访问 `X[i]` 时，返回位置 `i` 处元素的值。在多维数组中，当访问 `X[I_1, I_2, …, I_n]` 时，扩展为使用表达式 `getindex(X, I_1, I_2, …, I_n)`。
- `setindex!(X, v, i)`：将值 `v` 赋给位置 `i` 处的数组元素。在多维数组中，表达式 `X[I_1, I_2, …, I_n] = v` 在内部会调用 `setindex!(X, v, I_1, I_2, …, I_n)`。
- `firstindex(X)`：提供使用表达式 `X[begin]` 时的索引。`firstindex(X, dim)` 也可用于特定维度 `dim`。
- `lastindex(X)`：提供使用表达式 `X[end]` 时的索引。与 `firstindex` 类似，`lastindex` 也可以接受维度作为参数。

```
julia> firstindex(a)
1
julia> lastindex(a)
24
julia> lastindex(a, 1)
4
julia> lastindex(a, 2)
3
julia> lastindex(a, 3)
2
julia> lastindex(a, 4)
1
```

# 切片

切片是通过指定索引来使用数组的一部分。以下是一些示例：

```
julia> a = reshape(collect(1:9), 3, 3)
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9
julia> a[:, 1]
3-element Vector{Int64}:
 1
 2
 3
julia> a[1, :]
3-element Vector{Int64}:
 1
 4
 7
julia> a[1, 2:3]
2-element Vector{Int64}:
 4
 7
```

虽然大多数示例都很简单，但我们想引起您对 `a[1, :]` 和 `a[1, 2:3]` 的注意。这两者本应是行矩阵。然而，Julia 会返回一个一维向量。
