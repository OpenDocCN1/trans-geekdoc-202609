

# Julia 数组操作与抽象数组

## Reduce、Foldl 与 Foldr

```julia
julia> a = reshape(collect(1:16), (2, 2, 2, 2))
2×2×2×2 Array{Int64,4}:
[:, :, 1, 1] =
 1  3
 2  4
[:, :, 2, 1] =
 5  7
 6  8
[:, :, 1, 2] =
  9  11
 10  12
[:, :, 2, 2] =
 13  15
 14  16

julia> reduce(+, a)
136
```

给定集合 `a`，`reduce` 方法对所有元素应用二元操作（`+`）并返回所有元素的和。

让我们将前面的示例从操作符 `+` 替换为操作符 `-`。左结合性将产生与右结合性完全不同的结果。Julia 提供了两个方法 `foldl` 和 `foldr`，它们本质上是 `reduce` 方法在左结合性和右结合性下的表现形式。我们可以使用结合性操作符（`=>`）来仔细观察这些差异。

```julia
julia> foldl(=>, [1, 2, 3, 4])
((1 => 2) => 3) => 4

julia> foldr(=>, [1, 2, 3, 4])
1 => (2 => (3 => 4))

julia> reduce(=>, [1, 2, 3, 4])
((1 => 2) => 3) => 4
```

通过将操作符（`=>`）替换为操作符（`-`），可以观察到结果的差异。

```julia
julia> foldl(-, [1, 2, 3, 4])
-8

julia> foldr(-, [1, 2, 3, 4])
-2

julia> reduce(-, [1, 2, 3, 4])
-8
```

## Mapreduce

集合可以映射到特定函数，并将结果归约为聚合结果。一个名为 `mapreduce` 的专用函数可以同时结合这两种操作。

```julia
julia> mapreduce(x->x*x, +, [1, 2, 3, 4])
30
```

前面的示例计算集合元素平方和。

## Mapslices

我们迄今为止处理的所有映射和归约方法，对其他集合类型同样适用，正如它们对数组适用一样。`mapslices` 是一个特殊函数，它与数组特别是数组切片紧密相关。

```julia
julia> a = reshape(collect(1:16), 2, 2, 2, 2);

julia> mapslices(sum, a, dims=[1, 2])
1×1×2×2 Array{Int64,4}:
[:, :, 1, 1] =
 10
[:, :, 2, 1] =
 26
[:, :, 1, 2] =
 42
[:, :, 2, 2] =
 58
```

该函数在数组的前 2 个维度上应用 `sum` 函数并报告结果。

## 抽象数组接口

到目前为止，我们观察到数组有两个不同的操作。首先，它提供数据存储的容器；其次，它提供访问和修改数据的各种方法。迭代、索引和切片可以被视为数据的各种访问方法。具体类型如 `Array{T,N}` 满足这两种需求，但在存储要求上是僵化的。例如，一个只有对角线元素的矩阵只需要 `N` 个元素来存储数据。一个三对角矩阵，其对角线及平行于对角线的前后元素被定义，只需要 `3N-2` 个元素来存储数据。使用 `Array{T,2}` 或 `Matrix` 存储此类数据将是浪费的，因为需要 `N*N` 的存储空间。`AbstractArray{T,N}` 是一个用于解决此类需求的接口。以下是派生类型预期实现的一些功能，以便它们能与其他数组类型无缝协作。

1.  `size` 接口，提供数组在所有已定义维度上的大小。
2.  索引接口 `getindex` 和 `setindex!`，用于访问和修改数组数据。
3.  迭代器接口，使数组表现得像一个集合。
4.  `similar` 接口，在需要时将专用数组转换为等效的 `Array{T,N}` 类型。
5.  `axes` 方法，支持非标准索引（如从 0 开始索引等）。

虽然我们建议读者查阅 Julia 文档[1]以获得完整理解，但我们通过示例代码展示一些实现以便于理解。

> **注意：** `AbstractVector{T}` 和 `AbstractMatrix{T}` 分别是 `AbstractArray{T,1}` 和 `AbstractArray{T,2}` 的别名。

我们实现一个单位矩阵。单位矩阵的对角线元素定义为 1，所有其他元素为 0。由于它们具有固定模式，不需要 `setindex!` 方法。

```julia
struct MyIdentity{T} <: AbstractMatrix{T}
    l::Int
end

Base.size(m::MyIdentity) = (m.l, m.l)

Base.size(m::MyIdentity, d) = (d == 1 || d == 2) ? m.l :
    error("Invalid dimensions")

function Base.getindex(m::MyIdentity{T}, i, j) where {T}
    1 <= i <= m.l && 1 <= j <= m.l || error("Invalid indices")
    i == j && return one(T)
    return zero(T)
end
```

仅这一简单定义就能提供一个功能几乎完备的单位矩阵。

```julia
julia> a = MyIdentity{Int}(3)
3×3 MyIdentity{Int64}:
 1  0  0
 0  1  0
 0  0  1

julia> a[2, 1]
0

julia> a = MyIdentity{Float32}(3)
3×3 MyIdentity{Float32}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> size(a)
(3, 3)

julia> size(a, 2)
3

julia> length(a)
9
```

仅定义 `size` 和 `getindex` 方法就能处理矩阵的大部分行为。这是由于 Julia 基础库中定义的默认行为。现在如果我们将一个向量与 `MyIdentity{T}` 矩阵相乘，应该得到相同的向量。

```julia
julia> a[5] # Linear Indexing
1.0f0

julia> a * [1, 2, 3]
3-element Vector{Float32}:
 1.0
 2.0
 3.0
```

## 稀疏数组

稀疏数组是我们之前讨论的 `AbstractArray` 概念的扩展。稀疏数组的本质是减少数组所需的总体存储。在许多数值应用中，任意行和列组合中的大多数值可以是 0，而非零值仅出现在特定位置。例如，对角矩阵仅在对角线元素上有数据。稀疏数组更进一步，允许将值存储在一个向量中，并使用一个或多个索引向量存储值的位置[2]。

> **注意：** 稀疏数组是 Julia 标准库（`stdlib`）中 `SparseArrays` 模块的一部分。请确保在使用任何与稀疏数组相关的类型或方法之前，通过命令 `using SparseArrays` 导入符号。我们将在后续章节详细讨论模块。

```julia
using SparseArrays

struct SparseVector{Tv, Ti<:Integer} <:
    AbstractSparseVector{Tv, Ti}
    n::Int                  # Length of the sparse vector
    nzind::Vector{Ti}       # Indices of stored values
    nzval::Vector{Tv}       # Stored values, typically nonzeros
end
```

