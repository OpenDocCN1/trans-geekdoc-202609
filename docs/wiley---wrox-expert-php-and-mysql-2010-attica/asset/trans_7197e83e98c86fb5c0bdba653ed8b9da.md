
(gdb) continue
Continuing.

- 2. 在另一个终端中，重新运行导致错误的 SQL 语句：

```
mysql> select db_bytes(name) from sch;
ERROR 2006 (HY000): MySQL server has gone away
No connection. Trying to reconnect.
Connection id: 125
Current database: test
```

- 3. 该命令会在此处挂起，因为调试器已在您之前设置的断点 db_bytes_init() 处停止了执行。回到调试器终端窗口，您将看到：

```
[Switching to Thread 0x41cf6950 (LWP 18597)]

Breakpoint 1, db_bytes_init (initid=0x53f7610, args=0x53f75d8, message=0x53eb6ad "")
    at db_bytes.c:66
{
```

- 4. 您需要通过输入 gdb 命令 step（或仅字母 s）逐步执行 db_bytes_init()：

```
(gdb) step
if (args->arg_count != 1 || args->arg_type[0] !=
STRING_RESULT)
(gdb) step
66  {
(gdb) s
if (args->arg_count != 1 || args->arg_type[0] !=
STRING_RESULT)
(gdb) s
total_bytes = malloc(sizeof(char) * 12);
```

- 5. 接下来您逐步执行到包含错误代码块的行。您可以打印 args->args 来查看其值，在本例中为 NULL（0x0）：

```
(gdb) s
91      if (strcmp("test", args->args[0])) {
(gdb) print *args->args
$1 = 0x0
```

- 6. 下一步将导致段错误：

```
(gdb) s

Program received signal SIGSEGV, Segmentation fault.
0x00007f424da2dbbe in db_bytes_init (initid=0x53f7610, args=0x53f75d8, message=<value optimized out>) at db_bytes.c:91
91      if (strcmp("test", args->args[0])) {
```

## 处理字面值

因此，您现在知道 bug 在哪里。如果您对 db_bytes() 使用字面值作为参数会怎样？请按照以下步骤操作：

- 1. 在 MySQL 客户端终端窗口中，UDF 使用字面值 'test' 被调用：

```
mysql> select db_bytes('test') from sch;
```

- 2. 在调试器终端窗口中，调试器将在同一个断点 db_bytes_init() 处停止。尽管这次，您会看到 args->args 实际上已设置。如果继续程序执行，这次不会出现段错误：

```
(gdb) continue
Continuing.
[Switching to Thread 0x41a1c950 (LWP 18907)]

Breakpoint 1, db_bytes_init (initid=0x53F75e0, args=0x53F75a8,
    message=0x53eb66d "")
    at db_bytes.c:66
66 {
(gdb) s
73     if (args->arg_count != 1 || args->arg_type[0] != STRING_RESULT)
(gdb) s
88     total_bytes = malloc(sizeof(char) * 12);
(gdb) s
91     if (strcmp("test", args->args[0])) {
(
(gdb) print *args->args
$1 = 0x53f7410 "test"
(gdb) continue
Continuing.
```

- 3. SQL 语句成功完成：

```
mysql> select db_bytes('test') from sch;
ERROR 2006 (HY000): MySQL server has gone away
No connection. Trying to reconnect.
Connection id:    125
Current database: test
```

| db_bytes('test') |
|------------------|
| 583855 |

1 row in set (38.32 sec)

## 调试总结

如前所述，这是设计使然，也是 UDF 调用被解析的方式，使用调试器是演示这一点以及学习 UDF 工作原理的绝佳方法。

您现在已经了解了使用调试器调试 MySQL 的基础知识。这只是一个入门介绍，但能让您体会到在编写 UDF 时排查问题所涉及的内容。

您也可以使用调试器来分析 MySQL 的工作原理。在代码中设置断点并逐步执行。通过这种方式逐步浏览程序执行过程，您可以学到很多。调试 MySQL 还有其他方法。在 UNIX 系统上，您可以使用 DDD（gdb 的前端）和 Eclipse 来获得更图形化的调试用户界面。对于 Windows，Microsoft 调试器具有出色的可视化界面，我甚至见过 UNIX 开发者有时使用 Windows 来调试某些问题，只为使用 Microsoft 调试器！

## 摘要

