
# 默认构造函数与类型转换

默认构造函数 `RectangleB(::T, ::T)` where `T<:Real` 被创建了，但 `T` 只能是一个特定类型。它不能同时是 `Rational{Int64}` 和 `Float32`。

```julia
julia> RectangleB{Int}('a', 1f0)
RectangleB{Int64}(97, 1)
```

然而，当我们将参数类型显式指定为构造函数的一部分时，类型会被转换为合适的类型。

## RectangleB 的方法

让我们创建两个名为 `aspect_ratio` 和 `area` 的方法。长宽比是矩形中宽度与高度的比率。面积是矩形中高度与宽度的乘积。我们在前面的示例中已经看到了 `area` 方法的实现。

```julia
area(r::RectangleB) = r.w * r.h
```

```julia
aspect_ratio(r::RectangleB) = r.w / r.h
```

```julia
r, r1, r2 = RectangleB(1//2, 2//3), RectangleB(1.5, 0.5), RectangleB(1, 2)
```

```julia
julia> area(r), area(r1), area(r2)
(1//3, 0.75, 2)
```

```julia
julia> aspect_ratio(r), aspect_ratio(r1), aspect_ratio(r2)
(3//4, 3.0, 0.5)
```

虽然 `area` 函数根据 Rectangle 的参数化类型返回了 `Rational{Int}` 和 `Int` 值，但在 `aspect_ratio` 函数中似乎忽略了这一点。运算符 (`/`) 显式地是浮点除法运算符。Julia 中的有理数或除法运算符是 (`//`)。让我们为 `aspect_ratio` 引入两个专门针对整数和有理数类型的额外方法。

```julia
aspect_ratio(r::RectangleB{T}) where T<:Union{Integer, Rational} = r.w // r.h

julia> aspect_ratio(r), aspect_ratio(r1), aspect_ratio(r2)
(3//4, 3.0, 1//2)
```

显然，`Rational` 和 `Integer` 类型的方法被调度到了新方法，而其余数值类型（如 `Float64`）则被调度到了旧方法。`T<:Union{Integer, Rational}` 本质上意味着该类型可以派生自 `Integer` 类型，也可以是 `Rational` 类型。`Union` 在 Julia 中被广泛用于表示类型是其中一种类型的情况。也可以像以下示例那样使用 3 个方法，而不使用 `Union`。

```julia
aspect_ratio(r::RectangleB{T}) where T<:Integer = r.w // r.h
```

```julia
aspect_ratio(r::RectangleB{T}) where T<:Rational = r.w // r.h
```

从子类型关系如何流向参数化类型的角度来理解调度规则非常重要。

```julia
julia> RectangleB{Rational{Int}} <: RectangleB{Rational}
false
julia> RectangleB{Rational{Int}} <: RectangleB
true
julia> RectangleB{Rational} <: RectangleB
true
```

子类型关系仅与直接参数类型相关。`RectangleB{Rational{Int}}` 不是 `RectangleB{Rational}` 的子类型，但它是 `RectangleB` 的子类型。

## 类型提升示例

让我们看看以下一些示例：

```julia
julia> 1f0 + 2
3.0f0
julia> 1f0 + 2.0
3.0
```

我们将一个 `Float32` 与一个 `Int` 相加，返回的结果是 `Float32`。同样，我们将 `Float32` 与 `Float64` 相加，得到的结果是 `Float64`。所有这些看起来都很自然。看起来 `Int` 被提升为 `Float32`，然后执行了加法。与其他编程语言不同，Julia 中的类型提升不是隐式的。任何类型转换都需要显式进行。Julia 核心库内部定义了许多此类规则，并显式调用它们，以便我们看到这些无缝转换。

## 类型转换

初始化任何值的典型方法是通过构造函数。例如，你可以通过指定 `Int(1.0)` 将整数浮点值 1.0 转换为 `Int`。但 `Int(1.5)` 将抛出 `InexactError`。在大多数情况下，这需要由程序员显式调用来执行。但有时转换需要通过隐式调用来执行。在这种情况下，会调用 `convert(T, x)`。

```julia
julia> function f()
           i::Int = 0
           i = 1.5
           return i
       end
f (generic function with 1 method)
```

```julia
julia> f()
ERROR: InexactError: Int64(1.5)
Stacktrace:
 [1] Int64 at .\float.jl:710 [inlined]
 [2] convert(::Type{Int64}, ::Float64) at .\number.jl:7
 [3] f() at .\REPL[88]:3
 [4] top-level scope at REPL[89]:1
```

