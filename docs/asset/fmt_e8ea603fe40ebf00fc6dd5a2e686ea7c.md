
# Julia 中的迭代框架与自定义迭代器

我们已经看到了一些使用 `for` 循环迭代序列和集合的示例。之所以能够实现这一点，是因为所有这些类型都实现了迭代框架。如果你要编写自定义迭代器，可能需要实现这个框架。虽然此处强调了一些基本概念，但建议你阅读 Julia 文档 3 以获取相关细节。

```julia
julia> b = [1.0 2 3; 4 5 6; 7 8 9];
julia> for i=b
            println(i)
        end
1.0
4.0
7.0
2.0
5.0
8.0
3.0
6.0
9.0
```

除了 `for…=`，也可以使用 `for…in`。这种 for 循环的表示法与前一种类似，只是语法看起来更适合集合。让我们看看针对字典对象的用法。

```julia
julia> for p in d
            println(p)
        end
"e" => 2
"b" => 4
"a" => 1
"d" => 3
```

`Dict{K,V}` 元素作为 `Pair{K,V}` 存储，默认打印为：`k => v`。

```julia
julia> for (k, v) in d
            println("Key:", k," Value:", v)
        end
Key:e Value:2
Key:b Value:4
Key:a Value:1
Key:d Value:3
```

---

让我们看一个以数组为输入并返回所有值的平方作为数组的函数。

```julia
function collect_square(v)
    a = similar(v)
    for i=1:length(v)
        a[i] = v[i]*v[i]
    end
    return a
end
julia> collect_square(1:4)
4-element Vector{Int64}:
 1
 4
 9
 16
```

如果我们要扩展此函数，使其返回计算任意函数后的值而不是平方，可以按以下方式扩展：

```julia
function collect_function(f::Function, v)
    a = similar(v)
    for i=1:length(v)
        a[i] = f(v[i])
    end
    return a
end
julia> collect_function(x->x³, 1:4)
4-element Vector{Int64}:
 1
 8
 27
 64
```

调用同一方法的另一种方法是 `function…do` 表示法，如下所示。

```julia
julia> collect_function(1:4) do x
            return x³
        end
4-element Vector{Int64}:
 1
 8
 27
 64
```

`map` 是一个具有类似表示法的函数。它将集合的每个元素值映射并对每个元素应用一个函数，将函数求值的结果作为集合返回。

```julia
julia> map(1:4) do x
            return x³
        end
4-element Vector{Int64}:
 1
 8
 27
 64
```

## 核心迭代方法

`iterate(collection)` 返回第一个元素和初始状态，如果不存在值则返回 `nothing`。

在前面示例的返回值 `(3, 2)` 中，`3` 是第一个元素的值，`2` 是一个代表状态的内部参数。虽然它看起来像下一个值的索引，但不应做此假设，因为这些完全取决于具体实现。

`iterate(collection, state)` 返回下一个元素和下一个状态，如果不存在额外元素则返回 `nothing`。

所有迭代器类型都必须实现 `iterate` 方法。

## 可选迭代器方法

这些是迭代器作者可选择定义的方法。

`IteratorSize(IterType)` 是一个辅助方法，用于说明迭代器是否具有长度或形状。根据此方法，集合迭代器必须定义 `size` 和/或 `length` 方法。

```julia
julia> Base.IteratorSize(Vector{Int})
Base.HasShape{1}()
```

`IteratorEltype(IterType)` 是一个辅助方法，用于决定迭代器是否具有特定的元素类型。

```julia
julia> Base.IteratorEltype(Vector{Int})
Base.HasEltype()
```

`eltype(IterType)` 返回 `iterate` 方法第一个参数的类型。

```julia
julia> eltype(Vector{Int})
Int64
```

这些方法的详细解释可以在 Julia 的文档中找到。

## 示例：自定义 `Squares` 迭代器

我们创建一个 `Squares` 类型，它将提供一个数字平方序列，直到存储在该类型中的值。

```julia
struct Squares
    value::Int
end
```

```julia
Base.iterate(s::Squares) = s.value <= 0 ? nothing : (1, 2)

Base.iterate(s::Squares, state) = s.value < state ? nothing :
                                   (state*state, state+1)

julia> for i=Squares(3)
           println(i)
       end
1
4
9
```

虽然前面的代码适用于简单的 `for` 循环，但尝试使用 `collect` 创建数组将无法工作。

```julia
julia> collect(Squares(3))
ERROR: MethodError: no method matching length(::Squares)
…
```

因此我们添加一个 `length` 方法来实现相同功能。

