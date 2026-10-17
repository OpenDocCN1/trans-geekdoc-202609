

| || ***安装信息与主文档*** : [https://github.com/weyrick/roadsend-php](https://github.com/weyrick/roadsend-php) |

### 9.13 银弹 #5 - JIT 编译器与替代虚拟机

在详细讨论它们之前，我先定义几个即将使用的术语，以防你不熟悉它们。

*   虚拟机，或 VM。这个词通常用来指代过去我们所说的解释器。具体来说，这里讨论的是更正式称为“进程虚拟机”的东西，而不是通常在 VirtualBox 等平台上运行的虚拟化操作系统（即“系统虚拟机”）。当你编写 PHP 代码（或许多其他编程语言，如 Python 或 Java）时，它并不会像 C 语言那样被直接编译成机器可执行指令，而是首先被编译成一组中间指令，然后由虚拟机或解释器执行。VM 通常用 C 语言编写，并本身编译成机器可执行代码。这意味着用 PHP 编写的代码实际上是平台无关的，也就是说，它不需要知道特定平台可用的指令集。VM 负责处理这些（这就是为什么你会发现有针对 Windows、Linux、Mac 等平台的单独 PHP 可执行文件可供下载，但大多数 PHP 脚本本身不需要针对不同平台编写不同的脚本）。

| ![information](Images/image00248.jpeg) || **进一步阅读**维基百科上的进程虚拟机  

[http://en.wikipedia.org/wiki/Virtual\_machine#Process\_virtual\_machines](http://en.wikipedia.org/wiki/Virtual_machine#Process_virtual_machines) |

| --- | --- |

*   JIT 编译器：JIT 代表“即时”。与代码预先完全编译（如 C）或在每次脚本运行开始时编译（如传统 PHP）不同，JIT 编译器在代码运行时按函数逐个编译代码，即“实时”编译。这样做的优势在于：a) 只需编译实际执行的代码；b) 编译器可以利用运行时信息（例如当前变量类型，在像 PHP 这样的动态类型语言中，这些类型直到运行时才定义）来生成更优化的代码。简而言之，它们比传统解释器更快。

| ![information](Images/image00248.jpeg) || **进一步阅读**维基百科上的 JIT 编译  

