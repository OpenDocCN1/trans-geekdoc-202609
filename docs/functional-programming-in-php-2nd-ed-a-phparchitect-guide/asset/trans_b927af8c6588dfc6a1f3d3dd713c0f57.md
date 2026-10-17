

1.  `def` 等同于 PHP 的 `function` 关键字。

2.  `substr` 是我们要声明的函数名称。

3.  接下来，函数参数作为逗号分隔的列表声明在括号内。

4.  第一个参数是 `string`，其声明类型为 `String`。在 Scala 中，类型紧跟在参数名称之后，用冒号分隔——`string: String`。

5.  `start` 是第二个函数参数的名称，声明为 `Int` 类型（接受整数）。因此 `start: Int` 表示我们期望传入类型为 `Int` 的参数。该参数在函数内部将被称为 `start`。

6.  最后一个参数是 `length`，其定义与 `start` 相同，请参见步骤 5 以获取更深入的描述。

7.  括号之后，紧跟冒号声明了另一个类型。在此例中为 `String`，因为该函数将返回一个字符串，就像它所模仿的原始 PHP 函数一样。

函数定义的其余部分只是 `substr()` 内部工作原理的实现，本书无需进一步探讨。

同样，在 Haskell 中定义的函数也同样具有描述性，只是使用了略有不同的方言：

```

```

Haskell 的类型定义与 Scala 不同，其与函数定义分离是最显著的。第一行是预期的类型定义，第二行是实际实现。

查看第一行，可以将类型视为另一个列表来逐一分析：

1.  首先是函数名称 `substr`。

2.  接下来，两个连续的冒号表示这是一个类型定义，定义即将出现。

3.  第一个参数的类型首先指定为 `String`。紧接着是 `->`，表示该参数结束且后面还有另一个参数。这与 Scala 或 PHP 中的逗号类似（好吧，有点类似，但这里不深入探讨）。

4.  作为第二个参数，该函数将接受一个 `Int`（整数）。

5.  第三个参数也是一个 `Int`。

6.  最后的 `->` 表示接下来的类型定义将是函数的返回类型。与 Scala 示例一样，这是一个 `String`。

同样，我们将跳过实际实现，因为它与本书无关。

这两个定义很简单，各自的语言都能表达得更加丰富。虽然深入研究它们的类型系统可能很有趣，但理解本书并不必要。我故意对这两个类型系统的描述比较宽泛，以将其简化为理解本书所需的知识。当然，两者都有更多内容，但最好在 Haskell 或 Scala 书籍中探索。

在本书中，Haskell 语法将用于定义某些类型。这是因为函子（functors）、应用函子（applicatives）和单子（monads）等概念是在 Haskell 中定义的，并且有详细文档。这将使你能够查看其他 Haskell 单子实现的类型签名，并在 PHP 中构建它们。

如果你决定探索 Haskell 或 Scala，那么值得拥有 Hyperpolyglot

## 0.2 Using the UTF-8 Ellipsis

在本书过程中，介绍了一个使用三个连续点作为函数的项目，即 React/Partial。

> **CAUTION** React/Partial 使用下面的 Unicode 省略号字符作为占位符。它不应与 PHP 表示可变参数函数的 `...` 语法混淆。

> 