```julia
julia> Base.length(s::Squares)=s.value
julia> collect(Squares(3))
3-element Vector{Any}:
 1
 4
 9
```

虽然数组已正确填充，但类型却是 `Any`。定义 `eltype(IteratorType)` 方法将确保创建具有正确类型的 `Array`。

```julia
Base.eltype(::Type{Squares})=Int

julia> eltype(Squares)
Int64

julia> collect(Squares(3))
3-element Vector{Int64}:
 1
 4
 9
```

> **注意**：`Type{Squares}` 是一种特殊类型，其唯一的实例对象是 `Squares`。这是必需的，因为 `eltype` 是类型本身的函数，而不是类型实例的函数。

## 推导式与生成器

在 Julia 中，数组和集合广泛用于科学计算。语言提供对数组创建和操作的便捷访问显得尤为重要。推导式提供了创建此类数组的便利性。

```julia
julia> [i*i for i=1:3]
3-element Vector{Int64}:
 1
 4
 9
julia> [i*j for i=1:3, j=1:3]
3×3 Matrix{Int64}:
 1  2  3
 2  4  6
 3  6  9
```

在前面的示例中，推导式被用来创建一维和多维数组。以下是一个索引可能依赖于另一个索引的示例。

```julia
julia> [i*j for i=1:3 for j=i:3]
6-element Vector{Int64}:
 1
 2
 3
 4
 6
 9
```

推导式会计算完整的数组，有时也需要一种延迟执行的迭代器，即仅在需要时计算值，而不是一次性计算所有元素。这些被称为**生成器**。

```julia
julia> gen=(i*j for i=1:3 for j=i:3)
Base.Iterators.Flatten{Base.Generator{UnitRange{Int64},var"#6#7"}}(Base.Generator{UnitRange{Int64},var"#6#7"}(var"#6#7"(), 1:3))
julia> for v=gen
           println(v)
       end
1
2
3
4
6
9
```

## 总结

集合为一类算法提供了简单且可扩展的接口，并提供了统一的迭代器接口来访问元素。在本章中，我们回顾了 Julia 核心语言中定义的几个简单数据结构。然而，对于像 Julia 这样以计算为中心的语言来说，这些只是冰山一角。建议你查看 `DataStructures.jl` 包，以更详细地了解 Julia 可用的数据结构。同样，如果你正在实现自定义数据结构，建议为你的数据结构实现迭代器接口，使其兼容 Julia 语言的迭代框架，如 `for`、`while` 循环等。

# 练习

1.  在初始化数组时，空格 (` `)、逗号 (`,`) 和分号 (`;`) 符号被使用。当它们被包含在方括号 (`[]`) 内时，是否有任何特殊的运算符含义？

2.  选择一个你喜欢的数据结构并在 Julia 中实现它。编写该数据结构所需的基本操作。为其编写迭代器接口，以便可以使用 `for…in` 语法迭代该数据结构。

3.  `Dict` 类型要求必须为键定义哈希函数。尝试实现一个表现得像 `Dict` 但不强制要求键具有 `hash` 函数的 `MyDict` 类型。

4.  `Dict` 使用 `hash` 函数。但是，几乎所有 Julia 类型都存在 `hash` 函数。为什么要使用 `hash` 函数？如果未定义 `hash` 函数，是否还有其他功能可能无法工作？

5.  创建一个生成器，从 1 迭代到 100，并返回除能被 3 整除的数字之外的所有数字。

____________________________________

1 Wirth, Nicklaus, Algorithms + Data Structures = Programs, Prentice-Hall, 1976.

# Julia 数组与数据结构

## 类型别名

在 Julia 1.5 及更早版本中，你可能会看到 `Matrix` 类型被打印为 `Array{T, 2}`，`Vector` 类型被打印为 `Array{T, 1}`。`Matrix` 和 `Vector` 类型是 `Array{T, N}` 的别名。

# 参考文献

3. Julia 文档：迭代接口。([`docs.julialang.org/en/v1/manual/interfaces/#man-interface-iteration`](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-iteration))

Wirth, Nicklaus, *Algorithms + Data Structures = Programs*, Prentice-Hall, 1976.

## 迭代框架

我们已经看到了一些使用 `for` 循环迭代序列和集合的示例。之所以能够实现这一点，是因为所有这些类型都实现了迭代框架。如果你要编写自定义迭代器，可能需要实现此框架。虽然此处强调了一些基本概念，但建议阅读 Julia 文档[3]以获取相关详细信息。

## 数据结构概述

