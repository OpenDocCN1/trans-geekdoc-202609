
在前面的示例中，我们可以将 `Point2D` 和 `Point3D` 定义为 `Point{N}` 的别名。我们为这两种类型定义了两个 `dist` 函数，并确保了基于整数值 2 或 3 的分发可用。`Point{2}` 和 `Point{3}` 是两种截然不同的类型。以 `NTuple` 作为集合类型，让我们尝试拥有一个适用于 `Point{N}` 的 `dist` 方法。

```julia
function dist(p1::Point{N}, p2::Point{N}) where N
    sumval = 0f0
    for i=1:N
        d = p1.data[i] - p2.data[i]
        sumval += d*d
    end
    return sqrt(sumval)
end
```

```julia
julia> dist(Point(1, 2), Point(3, 4))
2.828427f0
julia> dist(Point(1, 2, 3), Point(3, 4, 5))
3.4641016f0
```

如果我们使用不带参数形式 `Point{N}` 的 `Point`，会不会是错的？`Point{2}` 和 `Point{3}` 是两种不同的类型。因此 `dist` 函数将为这两种不同的类型编译。我们本可以创建一个单一的 `dist` 函数。

```julia
function dist(p1::Point, p2::Point)
    N = length(p1.data)
    sumval = 0f0
    for i=1:N
        d = p1.data[i] - p2.data[i]
        sumval += d*d
    end
    return sqrt(sumval)
end
```

```julia
julia> dist(Point(1, 2), Point(3, 4))
2.828427f0
julia> dist(Point(1f0, 2f0, 3f0), Point(1, 2))
ERROR: BoundsError: attempt to access (1.0f0, 2.0f0) at index [3]
Stacktrace:
…
```

现在我们可以将 `Point{2}` 和 `Point{3}` 的参数传递给同一个函数。只创建了一个方法。没有为 `Point{2}` 和 `Point{3}` 版本编译两个方法。什么是正确的方法？不幸的是，这是一个设计决策，而不是编程语言概念。你认为 `Point2D` 和 `Point3D` 是可互操作的，我们应该支持一个针对 `Point{N1}` 和 `Point{N2}` 的可互操作的 `dist` 方法吗？这里是一个可能的实现。

```julia
function dist(p1::Point{N}, p2::Point{N}) where N
    sumval = 0f0
    for i=1:N
        d = p1.data[i] - p2.data[i]
        sumval += d*d
    end
    return sqrt(sumval)
end

function dist(p1::Point{N1}, p2::Point{N2}) where {N1, N2}
    N1 > N2 && return dist(p2, p1)
    tp = Point(p1.data..., ntuple(i->0f0, N2-N1)...)
    return dist(tp, p2)
end
```

*   我们为具有相同维度 `N` 的 `Point{N}` 创建了一个方法。
*   然后我们创建了一个方法，其中不同维度的 `Point` 可以作为输入。
*   这里，我们假设第一个参数的维度将小于第二个。
*   如果不是这样，我们通过翻转参数来调用该方法。从而确保第一个参数的维度小于第二个（N1 < N2）。
*   我们通过为更高维度填充零来创建一个与 `p2` 维度相同的 `temporary point`（`tp`），并调用 `dist(tp, p2)`。

## 

让我们看看以下代码的控制流：

```julia
if val == 1
    f1()
elseif val == 2
    f2()
elseif val == 3
    f3()
else
    f4()
end
```

这些函数能否使用多重分发代替 `if…elseif…else`？

```julia
struct MyVal{N}
    MyVal(N)=new{N}()
end
```

```julia
f(::MyVal{N}) where N = N
```

```julia
function f(::MyVal{1})
    println("Called from 1")
end
```

```julia
julia> f(MyVal(2))
2
julia> f(MyVal(1))
Called from 1
```

*   `MyVal{N}` 基于 `N` 的值定义类型。
*   方法 `f` 适用于 `MyVal{N}` 的所有值。
*   仅为 `MyVal{1}` 定义了一个特化的方法 `f`。
*   现在 `f(MyVal(2))` 调用了通用方法，而 `f(MyVal(1))` 调用了特定方法。

## 

当一个类型没有属性时，只为它创建一个对象。这样的对象称为 `singletons`。创建的值类型也是一个单例，因为该类型没有属性。

```julia
julia> MyVal(1) === MyVal(1)
true
julia> MyVal(1) === MyVal(2)
false
```

`MyVal{1}` 与 `MyVal{2}` 是不同的类型。因此，作为初始化一部分创建的对象是两个不同的对象。虽然值参数在 Julia 中是可能的，但它可能不是最优性能的方法。Julia 原生提供了一个类型 `Val{N}`，符合建议的原则。我们将在 Julia 性能管理章节进一步讨论这一点。

**注意**：不仅是 `Integer` 类型，甚至 `Symbol` 也可以用作值类型参数。

```julia
julia> MyVal(:a)
MyVal{:a}()
```

## 

有时我们需要连续的数字或具有固定步长的数字，无论是增加还是减少。这些被称为 **ranges**（范围）。以下是一些示例：

## 

```julia
julia> a=1:5
1:5
julia> typeof(a)
UnitRange{Int64}
```

`a` 是一个 `UnitRange`，意味着它包含从 1 到 5 的所有数字。`UnitRange` 的增量步长始终为 1。

```julia
julia> for i=a
           println(i)
       end
1
2
3
4
5
```

## 

```julia
julia> b=1:2:5
1:2:5
julia> typeof(b)
StepRange{Int64,Int64}
julia> for i=b
           println(i)
       end
1
3
5
```

`b` 是一个步长为 2 的 `StepRange`。

## 

```julia
julia> c=5:-1:1
5:-1:1
julia> typeof(c)
StepRange{Int64,Int64}
julia> for i=c
           println(i)
       end
5
4
3
2
1
```

`c` 是一个步长为 -1 的 `StepRange`。因此迭代时我们按从 5 到 1 的递减顺序打印。

范围用于迭代、索引和初始化集合。它们可以具有更复杂的参数，也可以对初始值、步长和最终值使用浮点数。我们将在后面的章节中回顾涉及的范围对象。这里只是一个带有浮点值的范围示例。

```julia
julia> d=1:2.1:6.0
1.0:2.1:5.2
julia> typeof(d)
StepRangeLen{Float64,Base.TwicePrecision{Float64},Base.TwicePrecision{Float64}}
```