> 对于较小的用途，最简单的方法是直接从 UTF-8 表（如 [http://www.fileformat.info/info/unicode/char/2026/index.htm](http://www.fileformat.info/info/unicode/char/2026/index.htm)）复制并粘贴该字符。不过，随着你越来越多地使用该函数，这很快就会变得乏味。

> 

> 如果你运行的是 MacOS，可以简单地使用键盘快捷键。在 QWERTY 键盘上，同时按住 `Option` 键和分号键即可得到该字符。对于 QWERTZ 键盘，则是 `Option` 和句点/点/句点（`.`）键。在 Mac 上，`Option` 键也令人困惑地被称为 `Alt`。

> 

> 在 Linux 上也有一个“快捷方式”，但坦白说，一旦你看到它，你肯定会同意复制粘贴看起来更有吸引力。按住 `Ctrl` + `Shift` + `u` 进入 Unicode 模式，然后按 `2`、`0`、`2`、`6` 和 `Enter`。有些人报告说 `Alt Gr` 和句点/点/句点可以在 Linux 上得到省略号，但在我实际使用中从未正常工作过。

> 

> 不幸的是，Windows 也同样受影响，你必须按住 `Alt` 进入 Unicode 模式，然后在数字键盘上按 `0`、`1`、`3`、`3` 并释放 `Alt` 键。如果你使用的是没有数字键盘的笔记本电脑，我不确定你应该怎么做！

> 

> 如果你想要一个简单的复制粘贴来源，也可以制作一个简单的 HTML 页面，如 [http://www.functionalphp.com/utf8](http://www.functionalphp.com/utf8)。省略号字符在 HTML 中编码为 `&hellip;` 和 `&#x2026;`。

> 

> 我倾向于使用 Vim 作为我的文本编辑器，虽然默认没有快捷方式（为什么会有呢？），但它高度可配置。你可以使用 `imap` 指令为 Vim 内的使用定义一个新的键映射。在省略号的情况下，我们可以为 `Ctrl` + `F5` 定义一个简单的快捷方式——记住你需要从某处复制并粘贴 UTF-8 省略号字符以插入到 `imap` 指令中。

> 

> ```
> :imap <C-F5> …
> ```

> 

> 现在，在编辑器的插入模式下，你可以同时按住 `Control` 和 `F5` 键，省略号将插入到光标位置。要使此键绑定始终可用，可以将其添加到 `.vimrc` 中，添加一行：

> 

> ```
> imap <C-F5> …
> ```

> 

> 对于 IDE，我主要使用 Netbeans（带有 Vim 键绑定），和之前的 Vim 一样，没有默认的插入省略号的方法。你可以在选项对话框中创建一个简单的宏，当按下键盘快捷键时插入一个省略号。

> 

> 你也可以通过四个简单的步骤享受这一启示：

> 

> 1.  Tools > Options > Editor > Macros。

> 2.  单击 New 并为其命名（“ellipsis” 也许）。

> 3.  在宏代码框中输入以下内容（包括引号！）：`"…"`。

> 4.  单击 Set Shortcut 并选择你想要的按键（我选择了 `Control` + `Alt` + `.`）。

> 

> 现在，按下 `Control` + `Alt` + `.` 键，UTF-8 省略号字符将插入到文档的光标位置。

> 

> 所以省略号是一个字符，而不是三个点/句点/句点连续出现。虽然默认情况下可能不容易使用，但有一些简单的技巧可以使其更容易。虽然这里详细介绍了 Vim 和 Netbeans，但我相信 Eclipse、PhpStorm 和 Emacs 也有类似的功能。

* * *

1.  [Hyperpolyglot](http://hyperpolyglot.org)[↩](#ch015.xhtml#fnref1)

2.  [React/Partial](https://github.com/reactphp/partial)[↩](#ch015.xhtml#fnref2)

3.  [Variadic Functions](http://php.net/functions.arguments#functions.variable-arg-list)[↩](#ch015.xhtml#fnref3)

# 12 Appendix B: Resources

> “Programmers are the worst people to discuss programming with.”

> 

> —Brian McKenna (Functional programmer, @puffnfresh)

有关功能性 PHP 额外内容和更新，请查看 [http://www.functionalphp.com](http://www.functionalphp.com) 并在 Twitter 上关注 @FunctionalPHP。

## 12.1 PHP REPLs

### Command line

*   phpsh—[http://phpsh.org](http://phpsh.org)

*   PsySH—[http://psysh.org](http://psysh.org)

*   Boris—[https://github.com/d11wtq/boris](https://github.com/d11wtq/boris)

### Online

*   3v4l—[http://3v4l.org](http://3v4l.org)

## 12.2 Libraries