[http://en.wikipedia.org/wiki/Just-in-time\_compilation](http://en.wikipedia.org/wiki/Just-in-time_compilation) |

| --- | --- |

目前有许多可用于 PHP 的替代虚拟机，其中最新的一个在 PHP 社区引起了一些轰动。HHVM 是 Facebook HipHop 项目的最新成果（在上面的编译器部分讨论过），因为其内置的 JIT 编译器而登上新闻头条。它绝对值得关注，因为在某些基准测试中，它目前比它所取代的 HPHPc 编译器快 40% 以上，它更自然地适应大多数生产工作流程，并且与 PHP 及其扩展具有更好的兼容性。

还有其他可用的 VM 和 JIT，如下所示。然而，包括 HHVM 在内的所有这些 VM 都共享一些缺点。

*   对 PHP 和扩展的覆盖有限 - 目前没有一个 VM 能完全覆盖 PHP 和常见扩展。HHVM 团队最近承诺与顶级 PHP 框架和应用程序协同工作，但他们尚未做到（尽管在撰写本文时，他们已设法让 27 个非常常见的框架和应用在 HHVM 下运行）。其他 VM，如 PHP-QB，明确表示它们专注于 PHP 的特定子集，因此不是通用解决方案。因此，在考虑使用替代 VM 时，你需要彻底测试（并可能修改）你的代码。

*   并非所有替代 VM 对所有任务都更快 - 例如，HHVM 中的 JIT 需要多次运行 CLI 脚本才能学习足够的知识来生成优化代码。正如 Sara Golemon 在“PHP 内部”邮件列表中所写：

> *“作为开源版 HipHop（HHVM）的维护者，我首先承认，官方 PHP 引擎和运行时拥有更广泛的平台/架构支持、更强大的社区，以及更丰富的扩展和功能库。此外，由于其生命周期设计，PHP 在单次运行的命令行脚本上性能优于 HHVM。*

> 

> *另一方面，HHVM 在处理 Web 请求方面确实比 Apache+PHP 表现好得多。如果使用普通 PHP，Facebook 将需要至少 5 倍的 Web 服务器（而我们已经使用了很多）。这并不是说 PHP 不够快，但使用松散类型的解释字节码永远无法跟上原生机器代码和严格类型的步伐。”* [http://marc.info/?l=php-internals&m=135399266632008&w=2](http://marc.info/?l=php-internals&m=135399266632008&w=2)

因此，你需要针对典型用例对每个可能的 VM 进行基准测试，以确保你真正获得所需的性能提升。

需要注意的是 PHP7，即 PHP 的“下一代”官方版本。在撰写本文时，这个新版本预计将在今年晚些时候发布。其承诺的功能之一是“预先编译”（AOT）编译器，在某些方面与 JIT 类似。这有利于不需要“预热”，因此可能比 HHVM 为单次运行的 CLI 脚本提供更好的性能改进。

| ![](Images/image00249.gif) || ***HHVM*** |

| --- | --- |

|   ||   |

|   || Facebook 的 HipHop 项目虚拟机。包含 JIT 编译器，并具有相当广泛的语言覆盖范围 |

|   ||   |

|   || ***主网站*** : [http://hhvm.com/](http://hhvm.com/) |

|   ||   |

|   || ***安装信息与主文档*** : [https://github.com/facebook/hhvm](https://github.com/facebook/hhvm) |

|   ||   |

|   || ***官方博客*** : [http://www.hhvm.com/blog/](http://www.hhvm.com/blog/) |

|   ||   |

|   || ***其他信息*** |

|   ||   |

|   || Facebook 工程师关于构建 HHVM 的演示文稿 |

|   || [http://www.infoq.com/presentations/PHP-HHVM-Facebook](http://www.infoq.com/presentations/PHP-HHVM-Facebook) |

|   ||   |

|   || Allan MacGregor 的“HHVM 入门”教程 |

|   || [http://coderoncode.com/2013/07/27/first-steps-on-hhvm.html](http://coderoncode.com/2013/07/27/first-steps-on-hhvm.html) |

|   ||   |

|   || 关于 HHVM 未来的官方博客文章 |

|   || [http://www.hhvm.com/blog/?p=875](http://www.hhvm.com/blog/?p=875) |

|   ||   |

|   || 关于 HHVM 在 CLI 脚本中性能的问答 |

|   || [http://stackoverflow.com/questions/17898783/hhvm-poor-performance](http://stackoverflow.com/questions/17898783/hhvm-poor-performance) |

|   ||   |

|   || “以调试模式调试 HHVM 下的 PHP 应用程序” |

|   || [http://labs.qandidate.com/blog/2013/10/29/debugging-php-applications-with-hhvm/](http://labs.qandidate.com/blog/2013/10/29/debugging-php-applications-with-hhvm/) |

| ![](Images/image00249.gif) || ***Quercus*** |

| --- | --- |

|   ||   |

|   || PHP 的 100% Java 实现。支持不断增长的扩展和常见 PHP 应用程序范围，声称可提升 4 倍性能，并提供 API 允许 PHP 访问 Java 库。 |

|   ||   |

|   || ***主网站*** : [http://quercus.caucho.com/](http://quercus.caucho.com/) |

|   ||   |

|   || ***安装信息与主文档*** : [http://quercus.caucho.com/quercus-3.1/doc/quercus.xtp](http://quercus.caucho.com/quercus-3.1/doc/quercus.xtp) |

| ![](Images/image00249.gif) || ***PHP-QB*** |

| --- | --- |

|   ||   |

|   || 旨在使用 PHP 进行图形编程的虚拟机。实现了令人印象深刻的性能提升，但实现了静态类型并具有数组限制。可以使用 G++ 或其他外部编译器编译为可执行文件。 |

|   ||   |

|   || ***主网站*** : [http://www.php-qb.net/](http://www.php-qb.net/) |

|   ||   |

