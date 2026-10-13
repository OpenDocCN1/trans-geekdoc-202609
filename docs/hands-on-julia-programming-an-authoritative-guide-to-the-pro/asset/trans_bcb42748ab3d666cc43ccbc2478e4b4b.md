

# Julia 数组与关联集合操作

## 创建填充数组

给定类型和维度，函数会创建一个指定类型的、填充了零或一的 `Array`。

```julia
julia> zeros(Float32, (2, 3))
2×3 Matrix{Float32}:
 0.0  0.0  0.0
 0.0  0.0  0.0

julia> ones(Float32, (2, 3))
2×3 Matrix{Float32}:
 1.0  1.0  1.0
 1.0  1.0  1.0

julia> ones(UInt8, (2, 3))
2×3 Matrix{UInt8}:
 0x01  0x01  0x01
 0x01  0x01  0x01
```

让我们看看以下两段代码的对比：

```julia
julia> zb = zeros(Bool, (8, 8))
8×8 Matrix{Bool}:
 0  0  0  0  0  0  0  0
 …
 0  0  0  0  0  0  0  0

julia> sizeof(zb)
64
```
可以看到，一个 `Bool` 变量占用 1 字节存储空间，因此该数组需要 64 字节的数据空间。

```julia
julia> z = falses(8, 8)
8×8 BitMatrix:
 0  0  0  0  0  0  0  0
 …
 0  0  0  0  0  0  0  0

julia> sizeof(z)
8
```

变量 `z` 的大小仅为 8 字节（64 位），因为所有条目都用单个位表示。此时创建的不是 `Array`，而是 `BitArray`。`BitArray` 是存储布尔值数组的高效方式，因为它用 1 位存储 1 位信息，而不是 1 字节。类似于 `falses`，`trues(dims)` 可用真值位初始化 `BitArray`。

## `fill` 函数

`fill(val, dims)` 创建一个填充 `val` 值的数组。数组的类型取决于 `val` 值的类型。

```julia
julia> a = fill(5.0, (2, 2))
2×2 Matrix{Float64}:
 5.0  5.0
 5.0  5.0

julia> a = fill(5, (2, 2))
2×2 Matrix{Int64}:
 5  5
 5  5
```

## `similar` 函数

`similar(a, elem_type, dims)` 通过使用数组 `a` 的默认元素类型和/或 `dims` 维度，创建一个未初始化的指定 `elem_type` 类型的 `Array`。

```julia
julia> b = similar(a, Int)
2×2 Matrix{Int64}:
 665953152  665953936
 665953600                    0
```

## `collect` 函数

`collect(elem_type, collection)` 是一个实用方法，用于从集合中的所有数据创建一个 `Array`。

```julia
julia> collect(1:3)
3-element Vector{Int64}:
 1
 2
 3

julia> collect(Float64, 1:2:3)
2-element Vector{Float64}:
 1.0
 3.0
```

## `reshape` 函数

数组在内存中作为线性连续块分配，索引以行优先格式覆盖在其上。`reshape` 是实现这一目的的便捷方法。

```julia
julia> a = collect(1:16)
16-element Vector{Int64}:
  1
  2
  3
  …
 16

julia> b = reshape(a, (4, 4))
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> c = reshape(b, (2, 8))
2×8 Matrix{Int64}:
 1  3  5  7   9  11  13  15
 2  4  6  8  10  12  14  16

julia> d = reshape(c, (8, 2))
8×2 Matrix{Int64}:
 1   9
 2  10
 3  11
 4  12
 5  13
 6  14
 7  15
 8  16
```

虽然数组的形状发生了变化，但数据的行优先排序仍保持原有序列。

## 数组拼接方法

这些方法通过组合输入数组创建新的 `Array` 对象。

### `vcat` (垂直拼接)

`vcat` 创建一个数组，将输入数组沿维度 1（垂直方向）放置。对于矩阵集合，效果类似于将数组一个接一个地向下堆叠。

```julia
julia> vcat([1 2; 3 4], [5 6; 7 8], [9 10; 11 12])
6×2 Matrix{Int64}:
  1   2
  3   4
  5   6
  7   8
  9  10
 11  12
```

### `hcat` (水平拼接)

`hcat` 创建一个数组，将输入数组沿维度 2（水平方向）放置。对于矩阵集合，效果类似于将数组一个接一个地向右放置。

```julia
julia> hcat([1 2; 3 4], [5 6; 7 8], [9 10; 11 12])
2×6 Matrix{Int64}:
 1  2  5  6   9  10
 3  4  7  8  11  12
```

### `hvcat` (分块拼接)

`hvcat(rows::Tuple{Int}, arrays…)` 利用第一个参数中 `rows` 元组的数据形成行，然后将形成的行堆叠在一起形成最终数组。

```julia
julia> hvcat((2, 2, 2), [1, 2], [3, 4], [5, 6], [7, 8], [9, 10], [11, 12])
6×2 Matrix{Int64}:
  1   3
  2   4
  5   7
  6   8
  9  11
 10  12
```

在上述示例中，向量以每组 2 个并排放置，从而创建了 3 个间歇矩阵。

![hvcat 示意图](n4upl4fndrk.jpeg)

将它们垂直堆叠即可得到最终输出。

```julia
julia> hvcat(6, [1, 2], [3, 4], [5, 6], [7, 8], [9, 10], [11, 12])
2×6 Matrix{Int64}:
 1  3  5  7   9  11
 2  4  6  8  10  12
```

同样地，在上述示例中，6 个向量并排放置形成一个矩阵。

## 关联集合

在关联集合中，集合的元素以键值对形式存储。值可以通过索引键或对键的高效搜索来访问。常见的集合包括字典、多重字典、集合（集合仅保留键，忽略值）。大多数关联集合派生自抽象类型 `AbstractDict{K, V}`。

### `Dict{K,V}`

`Dict{K,V}` 是 Julia 中使用的简单关联集合。参数类型 `K` 用作键，类型 `V` 用作值。唯一的要求是为类型 `K` 定义了哈希函数。

```julia
julia> d = Dict("a"=>1, "c"=>2, "b"=>3)
Dict{String,Int64} with 3 entries:
  "c" => 2
  "b" => 3
  "a" => 1

julia> d["b"]
3

julia> d["a"] = 5
5

julia> println(d)
Dict("c" => 2,"b" => 3,"a" => 5)
```

`Dict{K,V}` 不能为同一个键保存多个值。定义中重复的键会覆盖先前定义的值。

```julia
julia> d = Dict("a"=>1, "c"=>2, "b"=>3, "a"=>4)
Dict{String,Int64} with 3 entries:
  "c" => 2
  "b" => 3
  "a" => 4
```

### `get` 函数

`get(dict, key, defval)` 方法用于从 `Dict` 对象中提取信息。以下是几个示例：

```julia
julia> get(d, "a", 3)
4

julia> get(d, "e", 0)
0
```