`i` 是一个被定义为 `Int` 类型的变量。现在当值 `1.5` 被赋给它时，会调用 `convert` 方法，该方法抛出一个 `InexactError`。对于数值类型，`convert` 方法会调用 `T(x)` 或构造函数，在本例中即为 `Int64(1.5)`。一个更详尽的情况在前面的 `RectangleB` 示例中展示过。

```julia
julia> RectangleB{Int}('a', 1.0)
RectangleB{Int64}(97, 1)
```

在这种情况下，由于提供了 `RectangleB{Int}` 作为构造函数，`convert(Int, 'a')` 和 `convert(Int, 1.0)` 会被隐式调用，从而将 `Char` 和 `Float64` 转换为 `Int`。

```julia
julia> RectangleB{Int}("abc", 1.0)
ERROR: MethodError: Cannot `convert` an object of type String to an object of type Int64
Closest candidates are:
  convert(::Type{T}, ::T) where T<:Number at number.jl:6
  convert(::Type{T}, ::Number) where T<:Number at number.jl:7
  convert(::Type{T}, ::Ptr) where T<:Integer at pointer.jl:23
```

由于不存在从 `String` 到 `Int` 的 `convert` 方法，导致构造函数调用失败。

## 让我们再次看看 `RectangleP` 类型。

```julia
struct RectangleP{T <: Real}
    w::T
    h::T
end
```

当未指定构造函数时，会定义一个默认构造函数，其形式如下：

```julia
struct RectangleP{T<:Real}
    w::T
    h::T
    RectangleP(w::T, h::T) where T<:Real = new{T}(w, h)
end
```

```julia
julia> RectangleP(1, 2.0)
ERROR: MethodError: no method matching Rectangle(::Int64, ::Float64)
Closest candidates are:
  RectangleP(::T, ::T) where T<:Real at REPL[96]:4
```

`RectangleP(1, 2.0)` 正在失败。有办法解决这个问题吗？

```julia
function RectangleP(w::T1, h::T2) where {T1<:Real, T2<:Real}
    w1, h1 = promote(w, h)
    return RectangleP(w1, h1)
end

julia> RectangleP(1, 2.0)
RectangleP{Float64}(1.0, 2.0)
```

我们定义了一个支持两个参数的外部构造函数。这些参数可以源自 `Real` 但彼此不同。我们在参数上调用 `promote` 方法以获取提升后的函数参数，随后用这些提升后的参数创建 `RectangleP`。这里可以理解为，在 `Int` 和 `Float64` 的提升中，`Float64` 将是提升后的类型。这种行为将在以下示例中变得清晰。假设我们要找到能分别放入两个 `RectangleP` 对象内部的最小尺寸 `RectangleP`。

```julia
julia> function minrect(r1::RectangleP, r2::RectangleP)
           w = r1.w < r2.w ? r1.w : r2.w
           h = r1.h < r2.h ? r1.h : r2.h
           return RectangleP(w, h)
       end
minrect (generic function with 1 method)
julia> minrect(RectangleP(1, 2), RectangleP(2.0, 0.5))
RectangleP{Float64}(1.0, 0.5)
julia> minrect(RectangleP(1, 2), RectangleP(3.0, 4.0))
RectangleP{Int64}(1, 2)
```

虽然前面的代码没有错误，但你可以注意到一个异常：函数根据输入数据返回 `RectangleP{Float64}` 或 `RectangleP{Int}`。从类型稳定性的角度来看，这绝对是不可取的。当 `RectangleP{Float64}` 和 `RectangleP{Int}` 发生交互时，我们可以创建一个 `Base.promote_rule`，以便发生正确的提升。

```julia
Base.promote_rule(::Type{RectangleP{T}}, ::Type{RectangleP{S}}) where {T<:Real, S<:Real} = RectangleP{promote_type(S, T)}

Base.convert(::Type{RectangleP{T}}, x::RectangleP{S}) where {T<:Real, S<:Real} = S === T ? x : RectangleP(T(x.w), T(x.h))
```

```julia
function minrect(tr1::RectangleP, tr2::RectangleP)
    r1, r2 = promote(tr1, tr2)
    w = r1.w < r2.w ? r1.w : r2.w
    h = r1.h < r2.h ? r1.h : r2.h
    return RectangleP(w, h)
end
```

```julia
julia> minrect(RectangleP(1, 2), RectangleP(3.0, 4.0))
RectangleP{Float64}(1.0, 2.0)
```

