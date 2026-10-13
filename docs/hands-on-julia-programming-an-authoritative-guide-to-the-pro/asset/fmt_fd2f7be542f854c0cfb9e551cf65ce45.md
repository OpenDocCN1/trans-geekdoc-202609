
# 开发环境与工具

REPL 是原型设计时尝试简单代码片段的绝佳工具。然而，生产级代码开发需要编写、调试和验证大量代码。虽然普通工程师每天可能只编写 20 行左右的代码，但维护的代码行数却非常庞大。除非拥有信息丰富的可视化工具，否则难以维护此类代码。虽然大多数代码以纯文本形式编写，但源代码编辑要求编辑器理解语言的某些特性。

*   **文档引用**：开发者倾向于在使用函数前查看其文档。虽然像文学编程这样的集成文档生成系统已存在数十年，但函数帮助查找功能因 Javadoc 与 IDE 的集成而变得特别实用且普及。Visual Studio 和许多 Python 语言的 IDE 提供了类似功能。

## 参考文献

1. Sage McEnery, *How much computer code has been written?*, 18th July 2020, [https://medium.com/modern-stack/how-much-computer-code-has-been-written-c8c03100f459](https://medium.com/modern-stack/how-much-computer-code-has-been-written-c8c03100f459) (last accessed: 23rd Jan 2021).
2. D. E. Knuth, *Literate Programming*, The Computer Journal, September 1983.
3. IBM Rational ClearCase, [https://www.ibm.com/support/knowledgecenter/SSSH27_9.1/com.ibm.rational.clearcase.help.ic.doc/topics/c_product_ovw.htm](https://www.ibm.com/support/knowledgecenter/SSSH27_9.1/com.ibm.rational.clearcase.help.ic.doc/topics/c_product_ovw.htm)
4. Microsoft Visual Studio Teams Services, [https://visualstudio.microsoft.com/vs/features/collaborate/](https://visualstudio.microsoft.com/vs/features/collaborate/)
5. Editor War, [https://en.wikipedia.org/wiki/Editor_war](https://en.wikipedia.org/wiki/Editor_war)

## IDE 与编辑器生态

Microsoft Visual Studio 是 Microsoft 生态系统中几乎所有软件开发的知名前端。然而，随着 Microsoft 试图在云基础设施市场确立主导地位，推出不绑定 Windows 生态系统的工具变得必要。Microsoft 于 2015 年推出 Visual Studio Code 以满足此类需求。VS Code 基于 Electron 框架使用开源代码库开发，可在 Windows、Linux 和 Mac OS X 平台上运行。其使用体验与 Atom 相似。

Juno IDE 是 Julia 与 Atom 集成的核心，也是 Julia Computing 商业产品 Julia PRO 的首选编辑器。然而，随着 Microsoft VS Code 集成的推出，关注点正逐渐从该编辑器转移。

**IDE** 是完整的开发平台，有助于管理工作区、项目，并充当编辑器、构建、测试、调试和部署工具。虽然业界有许多标准 IDE，但 Julia 与 Atom 和 Microsoft Visual Studio Code (VS Code) 的集成最为完善，我们将在后续章节中探讨。Julia 还与 IntelliJ 有进行中的集成工作，并有已归档的 Eclipse 集成。

Julia 是一个相对较新的平台。所有前序组件的生态系统在 Julia 作为语言流行之前就已存在。开发者希望 Julia 能与他们最熟悉的工具无缝配合。在 UNIX 环境的文本编辑器世界中，vi 与 emacs 拥有近乎狂热的追随者。GitHub 下的 JuliaEditorSupport 组织维护着与多款知名编辑器（如 Vim、Emacs、Sublime、Atom、Notepad++ 和 Eclipse）的不同层级集成。部分集成处于活跃状态，但许多因缺乏关注和使用而已弃用。Julia IDE 正在 Atom 的 Juno 项目和 Microsoft Visual Studio Code (VS Code) 下开发。

### Vim 集成

用于 vim 的 Julia 插件 julia-vim 是一个 GitHub 项目，可安装在 Mac OS X、UNIX 和 Windows 操作系统的 vim 环境中。该插件是一组 vim 脚本，提供以下功能：

*   虽然有人使用终端模拟器配合 vim 来使用 Julia REPL，但这并非插件本身的功能。

### Notepad++ 集成

正如 vi 和 emacs 是 UNIX 世界最流行的编辑器，Notepad++ 在 Windows 操作系统中广受欢迎，且无直接移植到 Unix 或 Mac OS X 系统。切勿将其与 Windows 系统默认自带、仅具备基本文本编辑功能的 notepad.exe 混淆。Notepad++ 是一款相对高级的文本编辑器，拥有完整的插件功能以编程和增强编辑器渲染体验。它还支持通过 **用户定义语言 (UDL)** 自定义语言语法高亮。UDL 通过 XML 文件提供特定语法结构的简易方式，可用于有效识别和渲染文件。

Julia 的 UDL 可在 GitHub 项目 Julia-NotepadPlusPlus 中获取。

## 相关链接

*   Julia Editor Support: [https://github.com/JuliaEditorSupport](https://github.com/JuliaEditorSupport)
*   The Juno Project: [https://junolab.org/](https://junolab.org/)
*   Julia for VS Code: [https://www.julia-vscode.org/](https://www.julia-vscode.org/)
*   julia-vim: [https://github.com/JuliaEditorSupport/julia-vim](https://github.com/JuliaEditorSupport/julia-vim)

---

# 构建生产级应用

在过去的几章中，您可能一直在思考如何开发生产就绪的应用程序。等待即将结束。本章将提供构建真实应用程序的知识；从解决玩具问题转向您真正想从事的项目。

## 本章主题

在本章中，我们将涵盖以下主题：

*   背景
*   项目、模块和包
*   测试自动化
*   文档
*   持续集成
*   二进制依赖
*   环境
*   包架构
