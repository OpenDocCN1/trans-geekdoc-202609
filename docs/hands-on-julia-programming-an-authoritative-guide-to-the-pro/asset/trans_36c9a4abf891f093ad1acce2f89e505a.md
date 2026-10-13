
`nzval` 是存储所有非零值的向量，而 `nzind` 是这些值的索引位置，其中 `n` 是稀疏向量的长度。

```julia
using SparseArrays
I = [1, 4, 3, 5]; V = [1, 2, -5, 3];
R = sparsevec(I,V)
```

```text
5-element SparseVector{Int64,Int64} with 4 stored entries:
  [1]  =  1
  [3]  =  -5
  [4]  =  2
  [5]  =  3
```

由于 `I` 向量中的最大索引值为 5，因此创建了一个 5 元素的向量。向量 `R` 的成员可以像普通向量一样访问。

```julia
R[2]
```

```text
0
```

`findnz` 方法提供存储非零值的所有索引位置。本质上，给定一个稀疏向量或矩阵，它会报告 `nzind` 和 `nzval` 向量。

```julia
findnz(R)
```

```text
([1, 3, 4, 5], [1, -5, 2, 3])
```

# 稀疏矩阵存储（CSC 格式）

进一步推广稀疏向量的概念，可以通过为第二维度添加一个向量来存储矩阵。然而，为了更好的存储管理，通常采用以下方法。

1.  列索引按递增顺序存储在一个向量中。
2.  行索引存储在第二个向量中，当列索引发生冲突时，按递增顺序存储。
3.  值存储在一个单独的向量中，用于相同的目的。

这个概念称为**压缩稀疏列**（`CSC`）。虽然该格式存储效率极高，但不利于插入或修改，因为任何插入都可能需要将向量中的所有值向右移动。

```julia
struct SparseMatrixCSC{Tv,Ti<:Integer} <: AbstractSparseMatrix{Tv,Ti}
    m::Int                  # 行数
    n::Int                  # 列数
    colptr::Vector{Ti}      # 第 j 列位于
                            # colptr[j]:(colptr[j+1]-1)
    rowval::Vector{Ti}      # 存储值的行索引
    nzval::Vector{Tv}       # 存储的值，通常为非零值
end
```

```julia
I = [1, 4, 3, 5]; J = [4, 7, 18, 9]; V = [1, 2, -5, 3];
S = sparse(I, J, V)
```

```text
5×18 SparseMatrixCSC{Int64, Int64} with 4 stored entries:
⠀⠈⠀⡀⠀⠀⠀⠀⠠
⠀⠀⠀⠀⠁⠀⠀⠀⠀
```

```julia
findnz(S)
```

```text
([1, 4, 5, 3], [4, 7, 9, 18], [1, 2, 3, -5])
```

```julia
S[1, 2]
```

```text
0
```

```julia
size(S)
```

```text
(5, 18)
```

正如稀疏向量示例所示，`SparseMatrixCSC` 具有创建、访问和操作矩阵的类似函数。我们将把使用这些数据结构的细节留给读者，并建议参考语言文档以了解相关内容，这既是为了节省篇幅，也因为这些结构可能增加的复杂性。

# 性能考量

虽然稀疏数据结构利于存储，但可能不是索引和迭代的最佳选择。使用这些结构时，务必小心数据访问的复杂性。即使是简单的索引访问，也可能需要扫描索引和数据向量的很大一部分。虽然非零值的增量迭代访问可能很高效，但特定索引的随机访问可能不那么高效。

# Julia 中的线性代数

虽然我们迄今为止回顾的大多数概念都是数组、向量和矩阵的表示层面，但本节是关于将它们应用于解决数学和科学计算问题。Julia 的线性代数功能聚合在 `stdlib` 下的一个名为 `LinearAlgebra` 的模块中。因此，在使用这些方法和数据结构之前，需要使用以下语句。

```julia
using LinearAlgebra
```

Julia 线性代数模块可以被认为包含 3 个不同的部分。

1.  Julia 原生的基本矩阵和向量运算
2.  LAPACK 函数
3.  BLAS 函数

基础模块包含矩阵运算，如转置（`tr`）、求逆（`inv`）、点积（`dot`）等。还有进一步的方法，如奇异值分解（`svd`）、下三角和上三角分解等。还有一个特征模块，提供各种矩阵类型的特征值计算。我们将不在这里深入探讨这些概念。不过，我们建议读者查阅语言文档[3](#zfp2b22u.html#n4upl4fndgd)。在后续章节中，我们将根据需要有选择地介绍其中一些方法。

# 总结

作为一门面向研究社区的科学编程语言，Julia 提供了先进的数组、向量和矩阵表示及方法。我们在这里探讨了一些概念，并介绍了一些高级主题的存在。虽然数组是 Julia 的关键数据结构之一，但字符串也是编程中同样重要的方面。我们将在下一章探讨字符串，这将帮助我们更好地理解文本处理。

# 练习

1.  使用 `Vector` 实现一个二叉堆。
2.  通过 `@view` 宏创建的 View 类型中，数组索引是如何转换的？是否可能存在一个数组，其某一维度中的某些索引是无效的？
3.  使用 `AbstractMatrix` 接口创建一个 `MyTridiagonal` 矩阵，并与其维度之一大小相同的行矩阵进行广播加法（`+`）运算。
4.  如果要表示一个对角矩阵，应该使用 `SparseMatrixCSC` 吗？为什么这样做不是个好主意？
5.  Julia 是否提供矩阵 LU 分解的线性代数方法？如果有，请通过示例展示其应用。

---

[1](#zfp2b22u.html#n4upl4fndge) 抽象数组接口，Julia 文档，[https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-array](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-array)

[2](#zfp2b22u.html#n4upl4fndgf) 稀疏数组，Julia 文档，[https://docs.julialang.org/en/v1/stdlib/SparseArrays/#Sparse-Arrays](https://docs.julialang.org/en/v1/stdlib/SparseArrays/#Sparse-Arrays)

[3](#zfp2b22u.html#n4upl4fndgg) 线性代数，Julia 语言文档，[https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/)

稀疏数组是我们之前讨论的 `AbstractArray` 概念的扩展。稀疏数组的本质是减少数组所需的总体存储。在许多数值应用中，任意行和列组合的大多数值可以是 0，而非零值仅出现在特定位置。例如，对角矩阵仅在对角线元素上有数据。稀疏数组更进一步，允许将值存储在一个向量中，并用一个或多个索引向量存储值的位置2。