1975 年，著名计算机科学家、PASCAL 语言作者 *Niklaus Wirth* 撰写了《算法 + 数据结构 = 程序》[1]，明确强调了数据结构和算法在编程中的重要性。几乎没有现代编程语言不提供内置的数据结构支持。Julia 也不例外。许多数据结构定义在核心 Julia 语言中，大量数据结构定义在诸如 `DataStructures.jl` 之类的包中。本章将重点介绍语言中定义的、无需使用额外包即可使用的数据结构。例如：

## 数组进阶应用

在上一章中，我们介绍了简单数组以及其他形式的集合，并演示了如何迭代集合。然而，数组在 Julia 中扮演着重要角色，它提供高性能容器，由内存管理，并能在原生应用程序间传输数据。本章将介绍数组的一些高级应用。有时操作直接定义在数组上；或者通过简单的语法修改即可执行复杂的数组操作。

## 本章主题

*   容器
*   维度
*   索引
*   切片
*   广播
*   归约
*   抽象数组类型
*   稀疏数组
*   线性代数

## 学习目标

读者将能够了解数组、向量和矩阵的用例，以及与数组相关的抽象数据类型，从而设计自己的数组类型。数组具有多种索引方案。它们可以被切片为多个部分，组合成数组视图以减少大规模分配。稀疏数组可减少空间或内存分配。

## 数组特性

数组是用于各种操作的最常见集合，因为它们是可变的、可扩展的，且在正确使用时效率很高。本章讨论的某些主题对新手用户可能较为高级。因此，建议随着你对语言经验的积累，稍后再回顾本章的相关部分。

## 向量作为容器

向量作为容器是一种非常常见的用例。栈、队列、二叉堆等数据结构通常使用一维数组或向量实现。Julia 提供了简单的函数来处理这些情况，无需额外实现。以下示例展示了向量用作栈的能力。

```julia
julia> a = []
Any[]

julia> push!(a, 5)
1-element Vector{Any}:
 5

julia> push!(a, 5, 6, 7, 8)
5-element Vector{Any}:
 5
 5
 6
 7
 8

julia> pop!(a)
8
```

上述方法的应用将导致向量按以下方式修改。操作结束时，也可以使用 `empty!(vector)` 方法清空容器。

```julia
julia> length(a)
4

julia> isempty(a)
false

julia> empty!(a)
Any[]

julia> isempty(a)
true
```

让我们看看数组作为队列的操作。

```julia
julia> push!(a, 1, 2, 3, 4, 5)
5-element Vector{Any}:
 1
 2
 3
 4
 5

julia> popfirst!(a)
1

julia> a
4-element Vector{Any}:
 2
 3
 4
 5

julia> pushfirst!(a, 1)
5-element Vector{Any}:
 1
 2
 3
 4
 5
```

`pushfirst!(v, value)` 是在向量开头添加 `value` 的方法。

> **注意**：虽然 `pushfirst!` 和 `popfirst!` 方法存在，但它们不是最高效的，因为插入和删除第一个元素可能需要复制或移动元素。

## 数组维度

数组可以是任意维度的。虽然我们在上一章主要学习了向量（维度 1）和矩阵（维度 2），但本章将介绍更多高维数组。

```julia
julia> a = reshape(collect(1:24), 4, 3, 2)
4×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  5  9
 2  6 10
 3  7 11
 4  8 12
[:, :, 2] =
 13 17 21
 14 18 22
 15 19 23
 16 20 24

julia> ndims(a)
3

julia> size(a)
(4, 3, 2)

julia> size(a, 3)
2
```

`reshape` 接受一个集合并创建指定形状的数组。`ndims` 提供数组的维度数，而 `size` 提供每个维度的元素数量。特定维度的数组大小由 `size(array, dim)` 报告。数组的内存布局如下图所示：

![Figure 6.1: Array shown in 3-D with row-major indexing in Julia](img/n4upl4fndp9.jpeg)

**Figure 6.1:** Array shown in 3-D with row-major indexing in Julia

# 索引

数组使用类型为 `A[I_1, I_2, …, I_n]` 的表达式进行索引。`I_i` 是索引，可以是我们将在本节探讨的各种类型。

## 标量索引

索引表达式最简单的形式可以是标量或数字。以下是一些示例：

```julia
julia> a = reshape(collect(1:24), 4, 3, 2, 1)
4×3×2×1 Array{Int64,4}:
[:, :, 1, 1] =
 1  5  9
 2  6 10
 3  7 11
 4  8 12
[:, :, 2, 1] =
 13 17 21
 14 18 22
 15 19 23
 16 20 24

julia> a[1, 2, 1, 1]
5
```

## 范围索引

索引表达式也可以是范围。`Colon(:)` 具有特殊含义，表示该维度的所有索引。
