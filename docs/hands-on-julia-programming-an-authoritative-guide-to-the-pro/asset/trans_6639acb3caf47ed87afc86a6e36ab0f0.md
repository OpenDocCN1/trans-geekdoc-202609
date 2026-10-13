

让我们在 REPL 提示符下尝试几个实验。

```
julia> 2 + 2
4
julia> 2.0 + 2
4.0
julia> println("Hello, World!!!")
Hello, World!!!
```

这些示例相当简单，只是在每次计算后都会打印结果。如果你不想在 REPL 中打印某些内容，请在语句末尾使用分号（`;`）符号。然而，在使用显式 `println` 的地方，使用分号将不起作用。现在让我们看看使用分号的相同样本。

```
julia> 2 + 2;
julia> 2.0 + 2;
julia> println("Hello, World!!!");
Hello, World!!!
```

为什么会有这种行为？我们将把答案留到下一章，届时我们将讨论数据类型和 `nothing` 的概念。

REPL 提供了一个基于 Shell 的控制台，用于以交互方式与 Julia 进行交互。然而，这对于绘图或图像等图形输出并不十分有用。

## Jupyter 集成

Jupyter 旨在为 Julia、Python 和 R 等语言创建交互式、浏览器兼容的 Shell。可以创建简单的基于 Web 的笔记本用于教程和培训材料。在 Julia 中，这种集成是通过一个名为 `IJulia` 的包来实现的。需要在 `julia` Shell 中执行以下步骤，以便配置 Jupyter 并启动 Jupyter Notebook。

```
julia> ]add IJulia
Updating registry at `~/.julia/registries/General` …
julia> using IJulia
[Info: Precompiling IJulia [7073ff75-…-fcdaad2a7d2a]
julia> notebook()
[Info: running `/home/sambit/anaconda3/bin/jupyter notebook`
```

命令结束时，将打开一个新的浏览器窗口，显示如下截图所示的 Jupyter：

![](n4upl4fndqd.jpeg)

**图 1.2：** 从 Julia REPL 启动的 Jupyter 浏览器窗口

使用 GUI 创建一个以 *Julia 1.6.0* 为内核的新笔记本，如下所示：

![](n4upl4fndqe.jpeg)

**图 1.3：** 创建一个带有 Julia 1.6.0 内核的新笔记本

最后，输入命令并运行它们，如下截图所示：

![](n4upl4fndqf.jpeg)

**图 1.4：** 具有示例代码的交互式 Jupyter 笔记本

你可以输入并运行代码；结果将显示在同一个浏览器窗口中。

## 运行 Julia 程序

虽然交互式表达式是在终端上快速尝试某事并查看输出的方法，但现实世界的应用程序需要运行大量代码块。在 Julia 中，你将所有相关代码输入到一个文件中。Julia 程序通常具有 `.jl` 扩展名。打开你选择的文本编辑器，在文件中输入以下代码并另存为 `example01.jl`。

```
# example01.jl
println("2 + 2 = ", 2+2)
println("2 + 2.0 = ", 2+2.0)
println("Hello World!!!")
```

提供了我们之前编写的代码。每一行都使用 `println` 命令来展示该行已运行且输出已打印在终端上。

在命令提示符下运行 `julia`。然后在 julia 提示符下调用命令，如图所示，你应该会看到输出：

```
$ julia
julia> include("example01.jl")
2 + 2 = 4
2 + 2.0 = 4.0
Hello World!!!
```

另一种运行 Julia 程序的方法是在命令行运行，如图所示：

```
$ julia example01.jl
2 + 2 = 4
2 + 2.0 = 4.0
Hello World!!!
```

我们将在后面的章节中了解更多关于如何编写复杂程序和组织它们的细节。`include` 也用于将代码从一个 Julia 文件嵌入到另一个文件中。

## 总结

Julia 是一门非常强大的语言。虽然它是为数据科学应用而设计的，但该语言也可以作为通用语言使用。我们开始探索该语言提供的各种功能，并了解了本书的组织结构。我们安装了 Julia。我们启动了 REPL 和 Jupyter 笔记本，以尝试一些简单的 Julia 语言特性。现在环境已经设置完毕，我们将深入探究 Julia 平台。在下一章中，我们将研究 Julia 中的类型系统，动态类型语言如何在内部解释数据类型，并通过一些突出这些内容的代码示例进行更深入的探讨。

## 练习

1.  在你选择的机器上安装 Julia 并启动 REPL。
2.  安装 IJulia 和 Jupyter。确保你可以在 Jupyter 笔记本中运行 Julia 代码。

---

## 参考文献

[1] Stefan Karpinski, The Unreasonable Effectiveness of Multiple Dispatch, JuliaCon 2019, [https://www.youtube.com/watch?v=kc9HwsxE1OY](https://www.youtube.com/watch?v=kc9HwsxE1OY)

[2] Julia Micro-Benchmarks [https://julialang.org/benchmarks/](https://julialang.org/benchmarks/)

[3] Peter Norvig, Director of Research at Google, would have preferred Julia over Python for his research work, Gradient Descent Podcast, [https://www.youtube.com/watch?v=hVW1mwLtDcI](https://www.youtube.com/watch?v=hVW1mwLtDcI)

[4] TensorFlow.jl GitHub Repository [https://github.com/malmaud/TensorFlow.jl](https://github.com/malmaud/TensorFlow.jl)

[5] Cairo.jl GitHub Repository

[6] QML.jl GitHub Repository

[7] Blink.jl ([https://github.com/JuliaGizmos/Blink.jl](https://github.com/JuliaGizmos/Blink.jl))

[8] Electron.jl ([https://github.com/davidanthoff/Electron.jl](https://github.com/davidanthoff/Electron.jl))

[9] JuliaBinaryWrappers [https://github.com/JuliaBinaryWrappers](https://github.com/JuliaBinaryWrappers)

[10] Research, Julia Language Website, [https://julialang.org/research/](https://julialang.org/research/) last accessed 4th Dec 2020

[11] JuliaEditorSupport, GitHub Repositories, [https://github.com/JuliaEditorSupport](https://github.com/JuliaEditorSupport)

[12] JuliaHub, [https://juliahub.com/ui/Home](https://juliahub.com/ui/Home)

[13] PackageCompiler, [https://github.com/JuliaLang/PackageCompiler.jl](https://github.com/JuliaLang/PackageCompiler.jl)

[14] Julia Language is licensed under the MIT License. An exception statement is made on specific components that may have different licenses. [https://github.com/JuliaLang/julia/blob/master/LICENSE.md](https://github.com/JuliaLang/julia/blob/master/LICENSE.md)

[15] JuliaHub provides UI to search based on licenses

[16] Julia’s Release Process, [https://julialang.org/blog/2019/08/release-process/](https://julialang.org/blog/2019/08/release-process/)

[17] Julia Computing, [https://juliacomputing.com/](https://juliacomputing.com/)

[18] In a GitHub repository, a user can assign a star to a repository. This is one way to suggest, a developer is interested in the repository. Some people use these stars as bookmarks for future references.

[19] Julia GitHub repository, [https://github.com/JuliaLang/julia](https://github.com/JuliaLang/julia) as on 4th Dec. 2020.

[20] This annual conference is being organized from 2014. JuliaCon, 2020, [https://juliacon.org/2020/](https://juliacon.org/2020/)

[21] The Julia Community, [https://julialang.org/community/](https://julialang.org/community/)