本章向您介绍了 MySQL 用户定义函数（UDF）的使用和开发。这些函数允许您通过创建在 MySQL 服务器内运行的自己的函数来扩展 MySQL 的功能，您可以通过 PHP 应用程序发出的 SQL 语句使用这些函数。用户定义函数使用 C 或 C++ 编写，需要编译成共享库，然后安装到 MySQL 中。本章展示了实用 UDF 示例 `db_bytes()` 的完整开发过程，该函数仅汇总 MySQL 模式子目录中包含的文件的字节数。本章从概念化、项目设置、为实现 UDF 编写必要的 C 函数，到 UDF 的编译和安装，以及在 SQL 语句中使用 UDF 来提供所有模式及其磁盘字节数的列表，带您完成了整个过程。

您还学习了如何从 PHP 应用程序中使用 `db_bytes()`、可以使用 UDF 的其他有用 SQL 语句，以及如何使用 GNU 调试器 gdb 调试 UDF。

## 8

## 编写 PHP 扩展

## 本章内容

- 设置新的 PHP 扩展项目
- 向扩展添加函数
- 处理来自 PHP 的变量
- 使用哈希表和数组
- 访问 MySQLi 查询结果
- 定义对象
- 定义接口
- 提供有关扩展的更多信息

有时纯 PHP 是不够的。最常见的情况是速度成为问题或需要与第三方非 PHP 库集成时。编写扩展对于创建持久资源也非常有用。

本章构建了一个功能完整的 PHP 扩展，它可与 MySQLi Result 对象配合使用，并执行与每种数据类型相关的各种任务。它仅用于演示目的，但运行良好，可以作为自定义扩展的良好起点。

本章假设您对 C 语言有中级理解。特别有用的技能包括指针和内存分配。

## 设置构建环境

对于许多开发者来说，编写 PHP 扩展最令人沮丧的部分之一就是扩展并不是用 PHP 编写的。与 MySQL UDF 一样，PHP 扩展也是用 C 编写的。C 语言没有自动垃圾回收器、内存管理或 PHP 的任何便利之处，因此使用起来可能困难得多。然而，得益于为 PHP 提供动力的 Zend 引擎和 PHP 引擎本身，它在保持 PHP 所有灵活性的同时，还增加了低级语言的优势，可直接访问文件和内存。

PHP 和 Zend 引擎是用 C 编写的。需要注意 C 与 C++ 之间的区别，因为一些了解 C 的开发者可能会发现文件和内存访问等常见任务有所不同。编译 PHP 扩展时，您可以选择包含 Zend 和 PHP 的头文件。头文件定义了许多可在扩展内部使用的不同函数和宏。其中许多的文档很难找到；本书涵盖了几乎所有扩展都需要最常见的一些内容，以及一些更高级的内容。

在深入设置扩展之前，重要的是首先在您的机器上拥有 PHP 源代码。如果您从头编译过 PHP，您可能已经有了。如果没有，您可以从 PHP 网站下载。喜欢冒险的人可以从 Subversion 下载当前源代码，这在您决定公开发布扩展并希望提前开始为下一个版本开发和测试时很有用。

PHP 源代码目录有许多文件夹。在大多数情况下，您只需要关心其中三个：

- `Zend` 目录包含 Zend 引擎（为 PHP 提供动力的核心引擎）的头文件和源文件。基本的扩展将允许您仅使用标准 PHP API 访问 PHP 的大部分功能；然而，Zend 引擎具有执行许多更复杂和低级任务的工具。
- `main` 目录类似于 `Zend` 目录，但仅用于 PHP 特定功能。在这里您会找到定义对所有 PHP API 函数访问的头文件。值得注意的是，PHP 流包装器（用于 I/O）是在这里定义的。PHP 库包含大量可能看起来冗余的功能；然而，它们很重要，因为 PHP 版本遵守 `php.ini` 文件中的所有安全和配置设置。
- 第三个目录，也是您将花费大部分时间的地方，是 `ext` 目录。`ext` 目录存储所有 PHP 扩展的源代码——包括您自己编写的扩展。

源代码在机器上后，有必要确保您拥有构建 PHP 所需的所有工具。如果您过去构建过 PHP，应该不会有问题。在 Linux/UNIX 系统上，需要安装 gcc、flex 和 bison。在 Windows 上，配置和编译更困难。然而，一般来说，在 Linux/UNIX 环境中编写的扩展与 Windows 兼容，前提是遵守最佳实践。本书建议如果您计划分发扩展，请在 UNIX/Linux 环境中进行开发。由于大多数扩展部署到 Linux 服务器，本章其余部分仅关注 Linux/UNIX。
