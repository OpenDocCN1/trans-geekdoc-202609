
# Julia 模块与命名空间

## 模块定义与导出

可以看到，模块名 `m1` 和 `m2` 分别在各自的模块命名空间中定义。然而，只有函数 `f` 在模块 `m1` 的命名空间中可用，而函数 `g` 在模块 `m2` 的命名空间中可用。`names()` 函数仅报告从模块导出的符号。现在让我们在代码中使用函数 `f`。

```julia
julia> f()
UndefVarError: f not defined
Stacktrace:
 [1] top-level scope at In[6]:1
 [2] include_string(::Function, ::Module, ::String, ::String) at .\loading.jl:1091
 …
```

`f` 仅在模块内部定义，但无法从外部执行环境访问。然而，通过限定模块名调用 `f()` 可以正确执行该函数。

```julia
julia> m1.f()
Defined as m1.f

julia> m2.f()
Defined as m2.f
```

你可以使用命令 `using` 访问模块导出的所有名称。

```julia
julia> using .m1

julia> f()
Defined as m1.f

julia> g()
UndefVarError: g not defined
Stacktrace:
 [1] top-level scope at In[10]:1
 [2] include_string(::Function, ::Module, ::String, ::String) at .\loading.jl:1091
 …
```

只有 `f` 能够被调用，因为 `m1` 仅导出了函数 `f`。函数 `g` 未被导出，因此该符号无法被调用。这里第二点值得注意的是 `using` 语句中 `m1` 前的点号 (`.`)。该模块定义在当前环境中，`m1` 是当前模块的成员模块，而非最高层级模块。`.m1` 明确了模块的层级关系。

```julia
julia> using Main.m2

julia> g()
Defined as m2.g
```

也可以使用 `Main.m2` 代替 `.m2`，前者是模块 `m2` 的相对位置，而后者是完全限定的模块名。`Main` 是 Julia 执行环境的最高层级。当从 REPL 或 IJulia 环境进行调用时，所有交互发生的模块命名空间即为 `Main` 模块。我们将在下一节查看一些预定义模块。你可以通过 `using` 命令专门请求访问来导入未导出的函数（如 `m1.g()`），但这不会成功，因为 `g()` 已经可用（来自 `m2.g()`）。

```julia
julia> using .m1: g
WARNING: ignoring conflicting import of m1.g into Main

julia> g()
Defined as m2.g
```

然而，`m1.h()` 可以通过 `using` 命令访问，尽管它未从 `m1` 导出。

```julia
julia> using .m1: h

julia> h()
Defined as m1.h
```

我们简要了解了 Julia 的模块设计。稍后章节将在讨论包的同时回顾更多细节。目前，你可能已经能够使用 Julia 运行时中标准模块定义的各种功能。

## 预定义模块

在上一节中，我们了解到代码可以组织为模块。我们也理解了定义在一个模块中的函数可以在另一个模块中使用。一些模块内置于 Julia 系统中。启动 Julia 执行环境时，会初始化一个 `Main` 模块。函数 `varinfo()` 报告当前执行环境中定义的变量。

```julia
julia> varinfo()
name                    size summary
–––––––––––––––– ––––––––––– –––––––
Base                                    Module
Core                                    Module
InteractiveUtils        198.387 KiB Module
Main                                    Module
m1                        5.866 KiB Module
m2                        4.992 KiB Module
```

如上所示，报告显示 `Main`、`Core` 和 `Base` 均可用。`InteractiveUtils` 因 REPL 而加载。使用 IJulia 启动 Julia 环境时，可能不会加载该模块。之前定义的模块 `m1` 和 `m2` 也已加载。让我们定义几个变量。

```julia
julia> varinfo()
name                    size summary
–––––––––––––––– ––––––––––– –––––––
Base                                    Module
Core                                    Module
InteractiveUtils        198.387 KiB Module
Main                                    Module
m1                        5.866 KiB Module
m2                        4.992 KiB Module
ans                          8 bytes Int64
x                            8 bytes Int64
```

在上表中：

*   变量 `ans` 可能在 REPL 环境中报告，因为它存储了在 REPL 屏幕上最后打印的值。
*   `Core` 模块包含核心语言特性，没有它们系统根本无法运行。像 `String`、`Int` 等数据类型定义在 `Core` 模块中。
*   `Base` 模块也包含语言特性。但在某种意义上，它们可被视为比 `Core` 模块更外围的功能。例如，文件输入/输出 (`IO`) 定义在 `Base` 模块中。虽然 IO 是系统的基本特性，但可以构建不直接使用 IO 的应用程序。然而，许多内部系统组件可能需要 IO 来实现其功能。

