

## 代码格式指南

### 5. 行字符长度限制

这因项目而异。Julia GitHub 仓库倾向于将字符限制设置为 92 个字符。一些项目也建议 120 个字符，甚至有些不设限制。然而，限制有助于使代码保持一致和可读。作者倾向于 80 个字符，因为如果你在 1080p 显示器上使用像 emacs 这样的编辑器，可以并排编辑两个文件。无论决定何种值，所有贡献者都必须遵守。

请参考 Julia 语言的代码格式指南[4](#e7p95xmz.html#n4upl4fndm6) 以更好地理解其他一些格式相关的建议。其他一些组织和个人也提出了他们自己的风格[5](#e7p95xmz.html#n4upl4fndm7), [6](#e7p95xmz.html#n4upl4fndm8)，在社区中也相当流行。

## 函数式编程

函数式编程并非新事物。事实上，它是由于 Alonzo Church 对 Lambda 演算[7](#e7p95xmz.html#n4upl4fndm9) 的研究而出现的最古老的编程形式。甚至在 *Von Neumann* 计算机概念成为主流之前——即计算机拥有内存，状态机根据采取的每一步动作对其进行转换。内存在代码执行的每一步都被跟踪。这种顺序编程风格被称为**命令式编程**。

### 遍历列表示例

让我们遍历一个列表并打印所有值。

```julia
julia> a = [1, 2, 3];
julia> for i=firstindex(a):lastindex(a)
           println(a[i])
       end
1
2
3
```

在命令式编程中，遍历列表的声明性陈述被以相当详细的分步方式解释：

1. 从数组的第一个索引开始并初始化计数器（`i`）。
2. 如果计数器（`i`）小于或等于数组的最后一个索引。
    1. 取出存储在数组（`a`）计数器（`i`）位置的值。
    2. 将该值打印到 `stdout`。
    3. 将计数器（`i`）加 1。
3. 转到步骤 2。

与之对比，以下代码：

```julia
foreach(println, a)
```

解释该代码最接近的英文陈述是：遍历数组并将所有值打印到 `stdout`。这是一种声明式编程风格。Julia 为你提供了命令式编程的所有构造，同时也提供了声明式编程的灵活性。虽然声明式编程风格是函数式编程的核心，但还有其他一些属性。

### 数学函数与不可变性

数学上函数的定义是一种映射。你从函数的定义域输入一个参数，获得的输出是映射到函数值域中一个值的映射：

![](n4upl4fndrh.jpeg)

**Figure 10.1:** Function f mapping from domain A to range B

这种映射是刚性的，例如 `y1 = f(x1)`。且 `f` 永远不能改变 `x1` 的值。这本质上意味着函数不能改变输入的状态，输入数据是不可变的。你可以将其与定义不可变结构体（`struct`）的能力联系起来。在 Julia 中，可以改变输入参数的函数建议以感叹号（`!`）结尾命名。这些是会引起副作用的函数。

```julia
julia> a = [1, 2, 3];
julia> pop!(a)
3
julia> a
2-element Array{Int64,1}:
 1
 2
```

前面的 `pop!()` 方法改变了数组状态并引入了副作用。当函数依赖于其状态可变的全局变量时，副作用会变得更难追踪，因为函数不再对相同的输入返回相同的输出。

### 高阶函数

高阶函数表现得像函数的函数。它们本质上可以被视为函数的函数：

![](n4upl4fndri.jpeg)

**Figure 10.2:** g o f(x) = g(f(x)) is a higher order function h(x)

在前面的例子中，`h = g ∘ f` 是一个函数组合。Julia 也支持此类定义。

```julia
julia> f(x) = 2x;
julia> g(x) = x*x;
julia> h = g ∘ f
julia> h(3)
36
```

如果 `h` 是一个以 `f` 作为参数的函数呢？这些函数类型在数学中很常见。函数的导数就是这种关系。我们之前多次见过的 `map()` 函数也接受一个函数作为参数。这些本质上都是高阶函数。它们有助于声明式编程。

### 性能考量

在无副作用函数一节中，我们讨论了不可变性。`String` 和 `struct` 类型也是不可变的。因此，无副作用的函数在操作字符串或 `struct` 数据类型集合时可能会分配额外的临时内存。大量的小分配可能会成为性能损耗。使用 `map`、`reduce` 或 `mapreduce` 可以帮助最小化临时空间分配，使不可变函数更高效。

我们讨论了函数式编程的几个方面。有兴趣通过多种编程语言简明地理解函数式编程概念的读者可以参考 *Functional Thinking*[8](#e7p95xmz.html#n4upl4fndna)。读者自然会想知道应该遵循命令式风格还是函数式风格。在这方面 Julia 是一种相当灵活的语言。虽然在许多地方你会发现声明式程序、递归函数、推导式或类似特性，但 Julia 并不强制规定任何特定的编程风格。该语言提供了同样有用的构造来进行命令式编程。有时不可变性可能导致中间变量分配增加，影响代码性能。在这种情况下，使用有副作用的函数可能是理想的选择。

## 函数式编程模式

在上一节中，我们访问了函数式编程的基础知识，并了解了它们与 Julia 编程的相关性。然而，函数式编程原则在任何语言中的应用都可能因语言能力而异。在本节中，我们将看一些常用模式及其在 Julia 中的实现方式。关于此主题的详细论述请参阅 *Hands-On Design Patterns and Best Practices with Julia*[9](#e7p95xmz.html#n4upl4fndnb)。

### 接口定义

Julia 中的任何函数定义都可以充当接口。假设我们想创建一个 2D 几何模块，并规定 2D 形状必须拥有计算面积和包围盒的方法。接口可能如下所示：

```julia
module geom
# All shape objects must have implementation for the following methods.
# area(x): shall return the area of a 2-D shape
function area end
# bbox(x): shall return the bounding box of a 2-D shape
function bbox end
end
```

接口仅仅是指令。然而，可以通过强制一个抛出错误的默认实现，使它们成为硬性接口。

```julia
julia> module geom
       area(x) = throw(Base.MethodError(area, (x,)))
```

