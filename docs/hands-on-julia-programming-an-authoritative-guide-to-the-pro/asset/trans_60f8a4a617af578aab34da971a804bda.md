
`<strong>end</strong>`

`<strong>julia&gt; @btime sindegmemo($m3, 60.0)</strong>`

`<strong>2.699 ns (0 allocations: 0 bytes)</strong>`

`<strong>0.8660254037844386</strong>`

`<strong>julia&gt; @btime sindegmemo($m3, 22.0)</strong>`

`<strong>3.799 ns (0 allocations: 0 bytes)</strong>`

`<strong>0.3748975477461437</strong>`

我们已经非常接近 `sind(x)` 的性能，但尚未完全达到[9](#9ztdqvro.html#n4upl4fndin)。一个显而易见的问题是，为什么输入为 60° 时 `sindegmemo` 的表现比输入为 22° 时更好？

# 性能分析

在我们迄今分析的示例中，我们知道某个特定函数存在我们想要克服的性能瓶颈。在许多大型应用程序中，这种先验知识是不太可能具备的。例如，某个文字处理器打开文件并在屏幕上渲染内容的速度很慢。这背后可能有许多因素。文件读取可能很慢，文档中的某个特定功能在计算上很复杂，或者文件太大，读取所有数据并将数据缓存在内存中可能成为瓶颈。性能分析有助于识别此类场景。以特定的固定间隔（例如每毫秒），统计分析器会查看代码执行栈，并记录栈的状态，如查询期间执行所在的行号和函数。运行完成后，它们会关联所有此类数据，并报告遇到特定函数的次数，以及为到达该函数而被调用的所有函数的回溯跟踪。

Julia 拥有内置的统计分析器。`Profiler` 位于名为 `Profile` 的模块中。我们将使用此工具来分析函数 `profile_test`[10](#9ztdqvro.html#n4upl4fndio) 的性能。

```julia
using Profile

function profile_test(n)
    for i = 1:n
        A = randn(100,100,20)
        m = maximum(A)
        Am = mapslices(sum, A; dims=2)
        B = A[:,:,5]
        Bsort = mapslices(sort, B; dims=1)
        b = rand(100)
        C = B.*b
    end
end
```

```julia
julia> profile_test(1)
```

代码运行一次以便进行编译，这样编译所花费的时间就不会被作为分析器采样的一部分捕获。现在我们运行该函数进行 100 次迭代并分析该运行过程。

```julia
julia> @profile profile_test(100)
```

数据由分析器生成并缓存，可以通过 `Profile.print()` 调用来打印。截断视图如下：

```julia
julia> Profile.print()
Overhead ╎ [+additional indent] Count File:Line; Function
=========================================================
╎410 @Base\ttask.jl:356; (::IJulia.var"#15#18")()
╎ 410 @IJulia\src\eventloop.jl:8; eventloop(::ZMQ.Socket)
╎  410 @Base\essentials.jl:709; invokelatest
…
╎      ⎎  84  In[29]:3; profile_test(::Int64)
╎      ⎎  84  …dom\src\normal.jl:210; randn
╎      ⎎   84  …dom\src\normal.jl:204; randn
…
╎      ⎎  8   In[29]:4; profile_test(::Int64)
╎      ⎎  8   @Base\reducedim.jl:722; maximum
╎      ⎎   8   @Base\reducedim.jl:722; #maximum#631
…
╎      ⎎  264 In[29]:5; profile_test(::Int64)
╎      ⎎  264 …\abstractarray.jl:2062; mapslices##kw
…
╎      ⎎  9   In[29]:9; profile_test(::Int64)
╎      ⎎  9   @Base\broadcast.jl:837; materialize
╎      ⎎   9   @Base\broadcast.jl:862; copy
…
Total snapshots: 413
```

高亮部分来自顶层函数 `profile_test`。第 5 行花费的时间最长，因为在总共 413 次采样中，它被采样了 264 次。你可以使用 `ProfileView` 包获得更直观的输出视图。可以使用以下命令安装该包：

```julia
julia> ]add ProfileView
```

![](n4upl4fndqj.jpeg)

**图 11.2：** 使用 ProfileView 进行可视化。高亮区域代表函数的第 5 行代码占用了最多的时间。

我们已经了解了一些性能调优过程。在下一节中，我们将回顾一些编写高性能代码的指导原则。

# 性能设计模式

在[前一节]中，我们探讨了与函数式编程相关的设计模式。在本节中，我们将回顾一些有助于提高代码性能的模式。

## 备忘录模式

当一个纯函数被多次调用时，它应产生相同的输出。与其反复计算结果，如果我们能缓存该值，就能减少计算开销。这个过程称为 `memoization`（备忘录模式/记忆化）。在备忘录模式的语境下，最常见的例子之一是斐波那契数列[11](#9ztdqvro.html#n4upl4fndip)。斐波那契数列最适合用以下代码进行递归描述：

```julia
fib(n) = n < 3 ? 1 : fib(n-1) + fib(n-2)
```

该函数每次调用都会递归调用自身两次。如果我们通过稍微修改函数来记录调用次数，可以看到函数调用次数呈指数级增长。

```julia
function fib(n)
    if n < 3
        return (result=1, calls=1)
    else
        r1, c1 = fib(n-2)
        r2, c2 = fib(n-1)
        return (result=r1+r2, calls=1+c1+c2)
    end
end
```

```julia
julia> for i = 1:10
           r, c = fib(i)
           println("n:", i, "\tresult: ", r, "\tcalls: ", c)
       end
n:1 result: 1 calls: 1
n:2 result: 1 calls: 1
n:3 result: 2 calls: 3
n:4 result: 3 calls: 5
n:5 result: 5 calls: 9
n:6 result: 8 calls: 15
n:7 result: 13 calls: 25
n:8 result: 21 calls: 41
n:9 result: 34 calls: 67
n:10 result: 55 calls: 109
```

```julia
julia> @btime fib(20)
112.899 μs (0 allocations: 0 bytes)
(result = 6765, calls = 13529)
```

考虑到只涉及加法操作，该函数的开销仍然相当大。`fib(6) = fib(5) + fib(4)`。我们在计算 `fib(5)` 的过程中已经见过 `fib(4)`。如果我们在计算 `f(4)` 后立即将其缓存，那么在计算 `f(5)` 和 `f(6)` 时就无需再次计算。我们可以复用之前计算的值。我们在以下代码中采用了相同的概念：

```julia
const mem = Dict()

function fib(n)
    haskey(mem, n) && return mem[n]
    println("Calling fib: ", n)
    res = n < 3 ? 1 : fib(n-1) + fib(n-2)
    mem[n] = res
    return res
end
```

```julia
julia> fib(5)
Calling fib: 5
Calling fib: 4
```