为了保持一致性，我们必须确保提升发生在一致的类型上。由于 `Float64` 与 `Int64` 的提升结果是 `Float64`，我们希望确保 `RectangleP{Float64}` 和 `RectangleP{Int}` 之间的提升结果为 `RectangleP{Float64}`。其次，我们创建一个 convert 方法，用于从 `RectangleP{S}` 转换到 `RectangleP{T}`。当在 `minrect` 中调用 `promote` 时，`promote_rule` 和 convert 方法会在内部被调用。数据被转换为 `RectangleP{Float64}`。因此，最终的返回类型将是 `RectangleP{Float64}`。

## 函数是 Julia 的核心

函数是 Julia 的核心。凭借类型变体和分发架构，Julia 从函数和方法中获得了最大的威力。我们探讨了函数和方法的各种用例，并讨论了参数化数据类型所带来的复杂性。在下一章中，我们将了解集合，并学习如何遍历它们以及如何在其中提取和存储数据。

# 练习

1. 在八皇后谜题中，我们只得到了一个解。还有其他可能的解吗？扩展代码以找到所有可能的解。

2. 随着棋盘尺寸的增加，求解 N 皇后谜题所需的时间会增加。作者在他的环境中发现，求解棋盘尺寸为 30 时的等待时间极高。在你的环境中是多少？如何使程序更高效以降低该限制？

3. 由于 Julia 不支持尾调用优化，栈溢出的可能性可能很大。你认为如何克服栈溢出？

4. 当显式指定参数类型时，Julia 构造函数的表现会有所不同。为什么会这样？

5. 内部构造函数和外部构造函数有什么区别？外部构造函数是必需的吗？

---

## 参考资料

[1] Julia 拥有一套详尽的运算符和符号，它们可以是 Unicode 集合的一部分。借助内联运算符，你可以像编写数学方程一样编写表达式。我们将保持一个简化的观点，即运算符在 Julia 中是函数。然而，建议读者查阅 Julia 文档 ([`docs.julialang.org/en/v1/manual/mathematical-operations/`](https://docs.julialang.org/en/v1/manual/mathematical-operations/))，以详细了解运算符的优先级和结合性。

[2] `:x` 的类型是 `Symbol`。符号是 Julia 中用于创建自定义关键字的特殊用途类型。我们将在第 8 章“元编程”中回顾它们。

[3] Julia GitHub Issue 4964 ([`github.com/JuliaLang/julia/issues/4964`](https://github.com/JuliaLang/julia/issues/4964))

[4] 维基百科关于多重分派的文章 ([`https://en.wikipedia.org/wiki/Multiple_dispatch`](https://en.wikipedia.org/wiki/Multiple_dispatch))

`1//5` 是 Julia 中分数的一种表示形式。

# 尾调用优化

因此，函数调用可以被替换为跳转指令。一些函数式编程语言，如 `Lisp` 或 `Lua`，会以编程方式识别此类条件并消除栈帧的创建。此过程称为**尾调用优化** (`TCO`)。在函数式编程中，递归比迭代编程更受重视。栈帧的创建会消耗内存。因此，深层的递归函数调用可能导致栈溢出。与 `Lisp` 不同，Julia 没有原生支持 TCO。

# 运算符与符号

Julia 拥有一套精心设计的运算符和符号，它们可以是 Unicode 集合的一部分。借助内联运算符，你可以像编写数学方程一样编写表达式。我们将保持一个简化的观点，即运算符在 Julia 中就是函数。不过，建议读者查阅 Julia 文档 ([`https://docs.julialang.org/en/v1/manual/mathematical-operations/`](https://docs.julialang.org/en/v1/manual/mathematical-operations/)) 以详细了解运算符的优先级和结合性。

Julia Github Issue 4964 ([`https://github.com/JuliaLang/julia/issues/4964`](https://github.com/JuliaLang/julia/issues/4964))

维基百科关于多重分派的文章 ([`https://en.wikipedia.org/wiki/Multiple_dispatch`](https://en.wikipedia.org/wiki/Multiple_dispatch))

# 集合

每种编程语言都提供一组最基本的数据结构，用于将多个数据元素作为容器表示；即数组、字典、集合和列表等。Julia 提供的集合是本章讨论的主题。

## 涵盖主题

在本章中，我们将涵盖以下主题：

*   预定义数据结构
*   元组
*   范围
*   数组
*   关联集合
*   迭代
*   迭代框架
*   生成器和推导式

## 学习目标
