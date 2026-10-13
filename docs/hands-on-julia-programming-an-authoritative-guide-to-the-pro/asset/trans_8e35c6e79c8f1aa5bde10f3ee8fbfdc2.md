

`fib(n) = n < 3 ? 1 : fib(n-1) + fib(n-2)`

以下是在 REPL 中运行代码得到的一些测试结果。

```
julia> fib(3)
2
julia> fib(10)
55
julia> fib(-1)
1
julia> fib(0)
1
```

递归函数之所以终止，是因为对于所有 `n < 3` 的值都存在终止条件。根本问题在于斐波那契数列对于负数 `n` 是否有效。拥有一个小型纯函数并在 REPL 中验证它，使得确保代码正常运行并将其引入实际代码变得更加容易。在 IDE 中运行代码片段是实现相同结果的另一种方式。

虽然前述方法是测试和使用小块代码的一些较简单途径，但它们不同于用于原生二进制文件的 `gdb` 等工具所采用的行调试。Julia 拥有一个功能齐全的命令行调试器[21](#iftzdvy1.html#n4upl4fndlp)。

## 行调试

行调试最好在 IDE 中进行，因为使用指针设置断点、添加变量监视并查看这些值在单步进入、单步跳出或单步越过代码块或函数时如何变化会更加容易。你可以运行代码直到满足特定条件或触发断点。虽然行调试是大多数程序员最青睐的技术，但对于像 Julia 这样的解释型语言，它可能不是最高效的选择。

*   初始化调试器环境可能非常缓慢。
*   调试可能需要更多的内存。
*   单步执行代码并验证监视变量本身可能也是一个缓慢的过程。
*   当一个人对代码缺乏足够理解，或没有更简便的方法来排除已正常运行的代码时，行调试是最后的选择。
*   当错误代码可以被定位到非常小的部分并进行专门验证时，行调试可以非常有效：

![](n4upl4fndrc.jpeg)

**图 12.9：** 在 VS Code 中调试的 Julia 源代码

读者可以使用 VS Code 或 Atom 在 IDE 中打开文件 `fibonacci.jl` 并调试代码。

## Revise.jl 与运行时限制

无论程序员多么熟练，她都希望能快速尝试脑海中的想法，体验结果，修复更改，然后继续处理下一块代码。Julia 的运行时是预加载的。随着你将更多数据结构、模块和包加载到系统中，旧的符号和代码块会被加载到运行时中。如果不影响运行时其他地方的整体工作，可能无法修改已定义的符号。例如，在 REPL 中更改函数定义很简单。但是，不允许添加或删除 `struct` 数据类型的属性。当修改包时，后续使用 `using <<module>>` 命令不会重新加载它。为克服这些限制，可以使用 `Revise.jl`[22](#iftzdvy1.html#n4upl4fndlq) 包。该包可以自动加载，并能作为代码-运行-修复开发周期的一部分更新符号。我们建议读者查阅该包文档以获得详细了解。

## 总结

在与 Julia 同行的旅程中，我们已经走过了漫长的道路。我们从理解语言开始，处理了一些示例；尝试使用 REPL 或 Jupyter 来体验语言能力。在本章中，我们介绍了一些用于获得更好代码编辑和调试体验的工具。在下一章中，我们将尝试掌握构建 Julia 项目的专业知识，并以普遍期望的方式组织它们。

## 练习

1.  为你选择的文本编辑器安装 Julia 扩展或插件。观察编辑器提供的各种功能。
2.  安装 Emacs。如何将 Julia 模式与 Emacs Speaks Statistics 集成？你是否看到任何问题或顾虑？
3.  安装 Juno 并打开一个你选择的 Julia 包，尝试调试它。
4.  安装 Julia for VSCode 并打开一个你选择的 Julia 包，尝试调试它。
5.  有哪些有效的调试技术？你认为行调试是唯一的出路吗？

---

[1](#iftzdvy1.html#n4upl4fndlr) Sage McEnery, How much computer code has been written?, 18th July 2020, **[https://medium.com/modern-stack/how-much-computer-code-has-been-written-c8c03100f459](https://medium.com/modern-stack/how-much-computer-code-has-been-written-c8c03100f459)** 最后访问：2021 年 1 月 23 日。

[2](#iftzdvy1.html#n4upl4fndls) D. E. Knuth, Literate Programming, The Computer Journal, September 1983

[3](#iftzdvy1.html#n4upl4fndlt) IBM Rational ClearCase, **[https://www.ibm.com/support/knowledgecenter/SSSH27_9.1/com.ibm.rational.clearcase.help.ic.doc/topics/c_product_ovw.htm](https://www.ibm.com/support/knowledgecenter/SSSH27_9.1/com.ibm.rational.clearcase.help.ic.doc/topics/c_product_ovw.htm)**

[4](#iftzdvy1.html#n4upl4fndlu) Microsoft Visual Studio Teams Services, **[https://visualstudio.microsoft.com/vs/features/collaborate/](https://visualstudio.microsoft.com/vs/features/collaborate/)**

[5](#iftzdvy1.html#n4upl4fndlv) Editor War, **[https://en.wikipedia.org/wiki/Editor_war](https://en.wikipedia.org/wiki/Editor_war)**

[6](#iftzdvy1.html#n4upl4fndlw) Julia Editor Support, **[https://github.com/JuliaEditorSupport](https://github.com/JuliaEditorSupport)**

[7](#iftzdvy1.html#n4upl4fndlx) The Juno Project, **[https://junolab.org/](https://junolab.org/)**

[8](#iftzdvy1.html#n4upl4fndly) Julia for VS Code **[https://www.julia-vscode.org/](https://www.julia-vscode.org/)**

[9](#iftzdvy1.html#n4upl4fndlz) `julia-vim`, **[https://github.com/JuliaEditorSupport/julia-vim](https://github.com/JuliaEditorSupport/julia-vim)**

[10](#iftzdvy1.html#n4upl4fndl0) Installation Guideline `julia-vim`, **[https://github.com/JuliaEditorSupport/julia-vim/blob/master/INSTALL.md](https://github.com/JuliaEditorSupport/julia-vim/blob/master/INSTALL.md)**

[11](#iftzdvy1.html#n4upl4fndl1) Julia-vim tutorial for newbies, Julia Discourse Post, **[https://discourse.julialang.org/t/julia-vim-tutorial-for-newbies/36636/6](https://discourse.julialang.org/t/julia-vim-tutorial-for-newbies/36636/6)**

[12](#iftzdvy1.html#n4upl4fndl2) Some attempts have been made to run `Notepad++` in Linux using Wine emulator. Editors like `Sublime Text` have Julia integrations as well.

[13](#iftzdvy1.html#n4upl4fndl3) `Julia-NotepadPlusPlus`, Git Hub Repository, **[https://github.com/JuliaEditorSupport/julia-NotepadPlusPlus](https://github.com/JuliaEditorSupport/julia-NotepadPlusPlus)**

[14](#iftzdvy1.html#n4upl4fndl4) `julia-intellij`, GitHub Project, **[https://github.com/JuliaEditorSupport/julia-intellij](https://github.com/JuliaEditorSupport/julia-intellij)**

[15](#iftzdvy1.html#n4upl4fndl5) juliaDT, GitHub Project, **[https://github.com/JuliaEditorSupport/JuliaDT](https://github.com/JuliaEditorSupport/JuliaDT)**

[16](#iftzdvy1.html#n4upl4fndl6) Julia PRO, **[https://juliacomputing.com/products/juliapro/](https://juliacomputing.com/products/juliapro/)**

[17](#iftzdvy1.html#n4upl4fndl7) Julia client for Atom is entering maintenance mode, **[https://atom.io/packages/julia-client](https://atom.io/packages/julia-client)** 最后访问：2021 年 1 月 27 日

[18](#iftzdvy1.html#n4upl4fndl8) Visual Studio Code, **[https://code.visualstudio.com/](https://code.visualstudio.com/)**

[19](#iftzdvy1.html#n4upl4fndl9) Anecdotes, Grace Hopper, Wikipedia, **[https://en.wikipedia.org/wiki/Grace_Hopper](https://en.wikipedia.org/wiki/Grace_Hopper)**

[20](#iftzdvy1.html#n4upl4fndma) Devon H. O'Dell, The Debugging Mindset, acmqueue, Jan-Feb 2017

