
在前面的示例中，使用标准调度规则，`<strong>f(4)</strong>` 将调用 `<strong>f(::Integer)</strong>`，而 `<strong>f("John")</strong>` 将调用 `<strong>f(x)</strong>`。如果必须构建自定义调度规则，可以使用 `<strong>@generated</strong>` 宏来创建函数，如下所示：

```
julia> @generated function genf(x)
if x <: Integer
return :(x^2)
else
return :x
end
end
genf (generic function with 1 method)
```

在前面的函数中，仅在生成的函数中使用了 `<strong>x</strong>` 的类型。`<strong>x</strong>` 的值被忽略。该函数返回一个表达式，该表达式是基于自定义调度过程所期望的函数行为。

```
julia> genf(4)
16
julia> genf("John")
"John"
```

当这些方法被调用时，带有 `Integer` 参数的函数会被编译并缓存。后续对 `<strong>genf(3)</strong>` 的调用将调用已编译的表达式，效率可能更高。关于生成宏的更详细示例，建议参阅 Julia 文档[2](#olitpqt8.html#n4upl4fndas)。

**注意：**

*   **函数的缓存生成是非确定性的。因此，与生成器一起使用的函数不得有副作用。它们也不应修改全局变量。**
*   **生成函数用于难以消除歧义的复杂调度规则。对于标准场景，使用语言默认的调度规则始终更高效。**

# Julia 内置宏

Julia 有许多内置宏，用于简化某些任务。我们在前几章中已经接触过它们，如 `<strong>@view</strong>`、`<strong>@goto</strong>`、`<strong>@label</strong>` 等。在本节中，我们将了解其中的一些宏并欣赏其实现。

# 宏的内部变量

每个宏都可以访问变量 `<strong>__source__</strong>`（包含文件名、行号）和 `<strong>__module__</strong>`（包含定义该宏的模块名称）。

```
julia> macro test()
println(__module__)
println(__source__)
end
@test (macro with 1 method)

julia> @test
Main
#= In[6]:1 =#
```

这些变量用于开发一些实用的位置宏，如 `<strong>@__FILE__</strong>`、`<strong>@__LINE__</strong>` 和 `<strong>@__DIR__</strong>`。

```
function macro_usage()
println("Dir:", @__DIR__, " file:", @__FILE__, " Line no:", @__LINE__)
end

julia> macro_usage()
Dir:C:\mydir\GitHub\HOPJ\Chapter-8 file:In[9] Line no:2
```

**注意：** 当代码在 REPL 或 IJulia 上下文中使用时，`<strong>@__FILE__</strong>` **宏不返回文件名。它返回命令标识符。**

# @eval 宏

当需要生成大量样板代码时，可以有效地使用 `<strong>@eval</strong>`。

```
julia> struct MyNumber
v::Float64
end
```

假设我们想在这些数字上定义所有数学方法，如 `<strong>sin</strong>`、`<strong>cos</strong>` 和 `<strong>tan</strong>`。代码可能如下所示：

```
Base.sin(m::MyNumber)=Base.sin(m.v)
Base.cos(m::MyNumber)=Base.cos(m.v)
Base.tan(m::MyNumber)=Base.tan(m.v)
```

可以通过以下表达式避免重复代码：

```
julia> for op in [:sin, :cos, :tan]
eval(quote
Base.$op(m::MyNumber)=Base.$op(m.v)
end)
end
```

`<strong>eval(quote…end)</strong>` 是许多 Julia 应用程序中常用的表达式。同一功能以宏 `<strong>@eval</strong>` 表示，表达式如下所示：

```
julia> for op in [:sin, :cos, :tan]
@eval Base.$op(m::MyNumber)=Base.$op(m.v)
end
```

# @assert 宏

`<strong>@assert</strong>` 是一个宏，用于验证表达式的真值，如果表达式评估为 `<strong>false</strong>`，则抛出 `<strong>AssertionError</strong>`。C/C++ 等其他语言也有类似的宏。在某些语言中，断言验证仅在调试模式下执行代码时生效，在优化的发布模式代码中会被忽略。Julia 也建议仅将 `<strong>assert</strong>` 宏用于调试操作。因此，不应将其用作程序逻辑。`<strong>assert</strong>` 的最简单形式如下，完整代码可见 Julia GitHub 仓库[3](#olitpqt8.html#n4upl4fndat)：

```
macro myassert(ex, msg)
return :($(ex) ? nothing : throw(AssertionError($msg)))
end

julia> @myassert 1==0 "1 is not same as 0"
AssertionError: 1 is not same as 0
Stacktrace:
[1] top-level scope at In[24]:4
…
```

实际的 `<strong>assert</strong>` 宏不限制传递给它的参数数量，但仅将第一个消息作为有效消息。如果没有消息，则将 `<strong>ex</strong>` 作为消息。

```
macro myassert(ex, msgs...)
msg = isempty(msgs) ? ex : msgs[1]
msg = msg isa AbstractString ? String(msg) : string(msg)
return :($(ex) ? nothing : throw(AssertionError($msg)))
end

julia> @myassert 1==0
AssertionError: 1 == 0

Stacktrace:
[1] top-level scope at In[34]:10
…
```

最终代码与前面的代码略有不同，因为它解决了简单示例代码未处理的一些错误条件。将 `<strong>assert</strong>` 定义为宏是恰当的，因为 `<strong>ex</strong>` 参数在 Julia 中可以是任何表达式。

# @time 宏

`<strong>@time</strong>` 宏用于计算执行代码块的耗时和内存分配。

```
julia> @time begin
sleep(0.3)
1+1
end
0.310595 seconds (15 allocations: 672 bytes)
2
```

`<strong>@time</strong>` 宏的一部分实现如下代码所示：

```
macro mytime(ex)
return quote
local elapsedtime = time_ns()
local val = $(ex)
elapsedtime = time_ns() - elapsedtime
println("Elapsed time: ", elapsedtime/1e9)
val
end
end
```

`<strong>val</strong>` 在 `<strong>elapsedtime</strong>` 之前计算。因此，两者都需要存储在局部变量中。由于返回值是一个带引用的表达式。如果变量 `<strong>val</strong>` 和 `<strong>elapsedtime</strong>` 没有显式定义为局部变量，则会覆盖全局作用域中的 `<strong>val</strong>` 和 `<strong>elapsedtime</strong>` 变量。这仅适用于从宏返回的 `<strong>Expr</strong>`，不影响宏中使用的变量（如前一个示例中的 `<strong>msg</strong>`）。
