

# 4.9 IDEs 和编辑器

PHP 的集成开发环境（IDEs）和代码编辑器非常丰富，你很可能会有自己喜欢用于 Web 基础 PHP 开发的工具。目前没有专门针对 PHP CLI 编程的 IDE 或编辑器，但由于 PHP 代码在语法上与 Web 基础 PHP 编程兼容且非常相似，你使用现有的 PHP 编辑环境应该不会遇到太多问题。某些额外功能可能无法正常工作，例如基于 Web 的调试器，或者可能需要额外调试才能使用。流行的 PHP IDE 列表在本书末尾的附录 E 中给出。

# 4.10 文档生成器

文档生成器（也称为文档化工具）会自动从源代码生成文档。它们通过使用代码中的注释并提取代码中的语法结构来实现这一点。它们对于为编程 API 创建基础文档以及为处理你代码的其他开发者创建技术文档非常有用。提供的文档通常需要进一步完善或添加额外信息才能真正有用，并且通常对你软件的最终用户帮助不大。但是，它能很好地概述代码结构，并为较大的代码库提供有用的参考，因为从代码本身查找特定函数的细节可能很耗时。某些 IDE 和其他编程工具可以使用文档化工具未经修改的输出来提供额外功能，例如基于项目的上下文相关帮助和自动补全。

## phpDocumentor

流行且多功能的基于 PHP 的文档生成器

- **主网站**：[http://www.phpdoc.org/](http://www.phpdoc.org/)
- **安装信息**：[http://www.phpdoc.org/docs/latest/getting-started/installing.html](http://www.phpdoc.org/docs/latest/getting-started/installing.html)
- **主文档**：[http://www.phpdoc.org/docs/latest/index.html](http://www.phpdoc.org/docs/latest/index.html)

## phpDox

一个快速现代的文档生成器，可以从其他静态分析工具中提取信息

- **主网站**：[http://phpdox.de/](http://phpdox.de/)
- **主文档和安装信息**：[http://phpdox.de/getting-started.html](http://phpdox.de/getting-started.html)

## phpSimpleDoc

一个简化的文档生成器，输出 HTML 文档

- **主网站**：[http://phpsimpledoc.tig12.net/](http://phpsimpledoc.tig12.net/)
- **安装信息**：[http://phpsimpledoc.tig12.net/user-guide/quick-start#toc_1](http://phpsimpledoc.tig12.net/user-guide/quick-start#toc_1)
- **主文档**：[http://phpsimpledoc.tig12.net/user-guide](http://phpsimpledoc.tig12.net/user-guide)

## Doxygen

一个全面且广泛的文档生成器，支持 PHP 但不是 PHP 特有的。

- **主网站**：[http://www.stack.nl/~dimitri/doxygen/](http://www.stack.nl/~dimitri/doxygen/)
- **安装信息**：[http://www.stack.nl/~dimitri/doxygen/manual/install.html](http://www.stack.nl/~dimitri/doxygen/manual/install.html)
- **主文档**：[http://www.stack.nl/~dimitri/doxygen/manual](http://www.stack.nl/~dimitri/doxygen/manual)

## Sami

Symphony 框架项目为其 API 创建和使用的文档生成器，尽管它不是 Symphony 特有的。

- **主网站**：[https://github.com/fabpot/Sami](https://github.com/fabpot/Sami)
- **安装信息**：[https://github.com/fabpot/Sami#installation](https://github.com/fabpot/Sami#installation)
- **主文档**：[https://github.com/FriendsOfPHP/Sami#configuration](https://github.com/FriendsOfPHP/Sami#configuration)

# 4.11 分析器

分析器让你测量和查看代码的执行时间和路径，通常旨在提高脚本性能并消除代码瓶颈。我们将在第 9 章详细介绍这些内容，届时我们将进一步探讨脚本性能。

# 4.12 其他工具

本节列出了一些对严肃开发有用但不太符合上述类别的其他工具。

## PHP 编码标准修复器

尝试修复你的代码以符合 PSR 标准。

- **主网站、文档和安装信息**：[http://cs.sensiolabs.org/](http://cs.sensiolabs.org/)

## Composer 依赖管理器

