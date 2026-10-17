
# PHP 扩展与嵌入（开发者库）

## 概述

在短短几年内，PHP 已迅速从一种小众语言演变为一种强大的 Web 开发工具。现在，PHP 已应用于超过 1400 万个网站，比以往任何时候都更加稳定且具有扩展性。然而，关于如何扩展 PHP 并没有相关文档；那些寻求构建 PHP 扩展并提高 PHP 应用性能和功能的开发者，只能依靠口口相传，并在缺乏系统性、有帮助指导的情况下摸索 PHP 内部机制。虽然编写扩展的基础知识相当容易掌握，但更高级功能的学习曲线更加陡峭，可能很难克服。这在任何中高流量的网站上都是常见现象，迫使公司聘佣才华横溢且价格昂贵的开发者来提高性能。通过《扩展与嵌入 PHP》，Sara Golemon 让编写扩展成为每位 PHP 开发者都能触及的目标，同时引导读者了解 PHP 内部机制。

## 索引

## 献献

给我的伴侣 Angela，感谢当我夜夜忙碌让这本书成为现实时，你的耐心和守候。给我的家人，你们赋予了我力量、勇气和信心，成就了今天的我。

## 前言

如果在我在 PHP 项目提交第一个补丁时，有人告诉我三年后我将就此主题写一本书，我会对你说一些难听的话，并将你拉进 `/ignore` 名单。然而，PHP 开发的文化是如此令人欢迎，又如此令人痴迷，回首过去来，我唯一的问题是：“为什么没有更多的扩展开发者？”

当然，简单（容易）的答案是：虽然 PHP 关于用户空间语法和函数的文档在各方面都是无可比拟的，但其内部机制的文档远未完整，并且持续过时。即使是现在，`PHP6` 迈向完全 Unicode 支持的进展正在引入数十个新的 API 调用，并改变了从用户空间脚本编写人员到核心开发者所有人看待字符串和二进制安全的方式。

对于我们这些从事 PHP 并最熟悉其特性的的人来说，回答通常是：“查看源码”。公平地说，这是一个有效的答案，因为核心以及扩展（包括内置扩展和 `PECL` 扩展）中的几乎每个方法都慷慨地充满了注释，并按照严格且遵循良好的标准进行了格式化，易于阅读……一旦你习惯了它。

但新开发者应该从哪里开始呢？他们如何发现 `PHP_LONG_MACRO_NAME()` 是做什么的？`zval` 和 `pval` 之间究竟有什么区别？（提示：没有区别；它们是同一种变量类型）。本书旨在让 PHP 内部机制更接近用户空间语言那种受欢迎的易读性水平。通过展示 PHP 和 `Zend Engine` 规划良好且强大的 API，我们都将受益于来自商业领域和开源社区的更丰富的人才库。

## 关于作者

Sara Golemon 是一个自认为的终端极客（此处是双关语）。她作为核心开发者参与 PHP 项目已近四年，并以“与其他人方式略有不同”的方法来处理这种语言而闻名；你可以欢迎将这句话视为赞誉，也可以视为批评。在过去的六年里，她在加利州大学伯克利分校担任程序员/分析师，在此之前她曾在美国地区法院任职多年。Sara 还是十几个 `PECL` 扩展以及 `libssh2` 的开发者和首席维护者，后者是一个与 PHP 无关的项目，它提供了访问 `SSH2` 协议的便捷方法。在写本书期间，她正积极参与 `PHP6` 中兼容 Unicode 的流层迁移工作。

## 我们想听听你的声音！

作为本书的读者，你是我们最重要的评论家和反馈者。我们重视你的意见，并想知道我们做得对的地方、哪些地方可以改进、你希望看到我们出版哪些领域，以及你愿意传给我们的任何格言。

你可以直接发送电子邮件或写信给我，让我知道你对这本书的喜欢或不喜欢之处，以及我们可以做什么让我们的书籍更强大。

请注意，我无法帮助你解决与本书主题相关的技术问题，由于收到的邮件很多，我可能无法回复每条信息。

你在写信时，请务必包含本书的书名和作者，以及你的名字和电话或邮箱地址。我会仔细审查你的评论，并与参与本书的作者和编辑分享。

| 邮箱： | opensource@samspublishing.com |
| --- | --- |
| 邮件： | Mark Taber Associate Publisher Sams Publishing 800 East 96th Street Indianapolis, IN 46240 USA |

![](img/300115)

## 读者服务

![](img/300115)

## 引言

### 你应该读这本书吗？

你选择这本书可能是因为对 PHP 感兴趣并并了解它在底层是如何运行的。如果你是该语言的新手，它可能会让你感到无从从，但如果你是一个经验开发者，它将为你提供深刻的见解。

### 为什么你想扩展 PHP？

扩展 PHP 有四个常见原因。到目前为止，最常见的原因是链接外部库。这种扩展是开发者在描述 PHP 为“胶水”时所指的类型。构成扩展的代码本身不执行任何重大工作；相反，它在 PHP 和库之间建立了一个桥梁。

#### 1. 特殊内部操作

扩展 PHP 的另一个常见原因是执行特殊的内部操作，例如声明超级全局，这在用户空间是无法实现的。像 `apd`（高级调试器）和 `runkit` 这样的扩展通过暴露虚拟机执行栈的一部分来执行这种内部工作。

排第三的是对速度的纯粹需求。PHP 代码必须经过分词、编译并在虚拟机环境中步进执行，这永远无法像原生代码一样。某些工具（称为 Opcode 缓存）允许脚本在重复执行时跳过分词和编译步骤，但它们永远无法加速执行步骤。通过将其翻译为 C 代码，维护者牺牲了一些让 PHP 变得强大的设计易用性，但获得了几倍级的速度提升。

#### 2. 保护知识产权

最后，一个脚本作者可能在一个特别巧妙的子程序上投入了多年心血，现在想将其出售给另一方，但不想暴露源代码。一种方法是使用操作码加密程序；然而，这种方法比机器码扩展更容易被破解。毕竟，为了对被许可方有用，他们的 PHP 构建版本在某个时刻必须能够访问编译后的字节码。解密后的字节码进入内存后，将其提取到磁盘的路程很短。而字节码比原生二进制文件更容易被解析成源脚本。

#### 3. 什么是扩展

本书旨在教你两件事。首先，它将向你展示如何扩展语言。其次，它将向你展示如何使用扩展。为了理解这一点，我们需要理解扩展到底是什么。

图 I.1. 胶水扩展

![](img/in01)

## 嵌入究竟实现了什么？

假设你用一种像 `C` 这样优秀、快速、精简的编译型语言编写了整个应用程序。为了让应用程序对你的用户或客户更有用，你希望为他们提供一种方法，让他们使用简单的高级语言来编写某些行为，而他们不需要担心内存管理、指针、链接或任何那些复杂的内容。

如果这种功能的用处并非一而易见，请考虑一下：如果没有宏，你的办公效率软件会变成什么样？或者如果没有批处理文件，你的命令行会变成什么样？在没有 `JavaScript` 的网络浏览器中，哪些行为是不可能实现的？如果你无法通过编程让 F1 键在恰恰的时间发射火箭筒发射三连发来击败愤怒的猴子，你还能捕捉神奇的呼啦并救援王子吗？嗯，也许可以，但你的大指会很疼。

所以，假设你想在应用程序中构建可自定义的脚本功能；你可以编写自己的编译器，构建一个执行框架，并花费数千小时对其进行调试；或者你可以采用像 `PHP` 这样现成的企业级语言，并将其解释器直接嵌入到你的应用程序中。这是一个艰难的选择，不是吗？

## 里面包含什么？

本书分为三个主要主题。首先，在第一部分“重新认识 PHP”中，你将从内到外重新接触 `PHP`。

你将看到 `PHP` 解释器的构建模块是如何组合在一起的，并学习来自用户空间的熟悉概念是如何映射到其内部表示的。

在第二部分“扩展”（Extensions）中，你将开始构建一个功能性的 `PHP` 扩展，并学习如何使用 `PHPAPI` 的额外功能。在本节结束时，你应该将几乎任何 `PHP` 脚本翻译成更快、更精简的 `C` 代码。你也将准备好链接到外部库，并执行从用户空间无法的操作。

在第三部分“嵌入”（Embedding）中，你将从相反的角度处理 `PHP`。在这里，你将从一个普通的应用程序开始，添加 `PHP` 脚本支持。你将学习如何利用 `safe_mode` 和其他安全特性安全地执行用户提供的代码，并同时协调多个请求。

最后，你将找到一组附录，包含 API 调用参考指南、常见问题的解决方案以及在哪里可以找到现有的扩展进行参考。

## PHP 对比 Zend

关于 `PHP` 你需要知道的第一点是，它实际上由五个独立部分组成，如图 I.2 所示。

### 图 I.2. PHP 的结构。

[查看全尺寸图像

![](img/infig02.jpg)

堆的底部是 `SAPI`（服务器 API）层，它协调你在第 1 章 “PHP 生命周期”中看到的生命周期过程。这一层与 Web 服务器（通过 `mod_php5.so`）或命令行（通过 `bin/php`）接口。在第三部分中，你将链接到在该层运行的嵌入 `SAPI`。

`SAPI` 层之上是 `PHP Core`。核心部分为关键事件提供了绑定层，并处理某些低级操作，如文件流、错误处理以及启动/关闭触发。

紧邻核心部分，你会找到 `Zend Engine`，它将人类可读的脚本解析并编译成机器可读的字节码。`Zend` 还在虚拟机内部执行这些字节码，在其中读取和写入用户空间变量，管理程序流，并定期将控制权交给其他层之一（例如在函数调用期间）。`Zend` 还提供了按请求的内存管理和用于环境操作的健壮 API。

位于 `PHP` 和 `Zend` 之上的是扩展层。

| PEAR | PHP 扩展与应用仓库。PEAR 项目 ([`pear.php.net`](http://pear.php.net)) 是社区生成的开源免费项目的官方中心。PEAR 包含了数百个用 PHP 脚本编写的面向对象的类，为常见的编程任务提供了即插用的解决方案。尽管名字如此，PEAR 并不包含 C 语言编写的 PHP 扩展。 |
| --- | --- |
| PECL | PHP 扩展代码库，读作 "pickle"。PECL ([`pecl.php.net`](http://pecl.php.net)) 是 PEAR 项目的 C 代码衍生分支，它使用了许多相同的打包、部署和安装系统。PECL 包通常是 PHP 扩展，但也可能包含 Zend 扩展或 SAPI 实现。 |
| PHP 扩展 | 也称为模块（module）。它是一个编译代码的独立包，定义了用户空间可访问的函数、类、流实现、常量、ini 选项和特殊资源类型。在文中任何地方看到 `extension` 一词时，你都可以认为指的是 PHP 扩展。 |
| Zend 扩展 | PHP 扩展的一种变体，用于 OpCode 缓存和编码器等特殊系统。Zend 扩展不在本书的涵盖范围内。 |
| 用户空间 | 实际用 PHP 语言编写的脚本所可见的环境和 API 库。用户空间无法访问 Zend 引擎和各种 PHP 扩展显式授予它的 PHP 内部机制或数据结构。 |
| 内部（C 空间） | 引擎和扩展代码。该术语指所有用户空间代码无法直接访问的内容。 |

## 第 1 章：PHP 周期

在常见的 Web 服务器环境中，你永远不会显式地启动 PHP 解释器；你会启动 Apache 或其他 Web 服务器，由它根据需要加载 PHP 并处理脚本——即在请求了 `.php` 文档时进行处理。

### 一切都始于 SAPI

尽管看起来非常不同，但 CLI 二进制执行文件的行为实际上完全相同。在系统提示符处输入 `php` 命令会启动“命令行 sapi”，它像一个设计用于处理单个请求的微 Web 服务器。当脚本运行结束时，这个微型 PHP-web 服务器就会关闭并将控制权交给 shell。

### 启动与关闭

这个启动和关闭过程分为两个独立的启动阶段和两个独立的关闭阶段。其中一个周期用于整个 PHP 解释器执行初始结构和值的设置，这些值将在整个 SAPI 生命周期内持续存在。另一个周期则用于仅在单个页面请求期间持续的临时设置。

在初始启动期间，在任何请求发生之前，PHP 会调用每个扩展的 `MINIT`（模块初始化）方法。在这里，扩展需要声明常量、定义类，并注册资源、流和过滤器处理器，这些处理器将供后续所有的脚本请求使用。诸此类被设计为跨所有请求存在的特性被称为“持久性”（persistent）的。

一个常见的 `MINIT` 方法可能如下：

```
/* 初始化 myextension 模块
 * 这将在 SAPI 启动时立即发生
 */
PHP_MINIT_FUNCTION(myextension)
{
    /* 全局变量：第 12 章 */

#ifdef ZTS
    ts_allocate_id(&myextension_globals_id,
        sizeof(php_myextension_globals),
        (ts_allocate_ctor) myextension_globals_ctor,
        (ts_allocate_dtor) myextension_globals_dtor);
#else
    myextension_globals_ctor(&myextension_globals TSRMLS_CC);
#endif


    /* REGISTER_INI_ENTRIES() 指向一个全局
     * 该结构将在
     * 第 13 章“INI 设置”中介绍
     */
    REGISTER_INI_ENTRIES();

    /* define('MYEXT_MEANING', 42); */
    REGISTER_LONG_CONSTANT("MYEXT_MEANING", 42, CONST_CS | CONST_PERSISTENT);
    /* define('MYEXT_FOO', 'bar'); */
    REGISTER_STRING_CONSTANT("MYEXT_FOO", "bar", CONST_CS | CONST_PERSISTENT);


    /* 资源：第 9 章 */
    le_myresource = zend_register_list_destructors_ex(
                    php_myext_myresource_dtor, NULL,
                    "My Resource Type", module_number);
    le_myresource_persist = zend_register_list_destructors_ex(
                    NULL, php_myext_myresource_dtor,
                    "My Resource Type", module_number);


    /* 流过滤器：第 16 章 */
    if (FAILURE == php_stream_filter_register_factory("myfilter",
                   &php_myextension_filter_factory TSRMLS_CC)) {
        return FAILURE;
    }


    /* 流包装器：第 15 章 */
    if (FAILURE == php_register_url_stream_wrapper ("myproto",
                   &php_myextension_stream_wrapper TSRMLS_CC)) {
        return FAILURE;
    }


    /* 自动全局变量：第 12 章 */
#ifdef ZEND_ENGINE_2
    if (zend_register_auto_global("_MYEXTENSION", sizeof("_MYEXTENSION") - 1,
                                                NULL TSRMLS_CC) == FAILURE) {
        return FAILURE;
    }
    zend_auto_global_disable_jit ("_MYEXTENSION", sizeof("_MYEXTENSION") - 1
                                                     TSRMLS_CC);
#else
    if (zend_register_auto_global("_MYEXTENSION", sizeof("_MYEXTENSION") - 1
                                                     TSRMLS_CC) == FAILURE) {
        return FAILURE;
    }
#endif
    return SUCCESS;
}
```

在初始启动期间，在任何请求发生之前，PHP 会调用每个扩展的 `MINIT`（模块初始化）方法。在这里，扩展需要声明常量、定义类，并注册资源、流和过滤器处理器，这些处理器将供后续所有的脚本请求使用。诸此类被设计为跨所有请求存在的特性被称为“持久性”（persistent）的。

一个常见的 `MINIT` 方法可能如下：

（此处代码块已翻译，见上文）

在请求发生后，PHP 设置运行环境，包括符号表（存储变量的地方）并同步目录配置值。然后 PHP 再次遍历扩展，这次调用每个扩展的 `RINIT`（请求初始化）方法。在这里，扩展可以重置全局变量为默认值，向符号表中预填充变量，或者执行诸如将页面请求记录到文件的任务。`RINIT` 可以被视为所有脚本的 `auto_prepend_file` 指令。

一个 `RINIT` 方法预期如下：



在每个页面开始时运行：

```c
PHP_RINIT_FUNCTION(myextension)
{
    zval *myext_autoglobal;

    /* 将 MINIT 函数中声明的
     * 自动全局变量初始化为
     * 空数组。
     * 这等同于执行：
     * $_MYEXTENSION = array();
     */
    ALLOC_INIT_ZVAL(myext_autoglobal);
    array_init(myext_autoglobal);
    zend_hash_add(&EG(symbol_table), "_MYEXTENSION", sizeof("_MYEXTENSION") - 1,
                                (void**)&myext_autoglobal, sizeof(zval*), NULL);

    return SUCCESS;
}
```

请求处理完成后（无论是到达脚本末尾还是通过 `die()` 或 `exit()` 语句退出），PHP 会通过调用每个扩展的 `RSHUTDOWN`（请求关闭）方法启动清理过程。`RSHUTDOWN` 对应 `auto_append_file`，就像 `RINIT` 对应 `auto_prepend_file` 一样。然而，`RSHUTDOWN` 与 `auto_append_file` 主要区别在于，`RSHUTDOWN` 总是执行，而用户脚本内部调用 `die()` 或 `exit()` 会跳过任何 `auto_append_file`。

在符号表和其他资源销毁之前，可以在 `RSHUTDOWN` 中处理需要执行的最后任务。在所有 `RSHUTDOWN` 方法完成后，符号表中的每个变量都会被隐式地 `unset()`，在此期间，所有非持久资源和对象的析构函数将按顺序调用，以优雅地释放资源。

```php
/* 在每个页面请求的结束时运行
 */
PHP_RSHUTDOWN_FUNCTION(myextension)
{
    zval **myext_autoglobal;

    if (zend_hash_find(&EG(symbol_table), "_MYEXTENSION", sizeof("_MYEXTENSION"),
                                         (void**)&myext_autoglobal) == SUCCESS) {
        /* 使用 $_MYEXTENSION 数组
         * 值进行某些有意义
         * 操作
         */
        php_myextension_handle_values(myext_autoglobal TSRMLS_CC);
    }
    return SUCCESS;
}
```

最后，当所有请求都已完成且 Web 服务器或其他 SAPI 准备关闭时，PHP 会遍历每个扩展的 `MSHUTDOWN`（模块关闭）方法。这是扩展取消注册处理程序并释放在 `MINIT` 周期期间分配的持久内存的最后机会。

```php
/* 此模块正在被卸载
 * 常量和函数将被
 * 自动清理，
 * 持久资源、类条目、
 * 以及流处理器必须
 * 手动取消注册。
 */
PHP_MSHUTDOWN_FUNCTION(myextension)
{
    UNREGISTER_INI_ENTRIES();
    php_unregister_url_stream_wrapper ("myproto" TSRMLS_CC);
    php_stream_filter_unregister_factory ("myfilter" TSRMLS_CC);
    return SUCCESS;
}
```

![](img/30011536.html)

# 生命周期

每个 PHP 实例（无论是从 `init` 脚本启动还是从命令行启动）都遵循一系列事件，这些事件涉及之前涵盖的请求/模块初始化/关闭事件，以及脚本本身的实际执行。每个启动和关闭阶段的执行次数和频率取决于所使用的 SAPI。四种最常见的 SAPI 配置是 CLI/CGI、多进程模块（Multiprocess Module）、多线程模块（Multithreaded Module）和嵌入式（Embedded）。

## CLI 生命周期

CLI（以及 CGI）SAPI 在其单请求生命周期上相当独特；然而，模块与请求步骤仍然是离散循环中的周期。图 1.1 显示了当从命令行调用 `test.php` 脚本时 PHP 解释器的进展过程。

### 图 1.1. 请求周期与引擎生命周期。

![](img/01fig01.jpg)

## 多进程生命

嵌入到 Web 服务器中最常见的 PHP 配置是使用为 Apache 1 编译的 APXS 模块的 PHP，或者使用 Pre-fork MPM 的 Apache 2。许多其他 Web 服务器配置也属于这一类别，在本书的剩余部分中将其统称为“多进程模型”。

它之所以被称为多进程模型，是因为当 Apache 启动时，它立即派生（fork）几个子进程，每个子进程都有自己的进程空间并相互独立运行。在给定的子进程内部，该 PHP 实例的生命周期看起来非常熟悉，如图 1.2 所示。唯一的区别是多个请求被夹在单个 `MINIT`/`MSHUTDOWN` 对之间。

### 图 1.2. 个体进程生命周期。

![](img/01fig02.jpg)

该模型不允许任何子进程感知另一个子进程的数据，但它允许子进程随时死亡并替换，而不影响任何其他子进程的稳定性。图 1.3 显示了单次 Apache 调用多个子进程以及对它们每个 `MINIT`、`RINIT`、`RSHUTDOWN` 和 `MSHUTDOWN` 方法的调用。

### 图 1.3. 多进程生命。

![](img/01fig03.jpg)

## 多线程生命

PHP 越来越多出现在多线程 Web 服务器配置中，例如 IIS 的 ISAPI 接口和 Apache 2 的 Worker MPM。在多线程 Web 服务器下，任何时刻只有一个进程在运行，但多个线程在该进程空间内同时执行。这允许避免一些开销（包括避免重复调用 `MINIT`/`MSHUTDOWN`），允许真正的全局数据仅分配和初始化一次，并可能为多个请求确定性地共享信息打开门。图 1.4 显示了从 Apache 2 等多线程 Web 服务器运行时，PHP 内部发生的并行进程流。

### 图 1.4. 多线程生命。

[\[查看全尺寸图像\]](01fig04_alt.jpg)

![](img/01fig04.jpg)

## 嵌入生命

回想起嵌入 SAPI 只是遵循 CLI、APXS 或 ISAPI 接口相同规则的另一种 SAPI 实现，很容易想象请求的生命周期遵循相同的路径路径：模块初始化 => 请求初始化 => 请求 => 请求关闭 => 模块关闭。事实上，嵌入 SAPI 与它的兄弟完美同步地遵循每一个步骤。

嵌入 SAPI 显得独特之处在于，请求可能由多个脚本片段提供，这些片段作为单个完整请求的一部分。在大多数配置下，控制权还会 PHP 和调用应用程序之间多次往返。

尽管嵌入请求可能由一个或多个代码元素组成，但嵌入应用同样受到 Web 服务器相同的请求隔离要求。为了处理两个或多个同时的嵌入环境，你的应用程序要么需要像 Apache1 那样派生，要么需要像 Apache2 那样开启。尝试在单线程进程空间内处理两个独立的请求环境会导致意外结果。

pixel.jpg

# Zend 安全

当 PHP 处于婴儿阶段时，它作为单进程 CGI 运行，不需要线程安全，因为进程空间不会超出单个请求。内部变量可以在全局范围内声明，只要正确初始化即可访问。任何未正确清理的资源将在 CGI 进程终止时释放。

后来，PHP 被嵌入到多进程 Web 服务器中。内部变量仍然可以定义并由活动请求安全地访问，只要在请求开始时正确初始化并在结束时清理。此时增加了每个请求内存管理以防止资源泄漏失控。

然而，随着单进程多线程 Web 服务器的出现，处理全局数据的方法变得必要。最终这演变成了一个名为 TSRM（线程安全资源管理）的新层。

当在请求期间需要访问该数据段时，扩展会从 TSRM 层请求当前线程资源池的指针，并根据 `ts_allocate_id()` 返回的资源 ID 建议的相应索引进行偏移量。

换句话说，从代码流的角度来看，`SAMPLE_G(sampleint) = 5;` 这条语句可能会在与之前的 `MINIT` 语句相关的模块中看到。在线程安全的构建（build）下，该语句会通过一系列中间宏展开为以下内容：

```c
(((php_sample_globals*)(*((void ***)tsrm_ls))[sample_globals_id-1])->sampleint =
5;
```

如果你在解析该语句时遇到困难，不要担心；它已经深度集成到 PHPAPI 中，以至于有些开发者根本不打算去学习它的工作原理。

## 何时不使用线程安全

由于在 PHP 的线程安全构建中访问全局资源涉及到在正确的数据池中查找正确偏移量的开销，因此其运行速度最终比非线程版本慢，而在非线程版本中，数据直接从一个在编译时计算好地址的全局变量中提取。

再次考虑之前的例子，这次是在非线程的构建下：

```c
typedef struct {
    int sampleint;
    char *samplestring;
} php_sample_globals;
php_sample_globals sample_globals;
PHP_MINIT_FUNCTION(sample)
{
    php_sample_globals_ctor(&sample_globals TSRMLS_CC);
    return SUCCESS;
}
```

你在这里首先会注意到，你并没有声明一个 `int` 来标识对别处定义的全局结构体的引用，而是直接在进程的全局作用域内定义该结构。这意味着之前的 `SAMPLE_G(sampleint) = 5;` 语句只需要展开为 `sample_globals.sampleint = 5;`。简单、快速且高效。

非线程构建还具有进程隔离的优势，因此如果某个请求遇到了完全意外之外的情况，它可以直接退出甚至发生段错误（segfault），而不会导致整个 Web 服务器崩溃。事实上，Apache 的 `MaxRequestsPerChild` 指令就是为了利用这种效应，通过定期杀死子进程并生成新的进程来维持。

## 环境无关的全局访问

在创建扩展时，你不一定知道其构建目标的环境是否需要线程安全。幸运的是，你将使用的标准包含文件集中部分条件定义了 `ZTS` 预处理器标记。当 PHP 为线程安全而构建时（无论是因为 SAPI 需要，还是通过 `enable-maintainer-zts` 选项），该值会被自动定义，并可以使用常用的指令（如 `#ifdef ZTS`）进行测试。

正如你刚才看到的，只有在线程安全池确实存在时，在其中分配空间才有意义，而只有在 PHP 为线程安全而编译时，该池才会存在。这就是为什么在之前的示例中，它被封装在对 `ZTS` 的检查中，并为非 ZTS 构建调用非线程的替代方案。

在本章较早之前看到的 `PHP_MINIT_FUNCTION(myextension)` 示例中，使用了 `#ifdef ZTS` 来条件条件调用全局的正确版本。正如你刚才看到的，只有在线程安全池确实存在时，在其中分配空间才有意义，而只有在 PHP 为线程安全而编译时，该池才会存在。这就是为什么在之前的示例中，它被封装在对 `ZTS` 的检查中，并为非 ZTS 构建调用非线程的替代方案。

这就是 `enable-maintainer-zts` 派用用场。在编译 PHP 时，通过向你的 `./configure` 语句添加这一行，你的构建将自动包含 ZTS，即使你当前的 SAPI（如 `CLI`）并不需要它。启用此开关，你可以避免这种常见且必要的编程错误。

## Note

在 PHP4 中，`enable-maintainer-zts` 标记被称为 `enable-experimental-zts`；请务必根据你的 PHP 版本使用正确的标记。

### 寻找丢失的 `tsrm_ls`

有时，无法将 `tsrm_ls` 指针传递到需要它的函数中。通常是因为你的扩展正在与一个使用回调函数的库交互，而该库没有为返回抽象指针提供空间。考虑以下代码：

```c
void php_myext_event_callback(int eventtype, char *message)
{
    zval *event;

    /* $event = array('event'=>$eventtype,
                    'message'=>$message) */
    MAKE_STD_ZVAL(event);
    array_init(event);
    add_assoc_long(event, "type", eventtype);
    add_assoc_string(event, "message", message, 1);

    /* $eventlog[] = $event; */
    add_next_index_zval(EXT_G(eventlog), event);
}
PHP_FUNCTION(myext_startloop)
{
    /* The eventlib_loopme() 函数 
     * 由外部库导出，
     * 等待事件发生，
     * 然后将其分发给指定的
     * 回调处理器。
     */
    eventlib_loopme(php_myext_event_callback);
}
```

虽然这段代码段目前还不完全没有任何意义，但你会立即注意到回调函数使用了 `EXT_G()` 宏，众所周知它在线程构建（threaded builds）下需要 `tsrm_ls` 指针。更改函数原型没有用处，因为外部库没有 PHP 线程安全模型，也不应该有。那么，如何以可以被使用的方式恢复 `tsrm_ls` 呢？

解决方案是以名为 Zend 宏 `TSRMLS_FETCH()` 的形式出现的。当它被放置在代码段的顶部时，该宏将根据当前的线程上下文进行查找，并声明 `tsrm_ls` 指针的本地副本。

尽管你可能想随处使用这个宏而不费力通过函数调用传递 `tsrm_ls`，但重要的是，调用 `TSRMLS_FETCH()` 需要相当的计算时间来完成。在单次迭代中显然察觉不到，但随着线程数量的增加以及调用 `TSRMLS_FETCH()` 的实例增加，你的扩展将逐渐开始显示出性能瓶颈。请务必节节使用。

## Note

为了确保与 C++ 编译器的兼容，请确保将 `TSRMLS_FETCH()` 以及所有的变量声明放在给定块作用域的顶部、任何语句之前。由于 `TSRMLS_FETCH()` 宏本身可以以几种不同的方式解析，最好将其放在给定声明头中声明的最后一个变量。

### 总结

在本章中，你窥见了后续章节中将探索的几个概念。你还为理解底层运作奠定了基础，不仅是在你将要构建的扩展内部，还包括 Zend Engine 和 TSRM 层的幕后，你将在将在应用程序中嵌入和部署 PHP 时利用这些层级。

## 第 2 章：从内而外的变量

**所有编程语言共有的共同点之一**是存储和检索信息的手段；PHP 也不例外。尽管许多语言要求预先声明所有变量并固定它们将包含的信息类型，但 PHP 允许程序员动态创建变量，并存储语言能够表达的任何类型的信息。当需要存储的信息时，它会自动转换为当时任何合适的类型。

由于你已经从用户态侧使用过 PHP，这个被称为“松散类型”（loose typing）的概念对你来说应该并不。在本章中，你将查看 PHP 的父语言 C 如何在内部对这些信息编码，C 要求严格的类型转换。

当然，编码数据只是问题的一半。为了跟踪所有这些信息，每个信息都需要一个标签和一个容器。从用户态领域，你会识别这些概念为变量名和作用域。

### 数据类型

PHP 数据存储的基本单元被称为 `zval`，或 Zend Value。它是定义在 `Zend/zend.h` 中的一个带有四个成员的小结构体，格式如下：

```c
typedef struct _zval_struct {
    zvalue_value value;
    zend_uint refcount;
    zend_uchar type;
    zend_uchar is_ref;
} zval;
```

直觉判断这些大多数成员的基本存储类型应该是简单的事：`refcount` 使用无符号整数，`type` 和 `is_ref` 使用无符号字符。然而，从 PHP5 开始，`value` 成员实际上是一个联合体（union）：

```c
typedef union _zvalue_value {
    long lval;
    double dval;
    struct {
        char *val;
        int len;
    } str;
    HashTable *ht;
    zend_object obj;
} zvalue_value;
```

这个联合体允许 Zend 存储 PHP 能够的许多不同类型。

### 表 2.1 Zend 使用的数据类型

| 类型 | 用途 |
| --- | --- |
| `IS_NULL` | 该类型在第一次使用时自动赋值，也可以显式赋值为 `NULL`。这种类型提供了一个特殊的“无值”，它区别于布尔 `FALSE`。 |
| `IS_BOOL` | 布尔变量可以有两种状态之一：`TRUE` 或 `FALSE`。用户态的条件表达式 `if`、`while`、三元运算符、`for` 在评估时会被隐式类型转换。 |
| `IS_LONG` | 整数数据类型使用主系统的 `signed long` 数据类型。在大多数 32 位平台上，这产生了存储范围 -2147483648 到 +2147483647。除了少数例外，当用户态脚本尝试存储范围之外的整数值时，它会自动转换为双浮点类型（`IS_DOUBLE`）。 |



| `IS_DOUBLE` | 浮点数据类型使用主系统的 `signed double` 数据类型。浮点数不是以精确精度存储的；而是使用一个公式将值表示为有限精度的分数（尾数）乘以 2 的幂（指数）。这种表示允许计算机仅用 8 字节存储宽范围的值（正或负），从小至 2.225x10⁻³⁸ 到上限约为 1.798x10³⁰⁸。遗憾的是，十进制中评估为精确数字的数字无法以二进制分数的形式存储。例如，十进制表达式 `0.5` 评估为精确的二进制数字 `0.1`，而十进制 `0.8` 变成重复的二进制表示 `0.110011001...`。当转换回十进制时，截断的二进制位会产生一个稍微偏移的值，因为它们无法存储整个数字。这就像尝试用十进制表示数字 `1/3` 一样：`0.333333` 非常接近，但并不精确，`3 * 0.333333` 不等于 `1.0` 证明了这一点。（这些范围限制基于常见的 32 位平台；范围可能随系统而异。） |

| `IS_STRING` | PHP 最通用的数据类型是字符串，其存储方式正如经验丰富的 C 程序员所预期的那样。系统会分配一块足够容纳字符串所有字节/字符的内存块，并将指向该字符串的指针存储在宿主 `zval` 中。 |

| | 关于 PHP 字符串值得注意的是，字符串的长度在 `zval` 结构中始终是显式标出的。这允许字符串包含 `NULL` 字节而不被截断。PHP 字符串的这一特性在以后被称为“二进制安全（binary safety）”，因为它们可以安全地包含任何类型的二进制数据。 |

| | 注意，为给定的 PHP 字符串分配的内存量至少是其长度加一。这最后一个字节被填充一个终止符 `NULL` 字符，这样不需要二进制安全的函数就可以直接将字符串指针传递给它们的底层方法。 |

| `IS_ARRAY` | 数组是一种特殊用途变量，其唯一功能是携带其他变量。与 C 语言的数组概念不同，PHP 数组不是统一数据类型的向量（例如 `zval arrayofzvals[];`）。相反，PHP 数组是一个复杂的数据桶集合，它们被链接到一个名为 `HashTable` 的结构中。每个 `HashTable` 元素（桶）包含两个相关信息：标签（label）和数据（data）。在 PHP 数组中，标签是数组内的关联索引或数值索引，数据是该键引用的变量（`zval`）。 |

| `IS_OBJECT` | 对象利用了数组的多元素数据存储功能，并在此基础上添加了方法（methods）、访问修饰符、作用域常量和特殊事件处理器。作为扩展扩展开发者，构建在 PHP4 和 PHP5 中运行同样良好的面向对象代码是一项特殊挑战，因为内部对象模型在 Zend Engine 1 (PHP4) 和 Zend Engine 2 (PHP5) 之间发生了巨大的变化。 |

| `IS_RESOURCE` | 某些数据类型无法直接映射到用户空间。例如，stdio 的 `FILE` 指针或 libmysqlclient 的连接句柄不能简单地映射到标量值数组，即使可以这样做也没有意义。为了保护用户态脚本的编写者免于处理这些问题，PHP 提供了一种种通用的资源数据类型。关于资源如何实现的细节将在第 9 章“资源数据类型”中介绍；目前只需知道它们存在即可。 |

在表 2.1 中列出的 `IS_*` 常量存储在 `zval` 结构的 `type` 元素中，并决定了在检查其值时应该查看 `zval` 结构中 `value` 元素的哪个部分。

检查类型值最明显的方法可能是像下面的代码段所示，从给定的 `zval` 中解引用：

```c
void describe_zval(zval *foo)
{
    if (foo->type == IS_NULL) {
        php_printf("The variable is NULL");
    } else {
        php_printf("The variable is of type %d", foo->type);
    }
}
```

显而易见，但这是错误的。

嗯，并不是错误，但绝对不是首选方法。Zend 头文件包含大量的 `zval` 访问宏，扩展作者在检查 `zval` 数据时应该使用这些宏。其主要原因是为了避免在引擎 API 发生变化时出现兼容性问题，作为辅助收益，代码通常会变得更易读。这里是相同的代码段，这次使用了 `Z_TYPE_P()` 宏：

```c
void describe_zval(zval *foo)
{
    if (Z_TYPE_P(foo) == IS_NULL) {
        php_printf("The variable is NULL");
    } else {
        php_printf("The variable is of type %d", foo->type);
    }
}
```

`_P` 后缀的宏表示它期望一个 `zval` 指针。`Z_TYPE()` 和 `Z_TYPE_P()` 别，`Z_TYPE_PP()` 分别期望 `zval`。

注意的是在这个中中，`````  ` ` `    ` `                     的实现细节。你将在第 5 章“编写你的第一个 PHP 扩展` 的机制。

### 数据值

对于标量类型、布尔、整数和双精度，对应的宏是 `BVAL`、`LVAL` 和 `DVAL`：

```c
void display_values(zval *zv)
{
    if (Z_TYPE(zv) == IS_BOOL) {
        php_printf("The boolean is: %s", BVAL(zv) ? "true" : "false");
    }
    if (Z_TYPE(zv) == IS_LONG) {
        php_printf("The long is: %ld", LVAL(zv));
    }
    if (Z_TYPE(zv) == IS_DOUBLE) {
        php_printf("The double is: %f", DVAL(zv));
    }
}
```

字符串，因为它们包含了两个属性，具有 `char*` 和 `int`：

```c
void display_string(zval *zstr)
{
    if (Z_TYPE(zstr) != IS_STRING) {
        php_printf("The wrong datatype was passed!");
        return;
    }
    PHPWRITE(STRVAL(zstr), STREN(zstr));
}
```

数组类型在内部存储为 `HashTable`，可以使用 `ARRVAL` 三元组访问：`ARRVAL(zv)`、`ARRVAL_P(pzv)`、`ARRVAL_PP(ppzv)`。查看源码和 PECL 模块时，可能会遇到 `HASH_OF()` 宏，它期望一个 `zval`。该宏已过时，不应使用。

对象表示复杂的结构，并有很多宏：`OBJ_HANDLE` 返回句柄标识符，`OBJ_HT` 用于表，`OBJCE` 用于类定义，`OBJPROP` 用于属性 `HashTable`，`OBJ_HANDLER` 用于操作句柄表中的特定句处理器。先不要担心这些各种宏的含义；它们将在第 10 章“PHP4 对象”和第 11 章“PHP5 对象”中详细介绍。

在 `zval` 内部，资源数据类型存储为简单的整数，可以通过 `RESVAL` 三元组访问。该整数被传递给 `zend_fetch_resource()` 函数，该函数根据数字标识符查找注册的资源。

### 数据创建

现在你已经知道了如何从 `zval` 中提取数据，是时候创建你自己的数据了。虽然 `zval` 可以简单地声明在函数顶部，但这将使变量的数据存储变为局部的，为了离开函数并到达用户空间，必须进行复制。

由于你总是希望创建的 `zval` 能够以某种形式到达用户空间，你需要为它分配内存块并将该块分配给 `zval` 指针。再次，使用 `malloc(sizeof(zval))` 的“明显”解决方案不是正确答案。相反，你需要使用另一个 Zend 宏：`MAKE_STD_ZVAL(pzv)`。该宏会在其他 `zval` 附近的优化内存中分配空间，自动处理内存溢出错误（你将在下一章进一步探讨），并初始化新 `zval` 的 `refcount` 和 `is_ref` 属性。

除了 `MAKE_STD_ZVAL()` 之外，你经常会在 PHP 源码中看到另一个创建 `zval*` 的宏：`ALLOC_INIT_ZVAL()`。这个宏与 `MAKE_STD_ZVAL()` 的区别在于，它将 `zval*` 的数据类型初始化为 `IS_NULL`。

一旦数据存储空间可用，就是时候为你全新的 `zval` 填充一些信息了。在阅读了之前关于数据存储的章节后，你可能已经准备好使用那些 `Z_TYPE_P()` 和 `Z_SOMEVAL_P()` 宏来设置你的新变量了。看起来是“显而易见”的解决方案对吧？

再次，显而易见往往是不够！

Zend 暴露了另一组用于设置 `zval*` 值的宏。以下是这些新宏以及它们是如何展开为你你已经熟悉的宏的。

```c
ZVAL_NULL(pvz);                   Z_TYPE_P(pzv) = IS_NULL;
```

虽然这个宏并没有比使用更直接的版本节省任何开销，但为了完整性，将其包含了进来。

```c
ZVAL_BOOL(pzv, b);                Z_TYPE_P(pzv) = IS_BOOL;
                                  Z_BVAL_P(pzv) = b ? 1 : 0;

ZVAL_TRUE(pzv);                   ZVAL_BOOL(pzv, 1);
ZVAL_FALSE(pzv);                  ZVAL_BOOL(pzv, 0);
```

注意，提供给 `ZVAL_BOOL()` 的任何非零值将导致一个真值。这当然是有意义的，因为在用户空间中转换为布尔值的任何非零值都会表现出相同的行为。在内部代码中硬编码值时，显式使用值 1 作为真被认为是良好的做法。提供 `ZVAL_TRUE()` 和 `ZVAL_FALSE()` 宏是为了方便，并且有时可以提高代码的可读性。

```c
ZVAL_LONG(pzv, l);                Z_TYPE_P(pzv) = IS_LONG;
                                  Z_LVAL_P(pzv) = l;

ZVAL_DOUBLE(pzv, d);              Z_TYPE_P(pzv) = IS_DOUBLE;
                                  Z_DVAL_P(pzv) = d;
```

基础标量宏是简单极了。设置 `zval` 的类型，并为其分配一个数值。

```c
ZVAL_STRINGL(pzv,str,len,dup);    Z_TYPE_P(pzv) = IS_STRING;
                                  Z_STRLEN_P(pzv) = len;
                                  if (dup) {
                                      Z_STRVAL_P(pzv) =
                                            estrndup(str, len + 1);
                                  } else {
                                     Z_STRVAL_P(pzv) = str;
                                  }

ZVAL_STRING(pzv, str, dup);       ZVAL_STRINGL(pzv, str,
                                                strlen(str), dup);
```

这里是 `zval` 的创建开始变得有趣的地方。字符串像数组、对象和资源一样，需要为它们的数据存储分配额外的内存。你将在下一章探索内存管理的陷阱；现在，只需注意，值 1 将分配新内存并复制字符串的内容，而值 0 将仅指向已有的字符串数据。

```c
ZVAL_RESOURCE(pzv, res);          Z_TYPE_P(pzv) = IS_RESOURCE;
                                  RESVAL_P(pzv) = res;
```

回想之前，资源在 `zval` 中以简单的整数形式存储，引用由 Zend 管理的查找表。因此，`ZVAL_RESOURCE()` 宏的作用非常像 `ZVAL_LONG()` 宏，但使用的是不同的类型。

### 数据存储

```c
struct _zval_struct {
    // ...
};
```

```c
typedef struct _zend_array {
  // ...
} zend_array;

typedef HashTable HashTable;

typedef enum {
  IS_NULL,
  IS_LONG,
  // ...
} z_type;

typedef struct _zval {
  z_type type;
  union {
    // ...
  } value;
} zval;
```



这个示例中的几个部分看起来有点奇怪。为什么`fooval`定义了两个层间接？为什么`sizeof()`用于确定`"foo"`的长度？为什么`&fooval`（求值为`zval***`）被强制转换为`void**`？如果你问过这三个问题，请给自己表个掌。

首先，值得知道的是`HashTable`并不只用于用户空间变量。`HashTable`结构非常通用，它在引擎中到处都是，在某些情况下，想要存储一个非指针值是完全合理的。`HashTable`的桶是固定大小的，因此为了存储任何大小的数据，`HashTable`将分配一块内存来封装要存储的数据。在变量的情况下，存储的是`zval*`，因此`HashTable`存储机制分配了足够容纳指针的内存。`HashTable`的桶使用该新指针来携带`zval*`，你最终在`HashTable`中得到一个`zval**`。在`HashTable`明显可以存储`zval`的情况下，存储`zval*`的原因将在下一章讨论。

当尝试检索该数据时，`HashTable`仅知道它有一个指向某些内容的指针。为了将该指针填充到调用函数的局部存储中，调用函数会自然地对局部指针进行解引用，从而产生一个类型不确定且具有两层间接的变量（例如`void**`）。由于在这种情况下你的“不确定类型”是`zval*`，你就会发现传递给`zend_hash_find()`的类型在编译器看来会有所不同，因为它具有三层间接而不是两层。这里这样做是有意为之的，以便通过在函数调用处添加一个简单的类型转换来消除编译器的警告。

在上一个示例中使用`sizeof()`的目的是为了在变量标签所使用的`"foo"`常量中包含终止符`NULL`。在这里使用`4`效果同样良好；但不建议这样做，因为标签名称的更改可能会影响其长度，而且如果硬编码的长度中包含了要被替换的标签文本，那么找到这些硬编码的地方要容易得多。使用`strlen("foo")+1)`也可以解决这个问题；然而，某些编译器不会对这一步进行优化，导致生成的二进制文件可能会执行一个无意义的字符串长度循环，那还有什么趣呢？

如果`zend_hash_find()`找到了你正在查找的项目，它会将提供的解引用指针填充为在首次请求数据首次添加到`HashTable`时分配的桶指针（bucket pointer）的地址，并返回一个与`SUCCESS`常量匹配的整数值。如果`zend_hash_find()`无法找到数据，它将保持指针不变并返回一个与`FAILURE`常量匹配的整数值。

对于存储在符号表中的用户空间变量，`SUCCESS`或`FAILURE`实际上意味着变量已设置或未设置。

## 数据转换

现在你已经可以从符号表中获取变量了，你可能想对它们进行一些操作。一种直接但痛苦的方法可能是检查变量并根据类型执行特定操作。类似下面的简单`switch`语句可能有效：

```
void display_zval(zval *value)
{
    switch (Z_TYPE_P(value)) {
        case IS_NULL:
            /* NULLs are echoed as nothing */
            break;
        case IS_BOOL:
            if (Z_BVAL_P(value)) {
                php_printf("1");
            }
            break;
        case IS_LONG:
            php_printf("%ld", Z_LVAL_P(value));
            break;
        case IS_DOUBLE:
            php_printf("%f", Z_DVAL_P(value));
            break;
        case IS_STRING:
            PHPWRITE(Z_STRVAL_P(value), Z_STRLEN_P(value));
            break;
        case IS_RESOURCE:
            php_printf("Resource #%ld", Z_RESVAL_P(value));
            break;
        case IS_ARRAY:
            php_printf("Array");
            break;
        case IS_OBJECT:
            php_printf("Object");
            break;
        default:
            /* Should never happen in practice,
             * but it's dangerous to make assumptions
             */
             php_printf("Unknown");
             break;
    }
}
```

是的，`display_zval(zval *value)`稍微有点长，但它展示了处理不同`zval`类型的思路。在实践中，你可能会使用宏或函数来使代码更整洁。

考虑用户空间的`stristr()`函数；为了使用不区分大小写的搜索来查找字符串，它实际上会创建堆栈字符串（haystack）和针头字符串（needle）的小写副本，然后执行更传统的大小敏感搜索以找到相对偏移量。然而，在定位字符串偏移量后，就不再需要这些堆栈和针头字符串的小写版本了。如果释放释放这些副本，那么每个使用`stristr()`的脚本在每次调用时都会泄漏一些内存。最终，Web服务器进程将占用所有系统内存，但无法使用它。

我能听到你们在叫，理想的解决方案是编写良好、整洁、一致的代码，这完全正确。但在像PHP解释器这样的环境中，这只是解决了一部分问题。

## 错误处理

为了提供从活动请求中退出到用户空间脚本及其依赖的扩展函数的能力，需要一种能够完全跳出活动请求的方法。Zend引擎内部处理这种情况的方法是在请求开始时设置一个退出地址（bailout address），然后在任何`die()`或`exit()`调用，或者遇到任何严重错误（`E_ERROR`）时执行`longjmp()`跳转到该退出地址。

尽管这种退出过程简化了程序流，但它几乎总是意味着资源清理代码（如`free()`调用）被跳过，并导致内存泄漏。考虑这段处理函数调用的引擎简化版代码：

```
void call_function(const char *fname, int fname_len TSRMLS_DC)
{
    zend_function *fe;
    char *lcase_fname;

    /* PHP 函数名是不区分大小写的
     * 为了方便在函数表中查找它们
     * 所有函数名都会隐式地
     * 转换为小写
     */
    lcase_fname = estrndup(fname, fname_len);
    zend_str_tolower(lcase_fname, fname_len);

    if (zend_hash_find(EG(function_table),
            lcase_fname, fname_len + 1, (void **)&fe) == FAILURE) {
        zend_execute(fe->op_array TSRMLS_CC);
    } else {
        php_error_docref(NULL TSRMLS_CC, E_ERROR,
                         "Call to undefined function: %s()", fname);
    }
    efree(lcase_fname);
}
```

当遇到`php_error_docref()`行时，内部错误处理器看到错误级别是严重的，并调用`longjmp()`中断当前程序流，导致`call_function()`永远无法到达`efree(lcase_fname)`行。再次，你可能在想`efree()`行可以简单移动到`zend_error()`行之前，但最初调用这个`call_function()`程的代码又该呢？最可能是`fname`本身是一个被分配的字符串，在它被用于错误消息之前，你无法释放它。

#### 注意

`php_error_docref()`函数是`TRigger_error()`的内部等价物。第一个参数是一个可选的文档引用，如果`php.ini`中启用了该功能，则会将其附加到`docref.root`上。第三个参数可以是任何熟悉的`E_*`系列常量之一，表示严重程度。第四个及后续参数遵循`printf()`风格的格式和可变参数列表。

## Zend内存管理器

请求退出期间内存泄漏的解决方案是Zend内存管理（ZendMM）层。引擎的这部分工作方式类似于操作系统的正常行为，为调用应用程序分配内存。区别在于它在进程空间中足够低层，能够感知请求，因此当一个请求结束时，它可以执行操作系统在进程结束时执行的相同操作。也就是说，它隐式地释放了该请求拥有的所有内存。[图 3.1] 显示了ZendMM与操作系统及PHP进程之间的关系。

### 图 3.1. Zend内存管理器替换了每个请求分配的系统调用。

![](img/03fig01.jpg)

除了提供隐式内存清理外，ZendMM还根据`php.ini`设置`memory_limit`控制每个请求的内存使用。如果脚本尝试请求内存超过系统总可用内存，或超过其每个请求限制，ZendMM将自动发出`E_ERROR`并开始退出过程。这样做的一个优点是，大多数内存分配调用的返回值不需要检查，因为失败会导致立即`longjmp()`到引擎的关闭部分。

在PHP内部代码和操作系统实际内存管理层之间实现钩子，只需要求所有内部分配的内存都使用一组替代函数来请求即可。例如，PHP代码将不会使用`malloc(16)`分配16字节的内存块，而是使用`emalloc(16)`。除了执行实际的内存分配任务，ZendMM还会标记该区块关于其所属请求的信息，以便当请求退出时，ZendMM可以隐式地释放它。

通常，内存分配的时间需要超过单个请求的持续。这类分配被称为`persistent`（持久性）分配，因为它们在请求结束后仍然存在，可以使用传统的内存分配器执行，因为这些分配器没有添加ZendMM使用的额外每个请求信息。然而，有时在运行时并不知道特定分配是否是持久的，因此ZendMM导出了一系列辅助宏，这些宏的作用与内存函数相同，但多了一个额外的参数。

如果你确实想要持久性分配，该参数应设置为1，此时将通过`malloc`进行。如果运行时逻辑确定该区块不需要持久性，则该参数可以设置为0，调用将进入请求内存函数。例如，`pemalloc(len, 1)`映射到`malloc()`，而`pemalloc(len, 0)`则通过以下定义映射到`emalloc()`：

```
#define Zend/zend_alloc.h:
#define pemalloc(size, persistent) \
            ((persistent)?malloc(size):emalloc(size))
```

ZendMM中的每个分配函数都列在其传统的传统的等价物下方。表 3.1 显示了ZendMM支持的每个分配函数及其e/pe等价物：

### 表 3.1. 传统分配器与PHP特定分配器

| 分配函数 | e/pe 等价物 |
| --- | --- |
| `void *malloc(size_t count);` | `void *emalloc(size_t count);` <br> `void *pemalloc(size_t count, char persistent);` |
| `void *calloc(size_t count);` | `void *ecalloc(size_t count);` <br> `void *pecalloc(size_t count, char persistent);` |
| `void *realloc(void *ptr, size_t count);` | `void *erealloc(void *ptr, size_t count);` <br> `void *perealloc(void *ptr, size_t count, char persistent);` |
| `void *strdup(void *ptr);` | `void *estrdup(void *ptr);` <br> `void *pestrdup(void *ptr, char persistent);` |
| `void *free(void *ptr);` | `void *efree(void *ptr);` <br> `void *pefree(void *ptr, char persistent);` |

除了核心分配器函数集外，还有几个额外且非常有用的ZendMM特有函数：

```
void *estrndup(void *ptr, int len);
```

分配`len+1`字节的内存，并将`ptr`中的`len`字节拷贝到新分配的块中。`estrndup()`的行为大致如下：

```
void *estrndup(void *ptr, int len)
{
    char *dst = emalloc(len + 1);
    memcpy(dst, ptr, len);
    dst[len] = 0;
    return dst;
}
```

在这里缓冲区末尾隐式放置的终止符`NULL`字节确保了任何使用`estrndup()`进行字符串复制的函数都不需要担心将生成的缓冲区传递给如`printf()`这样期望`NULL`终止字符串的函数。当使用`estrndup()`拷贝非字符串数据时，最后一个字节实际上被浪费了，但大多数情况下，便利性大于这种轻微的效率低下。

```
void *safe_emalloc(size_t size, size_t count, size_t addtl);
void *safe_pemalloc(size_t size, size_t count, size_t addtl, char persistent);
```

这些函数分配的内存数量是`((size * count) + addtl)`的结果。你可能会问：“为什么还要用额外的函数？为什么不直接用`emalloc/pemalloc`并自己计算呢？”原因在于名称中的：`safe`（安全）。尽管导致这种情况的情况极不常见，但此类等式的最终结果可能会溢出主平台的整数限制。这可能导致分配负数字节内存，或者更糟糕，分配一个远小于调用程序认为其请求的的正数字节。`safe_emalloc()`通过检查整数溢出并在发生此类溢出时显式失败来避免这种陷阱。

#### 注意

并不是所有的内存分配程序都有对应的`p*`变。例如，没有`pestrndup()`，且`safe_pemalloc()`在PHP 5.1之前并不存在。你有时需要绕过ZendAPI中的这些空白。

![](img/30011536.html)

### 引用计数

仔细的内存分配和释放对于像PHP这样多请求进程的长期性能至关重要，但这仅是问题的一半。为了让每秒处理数千次访问的服务器高效运行，每个请求需要尽可能少地使用内存并执行最少的不必要的数据拷贝。考虑以下PHP代码段：

```php
<?php
    $a = 'Hello World';
    $b = $a;
    unset($a);
?>
```

在第一次调用后，创建了一个变量，并为其分配了一个12字节的内存块，其中存储了字符串'Hello World'以及一个随后的`NULL`。现在看接下来的两行：`$b`被设置为与`$a`相同的值，然后`$a`被unset（释放）。

如果PHP将每个变量赋值都视为拷贝变量内容的原因，那么复制的字符串将需要额外拷贝12字节，并且在数据拷贝期间会消耗额外的处理器负载。当第三行出现且原始变量被unset时，由于数据复制变得完全没有必要，这种行为开始显得很荒谬。再进一步，想象一下当一个10MB文件的内容加载到两个变量中时会发生什么。这可能会占用20MB的空间，而10MB就足够了。引擎会在这项无意义的事情上浪费这么多时间和内存吗？

你知道PHP比这更聪明。

记住，变量名和它们的值在引擎内部实际上是两个不同的概念。值本身是一个无名的`zval*`，在本例中它持有一个字符串值。它是使用`zend_hash_add()`被赋值给变量`$a`的。如果两个变量名指向同一个值呢？

```
{
    zval *helloval;
    MAKE_STD_ZVAL(helloval);
    ZVAL_STRING(helloval, "Hello World", 1);
    zend_hash_add(EG(active_symbol_table), "a", sizeof("a"),
                                           &helloval, sizeof(zval*), NULL);
    zend_hash_add(EG(active_symbol_table), "b", sizeof("b"),
                                           &helloval, sizeof(zval*), NULL);
}
```



此时，你实际上可以检查`$a`或`$b`，发现它们都包含字符串`"Hello World"`。不幸的是，你接着遇到了第三行：`unset($a);`。在这种情况下，`unset()`并不知道`$a`变量指向的数据也被另一个变量使用，因此它只是盲目地释放了内存。对`$b`的任何后续访问将指向已释放的内存空间并导致引擎崩溃。提示：你不希望引擎崩溃。

这通过`zval`四个成员中的第三个解决了：`refcount`（引用计数）。当一个变量首次创建并设置时，它的`refcount`被初始化为 1，因为假设它只被创建它的变量使用。当你的代码段执行将`helloval`赋值给`$b`时，它需要将该`refcount`增加到 2，因为该值现在被两个变量“引用”了：

```
{
    zval *helloval;
    MAKE_STD_ZVAL(helloval);
    ZVAL_STRING(helloval, "Hello World", 1);
    zend_hash_add(EG(active_symbol_table), "a", sizeof("a"),
                                           &helloval, sizeof(zval*), NULL);
    zend_hash_add(EG(active_symbol_table), "b", sizeof("b"),
                                           &helloval, sizeof(zval*), NULL);
}
```

### 写时拷贝 (Copy on Write)

通过引用计数节省内存是一个好主意，但当你只想改变其中一个变量时会发生什么？

如果 PHP 将每个变量赋值都视为拷贝变量的内容，那么复制的字符串将需要额外拷贝 12 字节，并且在数据拷贝期间会消耗额外的处理器负载。当第三行出现且原始变量被`unset`时，由于数据复制变得完全没有必要，这种行为开始显得很荒谬。再进一步，想象一下当一个 10MB 文件的内容加载到两个变量中会发生什么。这可能会占用 20MB 的空间，而 10MB 就足够了。

考虑以下 PHP 代码段：

```php
<?php
    $a = 'Hello World';
    $b = $a;
    unset($a);
?>
```

### 分离逻辑 (Separation Logic)

记住，变量名和它们的值在引擎内部实际上是两个不同的概念。值本身是一个无名的`zval*`，在本例中它持有一个字符串值。它是使用`zend_hash_add()`被赋值给变量`$a`的。如果两个变量名指向同一个值呢？

```
{
    zval *helloval;
    MAKE_STD_ZVAL(helloval);
    ZVAL_STRING(helloval, "Hello World", 1);
    zend_hash_add(EG(active_symbol_table), "a", sizeof("a"),
                                           &helloval, sizeof(zval*), NULL);
    zend_hash_add(EG(active_symbol_table), "b", sizeof("b"),
                                           &helloval, sizeof(zval*), NULL);
}
```

此时，你实际上可以检查`$a`或`$b`，发现它们都包含字符串`"Hello World"`。不幸的是，你接着遇到了第三行：`unset($a);`。在这种情况下，`unset()`并不知道`$a`变量指向的数据也被另一个变量使用，因此它只是盲目地释放了内存。对`$b`的任何后续访问将指向已释放的内存空间并导致引擎崩溃。提示：你不希望引擎崩溃。

Zend 引擎中的分离（Separation）是销毁引用的过程，与你刚刚看到的过程相反：

```
zval *get_var_and_separate(char *varname, int varname_len TSRMLS_DC)
{
    zval **varval, *varcopy;
    if (zend_hash_find(EG(active_symbol_table),
                       varname, varname_len + 1, (void**)&varval) == FAILURE) {
       /* 变量实际上不存在，失败 */
       return NULL;
   }
   if ((*varval)->refcount < 2) {
       /* varname 是唯一的引用，
        * 不需要分离
        */
       return *varval;
   }
   /* 否则，拷贝一个 zval* */
   MAKE_STD_ZVAL(varcopy);
   varcopy = *varval;
   /* 复制 zval* 内部任何分配的结构 */
   zval_copy_ctor(varcopy);
   /* 移除旧的 varname
    * 这将减少 varval 的引用计数
    */
   zend_hash_del(EG(active_symbol_table), varname, varname_len + 1);
   /* 初始化新值的引用计数
    * 并将其附加到 varname 变量
    */
   varcopy->refcount = 1;
   varcopy->is_ref = 0;
   zend_hash_add(EG(active_symbol_table), varname, varname_len + 1,
                                               &varcopy, sizeof(zval*), NULL);
   /* 返回新的 zval* */
   return varcopy;
}
```

引用计数的概念也为数据操作创建了新的可能性，其形式正如用户空间脚本编写者实际所理解的“引用”那样。考虑以下这段用户空间代码段：

```php
<?php
    $a = 1;
    $b = &$a;
    $b += 5;
?>
```

由于熟悉 PHP 代码的方式，你会直觉地察觉到`$a`的值现在是 6，尽管它被初始化为 1 且从未被（直接）改变过。发生这种情况是因为当引擎尝试将`$b`的值加 5 时，它注意到`$b`是`$a`的引用，并说：“对我来说，在不分离的情况下改变值是可以的，因为我希望所有引用变量都能看到这个变化。”

但引擎是如何知道的呢？很简单，它查看了`zval`结构体的第四个也是最后一个元素：`is_ref`。这只是一个简单的开启/关闭位值，用于定义该值实际上是否为用户空间风格引用集的一部分。在之前的代码段中，当执行第一行时，为`$a`创建的值获得了一个引用计数（`refcount`）为 1，且`is_ref`值为 0，因为它只被一个变量（`$a`）拥有，没有其他变量对其有写时复制引用。在第二行，该值的引用计数元素像以前一样增加到 2，但由于这次脚本包含了`&`符号来表示全引用，`is_ref`元素被设置为 1。

最后，在第三行，引擎再次获取与`$b`关联的值并检查是否有必要分离。这次该值没有被分离，是因为缺少了一个之前没有包含的检查。这里再次是`get_var_and_separate()`中的引用计数检查部分，增加了一个额外条件：

```
if ((*varval)->is_ref || (*varval)->refcount < 2) {
    /* varname 是唯一的实际引用，
     * 或者它是对其他变量的全引用
     * 无论如何：都不需要进行分离
     */
    return *varval;
}
```

这一次，尽管引用计数为 2，但由于该值是一个全引用这一事实，分离过程被短路了。引擎可以自由地修改它，而不必担心其他变量的值看起来神奇地自动发生了变化。

### 分离焦虑（Separation Anxiety）

有了所有这些复制和引用，有些事件组合是无法通过对`is_ref`和`refcount`的巧妙操作来的。考虑此块 PHP 代码：

```php
<?php
    $a = 1;
    $b = $a;
    $c = &$a;
?>
```

在这里你有一个需要与三个不同变量关联的单一值，两个在一个写时复制的全引用对中，第三个处于一个可分离的写时复制上下文中。仅使用`is_ref`和`refcount`来描述这种关系，什么值会有效？

答案是：全无效。在这种情况下，该值必须复制到两个离散的`zval*`中，尽管两者都包含完全相同的数据（参见图 3.2）。

#### 图 3.2. 引用时的强制分离。

![](img/03fig02.jpg)

同样，接下来的代码块将导致相同的冲突，并迫使该值分离为一个副本（参见图 3.3）。

#### 图 3.3. 复制时的强制分离。

![](img/03fig03.jpg)

```php
<?php
    $a = 1;
    $b = &$a;
    $c = $a;
?>
```



注意，在这里两种情况下，`$b` 都与原始 zval 对象关联，因为在分离发生时，引擎不知道操作中涉及的第三个变量的。

![](img/30011536.html)

### 总结

PHP 是一种托管语言。在用户空间方面，这种对资源和内存的细致控制意味着更容易原型设计和更少的崩溃。然而，当你深入底层后，一切规则失效，需要负责任的开发者来维护运行时环境的完整性。

## 第 4 章：搭建构建环境

到此时，你可能已经在至少一个系统上安装了 PHP 版本，并一直在使用它开发 Web 应用程序。你可能从 `php.net` 下载了 Win32 构建版本以便在 Windows 的 IIS 或 Apache 上运行，或者使用了你的 *nix 发行版（Linux、BSD 或其他符合 POSIX 标准的发行版）软件包系统来安装第三方创建的二进制文件。

### 编译 PHP

然而，除非你从 `php.net` 下载了 tar 包源码并自行编译，否则你很可能缺少至少一个组件。

#### *nix 工具

任何 C 开发者工具箱中的第一件设备都是真正的 C 编译器。极有可能是你的发行版默认就包含了一个，而且极有可能是它包含了 `gcc`（GNU 编译器编译集）。你可以通过执行 `gcc version` 或 `cc version` 轻松检查是否安装了编译器，其中任何一个希望都能成功运行并返回已安装编译器的版本信息。

如果你还没有编译器，请检查你发行版的网站查看关于下载和安装 `gcc` 的说明。通常情况下，你需要根据发行版下载并安装 `gcc`。取决于你的具体的发行版，以下命令可能有效：`rpm`、`apt-get`、`pkg-add` 或 `emerge`。

除了编译器，你还需要以下程序和工具：`make`、`autoconf`、`automake` 和 `libtool`。这些工具可以使用你安装 `gcc` 的相同方法进行安装，或者从 `gnu.org` 下载源码编译。

为了获得最佳结果，推荐使用 `libtool` 1.4 版本、`autoconf` 2.13 以及 `automake` 1.4 或 1.5 版本。使用更新版本的软件包可能也可以，但只有这些版本经过了验证。

如果你计划使用 CVS 获取最新的 PHP 版本，你还需要 `bison` 和 `flex` 来构建语言解析器。与其他软件包一样，这些可以通过你的发行版系统安装，或者从 `gnu.org` 下载并编译。

如果你选择 CVS 路线，你还需要 `cvs` 客户端本身。同样，这可以通过发行版安装，或者下载。与其他软件包不同，它位于 `cvshome.org`。

#### Win32 工具

Win32/PHP5 构建系统是一个完全重写，代表了相对于 PHP4 构建系统的飞跃。在 Windows 下编译 PHP4 的说明可以在 `php.net` 上找到，这里仅讨论 Windows 2000、Windows 2003 或 Windows XP。

首先，你需要获取许多核心扩展扩展使用的库和开发头文件。幸运的是，许多这些文件通过 `php.net` 重新发布为一个单一的 `.zip` 文件，位于 [`www.php.net/extra/win32build.zip`](http://www.php.net/extra/win32build.zip)。

创建一个名为 `C:\PHPDEV\` 的新目录，并使用你喜欢的压缩管理程序将 `win32build.zip` 解压到此处。zip 文件包含的文件夹结构将创建一个子目录 `C:\PHPDEV\win32build`，它将包含更多的子文件夹和文件。你的根目录不需要命名为 `PHPDEV`；唯一重要的是 win32build 和 PHP 源码树都是同一个父目录的子。

接下来，你需要一个编译器。如果你已经有了 Visual C++ .NET，你就有了所需要的；否则，请从微软下载 Visual C++ Express。

一旦下载并运行安装程序，它将显示常规欢迎界面、EULA（最终用户许可协议）和标识对话框。仔细阅读这些屏幕，并在同意 EULA 条款并输入任何适当信息后，使用“Next（下一步）”按钮继续。

安装位置显然由你决定，典型的安装完全可以正常工作。如果你想创建一个更精简的安装，可以取消勾选三个可选组件 `GUI`、`MSDN` 和 `SQL Server`。

最终的包是 Platform SDK，也可以从微软下载：[`www.microsoft.com/downloads/details.aspx?FamilyId=A55B43-E24F-EA3-93E-40EC4F685`](http://www.microsoft.com/downloads/details.aspx?FamilyId=A55B43-E24F-EA3-93E-40EC4F685)。该网站目前列出了三个下载选项：`PSDK-x86.exe`、`PSDK-ia64.exe` 和 `PSDK-amd64.exe`。这些选项分别指适用于 x86 32 位、Intel 64 位和 AMD 64 位的处理器。如果你不确定哪一个适用于你的处理器，请选择 `PSDK-x86.exe`，它应该可以工作，尽管效率不如 64 位版本。

在此之前，像使用其他安装程序一样继续前几个屏幕，直到提示选择“Typical（典型）”或“Custom（自定义）”安装。典型安装包含 Core 包，对于构建 PHP 来说足够了。通过选择自定义安装可以取消其他包，但如果你有剩余的磁盘空间，也可以全部安装。其他包以后可能会派用场。除非你对空间敏感，否则选择 Typical 并继续后续屏幕，直到安装程序开始复制文件。这个过程应该只需要几分钟即可。

一旦安装完成，你将在开始菜单中看到一个新项目：Windows Server 2003 SP1 Platform SDK。

### 获取 PHP 源码

下载 PHP 时你有几种选择。首先，如果你的发行版支持，可以使用如 `apt-get source php` 命令从那里下载。这种方法的好处是你的发行版可能包含某些需要修改源码的已知缺陷，通过从那里下载可以确保你的构建已经修复了这些缺陷。缺点是大多数发行版比官方发布落后几甚至几个月，导致你下载的版本在到达硬盘之前就已经过时了。

通常首选的选项是从 [www.php.net](http://www.php.net) 下载 `php-x.y.z.tar.gz`（其中 `x.y.z` 是当前发布的版本）。此版本的 PHP 已经过全球无数 PHP 用户的测试，处于非常前沿的状态。

你还可以进一步，从 `snaps.php.net` 下载快照（tarball）。在该网站上，PHP 仓库中所有源码文件每几小时打包一次。核心开发人员意外提交可能会导致这些程序包偶尔失效，但如果你在官方发布之前就需要最新的 PHP 功能，这里是更容易查找的地方。

最后，你可以使用 CVS 直接从 PHP 核心团队使用的开发仓库获取 PHP 源码树中的文件。对于扩展和嵌入开发，这比使用官方发布包或快照没有显著优势。但如果你计划在 CVS 仓库中发布你的扩展或其他应用程序，熟悉 checkout 将会有帮助。

### 执行 CVS Checkout

整个 PHP 项目（从 Zend Engine 和核心到最小的 PEAR 组件）都托管在 `cvs.php.net`。从这里，数百名开发者开发并维护构成 PHP 整体的各个部分。

在此处的其他部分中，核心 PHP 包位于 `php-src` 模块中，可以使用两个简单的命令将其下载到工作站。首先，你需要通过登录向 `php.net` CVS 服务器进行身份验证。

```
$ cvs -d:pserver:cvsread@cvs.php.net:/repository login
```

`cvsread` 账户是一个公共（只读）账户，密码为 `phpfi`，这是对我们所知的 PHP 的更早版本的致敬。登录后，可以使用以下命令检 PHP 源码：

```
$ cvs -d:pserver:cvsread@cvs.php.net:/repository co php-src
```

此命令的变体可以检追溯到 PHP2 的特定 PHP 版本。更多信息，请参阅 [`www.php.net/anoncvs`](http://www.php.net/anoncvs) 中的匿名 CVS 指南。

### 为开发配置 PHP

如 第 1 章 所示，在构建易于开发的 PHP 时，无论你计划为 PHP 编写扩展还是将 PHP 嵌入另一个应用程序，你都会想要使用两个特殊的 `./configure` 开关。这两个开关应配合构建 PHP 时通常使用的其他开关。

#### `enable-debug`

`enable-debug` 开关开启几个关键函数。回想 第 3 章“内存管理”，内存管理器会隐式释放已分配的请求内存。看下面的代码段：

```
void show_value(int n)
{
    char *message = emalloc(1024);
    sprintf(message, "The value of n is %d\n", n);
    php_printf("%s", message);
}
```

如果这段诚然愚蠢的代码在请求过程中执行，它将泄露 1024 字节。在通常情况下，ZendMM 会结束时静地释放该块内存而不会报错。

但在开启 `enable-debug` 的情况下，开发者会看到：

```
/php5/ext/sample/sample.c(33) :  Freeing 0x084504B8 (1024 bytes), script=-
=== Total 1 memory leaks detected ===
```

这条简短但有效的信息告诉你是 ZendMM 必须清理你的烂摊，并指出了丢失内存块分配的确切位置。使用这些信息，打开文件并滚动到相关行并在函数末尾添加适当的 `efree(message)` 调用是非常简单的。

内存泄漏并不是你遇到的难以追踪的唯一问题。有时问题更加隐蔽，且信息更少。假设你通宵宵开发了一个大补丁，涉及十几个文件并修改了大量代码。当一切准备就绪后，你自信地执行 `make`，尝试运行脚本，结果得到了如下输出：

```
$ sapi/cli/php -r 'myext_samplefunc();'
Segmentation Fault
```

哎……这真糟糕，但问题可能在哪里呢？查看你 `myext_samplefunc()` 的实现没有发现明显的线索，通过 gdb 运行只显示出一堆未知符号。

再次，`enable-debug` 提供了帮助。通过在 `./configure` 中添加此开关，生成的 PHP 二进制文件将包含 gdb 或另一个核心检查程序显示问题发生位置所需的所有调试符号。

使用此选项重新构建，并通过 gdb 触发崩溃，你现在可以看到类似如下的内容：

```
#0 0x1234567 php_myext_find_delimiter(str=0x1234567 "foo@#(FHVN)@\x98\xE0...",
                                      strlen=3, tsrm_ls=0x1234567)
    p = strchr(str, ',');
```

原因现在显而易见了。`str` 字符串并不是以 NULL 结尾的字符串（末尾的垃圾数据证明了这一点），而是由于其上使用了一个非二进制安全的函数。底层的 `strchr()` 实现尝试扫描 `str` 分配内存的末尾之外，并进入了它不拥有的内存区域，导致了段错误（segfault）。使用 `memchr()` 和 `strlen` 参数进行快速替换可以防止崩溃。

#### `enable-maintainer-zts`

这第二个 `./configure` 选项强制 PHP 在启用线程安全资源管理器（Thread Safe Resource Manager, TSRM）/ Zend 线程安全（ZTS）层的情况下进行构建。在不需要的情况下，此开关会增加复杂性和处理时间，但从开发的角度来看，你会发现这是一件好事。关于 ZTS 是什么以及为什么你想在开启它的情况下进行开发，请参考第 1 章。

#### `enable-embed`

最后一个重要的 `./configure` 开关只有在你将将 PHP 嵌入另一个应用程序时 是必要的。此选项标识了 `libphp5.so` 应该被构建为选定的 SAPI，就像 `with-apxs` 将构建 `mod_php5.so` 以专门将 PHP 嵌入 Apache 中一样。

### 在 UNIX 上编译

现在你已经集齐了所有必要的工具，下载了 PHP 源码 tar 包，并确定了所有必要的 `./configure` 选项，现在是时候编译 PHP 了。

假设你已经将 `php-5.1.0.tar.gz` 下载到了家目录下，你将输入以下系列命令来解压 tar 包并切换到 PHP 源码目录：

```
[/home/sarag]$ tar -zxf php-5.1.0.tar.gz
[/home/sarag]$ cd php-5.1.0
```

如果你使用的是 GNU tar 以外的工具，可能需要使用略有不同的命令：

```
[/home/sarag]$ gzip -d php-5.1.0.tar.gz | tar -xf -
```

现在，带有所需的选项以及任何你想要启用或禁用的选项执行 `./configure` 命令：

```
[/home/sarag/php-5.1.0]$ ./configure enable-debug \
enable-maintainer-zts disable-cgi enable-cli \
disable-pear disable-xml disable-sqlite \
without-mysql enable-embed
```

在经过漫长的过程中，会有几十行信息文本在你的屏幕上滚动，之后你就可以准备好开始编译过程了：

```
[/home/sarag]$ make all install
```

此时，站起来去喝杯咖啡吧。编译时间范围从高端强力系统上的几分钟，到老旧且过载的 486 机器上的半小时不等。当构建过程完成后，你将获得一个带有所有正确配置并供使用的 PHP 功能构建版本。

### 在 Win32 上编译

与 UNIX 构建一样，准备 Windows 构建的第一步是解压源码 tar 包。默认情况下，Windows 并知道如何处理 `.tar.gz` 文件。事实上，如果你使用 Internet Explorer 下载了 PHP，你可能注意到它将 tar 包的名称更改为了 `php-5.1.0.tar`。这不是一个 bug，而是一个特性。首先将文件名重命名回 `php-5.1.0.tar.gz`（如有必要）。如果你安装了可以读取 `.tar.gz` 文件的程序，你会发现图标发生了变化。你现在可以双击文件来打开解压缩程序。如果图标没有变化，或者双击图标时没有任何反应，说明你没有兼容 tar/gzip 的程序。请检查你常用的搜索引擎以查找 WinZIP、WinRAR 或任何其他适用于提取 `.tar.gz` 存档的应用程序。

无论你使用哪种解压程序，请将其将 `php-5.1.0.tar.gz` 解压到你之前创建的根文件夹。本节假设你已将其解压到 `C:\PHPDEV\`，这将导致源码树位于 `C:\PHPDEV\php.1.0`。

解压后，通过选择开始 -> 所有程序 -> Microsoft Platform SDK for Windows 2003 -> Open Build Environment -> Windows 2000 Build Environment -> Set Windows 2000 Build Environment (Debug) 来打开构建环境。具体路径可能会取决于你安装的 Platform SDK 版本以及你将要构建的目标平台（2000, XP, 2003）。将打开一个简单的命令行窗口并显示目标平台。此命令行提示符已设置了大部分（并非全部）必要的环境。你需要运行一个额外的批处理文件，让 PHP 构建系统知道 Visual++ 的位置。如果你接受了默认安装位置，该批处理文件位于 `C:\Program Files\Microsoft Visual Studio 8\VC\bin\vcvars32.bat`。如果找不到 `vcvars32.bat`，请检查同一目录或其父目录下的 `vcvarsall.bat`。

现在，进入你解压 PHP 的目录并运行 `buildconf.bat`。

```
C:\Program Files\Microsoft Platform SDK> cd \PHPDEV\1.0
C:\PHPDEV\1.0> buildconf.bat
```

如果一切顺利，你将看到以下两行输出：

```
Rebuilding configure.js
Now run 'cscript /nologo configure.js help'
```

此时，你可以按照所示查看可用选项。`enable-maintainer-zts` 选项在这里是不必要的，因为 Win32 构建会自动假设需要 ZTS。如果你想关闭它，可以使用 `disable-zts`，但由于你是在开发环境中构建，所以没关系。为了简单起见，我在示例中移除了一些与扩展无关的其他扩展。如果你想使用额外的扩展重新构建 PHP，你需要找到它们依赖的库。

```
C:\PHPDEV\1.0> cscript /nologo configure.js without-xml without-wdx \
without-simplexml without-dom without-libxml disable-zlib \
without-sqlite disable-odbc disable-cgi enable-cli \
enable-debug without-iconv
```

再次，会有信息流滚动，最后是执行最终命令的指令：

```
C:\PHPDEV\1.0> nmake
```



最后，一个为 Win32 平台编译的 PHP。

### 总结

现在 PHP 已经按照正确的选项安装完成，你准备好开始创建一个真正的扩展了。在接下来的章节中，你将介绍 PHP 扩展的结构。即使你只计划将 PHP 嵌入到应用程序而不进行任何语言扩展，你也应该阅读这一节，因为它详细解释了与 PHP 环境交互的机制。

![](img/30011536.html)

## 第 5 章 你的第一个扩展

每个 PHP 扩展至少由两个文件构建：配置文件（告诉编译器构建哪些文件以及需要哪些外部库）以及一个源文件（执行实际工作）。

### 扩展的结构

在实践中，通常会有第二个或第三个配置文件以及一个或多个头文件。对于你的第一个扩展，你将处理这些类型文件的每一种并在此基础上进行。

#### 配置文件

首先，在你的 PHP 源码树的 `ext/` 目录下创建一个名为 `sample` 的目录。

接下来，进入该目录并创建一个名为 `config.m4` 的文件，内容如下：

```
PHP_ARG_ENABLE(sample,

  [Whether to enable the "sample" extension],

  [  enable-sample        Enable "sample" extension support])

if test $PHP_SAMPLE != "no"; then

  PHP_SUBST(SAMPLE_SHARED_LIBADD)

  PHP_NEW_EXTENSION(sample, sample.c, $ext_shared)

fi
```

这个极简配置设置了一个名为 `enable-sample` 的 `./configure` 选项。`PHP_ARG_ENABLE` 的第二个参数将在 `./configure` 过程到达该扩展的配置文件时显示。如果最终用户执行 `./configurehelp`，第三个参数将作为可用选项显示。

### 注意事项

你是否曾想过，为什么某些扩展使用 `enable-extname` 配置，而另一些扩展则使用 `with-extname` 配置？从功能上讲，两者没有区别。但在实践中，`enable` 用于那些不需要任何第三方库即可开启的功能。相比之下，`with` 用于确实具有此类前提条件的功能。

目前，你的示例扩展不需要链接其他库，因此你将使用 `enable` 版本。第 17 章“外部库”将介绍如何使用 `with` 并指示编译器使用额外的 `CFLAGS` 和 `LDFLAGS` 设置。

如果最终用户使用 `enable-sample` 选项调用 `./configure`，那么本地环境变量 `$PHP_SAMPLE` 将被设置为 `yes`。`PHP_SUBST()` 是经过 PHP 修改的标准 autoconf `AC_SUBST()` 宏，它对于将扩展构建为共享模块是必要的。

最后但同样重要的是，`PHP_NEW_EXTENSION()` 声明了模块并列出了所有必须作为扩展部分编译的源文件。如果需要多个文件，它们将在第二个参数中使用空格作为分隔符列出，例如：

```
PHP_NEW_EXTENSION(sample, sample.c sample2.c sample3.c, $ext_shared)
```

最后一个参数是 `PHP_SUBST(SAMPLE_SHARED_LIBADD)` 命令的对应项，同样对于构建为共享模块是必要的。

### 头文件 (Header)

在 C 语言开发时，将某些类型的数据分离到外部头文件中并由源文件包含这些头文件通常是有意义的。虽然 PHP 不要求这样做，但当模块规模超过单个源文件的范围时，这会增加其简单性。

你将在新的头文件（名为 `php_sample.h`）中开始包含以下内容：

```
#ifndef PHP_SAMPLE_H

/* 防止重复包含 */

#define PHP_SAMPLE_H

/* 定义扩展属性 */

#define PHP_SAMPLE_EXTNAME    "sample"

#define PHP_SAMPLE_EXTVER    "1.0"

/* 在 PHP 源码树外部

   构建时导入配置 

   选项 */

#ifdef HAVE_CONFIG_H

#include "config.h"

#endif

/* 包含 PHP 标准头文件 */

#include "php.h"

/* 定义入口点符号

 * Zend 在加载此模块时将使用它

 */

extern zend_module_entry sample_module_entry;

#define phpext_sample_ptr &sample_module_entry

#endif /* PHP_SAMPLE_H */
```

此头文件完成了两个主要任务：如果扩展是使用 `phpize` 工具构建的（这是你通过本书大部分内容构建扩展的方式），那么 `HAVE_CONFIG_H` 将被定义，`config.h` 也将被包含。无论如何编译扩展，它还包含了来自 PHP 源码树的 `php.h`。该头文件随后包含了分布在 PHP 源码中的其他头文件，提供了对 PHPAPI 大部分的访问。

接下来，扩展扩展使用的 `zend_module_entry` 结构体被声明为外部，这样当使用 `extension=` 行加载此模块时，Zend 就能通过 `dlopen()` 和 `dlsym()` 获取它。

该头文件还包含了几个预处理器定义，这些定义稍后将在源文件中中使用。

### 源文件 (Source)

最后，也绝非最后，你将在 `sample.c` 文件创建一个简单的源文件骨架：

```
#include "php_sample.h"

zend_module_entry sample_module_entry = {

#if ZEND_MODULE_API_NO >= 20010901

     STANDARD_MODULE_HEADER,

#endif

    PHP_SAMPLE_EXTNAME,

    NULL, /* Functions */

    NULL, /* MINIT */

    NULL, /* MSHUTDOWN */

    NULL, /* RINIT */

    NULL, /* RSHUTDOWN */

    NULL, /* MINFO */

#if ZEND_MODULE_API_NO >= 20010901

    PHP_SAMPLE_EXTVER,

#endif

    STANDARD_MODULE_PROPERTIES

};

#ifdef COMPILE_DL_SAMPLE

ZEND_GET_MODULE(sample)

#endif
```

就这样！这三个文件就是创建模块骨架所需的所有内容。诚然，它没有做任何实用的事情，但这是一个起点，你将在本节的剩余部分添加功能。首先，让我们看看发生了什么。

第一行很简单：包含你刚刚创建的头文件，并因此包含了源码树中的所有其他 PHP 核心头文件。

接下来，创建你在头文件中声明的 `zend_module_entry` 结构体。你会注意到模块条目的第一个元素是根据当前的 `ZEND_MODULE_API_NO` 定义条件判断的。这个 API 数字约同于 PHP 4.2.0，所以如果你确定你的扩展永远不会在早于此版本的任何版本上构建，你可以完全舍弃 `#ifdef` 行，直接包含 `STANDARD_MODULE_HEADER` 元素。

然而，请考虑这在编译时间上的成本非常小。该结构中的其他六个元素目前都设置为 `NULL`；你可以从旁边的注释中看到它们最终的用途。

最后，在结构末尾，你会发现一个每个 PHP 扩展共有的短元素，它在你的扩展作为模块加载时被 Zend 使用。

### 构建你的第一个扩展

现在你已经准备好了所有文件，是时候让它运行了。和构建主二进制一样，不同的步骤取决于你是为 \*ix 还是 Windows 编译。

#### 在 \*ix 下构建

第一步是 `config.m4` 中的信息生成 `./configure` 脚本。这可以通过运行编译主二进制时安装的 `phpize` 程序来实现。

```
$ phpize

PHP Api Version: 20041225

Zend Module Api No: 20050617

Zend Extension Api No: 22050617
```

注意 `Zend Extension Api No` 开头的额外的 2 并不是错误，它对应于 Zend Engine 2 版本，旨在保持此 API 数字大于其 ZE1 对应版本。

现在查看当前目录，你会发现文件比几刻前多得多。`phpize` 程序结合了你扩展中 `config.m4` 的信息以及从 PHP 构建中收集的数据，列出了进行编译所需的所有部分。这意味着你不需要为 Makefile 和定位编译时所需的 PHP 头文件而苦恼。PHP 已经为你完成了这项工作。

下一步是任何其他 OSS 软件包都可能执行的简单 `./configure`。你在这里不是配置整个 PHP 束，而是你的这一个扩展，所以你只需要输入：

```
$ ./configure enable-sample
```

注意这里甚至没有使用 `enable-debug` 和 `enable-maintainer-zts`。这是因为 `phpize` 已经从主 PHP 构建获取了这些值并将其应用于你扩展的 `./configure` 脚本中。

现在构建它！像任何其他软件包一样，你只需输入 `make`，生成的脚本文件将处理剩余工作。

当构建过程完成后，你将看到一条消息，说明 `sample.so` 已编译并放置在当前构建目录下名为 `modules` 的目录中。

## 在 Windows 下构建

你之前创建的 `config.m4` 文件实际上是针对 *nix 构建的。为了让你的扩展能够在 Windows 下编译，你需要为它创建一个独立的、但内容相相似的配置文件。

在你的 `ext/sample` 目录中添加包含以下内容的 `config.w32` 文件：

```
ARG_ENABLE("sample", "enable sample extension", "no");

if (PHP_SAMPLE != "no") {

    EXTENSION("sample", "sample.c");

}
```

如你所见，此文件在高级别与 `config.m4` 相似。该选项被声明、测试并根据条件使用以启用你扩展的构建。

现在，你将重复在构建 PHP 核心时在第 4 章“设置构建环境”中执行的几个步骤。首先，从开始菜单打开构建窗口：选择“所有程序”、“Microsoft Platform SDK for Windows Server 2003 SP1”、“打开构建环境窗口”、“Windows 2000 构建环境”、“设置 Windows 2000 构建环境（调试）”，并运行 `C:\Program Files\Microsoft Visual Studio 8\VC\bin\vcvars32.bat` 批处理文件。

记住，你的安装可能需要你选择不同的构建目标或运行略有不同的批文件。请参阅第 4 章相应章节中的注释以唤起记忆。

再次，你需要进入构建目录的根目录并重新生成配置脚本。

```
C:\Program Files\Microsoft Platform SDK> cd \PHPDEV\php-5.1.0

C:\PHPDEV\php-5.1.0> buildconf.bat

Rebuilding configure.js

Now run 'cscript /nologo configure.js help'
```

这一次，你使用一组简化的选项来运行配置脚本。因为你只关注你自己的扩展而不是整个 PHP，你可以忽略掉与其它扩展相关的选项；但是，与 Unix 构建不同，尽管核心构建已经包含了该选项，你仍然需要显式包含 `enable-debug` 开关。

除了调试外，你在这里需要的唯一关键开关是 `enable-sample=shared`。此处需要 `shared` 选项是因为 `configure.js` 并不知道你计划将 `sample` 编译为可加载的扩展。因此，你的配置行看起来应该像这样：

```
C:\PHPDEV\php-5.1.0> cscript /nologo configure.js \

enable-debug enable-sample=shared
```

### 注意事项

记住，这里不需要 `enable-maintainer-zts`，因为所有 Win32 构建都假设必须启用 ZTS。与 SAPI 相关的选项（如 `embed`）在这里也是不需要的，因为 SAPI 层与扩展层是相互独立的。

最后，你已经准备好构建扩展了。由于这次构建是基于核心的（与 Unix 扩展构建的基于扩展本身不同），你需要在构建命令行中指定目标名称。

```
C:\PHPDEV\php-5.1.0> nmake php_sample.dll
```

一旦编译完成，你应该就有一个可以在下一步使用的可用 `php_sample.dll` 二进制文件了。记住，由于本书关注 *nix 开发，在随后的所有文本中，扩展将被称为 `sample.so` 而不是 `php_sample.dll`。

## 加载作为共享模块构建的扩展

为了让 PHP 在请求时定位此模块，它需要位于你 `php.ini` 设置中指定的相同目录下：`extension_dir`（默认情况下通常是 `/usr/lib/php/modules`）。编辑你的 `php.ini` 并添加以下行：

```
extension=sample
```

现在，你可以运行一个脚本来检查扩展是否已加载：

```php
<?php

phpinfo();

?>
```

如果输出中显示了 `sample` 模块，说明扩展已成功加载。如果没有显示，请检查 `php.ini` 配置和 `extension_dir` 路径是否正确。

另一种方法是在 PHP 脚本中使用 `dl()` 函数来加载扩展：

```php
<?php

dl("sample.so");

sample_hello_world();

?>
```

注意：`dl()` 函数在安全模式（`safe_mode`）下不可用。请确保 `php.ini` 中的 `safe_mode` 设置为 `Off`。

现在，你已经成功构建并加载了你的扩展。

## 静态构建

在加载的模块列表中，你可能注意到通过 `php.ini` 中的扩展指令包含了许多模块。这些模块被直接构建到 PHP 中，并作为主构建的一部分进行编译。

#### 在 *nix 下静态构建

此时，如果你尝试向上几个目录到达 PHP 根目录，运行 `./configure` 会发现虽然生成了脚本，但你的扩展未知。要重新生成 `./configure` 并让它定位新扩展，你只需执行一个命令：

```
$ ./buildconf
```

### 注意事项

如果你使用的是发行版 PHP 进行开发，你会发现单独运行 `./buildconf` 是无效的。在这种情况下，你需要运行 `./buildconf force` 来绕过内置的 `./configure` 命令。

现在你可以运行 `./configure help` 查看 `enable-sample` 是一个可用选项。从这里开始，你可以使用主构建时使用的所有选项加上 `enable-sample` 重新运行 `./configure`，创建一个包含完整解释器和你自定义扩展的二进制文件。

#### 在 Windows 下静态构建

为 Windows 重新生成 `configure.js` 脚本的模式与为 *nix 重新生成 `./configure` 相同。进入 PHP 源码树根并在第 4 章中所做的重新运行 `buildconf.bat`。

PHP 构建系统将扫描 `config.w32` 文件（包括你刚刚为 `ext/sample` 创建的那个），并生成一个新的 `configure.js` 脚本，用于构建静态 php。

### 功能函数

用户空间与扩展代码之间最快的链接是 `PHP_FUNCTION()`。首先在 `sample.c` 文件的顶部靠近 `#include "php_sample.h"` 的地方添加以下代码块：

```
PHP_FUNCTION(sample_hello_world)

{

    php_printf("Hello World!\n");

}
```

`PHP_FUNCTION()` 宏的作用方式就像普通的 C 函数声明一样，因为它的展开方式确实如此：

```php
#define PHP_FUNCTION(name) \

    void zif_##name(INTERNAL_FUNCTION_PARAMETERS)
```

在这种情况下，它会被展开为：

```php
void zif_sample_hello_world(zval *return_value,

    char return_value_used, zval *this_ptr TSRMLS_DC)
```

### `function_entry` 和 `PHP_FE` 宏

当然，仅仅声明函数是不够的。引擎需要知道函数的地址，以及函数名应该如何导出到用户空间。这通过接下来的代码块实现，你需要将其紧挨放在 `PHP_FUNCTION()` 块之后：

```php
static function_entry php_sample_functions[] = {

    PHP_FE(sample_hello_world,        NULL)

    { NULL, NULL, NULL }

};
```

`php_sample_functions` 向量是一个简单的 NULL 终止的向量，随着你继续向示例扩展添加功能，它会不断增长。你导出的每个函数都会作为该向量中的一项出现。拆解 `PHP_FE()` 宏，你会发现它展开为：

```php
{ "sample_hello_world", zif_sample_hello_world, NULL},
```



因此为新函数提供了一个名称，同时也提供了指向其实现函数的指针。该集合中的第三个参数用于提供参数提示信息，例如要求某些参数必须通过引用传递。你将在第 7 章“接收参数”中看到此功能的用法。

现在你有了一个可导出的函数列表，但仍然没有将其与引擎连接起来。这是通过对`sample.c`的最后修改实现的，只需将你的`sample_module_entry`结构中的`NULL, /* Functions */`行替换为`php_sample_functions,`（务必保留那个逗号！）

现在按照之前的说明重新构建，并使用`php`命令行行的`-r`选项进行测试，该选项允许运行简单的代码片段，而无需创建整个文件：

```bash
$ php -r 'sample_hello_world();'
```

如果一切顺利，你将几乎立即看到“Hello World!”字样。

## Zend 内部函数

内部函数名前的前缀`zif_`字符串代表“Zend Internal Function”（Zend 内部函数），用于避免可能的符号冲突。例如，用户空间的`strlen()`函数无法实现为`void strlen(INTERNAL_FUNCTION_PARAMTERS)`，因为它将与 C 库的`strlen`实现冲突。

有时即使是默认的`zif_`前缀也无济。这通常是因为函数名展开了另一个宏，并被 C 编译器误解。在这些情况下，可以使用`PHP_NAMED_FUNCTION()`宏为内部函数赋予任意名称；例如，`PHP_NAMED_FUNCTION(zif_sample_hello_world)`与之前使用的`PHP_FUNCTION(sample_hello_world)`相同。

在添加使用`PHP_NAMED_FUNCTION()`声明的实现时，需要使用`PHP_NAMED_FE()`宏将其链接到`function_entry`向量中。因此，如果你将函数声明为`PHP_NAMED_FUNCTION(purplefunc)`，你应该使用`PHP_NAMED_FE(sample_hello_world, purplefunc, NULL)`，而不是使用`PHP_FE(sample_hello_world, NULL)`。

这种做法可以在`ext/standard/file.c`中看到，其中`fopen()`函数实际上是使用`PHP_NAMED_FUNCTION(php_if_fopen)`声明的。对于用户空间而言，该函数并没有特殊；它仍然被简单地调用为`fopen()`。然而在内部，该函数防止了被预处理器宏和过度热心的编译器的篡改。

## 函数别名

某些函数可以使用多个名称引用。记得普通函数在内部声明时是带有`zif_`前缀的函数用户空间名，很容易看出可以使用`PHP_NAMED_FE()`宏来创建这种替代映射：

```php
PHP_FE(sample_hello_world,    NULL)
PHP_NAMED_FE(sample_hi,    zif_sample_hello_world,     NULL)
```

`PHP_FE()`宏将用户空间函数名`sample_hello_world`与`zif_sample_hello_world`（`PHP_FUNCTION(sample_hello_world)`的展开）关联起来。`PHP_NAMED_FE()`宏随后将用户空间函数名`sample_hi`与同一个内部实现关联起来。

现在假设由于 Zend 引擎的重大更改，内部函数的标准前缀从`zif_`变为`pif_`。你的扩展将突然停止编译，因为当遇到`PHP_NAMED_FE()`函数时，`zif_sample_hello_world`是未定义的。

这种异常但麻烦的情况可以通过使用`PHP_FNAME()`宏来为你展开`sample_hello_world`来避免：

```php
PHP_NAMED_FE(sample_hi, PHP_FNAME(sample_hello_world), NULL)
```

这样，如果函数前缀发生变化，函数条目将使用 PHP Core 定义的展开自动更新。

现在你已经让这个条目工作了，猜怎么着？没必要。PHP 导出了另一个专门为创建函数别设计的宏。之前的示例可以简单重写为：

```php
PHP_FALIAS(sample_hi, sample_hello_world, NULL)
```

事实上，这是创建函数别名的官方方法，你会在 PHP 源码树的几乎任何地方看到这样做。

## 总结

在本章中，你创建了一个简单的工作 PHP 扩展，并学习了在大多数主要平台上构建它所需的步骤。在接下来的章节中，你将扩展此扩展，最终包含所有类型的 PHP 特性。

PHP 源码树以及它在支持的许多平台上编译和构建所需的工具在不断变化。如果本章中的某些内容无法工作，请参考`php.net`在线手册下的`Installation`部分，查看你的版本是否有特殊需求。

![](img/30011536.html)

---

# 第 6 章.返回值

用户空间函数使用`return`关键字将信息传回其调用作用域，这与你可能在 C 应用程序中熟悉的做法相同，例如：

```php
function sample_long() {
  return 42;
}
$bar = sample_long();
```

当调用`sample_long()`时，数字`42`被返回并填充到`$bar`变量中。在 C 中，这可以使用几乎相同的代码库来实现：

```c
int sample_long(void) {
  return 42;
}
void main(void) {
  int bar = sample_long();
}
```

当然，在 C 中，你总是可以根据函数原型知道所调用的函数将返回什么，因此你可以声明存储结果的变量。然而在处理 PHP 用户空间时，变量类型是动态的，你必须依靠第 2 章“从内而外的变量”中引入的`zval`类型。

![](img/30011536.html)

## `return_value`变量

你可能认为你的内部函数应该立即返回一个 zval，或者为 zval 分配更多内存并返回一个 zval，如下代码块所示：

```php
PHP_FUNCTION(sample_long_wrong)
{
    zval *retval;
    MAKE_STD_ZVAL(retval);
    ZVAL_LONG(retval, 42);
    return retval;
}
```

遗憾的是，你很接近但错了。Zend 并不是让每个函数实现分配 zval 并返回，它在调用方法之前预分配了此空间。它将 zval 的类型初始化为`IS_NULL`，并以名为`return_value`的参数形式传递该值。这里是同一个函数的正确写法：

```php
PHP_FUNCTION(sample_long)
{
    ZVAL_LONG(return_value, 42);
    return;
}
```

注意`PHP_FUNCTION()`实现没有直接返回任何内容。相反，`return_value`参数被直接填充了适当的数据，Zend 引擎会在内部函数执行后将其处理为该值。

提醒一下，`ZVAL_LONG()`宏是对一组赋值操作简单封装，在本例中：

```php
Z_TYPE_P(return_value) = IS_LONG;
Z_LVAL_P(return_value) = 42;
```

或者更原始的方式：

```
return_value->type = IS_LONG;
return_value->value.lval = 42;
```

> **注意**
> `return_value`变量的`is_ref`和`refcount`属性几乎不应该被内部函数直接修改。这些值是由 Zend Engine 在调用你的函数时进行初始化和处理的。

让我们通过将该特定函数添加到第 5 章“你的第一个扩展”的示例扩展中（紧跟在`sample_hello_world()`函数下方）来查看它的实际运行情况。你还需要扩展`php_sample_functions`结构体，包含一个`sample_long()`的函数条目，如下所示：

```
static function_entry php_sample_functions[] = {
    PHP_FE(sample_hello_world, NULL)
    PHP_FE(sample_long, NULL)
    { NULL, NULL, NULL }
};
```

此时，可以通过在源目录中执行`make`，或者在 Windows 的 PHP 源码根目录下执行`nmake php_sample.dll`来重新构建扩展。

如果一切顺利，你现在可以运行 PHP 并测试你的新函数了：

```
$ php -r 'var_dump(sample_long());'
```

## 紧密封装你的宏

为了保持代码的可读性和可维护性，`ZVAL_*()`宏具有专门针对`return_value`变量的对应项。在每情况下，宏的`ZVAL`部分都被替换为`RETVAL`术语，并且省略了本该表示被修改变量的初始参数。

在之前的示例中，`sample_long()`的实现可以简化为如下：

```
PHP_FUNCTION(sample_long)
{
    RETVAL_LONG(42);
    return;
}
```

表 6.1 列出了 Zend Engine 定义的`RETVAL`系列宏。除极两种情况外，所有的`RETVAL`宏都与其`ZVAL`对应项相同，只是删除了初始的`return_value`参数。

### 表 6.1. 返回值宏

| 通用`ZVAL`宏 | `return_value`专用对应项 |
| --- | --- |
| `ZVAL_NULL(return_value)` | `RETVAL_NULL()` |
| `ZVAL_BOOL(return_value, bval)` | `RETVAL_BOOL(bval)` |
| `ZVAL_TRUE(return_value)` | `RETVAL_TRUE` |
| `ZVAL_FALSE(return_value)` | `RETVAL_FALSE` |
| `ZVAL_LONG(return_value, lval)` | `RETVAL_LONG(lval)` |
| `ZVAL_DOUBLE(return_value, dval)` | `RETVAL_DOUBLE(dval)` |
| `ZVAL_STRING(return_value, str, dup)` | `RETVAL_STRING(str, dup)` |
| `ZVAL_STRINGL(return_value, str, len, dup)` | `RETVAL_STRINGL(str,len,dup)` |
| `ZVAL_RESOURCE(return_value, rval)` | `RETVAL_RESOURCE(rval)` |

注意：`return_value`变量的`is_ref`和`refcount`属性几乎不应该被内部函数直接修改。这些值是由 Zend Engine 在调用你的函数时进行初始化和处理的。

`ZVAL_*()`宏具有专门针对`return_value`变量的对应项。在每情况下，宏的`ZVAL`部分都被替换为`RETVAL`术语，并且省略了本该表示被修改变量的初始参数。

`RETVAL`宏与其`ZVAL`对应项相同，只是删除了初始的`return_value`参数。

```
#if (PHP_MAJOR_VERSION > 5) || (PHP_MAJOR_VERSION == 5 && \
                          PHP_MINOR_VERSION > 0)
PHP_FUNCTION(sample_reference_a)
{
    zval **a_ptr, *a;
    /* 从全局符号表中获取 $a */
    if (zend_hash_find(&EG(symbol_table), "a", sizeof("a"),
                                          (void**)&a_ptr) == SUCCESS) {
        a = *a_ptr;
    } else {
        /* $GLOBALS['a'] 尚不存在，创建它 */
        ALLOC_INIT_ZVAL(a);
        zend_hash_add(&EG(symbol_table), "a", sizeof("a"), &a,
                                              sizeof(zval*), NULL);
    }
    /* 丢弃旧的 return_value */
    zval_ptr_dtor(return_value_ptr);
    if (!a->is_ref && a->refcount > 1) {
        /* $a 在在一个写时复制引用集中
         * 在使用之前必须将其分离
         */
        zval *newa;
        MAKE_STD_ZVAL(newa);
        *newa = *a;
        zval_copy_ctor(newa);
        newa->is_ref = 0;
        newa->refcount = 1;
        zend_hash_update(&EG(symbol_table), "a", sizeof("a"), &newa,
                                                 sizeof(zval*), NULL);
        a = newa;
    }
    /* 提升为引用并增加引用计数 */
    a->is_ref = 1;
    a->refcount++;
    *return_value_ptr = a;
}
#endif /* PHP >= 5.1.0 */
```

`return_value_ptr`参数是另一个传递给所有内部函数的常用参数，是一个包含指向`return_value`指针的`zval**`。通过对它调用`zval_ptr_dtor()`，可以释放默认的`return_value zval*`。然后你就可以自由地将其替换为你选择的新`zval*`，在本例中为变量`$a`，它已被提升为`is_ref`，并可能地与它可能拥有的任何非全引用配对分离。

然而，如果你现在编译并运行这段代码，将得到一个段错误（segfault）。为了让它工作，你需要在你的`php_sample.h`文件中添加一个结构：

```
#if (PHP_MAJOR_VERSION > 5) || (PHP_MAJOR_VERSION == 5 && \
                          PHP_MINOR_VERSION > 0)
static
    ZEND_BEGIN_ARG_INFO_EX(php_sample_retref_arginfo, 0, 1, 0)
    ZEND_END_ARG_INFO ()
#endif /* PHP >= 5.1.0 */
```

然后在在`php_sample_functions`中声明函数时使用该结构：

```
#if (PHP_MAJOR_VERSION > 5) || (PHP_MAJOR_VERSION == 5 && \
                          PHP_MINOR_VERSION > 0)
    PHP_FE(sample_reference_a, php_sample_retref_arginfo)
#endif /* PHP >= 5.1 */
```

该结构（你稍后会学习更多）为 Zend 引擎调用提供了关键的提示。在这种情况下，它告诉 ZE `return_value`需要被覆盖，并且应该用正确的地址填充`return_value_ptr`。如果没有这个提示，ZE 将简单地在`return_value_ptr`中放置 NULL，这将导致该函数在遇到`zval_ptr_dtor`时崩溃。

> **注意**
> 这些代码片段都封装在`#if`块中，以确保只有当 PHP 版本大于或等于 5 时才启用支持。如果没有这些指令，在 PHP4 上将无法编译（因为`return_value_ptr`不存在），并且无法在 PHP 上运行。

## 通过引用返回值

使用构造函数从函数返回值和引用是很好的，但有时你希望从函数返回多个值。你可以使用数组来实现这一点（我们将在第 8 章中探讨），或者你也可以通过参数返回值。

### 运行时引用传递

通过引用传递变量的一种较简单的方法是要求调用处包含`&`符号，如下所示的用户空间代码：

```
function sample_byref_calltime($a) {
    $a .= ' (modified by ref!)';
}
$foo = 'I am a string';
sample_byref_calltime(&$a);
echo $foo;
```

参数中的符号 (`&`) 将实际的`zval`而不是副本传递给函数，这允许函数原地修改值。如果`sample_byref_calltime()`没有带`&`被调用，函数内部的更改将不会影响原始变量。在 C 中重复这种尝试不需要特殊处理。在`sample.c`中创建以下函数：



## 第 6 章 引用传递

### 运行时引用传递

`PHP_FUNCTION(sample_byref_calltime)` 的实现如下：

```c
PHP_FUNCTION(sample_byref_calltime)
{
    zval *a;
    int addtl_len = sizeof(" (modified by ref!)") - 1;

    if (zend_parse_parameters(ZEND_NUM_ARGS(), "a", &a) == FAILURE) {
        return;
    }

    if (!a->is_ref) {
        /* 参数没有通过引用传递 */
        return;
    }

    /* 确保变量是字符串 */
    convert_to_string(a);

    /* 增大缓冲区以持有额外数据 */
    Z_STRVAL_P(a) = realloc(Z_STRVAL_P(a), Z_STRLEN_P(a) + addtl_len + 1);
    memcpy(Z_STRVAL_P(a) + Z_STRLEN_P(a), " (modified by ref!)", addtl_len);
    Z_STRLEN_P(a) += addtl_len;
}
```

同样，此函数需要添加到 `php_sample_functions` 结构中：

```c
PHP_FE(NULL, NULL)
```

#### 编译时引用传递

更常用的引用传递方法是通过编译时引用。在这里，函数的参数被声明仅供引用使用，传递常量或中间值（例如函数的结果）将导致错误，因为没有地方存储返回的值。用户空间的编译时引用函数可能看起来如下：

```php
function sample_byref_compiletime(&$a) {
    $a .= ' (modified by ref!)';
}

$foo = 'I am a string';
sample_byref_compiletime($foo);
echo $foo;
```

如你所见，这与运行时版本的区别仅在于引用符号的位置。当在 C 中查看此函数时，函数代码实现完全相同。真正的区别在于在 `php_sample_functions` 块中的声明方式：

```c
PHP_FE(sample_byref_compiletime, php_sample_byref_arginfo)
```

其中 `php_sample_byref_arginfo` 是一个（命名冗长的）常量结构，你需要在编译此条目之前定义它。

#### 注意

`is_ref` 的检查实际上可以从编译时版本中删除，因为它始终会失败并退出，但现在保留它也没有害处。

在 Zend 引擎 1 (PHP4) 中，这将是一个简单的 `char*` 列表，由一个长度字节和一组适用于函数每个参数的标志组成。

```c
static unsigned char php_sample_byref_arginfo[] =
                                { 1, BYREF_FORCE };
```

在这里，`1` 表示向量仅包含一个参数的参数信息。特定的参数信息随后在后续元素中，第一个参数位于第二个元素中如所示。如果涉及第二个或第三个参数，它们的标志将分别进入第三和第四个元素，依此类推。给定参数元素的可能值见表 6.2。

#### 表 6.2. Zend 引擎 1 参数信息常量

| 引用类型 | 含义 |
| --- | --- |
| `BYREF_NONE` | 永远不允许对此参数进行引用传递。尝试使用运行时引用传递将被忽略并取而复制参数。 |
| `BYREF_FORCE` | 无论如何调用函数，参数始终通过引用传递传递。这等同于在用户空间的函数参数声明中使用 `&` 符号。 |
| `BYREF_ALLOW` | 参数是否通过引用传递取决于调用时的语义。这等同于普通的用户空间函数声明。 |
| `BYREF_FORCE_REST` | 当前参数及所有后续参数都将应用 `BYREF_FORCE`。此标志只能是列表中的最后一个参数信息标志。在 `BYREF_FORCE_REST` 之后放置额外的标志将导致未定义行为。 |

在 Zend Engine 2 (`PHP5+`) 中，你将使用一个更广泛的结构，其中包含如最小和最大参数要求、类型提示以及是否强制引用等信息。

首先，使用两个宏之一来声明 `arg info` 结构体。较简单的宏 `ZEND_BEGIN_ARG_INFO()` 接受两个参数：

```c
ZEND_BEGIN_ARG_INFO(name, pass_rest_by_reference)
```

`name` 简单来说就是该结构在扩展内部的引用名称，在本例中为：`php_sample_byref_arginfo`。

`pass_rest_by_reference` 在此处的含义与在 Zend Engine 1 arg info 向量末尾使用 `BYREF_FORCE_REST` 相同。如果此参数设置为 `1`，则结构体中未显式描述的所有参数将被假设为编译时引用传递参数。

另一个起始宏引入了两个 Zend Engine 1 版本中没有的新选项，即 `ZEND_BEGIN_ARG_INFO_EX()`：

```c
ZEND_BEGIN_ARG_INFO_EX(name, pass_rest_by_reference, return_reference,
                             required_num_args)
```

`name` 和 `pass_rest_by_reference` 在此处的含义显然相同。`return_reference` 正如你在本章之前看到的那样，它向 Zend 提供一个提示，说明你的函数将用你自己的 `zval` 覆盖 `return_value_ptr`。

最后一个参数 `required_num_args` 是另一个给 Zend 的快捷提示，允许它在已知函数原型与其调用方式不兼容时，完全跳过某些函数调用。

在放置了合适的起始宏后，后面可以跟随零或多个 `ZEND_ARG_*INFO` 元素。这些宏的类型和用法见表 6.3。最后，所有使用 Zend Engine 2 宏的 arg info 结构体必须使用 `ZEND_END_ARG_INFO()` 结束列表。对于你的示例函数，你可能会选择如下的最终结构：

#### 表 6.3. ZEND_ARG_INFO 族宏

| Arg Info 宏 | 用途 |
| --- | --- |
| `ZEND_ARG_PASS_INFO(by_ref)` | 这里的 `by_ref` 与后续所有宏相同，是一个二进制选项，指示相应参数是否应强制通过引用传递。将此选项设置为 `1` 等同于在 Zend Engine 1 向量中使用 `BYREF_FORCE`。 |
| `ZEND_ARG_INFO(by_ref, name)` | 此宏提供了一个额外的 `name` 属性，用于内部生成的错误信息和反射 API。它应该被设置为有助于理解且不晦涩的名称。 |
| `ZEND_ARG_ARRAY_INFO(by_ref, name, allow_null)` `ZEND_ARG_OBJ_INFO(by_ref, name, classname, allow_null)` | 这两个宏为内部函数提供了参数类型提示，指定期望的参数为数组或特定的类实例。将 `allow_null` 设置为非零值将允许调用域传递 `NULL` 值来代替数组/对象。 |

```c
ZEND_BEGIN_ARG_INFO(php_sample_byref_arginfo, 0)
    ZEND_ARG_PASS_INFO(1)
ZEND_END_ARG_INFO()
```

为了制作同时兼容 ZE1 和 ZE2 的扩展，有必要使用 `#ifdef` 语句并为两者定义相同的 `arg_info` 结构体，在本例中：

```c
#ifdef ZEND_ENGINE_2
static
    ZEND_BEGIN_ARG_INFO(php_sample_byref_arginfo, 0)
        ZEND_ARG_PASS_INFO(1)
    ZEND_END_ARG_INFO()
#else /* ZE 1 */
static unsigned char php_sample_byref_arginfo[] =
                                { 1, BYREF_FORCE };
#endif
```

现在所有部分都已就绪，是时候创建一个实际的编译时引用传递实现了。首先，我们将定义 ZE1 和 ZE2 的 `php_sample_byref_arginfo` 块放入头文件 `php_sample.h` 中。

接下来，你可以采取两种方法：一种是复制并粘贴 `PHP_FUNCTION(sample_byref_calltime)` 的实现并将其重命名为 `PHP_FUNCTION(sample_byref_compiletime)`，然后在 `php_sample_functions` 中添加一行 `PHP_FE(sample_byref_compiletime, php_sample_byref_arginfo)`。

这种方法非常直观，而且在多年后进行更改时可能不容易产生困惑。然而，由于这只是示例代码，你可以使用上章看到的 `PHP_FALIAS()` 来稍微得意一点，并避免代码重复。

这一次，不是创建 `PHP_FUNCTION(sample_byref_calltime)` 的副本，而是在 `php_sample_functions` 中添加一行：

```c
PHP_FALIAS(sample_byref_compiletime, sample_byref_calltime,
    php_sample_byref_arginfo)
```

正如你从第 5 章回忆的这创建了一个名为 `sample_byref_compiletime()` 的用户空间函数，其内部实现使用 `sample_byref_calltime()` 的代码。添加 `php_sample_byref_arginfo` 使这个版本变得独特。

### 总结

在本章中，你查看了如何从内部函数返回值，包括直接通过值、通过引用以及通过引用使用参数栈。你还初步了解了使用 Zend Engine 2 的 `zend_arg_info` 结构进行参数类型提示。

在下一章中，你将更深入地研究接受基础 zvals 参数，并使用 `parse_parameters()` 强大的类型转换功能。

## 第 7 章 接收参数

除了几个“预告”例外外，你到目前为止处理的扩展函数都是简单的、仅返回值的。然而，大多数函数都想要传入某些参数并根据值接收有意义的响应。

### 使用 `zend_parse_parameters()` 进行自动类型转换

正如你上章看到的返回值一样，参数值是通过间接 zval 进行移动的。获取这些 zval 值的最简单方法是使用 `zend_parse_parameters()` 函数。

`zend_parse_parameters()` 的调用几乎总是以 `ZEND_NUM_ARGS()` 宏开始，随后是无处不在的 `TSRMLS_CC`。`ZEND_NUM_ARGS()` 如其名，返回一个表示实际传递给函数的参数数量的 `int`。由于 `zend_parse_parameters()` 的工作方式，你可能不需要直接检查此值，只需传递即可。

`zend_parse_parameters()` 的下一个参数是格式参数，它由一组字母或字符序列组成，对应 Zend Engine 支持的各种原始类型。表 7.1 显示了基础类型字符。

##### 表 7.1. z_parse_parameters() 类型限定

| 类型限定 | 用户空间数据类型 |
| --- | --- |
| `b` | 布尔值 |
| `l` | 整数 |
| `d` | 浮点数 |
| `s` | 字符串 |
| `r` | 资源 |
| `a` | 数组 |
| `o` | 对象实例 |
| `O` | 指定类型的对象实例 |
| `z` | 非特定 zval |
| `Z` | 解引用的非特定 zval |

ZPP 的剩余参数取决于你在格式字符串中请求了哪些特定类型。对于简单类型，这是一个解引用的 C 语言类型。例如，长整型数据类型提取如下：

```php
PHP_FUNCTION(sample_getlong)
{
    long foo;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC,
                         "l", &foo) == FAILURE) {
        RETURN_NULL();
    }

    php_printf("The integer value of the parameter you "
             "passed is: %ld\n", foo);
    RETURN_TRUE;
}
```

#### 注意

虽然整数（integer）和长整（long）的数据存储大小通常相同，但它们并不总是可以互换。尝试将 `int` 数据类型解引用到 `long*` 参数可能会导致意想不到的结果，尤其是在 64 位平台日益普及的情况下。请务必使用表 7.2 中列出的相应数据类型。

### 表 7.2. `zend_parse_parameters()` 数据类型

| 类型说明符 | C 数据类型 |
| --- | --- |
| `b` | `zend_bool` |
| `l` | `long` |
| `d` | `double` |
| `s` | `char*, int` |
| `r` | `zval*` |
| `a` | `zval*` |
| `o` | `zval*` |
| `O` | `zval*, zend_class_entry*` |
| `z` | `zval*` |
| `Z` | `zval*` |

注意，所有复杂数据类型实际上都被解析为简单的 zvals。在大多数情况下，这是由于与阻止使用 `RETURN_*()` 宏返回复杂数据类型的相同限制：在 C 语言中实际上没有与这些结构对应的对应物。然而，`Z` 对你的函数的作用是确保你收到的 `zval*` 是正确的类型。如果需要，它甚至会执行隐式转换，例如将数组转换为 `stdClass`。

`s` 和 `O` 类型也值得注意，因为它们每次调用都需要一对参数。当你深入探索第 10 章“PHP 对象”以及第 11 章“PHP 对象”时，你会更深入地看到 `O`。在 `s` 类型的情况下，假设你正在扩展第 5 章“你的第一个扩展”中的 `sample_hello_world()` 函数，以便通过名称向特定人员：

```php
function sample_hello_world($name) {
    echo "Hello $name!\n";
}
```

在 C 中，你将使用 `zend_parse_parameters()` 函数来请求字符串：

```php
PHP_FUNCTION(sample_hello_world)
{
    char *name;
    int name_len;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "s",
                        &name, &name_len) == FAILURE) {
        RETURN_NULL();
    }

    php_printf("Hello ");
    PHPWRITE(name, name_len);
    php_printf("!\n");
}
```

## 提示

`zend_parse_parameters()` 函数可能会因为传递给函数的参数太少，无法满足格式字符串而失败，或者因为传递的某一个参数无法转换为请求的类型而失败。在这种情况下，它会自动输出错误信息，这样你的扩展就不需要自己处理了。

要请求多个参数，请扩展格式说明符以包含额外的字符，并将后续参数堆叠到 `zend_parse_parameters()` 调用中。参数按从左到右的顺序解析，与它们在用户声明中的顺序完全一致：

```php
function sample_hello_world($name, $greeting) {
    echo "Hello $greeting $name!\n";
}
```

或者：

```php
PHP_FUNCTION(sample_hello_world)
{
    char *name;
    int name_len;
    char *greeting;
    int greeting_len;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "ss",
      &name, &name_len, &greeting, &greeting_len) == FAILURE) {
        RETURN_NULL();
    }

    php_printf("Hello ");
    PHPWRITE(greeting, greeting_len);
    php_printf(" ");
    PHPWRITE(name, name_len);
    php_printf("!\n");
}
```



除了类型原始类型外，还有三个额外的元字符，用于修改参数的处理方式。表 7.3 列出了这些修饰符。

### 表 7.3. `zend_parse_parameters()` 修饰符

| 类型修饰符 | 含义 |
| --- | --- |
| `\|` | 后面是可选参数。当指定此项时，所有之前的参数都被视为必填，而所有后续参数都被视为可选的。 |
| `!` | 如果为前面的参数说明符对应的参数传递了 `NULL`，则提供的内部变量将被设置为实际的 `NULL` 指针，而不是一个类型为 `IS_NULL` 的 `zval`。 |
| `/` | 如果与前面的参数说明符对应的参数在写时复制引用集中，它将自动分离到一个新的 `zval` 中，其 `is_ref=0` 且 `refcount=1`。 |

### 可选参数

再次查看修改后的 `sample_hello_world()`，在 PHP 中，可以让 `$greeting` 参数是可选的：

```php
function sample_hello_world($name, $greeting) {
    echo "Hello $greeting $name!\n";
}
```

`sample_hello_world()` 现在可以带参数调用，也可以只带：

```php
sample_hello_world('Rogers');
sample_hello_world('Astaire');
```

为了实现这一点，在 `zend_parse_parameters()` 中使用管道符 (`|`)。位于左侧的参数将被解析，而右侧未提供的参数将保持默认。例如：

```php
PHP_FUNCTION(sample_hello_world)
{
    char *name;
    int name_len;
    char *greeting = "Mr.";
    int greeting_len = sizeof("Mr.") - 1;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "s|s",
      &name, &name_len, &greeting, &greeting_len) == FAILURE) {
        RETURN_NULL();
    }

    php_printf("Hello ");
    PHPWRITE(greeting, greeting_len);
    php_printf(" ");
    PHPWRITE(name, name_len);
    php_printf("!\n");
}
```

## `IS_NULL` 与 `NULL`

每个 `zval`，即使是简单的 `IS_NULL` 类型，也会占用一定的内存。此外，分配这些内存、初始化值以及在不再需要时释放它们需要一定的时钟周期。

对于许多函数来说，为了发现参数被标记为 `NULL` 而经历这个过程是没有意义的。幸运的是，可以通过向格式说明符添加感叹号来允许 `NULL`。考虑以下两个代码片段，一个带有修饰符，另一个没有：

```php
PHP_FUNCTION(sample_arg_fullnull)
{
    zval *val;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "z",
                                    &val) == FAILURE) {
        RETURN_NULL();
    }

    if (Z_TYPE_P(val) == IS_NULL) {
        val = php_sample_make_defaultval(TSRMLS_C);
    }
}
```

```php
PHP_FUNCTION(sample_arg_nullok)
{
    zval *val;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "z!",
                                    &val) == FAILURE) {
        RETURN_NULL();
    }

    if (!val) {
        val = php_sample_make_defaultval(TSRMLS_C);
    }
}
```

这两个版本在代码上并没有太大区别，尽管前者名义上消耗更多的处理时间。通常情况下，这个功能并不非常有用，但知道它的存在是有好处的。

### 强制分离

当变量传递给函数时（无论是通过引用还是通过引用），它的引用计数至少为 2；一个是变量本身的引用，另一个是传递到函数的副本。在对该 `zval` 进行任何更改之前（如果是直接操作 `zval` 的话），将其从可能所属的任何非引用集中分离出来是非常重要的。

如果没有 `/` 格式说明符，这将是一项繁琐的任务，它会自动分离任何写时复制（copy-on-write）引用变量，以便你的函数可以随心所欲。就像 `NULL` 标志一样，这个修饰位于它所影响的类型之后。同样就像 `NULL` 标志，在你实际需要它之前，你并不知道你需要这个功能。

#### `zend_get_arguments()`

如果你恰好在设计适用于非常旧版本的 PHP 的代码，或者你有一个除了 `zval*` 之外不需要任何内容的函数，你可以考虑使用 `zend_get_parameters()` API 调用。

`zend_get_parameters()` 调用与其较新的 parse 对应版本有几点关键区别。首先，它不执行自动类型转换；相反，所有参数都作为原始 `zval*` 数据类型提取。`zend_get_parameters()` 最简单的用法可能如下：

```c
PHP_FUNCTION(sample_onearg)
{
    zval *firstarg;

    if (zend_get_parameters(ZEND_NUM_ARGS(), 1, &firstarg)
                                        == FAILURE) {
        php_error_docref(NULL TSRMLS_CC, E_WARNING,
            "Expected at least 1 parameter.");
        RETURN_NULL();
    }

    /* Do something with firstarg... */
}
```

其次，如从手动应用的错误消息所示，`zend_get_parameters()` 在失败时不会输出错误文本。它在处理可选参数方面也非常糟糕。具体来说，如果你要求它获取四个参数，你最好确保至少提供了四个参数，否则它将返回 `FAILURE`。

最后，与 parse 不同，这种特定的 `get` 变体会自动分离任何写时复制的引用集。如果你仍然想跳过自动分离，可以使用它的兄弟版本：`zend_get_parameters_ex()`。

除了不分离写时复制引用集外，`zend_get_parameters_ex()` 的区别在于它返回的是 `zval**` 指针，而不是简单的 `zval*`。尽管这种区别可能在你有使用原因之前并不知道自己需要它，但它的用法最终非常相似：

```c
PHP_FUNCTION(sample_onearg)
{
    zval **firstarg;

    if (zend_get_parameters_ex(1, &firstarg) == FAILURE) {
        WRONG_PARAM_COUNT;
    }

    /* Do something with firstarg... */
}
```

## Note

注意，`_ex` 版本不需要 `ZEND_NUM_ARGS()` 参数。这是由于 `_ex` 版本是在较后添加的，当时 Zend Engine 的更改使得该参数变得不再必要。

在这个示例中，你还使用了 `WRONG_PARAM_COUNT` 宏，它处理显示 `E_WARNING` 错误消息并自动离开函数。

#### Handling Arbitrary Numbers of Arguments

`zend_get_parameter` 家族还有两个成员，用于在参数数量巨大到无法接受或在运行时之前无法实际确定的情况下，提取一组 `zval*` 和 `zval**` 指针。

考虑 `var_dump()` 函数，它将显示传递给它的任意数量变量的内容：

```c
PHP_FUNCTION(var_dump)
{
    int i, argc = ZEND_NUM_ARGS();
    zval ***args;

    args = (zval ***)safe_emalloc(argc, sizeof(zval **), 0);

    if (ZEND_NUM_ARGS() == 0 ||
        zend_get_parameters_array_ex(argc, args) == FAILURE) {
        efree(args);
        WRONG_PARAM_COUNT;
    }

    for (i=0; i<argc; i++) {
        php_var_dump(args[i], 1 TSRMLS_CC);
    }

    efree(args);
}
```

在这里，`var_dump()` 根据传递给函数的参数数量预分配了一个 `zval**` 指针向量。然后它使用 `zend_get_parameters_array_ex()` 一次性填充该向量。正如你可能猜到的，该函数的另一个版本是 `zend_get_parameters_array()`，它具有相似的区别：自动分离。

### `Arg Info` and Type-hinting

除了不分离写时复制引用集外，`zend_get_parameters_ex()` 的区别在于它返回的是 `zval**` 指针，而不是简单的 `zval*`。尽管这种区别可能在你有使用原因之前并不知道自己需要它，但它的用法最终非常相似：

（注：提供的输入文本包含了重复的部分/损坏的字符串。我已根据提供的指令处理了唯一的逻辑流。）

在下一章中，你将探索数组数据类型，并查看其用户空间表示如何映射到底层的 `HashTable`。你还将了解到大量可用于操纵这些复杂结构的 Zend 和 PHP API 函数。

## 第 8 章：处理数组与哈希表

在 C 语言中，有**两种本质上完全不同的方式**可以在单个结构中存储任意数量的独立数据元素。两者各有优缺点。

### 向量（Vectors）与链表（Linked Lists）

通常根据正在编写的应用程序特定类型、需要存储的数据量以及检索速度快慢来选择其中一种。为了保持术语一致，让我们简要回顾这两种存储机制。

#### 向量 (Vectors)

向量是一块连续的内存区域，其中以固定间隔包含连续的数据段。向量最常见的例子无疑是字符串变量（`char*` 或 `char[]`），它包含一个一个接一个字符序列（字节）。

```c
char foo[4] = "bar";
```

在这里，`foo[0]` 包含字母 `'b'`；紧接着，你会在 `foo[1]` 中找到字母 `'a'`，以此此类推，最后在 `foo[3]` 处得到一个 `NULL` 字符 `'\0'`。

指向其他结构的指针也存储在向量中，例如你在上章使用 `zend_get_parameters_array_ex()` 函数时看到的 `zval` 向量。在那里，你看到 `var_dump()` 声明了一个 `zval***` 类型的函数变量，然后分配了空间来存储 `zval**` 指针，这些指针最终源于 `zend_get_parameters_ex()` 的调用。

```c
zval ***args = safe_emalloc(ZEND_NUM_ARGS(), sizeof(zval**), 0);
```

与访问字符串中的字符类似，`var_dump()` 的实现使用 `args[i]` 将单个 `zval**` 元素传递给内部函数 `php_var_dump()`。

向量最大的优势是运行时访问单个元素的速度。变量引用（如 `args[i]`）被快速计算为：`args` 指向地址处的数据加上 `i` 乘以 `args` 数据类型的大小。该索引结构的存储空间在单个高效的调用中完成分配和释放。

#### 链表 (Linked Lists)

另一种常见的数据存储方法是链表。在链表中，每个数据元素都是一个包含至少两个属性的结构体：一个指向列表中下一个项的指针，以及一些实际数据。考虑以下假设的数据结构：

```c
typedef struct _namelist namelist;
struct {
    struct namelist *next;
    char *name;
} _namelist;
```

使用此数据结构的应用程序可能定义了如下变量：

```c
static namelist *people;
```

列表中的第一个名称可以通过检查 `people` 变量的 `name` 属性来找到：`people->name`；第二个名称通过跟进 `next` 属性访问：`people->next->name`，然后是 `people->next->next->name`，以此此类推，直到 `next` 为 `NULL` 为止，这意味着列表中不再有更多名称。更常见的情况下，可能会使用循环来遍历此类链表：

```c
void name_show(namelist *p)
{
    while (p) {
        printf("Name: %s\n", p->name);
        p = p->next;
    }
}
```

这种列表对于 FIFO（先入先出）链非常有用，新数据在到达时被添加到列表末尾，而让另一个分支或线程来处理数据的消耗：

```c
static namelist *people = NULL, *last_person = NULL;

void name_add(namelist *person)
{
    person->next = NULL;
    if (!last_person) {
        /* 列表中还没有人 */
        people = last_person = person;
        return;
    }

    /* 将新人添加到列表末尾 */
    last_person->next = person;

    /* 更新列表尾部 */
    last_person = person;
}

namelist *name_pop(void)
{
    namelist *first_person = people;
    if (people) {
        people = people->next;
    }
    return first_person;
}
```



新的`namelist`结构可以根据需要无限次地移入此链表或从链表中弹出，而无需调整结构的大小或在位置之间复制元素。

你刚刚看到的这种链表形式是单向链表，虽然它有一些有趣的特性，但也有一些严重的缺点。给定链表中某一个项的指针，很难将该元素从链中剪除，并确保前一个元素能正确链接到下一个元素。

为了仅仅知道前一个元素是什么，必须遍历整个链表，直到在给定的临时元素的`next`属性中找到要删除的元素。对于大型链表，这可能会消耗大量的 CPU 时间。解决此问题的一种简单且相对廉价的方案是**双向链表**。

在双向链表中，每个元素都获得了一个额外的指针值，用于指示前一个元素的位置：

```
typedef struct _namelist namelist;

struct {

    namelist *next, *prev;

    char *name;

} _namelist;
```

当元素被添加到双向链表时，这两个指针都会随之相应更新：

```
void name_add(namelist *person)

{

    person->next = NULL;

    if (!last_person) {

        /* 列表中还没有人 */

        people = last_person = person;

        person->prev = NULL;

        return;

    }

    /* 将新人添加到列表末尾 */

    last_person ->next = person;

    person->prev = last_person;

    /* 更新列表尾部 */

    last_person = person;

}
```

到目前为止你还没有看到这种方法的任何优势，但现在假设你从`people`列表中间某处有一个任意的`namelist`记录，你想删除它。在单向链表中，你需要执行类似以下的操作：

```
void name_remove(namelist *person)

{

    namelist *p;

    if (person == people) {

        /* 恰好是列表中的第一个 */

        people = person->next;

        if (last_person == person) {

            /* 恰好也是列表中的最后一个 */

            last_person = NULL;

        }

        return;

    }

    /* 寻找前一个人人 */

    p = people;

    while (p) {

        if (p->next == person) {

            /* 解除 */

            p->next = person->next;

            if (last_person == person) {

                /* 这是最后一个元素 */

                last_person = p;

            }

            return;

        }

        p = p->next;

    }

    /* 列表中未找到 */

}
```

现在将这段代码与双向链表中这种更简单的方法进行对比：

```
void name_remove(namelist *person)

{

    if (people == person) {

        people = person->next;

    }

    if (last_person == person) {

        last_person = person->prev;

    }

    if (person->prev) {

        person->prev->next = person->next;

    }

    if (person->next) {

        person->next->prev = person->prev;

    }

}
```

与长而复杂的循环相比，将此元素从列表中删除只需要一组封装在条件判断中的简单赋值。该过程的反向操作允许以同样的改进效率在列表的任意位置插入元素。

## 哈希表：两者的结合

尽管你很可能在应用程序的几处使用向量或链表，但还有另一种你最终会使用得更多的集合类型：`HashTable`（哈希表）。

`HashTable`是双向链表的特殊形式，它通过查找索引的形式增加了向量的速度和效率。哈希表在 Zend 引擎和 PHP 核心中被使用非常频繁，以至于整个 Zend API 子集专门用于处理这些结构。

正如你在第 2 章中所看到的，“从内向外的变量”，所有用户空间变量都以`zval*`指针的形式存储在`HashTables`中。在后面的章节中，你将看到 Zend 引擎如何使用`HashTables`来存储用户空间函数、类、资源、自动全局标签以及其他结构。

复习第 2 章的知识：Zend 引擎`HashTable`实际上可以存储任何大小的任何数据。例如，函数是以完整的结构形式存储的。自动全局变量仅占几个字节，较小元素，而变量和 PHP5 类定义等其他结构仅被存储为指向内存中其他位置结构体的指针。

在本章的后续内容中，你将查看构成 Zend Hash API 的函数调用，以及你可以在你的扩展中使用这些方法。

![](img/30011536.html)

## Zend Hash API

Zend Hash API 分为几个基本类别，除了少数例外外，这些类别中的函数通常会返回`SUCCESS`或`FAILURE`。

### 创建

每个`HashTable`都由一个公共构造函数初始化：

```
int zend_hash_init(HashTable *ht, uint nSize,

    hash_func_t pHashFunction,

    dtor_func_t pDestructor, zend_bool persistent)
```

`ht`是一个指向`HashTable`变量的指针，该变量可以声明为立即值，也可以通过`emalloc()`、`pemalloc()`或更常见的`ALLOC_HASHTABLE(ht)`动态分配。`ALLOC_HASHTABLE()`宏使用来自特殊池的预设大小的内存块来加速分配所需的时间，通常优于`ht = emalloc(sizeof(HashTable));`。

`nSize`应该设置为`HashTable`预期包含的元素最大数量。如果向`HashTable`中添加了超过此数量的元素，它能够增长，但会在处理时间上产生显著的代价，因为 Zend 会为新扩宽的结构重新索引整个表。如果`nSize`不是 2 的幂，它将根据以下公式自动扩大到下一个更高的 2 的幂：

```
nSize = pow(2, ceil(log(nSize, 2)));
```

`pHashFunction`是 Zend 引擎早期版本的遗留物，不再被使用，因此此值应始终设置为`NULL`。在 Zend 引擎的早期版本中，此值可以指向备用的哈希算法以替代标准的`DJBX33A`方法——这是一种快速且中等抗碰撞的哈希算法，用于将任意字符串键转换为可重现整数值。

`pDestructor`是指向一个方法的指针，当元素从`HashTable`中移除时会调用该方法，例如使用`zend_hash_del()`或使用`zend_hash_update()`替换项目时。任何析构方法的原型必须是：

```
void method_name(void *pElement);
```

其中`pElement`是指向正从`HashTable`中移除的项的指针。

最后一个选项`persistent`是一个简单的标志，引擎将其传递给你在第 3 章“内存管理”中介绍的`pemalloc()`函数调用。任何需要在请求之间保持可用的`HashTables`必须设置此标志，并且必须使用`pemalloc()`进行分配。

此方法可以在每个 PHP 请求周期的开始时看到，当全局变量`EG(symbol_table)`被初始化时：

```
zend_hash_init(&EG(symbol_table), 50, NULL, ZVAL_PTR_DTOR, 0);
```

正如你在这里看到的，当项从符号表中移除时（可能是为了响应`unset($foo);`语句），指向存储在`HashTable`中的`zval*`的指针（实质上是`zval**`）会被发送给`zval_ptr_dtor()`，而这就是`ZVAL_PTR_DTOR`宏展开后的结果。

由于 50 不是 2 的精确幂，初始全局符号表的大小实际上将是 64——下一个更高的 2 的幂。

### 填充

有四个主要函数用于在`HashTables`中插入或更新数据：

```
int zend_hash_add(HashTable *ht, char *arKey, uint nKeyLen,

                void **pData, uint nDataSize, void *pDest);

int zend_hash_update(HashTable *ht, char *arKey, uint nKeyLen,

                void *pData, uint nDataSize, void **pDest);

int zend_hash_index_update(HashTable *ht, ulong h,

                void *pData, uint nDataSize, void **pDest);

int zend_hash_next_index_insert(HashTable *ht,

                void *pData, uint nDataSize, void **pDest);
```

这里的前两个函数用于向`HashTable`添加关联索引的数据，例如通过语句`$foo['bar'] = 'baz';`，这在 C 语言中看起来像这样：

```
zend_hash_add(fooHashTbl, "bar", sizeof("bar"), &barZval, sizeof(zval*), NULL);
```

`zend_hash_add()`和`zend_hash_update()`之间的唯一区别是，如果键已经存在，`zend_hash_add()`将失败。

接下来两个函数处理数值索引的`HashTables`，方式类似。此时，两者之间的区别在于是提供了特定索引，还是自动分配可用索引。

如果你需要插入下一个可用索引，使用`zend_hash_next_index_insert()`。如果你需要更新特定索引，使用`zend_hash_update()`。

### 回收

由于`HashTable`索引有两种不同的组织方式，因此有两个方法可以提取它们：

```
int zend_hash_find(HashTable *ht, char *arKey, uint nKeyLen,

                                        void **pData);

int zend_hash_index_find(HashTable *ht, ulong h, void **pData);
```

正如你猜测的，第一个用于关联数组，第二个用于数值数组。回想第 2 章](#ch02.html#ch02)，当数据添加到`HashTable`时，会为其分配新的内存块并复制传入的数据；当将其提取出来时，返回指针。下面的代码片段将`data1`添加到`HashTable`，然后将其提取出来，使得在程序结束时`*data2`内容与`*data1`相同，尽管指针指向不同的内存地址。

```
void hash_sample(HashTable *ht, sample_data *data1)

{

   sample_data *data2;

   ulong targetID = zend_hash_next_element(ht);

   if (zend_hash_index_update(ht, targetID,

           data1, sizeof(sample_data), NULL) == FAILURE) {

       /* 不应该发生 */

       return;

   }

   if(zend_hash_index_find(ht, targetID, (void **)&data2) == FAILURE) {

       /* 极不可能，因为我们刚刚添加了这个元素 */

       return;

   }

   /* data1 != data2，然而 *data1 == *data2 */

}
```

通常，获取存储的数据并不知道它是否存在那么重要；为了这个目的，存在两个函数：

```
int zend_hash_exists(HashTable *ht, char *arKey, uint nKeyLen);

int zend_hash_index_exists(HashTable *ht, ulong h);
```

这两个方法不返回`SUCCESS`/`FAILURE`；它们返回`1`表示请求的键/索引存在，返回`0`表示不存在。下面的代码片段执行的操作等同于`isset($foo)`：

```
if (zend_hash_exists(EG(active_symbol_table),

                                "foo", sizeof("foo"))) {

    /* $foo 已设置 */

} else {

    /* $foo 不存在 */

}
```

#### 快速填充与回收

```
ulong zend_get_hash_value(char *arKey, uint nKeyLen);
```

当对同一个关联键执行多次操作时，使用`zend_get_hash_value()`预计算哈希值会非常有用。然后可以将结果传递给一组“快速”（quick）函数，这些函数的行为与其对应的非快速版本完全相同，但它们使用预计算的哈希值，而不是每次都重新计算。

```
int zend_hash_quick_add(HashTable *ht,

    char *arKey, uint nKeyLen, ulong hashval,

    void *pData, uint nDataSize, void **pDest);

int zend_hash_quick_update(HashTable *ht,

    char *arKey, uint nKeyLen, ulong hashval,

    void *pData, uint nDataSize, void **pDest);

int zend_hash_quick_find(HashTable *ht,

    char *arKey, uint nKeyLen, ulong hashval, void **pData);

int zend_hash_quick_exists(HashTable *ht,

    char *arKey, uint nKeyLen, ulong hashval);
```

令人惊讶的是，并没有`zend_hash_quick_del()`。这些“快速”哈希函数可能用于如下所示的代码片段，该片段将特定元素从`hta`拷贝到`htb`，它们都是`zval*`类型的 HashTables：

```
void php_sample_hash_copy(HashTable *hta, HashTable *htb,

                    char *arKey, uint nKeyLen TSRMLS_DC)

{

    ulong hashval = zend_get_hash_value(arKey, nKeyLen);

    zval **copyval;

    if (zend_hash_quick_find(hta, arKey, nKeyLen,

                hashval, (void**)&copyval) == FAILURE) {

        /* arKey 实际上不存在 */

        return;

    }

    /* 该 zval* 将被另一个哈希表所有 */

    (*copyval)->refcount++;

    zend_hash_quick_update(htb, arKey, nKeyLen, hashval,

                copyval, sizeof(zval*), NULL);

}
```

### 复制与合并

上一个任务（将元素从一个`HashTable`复制到另一个）是非常常见的，并且通常是批量完成的。为了避免反复调用和填充循环带来的头疼和麻烦，存在三个辅助方法：

```
typedef void (*copy_ctor_func_t)(void *pElement);

void zend_hash_copy(HashTable *target, HashTable *source,

            copy_ctor_func_t pCopyConstructor,

            void *tmp, uint size);
```



`source` 中的每个元素都将被复制到 `target`，然后通过 `pCopyConstructor` 函数进行处理。对于像用户空间变量数组这样的 `HashTables`，这提供了增加引用计数的机会，以便当 `zval*` 从其中一个 `HashTable` 中移除时，它不会被过早销毁。如果目标 `HashTable` 中已存在相同元素，它会被新元素覆盖。其他未被覆盖的现有元素不会被隐式移除。

`tmp` 应该指向一个内存区域的指针，供 `zend_hash_copy()` 函数在执行期间使用。然而，从 PHP 4.0.3 开始，这个临时空间不再被使用。如果你确定你的扩展永远不会针对低于 4.0.3 的版本进行编译，只需将其留为 `NULL` 即可。

`size` 是每个成员元素占据的字节数。在用户空间变量哈希的情况下，这将是 `sizeof(zval*)`。

```c
void zend_hash_merge(HashTable *target, HashTable *source,
            copy_ctor_func_t pCopyConstructor,
            void *tmp, uint size, int overwrite);
```

`zend_hash_merge()` 与 `zend_hash_copy()` 的唯一区别在于增加了 `overwrite` 参数。当设置为非零值时，`zend_hash_merge()` 的行为与 `zend_hash_copy()` 完全相同；当设置为零时，它会跳过任何已存在的元素。

```c
typedef zend_bool (*merge_checker_func_t)(HashTable *target_ht,
    void *source_data, zend_hash_key *hash_key, void *pParam);

void zend_hash_merge_ex(HashTable *target, HashTable *source,
            copy_ctor_func_t pCopyConstructor, uint size,
            merge_checker_func_t pMergeSource, void *pParam);
```

这组函数的最终形式允许使用合并检查函数进行选择性复制。以下示例展示了如何使用 `zend_hash_merge_ex()` 仅复制源 `HashTable` 中按关联索引的成员（该表恰好是一个用户空间变量数组）：

```c
zend_bool associative_only(HashTable *ht, void *pData,
            zend_hash_key *hash_key, void *pParam)
{
    /* 如果存在键则返回 true，否则返回 false */
    return (hash_key->arKey && hash_key->nKeyLength);
}

void merge_associative(HashTable *target, HashTable *source)
{
    zend_hash_merge_ex(target, source, zval_add_ref,
                sizeof(zval*), associative_only, NULL);
}
```

### 通过哈希应用迭代

与用户空间一样，遍历分类数组有多种方法。第一种通常也是最简单的方法是使用类似于回调的系统。以下示例展示了如何使用 `zend_hash_merge_ex()` 仅复制源 `HashTable` 中关联索引的成员（该表恰好是一个用户空间变量数组）：

```c
zend_bool associative_only(HashTable *ht, void *pData,
            zend_hash_key *hash_key, void *pParam)
{
    /* 如果存在键则返回 true，否则返回 false */
    return (hash_key->arKey && hash_key->nKeyLength);
}

void merge_associative(HashTable *target, HashTable *source)
{
    zend_hash_merge_ex(target, source, zval_add_ref,
                sizeof(zval*), associative_only, NULL);
}
```

（注：此处原文文本似乎出现了重复的段落，根据指令“不要重复输出原文”，我将根据逻辑对后续内容进行完整翻译）

与用户空间一样，遍历分类数组有多种方法。第一种通常也是最简单的方法是使用类似于回调的系统。……（由于提供的原文文本后部分存在大量重复和错乱，此处已根据核心逻辑翻译了关于“通过哈希应用迭代”的说明部分）。

为了在循环期间同时接收键和值，必须使用 `zend_hash_apply()` 的第三种形式。例如，如果你扩展此项练习以支持输出键：

```php
<?php
foreach($arr as $key => $val) {
    echo "The value of $key is: $val\n";
}
?>
```

那么你当前的迭代器回调将无处获取 `$key`。然而，通过切换到 `zend_hash_apply_with_arguments()`，你的回调原型和实现现在变为：

```php
int php_sample_print_zval_and_key(zval **val,
        int num_args, va_list args, zend_hash_key *hash_key)
{
    /* Duplicate the zval so that
     * the original's contents are not destroyed */
    zval tmpcopy = **val;

    /* tsrm_ls is needed by output functions */
    TSRMLS_FETCH();

    zval_copy_ctor(&tmpcopy);

    /* Reset refcount & Convert */
    INIT_PZVAL(&tmpcopy);
    convert_to_string(&tmpcopy);

    /* Output */
    php_printf("The value of ");
    if (hash_key->nKeyLength) {
        /* String Key / Associative */
        PHPWRITE(hash_key->arKey, hash_key->nKeyLength);
    } else {
        /* Numeric Key */
        php_printf("%ld", hash_key->h);
    }
    php_printf(" is: ");
    PHPWRITE(Z_STRVAL(tmpcopy), Z_STRLEN(tmpcopy));
    php_printf("\n");

    /* Toss out old copy */
    zval_dtor(&tmpcopy);

    /* continue; */
    return ZEND_HASH_APPLY_KEEP;
}
```

然后可以这样调用它：

```php
zend_hash_apply_with_arguments(arrht,
                    php_sample_print_zval_and_key, 0);
```

**Note**

这个特定的示例不需要传递任何参数；有关如何从 `va_list args` 提取变参数列表的信息，请参阅 POSIX 文档页中的 `va_start()`、`va_arg()` 和 `va_end()`。

注意，使用 `nKeyLength` 而不是 `arKey` 来测试键是否为关联键。这是因为 Zend HashTables 的具体实现细节有时会在 `arKey` 变量中留存数据。然而，`nKeyLength` 即使对于空键也可以安全使用（例如，`$foo[''] = "Bar";`），因为末尾的 `NULL` 被包含在内，使得键的长度为 1。

### 向迭代

不使用回调函数遍历 `HashTable` 也是轻而易举的。为此，你需要回顾一个 HashTables 中经常被忽略的概念：内部指针。

在用户空间中，可以使用 `reset()`、`key()`、`current()`、`next()`、`prev()`、`each()` 和 `end()` 函数来访问数组中的元素，这取决于一个不可见的书签认为“当前”位置在哪里：

```php
<?php
    $arr = array('a'=>1, 'b'=>2, 'c'=>3);

    reset($arr);
    while (list($key, $val) = each($arr)) {
        /* Do something with $key and $val */
    }

    reset($arr);
    $firstkey = key($arr);
    $firstval = current($arr);
    $bval = next($arr);
    $cval = next($arr);
?>
```

这些函数中的每一个在内部都有对应的实现，封装在具有相似名称的内部 Zend Hash API 函数中：

```c
/* reset() */
void zend_hash_internal_pointer_reset(HashTable *ht);

/* key() */
int zend_hash_get_current_key(HashTable *ht,
        char **strIdx, unit *strIdxLen,
        ulong *numIdx, zend_bool duplicate);

/* current() */
int zend_hash_get_current_data(HashTable *ht, void **pData);

/* next()/each() */
int zend_hash_move_forward(HashTable *ht);

/* prev() */
int zend_hash_move_backwards(HashTable *ht);

/* end() */
void zend_hash_internal_pointer_end(HashTable *ht);

/* Other... */
int zend_hash_get_current_key_type(HashTable *ht);
int zend_hash_has_more_elements(HashTable *ht);
```

**Note**

用户空间的语句 `next()`、`prev()` 和 `end()` 实际上映射到它们的向前/向后移动语句，随后调用了 `zend_hash_get_current_data()`。`each()` 执行与 `next()` 相同的步骤，但它还会调用并返回 `zend_hash_get_current_key()`。

使用向移动迭代来模拟 `foreach()` 循环实际上开始变得更加熟悉，它重复了之前的 `print_zval_and_key` 示例：

```c
void php_sample_print_var_hash(HashTable *arrht)
{
    for(zend_hash_internal_pointer_reset(arrht);
    zend_hash_has_more_elements(arrht) == SUCCESS;
    zend_hash_move_forward(arrht)) {
        char *key;
        uint keylen;
        ulong idx;
        int type;
        zval **ppval;
        zval tmpcopy;

        type = zend_hash_get_current_key_ex(arrht, &key, &keylen, &idx, 0);
        if (type == HASH_KEY_NON_EXISTANT) {
            /* Should never fail
             * since the key is known to exist. */
            continue;
        }

        /* Duplicate the zval so that
         * the original's contents are not destroyed */
        tmpcopy = **ppval;
        zval_copy_ctor(&tmpcopy);

        /* Reset refcount & Convert */
        INIT_PZVAL(&tmpcopy);
        convert_to_string(&tmpcopy);

        /* Output */
        php_printf("The value of ");
        if (type == HASH_KEY_IS_STRING) {
            /* String Key / Associative */
            PHPWRITE(key, keylen);
        } else {
            /* Numeric Key */
            php_printf("%ld", idx);
        }
        php_printf(" is: ");
        PHPWRITE(Z_STRVAL(tmpcopy), Z_STRLEN(tmpcopy));
        php_printf("\n");

        /* Toss out old copy */
        zval_dtor(&tmpcopy);
    }
}
```

```c
void php_sample_print_var_hash(HashTable *arrht)
{
    HashPosition pos;

    for(zend_hash_internal_pointer_reset_ex(arrht, &pos);
    zend_hash_has_more_elements_ex(arrht, &pos) == SUCCESS;
    zend_hash_move_forward_ex(arrht, &pos)) {
        char *key;
        uint keylen;
        ulong idx;
        int type;
        zval **ppzval, tmpcopy;

        type = zend_hash_get_current_key_ex(arrht,
                                &key, &keylen,
                                &idx, 0, &pos);
        if (zend_hash_get_current_data_ex(arrht,
                    (void**)&ppzval, &pos) == FAILURE) {
            /* Should never actually fail
             * since the key is known to exist. */
            continue;
        }

        /* Duplicate the zval so that
         * the original's contents are not destroyed */
        tmpcopy = **ppzval;
        zval_copy_ctor(&tmpcopy);

        /* Reset refcount & Convert */
        INIT_PZVAL(&tmpcopy);
        convert_to_string(&tmpcopy);

        /* Output */
        php_printf("The value of ");
        if (type == HASH_KEY_IS_STRING) {
            /* String Key / Associative */
            PHPWRITE(key, keylen);
        } else {
            /* Numeric Key */
            php_printf("%ld", idx);
        }
        php_printf(" is: ");
        PHPWRITE(Z_STRVAL(tmpcopy), Z_STRLEN(tmpcopy));
        php_printf("\n");

        /* Toss out old copy */
        zval_dtor(&tmpcopy);
    }
}
```



`zval_dtor(&tmpcopy);`

通过这些非常微小的添加，`HashTable` 真正的内部指针将保持在进入函数时的其初始状态。在处理用户态空间变量 `HashTables`（即数组）的内部指针时，这个额外的步骤很可能会决定脚本代码是否按预期工作。

### 析构 (Destruction)

你只需要关注的四个析构函数。前两个用于从 `HashTable` 中移除单个元素：

```
int zend_hash_del(HashTable *ht, char *arKey, uint nKeyLen);
int zend_hash_index_del(HashTable *ht, ulong h);
```

正如你所猜的，这些函数涵盖了 `HashTable` 的“双重人格”索引设计，为关联数组和数值索引的哈希元素提供了删除函数。每个版本返回 `SUCCESS` 或 `FAILURE`。

请记住，当项从 `HashTable` 中移除时，会调用 `HashTable` 的析构函数，并将指向要移除项的指针作为唯一参数传递。

```
void zend_hash_clean(HashTable *ht);
```

当完全清空一个 `HashTable` 时，最快的方法是调用 `zend_hash_clean()`，它将遍历每一个元素并逐个对它们调用 `zend_hash_del()`。

```
void zend_hash_destroy(HashTable *ht);
```

通常，在清理 `HashTable` 时，你可能希望完全丢弃它。调用 `zend_hash_destroy()` 将执行 `zend_hash_clean()` 的所有操作，并释放在 `zend_hash_init()` 期间分配的额外结构。

一个完整的 `HashTable` 生命周期可能如下所示：

```
int sample_strvec_handler(int argc, char **argv TSRMLS_DC)
{
    HashTable *ht;

    /* 为 HashTable 结构
     * 分配一块内存 */
    ALLOC_HASHTABLE(ht);

    /* 初始化 */
    if (zend_hash_init(ht, 0, Z_HASH_VALUE) != SUCCESS) {
        return -1;
    }

    /* 示例操作 */
    zval val;
    array_init(&val);
    add_next_key(&val, "value");
    zend_hash_update(ht, "key", &val);

    /* 清理 */
    zend_hash_destroy(ht);
    return 0;
}
```

除非你打算实现自己的替代 `bubblesort`（泡泡排序）方法，否则你不需要自己实现排序函数。已经存在一个预定义的 `sort` 方法 `zend_qsort`，可以作为 `zend_hash_sort()` 的回调函数使用，你只需要实现比较函数即可。

```
int zend_hash_sort(HashTable *ht, sort_func_t sort_func,
        compare_func_t compare_func, int renumber TSRMLS_DC);
```

`zend_hash_sort()` 的最后一个参数如果被设置，将丢弃任何现有的关联键或索引数字，并根据排序操作的结果对数组进行重新索引。用户态的 `sort()` 实现以如下方式使用 `zend_hash_sort()`：

```
zend_hash_sort(target_hash, zend_qsort,
                        array_data_compare, 1 TSRMLS_CC);
```

其中 `array_data_compare` 是一个简单的 `compare_func_t` 实现，它根据 `HashTable` 中 `zval*` 的值进行排序。

### `zval*` 数组 API

你在 PHP 扩展中处理的 `HashTables` 百分之九都是为了存储和检索用户态变量。反之，大多数 `HashTables` 本身都被封装在 `zval` 容器中。

#### 快速创建数组

为了辅助这些常用 `HashTables` 的创建和操作，PHP API 暴露了一组以 `array_init(zval *arrval)` 开头的简单宏和辅助函数。该函数分配一个 `HashTable`，使用适用于用户态变量哈希的参数调用 `zend_hash_init()`，并用新创建的结构填充 `zval*`。

不需要特殊的析构函数，因为在 `zval` 通过调用 `zval_dtor()`/`zval_ptr_dtor()` 丢失其最后一个引用计数（refcount）后，引擎会自动调用 `zend_hash_destroy()` 和 `FREE_HASHTABLE()`。

将你刚刚学会 `array_init()` 方法与你在第 6 章“返回值”中看到的函数返回技巧结合起来：

```
PHP_FUNCTION(sample_array)
{
    array_init(return_value);
}
```

因为 `return_value` 是一个预分配的 `zval*`，你不需要做其他事情来设置它。而且它的唯一引用是你从函数发送出去的那个，所以你不需要担心清理它。

#### 快速填充数组

就像处理任何 `HashTable` 一样，你通过迭代向其添加元素来填充数组。特别对于用户态变量，你可以求助于从 C 中知道的原始数据类型。对于你已经拥有的、对应 `ZVAL_*()`、`RETVAL_*()` 和 `RETURN_*()` 宏的每种数据类型，存在一组形式为 `add_assoc_*()`、`add_index_*()` 和 `add_next_index_*()` 的三剑客。例如：

```
add_assoc_long(zval *arrval, char *key, long lval);
add_index_long(zval *arrval, ulong idx, long lval);
add_next_index_long(zval *arrval, long lval);
```

在每情况下，数组 `zval*` 都在前面，后面是关联键名、数字索引，或者对于 `next_index` 变体则什么都没有。最后是数据元素本身，它最终将被封装在新分配的 `zval*` 中，并通过 `zend_hash_update()`、`zend_hash_index_update()` 或 `zend_hash_next_index_insert()` 添加到数组。

`add_assoc_*()` 函数变体及其原型如下。在每种情况下，`assoc` 都可替换为 `index` 或 `next_index`，并根据需要调整或移除键/索引参数。

```
add_assoc_null(zval *aval, char *key);
add_assoc_bool(zval *aval, char *key, zend_bool bval);
add_assoc_long(zval *aval, char *key, long lval);
add_assoc_double(zval *aval, char *key, double dval);
add_assoc_string(zval *aval, char *key, char *strval, int dup);
add_assoc_stringl(zval *aval, char *key,
                    char *strval, uint strlen, int dup);
add_assoc_zval(zval *aval, char *key, zval *value);
```

这些函数的最后一个版本允许你准备任何任意类型的 `zvals`（包括资源、对象或数组），并以同样的简单方式将它们添加到你不断增长的数组中。尝试向你的 `sample_array()` 函数中添加几次：

```
PHP_FUNCTION(sample_array)
{
    zval *subarray;
    array_init(return_value);

    /* 添加一些标量 */
    add_assoc_long(return_value, "life", 42);
    add_index_bool(return_value, 123, 1);
    add_next_index_double(return_value, 3.1415926535);

    /* 丢入一个静态字符串，由 PHP 复制 */
    add_next_index_string(return_value, "Foo", 1);

    /* 现在手动复制字符串 */
    add_next_index_string(return_value, "Bar", 0);

    /* 创建子数组 */
    array_ZVAL(subarray);
    array_init(subarray);

    /* 填充子数组 */
    add_assoc_long(subarray, "a", 10);

    /* 将子数组添加到主数组 */
    add_assoc_zval(return_value, "sub", subarray);
}
```

如果你 `var_dump()` 函数返回的数组，将得到类似的输出：

```
array(6) {
  ["life"]=> int(42)
  [123]=> bool(1)
  [0]=> float(3.1415926535)
  [1]=> string(Foo)
  [2]=> string(Bar)
  ["sub"]=> array(1) {
    ["a"]=> int(10)
  }
}
```

这些 `add_assoc_*()` 函数变体也可以用于内部属性。请在第 10 章查看“对象”。

### 总结

你刚刚花费了一个章节学习了 Zend Engine 和 PHP Core 中常见的结构之一。现在你已经有了足够的工具来实现大部分标准功能。在接下来的几章中，我们将通过探索资源和对象来完成剩余的 `zval` 数据类型。

## 第 9 章 数据类型

到目前，你处理的是相当原始的用户态数据类型。

### 复杂结构

在现实世界中，你通常需要处理更复杂的集合，通常涉及指向不透明结构的指针。不透明结构的一个常见例子是 `stdio` 文件描述符，它在 C 代码中看起来仅仅是一个指针。

```
#include <stdio.h>
int main(void)
{
    FILE *fd;
    fd = fopen(stdout);
    fclose(fd);
    return 0;
}
```

文件描述符的使用方式就像大多数文件描述符一样是一个书签。调用应用程序只需将此值传递给 `feof()`、`fread()`、`fwrite()`、`fclose()` 等实现函数。然而，在某些情况下，书签必须对用户态代码可见；因此有必要在标准的 PHP 变量 `zval*` 中表示它。

#### 定义资源类型

为了让注册的资源条目理解它们包含的资源，有必要对该资源类型进行声明。从在 `sample.c` 中现有的函数实现之后添加以下代码段开始：

```
static int le_sample_descriptor;

PHP_MINIT_FUNCTION(sample)
{
    le_sample_descriptor = zend_register_list_destructors_ex(
                NULL, NULL, PHP_SAMPLE_DESCRIPTOR_RES_NAME,
                module_number);
    return SUCCESS;
}
```

接下来，滚动到文件底部并修改 `sample_module_entry` 结构体，替换 `NULL, /* MINIT */` 这一行。就像你将函数列表添加到此结构体时一样，你想要确保在这一行的末尾保留一个逗号。

```php
PHP_MINIT(sample), /* MINIT */
```

最后，你需要在 `php_sample.h` 中定义 `PHP_SAMPLE_DESCRIPTOR_RES_NAME`，只需将该行放在你其他常量定义旁边：

```php
#define PHP_SAMPLE_DESCRIPTOR_RES_NAME "File Descriptor"
```

`PHP_MINIT_FUNCTION()` 代表了四个特殊启动和关闭操作中的第一个，你之前在 第 1 章“PHP 生命周期”中概念性地接触过这些操作，并且你将在 第 12 章“启动、关闭及中间的细节”以及 第 13 章“INI 设置”中对其进行更深入的探索。

此时需要重要的是，`MINIT` 方法在扩展首次加载且在接收到任何请求之前执行一次。在这里，你利用了该机会为 `NULL` 值注册了析构函数，你很快就会将其更改为资源类型，该类型之后将通过唯一的整数 ID 来标识。

### 注册资源

现在引擎已经知道你将存储一些资源数据，是时候给用户空间代码提供一种生成实际资源的方法了。为了实现这一点，请实现以下 `fopen()` 命令的重建：

```php
PHP_FUNCTION(sample_fopen)
{
    FILE *fp;
    char *filename, *mode;
    int filename_len, mode_len;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "ss",
                        &filename, &filename_len,
                        &mode, &mode_len) == FAILURE) {
        RETURN_NULL();
    }

    if (!filename_len || !mode_len) {
        php_error_docref(NULL TSRMLS_CC, E_WARNING,
                "Invalid filename or mode length");
        RETURN_FALSE;
    }

    fp = fopen(filename, mode);
    if (!fp) {
        php_error_docref(NULL TSRMLS_CC, E_WARNING,
                "Unable to open %s using mode %s",
                filename, mode);
        RETURN_FALSE;
    }

    ZEND_REGISTER_RESOURCE(return_value, fp,
                                le_sample_descriptor);
}
```

#### 注意

为了让编译器知道 `FILE*` 是什么，你需要包含 `stdio.h`。这可以存放在 `sample.c` 中，但为了本章后面的部分做准备，我要求你将其放在 `php_sample.h` 中。

如果你一直关注之前的章节，你将认识最后一行之前的所有内容。这条命令完成了将 `fp` 指针存储到资源索引中的工作，将其与 `MINIT` 期间声明的类型关联，并将查找键存储到 `return_value` 中。

#### 注意

如果有必要存储多个指针值，或者存储即时值，则必须分配一个新的内存段来存储数据，然后可以将该内存段的指针注册为资源。

### 销毁资源

此时，你已经有了一种方法将内部数据块附加到用户空间变量上。由于你可能附加到用户空间资源变量的大部分数据在某个时刻需要通过调用 `fclose()` 进行清理，在这种情况下，你可能假设需要一个匹配的 `sample_fclose()` 函数接收资源变量并处理它的销毁和注销。

但是，如果变量简单地被 `unset()` 了会发生什么？由于失去了对原始 `FILE*` 指针的引用，将无法对其进行 `fclose()`，它将保持打开状态直到 PHP 进程结束。由于一个进程服务于许多请求，这可能会花费很长时间。

答案来自于你传递给 `zend_register_list_destructors_ex` 的那些 `NULL` 指针。正如名称所示，你正在注册销毁方法。第一个指针指向一个在注册的资源的最后一个引用在请求中超出作用范围时调用的方法。在实践中，这通常意味着在存储资源的变量上调用了 `unset()`。

传递给 `zend_register_list_destructors_ex` 的第二个指针指向另一个回调方法，该方法会在进程或线程关闭时对持久资源执行。你将在本章稍后的部分查看持久资源。

让我们现在定义这些销毁方法中的第一个。将以下代码段放在你的 `PHP_MINIT_FUNCTION` 块上方：

```php
static void php_sample_descriptor_dtor(
                    zend_rsrc_list_entry *rsrc TSRMLS_DC)
{
    FILE *fp = (FILE*)rsrc->ptr;
    fclose(fp);
}
```



接下来，将`zend_register_list_destructors_ex`中的第一个`NULL`替换为指向`php_sample_descriptor_dtor`的引用：

```php
le_sample_descriptor = zend_register_list_destructors_ex(
        php_sample_descriptor_dtor, NULL,
        PHP_SAMPLE_DESCRIPTOR_RES_NAME, module_number);
```

现在，当变量赋值来自`sample_fopen()`的已注册资源值时，它知道当变量显式地通过`unset()`或隐式地在函数结束时超出作用范围时，会自动`fclose()` `FILE*`指针。甚至不需要`sample_fclose()`的实现！

```php
<?php
  $fp = sample_fopen("/home/jdoe/notes.txt", "r");
  unset($fp);
?>
```

当在此调用`unset($fp);`时，`php_sample_descriptor_dtor`会被调用。

### 解码资源

创建资源只是第一步，因为书签的有用性取决于其返回原始页的能力。这里有另一个函数：

```php
PHP_FUNCTION(sample_fwrite)
{
    FILE *fp;
    zval *file_resource;
    char *data;
    int data_len;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "rs",
            &file_resource, &data, &data_len) == FAILURE ) {
        RETURN_NULL();
    }

    /* 使用 zval* 验证资源类型
     * 从查找表中检索指针 */
    ZEND_FETCH_RESOURCE(fp, FILE*, &file_resource, -1,
        PHP_SAMPLE_DESCRIPTOR_RES_NAME, le_sample_descriptor);

    /* 写入数据，
     * 返回写入文件的字节数 */
    RETURN_LONG(fwrite(data, 1, data_len, fp));
}
```

在`zend_parse_parameters()`中使用`"r"`格式符是一个相对新的技巧，但根据你在第 7 章“接受参数”中所读的内容是可以理解的。真正新鲜的是`ZEND_FETCH_RESOURCE()`。

展开`ZEND_FETCH_RESOURCE()`宏可以发现：

```php
#define ZEND_FETCH_RESOURCE(rsrc, rsrc_type, passed_id,
            default_id, resource_type_name, resource_type)
    rsrc = (rsrc_type) zend_fetch_resource(passed_id TSRMLS_CC,
                    default_id, resource_type_name, NULL,
                    1, resource_type);
    ZEND_VERIFY_RESOURCE(rsrc);
```

或者在这种情况下：

```php
fp = (FILE*) zend_fetch_resource(&file_descriptor TSRMLS_CC, -1,
                    PHP_SAMPLE_DESCRIPTOR_RES_NAME, NULL,
                    1, le_sample_descriptor);
if (!fp) {
    RETURN_FALSE;
}
```

就像你在上一章中探索的`zend_hash_find()`方法一样，`zend_fetch_resource()`实际上使用集合（一个`HashTable`）中的索引来提取之前存储的数据。与`zend_hash_find()`不同，该方法执行额外的数据完整性检查，例如确保资源表中的项与正确的资源类型匹配。

在这种情况下，你要求`zend_fetch_resource()`匹配存储在`le_sample_descriptor`中的资源类型。如果提供的资源 ID 不存在或类型错误，则`zend_fetch_resource()`将返回`NULL`并自动生成错误。

通过在`ZEND_FETCH_RESOURCE()`宏中包含`ZEND_VERIFY_RESOURCE()`宏，函数实现可以自动返回，将扩展特定的代码留给在条件正确时处理生成的资源值。现在，你的函数已经拿回了原始的`FILE*`指针，它只需像任何普通程序一样调用内部的`fwrite()`方法即可。

## 提示

为了避免`zend_fetch_resource()`在失败时产生错误，只需为`resource_type_name`参数传递`NULL`即可。在没有可显示的有效错误信息的情况下，`zend_fetch_resource()`将静默失败。

将资源变量 ID 转换为指针的另一种方法是使用`zend_list_find()`函数：

```php
PHP_FUNCTION(sample_fwrite)
{
    FILE *fp;
    zval *file_resource;
    char *data;
    int data_len, rsrc_type;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "rs",
            &file_resource, &data, &data_len) == FAILURE ) {
        RETURN_NULL();
    }

    fp = (FILE*)zend_list_find(Z_RESVAL_P(file_resource),
                                        &rsrc_type);
    if (!fp || rsrc_type != le_sample_descriptor) {
        php_error_docref(NULL TSRMLS_CC, E_WARNING,
                        "Invalid resource provided");
        RETURN_FALSE;
    }

    RETURN_LONG(fwrite(data, 1, data_len, fp));
}
```

虽然这种方法对于具有通用 C 语言背景的人来说可能更容易识别，但它比使用`ZEND_FETCH_RESOURCE()`要冗长得多。选择一种最适合你编程风格的方法，但要预见到在其他扩展代码（如 PHP 核心）中会主要使用`ZEND_FETCH_RESOURCE()`宏。

### 强制销毁

之前你已经看到使用`unset()`将变量移出手范围可以触发资源的销毁，并导致你注册的销毁方法清理其底层资源。现在想象一下资源变量被复制到了其他变量中：

```php
<?php
  $fp = sample_fopen("/home/jdoe/world_domination.log", "a");
  $evil_log = $fp;
  unset($fp);
?>
```

这一次，`$fp`并不是已注册资源的唯一引用，因此它实际上还没有离开范围，也不会被销毁。这意味着`$evil_log`仍然可以被写入。为了避免在真正想要删除它时不得不四处寻找丢失的、散乱的资源引用，实现一个`sample_fclose()`变得非常有必要：

```php
PHP_FUNCTION(sample_fclose)
{
    FILE *fp;
    zval *file_resource;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "r",
                        &file_resource) == FAILURE ) {
        RETURN_NULL();
    }

    /* 虽然没有必要去实际获取
     * FILE* 资源，但执行获取提供了
     * 一个机会来验证我们正在关闭
     * 正确的资源类型。 */
    ZEND_FETCH_RESOURCE(fp, FILE*, &file_resource, -1,
        PHP_SAMPLE_DESCRIPTOR_RES_NAME, le_sample_descriptor);

    /* 强制资源进入自毁模式 */
    zend_hash_index_del(&EG(regular_list),
                    Z_RESVAL_P(file_resource));
    RETURN_TRUE;
}
```

这种删除方法强化了资源变量注册在全局`HashTable`中的事实。从此`HashTable`中移除资源条目只需使用资源 ID 作为索引在普通列表中进行简单查找。虽然其他直接操作`HashTable`的方法（如`zend_hash_index_find()`和`zend_hash_next_index_insert()`）可以替代`FETCH`和`REGISTER`宏，但在尽可能的情况下不建议这样做，以防 Zend API 的更改破坏现有的扩展。

与用户态变量`HashTables`（数组）一样，`EG(regular_list) HashTable`拥有一个自动的`dtor`方法，该方法每当条目被移除或覆盖时就会被调用。该方法检查你的资源类型，并在你在`MINIT`时调用`zend_register_list_destructors_ex()`时提供的你注册的销毁方法。

#### 注意

在 PHP 核心和 Zend 引擎的许多地方，你会看到在此上下文中使用`zend_list_delete()`而不是`zend_hash_index_del()`。`zend_list_delete()`形式考虑了引用计数，你将在本章后面看到它。

### 持久资源

通常存储在资源变量中的复杂数据结构类型需要大量的内存分配、CPU 时间或网络通信来初始化。在脚本极可能需要在每次调用时重新建立此类资源（例如数据库连接）的情况下，在请求之间保留资源将变得非常有用。

### 内存分配

通过前面章节的接触，你知道在 PHP 中分配内存时，`emalloc()`等函数是首选的函数，因为如果脚本必须意外退出，它们能够进行垃圾回收，而系统`malloc()`函数简单地无法做到。然而，如果一个持久资源要在请求之间保持存，那么这种垃圾回收显然不是一件好事。

想象一下，如果需要存储打开的文件名称以及`FILE*`指针。现在你需要在`php.h`中创建一个自定义结构体来存储这些信息：

```c
typedef struct _descriptor_data {
    char *filename;
    FILE *fp;
} descriptor_data;
```

并且`sample.c`中处理资源的所有函数都需要修改：

```c
static void sample_dtor(zend_list_entry *rsrc TSRMLS_DC)
{
    descriptor_data *fdata = (descriptor_data*)rsrc->ptr;
    fclose(fdata->fp);
    efree(fdata->filename);
    efree(fdata);
}

PHP_FUNCTION(sample_fopen)
{
    descriptor_data *fdata;
    FILE *fp;
    char *filename, *mode;
    int filename_len, mode_len;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "ss",
                        &filename, &filename_len,
                        &mode, &mode_len) == FAILURE) {
        RETURN_NULL();
    }

    if (!filename_len || !mode_len) {
        php_error_docref(NULL TSRMLS_CC, E_WARNING,
                "Invalid filename or mode");
        RETURN_FALSE;
    }

    fp = fopen(filename, mode);
    if (!fp) {
        php_error_docref(NULL TSRMLS_CC, E_WARNING,
                "Unable to open %s using mode %s",
                filename, mode);
        RETURN_FALSE;
    }

    fdata = emalloc(sizeof(descriptor_data));
    fdata->fp = fp;
    fdata->filename = strndup(filename, filename_len);
    ZEND_REGISTER_RESOURCE(return_value, fdata,
                                le_sample_descriptor);
}

PHP_FUNCTION(sample_fwrite)
{
    descriptor_data *fdata;
    zval *file_resource;
    char *data;
    int data_len;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "rs",
            &file_resource, &data, &data_len) == FAILURE ) {
        RETURN_NULL();
    }

    ZEND_FETCH_RESOURCE(fdata, descriptor_data*,
        &file_resource, -1,
        PHP_SAMPLE_DESCRIPTOR_RES_NAME, le_sample_descriptor);

    RETURN_LONG(fwrite(data, 1, data_len, fdata->fp));
}
```

#### 注意

从技术上讲，`sample_fclose()`可以保持原样，因为并并不直接处理资源数据。如果你有信心，可以尝试自己更新它。

到目前为止，一切正常，因为你仍然只注册了非持久的描述符资源。你甚至可以添加一个新函数，从资源中提取原始的文件名：

```php
PHP_FUNCTION(sample_fname)
{
    php_sample_descriptor_data *fdata;
    zval *file_resource;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "r",
            &file_resource) == FAILURE ) {
        RETURN_NULL();
    }

    ZEND_FETCH_RESOURCE(fdata, php_sample_descriptor_data*,
        &file_resource, -1,
        PHP_SAMPLE_DESCRIPTOR_RES_NAME, le_sample_descriptor);

    RETURN_STRING(fdata->filename, 1);
}
```



然而，当你开始注册描述符资源的持久化版本时，像这样的用法很快就会开始出现问题。

### 延迟销毁 (Delayed Destruction)

正如你在非持久化资源中所看到的，一旦所有持有资源 ID 的变量被`unset()`或超出了作用域，它们就会从`EG(regular_list)`中移除，该列表是包含所有每个请求注册资源的`HashTable`。

正如你将在本章的稍后部分看到的，持久化资源也存储在第二个`HashTable`中：`EG(persistent_list)`。与`EG(regular_list)`不同，此表使用的索引是关联的，且元素不会在请求结束时自动从`HashTable`中移除。`EG(persistent_list)`中的项只有通过手动调用`zend_hash_del()`（你很快就会看到）或在线程或进程完全关闭（通常是 Web 服务器停止时）时才会移除。

与`EG(regular_list)` HashTable一样，`EG(persistent_list)` HashTable也有自己的`dtor`方法。与列表一样，该方法也是一个简单的封装，使用资源的类型来查找适当的销毁方法。这次，它获取的是`zend_register_list_destructors_ex()`第二参数中的销毁方法，而不是第一个。

在实践中，持久性和非持久化资源通常被注册为两种不同的类型，以避免非持久化的销毁代码运行在应该是持久化的资源上。根据你的实现，你可以选择将非持久化和持久化的销毁方法合并到一个类型中。现在，在`sample.c`顶部添加另一个静态`int`用于新的持久化描述符资源：

```c
static int le_sample_descriptor_persist;
```

然后，扩展你的`MINIT`函数，注册一个使用专门针对持久分配结构的新`dtor`函数的资源：

```c
static void php_sample_descriptor_dtor_persistent(
                    zend_rsrc_list_entry *rsrc TSRMLS_DC)
{
    php_sample_descriptor_data *fdata =
                (php_sample_descriptor_data*)rsrc->ptr;
    fclose(fdata->fp);
    pefree(fdata->filename, 1);
    pefree(fdata, 1);
}

PHP_MINIT_FUNCTION(sample)
{
    le_sample_descriptor =     zend_register_list_destructors_ex(
            php_sample_descriptor_dtor, NULL,
            PHP_SAMPLE_DESCRIPTOR_RES_NAME, module_number);
    le_sample_descriptor_persist =
                        zend_register_list_destructors_ex(
            NULL,
            PHP_SAMPLE_DESCRIPTOR_RES_NAME, module_number);
    return SUCCESS;
}
```

通过给这两个类型相同的名称，这种区别对用户来说是透明的。这次新出的是第二部分，但希望它并不完全陌生。

在这里，你实际上执行了与`ZEND_RESOURCE()`执行非常相似的操作；然而，你并没有给它一个数字索引并将其放入请求列表，而是为它分配了一个关联键，该键可以在后续的请求中重建并存储到持久化列表中，而该列表不会在每个脚本结束时自动清理。

### 长期注册 (Long Term Registration)

现在有了合适的方法，是时候实际创建一些可用的结构了。这通常使用单独函数完成，但你在这里会看到：

```php
PHP_FUNCTION(sample_fopen)
{
    php_sample_descriptor_data *fdata;
    FILE *fp;
    char *filename, *mode;
    int filename_len, mode_len;
    bool persist = 0;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "ss|b",
            &filename, &mode, &persist) == FAILURE) {
        RETURN_NULL();
    }

    if (!filename || !mode) {
        zend_error(E_WARNING, "Invalid filename or mode");
        RETURN_FALSE;
    }

    fp = fopen(filename, mode);
    if (!fp) {
        zend_error(E_WARNING, "Unable to open %s", filename);
        RETURN_FALSE;
    }

    filename_len = strlen(filename);
    if (!persist) {
        fdata = emalloc(sizeof(php_sample_descriptor_data));
        fdata->filename = strndup(filename, filename_len);
        fdata->fp = fp;
        ZEND_ADRESOURCE(le_sample_descriptor);
    } else {
        list_entry le;
        char *hash_key;
        int hash_key_len;

        fdata = pemalloc(sizeof(php_sample_descriptor_data));
        fdata->filename = strndup(filename, filename_len);
        fdata->fp = fp;

        /* 在 persistent_list 中存储一个副本 */
        le.type = le_sample_descriptor_persist;
        le.ptr = fdata;
        hash_key_len = sprintf(&hash_key, "sample_descriptor:%s:%s", filename, mode);
        zend_hash_update(&EG(persistent_list),
            hash_key, hash_key_len,
            (void*)&le, sizeof(list_entry), NULL);
        efree(hash_key);
    }

    return SUCCESS;
}
```

该函数的内核部分现在应该非常熟悉了。一个文件被打开了，它的名称被存储在新分配的内存中，并注册到一个填充了`return_value`的资源 ID 中。这次新出的是第二部分，但希望它并不完全陌生。

### 重用 (Reuse)

将资源项的副本放入`persistent_list`中，除了能够延长此类资源占用内存和文件锁的时间之外，否则你能以某种方式在后续请求中重用它们。

这就是那个`hash_key`发挥作用的地方。当调用`sample_fopen()`时，无论是为了持久化还是非持久化使用，你的函数都可以使用请求的文件和模式重新创建`hash_key`，并在费力重新打开文件之前尝试在`persistent_list`中查找它：

### 其他`refcounter`

与用户空间变量一样，注册资源也有引用计数器。在这里，引用计数器指的是有多少容器结构知道相关的资源 ID。

你现在已经知道，当用户空间变量（`zval*`）的类型为`IS_RESOURCE`时，它并没有真正持有任何结构的指针；它仅持有一个 HashTable 索引数字，以便从`EG(regular_list)` HashTable中查找该指针。

当资源被首次创建时（例如通过调用`sample_fopen()`），它被放入一个`zval*`容器中，其`refcount`被初始化为 1，因为它只被这一个变量持有。

```php
$a = sample_fopen('notes.txt', 'r');
/* var->refcount = 1, rsrc->refcount = 1 */
```

如果随后将该变量复制到另一个变量，你从第 3 章“内存管理”中知道，并没有创建新的`zval*`。相反，这些变量在写时复制引用集中共享该`zval*`。在这种情况下，`zval*`的`refcount`增加到 2；然而，资源的`refcount`仍然为 1，因为它只被一个`zval*`持有。

```php
$b = $a;
/* var->refcount = 2, rsrc->refcount = 1 */
```

当这两个变量中的一个被`unset()`时，`zval*`的`refcount`会递减，但它不会被销毁，因为另一个变量仍然引用着它。

```php
unset($b);
/* var->refcount = 1, rsrc->refcount = 1 */
```

你现在也知道，将全引用集与写时复制引用集混合将强制变量通过复制到新的`zval*`来实现分离开。当这种情况发生时，资源的引用计数确实会增加，因为它现在被第二个`zval*`拥有了。

```php
$b = $a;
$c = &$a;
/* bvar->refcount = 1, bvar->is_ref = 0
   acvar->refcount = 2, acvar->is_ref = 1
   rsrc->refcount = 2 */
```

现在，取消`$b`将完全销毁它的`zval*`，将`rsrc->refcount`带回 1。然而，取消`$a`或`$c`而不是两者都，都不会减少资源的引用计数，因为`acvar`、`zval*`仍然存在。直到所有三个变量（并由此及它们的两个`zval*`）都被`unset()`了，资源的引用计数才会达到 0 并触发其销毁。

### 总结

通过本章涵盖的主题，你可以开始应用 PHP 闻为闻名的“胶水”。资源（resource）使你的扩展能够将第三方库的不透明指针等抽象概念连接到让 PHP 如此强大的易用脚本语言。

在接下来的两个章节中，你将深入研究 PHP 词汇表中最后一个但绝非最不的部分。你将从探索简单的 Zend Engine 1 类开始，然后转向它们更强大的 Zend Engine 2 继任者。

## 第 10 章. PHP4 对象

**很久以前**，PHP 并不支持任何形式的面向对象编程。随着 PHP4 引入了 Zend Engine (ZE1)，几个新特性随之出现。

### PHP 对象的演变

面向对象编程 (OOP) 的首次化身仅涵盖了对象相关特性的裸实现。正如一位核心开发者所说：“一个 PHP4 对象只是在侧面挂载了某些函数的数组。这也就是你现在将探索的这一代对象。”

随着 PHP5 中 Zend Engine (ZE2) 的第二次重大发布，一些新特性被引入了 PHP 的实现中。例如，属性和方法现在可以被标记为访问修饰符，以确保从类定义外部无法访问它们。

### 实现类

当你开始探索 OOP 的世界时，是时候摆掉在此章节中积累的一些负担了。为了做到这一点，请“重置”回到你在第 5 章中开始的骨架。

为了将其与你之前的化身一起编译，你可以将此版本命名为`sample2`。将列表 10.1 到 10.3 所示的三个文件放在 PHP 源码树的`ext/sample2/`中。

#### 列表 10.1. ：`config.m4`

```php
PHP_ARG_ENABLE(sample2,
  [是否启用 "sample2" 扩展],
  [enable-sample2 extension support])

if test $PHP_SAMPLE2 != "no"; then
  PHP_SUBST(SAMPLE2_SHARED_LIBADD)
  PHP_NEW_EXTENSION(sample2, sample2.c, $ext_shared)
fi
```

#### 列表 10.2. 头文件：`php_sample2.h`

```php
#ifndef PHP_SAMPLE2_H
/* 防止重复包含 */
#define PHP_SAMPLE2_H

/* 定义扩展属性 */
#define PHP_SAMPLE2_EXTNAME    "sample2"
#define PHP_SAMPLE2_EXTVER    "1.0"

/* 配置选项
   当在 PHP 源码树
   之外构建时 */
#ifdef HAVE_CONFIG_H
#include "config.h"
#endif

/*  PHP 标准头文件 */
#include "php.h"

/* 定义入口点符号
 * Zend 在加载此模块时将使用 */
extern zend_module_entry sample2_module_entry;
#define phpext_sample2_ptr &sample2_module_entry

#endif /* PHP_SAMPLE2_H */
```

#### 列表 10.3. 源码：`sample2.c`

```php
#include "php_sample2.h"

static function_entry php_sample2_functions[] = {
    { NULL, NULL, NULL }
};

PHP_MINIT_FUNCTION(sample2)
{
    return SUCCESS;
}

zend_module_entry sample2_module_entry = {
#if ZEND_MODULE_API_NO >= 20010901
    STANDARD_MODULE_HEADER,
#endif
    PHP_SAMPLE2_EXTNAME,
    php_sample2_functions,
    PHP_MINIT(sample2),
    NULL, /* MSHUTDOWN */
    NULL, /* RINIT */
    NULL, /* RSHUTDOWN */
    NULL, /* MINFO */
#if ZEND_MODULE_API_NO >= 20010901
    PHP_SAMPLE2_EXTVER,
#endif
    STANDARD_MODULE_PROPERTIES
};

#ifdef COMPILE_DL_SAMPLE2
ZEND_GET_MODULE(sample2)
#endif
```

现在，就像你在第 5 章中所做一样，你可以执行`phpize`、`./configure`和`make`来构建你的`sample2.so`扩展模块。

**注意**

与`config.m4`一样，你之前的`sample2`版本在这里不需要额外操作即可工作。

#### 声明类条目

在用户空间，定义类的第一步是声明它。例如：

```php
<?php
class Sample2_FirstClass {
}
?>
```

正如你所料到的，在扩展内部这样做会变得稍微复杂。首先，你需要在源文件中定义一个`zend_class_entry`指针，就像你在上一章定义的那样：

```php
zend_class_entry *php_sample2_firstclass_entry;
```

现在，你可以在`MINIT`方法中初始化并注册该类：

```php
PHP_MINIT_FUNCTION(sample2)
{
    zend_class_entry ce; /* 临时变量 */

    /* 注册类 */
    INIT_CLASS_ENTRY(ce, "Sample2_FirstClass", NULL);
    php_sample2_firstclass_entry =
            zend_register_internal_class(&ce);

    return SUCCESS;
}
```

#### 方法实现

目前，你只实现了`stdClass`，它当然已经可用了。你现在希望你的类能做些什么。

为了实现这一点，你将再次回到第 5 章中学到的另一个概念。将`INIT_CLASS_ENTRY()`的`NULL`参数替换为`php_sample2_firstclass_functions`，并在`MINIT`方法上方直接定义该结构体如下：

```php
static function_entry php_sample2_firstclass_functions[] = {
    { NULL, NULL, NULL }
};
```

```php
PHP_NAMED_FE(method1, PHP_FN(Sample2_FirstClass_method1), NULL)
```



或者，你也可以使用 `PHP_FE(method1, NULL)`。然而，正如你在第 5 章中所回顾的，这期望找到一个名为 `zif_method1` 的实现函数，这可能会与其它地方的 `method1()` 实现产生冲突。为了安全地将函数与任何过程化实现隔离，会将类名附加在方法名之前，其中类名采用首字母大写（drop cap-casing），方法名采用驼峰命名（camel-casing）。

`PHP_FALIAS(method1, Sample2_FirstClass_method1, NULL)` 形式也是接受的；不过，当你以后回来查看并疑惑为什么没有匹配的 `PHP_FE()` 行时，它可能显得没那么直观。

现在你已经为类定义挂载了函数列表，是时候声明一些方法了。在 `php_sample2_firstclass_functions` 结构体上方创建以下函数：

```
PHP_FUNCTION(Sample2_FirstClass_countProps)
{
    RETURN_LONG(zend_hash_num_elements(Z_OBJPROP_P(getThis())));
}
```

现在在函数列表本身添加一个匹配的 `PHP_NAMED_FE()` 条目：

```
static function_entry php_sample2_firstclass_functions[] = {
    PHP_NAMED_FE(countprops,
            PHP_FN(Sample2_FirstClass_countProps), NULL)
    { NULL, NULL, NULL }
};
```

## 注意事项

务必注意，用于用户空间的函数名称全为全小写。为了确保方法和函数名不区分大小写的大写转换操作，要求内部函数必须赋予全小写的名称。

这里唯一的新元素应该是 `getThis()`，在所有当前的 PHP 版本中，它实际上是一个被解析为 `this_ptr` 的宏。而 `this_ptr` 质携带的含义与用户空间对象方法中的 `$this` 基本相同。如果没有可用的对象实例（例如在静态调用方法时），`getThis()` 将返回 `NULL`。

正如对象方法中的数据返回语义与过程函数相同一样，参数接收和 `arg_info` 方法论也是如此：

```
PHP_FUNCTION(Sample2_FirstClass_sayHello)
{
    char *name;
    int name_len;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "s",
                        &name, &name_len) == FAILURE) {
        RETURN_NULL();
    }

    php_printf("Hello");
    PHPWRITE(name, name_len);
    php_printf("!\nYou called an object method!\n");
    RETURN_TRUE;
}
```

### 构造函数

你的类构造函数可以简单地实现为任何其他普通类方法，在命名方面，相同的规则既适用于内部，也适用于用户空间。具体来说，你希望你的构造函数命名与类名完全相同。其他的 ZE1 魔法方法 `__sleep()` 和 `__wakeup()` 也可以以这种方式实现。

### 继承

PHP4 中内部对象之间的继承充其量是不可靠的，通常应该像避开恐怖片中的黑暗小巷一样避免它。如果你绝对必须继承另一个对象，你需要复制一些 ZE1 代码：

```
void php_sample2_inherit_from_class(zend_class_entry *ce,
                        zend_class_entry *parent_ce) {
    zend_hash_merge(&ce->function_table,
            &parent_ce->function_table, (void (*)(void *))function_add_ref,
            NULL, sizeof(zval*), 0);
    ce->parent = parent_ce;

    if (!ce->handle_property_get) {
        ce->handle_property_get =
                parent_ce->handle_property_get;
    }

    if (!ce->handle_property_set) {
        ce->handle_property_set =
                parent_ce->handle_property_set;
    }

    if (!ce->handle_call) {
        ce->handle_call =
                parent_ce->handle_call;
    }
}
```

在定义了这个函数后，你现在可以在 `MINIT` 块中在 `zend_register_class` 之后调用它：

```
INIT_CLASS_ENTRY(ce, "Sample2_FirstClass", NULL);
/* 假设 php_sample2_ancestor 是已经注册的 zend_class_entry */
php_sample2_inherit_from_class(ce, php_sample2_ancestor);
```

#### 注意

尽管这种继承方法可行，但通常应该被避免，因为 ZE1 根本没有设计用于处理继承。

#### 操作实例

像用户空间变量一样，对象存储在 `zval*` 容器中。在 ZE1 中，`zval*` 包含一个属性 `HashTable*` 和一个指向类定义的 `zend_class_entry*`。在 ZE2 中，这些值被一个处理表（我们将在下一章深入探讨）和一个与资源 ID（参见第 9 章，“资源数据类型”）使用方式类似的对象 ID 所取代。

ZE1 对象和 ZE2 对象之间的这种差异幸运地通过 `Z_*()` 宏族对你的扩展隐藏了，这个宏族是你在第 2 章“从内部向外变量”中就已经看到的。表 10.1 列出了两个 ZE1 宏，它们与非 OOP 相关的亲戚一样，具有处理一级和二级间接的 `_P` 和 `_PP` 变体。

#### 表 10.1. 对象访问宏

| 宏 | 目的 |
| --- | --- |
| `Z_OBJPROP(zv)` | 解析内置属性 `HashTable*` |
| `Z_OBJCE(zv)` | 返回关联的 `zend_class_entry*` |

```
PHP_FUNCTION(sample2_new)
{
    int argc = ZEND_NUM_ARGS();
    zval ***argv = safe_emalloc(sizeof(zval**), argc, 0);
    zend_class_entry *ce;

    if (argc == 0 ||
        zend_get_parameters_array_ex(argc, argv) == FAILURE) {
        efree(argv);
        WRONG_PARAM_COUNT;
    }

    /* First arg is classname */
    SEPARATE_ZVAL(argv[0]);
    convert_to_string(*argv[0]);

    /* class names are stored in lowercase */
    php_strtolower(Z_STRVAL_PP(argv[0]), Z_STRLEN_PP(argv[0]));

    if (zend_hash_find(EG(class_table),
            Z_STRVAL_PP(argv[0]), Z_STRLEN_PP(argv[0]) + 1,
            (void**)&ce) == FAILURE) {
        php_error_docref(NULL TSRMLS_CC, E_WARNING,
            "Class %s does not exist.",
            Z_STRVAL_PP(argv[0]));
        zval_ptr_dtor(argv[0]);
        efree(argv);
        RETURN_FALSE;
    }

    object_init_ex(return_value, ce);

    /* Call the constructor if it has one
     * Additional arguments will be passed through as
     * constructor parameters */
    if (zend_hash_exists(&ce->function_table,
            Z_STRVAL_PP(argv[0]),Z_STRLEN_PP(argv[0]) + 1)) {
        /* Object has constructor */
        zval *ctor, *dummy = NULL;

        /* constructor == classname */
        MAKE_STD_ZVAL(ctor);
        array_init(ctor);
        zval_add_ref(argv[0]);
        add_next_index_zval(ctor, *argv[0]);
        zval_add_ref(argv[0]);
        add_next_index_zval(ctor, *argv[0]);

        if (call_user_function_ex(&ce->function_table,
                NULL, ctor,
                &dummy, /* Don't care about return value */
                argc - 1, argv + 1, /* parameters */
                0, NULL TSRMLS_CC) == FAILURE) {
            php_error_docref(NULL TSRMLS_CC, E_WARNING,
                 "Unable to call constructor");
        }

        if (dummy) {
            zval_ptr_dtor(&dummy);
        }
        zval_ptr_dtor(&ctor);
    }

    zval_ptr_dtor(argv[0]);
    efree(argv);
}
```

不要忘记在 `php_sample2_functions` 中对其添加引用。那是你扩展的程序化函数列表，而不是你类的方法列表。你还需要添加 `#include "ext/standard/php_string.h"` 以获取 `php_strtolower()` 函数的原型。

该函数是你实现的函数之一是将类名转换为小写，因为 PHP 中所有类名和函数名都是以这种方式存储的，以实现大小写不敏感。这只是你在附录 B 中可以找到许多实用函数之一。

`EG(class_table)` 是所有请求可用的 `zend_class_entry` 定义的全局注册表。注意，在 ZE1(PHP4) 中，它在单级间接层存储 `zend_class_entry*` 结构。在 ZE2(PHP5) 中，这些存储在双级间接层。这不应该是一个问题，因为直接访问此表是不常见的任务，但你最好意识到这一点。

`call_user_function_ex()` 是你将在第 2 章中查看的对对之一。在这里，你通过 `zend_get_parameters_array_ex()` 从栈上获取的内容向前移动了一个 `zval**`，以便原封不动地传递剩余参数。

### 接收实例

通常，你需要你的函数或方法接受来自用户空间的对象。为了此目的，`zend_parse_parameters()` 提供了格式说明符。第一个是 `o`（小写字母），它将验证参数是否为对象并填充到传递的 `zval**` 中。这种类型的简单用法可以是下面的用户空间函数，它可以返回传递的任何对象的类名：

```
PHP_FUNCTION(sample2_classname)
{
    zval *objvar;
    zend_class_entry *ce;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "o", &objvar) == FAILURE) {
        RETURN_NULL();
    }

    ce = Z_OBJCE_P(objvar);
    RETURN_STRINGL(ce->name, ce->name_length, 1);
}
```

用于对象的第二个格式说明符 `O`（大写字母）允许 `zend_parse_parameters()` 不仅验证 `zval*` 类型，还验证类类型。为了此目的，假设你有一个 `Sample2_Class` 实例，以下代码将获取该属性：

```
PHP_FUNCTION(reload)
{
    zval *objvar;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "O", &objvar) == FAILURE) {
        return
    }

    /* 占位符 */
    RETURN_BOOL(1);
}
```

### 访问属性

通常，你需要你的函数或方法接受来自用户空间的对象。为了此目的，`zend_parse_parameters()` 提供了格式说明符。第一个是 `o`（小写字母），它将验证参数是否为对象并填充到传递的 `zval**` 中。

访问属性

正如你所见，类方法通过 `getThis()` 访问当前对象。使用你在第 8 章中学习的 `zend_hash` API 获取并设置属性：

```
zval **fooval;

if (zend_hash_find(Z_OBJPROP_P(rcvdclass), "foo", sizeof("foo"), (void**)&fooval) == FAILURE) {
    /* $rcvdclass->foo 不存在 */
    return;
}
```

要在属性表中添加元素，只需反转此过程并调用 `zend_hash_add()`，在处理对象时将 `assoc` 一词替换为 `property`。

以下构造函数方法为 `Sample2_Class` 实例提供一组预定义的默认属性：

```
PHP_NAMED_FUNCTION(php_sample2_fc_ctor)
{
    /* 为了简洁，并为了说明可以使用任意函数名，
     这次名称是手动分配的 */
    zval *objvar = getThis();

    if (!objvar) {
        php_error_docref(NULL TSRMLS_CC, E_WARNING, "静态调用构造函数!");
        RETURN_FALSE;
    }

    add_property_long(objvar, "life", 42);
    add_property_double(objvar, "pi", 3.1415926535);
    /* 构造函数的返回值是无关的 */
}
```

构造函数可以通过 `php_sample2_firstclass_functions` 列表链接到对象：

```
PHP_NAMED_FE(sample2_firstclass, php_sample2_fc_ctor, NULL)
```



### 总结

尽管`ZE1 / PHP4`类提供的功能有限，但它们具有与目前环境中广泛安装的`PHP4`基兼容的优势。本章涵盖的简单技术允许你编写今天可以运行并在明天继续工作的功能、通用代码。

在下一章中，你将发现围绕`PHP5`的热点究竟是什么，以及为什么如果你想要`OOP`功能，你将找到一个升级且永不回头的理由。

将`PHP5`对象与其`PHP4`祖先进行比较是非常不公平的；然而，许多配合`PHP5`对象使用的`API`函数都是为了符合`PHP4 API`而构建的。如果你读过第 10 章“`PHP4`对象”，那么你会发现这里的内容有些熟悉。在开始本章之前，请从第 10 章获取骨架文件，并将`sample2`重命名为`sample3`，这样你就能从一个干净的扩展源码开始。

### 演进飞跃

`PHP5`对象变量有两个关键组件。第一个是数字标识符，它类似于第 9 章“资源数据类型”中找到数字资源`ID`，充当整个请求范围内对象实例表的查找索引。该实例表中的元素包含指向类条和内部属性表的引用，以及其他特定于实例的信息。

对象变量中的第二个元素是处理表（handler table），它能够自定义`Zend`与实例交互的方式。你将在本章稍后的部分查看处理表。

### `zend_class_entry`

类条目是你在用户空间中声明类定义的内部表示。正如你在上一章中看到的，该结构通过调用`INIT_CLASS_ENTRY()`进行初始化，并传入类名和其函数表，然后在`MINIT`阶段通过`zend_register_internal_class()`进行注册：

```c
zend_class_entry *php_sample3_sc_entry;

#define PHP_SAMPLE3_SC_NAME "Sample3_SecondClass"

static function_entry php_sample3_sc_functions[] = {
    { NULL, NULL, NULL }
};

PHP_MINIT_FUNCTION(sample3)
{
    zend_class_entry ce;

    INIT_CLASS_ENTRY(ce, PHP_SAMPLE3_SC_NAME,
                            php_sample3_sc_functions);
    php_sample3_sc_entry =
                zend_register_internal_class(&ce TSRMLS_CC);
    return SUCCESS;
}
```

### 方法

如果你确实读了上一章，你可能开始想：“到目前为止一切看起来都差不多”，到目前为止你是对的。现在是时候声明一些对象方法了。然而，你将开始看到非常明确且深受欢迎的差异。

```c
PHP_METHOD(Sample3_SecondClass, helloWorld)
{
    php_printf("Hello World\n");
}
```

`PHP_METHOD()`宏随`Zend Engine`版本 2 引入，它封装了`PHP_FUNCTION()`宏，通过将类名与方法名结合，就像你之前手动为`PHP4`方法声明时操作的那样。通过使用此宏，可以保持扩展与代码之间命名规范的一致，并且代码更容易被其他维护者解析。

#### 声明

定义方法实现与其他任何函数一样，只有当通过类条目的函数表链接到用户空间时才有用。与用于实现的`PHP_METHOD()`宏一样，在函数列表中也也有用于声明的新型宏：

*   `PHP_ME(classname, methodname, arg_info, flags)`

    `PHP_ME()`在第 5 章“你的第一个扩展”中的`PHP_FE()`宏基础上添加了类名部分，并在结尾添加了一个新参数，提供访问控制修饰符，如`public`、`protected`、`private`、`static`、`abstract`以及其他选项。要声明你刚刚定义的`helloWorld`方法，你可以使用如下条目：

    ```c
    PHP_ME(Sample3_SecondClass, helloWorld, NULL, ZEND_ACC_PUBLIC)
    ```

*   `PHP_MALIAS(classname, name, alias, arg_info, flags)`

    就像`PHP_FALIAS()`宏一样，此声明允许你将`name`参数提供的新名分配给同一类的现有方法实现（由`alias`指定）。例如，给你的`helloWorld`方法一个重名，你可能使用：

    ```c
    PHP_MALIAS(Sample3_SecondClass, helloWorld, NULL, ZEND_ACC_PUBLIC)
    ```

*   `PHP_ABSTRACT(classname, methodname, arg_info)`

    抽象方法不是真正的实现。在调用它之前，当前方法应该被子类重写。

    ```c
    PHP_ABSTRACT(Sample3_SecondClass, helloWorld, NULL, ZEND_ACC_PUBLIC)
    ```

*   `PHP_FINAL(classname, methodname, arg_info)`

    方法不能被子类重写。

    ```c
    PHP_FINAL(Sample3_SecondClass, helloWorld, NULL, ZEND_ACC_PUBLIC)
    ```

*   `PHP_ME_MAPPING(classname, methodname, arg_info)`

    这种即使通过实例调用，`this`也不会填充实例作用域。

    ```c
    PHP_ME_MAPPING(Sample3_SecondClass, helloWorld, NULL)
    ```

### 魔术方法 (Magic Methods)

| `__clone()` | 默认情况下，所有实例都以真实引用的方式传递。然而，从`PHP5`开始，可以使用`clone`关键字显式地复制实例。当在对象实例上调用`clone`时，会隐式地调用`__clone()`方法，允许对象根据需要复制其任何内部资源。 |
| `__toString()` | 当将实例表示为文本对象时（例如使用`echo`或`print`语句时），引擎会自动调用`__toString()`方法。实现此魔术方法的类应该返回一个包含对象当前状态表示的字符串。 |
| `__get($var)` | 如果脚本从对象实例中请求一个属性，而该属性既不在标准属性表中不存在，又被声明为非公有（`non-public`），则会调用`__get()`魔术方法，并将属性名作为唯一参数传递。实现类可以使用其自身的内部逻辑来决定提供最合理的返回值。 |
| `__set($var, $value)` | 与`__get()`类似，`__set()`在当被赋值的变量不在标准属性表中或被声明为非公有时，提供了处理变量赋值的机会。`__set()`的实现可以选择在标准属性表中隐式创建这些变量、在其他存储机制中设置值，或简单地抛出错误并丢弃该值。 |
| `__call($fname, $args)` | 在对象上调用未定义的方法可以通过使用`__call()`魔术方法实现优雅地处理。该方法接收两个参数：正在调用的方法名，以及一个包含传递给该方法的参数的数字索引数组。 |
| `__isset($varname)` | 从`PHP 5.1.0`开始，对`isset($obj->prop)`的调用不仅会检查`$obj`中是否存在`prop`属性，还会调用`$obj`内部任何定义的`__isset()`方法，以根据动态的`__get()`和`__set()`方法动态评估读取或写入该属性的尝试是否会成功。 |
| `__unset($varname)` | 与`__isset()`类似，`PHP 5.1.0`为`unset()`函数引入了简单的`OOP`接口，用于属性。这些属性虽然在对象的标准属性表中不存在，但在`__get()`和`__set()`动态属性空间内可能具有意义。 |

#### 注意

额外的魔术方法功能可以通过某些接口提供，例如`ArrayAccess`接口以及多个`SPL`接口。

在内部对象实现中，这些特殊的“魔术方法”中的每一个都可以通过定义一个带有正确名称和`PUBLIC`访问修饰符的`PHP_ME()`行，实现为对象中的任何其他方法。对于需要传递精确参数数量的`__get()`、`__set()`、`__call()`、`__isset()`和`__unset()`，你必须定义适当的`arg_info`结构体，说明该方法恰好接收 1 或 2 个参数。以下代码段显示了每个魔术方法对应的`arg_info`结构体及其对应的`PHP_ME()`条目：

```c
static
    ZEND_BEGIN_ARG_INFO_EX(php_sample3_one_arg, 0, 0, 1)
    ZEND_END_ARG_INFO()

static
    ZEND_BEGIN_ARG_INFO_EX(php_sample3_two_args, 0, 0, 2)
    ZEND_END_ARG_INFO()

static function_entry php_sample3_sc_functions[] = {
    PHP_ME(Sample3_SecondClass, __construct, NULL,
                        ZEND_ACC_PUBLIC|ZEND_ACC_CTOR)
    PHP_ME(Sample3_SecondClass, __destruct, NULL,
                        ZEND_ACC_PUBLIC|ZEND_ACC_DTOR)
    PHP_ME(Sample3_SecondClass, __clone, NULL,
                        ZEND_ACC_PUBLIC)
    PHP_ME(Sample3_SecondClass, __toString, NULL,
                        ZEND_ACC_PUBLIC)
    PHP_ME(Sample3_SecondClass, __get, NULL,
                        ZEND_ACC_PUBLIC)
    PHP_ME(Sample3_SecondClass, __set, NULL,
                        ZEND_ACC_PUBLIC)
    PHP_ME(Sample3_SecondClass, __call, NULL,
                        ZEND_ACC_PUBLIC)
    PHP_ME(Sample3_SecondClass, __isset, NULL,
                        ZEND_ACC_PUBLIC)
    PHP_ME(Sample3_SecondClass, __unset, NULL,
                        ZEND_ACC_PUBLIC)
};
```

```c
void php_sample3_register_constants(zend_class_entry *ce)
{
    zval *constval;

    /* Basic scalar values can use Z_*() to set their value */
    constval = pemalloc(sizeof(zval), 1);
    INIT_PZVAL(constval);
    ZVAL_DOUBLE(constval, 2.7182818284);
    zend_hash_add(&ce->constants_table, "E", sizeof("E"),
                    (void*)&constval, sizeof(zval*), NULL);

    /* Strings require additional mallocs */
    constval = pemalloc(sizeof(zval), 1);
    INIT_PZVAL(constval);
    Z_TYPE_P(constval) = IS_STRING;
    Z_STRLEN_P(constval) = sizeof("Hello World") - 1;
    Z_STRVAL_P(constval) = pemalloc(Z_STRLEN_P(constval)+1, 1);
    memcpy(Z_STRVAL_P(constval), "Hello World",
                            Z_STRLEN_P(constval) + 1);
    zend_hash_add(&ce->constants_table,
                    "GREETING", sizeof("GREETING"),
                    (void*)&constval, sizeof(zval*), NULL);

    /* Objects, Arrays, and Resources can't be constants */
}

PHP_MINIT_FUNCTION(sample3)
{
    zend_class_entry ce;

    INIT_CLASS_ENTRY(ce, PHP_SAMPLE3_SC_NAME,
                            php_sample3_sc_functions);
    php_sample3_sc_entry =
                zend_register_internal_class(&ce TSRMLS_CC);
    php_sample3_register_constants(php_sample3_sc_entry);
    return SUCCESS;
}
```

完成这些添加后，可以通过`Sample3_SecondClass::E`和`Sample3_SecondClass::GREETING`分别访问这些类常量。

### 接口 (Interfaces)

声明接口与声明任何其他类一样，仅在于步骤不同。其中第一步是将其所有方法声明为抽象方法，这可以通过使用`PHP_ABSTRACT_ME()`宏完成：

```c
static function_entry php_sample3_iface_methods[] = {
    PHP_ABSTRACT_ME(Sample3_Interface, workerOne, NULL)
    PHP_ABSTRACT_ME(Sample3_Interface, workerTwo, NULL)
    PHP_ABSTRACT_ME(Sample3_Interface, workerThree, NULL)
    { NULL, NULL, NULL }
};
```

由于这些方法是抽象的，因此不需要任何实现方法。你已经准备好了第二步，即注册。与真实类的注册一样，这始于调用`INIT_CLASS_ENTRY`和`zend_register_internal_class`。

当类项可用时，最后一步是将该类标记为接口，以便它可以被实现：

```c
zend_class_entry *php_sample3_iface_entry;

PHP_MINIT_FUNCTION(sample3)
{
    zend_class_entry ce;

    INIT_CLASS_ENTRY(ce, "Sample3_Interface",
                        php_sample3_iface_methods);
    php_sample3_iface_entry =
                zend_register_internal_class(&ce TSRMLS_CC);
    php_sample3_iface_entry->ce_flags|= ZEND_ACC_INTERFACE;
    ...
```

#### 实现接口 (Implementing Interfaces)

假设你想让`Sample3_SecondClass`类实现`Sample3_Interface`接口，你需要在类中作为接口的一部分实现每个抽象方法：

```c
PHP_METHOD(Sample3_SecondClass, workerOne)
{
    php_printf("Working Hard.");
}

PHP_METHOD(Sample3_SecondClass, workerTwo)
{
    php_printf("Hardly Working.");
}

PHP_METHOD(Sample3_SecondClass, workerThree)
{
    php_printf("Going wee-wee all the way home.");
}
```

然后在`php_sample3_sc_functions`列表中声明它们：

```c
PHP_ME(Sample3_SecondClass, workerOne, ZEND_ACC_PUBLIC)
```



`PHP_ME(Sample3_SecondClass,workerTwo,ZEND_ACC_PUBLIC)`

`PHP_ME(Sample3_SecondClass,workerThree,ZEND_ACC_PUBLIC)`

最后，声明你新注册的类实现了 `php_sample3_iface_entry`：

```c
PHP_MINIT_FUNCTION(sample3)
{
    zend_class_entry ce;

    /* Register Interface */
    INIT_CLASS_ENTRY(ce, "Sample3_Interface",
                        php_sample3_iface_methods);
    php_sample3_iface_entry =
                zend_register_internal_class(&ce TSRMLS_CC);
    php_sample3_iface_entry->ce_flags|= ZEND_ACC_INTERFACE;

    /* Register Class */
    INIT_CLASS_ENTRY(ce, PHP_SAMPLE3_SC_NAME,
                            php_sample3_sc_functions);
    php_sample3_sc_entry =
                zend_register_internal_class(&ce TSRMLS_CC);
    php_sample3_sc_entry_register_constants(php_sample3_sc_entry);
    zend_class_implements(php_sample3_sc_entry, TSRMLS_CC,
                1, php_sample3_iface_entry);

    return SUCCESS;
}
```

如果 `Sample3_SecondClass` 实现了其他接口（例如 `ArrayAccess`），可以通过增加参数以匹配接口数量，将类项作为额外参数添加到 `zend_class_implements()` 中：

```c
zend_class_implements(php_sample3_sc_entry, TSRMLS_CC,
            2, php_sample3_iface_entry, other_interface_entry);
```

### 处理器 (Handlers)

Zend 没有同等对待每一个对象实例，而是为每个对象实例关联了一个处理器表。当对对象执行特定操作时，引擎会调用对象的处理器表，以便执行任何自定义操作。

#### 标准处理器 (Standard Handlers)

默认情况下，每个对象都分配了来自 `std_object_handlers` 内置表的处理器。处理器方法及其默认行为如下：

- `void add_ref(zval *object)`
  当对象的引用计数增加时（例如将对象赋值给新变量）时调用。

- `void del_ref(zval *object)`
  与 `add_ref` 类似，当对象的引用计数变化（通常是 `unset()` 调用）时调用。

- `zend_object clone_obj(zval *object)`
  用于从已实例的对象生成新对象。默认行为是创建一个新对象，关联原始属性表，如果类定义了 `__clone()` 方法，则调用它允许新对象执行额外的工作。

```c
zval *read_property(zval *obj, zval *prop, int type)
void write_property(zval *obj, zval *prop,zval *value)
```

`read` 和 `write` 属性方法响应用户对 `$obj->prop` 的读取或写入尝试。默认处理器会首先在标准属性表中查找属性。如果属性未定义，将调用相应的 `__get()` 或 `__set()` 魔法方法（假设它们已定义）。

- `zval **get_property_ptr_ptr(zval *obj, zval *value)`
  `get_property_ptr_ptr` 是 `read_property` 的变体，允许调用作用域直接用新的 `zval*` 替换当前值。默认行为是返回标准属性表中属性的解引用指针。如果它尚不存在，且没有 `__get()`/`__set()` 魔法方法，将隐式创建一个新变量并返回指针。已有的 `__get()` 或 `__set()` 方法会导致此处理器失败，让引擎回退到对 `read_property` 和 `write_property` 的单独调用。

```c
zval *read_dimension(zval *obj, zval *idx, int type)
void write_dimension(zval *obj, zval *idx,zval *value)
```

`read` 和 `write` 维度对与其读取和写入属性对应的类似；但它们响应于将对象视为数组的操作（例如使用 `$obj['idx']`）。如果对象的类没有实现 `ArrayAccess` 接口，默认处理器将抛出错误；否则，将调用相应的魔法方法 `offsetget($idx)` 或 `offsetset($idx, $value)`。

```c
zval *get(zval *obj TSRMLS_DC)
void set(zval *obj, zval *value TSRMLS_DC)
```

在设置或检索对象的值时，会调用该对象上相应的 `get()` 或 `set()` 方法。对象本身作为第一个参数的指针（courtesy pointer）传递。对于设置操作，新值通过第二个参数传递。在实践中，这些方法通常成对用于算术运算。这些操作没有默认的处理器程序。

- `int has_property(zval *obj, zval *prop, int chk_type TSRMLS_DC)`

  当对对象属性调用 `isset()` 时，会调用此处理器程序。默认情况下，标准处理器会检查由 `prop` 命名的属性；如果未找到，且从 PHP 5.1.0 起如果定义了 `__isset()` 方法，则会调用该方法。`chk_type` 参数有三个可能的值之一。如果该值为 2，则属性只需存在即视为成功。如果 `chk_type` 为 0，则它必须存在且类型为除 `IS_NULL` 以外的任何类型。如果 `chk_type` 的值为 1，则该值必须存在且求值为非假值。注意：在 PHP 5.0.x 中，`chk_type` 的含义与 `has_dimension` 版本的 `chk_type` 一致。

- `int has_dimension(zval *obj, zval *idx, int chk_type TSRMLS_DC)`

  当被视为数组的对象调用 `isset()` 时（例如 `isset($obj['idx'])`），将使用此处理器程序。如果对象实现了 `ArrayAccess` 接口，标准处理器将先调用 `offsetexists($idx)` 方法。如果未找到，则返回 0 表示失败。否则，如果 `chk_type` 为 0，它将立即返回真 (1)。`chk_type` 为 1 表示还必须通过调用对象的 `offsetget($idx)` 方法并检查返回的值，来确保该值也是非假的。

- ```c
  void unset_property(zval *obj, zval *prop TSRMLS_DC)
  void unset_dimension(zval *obj, zval *idx TSRMLS_DC)
  ```

  这些方法分别响应尝试取消对象属性或取消被视为数组的对象的偏移量（offset）。`unset_property()` 处理器程序将从标准属性表中删除该属性（如果存在），或者从 PHP 5.1.0 起尝试调用任何实现的 `__unset($prop)` 方法。如果类实现了 `ArrayAccess`，`unset_dimension()` 将调用 `offsetunset($idx)` 方法。

- `HashTable *get_properties(zval *object TSRMLS_DC)`

  当内部函数使用 `Z_OBJPROP()` 宏来检索标准属性 HashTable 时，实际上调用的是此处理器程序。PHP 对象的默认处理器程序会提取并返回 `Z_OBJ_P(object)->properties`，这才是真正的标准 HashTable。

- ```c
  union _zend_function *get_method(zval **obj, char *method, int method_len, TSRMLS_DC)
  ```

  当内部函数使用 `Z_OBJPROP()` 宏来检索标准属性 HashTable 时，实际上调用的是此处理器程序。PHP 对象的默认处理器程序会提取并返回 `Z_OBJ_P(object)->properties`，这才是真正的标准 HashTable。

- `int call_method(zval *obj, char *method, int method_len, TSRMLS_DC)`

  当内部函数使用 `Z_OBJPROP()` 宏来检索标准属性 HashTable 时，实际上调用的是此处理器程序。PHP 对象的默认处理器程序会提取并返回 `Z_OBJ_P(object)->properties`，这才是真正的标准 HashTable。

- `union _zend_function *get_constructor(zval *obj TSRMLS_DC)`

  当内部函数使用 `Z_OBJPROP()` 宏来检索标准属性 HashTable 时，实际上调用的是此处理器程序。PHP 对象的默认处理器程序会提取并返回 `Z_OBJ_P(object)->properties`，这才是真正的标准 HashTable。

- `zend_class_entry *get_class(zval *obj TSRMLS_DC)`

  当内部函数使用 `Z_OBJPROP()` 宏来检索标准属性 HashTable 时，实际上调用的是此处理器程序。PHP 对象的默认处理器程序会提取并返回 `Z_OBJ_P(object)->properties`，这才是真正的标准 HashTable。

- ```c
  int get_class_name(zval *object, char **name, uint *len, int parent, TSRMLS_DC)
  ```

  `get_class_name()` 比 `get_class_entry()` 更进了一步，它根据 `parent` 的值提取对象类或其父类的复制副本。类名的副本必须使用非持久性（`emalloc`）存储。

- `int compare_objects(zval *obj1, zval *obj2 TSRMLS_DC)`

  当对对象对使用 `==`、`!=`、`<=`、`<`、`>`、`>=` 等运算符时，会对等式左侧的对象调用 `compare_objects` 处理器。返回值遵循典型的大于、等于、小于 1、0,-1。默认情况下，对象根据其属性 HashTable 进行比较，使用你在第 8 章中看到的数组比较规则。

- ```c
  int cast_object(zval *src, zval *dst, int type, int should_free, TSRMLS_DC)
  ```

  某些将对象转换为其他类型的尝试会触发此处理器程序。如果 `should_free` 设置为非零值，则应先对 `dst` 调用 `zval_dtor()` 以释放任何内部资源。无论如何，处理器程序都应尝试将 `src` 中的对象表示为 `dst` 中指定的 `type`。此处理器程序默认定义，但在调用时应返回 `SUCCESS` 或 `FAILURE`。

- `int count_elements(zval *obj, long *count TSRMLS_DC)`

  定义了重载维度的对象应实现此处理器程序，然后填充 `count` 为元素数量并返回 `SUCCESS`。如果当前实例实际上没有实现重载属性，可能会返回 `FAILURE`，允许引擎退回到检查标准属性表。

### 魔术方法之二

通过使用之前看到的对象处理器的自定义版本，内部类可以在每个类或每个对象的基础上，复制用户空间通过 `__special()` 方法可用的相同重载行为（以及更多功能）。在对象实例上推送这些自定义处理器首先需要创建一个新的处理器表。由于你几乎肯定不想覆盖所有的处理器，合理的做法是将标准处理器拷贝到你的自定义表中，然后覆盖你想要更改的处理器：

```c
static zend_object_handlers php_sample3_obj_handlers;

int php_sample3_has_dimension(zval *obj, zval *idx,
                        int chk_type TSRMLS_DC)
{
    /* Only used when PHP >= 5.1.0 */
    if (chk_type == 0) {
       /* Remap check type */
       chk_type = 2;
    }
    /* Check type of 1 remains unchanged
     * Use standard has_property method with
     * (un)modified Check Type */
    return php_sample3_obj_handlers.has_property(obj,
                            idx, chk_type TSRMLS_CC);
}

PHP_MINIT_FUNCTION(sample3)
{
    zend_class_entry ce;
    zend_object_handlers *h = &php_sample3_obj_handlers;

    /* Register Interface */
    INIT_CLASS_ENTRY(ce, "Sample3_Interface",
                        php_sample3_iface_methods);
    php_sample3_iface_entry =
                zend_register_internal_class(&ce TSRMLS_CC);
    php_sample3_iface_entry->ce_flags = ZEND_ACC_INTERFACE;

    /* Register SecondClass class */
    INIT_CLASS_ENTRY(ce, PHP_SAMPLE3_SC_NAME,
                            php_sample3_sc_functions);
    php_sample3_sc_entry =
                zend_register_internal_class(&ce TSRMLS_CC);
    php_sample3_register_constants(php_sample3_sc_entry);

    /* Implement AbstractClass interface */
    zend_class_implements(php_sample3_sc_entry TSRMLS_CC,
                1, php_sample3_iface_entry);

    /* Create custom Handler Table */
    php_sample3_obj_handlers = *zend_get_std_object_handlers();

    /* Make $obj['foo'] act like $obj->foo */
    h->read_dimension = h->read_property;
    h->write_dimension = h->write_property;
    h->unset_dimension = h->unset_property;

#if PHP_MAJOR_VERSION > 5 || \
            (PHP_MAJOR_VERSION == 5 && PHP_MINOR_VERSION > 0)
    /* As of PHP 5.1.0 has_property and has_dimension differ
     * In order to make them behave the same we have to
     * wrap the call through a proxy */
    h->has_dimension = php_sample3_has_dimension;
#else
    /* PHP 5.0.x has_property and has_dimension act the same */
    h->has_dimension = h->has_property;
#endif

    return SUCCESS;
}
```

要将此句柄表应用到对象，你有几种选择。最简单的方法是实现一个构造函数方法，并在此时重新分配变量的句柄表：

```php
PHP_METHOD(Sample3_SecondClass,__construct)
{



```c
zval *objptr = getThis();

if (!objptr) {
    php_error_docref(NULL TSRMLS_CC, E_WARNING,
                "Constructor called statically!");
    RETURN_FALSE;
}

/* Perform usual constructor tasks here... */

/* Override handler table */
Z_OBJ_HT_P(objptr) = &php_sample3_obj_handlers;
```

当构造函数返回时，对象将拥有一个新的句柄表并表现出自定义行为。另一种通常更受青睐的方法是覆盖类目的对象创建方法：

```php
zend_object_value php_sample3_sc_create(zend_class_entry *ce
                                        TSRMLS_DC)
{
    zend_object *object;
    zend_object_value retval;

    /* Reuse Zend's generic object creator */
    retval = zend_objects_new(&object, ce TSRMLS_CC);

    /* When overriding create_object,
     * properties must be manually initialized */
    ALLOC_HASHTABLE(object->properties);
    zend_hash_init(object->properties, 0, NULL,
                                    ZVAL_PTR_DTOR, 0);

    /* Override default handlers */
    retval.handlers = &php_sample3_obj_handlers;

    /* Other object initialization may occur here */
    return retval;
}
```

这可以被附加到类目，一旦它在 `MINIT` 阶段注册：

```php
INIT_CLASS_ENTRY(ce, PHP_SAMPLE3_SC_NAME,
                        php_sample3_sc_functions);
php_sample3_sc_entry =
                zend_register_internal_class(&ce TSRMLS_CC);
php_sample3_register_constants(php_sample3_sc_entry);
zend_class_implements(php_sample3_sc_entry TSRMLS_CC,
                1, php_sample3_iface_entry);
```

将此句柄表应用到对象，你有几种选择。最简单的方法通常是实现一个构造函数方法，并在此时重新分配变量的句柄表：

当构造函数返回时，对象将拥有一个新的句柄表并表现出自定义行为。另一种通常更受青睐的方法是覆盖类目的对象创建方法：

这两个方法的唯一显著区别在于时机。引擎在遇到 `new Sample3_SecondClass` 时会调用 `create_object`，甚至在考虑构造函数之前。通常，你应该使用你计划覆盖的任何一种方法（`create_object` 或 `__construct`）。

## 总结

毫无疑问，PHP5/ZE2 对象模型比其 PHP4/ZE1 前身更复杂。在看到本章所有的特性和实现细节后，你可能会感到有些压力。幸运的是，组成 OOP 的层允许你选择适合任务的部分并忽略其他部分。找到一个舒适的起点并逐渐增加复杂度。

现在已经涵盖了 PHP 的所有内部数据类型，是时候回到之前的话题：请求生命周期。在接下来的两个章节中，你将通过使用线程安全全局变量添加内部状态，定义自定义 `ini` 设置，声明常量并为用户脚本提供超级全局。

## 周期

除了这些直接链接到模块目的的四个方法外，还有两种方法仅用于线程环境，用于处理单个线程的启动和它们使用的私有存储。要开始，请使用 PHP 源码树下 `ext/sample4` 中的这些源文件设置一个更完整的基础扩展（参见列表 12.1 到 12.3）。

```c
#include "php_sample4.h"
#include "ext/standard/info.h"

static function_entry php_sample4_functions[] = {
    { NULL, NULL, NULL }
};

PHP_MINIT_FUNCTION(sample4)
{
    return SUCCESS;
}

PHP_MSHUTDOWN_FUNCTION(sample4)
{
    return SUCCESS;
}

PHP_RINIT_FUNCTION(sample4)
{
    return SUCCESS;
}

PHP_RSHUTDOWN_FUNCTION(sample4)
{
    return SUCCESS;
}

PHP_MINFO_FUNCTION(sample4)
{
}

zend_module_entry sample4_module_entry = {
#if ZEND_MODULE_API_NO >= 20010901
    STANDARD_MODULE_HEADER,
#endif
    PHP_SAMPLE4_EXTNAME,
    php_sample4_functions,
    PHP_MINIT(sample4),
    PHP_MSHUTDOWN(sample4),
    PHP_RINIT(sample4),
    PHP_RSHUTDOWN(sample4),
    PHP_MINFO(sample4),
#if ZEND_MODULE_API_NO >= 20010901
    PHP_SAMPLE4_EXTVER,
#endif
    STANDARD_MODULE_PROPERTIES
};

#ifdef COMPILE_DL_SAMPLE4
ZEND_GET_MODULE(sample4)
#endif
```

注意，每个启动和关闭方法在退出时都会返回 `SUCCESS`。如果任何方法返回 `FAILURE`，PHP 将会中止模块加载或请求，以避免在引擎的其他地方出现任何严重问题。

### 模块周期

`MINIT` 你应该觉得很熟悉，因为你在之前的章节中已经多次使用了它。它在模块第一次被加载到进程空间时触发，对于像 `CLI` 和 `CGI` 这样的单请求 SAPI，或者像 `Apache2-worker` 这样的多线程 SAPI，它恰好执行一次，因为不涉及派生（forking）。

对于像 `Apache1` 和 `Apache2-prefork` 这样的多进程 SAPI，会派生多个 Web 服务器进程，并随之产生多个 `mod_php` 实例。每个 `mod_php` 实例都必须加载它自己的扩展模块实例，这意味着你的 `MINIT` 方法会被运行多次，但在每个进程空间中仍然只运行一次。

当模块被卸载时，会调用 `MSHUTDOWN` 方法，以便该模块拥有的任何资源（例如持久内存块）可以被释放并返回操作系统。

引擎级特性，例如类条目（Class Entries）、资源 ID（Resource IDs）、流包装器和过滤器（Stream wrappers and filters）、用户态全局变量（userspace autoglobals）以及 `php.ini` 配置，是在模块 `INIT` 和 `SHUTDOWN` 阶段分别分配和清理的一些常见资源示例。

#### 注意

理论上，你可以跳过 `MSHUTDOWN` 阶段的适当资源清理，转而允许操作系统隐式释放内存和文件句柄。但在 Apache 1.3 使用你的扩展时，你会发现一个有趣的现象：Apache 会加载 `mod_php`，在进程中启动所有的 `MINIT` 方法，然后立即卸载 `mod_php` 触发 `MSHUTDOWN` 方法，再次再次加载。如果没有适当的 `MSHUTDOWN` 阶段，初始 `MINIT` 期间分配的资源将会泄漏并浪费。

### 线程周期

在多线程 SAPI 中，有时需要每个线程分配自己的独立资源或跟踪它自己的个人请求计数器。对于这些特殊情况，有一个每线程钩子（per-thread hook），允许执行额外的启动和关闭方法。通常当像 `Apache2-worker` 这样的多线程 SAPI 启动时，它会产生几十或更多线程，以便能够处理多个并发请求。

任何可以在请求之间共享但不能在同一进程空间内被多个线程同时访问的资源，通常在线程构造方法和析构方法中分配和释放。示例可能 `EG(persistent_list)` `HashTable` 中的持久资源，因为它们通常包含了网络或文件资源，这些资源假设从指令到指令的状态具有一致性。

### 请求周期

最后一个也是最转瞬即逝的启动和关闭周期发生在每个请求中，你的扩展可能会在此处选择初始化默认的用户态变量或初始化内部状态跟踪信息。由于这两个方法在每一个页面请求时都会被调用，因此将处理和内存分配负载保持在最低是非常关重要的。

### 通过 MINFO 暴露信息

除非你打算成为唯一使用你扩展的人，并且永远不计划更改 API，否则你可能需要你的扩展能够向用户态提供一些关于自身的信息。例如，它所有的环境和特定版本的特性都可用吗？它是针对哪些版本的外部库编译的？是否有使用你扩展的用户可以联系寻求帮助的网站或电子邮件地址？

如果你曾经查看过 `phpinfo()` 或 `php -i` 的输出，你会发现所有这些信息都被分组在一个格式良好、易于解析的输出中。你的扩展可以通过由模块条目结构指向的 `MINFO`（模块信息）方法中放置几行代码，轻松地在此列表中添加它自己的区块：

```c
PHP_MINFO_FUNCTION(sample4)
{
    php_info_print_table_start();
    php_info_print_table_row(2, "Sample4 Module", "enabled");
    php_info_print_table_row(2, "version", PHP_SAMPLE4_EXTVER);
    php_info_print_table_end();
}
```

通常的 `PHPWRITE()` 和 `php_printf()` 函数也可以在 `MINFO` 方法中使用，尽管在手动输出内容时，你应该始终根据当前 SAPI 期望的是纯文本还是 HTML 内容来确保输出正确类型的信息。要实现这一点，只需检查全局 `sapi_module` 结构体的 `phpinfo_as_text` 属性即可：

```c
PHP_MINFO_FUNCTION(sample4)
{
    php_info_print_table_start();
    php_info_print_table_row(2, "Sample4 Module", "enabled");
    php_info_print_table_row(2, "version", PHP_SAMPLE4_EXTVER);

    if (sapi_module.phpinfo_as_text) {
        /* 这里没有 HTML 给你 */
        php_info_print_table_row(2, "By",
            "Example Technologies\nhttp://www.example.com");
    } else {
        /* HTML 版本 */
        php_printf("<tr>"
            "<td class=\"v\">By</td>"
            "<td class=\"v\">"
            "<a href=\"http://www.example.com\""
            " alt=\"Example Technologies\">"
            "<img src=\"http://www.example.com/logo.png\" />"
            "</a></td></tr>");
    }

    php_info_print_table_end();
}
```

### 常量

向使用你扩展的脚本暴露信息的一种更易于访问的方法是定义可以在运行时由脚本访问的常量，这可能允许它们修改自己的行为。在用户空间中，你使用 `define()` 函数声明常量；在内部，这种方式几乎相同，并使用 `REGISTER_*_CONSTANT()` 系列的宏。

大多数常量都是你希望在所有初始化为相同值的脚本中提供的且具有相同值。要声明这些常量，你需要在 `MINIT` 方法中声明它们：

```c
PHP_MINIT_FUNCTION(sample4)
{
    REGISTER_STRING_CONSTANT("SAMPLE4_VERSION",
            PHP_SAMPLE4_EXTVER, CONST_CS | CONST_PERSISTENT);
    return SUCCESS;
}
```

此宏的第一个参数是导出到用户空间的常量名称。在这个示例中，用户空间脚本将能够执行 `echo SAMPLE4_VERSION;` 并输出 `1.0`。这里需要注意的是，`REGISTER_*_CONSTANT()` 系列宏使用 `sizeof()` 调用来确定常量名称的长度。这意味着只能使用字面量值。尝试使用 `char*` 变量将导致错误的字符串长度（在 32 位平台上，`sizeof(char*)` 通常为 4）。

接下来是常量本身的值。在大多数情况下，它是具有具名类型的单数参数；然而，你稍后会看到的 `STRINGL` 版本确实需要第二个长度参数。在注册字符串常量时，字符串值不会被复制到常量中，仅由其引用。这意味着动态创建的字符串需要在永久内存中分配，并在适当的关闭阶段进行释放。

最后，你传递的最后一个参数是两个可选标志的按位或（OR）组合。包含 `CONST_CS` 标志将该常量指定为大小写敏感。这是用户定义常量以及 PHP 使用的几乎所有内部常量的默认设置。对于少数特殊情况，如 `trUE`、`FALSE` 和 `NULL`，省略了此参数以便它们能够以不区分大小写的方式进行解析。

常量注册的两个标志中的第二个是持久性标志。在 `MINIT` 中声明常量时，它们必须构建为从请求到请求持久化。在请求内声明常量（例如在 `RINIT` 期间），你可以且几乎应该省略此标志，允许引擎在请求结束时销毁该常量。

以下原型描述了四个可用的常量注册宏。记住，名称参数必须是字符串字面量而不是 `char*` 变量：

```c
REGISTER_LONG_CONSTANT(char *name, long lval, int flags)
REGISTER_DOUBLE_CONSTANT(char *name, double dval, int flags)
REGISTER_STRING_CONSTANT(char *name, char *value, int flags)
REGISTER_STRINGL_CONSTANT(char *name,
                     char *value, int value_len, int flags)
```

如果字符串必须从变量名初始化（例如在循环内部），你可以使用这些宏映射到的底层函数调用：

```c
void zend_register_long_constant(char *name, uint name_len,
        long lval, int flags, int module_number TSRMLS_DC)
void zend_register_double_constant(char *name, uint name_len,
        double dval, int flags, int module_number TSRMLS_DC)
void zend_register_string_constant(char *name, uint name_len,
        char *strval, int flags, int module_number TSRMLS_DC)
void zend_register_stringl_constant(char *name, uint name_len,
        char *strval, uint strlen, int flags,
        int module_number TSRMLS_DC)
```

这一次，名称参数的长度可以由调用范围直接提供。你会注意到这次必须显式传递 `TSRMLS_CC`，并且引入了一个新参数。

`module_number` 在你的扩展加载时由引擎分配，并作为清理时的线索。你不需要担心这个变量的值；只需在所有 `MINIT` 和 `RINIT` 方法中传递它。这里是相同的常量：

```c
PHP_MINIT_FUNCTION(sample4)
{
    register_string_constant("SAMPLE4_VERSION",
        sizeof("SAMPLE4_VERSION"),
        PHP_SAMPLE4_EXTVER,
        CONST_CS | CONST_PERSISTENT,
```



`module_number`);

    return SUCCESS;

}

```

再次注意到当使用`sizeof()`确定长度时它没有减 1。如果你从`strlen()`开始确定长度，请确保加一以便包含`NULL`。除了数组和对象之外，其余类型也可以注册，但由于 Zend API 中不存在涵盖这些类型的宏或函数，你必须手动声明常量。要这样做，请遵循此简单的配方，在创建`zval*`时替换相应的类型：

```
void php_sample4_register_boolean_constant(char *name, uint len,

    zend_bool bval, int flags, int module_number TSRMLS_DC)

{

    zend_constant c;

    ZVAL_BOOL(&c.value, bval);

    c.flags = flags;

    c.name = zend_strndup(name, len - 1);

    c.name_len = len;

    c.module_number = module_number;

    zend_register_constant(&c TSRMLS_CC);

}
```

### 扩展全局

如果能够保证任何时候只有一个 PHP 脚本在单个进程中活动，你的扩展就可以声明任何需要的全局变量并访问它们，而无需担心其他脚本操作会在操作码之间损坏值。对于非线程 SAPI，这实际上是真实的，因为任何给定的进程空间一次只能执行一条代码路径。

在线程 SAPI 的情况下，两个或多个请求可能会尝试读取，更糟糕地同时写入同一个值。为了解决这个问题，引入了扩展全局变量的概念，为每个扩展的数据提供独特的数据存储桶。

#### 声明扩展全局

要为你的扩展请求存储桶，你首先需要在`php_sample4.h`文件的某处将所有的“全局”变量声明在一个统一结构中。例如，如果你的扩展跟踪在请求内调用特定函数的次数的计数器，你可以定义一个包含`unsigned long`的结构：

```
ZEND_BEGIN_MODULE_GLOBALS(sample4)

    unsigned long counter;

ZEND_END_MODULE_GLOBALS(sample4)
```

`ZEND_BEGIN_MODULE_GLOBALS`和`ZEND_END_MODULE_GLOBALS`宏为定义扩展全局结构体提供了一个统一的框架。如果你查看此块的展开，你会发现它仅仅是：

```
typedef struct _zend_sample4_globals {

    unsigned long counter;

} zend_sample4_globals;
```

然后，你可以像处理任何其他 C 结构体一样添加额外的成员。现在你已经定义了存储桶（storage bucket），是时候在扩展的`sample4.c`文件中、紧跟在`#include "php_sample4.h"`语句之后声明它：

```
ZEND_DECLARE_MODULE_GLOBALS(sample4);
```

取决于是否启用了线程安全，这将解析解析为两种形式之一。对于非线程安全的构建（例如`Apache1`、`Apache2-prefork`、`CGI`、`CLI`等），它会将`zend_sample4_globals`结构声明为真全局作用范围内的一个立即值：

```
zend_sample4_globals sample4_globals;
```

这与你在任何其他单线程应用中声明的任何其他全局变量没有任何区别。`counter`值通过`sample4_globals.counter`直接访问。另一方面，对于线程安全的构建，只声明了一个整数，它稍后将作为真实数据的引用：

```
int sample4_globals_id;
```

填充此 ID 意味着将你的扩展全局变量声明给引擎。使用提供的信息，引擎将在每个新线程创建时分配一个内存块，作为私有存储空间，供该线程服务的各个请求使用。在你的`MINIT`函数中添加以下几行：

```
#ifdef ZTS

    ts_allocate_id(&sample4_globals_id,

                sizeof(zend_sample4_globals),

                NULL, NULL);

#endif
```

注意，该语句被封装在一组`ifdef`块中，以防止在未启用 Zend 线程安全 (ZTS) 时执行它。这是合理的，因为`sample4_globals_id`只在将在线程环境中使用的构建中才被声明（或被需要）。非线程构建将使用之前声明的立即变量`sample4_globals`。

### 线程级初始化与销毁

在非线程构建中，给定进程内只会存在一个`zend_sample4_globals`结构副本。要初始化它，你可以在`MINIT`或`RINIT`中分配默认值或分配资源，并在必要时在`MSHUTDOWN`或`RSHUTDOWN`中相应地释放这些资源。

然而，对于线程构建，每当开启新线程时，都会分配一个新的结构。在实践中，仅在 Web 服务器启动期间这可能发生几十次，而在 Web 服务器进程的生命周期内可能会发生数百甚至数千次。为了知道如何初始化和销毁扩展的全局变量，引擎需要一组回调函数。这就是你之前传递给`ts_allocate_id()`的`NULL`参数发挥用场的地方；在你的`MINIT`函数上方添加以下两个方法：

```
static void php_sample4_globals_ctor(

            zend_sample4_globals *sample4_globals TSRMLS_DC)

{

    /* 在线程启动期间

     * 初始化一个新的 zend_sample4_globals 结构 */

    sample4_globals->counter = 0;

}

static void php_sample4_globals_dtor(

            zend_sample4_globals *sample4_globals TSRMLS_DC)

{

    /* 在初始化期间分配的任何资源

     * 在此处释放 */

}
```

然后使用这些函数进行启动和销毁：

```
PHP_MINIT_FUNCTION(sample4)

{

    REGISTER_STRING_CONSTANT("SAMPLE4_VERSION",

            PHP_SAMPLE4_EXTVER, CONST_CS | CONST_PERSISTENT);

#ifdef ZTS

    ts_allocate_id(&sample4_globals_id,

                sizeof(zend_sample4_globals),

                (ts_allocate_ctor)php_sample4_globals_ctor,

                (ts_allocate_dtor)php_sample4_globals_dtor);

#else

    php_sample4_globals_ctor(&sample4_globals TSRMLS_CC);

#endif

    return SUCCESS;

}

PHP_MSHUTDOWN_FUNCTION(sample4)

{

#ifndef ZTS

    php_sample4_globals_dtor(&sample4_globals TSRMLS_CC);

#endif

    return SUCCESS;

}
```

注意，当未定义 ZTS 时，手动调用了`ctor`和`dtor`函数。不要忘记非线程构建也需要初始化和销毁！

#### 注意

你可能在想为什么在直接调用`php_sampl4_globals_ctor()`和`php_sample4_globals_dtor()`时使用了`TSRMLS_CC`。如果你在想“这完全没有必要，当 ZTS 禁用时这些值完全无意义，而且由于`#ifdef`指令的存在，我知道 ZTS 已经被禁用了！”，那么你是完全正确的。这些与声明中`TSRMLS_DC`指令对应的对应项纯粹是出于一致性的考量。从积极的一方面来说，如果 Zend API 发生变化，以至于这些值即使对于非 ZTS 构建也变得相关，你的代码将是正确并准备好应对它的。

### 访问扩展全局变量

现在你的扩展有了一组全局变量，你可以在代码中开始访问它们。在非 ZTS 模式下，这非常简单；直接访问全局作用范围内的`sample4_globals`变量，如如下函数所示，它递增你之前定义的计数器并返回其当前值：

```
PHP_FUNCTION(sample4_counter)

{

    RETURN_LONG(++sample4_globals.counter);

}
```

既整洁。然而，这种方法对线程构建无效。对于这些构建，你需要进行更多工作。这里是该函数的返回语句，这次使用了 ZTS 语义：

```
RETURN_LONG(++TSRMG(sample4_globals_id,

                zend_sample4_globals*, counter));
```

`TSRMG()`宏通过你一直传递的`TSRMLS_CC`参数找到当前线程的资源池。从那里，它使用`sample4_globals_id`索引映射到你扩展特定的全局结构点。最后，它使用数据类型将元素名称映射到该结构中的偏移量。由于你通常不知道扩展将在 ZTS 还是非 ZTS 模式下使用，你需要兼容两者。为了做到这一点，你可以像这样重写函数：

```
PHP_FUNCTION(sample4_counter)

{

#ifdef ZTS

    RETURN_LONG(++TSRMG(sample4_globals_id,

                    zend_sample4_globals*, counter));

#else /* 非 ZTS */

    RETURN_LONG(++sample4_globals.counter);

#endif

}
```

看起来很难看？确实如此。想象你的整个代码库中每次访问线程安全全局时都布满了这些`ifdef`指令。那看起来比 Perl 还要糟糕！这就是为什么所有核心扩展以及在 PECL 中找到的扩展都使用一个额外的宏层来抽象这些内容。将以下定义放入你的`php_sample4.h`文件中：

```
#ifdef ZTS

#include "TSRM.h"

#define SAMPLE4_G(v)    TSRMG(sample4_globals_id,

                         zend_sample4_globals*, v)

#else

#define SAMPLE4_G(v)    (sample4_globals.v)

#endif
```

然后将你的新函数定义替换为这种更简单、更具读性的形式：

```
PHP_FUNCTION(sample4_counter)

{

    RETURN_LONG(++SAMPLE4_G(counter));

}
```

| `CG()` | 核心全局。主要由 Zend 在脚本编译期间以及一系列深层执行步骤中使用。你的扩展很少会直接检查这些值。 |
| `PG()` | PHP 全局变量。大多数“核心”`php.ini`指令都映射到 php 全局变量结构中的一个或多个元素。`PG(register_globals)`、`PG(safe_mode)`和`PG(memory_limit)`只是其中的几个例子。 |
| `FG()` | 文件全局变量。大多数与文件 I/O 或流相关的全局变量都封装在这个由标准扩展导出的结构体中。 |

![](img/30011536.html)

### 用户空间超全局变量 (Userspace Superglobals)

用户空间世界有其自己独立且完全无关的全局性概念。即使在这里，也存在一种所谓的“特殊”全局变量，通常被称为超全局变量（superglobal）。这些独特的用户空间变量类型（包括`$_GET`、`$_POST`、`$_FILE`等）可以从全局作用域访问，也可以在函数或方法内部访问，就像它们是该作用域的局部变量一样。

由于超全局变量的解析方式，它们必须在脚本编译之前声明。对于普通脚本来说，这意味着它们不能将额外的变量声明为超全局。然而，对于扩展来说，可以在接收任何请求之前将变量名声明为超全局。

声明自己的有超全局变量的扩展的一个典型示例是`ext/session`，它使用`$_SESSION`超全局变量在多次调用`session_start()`和`session_write_close()`之间（或脚本结束时，以先者为准）存储会话信息。为了将`$_SESSION`声明为超全局，sessions 扩展在它的`MINIT`方法中执行了下面这条简单的一次性语句：

```
PHP_MINIT_FUNCTION(session)

{

    zend_register_auto_global("_SESSION",

                         sizeof("_SESSION") - 1,

                         NULL TSRMLS_CC);

    return SUCCESS;

}
```

注意，这里的第二个参数（引用变量名的长度）使用了`sizeof()-1`来排除终止的`NULL`。这与你到目前为止看到的大多数内部调用截然相反，因此在声明自己的变量时要小心不要被它坑了。

Zend Engine 2 中`zend_register_auto_global()`函数的原型如下：

```
int zend_register_auto_global(char *name, uint name_len,

    zend_auto_global_callback auto_global_callback TSRMLS_DC)
```

在 Zend Engine 1 中，不存在`auto_global_callback`参数。为了让你的扩展兼容旧的 PHP4 安装版本，你需要像下面这个`MINIT`方法那样加入一个`#ifdef`块来声明一个`$_SAMPLE4`自动全局变量：

```
PHP_MINIT_FUNCTION(sample4)

{

    zend_register_auto_global("_SAMPLE4", sizeof("_SAMPLE4") - 1

#ifdef ZEND_ENGINE_2

                        , NULL

#endif

                        TSRMLS_CC);

    return SUCCESS;

}
```

### 自动全局回调 (Auto Global Callback)

ZE2 的`zend_register_auto_global`的`auto_global_callback`参数是一个指向自定义函数的指针，每当引擎在用户空间脚本遇到你的超全局变量时，该函数就会被触发。在实践中，这可以用于避免复杂的初始化程序，除非已知当前脚本确实会访问该变量。考虑以下设置：

```
zend_bool php_sample4_autoglobal_callback(char *name,

                            uint name_len TSRMLS_DC)

{

    zval *sample4_val;

    int i;

    MAKE_STD_ZVAL(sample4_val);

    array_init(sample4_val);

    for (i = 0; i < 100; i++) {

        array_init_add(sample4_val, "key", "value"); 

    }

    EG(sample4) = *sample4_val;

    return SUCCESS;

}
```

*(注：原文中示例代码逻辑不完整且存在截断，翻译保留了其原始代码结构。)*

```
PHP_FUNCTION(sample4_hello_world)

{

    php_printf("Hello World!\n");

}
```

最直接的方法是定义一个 INI 设置，并赋予其默认值 "Hello World!"，如下：

```
#include "php_ini.h"

PHP_INI_BEGIN()

    PHP_INI_ENTRY("sample4.greeting", "Hello World",

                                    PHP_INI_ALL, NULL)

PHP_INI_END()
```

正如你可能猜到的那样，该宏的前两个参数分别代表 INI 设置的名称和它的默认值。第三个参数决定了引擎何时允许更改该设置，将在本章稍后的“访问级别（Access Levels）”部分进行介绍。最后一个参数接收一个指向回调函数的指针，每当 INI 值发生变化时，该函数就会被触发。你将在“修改事件（modification events）”部分详细查看此参数。

现在你已经声明了 INI 设置，准备可以在你的问候函数中使用它了：

```
PHP_FUNCTION(sample4_hello_world)

{

    const char *greeting = INI_STR("sample4.greeting");

    php_printf("%s\n", greeting);

}
```



需要注意的是，`char*` 值被认为由引擎拥有，不能被修改。因此，你用于填充 INI 设置的局部变量在你的函数内部中被声明为 `const`。当然，并不是所有的 INI 值都是字符串形式的；还存在额外的宏用于获取整数、浮点数或布尔值：

```php
long lval = INI_INT("sample4.intval");
double dval = INI_FLT("sample4.fltval");
zend_bool bval = INI_BOOL("sample4.boolval");
```

通常情况下，你想知道 INI 设置的当前值；然而，每种类型都有一组互补的宏，可以显示原始的、未修改的 INI 设置。

```php
const char *strval = INI_ORIG_STR("sample4.stringval");
long lval = INI_ORIG_INT("sample4.intval");
double dval = INI_ORIG_FLT("sample4.fltval");
zend_bool bval = INI_ORIG_BOOL("sample4.boolval");
```

## Note

在此示例中，INI 项 `sample4.greeting` 的名称带有扩展名前缀，这有助于确保它不会与其他不同扩展导出的 INI 设置发生冲突。这种前缀对于私有扩展不是强制要求的，但对于任何公开发布的扩展（无论是商业还是开源的），都被视为一种礼貌。

### 访问级别

给定的 INI 值始终从默认值开始。在许多情况下，保留该默认值是合理的；然而，这些值通常需要针对特定环境或脚本中的特定操作进行修改。此类设置修改可以在三个不同点之一发生，如表 13.1 所示。

#### 表 13.1

| 访问级别 | 含义 |
| --- | --- |
| `SYSTEM` | 放置在 `php.ini` 中，或者在 Apache 的 `httpd.conf` 文件的 `<Directory>` 和 `<VirtualHost>` 指令之外的设置将在引擎启动阶段生效，并视为设置的“全局”值。 |
| `PERDIR` | 在 Apache 的 `httpd.conf` 中的 `<Directory>` 或 `<VirtualHost>` 块内找到的设置，或者位于 `.htaccess` 文件以及某些非 Apache 专有的其他位置的设置，如果该请求位于相应的目录或虚拟主机内，会在该请求处理之前进行处理。 |
| `USER` | 一旦脚本执行，剩余可以执行的 INI 更改只有响应于用户空间函数调用：`ini_set()` 的更改。 |

此宏获取在 `PHP_INI_BEGIN` 和 `PHP_INI_END` 宏之间已定义的 INI 设置，并迭代地在一个三列表格中显示它们。表格包含 INI 设置的名称、原始（全局）设置以及通过 `PERDIR` 指令和 `ini_set()` 调用修改后的当前设置。

默认情况下，所有条目都按照其字符串表示原样输出。某些设置（例如布尔值和语法高亮的颜色值）在显示过程中会应用额外的格式化。这种格式化的应用是通过每个 INI 设置单独的显示处理器来实现的，它是一个指向回调函数的动态指针，类似于你之前看到的 `OnModify` 处理器。

显示处理器是使用 `PHP_INI_ENTRY()` 宏的扩展版本来指定的，该宏接受一个额外的参数。如果设置为 `NULL`，则将使用原样显示字符串值的默认处理器。

```php
PHP_INI_ENTRY_EX("sample4.greeting", "Hello World", PHP_INI_ALL,
    php_sample4_modify_greeting, php_sample4_display_greeting)
```

显然，这个回调函数需要在 INI 设置声明之前的某处定义。与 `OnModify` 回调一样，这将通过一个包装宏和少量的处理器代码完成：

```c
#include "SAPI.h" /* needed for sapi_module */

PHP_INI_DISP(php_sample4_display_greeting)
{
    const char *value = ini_entry->value;
    /* 根据需要选择当前值或原始值 */
    if (type == ZEND_INI_DISPLAY_ORIG &&
        ini_entry->modified) {
        value = ini_entry->orig_value;
    }
    /* 将问候语加粗（当启用 HTML 输出时） */
    if (sapi_module.phpinfo_as_text) {
        php_printf("%s", value);
    } else {
        php_printf("b%s</b>", value);
    }
}
```

### 绑定到扩展全局变量

所有的 INI 条目在 Zend Engine 内部获得了存储空间，用于跟踪脚本中的更改并维护请求之外的全局设置。在这个存储空间内，所有 INI 设置都以字符串值的形式存储。如你所知，这些值可以通过 `INI_INT()`、`INI_FLT()` 和 `INI_BOOL()` 宏轻松转换为标量值。

这种查找和转换过程由于两个原因而极其低效：首先，每次获取 INI 值时，必须通过名称在哈希表中查找。对于仅在运行时编译特定脚本的用户态脚本来说，这种查找没有问题，但对于编译后的机器码源码，在运行时执行此工作是没有意义的。

对于标量值，效率更低，因为每当请求标量值时，必须对底层字符串进行重新转换。利用你已有的知识，你可以声明一个线程安全的全局变量作为存储介质，并在每次更改时更新新值的地址。这样，任何访问该 INI 设置的代码都可以在你的线程安全全局结构体中查找指针，并利用编译时优化。

在 `php_sample4.h` 中向 `MODULE_GLOBALS` 结构体添加 `const char *greeting;`，然后更新 `sample4.c` 中的以下两个方法：

```c
ZEND_INI_MH(php_sample4_modify_greeting)
{
    /* 不允许空问候语 */
    if (new_value_length == 0) {
        return FAILURE;
    }
    SAMPLE4_G(greeting) = new_value;
    return SUCCESS;
}

PHP_FUNCTION(sample4_hello_world)
{
    php_printf("%s\n", SAMPLE4_G(greeting));
}
```

由于这是优化 INI 的常用方法，引擎还导出了另一对宏，用于处理 INI 设置到全局变量的绑定。

```c
STD_PHP_INI_ENTRY_EX("sample4.greeting", "Hello World",
    PHP_INI_ALL, OnUpdateStringUnempty, greeting,
    zend_sample4_globals, sample4_globals,
    php_sample4_display_greeting)
```

此条目执行的工作与你刚才的条目相同，但不需要 `OnModify` 回调。相反，它使用一个通用的修改回调 `OnUpdateStringUnempty`。

为了确保这些显示有意义，你可以使用 `PHP_INI_ENTRY_EX()` 宏并创建一个显示处理器，或者你可以使用备选宏：

```c
STD_PHP_INI_ENTRY_EX("sample4.greeting", "Hello World",
    PHP_INI_ALL, OnUpdateStringUnempty, greeting,
    zend_sample4_globals, sample4_globals,
    php_sample4_display_greeting)
```

这种特定类型的宏在 INI 族中仅适用于布尔值，其作用是提供一个显示处理器，将真值翻译为 `"on"`，将非真值翻译为 `"off"`。

---

## 第 14 章：访问流

PHP 用户空间中处理的所有文件 I/O 都通过 PHP 4.3 引入的流层进行处理。在内部，扩展代码可能会选择使用 stdio 或 posix 文件句柄与本地文件系统或 Berkeley 域接字通信，可能会调用与用户态流 I/O 相同的 API。

### 概述

通常，直接使用文件描述符比通过流层调用更节省 CPU 和内存；然而，这会将实现特定协议的工作全部交给你扩展编写者。通过挂钩流层，你的扩展代码可以透明地使用任何内置的流包装器，如 HTTP、FTP 及其启用 SSL 的对应项，以及 gzip 和 bzip2 压缩器。通过包含某些 PEAR 或 PECL 模块，你的代码还可以访问其他协议，如 SSH2、WebDav 甚至 Gopher！

本章将介绍从内部处理流的基本 API。稍在第 16 章“重定向流”中，你将查看更高级的概念，例如应用过滤器以及使用上下文选项和参数。

### 打开流

尽管这是一个高度统一的 API，但实际上根据所需的流类型，有四种不同的打开流的路径。从用户空间的角度来看，这四类大致区分如下（函数列表仅为代表性，并非完整列表）：

```php
<?php
    /* fopen 包装器
     * 对文件或指定
     * 类文件资源的 URI 进行的操作 */
    $fp = fopen($url, $mode);
    $data = file_get_contents($url);
    file_put_contents($url, $data);
    $lines = file($url);

    /* 传输层 (Transports)
     * 基于 socket 的顺序 I/O */
    $fp = fsockopen($host, $port);
    $fp = stream_socket_client($uri);
    $fp = stream_socket_server($uri, $options);

    /* 目录流 (Directory streams) */
    $dir = opendir($url);
    $files = scandir($url);
    $obj = dir($url);

    /* “特殊”流 */
    $fp = tmpfile();
    $fp = popen($cmd);
    proc_open($cmd, $pipes);
?>
```

无论你打开的是哪种类型的流，它们都存储在一个单一的通用结构中：`php_stream`。

### Fopen 包装器 (Fopen Wrappers)

让我们从简单重新实现 `fopen()` 函数开始并继续下去。此时，你应该已经习惯了创建扩展骨架；如果没有，请参阅第 5 章“你的第一个扩展”以获取基本结构：

```c
PHP_FUNCTION(sample5_fopen)
{
    php_stream *stream;
    char *path, *mode;
    int path_len, mode_len;
    int options = ENFORCE_SAFE_MODE | REPORT_ERRORS;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "ss",
            &path, &path_len, &mode, &mode_len) == FAILURE) {
        return;
    }

    stream = php_stream_open_wrapper(path, mode, options, NULL);
    if (!stream) {
        RETURN_FALSE;
    }
    php_stream_to_zval(stream, return_value);
}
```

`php_stream_open_wrapper()` 的目的从一开始就显而易见。`path` 指定了要读取、写入或同时打开的文件或 URL，具体取决于 `mode` 的值。

`options` 是一个零或多个标志位集合，在此情况下，它设置为此处描述的一对固定值：

| `USE_PATH` | 相对路径将应用于在 `.ini` 选项 `include_path` 中指定的路径。此选项由内置的 `fopen()` 函数在第三参数传递为 `TRUE` 时指定。 |
| --- | --- |
| `STREAM_USE_URL` | 设置时，仅将打开远程 URL。未标记为远程 URL 的包装器（如 `file://`、`php://`、`compress.zlib://` 和 `compress.bzip2://`）将导致失败。 |
| `ENFORCE_SAFE_MODE` | 尽管该常量的命名如此，但只有在设置了此选项且启用了相应的 `safe_mode ini` 指令时，安全模式检查才会被真正强制执行。排除此选项将导致无论 INI 设置如何跳过 `safe_mode` 检查。 |
| `REPORT_ERRORS` | 在打开指定的资源期间遇到错误，只有传递了此标志时才会生成错误。 |
| `STREAM_MUST_SEEK` | 某些流（如 socket 传输）永远不可寻址；其他流（如文件句柄）仅在某些情况下可寻址。如果调用范围指定了此选项且包装器确定它无法保证寻址性，它将拒绝打开流。 |
| `STREAM_WILL_CAST` | 如果调用范围要求流可以转换为 stdio 或 posix 文件描述符，则应将此选项传递给 `open_wrapper` 函数，以便其在 I/O 操作开始之前优雅地失败。 |
| `STREAM_ONLY_GET_HEADERS` | 表示仅从流中请求元数据。在实践中，这被 http 包装器用于填充 `http_response_headers` 全局变量，而无需实际获取远程文件的内容。 |
| `STREAM_DISABLE_OPEN_BASEDIR` | 类似于 `safe_mode` 检查，此选项即使不存在，仍需要启用 `open_basedir ini` 选项才能执行检查。将其指定为选项仅允许跳过默认检查。 |
| `STREAM_OPEN_PERSISTENT` | 指示流层持久地分配所有内部结构，并将关联资源注册到持久列表中。 |
| `IGNORE_PATH` | 如果未指定，将搜索默认包含路径。大多数 URL 包装器都会忽略此选项。 |
| `IGNORE_URL` | 提供时，流层将仅打开本地文件。所有 `is_url` 包装器将被忽略。 |

最后的 `NULL` 参数可以是一个 `char**`，它最初被设置为匹配路径，如果路径指向普通文件 URL，则会被更新为排除 `file://` 部分，留下一个供传统文件名操作使用的简单路径。该参数传统上供内部引擎进程使用。

`php_stream_open_wrapper()` 的扩展版本也存在：

```c
php_stream *php_stream_open_wrapper(char *path, char *mode, int options, char **path, char **context);
```

最后一个参数 `context` 允许进行额外的控制。你将在第 16 章看到此参数。

### 传输层 (Transports)

虽然传输流由与 `fopen` 相同的部分组成，但它们有自己的方案并与其余分开。从你扩展开发者的角度来看，打开传输层的过程是相同的。看看这个 `fsockopen()` 的重新实现：

```c
PHP_FUNCTION(sample5_fsockopen)
{
    php_stream *stream;
    char *host, *transport, *errstr = NULL;
    int host_len, transport_len, implicit_tcp = 1, errcode = 0;
    long port = 0;
    int options = ENFORCE_SAFE_MODE;
    int flags = STREAM_XPORT_CLIENT | STREAM_XPORT_CONNECT;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "s|l",
                        &host, &host_len, &port) == FAILURE) {
        return;
    }

    if (port) {
        int implicit_tcp = 1;
        if (strstr(host, "://")) {
                /* 指定了协议，
                 * 不需要回退到 tcp:// */
            implicit_tcp = 0;
        }
        transport_len = spprintf(&transport, 0, "%s%s:%d",
                implicit_tcp ? "tcp://" : "", host, port);
    } else {
        /* 当未指定端口时
         * 我们可以安全地假设已指定协议
         *（例如 udg://） */
        transport = host;
        transport_len = host_len;
    }

    stream = php_stream_xport_create(transport, transport_len,



以下代码片段展示了 `php_stream_xport_create()` 的调用方式：

```
options, flags,

NULL, NULL, NULL, &errstr, &errcode);

if (transport != host) {

    efree(transport);

}

if (errstr) {

    php_error_docref(NULL TSRMLS_CC, E_WARNING, "[%d] %s",

                    errcode, errstr);

    efree(errstr);

}

if (!stream) {

    RETURN_FALSE;

}

php_stream_to_zval(stream, return_value);
```

此处描述了 `php_stream_xport_create()` 的完整原型：

```php
php_stream *php_stream_xport_create(char *xport, int xport_len,

                int options, int flags,

                const char *persistent_id,

                struct timeval *timeout,

                php_stream_context *context,

                char **errstr, int *errcode);
```

这些参数的含义如下：

| 参数 | 描述 |
| :--- | :--- |
| `xport` | 基于 URI 的传输描述符。对于基于 inet 套接字的流，这可能是 `tcp://127.0.0.1:80`、`udp://10.0.0.1:53` 或 `ssl://169.254.13.24:445`。对于 UNIX 传输，合理的值可能是 `unix:///path/to/socket` 或 `udg:///path/to/dgramsocket`。`xport_len` 允许 `xport` 通过显式指定传输字符串长度来指定二进制安全的值。 |
| `options` | 该值由本章之前介绍的 `php_stream_open_wrapper()` 所使用的相同值的按位或组合而构成。 |
| `flags` | 同样由 `STREAM_XPORT_CLIENT` 或 `STREAM_XPORT_SERVER` 与下表定义的任意数量剩余 `STREAM_XPORT_*` 常量按位或组合而成。 |
| `persistent_id` | 如果该传输应在请求之间保持持久化，则调用作用域可以提供一个键名来描述连接。将此值指定为 `NULL` 将创建一个非持久化连接；指定唯一的字符串值将尝试从持久化池中恢复现有的传输，如果尚不存在则创建一个新的持久化流。 |
| `timeout` | 连接尝试在超时并返回失败之前阻塞多久。在此处传递的 `NULL` 值将使用 `php.ini` 中指定的默认超时时间。此参数对于服务器传输没有意义。 |
| `errstr` | 如果创建、连接、绑定或监听所选传输时发生错误，此处通过引用传递的 `char*` 值将填充一个描述性字符串，以报告失败原因。`errstr` 的值初始应指向 `NULL`；如果返回时它被填充了值，则调用作用域负责释放与该字符串相关的内存。 |
| `errcode` | 与通过 `errstr` 返回的错误消息对应的数值错误代码。 |

用于 `php_stream_xport_create()` `flags` 参数的 `STREAM_XPORT_*` 系列常量如下：

| 常量 | 描述 |
| :--- | :--- |
| `STREAM_XPORT_CLIENT` | 本地将通过传输建立到远程资源的连接。此标志通常与 `STREAM_XPORT_CONNECT` 或 `STREAM_XPORT_CONNECT_ASYNC` 伴用。 |
| `STREAM_XPORT_SERVER` | 本地将通过传输接受来自远程客户端的连接。此标志通常与 `STREAM_XPORT_BIND` 伴用，通常还包含 `STREAM_XPORT_LISTEN`。 |
| `STREAM_XPORT_CONNECT` | 应在传输创建过程中建立到远程资源的连接。在创建客户端传输时省略此标志是合法的，但这种情况下需要单独调用 `php_stream_xport_connect()`。 |
| `STREAM_XPORT_CONNECT_ASYNC` | 尝试连接到远程资源，但不阻塞。 |
| `STREAM_XPORT_BIND` | 将传输绑定到本地资源。当与服务器传输配合使用时，这将准备传输在特定端口、路径或其他特定端标识符上接受连接。 |
| `STREAM_XPORT_LISTEN` | 在绑定的传输端上监听入站连接。这通常用于基于流的传输，如 `tcp://`、`ssl://` 和 `unix://`。 |

### 目录访问

对于支持目录访问的 `fopen` 封装（例如 `file://` 和 `ftp://`），可以使用第三种流打开函数，如下所示 `opendir()` 的重实现：

```
PHP_FUNCTION(sample5_opendir)

{

    php_stream *stream;

    char *path;

    int path_len, options = ENFORCE_SAFE_MODE | REPORT_ERRORS;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "s",

                               &path, &path_len) == FAILURE) {

        return;

    }

    stream = php_stream_opendir(path, options, NULL);

    if (!stream) {

        RETURN_FALSE;

    }

    php_stream_to_zval(stream, return_value);

}
```

再次，为某个特定的路径描述打开了一个流，该路径可能是本地文件系统上的简单目录名称，也可能是描述支持目录访问的封装的 URL 格式资源。我们再次发现了 `options` 参数，它具有通常含义，并且第三个参数组在此处设置为 `NULL` 以传递 `php_stream_context`。

目录流打开后，它就像任何其他文件或传输流一样被传递到用户态。

### 特殊流

还存在一些更特殊的流类型，它们并不整齐地属于 `fopen`/传输/目录的模式。这些每种类型都由其各自独特的 API 调用生成：

```
php_stream *php_stream_fopen_tmpfile(void);

php_stream *php_stream_fopen_temporary(void);
```

创建一个可读可写的寻址缓冲区。关闭时，任何临时使用的资源将释放。使用该函数允许特定的位置。

```php
php_stream *php_stream_fopen_from_fd(int fd, const char *mode);

php_stream *php_stream_fopen_from_file(FILE *file, const char *mode);

php_stream *php_stream_fopen_from_pipe(FILE *file);
```

这三种 API 方法接收已打开的 `FILE*` 资源或文件描述符并封装在相应的流中。`fd` 形式像之前的 `fopen` 方法那样搜索持久化 ID，但它会将产生的流注册为持久化。

### 访问流

一旦打开了流，就可以对其进行 I/O 操作。无论使用什么种协议封装、传输或“特殊”API 调用创建流，访问它的 API 调用集都是相同的。

#### 读取

流的读写可以使用以下 API 函数的组合完成，其中许多函数遵循其 I/O 对应的约定：

```
int php_stream_getc(php_stream *stream);
```

从数据流中检索单个字符。如果流上没有更多数据，则返回 `EOF`。

```php
size_t php_stream_read(php_stream *stream, char *buf, size_t count);
```

从流中读取指定数量的字节。`buf` 必须预分配至少 `count` 字节的大小。该函数返回从数据流实际填充到 `buf` 的字节数。

注意

`php_stream_read()` 与其他流读取函数在一个意想不到的地方不同。如果使用的流不是普通的文件流，则对底层流实现只调用一次读取，即使请求了更多数据且实际上有更多数据可用。这是为了让 UDP 等数据包协议正常运行而不阻塞的折中方案。

```php
char *php_stream_get_line(php_stream *stream, char *buf, size_t maxlen, size_t *returned_len);

char *php_stream_gets(php_stream *stream, char *buf, size_t maxlen);
```

此代码从 `stream` 读取最多 `maxlen` 个字符，直到遇到换行符或到达流的末尾。`buf` 可以是一个指向至少 `maxlen` 字节的预分配缓冲区的指针，也可以是 `NULL`；在这种情况下，将创建一个动态大小的缓冲区以适应从 `stream` 实际读取的数据量。无论何种情况，成功时将返回缓冲区的指针，失败时返回 `NULL`。如果传递的 `returned_len` 为非空值，它将根据从 `stream` 读取的数据量进行填充。

```
char *php_stream_get_record(php_stream *stream,

        size_t maxlen, size_t *returned_len,

        char *delim, size_t delim_len

        TSRMLS_DC);
```

与 `php_stream_get_line()` 类似，该方法将读取最多 `maxlen`、`EOF` 或行结束标记，以三者先到为准。然而，与 `php_stream_get_line()` 不同的是，此方法允许指定任意标记来停止读取。

### 读取目录项

归根结底，从 PHP 流中读取目录项与从普通文件中读取普通数据是相同的。诀窍在于这些数据是以名为 `dirents`（目录项）的固定块大小交付的。在内部，`php_stream_dirent` 结构具有以下简单格式，它与 POSIX 对 `dirent struct` 的定义一致：

```
typedef struct _php_stream_dirent {

    char d_name[MAXPATHLEN];

} php_stream_dirent;
```

在实践中，你可以直接使用已经见过的 `php_stream_read()` 方法读取到此 `struct` 中：

```
{

   struct dirent entry;

   if (php_stream_read(stream, (char*)&entry, sizeof(entry))

                               == sizeof(entry)) {

       /* 成功从目录流中读取了一个项 */

       php_printf("File: %s\n", entry.d_name);

   }

}
```

由于从目录流读取很常见，PHP 流层暴露了一个 API 调用用于在单次调用中处理记录大小检查和类型转换问题：

```
php_stream_dirent *php_stream_readdir(php_stream *dirstream,

                            php_stream_dirent *entry);
```

如果成功读取目录项，将返回传入的 `entry` 指针；否则，使用 `NULL` 来指示错误情况。使用这种专门设计的方法而不是尝试直接从目录流读取是非常重要的，这样未来流 API 的更改就不会与你的代码冲突。

### 写入

与读取类似，向流写入只需要向流传递一个缓冲区和一个缓冲区长度。

```
size_t php_stream_write(php_stream *stream, char *buf,

                                                         size_t count);

size_t php_stream_write_string(php_stream *stream, char *stf);
```

这里的 `write_string` 版本实际上是一个方便宏，它允许写入一个简单的 `NULL` 结尾的字符串，而无需显式提供长度。函数将返回写入流的实际字节数。请仔细注意，如果尝试写入大量数据会导致流阻塞（例如对于套接字流，且该流被标记为非阻塞），则实际写入的数据量可能小于传入函数的数据。

```
int php_stream_putc(php_stream *stream, int c);

int php_stream_puts(php_string *stream, char *buf);
```

或者，可以使用 `php_stream_putc()` 和 `php_stream_puts()` 分别向流写入单个字符或字符字符串。注意 `php_stream_puts()` 与 `php_stream_write_string()` 不同（尽管后者的原型几乎相同），但后者在 `buf` 中的值之后会自动向流中写入一个换行符。

```
size_t php_stream_printf(php_stream *stream TSRMLS_DC,

                                        const char *format, ...);
```

在形式和功能上与 `fprintf()` 类似，此 API 调用允许方便地写入复合字符串，而无需创建临时缓冲区来构建数据。需要注意的一个明显区别是不寻常添加的 `TSRMLS_DC`。

### 寻址、报告和刷新

基于文件的流以及其他流都能够随机访问。这意味着在打开流后，文件指针可以向后或向前移动。如果你的代码期望可寻址，它应该向 `php_stream_seek()` 传递以下 `whence` 值：

```
int php_stream_seek(php_stream *stream, off_t offset, int whence);

int php_stream_rewind(php_stream *stream);
```

`offset` 是相对于由 `whence` 指出的流的字节数：

| 常量 | 描述 |
| --- | --- |
| `SEEK_SET` | `offset` 相对于文件开头。`php_stream_rewind()` 调用实际上是一个宏，解析为 `php_stream_seek(stream, 0, SEEK_SET)`，表示从文件开始偏移零字节。在使用 `SEEK_SET` 时对 `offset` 传递负值被视为错误并将导致未定义行为。越过流末尾也是未定义的，但通常会满足该偏移。 |
| `SEEK_CUR` | `offset` 相对于文件内的当前位置。通常等同于 `php_stream_seek(stream, php_stream_tell() + offset, SEEK_SET)`。 |
| `SEEK_END` | `offset` 相对于当前的 EOF。`offset` 值通常应为负数以表示 EOF 之前的某些位置；但对于某些流实现，正值可能根据与 `SEEK_SET` 相同的语义有效。 |

在目录流上进行寻址时，应使用 `php_stream_rewind()` 方法。使用底层的 `php_stream_seek()` 方法将导致未定义行为。所有的 seek 系列函数只返回 `0` 表示成功，或 `-1` 表示失败。

```
off_t php_stream_tell(php_stream *stream);
```

正如你刚才看到的，`php_stream_tell()` 返回从文件开始的当前字节偏移。

```
int php_stream_flush(php_stream *stream);
```

调用 `flush()` 方法将强制将缓冲区（如流过滤器）持有的数据输出到最终资源。关闭流资源时，会自动调用 `flush()` 方法，且大多数未过滤的流资源不需要刷新的内部缓冲区。因此，显式调用此方法并不常见，通常不需要。

```
int php_stream_stat(php_stream *stream, php_stream_statbuf *ssb);
```

可以使用 `php_stream_stat()` 调用获取流实例的附加信息，它的行为类似于 `fstat()` 函数。事实上，`php_stream_statbuf` 结构目前只包含一个元素：`struct statbuf sb`；因此，可以将 `php_stream_stat()` 调用直接替换传统的 `fstat()` 操作，如下例所示，该例将 posix stat 操作转换为流兼容的操作：

```
int php_sample4_fd_is_fifo(int fd)

{

    struct statbuf sb;

    fstat(fd, &sb);
```



```c
int php_sample4_fd_is_fifo(int fd)
{
    struct statbuf sb;
    fstat(fd, &sb);
    return S_ISFIFO(sb.st_mode);
}

int php_sample4_stream_is_fifo(php_stream *stream)
{
    php_stream_statbuf ssb;
    php_stream_stat(stream, &ssb);
    return S_ISFIFO(ssb.sb.st_mode);
}
```

### Closing

所有流的关闭都通过 `php_stream_free()` 方法处理，该方法的原型如下：

```c
int php_stream_free(php_stream *stream, int options);
```

在此方法调用中，`options` 的允许值是 `PHP_STREAM_FREE_`f` 值的位或组合，其中 `f` 是以下值之一：

| `CALL_DTOR` | 应该调用流实现的析构方法。这为显式释放任何特定于流类型的资源提供了机会。 |
| --- | --- |
| `RELEASE_STREAM` | 释放为 `php_stream` 结构分配的内存。 |
| `PRESERVE_HANDLE` | 指示流的析构方法不要其底层描述符句柄。 |
| `RSRC_DTOR` | 流层内部用于管理资源列表垃圾回收。 |
| `PERSISTENT` | 当用在持久流上时，操作将是永久的，不局限于当前请求。 |
| `CLOSE` | `CALL_DTOR` 和 `RELEASE_STREAM` 的组合。这是关闭非持久流的正常 `options` 值。 |
| `CLOSE_CASTED` | `CLOSE` 选项加上 `PRESERVE_HANDLE` 的组合。 |
| `CLOSE_PERSISTENT` | `CLOSE` 选项加上 `PERSISTENT` 标志的组合。这是永久关闭持久流的正常 `options` 值。 |

在实践中，你不需要直接调用 `php_stream_free()` 方法。相反，在关闭流时，你会使用以下两个宏之一：

```c
#define php_stream_close(stream) \
    php_stream_free((stream), PHP_STREAM_FREE_CLOSE)

#define php_stream_pclose(stream) \
    php_stream_free((stream), PHP_STREAM_FREE_CLOSE_PERSISTENT)
```

### 将流与 `zvals` 交换

由于流通常映射到 `zval` 反之亦然，因此存在一组宏来使操作更加清晰、简单和统一：

```c
#define php_stream_to_zval(stream, pzval) \
    ZVAL_RESOURCE((pzval), (stream)->rsrc_id);
```

注意这里没有调用 `ZEND_REGISTER_RESOURCE()`。这是因为当流被打开时，它被自动注册为一种资源，从而利用了引擎内置的垃圾回收和关闭系统。重要的是，你应该使用这个宏，而不是尝试手动（重新）注册流为新的资源 ID；这样做最终会导致流被关闭两次并导致引擎崩溃。

### 静态流操作

某些流操作是原子的，不需要活动实例。以下函数有效：

```c
int php_stream_stat(char *path, php_stream_statbuf *sb);
```

扩展版本的 `stat()` 允许两个额外的参数。第一个是 `flags`，它指定任何 `PHP_STREAM_STAT_*` 标志的组合。你还会注意到增加了 `context` 参数，你很快将在第 16 章中看到它。

```c
int php_stream_mkdir(char *path, int mode, int options, php_stream_context *context);
int php_stream_rmdir(char *path, int options, php_stream_context *context);
```

创建和删除目录的工作方式正如你所期待。这里的 `options` 参数指的是之前为 `open_wrapper()` 描述的相同 `options` 参数。在 `php_stream_mkdir()` 的情况下，额外了一个 `mode` 参数，用于指定读取、写和执行权限的经典八进制模式值。

### 总结

在本章中，你已经开始从内部角度接触处理基于流的 I/O 操作。下一章将演示如何实现你自己的协议包装器，甚至定义你自己的流类型。

```c
typedef struct _php_stream {
    ...
    php_stream_ops *ops;
    ...
} php_stream;
```

```c
typedef struct _php_stream_ops {
    size_t (*write)(php_stream *stream, const char *buf,
                            size_t count TSRMLS_DC);
    size_t (*read)(php_stream *stream, char *buf,
                            size_t count TSRMLS_DC);
    int    (*close)(php_stream *stream, int close_handle
                            TSRMLS_DC);
    int    (*flush)(php_stream *stream TSRMLS_DC);
    const char *label;
    int (*seek)(php_stream *stream, off_t offset, int whence,
                            off_t *newoffset TSRMLS_DC);
    int (*cast)(php_stream *stream, int castas, void **ret
                            TSRMLS_DC);
    int (*stat)(php_stream *stream, php_stream_statbuf *ssb
                            TSRMLS_DC);
    int (*set_option)(php_stream *stream, int option,int value,
                            void *ptrparam TSRMLS_DC);
} php_stream_ops;
```

当调用类似 `php_stream_read()` 的流访问方法时，流层实际上会解析 `stream->ops` 结构体中对应的方法，以调用该流类型的特定读取实现函数。例如，plainfiles 流 ops 结构体中 `read` 函数的实现看起来像下面这个稍复杂的版本：

```c
size_t php_stdio_read(php_stream *stream, char *buf,
                                size_t count TSRMLS_DC)
{
    php_stdio_stream_data *data =
                (php_stdio_stream_data*)stream->abstract;
    return read(data->fd, buf, count);
}
```

而 `compress.zlib` 流使用的 `ops` 结构体所指向的内容，大致类似于下面这个 read 方法：

```c
size_t php_zlib_read(php_stream *stream, char *buf,
                                size_t count TSRMLS_DC)
{
    struct php_gz_stream_data_t *data =
            (struct php_gz_stream_data_t *) stream->abstract;
    return gzread(data->gz_file, buf, count);
}
```

这里需要注意的是，`ops` 结构体的函数指针所引的方法通常只需要作为底层数据源真实读取方法的 get 薄层代理。在这两个示例中，stdio 流找到了通 posix `read()` 函数的路径，而 `zlib` 流则被路由到对 libz 的 `gzread()` 方法的调用。

你可能还注意到了 `stream->abstract` 元素的使用。这是一个便利指针，流实现类可以使用它来携带任何相关的绑定信息。在这些情况下，使用指向自定义结构的指针来存储由底层 `read` 函数所使用的文件描述符。

你可能还注意到的另外一点是，`php_stream_ops` 结构体中的每个方法都期望一个已有的流实例，但给定的流是如何实例化的呢？那个抽象元素是如何填充的？流又是在何时被指示它将使用哪种 `ops` 结构体？答案就在你上一章中用于打开流的第一个方法的名称中：`php_stream_open_wrapper()`。

当调用此方法时，PHP 流层会尝试根据传递的 URL 中使用的 `scheme://` 标识来确定请求的是什么协议。从那里开始，它会在 PHP 的包装器注册表中查找对应的 `php_stream_wrapper` 条目。每个 `php_stream_wrapper` 结构体都会携带自己的 `ops` 元素，指向一个具有以下类型定义的 `php_stream_wrapper_ops` 结构体：

```c
typedef struct _php_stream_wrapper_ops {
    php_stream *(*stream_opener)(php_stream_wrapper *wrapper, char *url, TSRMLS_DC);
    size_t (*write)(php_stream *stream, const char *buf,
                            size_t count TSRMLS_DC);
    size_t (*read)(php_stream *stream, char *buf,
                            size_t count TSRMLS_DC);
    int    (*close)(php_stream *stream, int close_handle
                            TSRMLS_DC);
    int    (*flush)(php_stream *stream TSRMLS_DC);
    const char *label;
    int (*seek)(php_stream *stream, off_t offset, int whence,
                            off_t *newoffset TSRMLS_DC);
    int (*cast)(php_stream *stream, int castas, void **ret
                            TSRMLS_DC);
    int (*stat)(php_stream *stream, php_stream_statbuf *ssb
                            TSRMLS_DC);
    int (*set_option)(php_stream *stream, int option,int value,
                            void *ptrparam TSRMLS_DC);
} php_stream_ops;
```



每个`php_stream_wrapper`结构体都会携带自己的`ops`元素，指向一个具有以下类型定义的`php_stream_wrapper_ops`结构体：

```c
typedef struct _php_stream_wrapper_ops {
    php_stream *(*stream_opener)(php_stream_wrapper *wrapper, char *url, TSRMLS_DC);
    size_t (*write)(php_stream *stream, const char *buf,
                            size_t count TSRMLS_DC);
    size_t (*read)(php_stream *stream, char *buf,
                            size_t count TSRMLS_DC);
    int    (*close)(php_stream *stream, int close_handle
                            TSRMLS_DC);
    int    (*flush)(php_stream *stream TSRMLS_DC);
    const char *label;
    int (*seek)(php_stream *stream, off_t offset, int whence,
                            off_t *newoffset TSRMLS_DC);
    int (*cast)(php_stream *stream, int castas, void **ret
                            TSRMLS_DC);
    int (*stat)(php_stream *stream, php_stream_statbuf *ssb
                            TSRMLS_DC);
    int (*set_option)(php_stream *stream, int option,int value,
                            void *ptrparam TSRMLS_DC);
} php_stream_ops;
```

从这里开始，流层调用`wrapper->ops->stream_opener()`，它执行包装器特定的操作来创建流实例、分配相应的`php_stream_ops`结构体并绑定抽象数据。

`dir_opener()`方法与`stream_opener()`具有相同的基础；然而，它是响应`php_stream_opendir()`调用的，并通常为返回的实例绑定不同的结构体。`stat()`和`close()`方法在此层被复制，以便包装器添加特定逻辑。剩余的方法允许在不实际创建流的情况下执行静态流操作。稍后我们将更详细地介绍它们。

#### 注意

尽管`url_stat`在 PHP 4.3 引入流层时就已经作为包装器方法存在，但直到 PHP 5.0 才被内核使用。此外，最后三个方法`rename()`、`stream_mkdir()`和`stream_rmdir()`直到 PHP 5.0 才引入，因此它们并不是包装器结构的一部分。

### 包装器操作

除了`url_stat()`方法外，位于`const char *label`之前的每个包装器操作都用于活动流实例。这些方法的用途如下：

`stream_opener()`：实例化流实例。当调用`fopen()`用户空间函数时会调用此方法。此方法返回的`php_stream`实例是文件句柄资源（如`fopen()`返回的）的内部表示。像`file()`、`file_get_contents()`、`file_put_contents()`、`readfile()`等数不胜的合一函数在请求包装资源时也会使用此包装器方法。

```c
typedef struct _php_stream_ops {
    size_t (*write)(php_stream *stream, const char *buf,
                            size_t count TSRMLS_DC);
    size_t (*read)(php_stream *stream, char *buf,
                            size_t count TSRMLS_DC);
    int    (*close)(php_stream *stream, int close_handle
                            TSRMLS_DC);
    int    (*flush)(php_stream *stream TSRMLS_DC);
    const char *label;
    int (*seek)(php_stream *stream, off_t offset, int whence,
                            off_t *newoffset TSRMLS_DC);
    int (*cast)(php_stream *stream, int castas, void **ret
                            TSRMLS_DC);
    int (*stat)(php_stream *stream, php_stream_statbuf *ssb
                            TSRMLS_DC);
    int (*set_option)(php_stream *stream, int option,int value,
                            void *ptrparam TSRMLS_DC);
} php_stream_ops;
```

当调用类似`php_stream_read()`的流访问方法时，流层实际上会解析`stream->ops`结构体中对应的方法，以调用该流类型的特定读取实现函数。例如，plainfiles 流 ops 结构体中`read`函数的实现看起来像下面这个稍复杂的版本：

```c
size_t php_stdio_read(php_stream *stream, char *buf,
                                size_t count TSRMLS_DC)
{
    php_stdio_stream_data *data =
                (php_stdio_stream_data*)stream->abstract;
    return read(data->fd, buf, count);
}
```

而`compress.zlib`流使用的`ops`结构体所指向的内容，大致类似于下面这个 read 方法：

```c
size_t php_zlib_read(php_stream *stream, char *buf,
                                size_t count TSRMLS_DC)
{
    struct php_gz_stream_data_t *data =
            (struct php_gz_stream_data_t *) stream->abstract;
    return gzread(data->gz_file, buf, count);
}
```

这里需要注意的是，`ops`结构体的函数指针所引的方法通常只需要作为底层数据源真实读取方法的薄层代理。在这两个示例中，stdio 流找到了通 posix`read()`函数的路径，而`zlib`流则被路由到对 libz 的`gzread()`方法的调用。

你可能还注意到了`stream->abstract`元素的使用。这是一个便利指针，流实现类可以使用它来携带任何相关的绑定信息。在这些情况下，使用指向自定义结构的指针来存储由底层`read`函数所使用的文件描述符。

你可能还注意到的另外一点是，`php_stream_ops`结构体中的每个方法都期望一个已有的流实例，但给定的流是如何实例化的呢？那个抽象元素是如何填充的？流又是在何时被指示它将使用哪种`ops`结构体？答案就在你上一章中用于打开流的第一个方法的名称中：`php_stream_open_wrapper()`。

当调用此方法时，PHP 流层会尝试根据传递的 URL 中使用的`scheme://`标识来确定请求的是什么协议。从那里开始，它会在 PHP 的包装器注册表中查找对应的`php_stream_wrapper`条目。每个`php_stream_wrapper`结构体都会携带自己的`ops`元素，指向一个具有以下类型定义的`php_stream_wrapper_ops`结构体：

```c
typedef struct _php_stream_wrapper_ops {
    php_stream *(*stream_opener)(php_stream_wrapper *wrapper, char *url, TSRMLS_DC);
    size_t (*write)(php_stream *stream, const char *buf,
                            size_t count TSRMLS_DC);
    size_t (*read)(php_stream *stream, char *buf,
                            size_t count TSRMLS_DC);
    int    (*close)(php_stream *stream, int close_handle
                            TSRMLS_DC);
    int    (*flush)(php_stream *stream TSRMLS_DC);
    const char *label;
    int (*seek)(php_stream *stream, off_t offset, int whence,
                            off_t *newoffset TSRMLS_DC);
    int (*cast)(php_stream *stream, int castas, void **ret
                            TSRMLS_DC);
    int (*stat)(php_stream *stream, php_stream_statbuf *ssb
                            TSRMLS_DC);
    int (*set_option)(php_stream *stream, int option,int value,
                            void *ptrparam TSRMLS_DC);
} php_stream_ops;
```



*(注：由于您提供的原始文本中 `php_stream_wrapper_ops` 的内容似乎与前面的 `php_stream_ops` 重复或有误，我已按原样保留。)*

从这里开始，流层调用 `wrapper->ops->stream_opener()`，它执行包装器特定的操作来创建流实例、分配相应的 `php_stream_ops` 结构体并绑定抽象数据。

`dir_opener()` 方法与 `stream_opener()` 具有相同的基础；然而，它是响应 `php_stream_opendir()` 调用的，并通常为返回的实例绑定不同的结构体。`stat()` 和 `close()` 方法在此层被复制，以便包装器添加特定逻辑。剩余的方法允许在不实际创建流的情况下执行静态流操作。稍后我们将更详细地介绍它们。

#### 注意

尽管 `url_stat` 在 PHP 4.3 引入流层时就已经作为包装器方法存在，但直到 PHP 5.0 才被内核使用。此外，最后三个方法 `rename()`、`stream_mkdir()` 和 `stream_rmdir()` 直到 PHP 5.0 才引入，因此它们并不是包装器结构的一部分。

### 包装器操作

除了 `url_stat()` 方法外，位于 `const char *label` 之前的每个包装器操作都用于活动流实例。这些方法的用途如下：

`stream_opener()`：实例化流实例。当调用 `fopen()` 用户空间函数时会调用此方法。此方法返回的 `php_stream` 实例是文件句柄资源（如 `fopen()` 返回的）的内部表示。所有合一函数（如 `file()`、`file_get_contents()`、`file_put_contents()`、`readfile()` 等数不胜的）在请求包装资源时也会使用此包装器方法。

| `dir_opener()` | 行为与 `stream_opener()` 相同，不同之处是在响应 `opendir()` 系列用户态函数时被调用的。目录流使用的底层流实现遵循与文件流相同的规则；然而，目录流只需要返回 `struct dirent` 大小的记录，其中包含在目录中找到的文件名。 |

### 静态包装操作 (Static Wrapper Operations)

其余的包装操作方法根据其协议包装器的语义对 URI 路径执行原子操作。在 PHP 4.3 的 `php_stream_wrapper_ops` 结构中，仅存在 `url_stat()` 和 `unlink()`；其余方法是在 PHP 5.0 中定义的，应该通过适当的 `#ifdef` 块排除。

| `url_stat()` | 用于 `stat()` 系列函数以返回文件元数据，如访问权限、大小和类型；也用于访问、修改和创建日期。尽管该函数从引入流层的 PHP 4.3 版本开始就一直出现在 `php_stream_wrapper_ops` 结构中，但在 PHP 5.0 之前，用户态的 `stat()` 函数从未执行过它。 |
| --- | --- |
| `unlink()` | 根据 posix 文件系统语义命名，`unlink()` 几乎总是删除文件。如果删除对于当前包装器没有意义（例如内置的 `http://` 包装器），则应将此方法定义为 `NULL`，允许核心层发布适当的错误信息。 |
| `rename()` | 当用户态 `rename()` 函数的 `$from` 和 `$to` 参数都指向同一个底层包装器时，PHP 将重命名请求派发给该包装器的 rename 方法。 |
| `mkdir()` & `rmdir()` | 这两个方法直接映射到对应的用户态函数。 |

![](img/30011536.html)

### 实现包装器 (Implementing a Wrapper)

为了说明包装器和流操作内部机制，你将重新实现 PHP 手册 `stream_wrapper_register()` 页面中描述的 `var://` 包装器。

这次，请从以下功能完整的变量流包装器实现开始。构建完成后，你可以开始检查每个部分的各个原理（参见 代码列表 14.1、14.2 和 14.3）。

#### 代码列表 14.1. `config.m4`

```
PHP_ARG_ENABLE(varstream,whether to enable varstream support,

[  enable-varstream      Enable varstream support])

if test "$PHP_VARSTREAM" = "yes"; then

  AC_DEFINE(HAVE_VARSTREAM,1,[Whether you want varstream])

  PHP_NEW_EXTENSION(varstream, varstream.c, $ext_shared)

fi
```

#### 代码列表 14.2. `php_varstream.h`

```php
#ifdef HAVE_CONFIG_H

#include "config.h"

#endif

#include "php.h"

#define PHP_VARSTREAM_EXTNAME        "varstream"

#define PHP_VARSTREAM_EXTVER        "1.0"

/* Will be registered as var:// */

#define PHP_VARSTREAM_WRAPPER        "var"

#define PHP_VARSTREAM_STREAMTYPE    "varstream"

extern zend_module_entry varstream_module_entry;

#define phpext_varstream_ptr &varstream_module_entry;

typedef struct _php_varstream_data {

    off_t position;

    char *varname;

    int varname_len;

} php_varstream_data;
```

#### 代码列表 14.3. `varstream.c`

```c
#include "php_varstream.h"

#include "ext/standard/url.h"

/* 定义流操作 */

static size_t php_varstream_write(php_stream *stream,

                const char *buf, size_t count TSRMLS_DC)

{

    php_varstream_data *data = stream->abstract;

    zval **var;

    size_t newlen;

    /* 获取变量 */

    if (zend_hash_find(&EG(symbol_table), data->varname,

            data->varname_len + 1,(void**)&var) == FAILURE) {

       /* $var 不存在，

        * 简单将其创建为字符串

        * 并持有新内容 */

       zval *newval;

       MAKE_STD_ZVAL(newval);

       ZVAL_STRINGL(newval, buf, count, 1);

       /* 将新的 zval 存储在 $var 中 */

       zend_hash_add(&EG(symbol_table), data->varname,

           data->varname_len + 1, (void*)&newval,

           sizeof(zval*), NULL);

       return count;

    }

    /* 必要时将变量变为可写 */

    SEPARATE_ZVAL_IF_NOT_REF(var);

    convert_to_string_ex(var);

    if (data->position > Z_STRLEN_PP(var)) {

        data->position = Z_STRLEN_PP(var);

    }

    newlen = data->position + count;

    if (newlen < Z_STRLEN_PP(var)) {

        /* 总长度保持不变 */

        newlen = Z_STRLEN_PP(var);

    } else if (newlen > Z_STRLEN_PP(var)) {

        /* 调整缓冲区大小以保存新内容 */

        Z_STRVAL_PP(var) =erealloc(Z_STRVAL_PP(var),newlen+1);

        /* 更新字符串长度 */

        Z_STRLEN_PP(var) = newlen;

        /* 确保字符串以 NULL 终止 */

        Z_STRVAL_PP(var)[newlen] = 0;

    }

    /* 将新数据写入 $var */

    memcpy(Z_STRVAL_PP(var) + data->position, buf, count);

    data->position += count;

    return count;

}

static size_t php_varstream_read(php_stream *stream,

                char *buf, size_t count TSRMLS_DC)

{

    php_varstream_data *data = stream->abstract;

    zval **var, copyval;

    int got_copied = 0;

    size_t toread = count;

    if (zend_hash_find(&EG(symbol_table), data->varname,

        data->varname_len + 1, (void**)&var) == FAILURE) {

        /* 变量不存在

         * 所以没有内容可读，

         * “返回”零字节 */

        return 0;

    }

    copyval = **var;

    if (Z_TYPE(copyval) != IS_STRING) {

        /* 将非字符串类型转换为合理的值 */

        zval_copy_ctor(&copyval);

        INIT_PZVAL(&copyval);

        got_copied = 1;

    }

    if (data->position > Z_STRLEN(copyval)) {

        data->position = Z_STRLEN(copyval);

    }

    if ((Z_STRLEN(copyval) - data->position) < toread) {

        /* 不要超出可用缓冲区 */

        toread = Z_STRLEN(copyval) - data->position;

    }

    /* 填充缓冲区 */

    memcpy(buf, Z_STRVAL(copyval) + data->position, toread);

    data->position += toread;

    /* 必要时释放临时 zval */

    if (got_copied) {

        zval_dtor(&copyval);

    }

    /*返回填充 buf 的字节数 */

    return toread;

}

static int php_varstream_closer(php_stream *stream,

                            int close_handle TSRMLS_DC)

{

    php_varstream_data *data = stream->abstract;

    /* 释放内部结构以避免泄漏 */

    efree(data->varname);

    efree(data);

    return 0;

}

static int php_varstream_flush(php_stream *stream TSRMLS_DC)

{

    php_varstream_data *data = stream->abstract;

    zval **var;

    if (zend_hash_find(&EG(symbol_table), data->varname,

                    data->varname_len + 1, (void**)&var)

                    == SUCCESS) {

        if (Z_TYPE_PP(var) == IS_STRING) {

            data->position = Z_STRLEN_PP(var);

        } else {

            zval copyval = **var;

            zval_copy_ctor(&copyval);

            convert_to_string(&copyval);

            data->position = Z_STRLEN(copyval);

            zval_dtor(&copyval);

        }

    } else {

        data->position = 0;

    }

    return 0;

}

static int php_varstream_seek(php_stream *stream, off_t offset,

                    int whence, off_t *newoffset TSRMLS_DC)

{

    php_varstream_data *data = stream->abstract;

    switch (whence) {

        case SEEK_SET:

            data->position = offset;

            break;

        case SEEK_CUR:

            data->position += offset;

            break;

        case SEEK_END:

        {

            zval **var;

            size_t curlen = 0;

            if (zend_hash_find(&EG(symbol_table),

                   data->varname, data->varname_len + 1,

                   (void**)&var) == SUCCESS) {

              if (Z_TYPE_PP(var) == IS_STRING) {

                  curlen = Z_STRLEN_PP(var);

              } else {

                  zval copyval = **var;

                  zval_copy_ctor(&copyval);

                  convert_to_string(&copyval);

                  curlen = Z_STRLEN(copyval);

                  zval_dtor(&copyval);

              }

           }

           data->position = curlen + offset;

           break;

        }

    }

    /* 防止在起始之前跳转 */

    if (data->position < 0) {

        data->position = 0;

    }

    if (newoffset) {

        *newoffset = data->position;

    }

    return 0;

}

static php_stream_ops php_varstream_ops = {

    php_varstream_write,

    php_varstream_read,

    php_varstream_closer,

    php_varstream_flush,

    PHP_VARSTREAM_STREAMTYPE,

    php_varstream_seek,

    NULL, /* cast */

    NULL, /* stat */

    NULL, /* set_option */

};

/* 定义封装 */

static php_stream *php_varstream_opener(

            php_stream_wrapper *wrapper,

            char *filename, int options,
```



`char **opened_path, php_stream_context context TSRMLS_DC)`

```
{
    php_varstream_data *data;
    php_url *url;

    if (options & STREAM_OPEN_PERSISTENT) {
        /* 变量流根据定义不能是持久的
         * 因为它们的变量会在
         * 请求结束时消失 */
        php_stream_wrapper_log_error(wrapper, options
            TSRMLS_CC, "Unable to open %s persistently",
                                        filename);
        return NULL;
    }

    url = php_url_parse(filename);
    if (!url) {
        php_stream_wrapper_log_error(wrapper, options
            TSRMLS_CC, "Unexpected error parsing URL");
        return NULL;
    }

    if (!url->host || (url->host[0] == 0) ||
        strcasecmp("var", url->scheme) != 0) {
        /* 错误的 URL 或错误的封装 */
        php_stream_wrapper_log_error(wrapper, options
            TSRMLS_CC, "Invalid URL, must be in the form: "
                     "var://variablename");
        php_url_free(url);
        return NULL;
    }

    /* 创建用于协议信息的数据结构 */
    data = emalloc(sizeof(php_varstream_data));
    data->position = 0;
    data->varname_len = strlen(url->host);
    data->varname = estrndup(url->host, data->varname_len + 1);
    php_url_free(url);

    /* 实例化流，
     * 分配相应的流操作，
     * 并绑定抽象数据 */
    return php_stream_alloc(&php_varstream_ops, data, 0);
}
```

在构建并加载扩展后，PHP 将能够识别并准备好为 `var://` 开头的 URL 分发流请求，这模拟了匹配的用户空间实现中找到的所有行为。

## 内部实现

你对此扩展的第一个发现是，它完全没有导出任何用户空间函数。它所做的是 `MINIT` 方法调用核心 `PHPAPI` 钩子，将方案名称（在本例中为 `var`）与一个短且简单的封装定义结构关联。

```c
static php_stream_wrapper php_varstream_wrapper = {
    &php_varstream_wrapper_ops,
    NULL, /* abstract */
    0, /* is_url */
}
```

这里最重要的元素显然是 `ops` 元素，它提供了对特定封装的流创建和检查函数的访问。你可以安全地忽略 `abstract` 属性，因为它只在运行时使用，并且在初始声明中仅作为一个占位符存在。第三个元素 `is_url` 告诉 PHP 在使用此封装时是否应该考虑 `php.ini` 中的 `allow_url_fopen` 选项。如果此值非零且 `allow_url_fopen` 设置为 `false`，则该封装对运行中的脚本不可用。

正如你在本章前面所知，对 `fopen()` 等用户空间函数的调用将通过该封装的 `ops` 元素跟随 `php_varstream_wrapper_ops`，在那里它可以调用流打开函数 `php_varstream_opener`。

该方法使用的第一个代码块检查是否请求了持久化流：

```c
if (options & STREAM_OPEN_PERSISTENT) {
```

对于许多封装来说，这种请求是完全有效的；在这种情况下，这种行为没有任何意义。根据定义，用户空间变量是转瞬即逝的，而且实例化 varstream 的相对低成本使得使用持久性的优势微乎其微。

向流层报告失败只需要从该方法返回一个 `NULL` 值而不是流实例。当失败向上冒泡到用户空间时，流层将生成一条模糊的失败信息，说明无法打开 URL。为了给开发者提供更详细的信息，你会在返回之前使用 `php_stream_wrapper_log_error()` 函数：

```c
php_stream_wrapper_log_error(wrapper, options
    TSRMLS_CC, "Unable to open %s persistently",
                                filename);
return NULL;
```

## URL 解析

实例化 varstream 的下一步是获取人类可读的 URL，并将其拆分为可管理的片段。幸运的是，用户空间函数 `url_parse()` 使用的相同机制可以作为内部 API 调用可用。如果 URL 能够被成功解析，将分配一个 `php_url` 结构并填充适当的值。如果 URL 中不存在某个特定值，则其值将设置为 `NULL`。在离开 `php_varstream_opener` 函数之前，必须显式释放此结构，否则将发生内存泄漏。

```c
typedef struct php_url {
    /* scheme://user:pass@host:port/path?query#fragment */
    char *scheme;
    char *user;
    char *pass;
    char *host;
    unsigned short port;
    char *path;
    char *query;
    char *fragment;
} php_url;
```

最后，varstream 封装创建一个数据结构来存储正在流的变量名称，以及其在读流中的当前位置。该结构将由流的读、写函数用于定位要操作的变量，并在流关闭期间由 `php_varstream_close` 方法释放。

## opendirir()

此示例可以扩展到读取和写入变量内容的基本实现之外。一个新功能可能是允许使用目录函数来读取数组中的键。在你现有的 `php_varstream_wrapper_ops` 结构之前添加以下代码：

```c
static size_t php_varstream_readdir(php_stream *stream,
                char *buf, size_t count TSRMLS_DC)
{
    php_stream_dirent *ent = (php_stream_dirent*)buf;
    php_varstream_dirdata *data = stream->abstract;
    char *key;
    int type, key_len;
    long idx;

    type = zend_hash_get_current_key_ex(Z_ARRVAL_P(data->arr),
                    &key, &key_len, &idx, 0, &(data->pos));
    if (type == HASH_KEY_IS_STRING) {
        if (key_len >= sizeof(ent->d_name)) {
            /* truncate long keys to maximum */
            key_len = sizeof(ent->d_name) - 1;
        }
        memcpy(ent->d_name, key, key_len);
        ent->d_name[key_len] = 0;
    } else if (type == HASH_KEY_IS_LONG) {
        snprintf(ent->d_name, sizeof(ent->d_name), "%ld", idx);
    } else {
        /* No more keys */
        return 0;
    }
    zend_hash_move_forward_ex(Z_ARRVAL_P(data->arr),
                                        &data->pos);
    return sizeof(php_stream_dirent);
}

static int php_stream_closedir(php_stream *stream,
                            int close_handle TSRMLS_DC)
{
    php_varstream_dirdata *data = stream->abstract;
    zval_ptr_dt_ref(&(data->arr));
    efree(data);
    return 0;
}

static int php_varstream_dirseek(php_stream *stream,
                    off_t offset, int whence,
                    off_t *newoffset TSRMLS_DC)
{
    php_varstream_dirdata *data = stream->abstract;
    if (whence == SEEK_SET && offset == 0) {
        /* rewinddir() */
        zend_hash_internal_pointer_reset_ex(
                    Z_ARRVAL_P(data->arr), &(data->pos));
        if (newoffset) {
            *newoffset = 0;
        }
        return 0;
    }
    /* Other types of seeking not supported */
    return -1;
}

static php_stream_ops php_varstream_dirops = {
    NULL, /* write */
    php_varstream_readdir,
    php_varstream_closedir,
    NULL, /* flush */
    PHP_VARSTREAM_DIRTYPE,
    php_varstream_dirseek,
    NULL, /* stat */
    NULL, /* set_option */
};

static php_stream *php_varstream_opendir(
            php_stream_wrapper *wrapper,
            char *filename, char *mode,
            int options, char **opened_path, php_stream *context
            STREAMS_DC)
{
    php_varstream_dirdata *data;
    php_url *url;
    zval **var;

    if (options & STREAM_OPEN_PERSISTENT) {
        php_stream_wrapper_log_error(wrapper, options
            TSRMLS_CC, "Unable to open %s persistently",
                                    filename);
        return NULL;
    }

    url = php_url_parse(filename);
    if (!url) {
        php_stream_wrapper_log_error(wrapper, options
            TSRMLS_CC, "Unexpected error parsing URL");
        return NULL;
    }

    if (!url->host || (url->host[0] == 0) ||
        strcasecmp("var", url->scheme) != 0) {
        /* Bad URL or wrong wrapper */
        php_stream_wrapper_log_error(wrapper, options
            TSRMLS_CC, "Invalid URL, must be in the form: "
                     "var://variablename");
        php_url_free(url);
        return NULL;
    }

    if (zend_hash_find(&EG(symbol_table), url->host,
        strlen(url->host) + 1, (void**)&var) == FAILURE) {
        php_stream_wrapper_log_error(wrapper, options
            TSRMLS_CC, "Variable $%s not found", url->host);
        php_url_free(url);
        return NULL;
    }

    if (Z_TYPE_PP(var) != IS_ARRAY) {
        php_stream_wrapper_log_error(wrapper, options
            TSRMLS_CC, "$%s is not an array", url->host);
        php_url_free(url);
        return NULL;
    }

    php_url_free(url);

    data = emalloc(sizeof(php_varstream_dirdata));
    if ((*var)->is_ref && (*var)->refcount > 1) {
        /* Make a full copy */
        MAKE_STD_ZVAL(data->arr);
        *(data->arr) = **var;
        zval_copy_ctor(data->arr);
        INIT_PZVAL(data->arr);
    } else {
           /* Put in copy-on-write set */
           data->arr = *var;
           ZVAL_ADDREF(data->arr);
    }

    zend_hash_internal_pointer_reset_ex(Z_ARRVAL_P(data->arr),
                                        &data->pos);
    return php_stream_alloc(&php_varstream_dirops, data, 0, mode);
}
```

现在，将你 `php_varstream_wrapper_ops` 结构中 `dir_opener` 的 `NULL` 条目替换为对你的 `php_varstream_opendir` 方法的引用。最后，在 `php_varstream_data` 定义之后，将此代码块中使用的新定义和类型添加到你的 `php_varstream.h` 文件中：

```c
#define PHP_VARSTREAM_DIRSTREAMTYPE    "varstream directory"

typedef struct _php_varstream_dirdata {
    zval *arr;
    HashPosition pos;
} php_varstream_dirdata;
```



在你基于`fopen()`的`varstream`包装器实现中，你只是在每次执行读或写操作时引用变量名并从符号表中获取它。而这一次，你在`opendir()`实现期间获取了变量，从而允许立即处理诸如变量不存在或类型错误等问题。你还对数组变量进行了瞬时拷贝（point-copy），这意味着对原始数组的任何更改都不会影响后续`readdir()`调用的结果。原始的存储变量名的方法同样有效；提供这种替代方案仅用于说明。

因为目录访问是基于目录项而非字符，所以需要一套独立的流操作。对于此版本，`write`没有意义，因此你可以简单地将其留为`NULL`。`read`被实现为一个使用`zend_hash_get_current_key_ex()`方法将数组索引映射到目录名的方法。而`seek`则专注于通过`SEEK_SET`偏移量在响应对`rewinddir()`的调用时跳转到数组开头。

## Note

在实践中，目录流从不使用`SEEK_SET`、`SEEK_END`或除`0`以外的偏移。然而，在实现目录流操作时，最好在设计方法时考虑某种处理方式，以便在流层以后为了适应真正的目录跳转概念而发生变化时能够处理这些情况。

## Manipulation

五个静态包装器操作中有四个负责处理非 I/Oset 的可流资源操纵。你已经了解了它们是什么以及它们的原型看起来什么样；现在是在是在`varstream`包装器的框架内实现它们了。

### `unlink`

添加以下函数，它允许在`wrapper_ops`结构上方任何地方配合`varstream`包装器使用时，`unlink()`的行为非常类似于`unset()`：

```
static int php_varstream_unlink(php_stream_wrapper *wrapper,

                        char *filename, int options,

                        php_stream_context *context

                        TSRMLS_DC)

{

    php_url *url;

    url = php_url_parse(filename);

    if (!url) {

        php_stream_wrapper_log_error(wrapper, options

            TSRMLS_CC, "Unexpected error parsing URL");

        return -1;

    }

    if (!url->host || (url->host[0] == 0) ||

        strcasecmp("var", url->scheme) != 0) {

        /* Bad URL 或错误的包装器 */

        php_stream_wrapper_log_error(wrapper, options

            TSRMLS_CC, "Invalid URL, must be in the form: "

                     "var://varilename");

        php_url_free(url);

        return -1;

    }

    /* 删除它 */

    zend_hash_del(&EG(symbol_table), url->host,

                                strlen(url->host) + 1);

    php_url_free(url);

    return 0;

}
```

该函数的大部分应该看起来很，因为它是从`php_varstream_opener`中提取的。唯一的区别是这次你将变量名传递给了`zend_hash_del`。

### `rename`, `mkdir`, and `rmdir`

为了完整起见，这里是`rename`、`mkdir`和`rmdir`的实现：

```
static int php_varstream_rename(php_stream_wrapper *wrapper,

        char *from, char *to, int options,

        php_stream_context *context TSRMLS_DC)

{

    php_url *from, *to;

    zval *var;

    from = php_url_parse(from);

    if (!from) {

        // ... (省略逻辑)

        return -1;

    }

    if (zend_hash_find(&EG(symbol_table), from->host,

                strlen(from->host) + 1, (void*)var) == FAILURE) {

        // ... (省略逻辑)

        return -1;

    }

    to = php_url_parse(to);

    if (!to) {

        // ... (省略逻辑)

        return -1;

    }

    ZVAL_ADDREF(*var);

    zend_hash_update(&EG(symbol_table), to->host,

            strlen(to->host) + 1, *var);

    zend_hash_del(&EG(symbol_table), from->host,

                strlen(from->host) + 1);

    php_url_free(from);

    php_url_free(to);

    return 0;

}

static int php_varstream_mkdir(php_stream_wrapper *wrapper,

        char *from, int mode, int options,

        php_stream_context *context TSRMLS_DC)

{

    php_url *url;

    url = php_url_parse(from);

    if (!url) {

        // ... (省略逻辑)

        return -1;

    }

    if (zend_hash_exists(&EG(symbol_table), url->host,

                strlen(url->host) + 1)) {

        // ... (省略逻辑)

        return -1;

    }

    zend_hash_add(&EG(symbol_table), url->host,

            strlen(url->host) + 1, mode);

    php_url_free(url);

    return 0;

}

static int php_varstream_rmdir(php_stream_wrapper *wrapper,

        char *from, int options,

        php_stream_context *context TSRMLS_DC)

{

    php_url *url;

    url = php_url_parse(from);

    if (!url) {

        // ... (省略逻辑)

        return -1;

    }

    if (!zend_hash_del(&EG(symbol_table), url->host,

                strlen(url->host) + 1)) {

        // ... (省略逻辑)

        return -1;

    }

    php_url_free(url);

    return 0;

}
```

在配合`varstream`包装器使用时，`unlink()`的行为非常类似于`unset()`：

```
static int php_varstream_rmdir(php_stream_wrapper *wrapper,

        char *url, int options,

        php_stream_context *context TSRMLS_DC)

{

    /* 像 unlink() 一样操作 */

    wrapper->wops->unlink(wrapper, url, options,

                                context TSRMLS_CC);

}
```

## Inspection

并不是所有的流操作都涉及资源操纵。有时，查看活动流当前的状态，或者检查一个可能打开的资源以观察其反应是一个很好的主意。

此节中的流和包装器操作都使用相同的数据结构：`php_stream_statbuf`，它由一个元素组成：标准的 POSIX `struct statbuf`。当调用任何方法时，它都应该尽可能填充`statbuf`元素，同时保持未知元素不变。

### `stat`

如果设置，当请求活动实例的信息时，将调用`wrapper->ops->stream_stat()`。如果没有设置，将调用相应的`stream->ops->stat()`方法。无论调用哪种方法，它都尽力将有关流实例的有效信息填充到`ssb->sb`中。在普通的文件/O 术语中，这些调用对应于`fstat()`标准调用。

### `url_stat`

`wrapper->ops->url_stat()`在流实例之外调用，用于检索可流资源的元数据。通常，应该跟随符号链接或重定向，直到找到真实资源并根据与`stat()`系统调用相同的语义返回该资源的信息。`url_stat`的`flags`参数允许根据`PHP_STREAM_URL_STAT_*`系列常量修改这种行为：

- `LINK`: 不跟随符号链接和重定向。相反，报告遇到的第一个节点的信息，无论是链接还是真实资源。
- `QUIET`: 不报告错误。注意这与许多其他流函数中的`REPORT_ERRORS`逻辑相反。

![](img/30011536.html)

### Summary

暴露流式资源（无论是远程网络 I/O 还是本地数据源）允许你的扩展程序钩入核心数据处理函数，并避免重新实现描述符管理和 I/O 缓冲等繁琐工作。这使得它在处于用户空间设置时变得更加有用且强大。

下一章将通过查看过滤器（filters）和上下文（contexts）来完成流层，用于更改流默认的行为，甚至在传输过程中修改数据。

# 第 16 章. 分流流

PHP 经常被低估的特性是流上下文（stream context）。这些可选参数在大多数与流创建相关的函数中都可以从用户空间访问，它们作为一个通用框架，用于向特定的包装器或流实现传入或输出附加信息。

### 上下文

每个流上下文包含两种内在类型的信息。第一种也是最常用的是上下文选项（context option）。这些值在上下文中被组织为两级嵌套数组，通常用于更改流包装器的初始化方式。另一种类型是上下文参数（context parameters），它们的设计旨在与包装器无关，目前提供了一种将流层内的事件通知冒泡到流代码的机制。

```
php_stream_context *php_stream_context_alloc(void);
```

创建上下文使用此简单的 API 调用，它分配一些存储空间并初始化存储上下文选项和参数的`HashTables`。它还被自动注册为资源，因此在请求关闭时会被隐清理。

### 设置选项

设置上下文选项的内部 API 与用户空间 API 几乎完全相同：

```
int php_stream_context_set_option(php_stream_context *context,

            const char *wrappername, const char *optionname,

            zval *optionvalue);
```

与用户空间原型唯一真实区别的是：

```
bool stream_context_set_option(resource $context,

            string $wrapper, string $optionname,

            mixed $value);
```

是特定的数据类型，由于需要，这些类型在用户空间和内部之间是不同的。例如，一段内部代码可以使用刚刚介绍的两个 API 调用来使用内置包装器发送 HTTP 请求，同时通过上下文选项覆盖`user_agent`设置。

```
php_stream *php_sample6_get_homepage(

                            const char *alt_user_agent)

{

    php_stream_context *context;

    zval tmpval;

    context = php_stream_context_alloc();

    ZVAL_STRING(&tmpval, alt_user_agent, 0);

    php_stream_context_set_option(context, "http",

                                "user_agent", &tmpval);

    return php_stream_open_wrapper_ex("http://www.php.net",

                "rb", REPORT_ERRORS | ENFORCE_SAFE_MODE,

                NULL, context);

}
```

#### 注意

请注意`tmpval`没有分配任何永久存储空间，填充它的它的字符串也没有被复制。`php_stream_context_set_option`会自动对传递的`zval`及其所有内容创建一个副本。

### 获取选项

获取上下文选项的 API 调用与其设置对应的项相镜像，并带有一种似曾相识的暗示。

```
int php_stream_context_get_option(php_stream_context *context,

            const char *wrapper_name, const char *optionname,

            zval ***optionvalue);
```

回想上下文选项存储在一组嵌套的`HashTables`中，当从`HashTable`检索值时，标准方法是将指向`zval**`的指针传递给`zend_hash_find()`。由于`php_stream_context_get_option()`是`zend_hash_find()`的专用代理，逻辑上其语义应该是相同的。这里是内置 http 包装器使用`php_stream_context_get_option`的一个简化示例，展示了`user_agent`设置是如何应用到特定的：

```
zval **ua_zval;

char *user_agent = "PHP/5.1";

if (context &&

    php_stream_context_get_option(context, "http",

                "user_agent", &ua_zval) == SUCCESS &&

                Z_TYPE_PP(ua_zval) == IS_STRING) {

    user_agent = Z_STRVAL_PP(ua_zval);

}
```

在这种情况下，非字符串值会被直接丢弃，因为对`user_agent`字符串使用数字是没有意义的。其他上下文选项（如`max_redirects`）接受数值，而且因为在字符串`zval`中找到数值值并不罕见，所以可能需要进行类型转换以使用原本合合法的设置。遗憾的是，这些变量由上下文拥有，因此不能简单地转换；相反，必须分离出来进行转换，并在必要时销毁：

```
long max_redirects = 20;

zval **tmp_zval;

if (context &&

    php_stream_context_get_option(context, "http",

            "max_redirects", &tmp_zval) == SUCCESS) {

    if (Z_TYPE_PP(tmp_zval) == IS_LONG) {

        max_redirects = Z_LVAL_PP(tmp_zval);

    } else {

        zval copyval = **tmp_zval;

        zval_copy_ctor(&copyval);

        convert_to_long(&copyval);

        max_redirects = Z_LVAL(copyval);

        zval_free(&copyval);

    }

}
```



#### 注意

在实践中，此示例中的`zval_free()`是必要的。`IS_LONG`变量除了`zval`容器本身外不使用任何额外存储，因此`zval_free()`是一个空操作。将其包含在此示例中是为了完整性，因为它对于`String`、`Array`、`Resource`以及未来可能的其他数据类型是必要的。

### 参数

尽管用户空间 API 将上下文参数呈现为与上下文选项相似的统一结构，但在语言内部，它们实际上被声明为`php_stream_context`结构体的独立成员。

目前，仅支持一个上下文参数：`notifier`。`php_stream_context`结构体的此元素可以可选地指向`php_stream_notifier`结构体，该结构体包含以下成员：

```
typedef struct {
    php_stream_notification_func func;
    void (*dtor)(php_stream_notifier *notifier);
    void *ptr;
    int mask;
    size_t progress, progress_max;
} php_stream_notifier;
```

当`php_stream_notifier`结构体赋值给`context->notifier`时，它提供了一个回调函数`func`，该回调会在表 16.1 所示的`PHP_STREAM_NOTIFY_*`代码对应的特殊流事件上触发。给事件还将带有表 16.2 所示的`PHP_STREAM_NOTIFY_SEVERITY_*`级别。

| `ERR` | 严重错误条件。等于`E_ERROR`错误。 |
|---|---|

提供了一个方便指针`*ptr`供通知器实现（notifier implementations）携带额外数据。如果该指针指向在上下文析构时必须释放的空间，则可以指定一个`dtor`方法，该方法会在上下文的最后一个引用离开作用范围时被调用。

`mask`元素允许将事件触发限制在特定的严重性级别。如果事件发生的严重级别不在`mask`包含的范围内，则通知器函数将不会被触发。

最后两个元素`progress`和`progress_max`可以由流实现填充；但是，通知器函数在分别接收到至少一个`PHP_STREAM_NOTIFY_PROGRESS`或`PHP_STREAM_NOTIFY_FILE_SIZE_IS_`事件之前，应避免使用这这两个值中的任何一个。

以下示例符合`php_stream_notification_func`回调的原型：

```
void php_sample6_notifier(php_stream_context *context,
        int notifycode, int severity, char *xmsg, int xcode,
        size_t bytes_sofar, size_t bytes_max,
        void *ptr TSRMLS_DC)
{
    if (notifycode != PHP_STREAM_NOTIFY_FAILURE) {
        /* 忽略所有其他通知 */
        return;
    }
    if (severity == PHP_STREAM_NOTIFY_SEVERITY_ERR) {
        /* 分发给危机处理器 */
        php_sample6_theskyisfalling(context, xcode, xmsg);
        return;
    } else if (severity == PHP_STREAM_NOTIFY_SEVERITY_WARN) {
        /* 记录潜在问题 */
        php_sample6_logstrangeevent(context, xcode, xmsg);
        return;
    }
}
```

### 默认上下文

从 PHP 5.0 开始，当调用没有带上下文参数的用户态流创建函数时，将使用请求范围内的默认上下文。该上下文变量存储在 File Globals 结构中，命名为`FG(default_context)`，其访问方式与任何其他`php_stream_context`变量相同。在为用户态脚本创建流时，通常最好允许用户指定上下文，或者至少回退到默认上下文。可以通过使用`php_stream_context_from_zval()`宏将用户态的`zval*`解码为`php_stream_context`，如下例自第 14 章“访问流”的示例所示：

```
PHP_FUNCTION(sample6_fopen)
{
    php_stream *stream;
    char *path, *mode;
    int path_len, mode_len;
    int options = ENFORCE_SAFE_MODE | REPORT_ERRORS;
    zend_bool use_include_path = 0;
    zval *zcontext = NULL;
    php_stream_context *context;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC,
            "ss|br", &path, &path_len, &mode, &mode_len,
                &use_include_path, &zcontext) == FAILURE) {
        return;
    }
    context = php_stream_context_from_zval(zcontext, 0);
    if (use_include_path) {
        options |= PHP_FILE_USE_INCLUDE_PATH;
    }
    stream = php_stream_open_wrapper_ex(path, mode, options,
                                    NULL, context);
    if (!stream) {
        RETURN_FALSE;
    }
    php_stream_to_zval(stream, return_value);
}
```

如果`zcontext`包含一个用户态上下文资源，则像任何`ZEND_FETCH_RESOURCE()`调用一样，其关联指针将填充到`context`中。相反，如果`zcontext`为`NULL`且`php_stream_context_from_zval()`的第二个参数设置为非零值，则宏的结果将简单为`NULL`。当像本示例以及几乎所有的核心流创建用户态函数那样设置为零时，将使用`FG(default_context)`的值（并在适当时进行初始化）。

### 过滤器 (Filters)

过滤器在读写操作期间对流内容应用额外的转换阶段。请注意，虽然 PHP 从 4.3 版本开始存在流过滤器，但流过滤器 API 的设计在 PHP 5.0 中发生了巨大变化。本章的内容特指 PHP 5 这一代的流过滤器。

#### 在流上应用现有过滤器

向打开的流上应用过滤器只需要几行代码：

```
php_stream *php_sample6_fopen_read_ucase(const char *path
                                        TSRMLS_DC) {
    php_stream_filter *filter;
    php_stream *stream;

    stream = php_stream_open_wrapper_ex(path, "r",
                        REPORT_ERRORS | ENFORCE_SAFE_MODE,
                        NULL, FG(default_context));
    if (!stream) {
        return NULL;
    }
    filter = php_stream_filter_create("string.toupper", NULL,
                                        0 TSRMLS_CC);
    if (!filter) {
        php_stream_close(stream);
        return NULL;
    }
    php_stream_filter_append(&stream->readfilters, filter);
    return stream;
}
```

首先，看看与其兄弟函数相关的 API 函数：

```
php_stream_filter *php_stream_filter_create(const char *filtername, zval *filterparams,
                int persistent TSRMLS_DC);
void php_stream_filter_append(php_stream_filter_chain *chain,
                php_stream_filter *filter);
void php_stream_filter_prepend(php_stream_filter_chain *chain,
                php_stream_filter *filter);
```

`php_stream_filter_create()`的`filterparams`参数与其对应的用户态`stream_filter_append()`和`stream_filter_prepend()`函数含义相同。注意，传入`php_stream_filter_create()`的`zval*`并不属于过滤器；它在过滤器创建期间被借用。

如果过滤器将应用于持久化流，持久化标记必须设置为非零值。如果你不确定要对哪个流应用过滤器，请使用`php_stream_is_persistent()`宏，它接受一个`php_stream*`变量。正如前面的示例所示，流过滤被分为两个独立的链。一个用于写入，在响应`stream->ops->write()`调用时触发；另一个用于读取，处理来自流层中`stream->ops->read()`的所有数据。

在本示例中，你使用了`&stream->readfilters`来指明读取链。如果你想将过滤器应用于写入链，只需使用`&stream->writefilters`。

#### 定义过滤器实现

注册过滤器实现与注册包装器（wrapper）的基本规则相同。引入过滤器的第一步发生在`MINIT`阶段，与`MSHUTDOWN`阶段的移除相对应。以下你将使用的 API 调用原型，以及注册两个过滤器工厂的示例用法：

```
int php_stream_filter_register_factory(
            const char *filterpattern,
            php_stream_filter_factory *factory TSRMLS_DC);
int php_stream_filter_unregister_factory(
            const char *filterpattern TSRMLS_DC);

PHP_MINIT_FUNCTION(sample6)
{
    php_stream_filter_register_factory("sample6",
            &php_sample6_sample6_factory TSRMLS_CC);
    php_stream_filter_register_factory("sample.*",
            &php_sample6_samples_factory TSRMLS_CC);
    return SUCCESS;
}

PHP_MSHUTDOWN_FUNCTION(sample6)
{
    php_stream_filter_unregister_factory("sample6" TSRMLS_CC);
    php_stream_filter_unregister_factory("sample.*"
                                        TSRMLS_CC);
    return SUCCESS;
}
```

在这里注册的第一个过滤器工厂声明了一个特定的过滤器名称`sample6`；第二个工厂利用了流层内置的一些基础模式匹配。为了说明，以下用户态代码的每一行都会尝试实例化`php_sample6_samples_factory`，尽管它们的名称不同：

```php
<?php
    stream_filter_append(STDERR, 'sample.one');
    stream_filter_append(STDERR, 'sample.3');
    stream_filter_append(STDERR, 'sample.filter.thingymabob');
    stream_filter_append(STDERR, 'sample.whatever');
?>
```

`php_sample6_samples_factory`的定义可能如下代码所示，你可以将其放置在`MINIT`块的任何上方：

```c
#include "ext/standard/php_string.h"

typedef struct {
    char is_persistent;
    char *tr_from;
    char *tr_to;
    int tr_len;
} php_sample6_filter_data;

static php_stream_filter_status_t php_sample6_filter(
    php_stream *stream, php_stream_filter *thisfilter,
    php_stream_bucket_brigade *buckets_in,
    php_stream_bucket_brigade *buckets_out,
    size_t *bytes_consumed, int flags TSRMLS_DC)
{
    php_sample6_filter_data *data = thisfilter->abstract;
    php_stream_bucket *bucket;
    size_t consumed = 0;

    while (buckets_in->head) {
        bucket = php_stream_bucket_make_writeable(
                                   buckets_in->head TSRMLS_CC);
        php_strtr(bucket->buf, bucket->buflen, data->tr_from,
                                   data->tr_to, data->tr_len);
        consumed += bucket->buflen;
        php_stream_bucket_append(buckets_out, bucket TSRMLS_CC);
    }
    if (bytes_consumed) {
        *bytes_consumed = consumed;
    }
    return PSFS_PASS_ON;
}

static void php_sample6_filter_dtor(
            php_stream_filter *thisfilter TSRMLS_DC)
{
    php_sample6_filter_data *data = thisfilter->abstract;
    pefree(data, data->is_persistent);
}

static php_stream_filter_ops php_sample6_filter_ops = {
    php_sample6_filter,
    php_sample6_filter_dtor,
    "sample.*",
};

#define PHP_SAMPLE6_ALPHA_UCASE "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
#define PHP_SAMPLE6_ALPHA_LCASE "abcdefghijklmnopqrstuvwxyz"
#define PHP_SAMPLE6_ROT13_UCASE "NOPQRSTUVWXYZABCDEFGHIJKLM"
#define PHP_SAMPLE6_ROT13_LCASE "nopqrstuvwxyzabcdefghijklm"

static php_stream_filter *php_sample6_filter_create(
    const char *name, zval *param, int persistent TSRMLS_DC)
{
    php_sample6_filter_data *data;
    char *subname;
```



```
if (strlen(name) < sizeof("sample.") ||
    strncmp(name, "sample.", sizeof("sample.") - 1)) {
    /* 错误的过滤器创建 */
    return NULL;
}

/* 准备过滤器数据存储 */
data = pemalloc(sizeof(php_sample6_filter_data), persistent);
if (!data) {
    /* 持久内存分配可能返回 NULL */
    return NULL;
}

/* 记录分配是否为持久性 */
data->is_persistent = persistent;

/* 关注请求的特定子过滤器 */
subname = name + sizeof("sample.") - 1;
if (strcmp(subname, "ucase") == 0) {
    data->tr_from = PHP_SAMPLE6_ALPHA_LCASE;
    data->tr_to = PHP_SAMPLE6_ALPHA_UCASE;
} else if (strcmp(subname, "lcase") == 0) {
    data->tr_from = PHP_SAMPLE6_ALPHA_UCASE;
    data->tr_to = PHP_SAMPLE6_ALPHA_LCASE;
} else if (strcmp(subname, "rot13") == 0) {
    data->tr_from = PHP_SAMPLE6_ALPHA_LCASE PHP_SAMPLE6_ALPHA_UCASE;
    data->tr_to = PHP_SAMPLE6_ROT13_LCASE PHP_SAMPLE6_ROT13_UCASE;
} else {
    /* 未识别的过滤器名称 */
    pefree(data, persistent);
    return NULL;
}

/* 避免每次都计算 */
data->tr_len = strlen(data->tr_from);
return php_stream_filter_alloc(&php_sample6_filter_ops, data, persistent);
}

static php_stream_filter_factory php_sample6_samples_factory = {
    php_sample6_filter_create
};
```

由于在上一章中实现过流包装器（stream wrappers），你可能已经识别出这里的基本结构。工厂方法（`php_sample6_filter_create`）会被调用以分配过滤器实例，并为其分配一组操作和抽象数据。在这种情况下，你的工厂为所有过滤器类型分配了相同的 `ops` 结构体，但以不同的方式初始化数据结构。

调用作用域会将此分配的过滤器赋值给流。

- [费曼学习法](https://wiki.example.org/feynmans_learning_method)的灵感源自**查德·费曼**，这位诺贝尔物理奖得主。

1. 通过费曼的技巧，你只需`20 min`就能深入理解知识点，而且令人记忆深刻且*难以忘记*。

```
if (condVar > someVal) {console.log("xxx")}
```

当然，这只涵盖了问题的一部分。例如，如果安装了另一个同名的库，但它与你正在寻找的库不兼容怎么办？测试你的扩展是否能针对找到的库成功编译的最佳方法，是实际上对它进行编译。你将通过在调用`PHP_ADD_LIBRARY_WITH_PATH`之前放置一个新的`config.m4`宏来做到这一点：

```
PHP_CHECK_LIBRARY(z, deflateInit,,[
  AC_MSG_ERROR([Invalid zlib extension, gzInit() not found])
],-L$ZLIB_DIR/lib)
```

此实用宏将展开为整个程序，`./configure`将尝试编译它。如果编译成功，意味着在由第一个参数命库中找到了由第二个参数定义的符号。如果成功，将执行位于第三个参数中的任何 autoconf 脚本；如果失败，则运行第四个参数中的 autoconf 脚本。在这个示例中，第三个（成功）参数留为空，因为“没有消息就是好消息”。第五个也是最后一个参数用于指定额外的编译器和链接器标志，在这种情况下，`-L`表示查找库的额外位置。

### 可选功能

现在你已经找到了一组匹配的库和头文件，但根据安装的该库的版本，你可能想要包含或排除额外功能。由于此类版本更改通常涉及特定过程入口的引入或删除，你可以重用刚刚使用的`PHP_CHECK_LIBRARY()`宏来更精细地查阅该库的能力。

```
PHP_CHECK_LIBRARY(z, gzgets,[
  AC_DEFINE(HAVE_ZLIB_GETS,1,[Having gzgets indicates zlib >= 1.0.9])
],[
  AC_MSG_WARN([zlib < 1.0.9 installed, gzgets() will not be available])
],-L$ZLIB_DIR/lib)
```

### 测试实际行为

仅仅知道符号是否存在以及你的代码能否成功编译可能是不够的；某些库在特定版本存在 bug，只有通过对它们运行某些测试代码才能发现并随后规避它们。

`AC_TRY_RUN()`宏会将一个小的源文件编译为可执行程序并让其运行。根据传递给`./configure`的返回码，你的脚本随后可以设置可选的`#define`语句，或者如果无法规避 bug，则直接带消息请求升级。考虑来自`ext/standard/config.m4`的以下片段：

```
AC_TRY_RUN([
#include <math.h>
double somefn(double n) {
  return floor(n*pow(10,2) + 0.5);
}
int main() {
  return somefn(0.045)/10.0 != 0.5;
}
],[
  PHP_ROUND_FUZZ=0.5
  AC_MSG_RESULT(yes)
],[
  PHP_ROUND_FUZZ=0.50000000001
  AC_MSG_RESULT(no)
],[
  PHP_ROUND_FUZZ=0.50000000001
  AC_MSG_RESULT(cross compile)
])
AC_DEFINE_UNQUOTED(PHP_ROUND_FUZZ, $PHP_ROUND_FUZZ,
                    [Is double precision imprecise?])
```

如你所示，`AC_TRY_RUN()`的第一个参数是一个字面量 C 代码块，它将被编译并执行。如果该块的退出码为零，则执行位于第二个参数中的 autoconf 脚本，在这种情况下，表示`round()`函数按预期工作，并恰好在`0.5`处分割。

如果代码块返回非零值，则执行位于第三个参数中的 autoconf 脚本。第四个也是最后一个参数是 PHP 进行交叉编译时使用的默认值。在这种情况下，任何运行示例代码的尝试都是徒的，因为目标平台与编译扩展的平台不同。

![](img/30011536.html)

### 强制模块依赖

从 PHP 5.1 开始，可以强制扩展之间的相互依赖关系。由于扩展可以静态编译到 PHP 中，也可以作为共享对象动态加载，因此需要在两个位置强制依赖关系。

#### 配置时模块依赖

第一个位置是在你在本章中密切关注的`config.m4`文件。在这里，你将使用`PHP_ADD_EXTENSION_DEP(extname, depname[,optional])`宏来指示`extname`扩展依赖于`depname`扩展。当`extname`被静态编译到 PHP 中时，`./configure`脚本将使用此行确定`depname`必须先初始化。`optional`参数是一个标志，表示如果`depname`也被静态编译，则应该在`extname`之前加载它，但它不是强制依赖项。

该宏使用的示例可以在 PDO 驱动程序中找到，例如`pdo_mysql`，它们预见地依赖于 PDO 扩展：

```
ifdef([PHP_ADD_EXTENDION_DEP],
[
  PHP_ADD_EXTENSION_DEP(pdo_mysql, pdo)
])
```

注意`PHP_ADD_EXTENSION_DEP()`宏被封装在`ifdef()`结构中。

```
PHP_ARG_WITH(argname,description,helptext)
ARG_WITH(argname,helptext,default)
```

> 如你所见，win32 变体的原型明显不同。与 m4 版本不同，后者的默认值是通过脚本稍后对值的测试来暗示的，而在这里显式地设置了默认值，并完全省略了描述文本。

```
PHP_ARG_ENABLE(argname,description,helptext)
ARG_ENABLE(argname,helptext,default)
```

`ENABLE`宏遵循与其`WITH`对应项相同的异常规则。

```
PHP_CHECK_LIBRARY(library,symbol,success,failure,flags)
CHECK_LIB(library,symbol,path,common)
```

> 此基于宏动作的 win32 版本返回真或假值，取决于位于`path`下的`library`中是否未找到`symbol`。如果指定了`common`为包含此库的包的通用名称，则还将扫描包含此名称的附加搜索路径。使用`CHECK_LIB`的配置文件应测试返回值，并使用更传统的 if/then/else 结构采取行动。

```
AC_DEFINE(name,value,comment)
AC_DEFINE(name,value,comment)
```

> 此宏在`config.w32`术语中与`config.m4`相同的名称和定义。

```
AD_DEFINE_UNQUOTED(name,value,comment)
DEFINE(name,value)
```

> `AC_DEFINE`的`UNQUOTED`变体在于，`name`和`value`的内容以字面形式用在生成的`config.h`文件中。在`config.w32`的变体`DEFINE`中，不允许注释，因为定义是以不同的方式包含的。

```
PHP_ADD_EXTENSION_DEP(extname,depname,optional)
ADD_EXTENSION_DEP(extname,depname,optional)
```

> 此宏的`config.m4`和`config.w32`版本之间唯一的区别在于名称。

```
PHP_NEW_EXTENSION(extname,sources[,shared[,sapi[,cflags[,cxx]]]])
EXTENSION(extname,sources[,shared[,cflags[,dllname[,objdir]]]])
```

> 在两种情况下，都使用`sources`中指定的源文件声明名为`extname`的新 PHP 扩展。`shared`可以是`shared`或`yes`，表示该扩展将编译为动态可加载模块。通常此值通过`$ext_shared`变量传递，如果扩展作为`enable-extname=shared`包含，则由`./configure` / `./configure.js`自动提供。`sapi`可可选设置为`cli`，表示模块仅为`CLI`或`CGI` sapi 构建。`cflags`参数可以包含额外的编译器设置，在构建对象时传递给`CC`。默认情况下，除非在`dllname`参数中指定替代，否则 Windows DLL 将命名为`php_extname.dll`。所有源文件都使用 Windows 下的 Visual C++ 编译器编译；然而，Unix 构建将使用`CC`（通常是`gcc`）编译文件，除非`cxx`参数设置为真值。在 Windows 下，可以指定`objdir`将中间文件放在临时文件夹中。

```
AC_MSG_ERROR(message)
ERROR(message)
```

> 这些宏将输出错误`message`并停止配置过程。每当你的配置脚本遇到无法优雅降级其选项的情况时，请使用这些宏。

```
AC_MSG_WARNING(message)
WARNING(message)
```

> 像错误宏一样，这些结构在配置期间会输出`message`。在这种情况下，message 是一个警告，配置将继续进行而不停止。

### 总结

如果你的扩展将在不受控的环境下构建，那么让它足够智能以适应那些环境将至关重要。通过使用 PHP 的 UNIX 和 Windows 构建系统提供的强大脚本能力，你应该能够检测并引导你发现自己已经有了从零构建扩展以及与 API 接口的基础，你准备好使用多年来为 PHP 开发的一些方便工具来消除扩展开发的繁琐工作，使新扩展的原型设计变得快速且轻松。

## 第 18 章 扩展生成器

每个 PHP 扩展都包含一些常见且坦率说无聊的结构和文件。在开始创建一个新扩展时，从这些常见结构开始是很有意义的，你只需要关注功能部分即可。为此，标准 PHP 分发中包含了一个非常简单、实用的 shell 脚本。

### `ext_skel`

导航到 PHP 源码树下的`ext/`文件夹并执行以下命令：

```
jdoe@devbox:/home/jdoe/cvs/php-src/ext/$ ./ext_skel extname=sample7
```

几刻之后，看到一些文本后，你将收到类似下面的指令：

```
要使用你的新扩展，你必须执行以下步骤：
1.  $ cd ..
2.  $ vi ext/sample7/config.m4
3.  $ ./buildconf
4.  $ ./configure [with-enable]-sample7
5.  $ make
6.  $ ./php -f ext/sample7/sample7.php
7.  $ vi ext/sample7/sample7.c
8.  $ make
```

重复步骤 3-6，直到你对`ext/sample7/config.m4`满意且步骤 6 确认你的模块已编译到 PHP 中。然后，开始编写代码并在需要重复最后两个步骤。

此时查看`ext/sample7`，你将看到你在第 5 章“你的第一个扩展”中组合的文件的带有详细注释的版本。目前你还无法编译你的扩展；但是，只需按照指令对`config.m4`进行一些细微的调整，你就可以开始运行一个实现功能几乎与你最初在第 5 章中编写的内容相同的扩展了。

#### 生成函数原型

如果你正在编写一个扩展来封装第三方库，你已经有了关于函数需要像什么样以及它们的基本行为应该是什么的机器可读版本。通过向`./ext_skel`传递一个额外的参数，它会自动扫描你的头文件并创建简单的`PHP_FUNCTION()`块来适应接口。通过指示`./ext_skel`解析`zlib`头文件来测试：

```
jdoe@devbox:/home/jdoe/cvs/php-src/ext/$ ./ext_skel extname=sample8 \
proto=/usr/local/include/zlib/zlib.h
```

现在查看`ext/sample8/sample8.c`，你会发现`PHP_FUNCTION()`声明，对应每个`zlib`函数。然而，注意骨架生成过程对未知资源类型发出了一些警告消息。你需要特别注意这些函数，并应用你在第 9 章“资源数据类型”中获得的经验，并将内部复杂结构链接到用户空间变量。

![pixel.jpg](img/30011536)

![pixel.jpg](img/30011536)

### `PECL_Gen`

更完整但复杂的代码生成器`PECL_Gen`可从 PECL ([`pecl.php.net`](http://pecl.php.net)) 获取并通过常用的`pear install PECL_Gen`命令安装。

安装后，可以与`ext_skel`相同的方式运行，接收相同的参数并产生大致相同的输出，如果提供了完整的 XML 定义文件，它将产生一个更健壮、完整的准备编译的扩展。`PECL_Gen`并不能免除编写扩展的核心功能；相反，它在生成扩展之前提供了一种表达代码的替代形式。

#### `specfile.xml`

简单的扩展定义文件可能如列表 18.1 所示。

##### 列表 18.1. 最小的`specfile.xml`

```xml
<?xml version="1.0" encoding="utf-8">
<extension name="sample9">
 <functions>
```



<function name="sample9_hello_world" role="public">

   <code

<![CDATA[

    php_printf("Hello World!");

]]>

   </code>

  </function>

 </functions>

</extension>

```

通过运行 `PECL-Gen` 命令执行此文件：

```
jdoe@devbox:/home/jdoe/cvs/php-src/ext/$ pecl-gen specfile.xml
```

将生成一组完整的文件，用于生成名为 `sample9` 的扩展，该扩展导出了一个用户态函数 `sample9_hello_world()`。

## 关于扩展

除了你已经熟悉的功能文件外，`PECL_Gen` 还会构建一个可以供 pear 安装程序使用的 `package.xml` 文件。如果你计划在 PECL 仓库中发布包，或者只是想使用 pear 打包系统来交付你的内容，这个文件将非常有用。

无论哪种方式，你都可以将 `PECL_Gen` 规范文件指定 `package.xml` 文件的大部分元素。

```xml
<extension name="sample9">
 <summary>由 PECL_Gen 生成的扩展 9</summary>
 <description>PHP 扩展编写的另一个示例</description>
 <maintainers>
  <maintainer>
   <name>John D. Bookreader</name>
   <email>jdb@example.com</email>
   <role>lead</role>
  </maintainer>
 </maintainers>
 <release>
  <version>0.1</version>
  <date>2006-01-01</date>
  <state>beta</state>
  <notes>初始发布</notes>
 </release>
 ...
</extension>
```

当 `PECL_Gen` 创建扩展的其他部分时，这些信息将被翻译到最终的 `package.xml` 文件中。

## 依赖项

正如你在第 17 章“配置与链接”中所看到的，可以在 `config.m4` 和 `config.w32` 文件中扫描依赖项。`PECL_Gen` 能够使用 `<deps>` 部分构建这些扫描步骤，以声明各种类型的依赖项。默认情况下，`<deps>` 标签下列出的依赖同时适用于 UNIX 和 win32 构建，除非指定了 `platform` 属性并列出其中一个目标。

```xml
<extension name="sample9">
 ...
 <deps platform="unix">
  <! UNIX 特有的依赖项 >
 </deps>
 <deps platform="win32">
  <! Win32 特有的依赖项 >
 </deps>
 <deps platform="all">
  <! 适用于所有平台的依赖项 >
 </deps>
</extension>
```

### `with`

通常，扩展会被配置为使用 `enable-extname` 风格配置选项。通过向 `<deps>` 块添加一个或多个 `<with>` 标签，不仅可以将配置选项改为 `with-extname`，还可以扫描所需的头文件：

```xml
<deps platform="unix">
 <with defaults="/usr:/usr/local:/opt"
        testfile="include/zlib/zlib.h">zlib 头文件</with>
</deps>
```

### 库

所需的库也使用 `<lib>` 标签列在 `<deps>` 部分下。

```xml
<deps platform="all">
 <lib name="ssle" platform="win32"/>
 <lib name="crypto" platform="unix"/>
 <lib name="z" platform="unix" function="inflate"/>
</deps>
```

在前两个示例中，仅检查了库的存在；在第三个示例中，实际上加载了库以确保 `inflate()` 函数已定义。

注意：尽管 `<deps>` 标签已经命名了目标，但 `<lib>` 标签也有一个 `platform` 属性，它可以覆盖 `<deps>` 的设置。在混合使用时要小心！

### `<header>`

通过在 `<deps>` 块中指定 `<header>` 标签，可以将代码所需的额外包含文件追加到 `#include` 指令列表中。要强制包含特定的头文件，请向 `<header>` 标签添加 `prepend="yes"` 参数。与 `<lib>` 依赖一样，`<header>` 也可以按平台进行限制：

```xml
<deps>
 <header name="sys/types.h" platform="unix" prepend="yes"/>
 <header name="zlib/zlib.h"/>
</deps>
```

### 常量

用户态常量使用 `<constants>` 块内的一个或多个 `<constant>` 标签声明。每个标签都需要 `name` 和 `value` 属性，以及 `type` 属性，该类型必须等于以下之一：`int`、`float` 或 `string`。

```xml
<example name="sample9">
 <constants>
  <constant name="SAMPLE9_APINO" type="int" value="200601"/>
  <constant name="SAMPLE9_VERSION" type="float" value="1.0"/>
  <constant name="SAMPLE9_AUTHOR" type="string" value="John Doe"/>
 </constants>
</example>
```

### 全局变量

线程全局变量的声明方式几乎相同。区别在于 `type` 参数是使用 C 语言原型而不是用户态描述符来指定的。一旦声明并构建，即可通过全局变量访问。正如在第 12 章](#ch12.html#ch12)中讨论的 `EXTNAME(global)` 宏一样，全局变量 `value` 属性表示请求开始。

```xml
<example name="sample9">
 <globals>
  <global name="greeting" type="char *"/>
  <global name="is_set" type="bool" value="1"/>
 </globals>
</example>
```

### INI 选项

要将线程安全的全局变量绑定到 phpini，使用 `<phpini>` 标签而不是 `<global>`。此标签需要两个参数：`onupdate` 指明如何处理 INI 更改，以及 `access` 模式为 `all`、`user`、`perdir` 或 `system` 之一，正如在第 13 章](#ch13.html#ch13)所示。

```xml
<example name="sample9">
 <globals>
  <! 定义 mysetting >
  <phpini name="mysetting" type="int" value="42"
="all
```

### 函数

你已经看到了最基本的函数声明；但是，`PECL_Gen` 规范文件中的 `<function>` 标签实际上支持两种类型的函数。

这两个版本都支持 `<summary>` 和 `<description>` 属性，你已经在 `<extension>` 级别使用过；但是，每个类型唯一的强制元素是 `code` 标签，它包含放置在你的源文件字面 C 代码。

```xml
<extension name="sample9">
 <functions>
  <! 函数定义在这里 >
</functions>
</extension>
```

#### `role="public"`

正如你预期的，任何用公共角色声明的函数都将被封装在适当的 `PHP_FUNCTION()` 头文件括号中，并进入扩展的函数向量。

除了其他函数支持的标签外，公共类型还可以指定 `<proto>` 标签。此标签的格式应与 PHP 在线手册中的原型匹配，以便文档生成器进行解析。

```xml
<functions>
 <function role="public" name="sample9_greet_me">
  <summary>通过名字打招呼</summary>
  <description>接受一个字符串名称参数并向那个人问好。返回 TRUE。</description>
  <proto>bool sample9_greet_me(string name)</proto>
  <code
<![CDATA[
    char *name;
    int name_len;
    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "s",
                              &name, &name_len) == FAILURE) {
        return;
    }
    php_printf("Hello ");
    PHPWRITE(name, name_len);
    php_printf("!\n");
    RETURN_TRUE;
]]>
  </code>
 </function>
</functions>
```

#### `role="internal"`

内部函数涵盖五个 `zend_module_entry` 函数：`MINIT`、`MSHUTDOWN`、`RINIT`、`RSHUTDOWN` 和 `MINFO`。指定这五个之外的名称都是错误，且不会被 `pecl-gen` 命令处理。

```xml
<functions>
 <function role="internal" name="MINFO">
  <code
<![CDATA[
    php_info_print_table_start();
    php_info_print_table_header(2, "Column1", "Column2");
    php_info_print_table_end();
]]>
  </code>
 </function>
</functions>
```

## 自定义代码

你的扩展中需要存在的任何其他程序代码都可以使用 `<code>` 标签包含。要将任意代码放入你的目标 `extname.c` 文件中，请使用 `role="code"`；否则，使用 `role="header"` 将代码放入目标 `php_extname.h` 文件中。默认情况下，除非指定了 `position="top"`，否则代码将放在代码文件或头文件的底部。

```xml
<example name="sample9">
  <code name="php_sample9_data" role="header" position="bottom">
<![CDATA[
typedef struct _php_sample9_data {
  long val;
} php_sample9_data;
]]>
  </code>
  <code name="php_sample9_data_ctor" role="code" position="top">
<![CDATA[
static php_sample9_data *php_sample9_data_ctor(long value)
{
    php_sample9_data *ret;
    ret = emalloc(sizeof(php_sample9_data));
    ret->val = value;
    return ret;
}
]]>
  </code>
  ...
</example>
```

### 总结

使用本章涵盖的工具，你已经准备好快速开发 PHP 扩展，并以比手写更少的 Bug 将你的代码投入生产。现在是时候转向将 PHP 嵌入到其他项目中了。在接下来的章节中，你将控制 PHP 环境并利用 Zend Engine 的力量为现有的应用程序添加脚本功能，使其变得更加多功能且实用。

## 第 19 章。设置主机环境

现在你已经探索了 PHP API 的世界，并熟悉了处理 `zvals` 以及通过内部钩子扩展语言，现在是时候扭转局面，真正让这种语言发挥它最擅长的作用：解释脚本代码。

### 嵌入式 SAPI (The Embed SAPI)

回想介绍，PHP 是由分层系统构建的。在最高层是所有提供用户空间函数和类的扩展。与此同时，底部由服务器 API (SAPI) 层占据，它充当到 Apache 等 Web 服务器以及命令行界面 (CLI) 的接口。

在许多 SAPI 实现中，有一种被称为 Embed 的特殊类型。当构建此 SAPI 实现时，会创建一个库对象，其中包含了你所熟悉的所有 PHP 和 Zend API 函数与变量，以及一组额外的辅助函数和宏，使得从外部程序进行接口调用变得简单。

生成 Embed SAPI 的库文件和头文件的操作方法与任何其他 SAPI 编译相同。只需向 `./configure` 命令传递 `enable-embed` 并像往常一样构建即可。与之前一样，如果出现错误，使用 `enable-debug` 将很有帮助。此外，保持 `enable-zts` 开启，原因众所周知（它可以帮助你发现编码错误），但还有另一个原因。想象一下，你有有多个使用 Embed 库执行脚本任务的应用；其中一个是简单的、短寿命的应用，不需要线程，因此为了效率会想要关闭 ZTS。现在想象第二个应用确实使用了线程，并且像 Web 服务器一样，每个线程都需要自己的请求上下文。如果关闭了 ZTS，则只有第一个应用可以使用该库；然而，如果启用了 ZTS，两个应用程序都可以在自己的进程空间内利用同一个共享对象。当然，你可以构建两个版本并简单地给它们起不同的名称，但这往往比简单接受包括不需要时的 ZTS 支持在内的轻微减速更具问题性。默认情况下，嵌入库将构建为共享对象 `libphp5.so` 或动态链接库，但它也可以使用可选的 `static` 关键字构建为静态库：`enable-embed=static`。

构建 Embed SAPI 的静态版本可以避免 ZTS 与非 ZTS 的冲突问题，以及在单个系统上存在多个 PHP 版本的潜在情况。但缺点是，这意味着你生成的应用程序二进制文件将显著增大，因为它承载了整个 Zend Engine 和 PHP 框架的重量，因此在做出选择时，要像对待其他较小的库一样仔细（甚至更加仔细）。

无论你选择哪种构建类型，一旦执行了 `make install`，`libphp5` 将被复制到你通过 `./configure` 选择的 `EPREFIX` 根目录下的 `lib/`。一个名为 `php_embed.h` 的额外头文件也将放置在 `EPREFIX/include/php/sapi/embed` 中，与你使用 PHP Embed 库编译程序时需要的其他重要头文件并列。

### 构建和编译主机应用程序

库本身只是没有目的的代码集合。为了让它“运行起来”，你需要一些嵌入 PHP 的东西。首先，让我们编写一个简单的封装应用程序，它启动 Zend Engine 并初始化 PHP 处理请求，然后反转过程以释放栈并清理资源（见列表 19.1）。

#### 列表 19.1 简单的 `embed1.c` 应用

```c
#include <sapi/embed/php_embed.h>

int main(int argc, char *argv[])
{
    PHP_EMBED_START_BLOCK(argc,argv)
    PHP_EMBED_END_BLOCK()
    return 0;
}
```

由于涉及许多头文件，实际构建所需的命令比这段简单的代码片段要长得多。如果你使用了不同于默认的 `EPREFIX` 位置，请务必在以下示例中替换该位置：

```bash
$ gcc -o embed1 embed1.c \
      -I/usr/local/include/php/ \
      -I/usr/local/include/php/main \
      -I/usr/local/include/php/Zend \
      -I/usr/local/include/php/TSRM \
      -L/usr/local/lib -lphp5
```

由于反复输入这个命令会非常麻烦，你可能更倾向于使用简单的 Makefile（见列表 19.2）。

#### 列表 19.2 使用 Makefile 减少工作量

```makefile
CC = gcc
CFLAGS = -c -I/usr/local/include/php/ \
            -I/usr/local/include/php/main \
            -I/usr/local/include/php/Zend \
            -I/usr/local/include/php/TSRM \
            -Wall -g
LDFLAGS = -L/usr/local/lib -lphp5

all: embed1.c
    $(CC) -o embed1.o embed1.c $(CFLAGS)
    $(CC) -o embed1 embed1.o $(LDFLAGS)
```



```c
#include <stdio.h>
#include <sapi/embed/php_embed.h>

int main(int argc, char *argv[])
{
    zend_file_handle script;

    /* Basic parameter checking */
    if (argc <= 1) {
        fprintf(stderr, "Usage: embed1 filename.php <arguments>\n");
        return -1;
    }

    /* Set up a File Handle structure */
    script.type = ZEND_HANDLE_FP;
    script.filename = argv[1];
    script.opened_path = NULL;
    script.free_filename = 0;

    if (!(script.handle.fp = fopen(script.filename, "rb"))) {
        fprintf(stderr, "Unable to open: %s\n", argv[1]);
        return -1;
    }

    /* Ignore argv[0] when passing to PHP */
    argc;
    argv++;

    PHP_EMBED_START_BLOCK(argc,argv)
        php_execute_script(&script TSRMLS_CC);
    PHP_EMBED_END_BLOCK()

    return 0;
}
```

当然，你还需要一个文件来测试这些内容，在名为`test.php`的文件中编写任何你喜欢的短 PHP 脚本，然后使用你的`embed1`二进制文件执行它：

```
$ ./embed1 test.php
```

如果你在命令行中传递了额外的参数，你会发现它们会通过`$_SERVER['argc']`和`$_SERVER['argv']`变量进入你的脚本。

## 注意

你可能已经注意到，放置在`PHP_EMBED_START_BLOCK()`和`PHP_EMBED_END_BLOCK()`之间的代码被缩进了。这是一种微妙的致敬，因为这些宏形成了一个 C 块作用域（C block scope）。也就是说，`PHP_EMBED_START_BLOCK()`包含一个左大括号`{`，与之匹配的右大括号`}`则隐藏在`PHP_EMBED_END_BLOCK()`中。这里的重点在于，这些宏不能被埋在独立的实用程序启动/关闭函数中。你将在下一章看到解决方案。

## 重用旧技巧

在调用`PHP_EMBED_START_BLOCK()`之后，你的应用程序处于 PHP 请求周期的起始位置，紧接`RINIT`回调完成之后。在此时，你可以像之前那样发执行`php_execute_script()`命令，或者在`PHP_FUNCTION()`或`RINIT()`块中可能找到任何其他有效的 PHP/Zend API 指令。

## 设置初始变量

第 2 章，“从内而外的变量”引入了操纵符号表的概念，然后第 5 章第 18 章向你展示了如何将这些技术应用于用户空间脚本调用的内部函数。由于过程的反转，一切都没有变化；即使没有活跃的用户空间脚本，你的封装应用程序仍然可以操纵符号表。尝试将你当前的`PHP_EMBED_START_BLOCK()`/`PHP_EMBED_END_BLOCK()`组替换为以下列表：

```c
PHP_EMBED_START_BLOCK(argc,argv)
    zval *type;

    /* $type = "Embedded"; */
    ALLOC_INIT_ZVAL(type);
    ZVAL_STRING(type, "Embedded", 1);
    ZEND_SET_SYMBOL(&EG(symbol_table), "type", type);

    php_execute_script(&script TSRMLS_CC);
PHP_EMBED_END_BLOCK()
```

现在用`make`重新构建`embed1`，并使用以下简单的测试脚本进行测试：

```php
<?php
    var_dump($type);
?>
```

这个简单的概念可以很容易扩展，以填充`$_SERVER`超全局数组，而这当然是这类信息应该所属的地方。

```c
PHP_EMBED_START_BLOCK(argc,argv)
    zval **SERVER, *type;

    /* 从全局作用域获取 $_SERVER */
    zend_hash_find(&EG(symbol_table), "_SERVER", sizeof("_SERVER"),
                                                 (void**)&SERVER);

    /* $_SERVER['SAPI_TYPE'] = "Embedded"; */
    ALLOC_INIT_ZVAL(type);
    ZVAL_STRING(type, "Embedded", 1);
    ZEND_SET_SYMBOL(Z_ARRVAL_PP(SERVER), "SAPI_TYPE", type);

    php_execute_script(&script TSRMLS_CC);
PHP_EMBED_END_BLOCK()
```

## 覆盖 INI 选项

在第 13 章“INI 设置”中，作为 INI 修改处理程序主题的一部分，你简要看了 INI 阶段的话。示例中使用的`PHP_EMBED_START_BLOCK()`宏将你的所有代码直接置于`RUNTIME`阶段。这在实践中意味着，对于修改某些设置（如`register_globals`和`magic_quotes_gpc`）已经太晚了。

然而，访问内部机制并不是没有好处的。所谓的“管理设置”（如`safe_mode`）甚至可以通过以下原型描述的`zend_alter_ini_entry()`命令在这一后期开启或关闭：

```c
int zend_alter_ini_entry(char *name, uint name_length, char *value, uint value_length, int modify_type, int stage);
```

`name`、`name_length`、`value`、`value_length`、`modify_type`和`stage`正如你所预期。`name`必须以空字符结尾，`value`则不然；但`modify_type`包含一个标志。`stage`必须对应 Zend Engine 的当前状态；对于简单的嵌入，这始终是`PHP_INI_ALL`。

用户空间的`ini_set()`函数通过传递`PHP_INI_USER`利用了这一内置功能，这意味着只有可修改的 INI 设置可以被更改。当从嵌入应用程序中使用`zend_alter_ini_entry()`时，可以通过传递包含所有 INI 级别的`PHP_INI_ALL`标志来绕过这种访问控制。

通过在脚本开始处扩展当前的`embed1.c`源文件以强制执行安全模式：

```c
PHP_EMBED_START_BLOCK(argc,argv)
    zval **SERVER, *type;

    /* 无论 php.ini 设置如何，
     * 确保启用 safe_mode */
    zend_alter_ini_entry("safe_mode", sizeof("safe_mode"), "1", sizeof("1") - 1, PHP_INI_ALL, PHP_INI_RUNTIME);

    /* 从全局作用域获取 $_SERVER */
    zend_hash_find(&EG(symbol_table), "_SERVER", sizeof("_SERVER"),
                                                  (void**)&SERVER);

    /* $_SERVER['SAPI_TYPE'] = "Embedded"; */
    ALLOC_INIT_ZVAL(type);
    ZVAL_STRING(type, "Embedded", 1);
    ZEND_SET_SYMBOL(Z_ARRVAL_PP(SERVER), "SAPI_TYPE", type);

    php_execute_script(&script TSRMLS_CC);
PHP_EMBED_END_BLOCK()
```

## 声明超全局变量

在第 12 章“启动、关闭以及之间的几点”中，你被告诉用户空间自动变量（也称为超全局变量）只能在`MINIT`阶段声明。而本章描述的嵌入方法直接跳过启动和激活进入运行阶段。

超全局变量声明的现实情况是，它只需要在脚本编译之前出现，并且在 PHP 进程的生命期间内发生一次。在扩展的通常情况下，`MINIT`是唯一可以保证这一点的地方。

由于现在你的封装器应用接管了控制权，只需通过在执行`php_execute_script()`命令（即脚本源文件实际编译的地方）之前声明用户空间的自动全局变量（autoglobal），就可以保证这两点都得到遵循。尝试通过将`$_EMBED`声明为全局变量并将其初始化为某个默认值来测试一下：

```c
PHP_EMBED_START_BLOCK(argc,argv)
    zval *EMBED, *foo;

    /* 在全局作用域内将 $_EMBED 创建为数组 */
    ALLOC_INIT_ZVAL(EMBED);
    array_init(EMBED);
    ZEND_SET_SYMBOL(&EG(symbol_table), "_EMBED", EMBED);

    /* $_EMBED['foo'] = "Bar"; */
    ALLOC_INIT_ZVAL(foo);
    ZVAL_STRING(foo, "Bar", 1);
    ZEND_SET_SYMBOL(Z_ARRVAL_P(EMBED), "foo", foo);

    /* 将 $_EMBED 声明为全局变量 */
    zend_register_auto_global("_EMBED", sizeof("_EMBED") - 1
#ifdef ZEND_ENGINE_2
                            , NULL TSRMLS_CC);
#if PHP_MAJOR_VERSION > 5 || (PHP_MAJOR_VERSION == 5 && PHP_MINOR_VERSION > 0)
    /* PHP >= 5.1 要求手动禁用 arming 函数 */
    zend_auto_global_disable_jit("_EMBED", sizeof("_EMBED") - 1 TSRMLS_CC);
#endif
#else
                            TSRMLS_CC);
#endif

    php_execute_script(&script TSRMLS_CC);
PHP_EMBED_END_BLOCK()
```

记住，Zend Engine 2（PHP 5.0 及更高版本）使用了不同的`zend_register_auto_global()`原型，因此你需要使用之前显示的`#ifdef`来保持对 PHP4 的兼容性。如果你不在乎与旧版本 PHP 的兼容性，可以省略这些指令，最终获得更整洁的代码。

## 总结

正如你所见，将 Zend Engine 和 PHP 语言的全方位嵌入到你的应用中，实际上比通过新功能扩展它需要的工作更少。因为它们共享相同的底层 API，学习其中一种会让另一种也变得立而易懂。

通过本章，你利用全合一宏`PHP_EMBED_START_BLOCK()`和`PHP_EMBED_END_BLOCK()`探索了脚本代码嵌入的最简单形式。在下一章中，你将剥开这些宏的层次，将 PHP 更无缝地集成到你的主机应用程序中。

## 第 20 章. 高级嵌入

PHP 的嵌入式 SAPI 提供的不仅仅是同步加载和执行脚本文件的方法。通过理解 PHP 执行模型各个部分是如何结合在一起的，可以在特定的请求期间在 PHP 环境中进进出出，甚至赋予脚本回调你的主机应用程序的能力。本章将介绍利用 SAPI 层提供的 I/O 钩子的方法，并扩展你已经在之前的主题中开始探索的执行模型。

### 回调 PHP

除了加载外部脚本外，正如你在上一章中看到的，你的 PHP 嵌入应用还可以使用实现熟悉的用户空间`eval()`命令的底层函数来执行较小的任意代码段。

```c
int zend_eval_string(char *str, zval *retval_ptr,
                     char *string_name TSRMLS_DC)
```

这里，`str`是要执行的实际 PHP 脚本代码，而`string_name`是与执行关联的任意描述。如果发生错误，PHP 将把此描述作为错误输出中的“文件名”报告。`retval_ptr`正如你所料的，将填充返回结果。尝试通过创建 20.1 任意代码来测试：

#### 20.1 任意代码 `embed.c`

```c
#include <sapi/embed.h>

int main(int argc, char *argv[])
{
    PHP_EMBED_START_BLOCK(argc,argv)
        zval *filename;
        zend_eval_string("Hello World!", NULL);
    PHP_EMBED_END_BLOCK()

    return 0;
}
```

#### 脚本文件的替代方案

正如你所看到的，执行脚本文件比通过新功能扩展它要简单得多。因为它们共享相同的底层 API，学习其中一种会让另一种也变得立而易懂。

```c
#include <sapi/embed.h>

int main(int argc, char *argv[])
{
    if (argc <= 1) {
        fprintf(stderr, "Usage: embed <filename>\n");
        return -1;
    }

    char *filename = argv[1];

    PHP_EMBED_START_BLOCK(argc,argv)
        char *include_script;
```



// 此处逻辑应为加载并执行脚本的逻辑

`zend_eval_string(include_script, NULL);`

`PHP_EMBED_END_BLOCK()`

`return 0;`

}

#### 调用用户空间函数

正如你在加载和执行脚本文件时看到的，有两种方法可以调用用户空间函数。最明显的方法是将函数名和所有参数合并到一个字符串中，然后收集返回结果：

```php
PHP_EMBED_START_BLOCK(argc,argv)

  char *command;

  zval retval;

  spprintf(&command, 0, "return nl2br('%s');", paramin);

  zend_eval_string(command, &retval);

  efree(command);

  paramout = Z_STRVAL(retval);

PHP_EMBED_END_BLOCK()
```

正如刚才的 `include` 变体，这种方法有一个致命缺陷：如果提供的 `paramin` 是错误数据，函数将会失败。解决方案是完全不编译代码，而是直接使用 `call_user_function()` API 调用函数：

```c
int call_user_function(HashTable *function_table, zval **object_pp,

                       zval *function_name, zval *retval_ptr,

                       zend_uint param_count, zval *params[] TSRMLS_DC);
```

在实践中，从引擎外部调用时，`function_table` 始终是 `EG(function_table)`。如果是调用对象或类方法，`object_pp` 可以是 `IS_STRING` 值用于静态类调用。`function_name` 通常是要调用函数名称的 `IS_STRING` 值，但也可以是包含元素 0 为对象或类名、元素 1 为方法名的 `IS_ARRAY`。

函数调用的结果将填充到传入 `retval_ptr` 的 `zval` 指针中。`param_count` 和 `params` 就像函数的 `argc/argv` 数据。也就是说，`params[0]` 包含第一个的参数，而 `params[param_count-1]` 包含要传递的最后一个参数。

虽然这里的代码列表实际上变得更长了，但需要完成的工作却大大减少，因为不需要编译中间代码，传递的数据不需要复制，而且每个参数都已经是 Zend 兼容的结构了。此外，请记住，如果使用包含引号的字符串，原始示例可能会产生潜在错误。而这个版本没有了这种缺点。

### 处理错误

当发生严重错误（例如脚本解析错误）时，PHP 将进入 `bailout`（退出）模式。在您目前为止看到的简单嵌入示例中，这意味着直接跳转到 `PHP_EMBED_END_BLOCK()` 宏，并跳过块内剩余的任何代码。由于大多数嵌入 PHP 解释器的应用程序目的并不严格仅仅为了执行 PHP 代码，因此避免 PHP 脚本的退出导致整个应用程序的崩溃是合理的。

一种方法是将所有执行限制在非常小的 `START`/`END` 块中，这样给定的退出只会导致当前块的退出。这种做法的缺点是，每个 `START`/`END` 块都充当自己独立的孤立 PHP 请求。因此，如下所示，一对 `START`/`END` 块不会共享公共作用域，尽管每个块的合法语法本应允许一个块与另一个块协同工作：

```c
int main(int argc, char *argv[])

{

    PHP_EMBED_START_BLOCK(argc, argv)

        zend_eval_string("$a = 1;", NULL, "Script Block 1");

    PHP_EMBED_END_BLOCK()

    PHP_EMBED_START_BLOCK(argc, argv)

        /* 将显示 "NULL",

         * 因为变量 $a 在此请求中并未定义 */

        zend_eval_string("var_dump($a);", NULL, "Script Block 2");

    PHP_EMBED_END_BLOCK()

    return 0;

}
```

另一种隔离这两个 `zend_eval_string()` 调的方法是通过使用某些 Zend 特有的伪语言结构：`zend_try`、`zend_catch` 和 `zend_end_try`。通过使用这些结构，您的应用程序可以为退出目标设置一个临时覆盖，并以合理的方式处理这些严重错误。考虑上述示例的以下变体：

```c
int main(int argc, char *argv[])

{

    PHP_EMBED_START_BLOCK(argc, argv)

        zend_try {

            /* 尝试执行会失败的代码 */

            zend_eval_string("$1a = 1;", NULL, "Script Block 1a");

        } zend_catch {

            /* 发生了错误！

             * 尝试使用不同的行 */

            zend_eval_string("$a = 1;", NULL, "Script Block 1");

        } zend_end_try();

        /* 将显示 "NULL",

         * 因为变量 $a 在此请求中并未定义 */

        zend_eval_string("var_dump($a);", NULL, "Script Block 2");

    PHP_EMBED_END_BLOCK()

    return 0;

}
```

在代码示例的第二个版本中，在 `zend_try` 块内发生的解析错误只会退出到 `zend_catch` 块，并在那里处通过使用一段良好的代码来处理它。相同的块也可以应用于稍后的 `var_dump()` 部分；请尽管尝试一下。

### 初始化 PHP

到目前为止，您已经看到了使用 `PHP_EMBED_START_BLOCK()` 和 `PHP_EMBED_END_BLOCK()` 宏在一个紧凑、原子的包中启动、执行和关闭 PHP 请求。这种方法的好处是，任何严重错误只会导致 PHP 退出到其当前作用域的 `PHP_EMBED_END_BLOCK()` 宏。正如您刚刚学到的，这种理论的主要缺点是，每当您建立一个新的 `START`/`END` 块时，您实际上创建了一个带有新符号表的新请求，并且丢失了任何持久性。获得兼顾隔离性和持久性这两者优点的方法，是将 `START` 和 `END` 宏拆解为它们的组成部分。列表 20.2 显示了本章开始的 `embed3.c` 程序，这次它被拆分成了易于处理的部分。

#### 列表 20.2. `embed3.c` 手动初始化和关闭

```c
#include <sapi/php_embed.h>

int main(int argc, char *argv[])

{

#ifdef ZTS

    void ***tsrm_ls;

#endif

    php_embed_init(argc, argv TSRMLS_CC);

    zend_first_try {

        zend_eval_string("echo 'Hello World!'; NULL,

                         "Embed'd string" TSRMLS_CC);

    } zend_end_try();

    php_embed_shutdown(TSRMLS_C);

    return 0;

}
```

执行的代码与之前相同，只是这次您可以看到那些锁定了您无法分离 `START` 和 `END` 块的左右括号。通过将 `php_embed_init()` 放置于应用程序的开头并将 `php_embed_shutdown()` 置于末尾，您可以在应用程序的整个生命周期内获得单个请求的持久性，同时可以使用 `zend_first_try { } zend_end_try();` 结构来捕获任何原本会导致您的外壳程序退出到 `PHP_EMBED_END_BLOCK()` 宏的致命错误。

**注意**：注意这次使用的是 `zend_first_try` 而不是 `zend_try`。为了在真实环境中使用这种方法，请按照下所示抽象启动和关闭（参见列表 20.3）。

#### 列表 20.3. `embed4.c` 抽象启动和关闭

```c
#include <sapi/php_embed.h>

#ifdef ZTS

    void ***tsrm_ls;

#endif

static void startup_php(void)

{

    /* 为我们的应用程序创建伪造 argc/argv */

    int argc = 1;

    char *argv[2] = { "embed4", NULL };

    php_embed_init(argc, argv TSRMLS_CC);

}

static void shutdown_php(void)

{

    php_embed_shutdown(TSRMLS_C);

}

static void execute_php(char *filename)

{

    zend_first_try {

        char *include_script;

        spprintf(&include_script, 0, "include '%s';", filename);

        zend_eval_string(include_script, NULL, filename TSR_CC);

        efree(include_script);

    } zend_end_try();

}

int main(int argc, char *argv[])

{

    if (argc <= 1) {

        printf("Usage: embed4 scriptfile");

        return -1;

    }

    startup_php();

    execute_php(argv[1]);

    shutdown_php();

    return 0;

}
```

### 覆盖 `INI_SYSTEM` 和 `INI_PERDIR` 选项

在上一章中，您使用了 `zend_alter_ini_setting()` 来某些 PHP INI 选项。由于 `sapi/embed` 直接将脚本推入运行模式，在控制权返回您的应用程序之后，大多数重要的 INI 选项都是不可修改的。为了更改这些值，需要在主引擎启动之后、请求启动之前执行代码，以便这些变量的空间可用。

由于 `embed` 就像任何其他 PHP sapi 实现一样，它通过 `sapi_module_struct` 挂钩到引擎中。`embed` SAPI 声明并填充了该结构体实例，你的应用程序在调用 `php_embed_init()` 之前就可以访问它。

在此结构体中，有一个名为 `php_ini_path_override` 的简单 `char*` 字段。若要请求 `embed`（以及扩展的 PHP 和 Zend）使用你的备用文件，只需在调用 `php_embed_init()` 之前，将此字段填充为以 `NULL` 结尾的字符串，如下 `embed4.c` 中修改后的 `startup_php()` 函数所示：

```c
static void startup_php(void)

{

    /* 创建“虚假” argc/argv 以隐藏

     * 用于我们实际应用程序的参数 */

    int argc = 1;

    char *argv[2] = { "embed4", NULL };

    php_embed_module.php_ini_path_override = "/etc/php_embed4.ini";

    php_embed_init(argc, argv PTSRMLS_CC);

}
```

这允许每个使用 embed 库的应用程序保持可定制性，而不会将其配置强加彼此。相反，如果你希望防止你的应用程序完全使用 `php.ini`，只需设置 `php_embed_module` 中的 `php_ini_ignore` 字段，除非你的应用程序进行了特定的修改，否则所有设置将默认使用其内置值。

## 覆盖 Embed 启动

`sapi_module_struct` 还包含几个回调函数，其中四个函数对于在 PHP 启动和关闭期间定期取回控制权非常有用。

```c
/* 来自 main/SAPI.h */

typedef struct _sapi_module_struct {

    ...

    int (*startup)(struct _sapi_module_struct *sapi_module);

    int (*shutdown)(struct _sapi_module_struct *sapi_module);

    int (*activate)(TSRMLS_D);

    int (*deactivate)(TSRMLS_D);

    ...

} sapi_module_struct;
```

这些方法名让你感到熟悉吗？它们应该对应于扩展的 `MINIT`、`MSHUTDOWN`、`RINIT` 和 `RSHUTDOWN` 方法，并在与扩展相同的周期内触发。为了利用这些挂钩，请将 `embed4` 中的 `startup_php()` 修改为以下版本，并带上提供的额外代码：

```c
static int (*original_embed_startup)(struct _sapi_module_struct *sapi_module);

static int embed4_startup_callback(struct _sapi_module_struct *sapi_module)

{

    /* 先调用原始启动回调，

     * 否则环境将尚未就绪 */

    if (original_embed_startup(sapi_module) == FAILURE) {

        /* 此处可能发生应用程序失败处理 */

        return FAILURE;

    }

    /* 调用原始的 embed_startup 实际上让我们处于

     * ACTIVATE 阶段而不是 STARTUP 阶段，但

     * 我们仍然可以修改大多数 INI_SYSTEM 和 INI_PERDIR 条目

     */

    zend_alter_ini_entry("max_execution_time", sizeof("max_execution_time"),

                 "15", sizeof("15") - 1, PHP_INI_SYSTEM, PHP_INI_STAGE_ACTIVATE);

    zend_alter_ini_entry("safe_mode", sizeof("safe_mode"),

                 "1", sizeof("1") - 1, PHP_INI_SYSTEM, PHP_INI_STAGE_ACTIVATE);

    return SUCCESS;

}

static void startup_php(void)

{

    /* 创建“虚假” argc/argv 以隐藏

     * 用于我们实际应用程序的参数 */

    int argc = 1;

    char *argv[2] = { "embed4", NULL };

    /* 保存原始的启动方法

     * 稍后进行覆盖 */

    original_embed_startup = php_embed_module.startup;

    php_embed_module.startup = embed4_startup_callback;

    php_embed_init(argc, argv PTSRMLS_CC);

}
```

这允许每个使用 embed 库的应用程序保持可定制性，而不会将其配置强加彼此。利用这些挂钩，可以实现你的应用程序捕获 PHP 生成的输出。

## 覆盖 Embed 启动

除非你正在开发一个不需要缓冲区 PHP 输出的应用程序，否则你可能希望通过这种方式来捕获输出。

你会注意到 `log_message` 回调函数的第一个点是，它不包含长度参数，因此不是二进制安全的（binary safe）。这意味着它只会包含一个 NULL 字符，且该字符位于字符串末尾。

对于错误报告用途，这几乎不是问题；事实上，它很有帮助，因为可以对错误消息的操作做出更多假设。默认情况下，`sapi/embed` 会通过这个简单的内置回调将此类错误消息发送到标准错误管道（stderr）：

```c
static void php_embed_log_message(char *message)

{

    fprintf (stderr, "%s\n", message);

}
```

如果你更希望将这些消息发送到日志文件，可以将此版本替换为如下内容：

```c
```



`static void embed4_log_message(char *message)`

```
{
    FILE *log;
    log = fopen("/var/log/embed4.log", "a");
    fprintf (log, "%s\n", message);
    fclose(log);
}
```

## 特殊错误：`sapi_error`

少数特定情况的错误专门属于 SAPI，并绕过主 PHP 错误处理器。这些错误通常与 `header()` 函数的不当使用有关——这是你的非 Web 应用程序不需要担心的事情——以及格式不正确的 HTTP 文件上传（对于控制台应用程序来说这更不是问题）。

由于这些情况与你可能在 `sapi/embed` 中执行的操作非常遥远，最好的办法可能是不要动这个回调。然而，如果你坚持要在源头捕获每种错误，只需实现已提供的回调原型，并在调用 `php_embed_init()` 之前对其进行覆盖即可。

## 同时扩展与嵌入

在你的应用程序中运行 PHP 代码固然很好，但此时 PHP 执行环境仍然是一个被匆忙挂载在主程序旁边的孤立孤儿功能，没有在实质性水平上与之交互的真实手段。

到目前，你应该已经熟悉开发 PHP 扩展以及构建和启用此类扩展所需的各个部分。好了，你现在是在进行嵌入，所以可以把其中一半丢掉。将扩展代码植入嵌入应用程序中所需的胶水代码实际上比独立扩展要少。从一个良好的、全新的嵌入项目开始，如列表 20.4 所示。

### 列表 20.4. `embed5.c` 扩展与嵌入 PHP

```c
#include <sapi/embed/php_embed.h>

#ifdef ZTS
    void ***tsrm_ls;
#endif

/* 扩展部分 */
zend_module_entry php_mymod_module_entry = {
    STANDARD_MODULE_HEADER,
    "mymod", /* extension name */
    NULL, /* function entries */
    NULL, /* MINIT */
    NULL, /* MSHUTDOWN */
    NULL, /* RINIT */
    NULL, /* RSHUTDOWN */
    NULL, /* MINFO */
    "1.0", /* version */
    STANDARD_MODULE_PROPERTIES
};

/* 嵌入部分 */
static void startup_php(void)
{
    int argc = 1;
    char *argv[2] = { "embed5", NULL };
    php_embed_init(argc, argv PTSRMLS_CC);
    zend_startup_module(&php_mymod_module_entry);
}

static void execute_php(char *filename)
{
    zend_first_try {
        char *include_script;
        spprintf(&include_script, 0, "include '%s'", filename);
        zend_eval_string(include_script, NULL, filename TSRMLS_CC);
        efree(include_script);
    } zend_end_try();
}

int main(int argc, char *argv[])
{
    if (argc <= 1) {
        printf("Usage: embed4 scriptfile");
        return -1;
    }
    startup_php();
    execute_php(argv[1]);
    php_embed_shutdown(TSRMLS_CC);
    return 0;
}
```

就这些！从这里开始，你可以定义一个 `function_entry` 向量、启动和关闭方法、声明类以及你想要的任何内容。这就像是你正在使用用户态的 `dl()` 命令加载扩展库一样；Zend 会自动处理所有粘琐的部分，并通过这一个命令让你的模块完成注册并准备就绪。

### 总结

在本章中，你采用了上一章的简单嵌入示例并对其进行了扩展，直到你可以将 PHP 放入大多数任何非线程应用程序的程度。现在你已经掌握了扩展、嵌入以及处理 `zvals`、类条目、资源和哈希表的基础知识，你准备好将它们应用于真实项目了。

在剩余的附录中，你将找到由 PHP、Zend 以及其他扩展导出的许多 API 函数目录。你将看到一组常用代码片段，以及数百个开源 PECL 项目中的几个目录，它们将作为你未来项目的参考。

## A. Zend API 参考

**ZEND 引擎的核心是两组基础性的 API**。第一组是指令处理，它包括脚本的词法分析、编译和执行。第二组 API 则围绕着变量的操作展开，正如你所了解的那样。

### 参数获取

```c
int zend_parse_parameters(int num_args, char *type_spec, ...);
int zend_parse_parameters_ex(int num_args, ...);
int zend_parse_method_parameters(int num_args, zval *this_ptr, char *type_spec, ...);
int zend_parse_method_parameters_ex(int flags, int num_args, zval *this_ptr, char *type_spec, ...);
```

```c
int zend_get_parameters(int ht, int param_count, ...);
int zend_get_parameters_ex(int flags, int param_count, ...);
int zend_get_parameters_array(int ht, int param_count, zval **argument_array);
int zend_get_parameters_array_ex(int flags, int param_count, zval ***argument_array);
```

```c
int zend_copy_parameters_array(int param_count, zval *argument_array);
```

`int ZEND_NUM_ARGS(void);`

| `type_spec` | 参数类型说明符。所处理的参数将根据这些类型进行验证，并在必要时进行转换。详情请参见第 7 章。 |
| --- | --- |
| `...` | 被解引的原生 C 数据类型，用于填充从参数栈中解析出的值。请参见第 7 章。 |
| `flags` | 位掩码字段，目前仅允许一个可能的值 `ZEND_PARSE_PARAMS_QUIET`，它会抑制警告和失败信息。 |
| `this_ptr` | 包含当前对象实例的 `zval*` 指针，例如通过 `getThis()` 返回的内容。 |

### Classes

```c
void INIT_CLASS_ENTRY(zend_class_entry ce, char *classname,
                      zend_function_entry *functions);
void INIT_OVERLOADED_CLASS_ENTRY(zend_class_entry ce, char *classname,
          zend_function_entry *functions, zend_function *handle_fcall,
          zend_function *handle_propget, zend_function *handle_propset);
void INIT_OVERLOADED_CLASS_ENTRY_EX(zend_class_entry ce, char *classname,
          zend_function_entry *functions, zend_function *handle_fcall,
          zend_function *handle_propget, zend_function *handle_propset,
          zend_function *handle_propunset, zend_function *handle_propisset);
```

这组宏使用给定的属性初始化 `zend_class_entry` 结构。注意，尽管 `ce` 是作为立即值传递的，但这些是宏结构，因此可以并且会修改调用值。

| Argument | Purpose |
| --- | --- |
| `ce` | 用于存储初始化值的临时单元。当之后调用 `zend_register_internal_class()` 时，该值将不再有效。 |
| `classname` | 以 `NULL` 结尾的字符字符串，包含用户空间可见的类名。 |
| `functions` | 以 `NULL` 结尾的 `zend_function_entry` 元素向量，如同用于 `zend_module_entry` 结构一样。 |
| `handle_fcall`, `handle_propset`, `handle_propget`, `handle_propunset`, `handle_propisset` | 分别对应 `__call()`、`__get()`、`__set()`、`__unset()` 和 `__isset()` 的系列“魔方法”。 |

```c
void zend_class_implements(zend_class_entry *ce TSRMLS_DC,
                      int num_interfaces, ...);
```

标记一个类实现了一个或多个接口。

| Argument | Purpose |
| --- | --- |
| `ce` | 实现所列接口的类条目 |
| `num_interfaces` | 后续接口的数量，以 `zend_class_entry*` 形式传递 |
| `...` | `num_interfaces` 个 `zend_class_entry*` 指针实例 |

```c
zend_class_entry *zend_register_internal_class(
                      zend_class_entry *ce  TSRMLS_DC);
zend_class_entry *zend_register_internal_class_ex(zend_class_entry *ce,
                      zend_class_entry *parent_ce, char *parent_name TSRMLS_DC);
zend_class_entry *zend_register_internal_interface(
                      zend_class_entry *ce TSRMLS_DC);
```

注册一个之前使用 `INIT_CLASS_ENTRY` 系列宏初始化的 `zend_class_entry`。该方法的 `_ex` 变体允许在注册时进行继承。

| Argument | Purpose |
| --- | --- |
| `ce` | 正在注册的已初始化类条目 |
| `parent_ce` | 该类的父类的已注册类条目 |
| `parent_name` | 如果 `parent_ce->name` 不可用，则用于错误报告的父类名 |

```c
int zend_lookup_class(char *name, int name_len,
                      zend_class_entry ***ppce TSRMLS_DC);
int zend_lookup_class_ex(char *name, int name_len, int use_autoload,
                      zend_class_entry ***ppce TSRMLS_DC);
zend_class_entry *zend_fetch_class(char * name, uint name_len,
                      int fetch_type TSRMLS_DC);
```

通过名称查找类条目。`zend_fetch_class()` 直接返回类条目，而另外两个方法通过引用返回 `zend_class_entry**` 容器。

| Argument | Purpose |
| --- | --- |
| `name` | 要查找的类名，以 `NULL` 结尾。在调用此函数之前不需要转为小写。 |
| `name_len` | 不包含结尾 `NULL` 的类名长度。 |
| `use_autoload` | 如果应使用 `__autoload()` 机制则设置为非零。 |
| `ppce` | 指向 `zend_class_entry**` 变量的指针，用于存储类定义。 |

### Properties

```c
int zend_declare_property(zend_class_entry *ce, char *name, int name,
                      zval *value, int access_type);
int zend_declare_property_ex(zend_class_entry *ce, char *name, int name_length,
                      zval *value, int access_type,
                      char *doc_comment, int doc_comment_len);
int zend_declare_property_null(zend_class_entry *ce, char *name, int name_length,
                      int access_type);
int zend_declare_property_long(zend_class_entry *ce, char *name, int name_length,
                      long value, int access_type);
int zend_declare_property_double(zend_class_entry *ce, char *name, int name_length,
                      double value, int access_type);
int zend_declare_property_string(zend_class_entry *ce, char *name, int name_length,
                      char *value, int access_type);
int zend_declare_property_stringl(zend_class_entry *ce, char *name, int name_length,
                      char *value, int value_len,
                      int access_type);
```

为类定义声明默认属性。这些方法应该在类声明期间调用（例如在 `MINIT` 阶段）。

| Argument | Purpose |
| --- | --- |
| `ce` | 正在修改的 `zend_class_entry*`。 |
| `name` | 以 `NULL` 结尾的属性名。 |
| `name_length` | 不包含结尾 `NULL` 字节的属性名长度。 |
| `value` | 取决于所使用的方法。注意从 `zval` 声明属性时，`zval` 必须是持久分配的。 |
| `value_len` | 这些方法的 `stringl` 变体特有；指定指向值的字符串的长度，不包含结尾的 `NULL`。 |
| `access_type` | `ZEND_ACC_PUBLIC`、`ZEND_ACC_PROTECTED` 或 `ZEND_ACC_PRIVATE` 之一。要声明静态属性而非标准属性，请使用位 `OR` 结合 `ZEND_ACC_STATIC` 的值。 |

| `name_length` | 属性名的长度，不包括末尾的 `NULL` 字节。 |
| --- | --- |
| `value` | 类型特定的值取决于所使用的方法。注意，当从 `zval` 声明属性时，该 `zval` 必须是持久分配的。 |
| `value_len` | 仅适用于这些方法的 `stringl` 变体，指定 `value` 指向的字符串长度，不包括末尾的 `NULL`。 |

```c
void zend_update_property(zend_class_entry *scope, zval *object,
                      char *name, int name_length,
                      zval *value TSRMLS_DC);
```



```c
void zend_update_property_null(zend_class_entry *scope, zval *object,
                      char *name, int name_length TSRMLS_DC);
void zend_update_property_bool(zend_class_entry *scope, zval *object,
                      char *name, int name_length, long value TSRMLS_DC);
void zend_update_property_long(zend_class_entry *scope, zval *object,
                      char *name, int name_length, long value TSRMLS_DC);
void zend_update_property_double(zend_class_entry *scope, zval *object,
                      char *name, int name_length, double value TSRMLS_DC);
void zend_update_property_string(zend_class_entry *scope, zval *object,
                      char *name, int name_length, char *value TSRMLS_DC);
void zend_update_property_stringl(zend_class_entry *scope, zval *object,
                      char *name, int name_length,
                      char *value, int value_len TSRMLS_DC);
int zend_update_static_property(zend_class_entry *scope,
                      char *name, int name_length,
                      zval *value TSRMLS_DC);
int zend_update_static_property_null(zend_class_entry *scope,
                      char *name, int name_length TSRMLS_DC);
int zend_update_static_property_bool(zend_class_entry *scope,
                      char *name, int name_length,
                      long value TSRMLS_DC);
int zend_update_static_property_long(zend_class_entry *scope,
                      char *name, int name_length,
                      long value TSRMLS_DC);
int zend_update_static_property_double(zend_class_entry *scope,
                      char *name, int name_length,
                      double value TSRMLS_DC);
int zend_update_static_property_string(zend_class_entry *scope,
                      char *name, int name_length,
                      char *value TSRMLS_DC);
int zend_update_static_property_stringl(zend_class_entry *scope,
                      char *name, int name_length,
                      char *value, int value_len TSRMLS_DC);
```

设置已实例化对象的标准属性或静态属性。非静态方法会调用 `write_property` 处理器，从而允许对重载的一致使用。

| 参数 | 目的 |
| --- | --- |
| `scope` | 调用时的活动作用域，用于强制 `PPP`（公共/保护/私人）限制。 |
| `object` | 更新非静态属性时，这指向被更新的实例。 |
| `name` | 以 `NULL` 结尾的属性名。 |
| `name_length` | 属性名的长度，不包括末尾的 `NULL` 字节。 |
| `value` | 类型特定的值取决于所使用的方法。 |
| `value_len` | 仅适用于这些方法的 `stringl` 变体；指定 `value` 指向的字符串长度，不包括末尾的 `NULL`。 |

```c
void zend_update_property(zend_class_entry *scope, zval *object,
                      char *name, int name_length,
                      char *value, int value_len TSRMLS_DC);
int zend_update_static_property(zend_class_entry *scope, zval *object,
                      char *name, int name_length,
                      z *value_
```

从给定的类读取属性。非静态方法调用 `read_property` 处理器以允许重载的一致使用。

| 参数 | 目的 |
| --- | --- |
| `scope` | 调用时的活动作用域，用于强制 `PPP`（公共/保护/私人）限制。 |
| `object` | 更新非静态属性时，这指向被更新的实例。 |
| `name` | 以 `NULL` 结尾的属性名。 |
| `name_length` | 属性名的长度，不包括末尾的 `NULL` 字节。 |
| `value` | 类型特定的值取决于所使用的方法。 |
| `value_len` | 仅适用于这些方法的 `stringl` 变体；指定 `value` 指向的字符串长度，不包括末尾的 `NULL`。 |

```c
void zend_update_property(zend_class_entry *scope, zval *object,
                      char *name, int name_length,
                      char *value, int value_len TSRMLS_DC);
int zend_update_static_property(zend_class_entry *scope, zval *object,
                      char *name, int name_length,
                      z *value_
```

从类或实例读取静态属性。

| 参数 | 目的 |
| --- | --- |
| `scope` | 调用时的活动作用域，用于强制 `PPP`（公共/保护/私人）限制。 |
| `object` | 更新非静态属性时，这指向被更新的实例。 |
| `name` | 以 `NULL` 结尾的属性名。 |
| `name_length` | 属性名的长度，不包括末尾的 `NULL` 字节。 |
| `value` | 类型特定的值取决于所使用的方法。 |
| `value_len` | 仅适用于这些方法的 `stringl` 变体；指定 `value` 指向的字符串长度，不包括末尾的 `NULL`。 |

```c
void zend_update_property(zend_class_entry *scope, zval *object,
                      char *name, int name_length,
                      char *value, int value_len TSRMLS_DC);
int zend_update_static_property(zend_class_entry *scope, zval *object,
                      char *name, int name_length,
                      z *value_
```

向已实例化对象添加属性。

| 参数 | 目的 |
| --- | --- |
| `object` | 被更新的实例。 |
| `key` | `NULL` 结尾的字符串（对于公共属性），或由 `zend_mangle_property()` 返回的特殊格式字符串。 |
| `key_length` | 包含末尾 `NULL` 字节的键长度。注意：这些 `ex` 版本会排除此参数中的 `NULL`。 |
| `value` | 类型特定的值取决于所使用的方法。 |
| `value_len` | 仅适用于这些方法的 `stringl` 变体；指定 `value` 指向的字符串长度，不包括末尾的 `NULL`。 |
| `dup` | 如果字符串位于可以传递引擎的 `emalloc` 缓冲区中，则将其设置为非零以强制复制字符串。 |

| 参数 | 目的 |
| --- | --- |
| `scope` | 调用时的活动作用域，用于强制 `PPP`（公共/保护/私人）限制。 |
| `object` | 更新非静态属性时，这指向被更新的实例。 |
| `name` | 以 `NULL` 结尾的属性名。 |
| `name_length` | 属性名的长度，不包括末尾的 `NULL` 字节。 |
| `value` | 类型特定的值取决于所使用的方法。 |
| `value_len` | 仅适用于这些方法的 `stringl` 变体，指定 `value` 指向的字符串长度，不包括末尾的 `NULL`。 |

```c
void zend_update_property(zend_class_entry *scope, zval *object,
                      char *name, int name_length,
                      zval *value TSRMLS_DC);
void zend_update_property_null(zend_class_entry *scope, zval *object,
                      char *name, int name_length TSRMLS_DC);
void zend_update_property_bool(zend_class_entry *scope, zval *object,
                      char *name, int name_length, long value TSRMLS_DC);
void zend_update_property_long(zend_class_entry *scope, zval *object,
                      char *name, int name_length, long value TSRMLS_DC);
void zend_update_property_double(zend_class_entry *scope, zval *object,
                      char *name, int name_length, double value TSRMLS_DC);
void zend_update_property_string(zend_class_entry *scope, zval *object,
                      char *name, int name_length, char *value TSRMLS_DC);
void zend_update_property_stringl(zend_class_entry *scope, zval *object,
                      char *name, int name_length,
                      char *value, int value_len TSRMLS_DC);
int zend_update_static_property(zend_class_entry *scope,
                      char *name, int name_length,
                      zval *value TSRMLS_DC);
int zend_update_static_property_null(zend_class_entry *scope,
                      char *name, int name_length TSRMLS_DC);
int zend_update_static_property_bool(zend_class_entry *scope,
                      char *name, int name_length,
                      long value TSRMLS_DC);
int zend_update_static_property_long(zend_class_entry *scope,
                      char *name, int name_length,
                      long value TSRMLS_DC);
int zend_update_static_property_double(zend_class_entry *scope,
                      char *name, int name_length,
                      double value TSRMLS_DC);
int zend_update_static_property_string(zend_class_entry *scope,
                      char *name, int name_length,
                      char *value TSRMLS_DC);
int zend_update_static_property_stringl(zend_class_entry *scope,
                      char *name, int name_length,
                      char *value, int value_len TSRMLS_DC);
```

设置已实例化对象的标准属性或静态属性。非静态方法会调用 `write_property` 处理器，从而允许对重载的一致使用。

| 参数 | 目的 |
| --- | --- |
| `scope` | 调用时的活动作用域，用于强制 `PPP`（公共/保护/私人）限制。 |
| `object` | 更新非静态属性时，这指向被更新的实例。 |
| `name` | 以 `NULL` 结尾的属性名。 |
| `name_length` | 属性名的长度，不包括末尾的 `NULL` 字节。 |
| `value` | 类型特定的值取决于所使用的方法。 |
| `value_len` | 仅适用于这些方法的 `stringl` 变体；指定 `value` 指向的字符串长度，不包括末尾的 `NULL`。 |



从给定的类读取属性。非静态方法调用`read_property`处理器以允许重载的一致使用。

| 参数 | 目的 |
| --- | --- |
| `scope` | 调用时的活动作用域，用于强制`PPP`（公共/保护/私人）限制。 |
| `object` | 更新非静态属性时，这指向被更新的实例。 |
| `name` | 以`NULL`结尾的属性名。 |
| `name_length` | 属性名的长度，不包括末尾的`NULL`字节。 |
| `value` | 类型特定的值取决于所使用的方法。 |
| `value_len` | 仅适用于这些方法的`stringl`变体；指定`value`指向的字符串长度，不包括末尾的`NULL`。 |

从类或实例读取静态属性。

| 参数 | 目的 |
| --- | --- |
| `scope` | 调用时的活动作用域，用于强制`PPP`（公共/保护/私人）限制。 |
| `object` | 更新非静态属性时，这指向被更新的实例。 |
| `name` | 以`NULL`结尾的属性名。 |
| `name_length` | 属性名的长度，不包括末尾的`NULL`字节。 |
| `value` | 类型特定的值取决于所使用的方法。 |
| `value_len` | 仅适用于这些方法的`stringl`变体；指定`value`指向的字符串长度，不包括末尾的`NULL`。 |

向已实例化对象添加属性。

| 参数 | 目的 |
| --- | --- |
| `object` | 被更新的实例。 |
| `key` | `NULL`结尾的字符串（对于公共属性），或由`zend_mangle_property()`返回的特殊格式字符串。 |
| `key_length` | 包含末尾`NULL`字节的键长度。注意：这些`ex`版本会排除此参数中的`NULL`。 |
| `value` | 类型特定的值取决于所使用的方法。 |
| `value_len` | 仅适用于这些方法的`stringl`变体；指定`value`指向的字符串长度，不包括末尾的`NULL`。 |
| `dup` | 如果字符串位于可以传递引擎的`emalloc`缓冲区中，则将其设置为非零以强制复制字符串。 |

带有作用域信息的属性属性编码。

| 参数 | 目的 |
| --- | --- |
| `dest` | 通过引用填充的包含混淆属性名的新分配内存。 |
| `dest_len` | 包含末尾`NULL`字节的混淆属性名的长度。 |
| `scope` | 为了为`PRIVATE`访问编码属性名，在此指定“所有”类的`NULL`结尾名称。`PROTECTED`属性应使用`*`。`PUBLIC`属性不应使用此函数。 |
| `scope_len` | 不包括末尾`NULL`字节的作用域长度。例如，`PROTECTED`作用域长度始终为1。 |
| `propname` | 在用户空间中显示的实际属性的`NULL`结尾名称。 |
| `propname_len` | 不包括末尾`NULL`字节的属性名长度。 |
| `internal` | 设置为0时将使用每次请求内存分配；否则，将执行持久分配。 |

### 对象

```c
int object_init(zval *arg);
int object_init_ex(zval *arg, zend_class_entry *ce);
int object_and_properties_init(zval *arg, zend_class_entry *ce,
                          HashTable *properties TSR_DC);
```

实例化一个新对象。

| `ce` | 要实例化对象的类条目。`object_init()`会自动分配与内置`stdClass`对应的调用条目。 |
| `properties` | 要复制到新对象中的初始属性，以代替该类的默认属性。 |

```c
zend_object *zend_objects_get_address(zval *object TSRMLS_DC);
void *zend_object_store_get_object(zval *object TSRMLS_DC);
```

这些函数除了返回值的类型转换外完全相同。它们获取一个指向`zend_object*`结构体的指针（在第一个情况下，第一个元素是包含`zend_object`的自定义结构），该指针对应传入的`object` zval。

| 参数 | 目的 |
| --- | --- |
| `object` | 对象实例 |

```c
zend_class_entry *Z_OBJCE_P(zval *object)
zend_class_entry *zend_get_class_entry(zval *object TSRMLS_DC);
int zend_get_object_classname(zval *object,
                      char **name, zend_uint *name_len TSRMLS_DC);
```

获取给定对象的类条目或名称。

| 参数 | 目的 |
| --- | --- |
| `object` | 对象实例。 |
| `name` | 返回时，填充指向`NULL`结尾字符串的指针，该字符串包含与`object`关联类名。返回的内存位置仍属于类条目，调用范围不应释放。 |
| `name_len` | 返回`name`指向的字符串长度。 |

```c
zend_object_handlers *zend_get_std_object_handlers();
```

返回一个常量（不可修改的）结构，其中包含用户态类定义和`stdClass`实例使用的标准对象处理程序。

### 异常

```c
zval * zend_throw_exception(zend_class_entry *exception_ce,
                            char *message, long code TSRMLS_DC);
zval * zend_throw_exception_ex(zend_class_entry *exception_ce,
                            long code TSRMLS_DC, char *format, ...);
zval * zend_throw_error_exception(zend_class_entry *exception_ce,
                            char *message, long code, int severity TSRMLS_DC);
void zend_throw_exception_object(zval *exception_obj TSRMLS_DC);
```

抛出一个类似于在用户态中使用`throw`关键字调用的异常。从内部调用此函数不会立即恢复脚本执行到下一个catch，意味着可能会进行额外的抛出后处理。然而，在你的内部函数将控制权交回执行器之后，catch将被处理。

| 参数 | 目的 |
| --- | --- |
| `exception_ce` | 以类条目形式提供的抛出的异常类型。通常将使用`zend_exception_get_default()`或`zend_get_error_exception()`之一传递。 |
| `exception_obj` | 一个自自`Exception`类的准备异常对象。 |
| `code` | 数值异常代码；通过`$e->getCode()`返回。 |
| `severity` | 异常类特定；通过`$e->getSeverity()`返回。 |
| `message` | 简单的`NULL`结尾消息。 |
| `format` | `sprintf`风格的格式参数以及后续参数列表。 |
| `...` | 与`sprintf`格式说明符对应的变参数列表。 |

```c
zend_class_entry *zend_exception_get_default(void);
zend_class_entry *zend_get_error_exception(void);
```

返回引擎定义的异常类的类条目。`ErrorException`是`zend_throw_error_exception()`使用的`Exception`类的子类。

### 执行

```c
zend_bool zend_make_callable(zval *callable, char **callable_name TSRMLS_DC);
zend_bool zend_is_callable(zval *callable, uint check_flags,
                      char **call_name);
zend_bool zend_is_callable_ex(zval *callable, uint check_flags,
                      char **call_name, int *call_name_len,
                      zend_class_entry **ce_ptr, zend_function **fptr_ptr,
                      zval ***obj_ptr_ptr TSRMLS_DC);
```

检查命名函数是否可调用。如果可调用则返回0，否则返回非0。

| 参数 | 目的 |
| --- | --- |
| `callable` | 通用回调值。可能是简单的字符串，也可能是包含对象/类和方法名的数组。 |
| `check_flags` | 以下值中的一个或多个：`IS_CALLABLE_CHECK_SYNTAX_ONLY`、`IS_CALLABLE_CHECK_STATIC`。 |
| `call_name` | 如果不是作为`NULL`传递，则填充将使用的调用语法的可读表示。对错误消息很有帮助。 |
| `call_name_len` | 格式化`call_name`字符串的长度。 |
| `ce_ptr` | 使用数组语法时，此值将填充发现的类条目。 |
| `fptr_ptr` | 填充指向发现的函数或方法的`zend_function*`指针。 |
| `obj_ptr_ptr` | 使用数组语法时，此值将填充发现的对象实例。 |

```c
int call_user_function(HashTable *function_table, zval **object_pp,
                      zval *function_name, zval *retval_ptr,
                      zend_uint param_count, zval *params[] TSRMLS_DC);
int call_user_function_ex(HashTable *function_table, zval **object_pp,
                      zval *function_name, zval **retval_ptr_ptr,
                      zend_uint param_count, zval **params[],
                      int no_separation, HashTable *symbol_table TSRMLS_DC);
```

通过其用户态名称调用用户态或内部函数。函数的返回值将要么复制到`retval_ptr`中或引用到`retval_ptr_ptr`中。返回`SUCCESS`或`FAILURE`。

| 参数 | 目的 |
| --- | --- |
| `function_table` | 用于查找命名函数的默认函数表。这通常将是`EG(function_table)`。 |
| `object_pp` | 执行方法调用的对象实例或类名。 |
| `function_name` | 通用回调值。如`zend_is_callable()`的`String`或`Array`。 |
| `retval_ptr` | 填充被调用函数的结果。 |
| `param_count` | `params`向量中预期参数数量。 |
| `params` | `param_count`个单或双引用`zvals`向量。 |
| `no_separation` | 设置为1时，分离传递参数会导致调用`FAILURE`。 |
| `symbol_table` | 给被调用函数的预构建符号表。注意：在此函数完成后，符号表将被销毁。 |

```c
int zend_eval_string(char *str, zval *retval_ptr, char *string_name TSRMLS_DC);
int zend_eval_string_ex(char *str, zval *retval_ptr, char *string_name,
                      int handle_exceptns TSRMLS_DC);
```

评估任意PHP代码字符串，类似于用户态函数`eval()`。

| 参数 | 目的 |
| --- | --- |
| `str` | 要处理的PHP代码字符串。 |
| `retval_ptr` | 如果产生返回值，则填充。 |
| `string_name` | 用于错误响应的描述性字符串。 |
| `handle_exceptns` | 如果设置为真，任何异常都将自动重新抛出并返回结果码`FAILURE`。 |

```c
int zend_execute_scripts(int type TSRMLS_DC, zval **retval, int count, ...);
```

执行由准备好的`zend_file_handle`结构引用或多个脚本文件。此方法与第19章“设置主机环境”中`php_execute_script()`函数类似。这两个之间的主要区别是，PHPAPI版本处理额外的INI设置，如`auto_prepend_file`和`auto_append_file`。

| 参数 | 目的 |
| --- | --- |
| `type` | 包含类型。`ZEND_INCLUDE`、`ZEND_REQUIRE`、`ZEND_INCLUDE_ONCE`或`ZEND_REQUIRE_ONCE`之一。 |
| `retval` | 完成后填充为由系列脚本产生的最终返回值。 |
| `count` | 预期后续变长参数列表中`zend_file_handle`结构体的数量。 |
| `...` | 需要处理的`count`个`zend_file_handle*`变量列表。 |

```c
void zend_set_timeout(long seconds);
void zend_unset_timeout(TSRMLS_D);
```

控制脚本执行超时时间，类似于用户态的`set_time_limit()`函数。

### INI设置

```c
int zend_alter_ini_entry(char *name, uint name_length,
                      char *value, uint value_length,
                      int modify_type, int stage);
int zend_restore_ini_entry(char *name, uint name_length, int stage);
```

更改或恢复INI设置。

| 参数 | 目的 |
| --- | --- |
| `name` | 被修改的INI条目的`NULL`结尾名称。 |
| `name_length` | `name`的长度，包括结尾的`NULL`字节。 |
| `value` | 文本字符串形式的新值，无论最终存储类型为何。始终以`NULL`结尾。 |
| `value_length` | `value`的长度，不包括结尾的`NULL`字节。 |
| `modify_type` | 调用作用域声明的访问级别；必须包含与被修改选项相同的级别，但也可以包含其他级别：`PHP_INI_SYSTEM`、`PHP_INI_PERDIR`、`PHP_INI_USER`。 |



| `stage` | Zend Engine 的当前执行阶段。可选：`PHP_INI_STAGE_STARTUP`、`PHP_INI_STAGE_ACTIVATE`、`PHP_INI_STAGE_RUNTIME`、`PHP_INI_STAGE_DEACTIVATE`、`PHP_INI_STAGE_SHUTDOWN`。 |

```
long zend_ini_long(char *name, uint name_length, int orig);
double zend_ini_double(char *name, uint name_length, int orig);
char *zend_ini_string(char *name, uint name_length, int orig);
```

获取并转换 INI 值。这些 API 函数还封装在宏中，如 `INI_STR()` 或 `INI_ORIG_LONG()`；更多信息请参阅第 13 章“INI 设置”。

| 参数 | 目的 |
| --- | --- |
| `name` | 要查找的 INI 选项的 `NULL` 结尾名称。 |
| `length` | `name` 的长度，包括结尾的 `NULL` 字节。 |
| `orig` | 设置为零时，返回可能被覆盖的当前 INI 设置。否则，返回原始的、未修改的设置。 |

### 数组操作

```
int array_init(zval *arg);
```

在预分配的 `arg` 中初始化数组。

```
int add_assoc_null(zval *arg, char *key);
int add_assoc_bool(zval *arg, char *key, int val);
int add_assoc_long(zval *arg, char *key, long val);
int add_assoc_double(zval *arg, char *key, double val);
int add_assoc_resource(zval *arg, char *key, int val);
int add_assoc_string(zval *arg, char *key, char *val);
int add_assoc_stringl(zval *arg, char *key, char *val, uint len);
int add_assoc_zval(zval *arg, char *key, zval);
int add_index_null(zval *arg, ulong idx);
int add_index_bool(zval *arg, ulong idx, int val);
int add_index_long(zval *arg, ulong idx, long val);
int add_index_resource(zval *arg, ulong idx, int val);
int add_index_double(zval *arg, ulong idx, double val);
int add_index_string(zval *arg, ulong idx, char *val, int dup);
int add_index_stringl(zval *arg, ulong idx, char *val, uint len, dup);
int add_index_zval(zval *arg, ulong index, zval);
int add_next_index_null(zval *arg);
int add_next_index_bool(zval *arg, int val);
int add_next_index_long(zval *arg, long val);
int add_next_index_resource(zval *arg, int val);
int add_next_index_double(zval *arg, double val);
int add_next_index_string(zval *arg, char *val, int dup);
int add_next_index_stringl(zval *arg, char *val, uint len, dup);
int add_next_index_zval(zval *arg, zval);
```

向 `Array` 变量中以特定索引、键或下一个连续位置添加元素。

| 参数 | 目的 |
| --- | --- |
| `arg` | 需要扩展的预初始化的 `Array zval`。 |
| `index` / `key` | 数组中用于放置新元素的数值位置或关联位置。 |
| `val` | 封装在 `zval` 中的特定类型数据（如有必要），并放入数组的 `HashTable` 中。请注意，这些函数不会增加原始 `zval` 的 `refcount`（引用计数）。 |
| `len` | 字符串特定的长度指定符。 |
| `dup` | 字符串特定的复制标志位，如果传递的字符串无法直接被引擎所有。 |

### 哈希表

```
int zend_hash_init(HashTable *ht, uint nSize, hash_func_t pHashFunction,
                      dtor_func_t pDestructor, zend_bool persistent);
int zend_hash_init_ex(HashTable *ht, uint nSize, hash_func_t pHashFunction,
                      dtor_func_t pDestructor, zend_bool persistent,
                      zend_bool bApplyProtection);
```

创建一个原始 `HashTable`。

| 参数 | 目的 |
| --- | --- |
| `ht` | 正在初始化、销毁或清理的 `HashTable`。 |
| `nSize` | `HashTable` 预期包含的元素数量。增加此数值需要更多内存。 |
| `pHashFunction` | 已弃用。旧版本的 Zend Engine 允许覆盖哈希函数。 |
| `pDestructor` | 每当元素从 `HashTable` 移除或替换时自动调用的函数。 |
| `persistent` | 设置为非零时，将使用持久性内存分配器而非 `emalloc()` 系列。 |
| `bApplyProtection` | 设置为非零时，遍历 `HashTable` 的迭代将被限制在最大次数。 |

```
int zend_hash_add(HashTable *ht, char *arKey, uint nKeyLength,
                      void *pData, uint nDataSize, void **pDest);
int zend_hash_update(HashTable *ht, char *arKey, uint nKeyLength,
                      void *pData, uint nDataSize, void **pDest);
int zend_hash_quick_add(HashTable *ht, char *arKey, uint nKeyLength,
                      ulong hash_value, void *pData, uint nDataSize,
                      void **pDest);
int zend_hash_quick_update(HashTable *ht, char *arKey, uint nKeyLength,
                      ulong hash_value, void *pData, uint nDataSize,
                      void **pDest);
int zend_hash_index_update(HashTable *ht, ulong index,
                      void *pData, uint nDataSize, void **pDest);
int zend_hash_next_insert(HashTable *ht, void *pData, uint nDataSize,
                      void **pDest);
```

| 参数 | 目的 |
| --- | --- |
| `ht` | 正在修改的 `HashTable`。 |
| `arKey` | `NULL` 结尾的关联键字符串。 |
| `nKeyLength` | `arKey` 的长度，包括结尾的 `NULL` 字节。 |
| `index` | 数值哈希索引。 |
| `hash_value` | 预计算的关联键哈希值。 |
| `pData` | 要存储数据的指针。 |
| `nDataSize` | 存储的数据大小（字节）。 |
| `pDest` | 如果请求，将填充一个指向 `pData` 所指数据在 `HashTable` 内部副本的指针。允许原地修改。 |

`zend_hash_clean()` 仅会清空 `HashTable` 的内容，而 `destroy` 变体会释放所有内部结构并使 `HashTable` 变得不可用。优雅的关闭耗时稍长；但它能保持 `HashTable` 处于一致状态，允许在销毁期间进行访问和修改。

```
void zend_hash_apply(HashTable *ht, apply_func_t apply_func TSRMLS_DC);
void zend_hash_apply_with_argument(HashTable *ht,
                      apply_func_arg_t apply_func, void *arg TSRMLS_DC);
void zend_hash_apply_with_arguments(HashTable *ht,
                      apply_func_args_t apply_func, int, ...);
void zend_hash_reverse_apply(HashTable *ht, apply_func_t apply_func TSRMLS_DC);
```

遍历 `HashTable` 并在每个元素调用一个应用函数，同时传递可选参数。

| 参数 | 目的 |
| --- | --- |
| `ht` | 要遍历的 `HashTable`。 |
| `apply_func` | 符合相应原型的回调函数；更多信息请参阅第 8 章，“处理数组和哈希表”。 |
| `arg` | 用于传递单个 `arg` 的通用指针参数。 |
| `arg_count` | 可变参数列表中后续的参数数量。 |
| `...` | 包含 `arg_count` 个用于应用函数的可变参数列表。 |

```
void zend_hash_internal_pointer_reset_ex(HashTable *ht, HashPosition *pos);
int zend_hash_move_forward_ex(HashTable *ht, HashPosition *pos);
int zend_hash_move_backwards_ex(HashTable *ht, HashPosition *pos);
void zend_hash_internal_pointer_end_ex(HashTable *ht, HashPosition *pos);
```

使用 `HashPosition` 指示器手动遍历 `HashTable`。

| 参数 | 目的 |
| --- | --- |
| `ht` | 正在遍历的 `HashTable`。 |
| `pos` | 位置指示器。此值将由 `zend_hash_internal_pointer_reset_ex()` 自动初始化，不需要销。 |

```
int zend_hash_get_current_key_type_ex(HashTable *ht, HashPosition *pos);
```

确定 `pos` 所指示的 `HashTable` 位置处的键类型。返回三个值之一：`HASH_KEY_IS_LONG`、`HASH_KEY_IS_STRING` 或 `HASH_KEY_NON_EXISTANT`。

```
int zend_hash_get_current_key_ex(HashTable *ht,
                      char **str_index, uint *str_length, ulong *num_index,
                      zend_bool duplicate, HashPosition *pos);
int zend_hash_get_current_data_ex(HashTable *ht, void **pData,
                      HashPosition *pos);
```

检查当前 `HashTable` 位置处的键和数据元素。数据变体返回 `SUCCESS` 或 `FAILURE`，键变体返回 `zend_hash_get_current_key_type_ex()` 中描述的键类型。

| 参数 | 目的 |
| --- | --- |
| `ht` | 正在检查的 `HashTable`。 |
| `str_index` | 填充关联键名。 |
| `str_length` | 填充关联键的长度。此值将包含末尾的 `NULL` 字节。 |
| `num_index` | 填充数值键索引。 |
| `duplicate` | 如果键名在返回到调用作用域之前应复制，则设置为非零值；在这种情况下，调用作用域需要在适当的时间释放该拷贝。 |
| `pData` | 填充指向 `HashTable` 内部存储中持有数据的指针。此值可以直接修改、被动检查或复制到局部结构中。 |
| `pos` | 当前 `HashTable` 遍历位置。 |

```
int zend_hash_exists(HashTable *ht, char *arKey, uint nKeyLength);
int zend_hash_quick_exists(HashTable *ht, char *arKey, uint nKeyLength, ulong hash_value);
int zend_hash_index_exists(HashTable *ht, ulong index);
```

确定 `HashTable` 中的给定位置是否被占用。如果索引或键存在，则返回 1，否则返回 0。

| 参数 | 目的 |
| --- | --- |
| `ht` | 正在检查的 `HashTable`。 |
| `arKey` | 关联键名。 |
| `nKeyLength` | 包含末尾 `NULL` 字节的键名长度。 |
| `hash_value` | 预计算的键哈希，由 `zend_get_hash_value()` 返回。 |
| `index` | 数值键索引。 |

```
int zend_hash_find(HashTable *ht, char *arKey, uint nKeyLength, void **pData);
int zend_hash_quick_find(HashTable *ht, char *arKey, uint nKeyLength, ulong hash_value, void **pData);
int zend_hash_index_find(HashTable *ht, ulong index, void **pData);
```

通过键或索引从 `HashTable` 获取数据元素。

| 参数 | 目的 |
| --- | --- |
| `ht` | 正在检查的 `HashTable`。 |
| `arKey` | 关联键名。 |
| `nKeyLength` | 包含末尾 `NULL` 字节的键长度。 |
| `hash_value` | 预计算的键哈希，由 `zend_get_hash_value()` 返回。 |
| `index` | 数值键索引。 |

```
int zend_hash_update_current_key_ex(HashTable *ht, int key_type, ulong index, HashPosition *pos);
```

更改与当前数据相关的键或索引。也可以将 `HashTable` 从索引改为关联键。

| 参数 | 目的 |
| --- | --- |
| `ht` | 正在修改的 `HashTable`。 |
| `key_type` | 新键类型：`HASH_KEY_IS_LONG` 或 `HASH_KEY_IS_STRING`。 |
| `str_index` | 仅用于 `HASH_KEY_IS_STRING` 的关联键。 |
| `str_length` | 关联键长度。 |
| `index` | 仅用于 `HASH_KEY_IS_LONG` 的数值索引。 |
| `pos` | 当前 `HashTable` 遍历位置。 |



```c
int zend_hash_del(HashTable *ht, char *arKey, uint nKeyLength);
int zend_hash_index_del(HashTable *ht, ulong index);
```

通过索引或关联键从 `HashTable` 中删除元素。

| 参数 | 目的 |
| --- | --- |
| `ht` | 正在修改的 `HashTable`。 |
| `arKey` | `NULL` 终止的关联键。 |
| `nKeyLength` | 包含末尾 `NULL` 字节的键长度。 |
| `index` | 数值索引值。 |

```c
void zend_hash_copy(HashTable *dst, HashTable *src, copy_ctor_func_t pCopyConstructor, void *tmp, uint size);
void zend_hash_merge(HashTable *dst, HashTable *src, copy_ctor_func_t pCopyConstructor, void *tmp, uint size, int overwrite);
void zend_hash_merge_ex(HashTable *dst, HashTable *src, copy_ctor_func_t pCopyConstructor, uint size, merge_checker_func_t pMergeSource, void *pParam);
```

使用 `pCopyConstructor` 方法将元素从 `src` 复制到 `dst`，必要时执行额外的资源复制。对于 `zend_hash_copy()`，`src` 中的所有元素都会复制到 `dst`。`zend_hash_merge()` 行为相同，除非 `overwrite` 值为零，此时现有键/索引将保持不变。`zend_hash_merge_ex()` 使用回调方法逐个判断元素是否应该被替换。更多信息请参阅第 8 章，“处理数组和哈希表”。

| 参数 | 目的 |
| --- | --- |
| `dst` | 目标 `HashTable`。 |
| `src` | 源 `HashTable`。 |
| `tmp` | 有足够空间存储 `src` 中任意元素的临时变量。注意：自 PHP 4.0.3 版本起不再使用。 |
| `size` | 元素的大小。 |
| `pCopyConstructor` | 用于复制元素子数据的回调。 |
| `pMergeChecker` | 用于比较源和目的键值以确定是否应替换的回调。 |
| `pParam` | 传递给 `pMergeChecker` 函数的任意参数。 |
| `overwrite` | 设置为非零值使 `zend_hash_merge()` 行为类似于 `zend_hash_copy()`。 |

```c
int zend_hash_sort(HashTable *ht, sort_func_t sort_func,
                      compare_func_t compare_func, int renumber TSRMLS_DC);
int zend_hash_compare(HashTable *ht, HashTable *ht2,
                      compare_func_t compare_func, zend_bool ordered TSRMLS_DC);
```

排序给定的 `HashTable` 或将其与另一个比较。有关这些 API 调用的示例，请参考第 8 章。

| 参数 | 目的 |
| --- | --- |
| `ht` | 正在排序或比较的主 `HashTable`。 |
| `ht2` | 用于比较的次要 `HashTable`。 |
| `sort_func` | 用于处理实际排序操作的回调方法。 |
| `compare_func` | 用于比较 `ht` 中的单个元素与 `ht2` 中的单个元素的回调函数。 |
| `renumber` | 如果在排序时应对数字索引从零开始重新编号，则设置为非零。 |
| `ordered` | 设置为非零以根据 `HashTable` 内部的顺序进行比较，而不是内部索引或键值。 |

```c
int zend_hash_num_elements(HashTable *ht);
ulong zend_hash_next_free_element(HashTable *ht);
int zend_hash_minmax(HashTable *ht, compare_func_t compare_func,
                      int findmax, void **pData TSRMLS_DC);
```

分别返回元素数量、下一个可分配索引号以及 `HashTable` 中最低/最高的数据。

| 参数 | 目的 |
| --- | --- |
| `ht` | 正在检查的 `HashTable`。 |
| `compare_func` | 用于确定最大/最小值的比较函数。 |
| `findmax` | 设置为非零以查找最大值，设置为零以查找最小值。 |
| `pData` | 填充由 `compare_func` 确定的最小值/最大值。 |

```c
ulong zend_hash_func(char *arKey, uint nKeyLength);
ulong zend_get_hash_value(char *arKey, uint nKeyLength);
```

相同的函数，旨在根据 `arKey` 和 `nKeyLength` 使用内置的 `DJBX33A` 哈希函数返回哈希值。

### 资源/列表

```c
int zend_register_list_destructors(void (*ld)(void *),
                      void (*pld)(void *), int module_number);
int zend_register_list_destructors_ex(rsrc_dtor_func_t ld,
                      rsrc_dtor_func_t pld, char *type_name,
                      int module_number);
```

注册一个列表项并与其关联析构函数。当使用关联列表类型的项从 `EG(reuglar_list)` 中移除时，将调用非持久的 `ld` 析构函数。当移除此类持久性项时，将改为调用 `pld` 析构函数。

| 参数 | 目的 |
| --- | --- |
| `ld` | 非持久性析构方法。 |
| `pld` | 持久性析构方法。 |
| `type_name` | 资源类型的描述名称。 |
| `module_number` | 给引擎关于谁拥有此资源类型的提示。应该从 `MINIT` 方法原封不动地传递。 |

```c
int zend_list_insert(void *ptr, int type);
int zend_register_resource(zval *result, void *ptr, int type);
```

将资源指针放入 `EG(regular_list)` `HashTable` 中并返回一个数字资源 ID。`zend_register_resource()` 更进了一步，并将该资源 ID 填充到资源变量中。

| 参数 | 目的 |
| --- | --- |
| `ptr` | 要存储的资源指针。 |
| `type` | 注册并用于后续销毁的类型。 |
| `result zval` | 填充资源 ID 以返回用户空间代码。 |

```c
int zend_list_addref(int id);
int zend_list_delete(int id);
```

增加给定 ID 的引用计数。`zend_list_delete()` 在引用计数归零时删除资源。

```c
int *zend_list_num_elements(HashTable *ht);
ulong *zend_list_next_free_element(HashTable *ht);
int *zend_list_minmax(HashTable *ht, compare_func_t compare_func,
                      int findmax, void **pData TSR_DC);
```

分别返回元素数量、下一个可分配索引号以及 `HashTable` 中最低/最高的数据。

```c
ulong *zend_list_func(char *arKey, uint nKeyLength);
ulong *zend_list_get_hash_value(char *arKey, uint nKeyLength);
```

相同的函数，旨在根据 `arKey` 和 `nKeyLength` 使用内置的 `DJBX33A` 哈希函数返回哈希值。

### 链列表

```c
int zend_llist_count(zend_llist *l);
```

返回 Zend 链表中的元素数量。

![](img/30011536.html)

### Memory

```c
void *emalloc(size_t size);
void *safe_emalloc(size_t nmemb, size_t size, size_t offset);
void *ecalloc(size_t nmemb, size_t siz);
void *erealloc(void *ptr, size_t size, int allow_failure);
void *pemalloc(size_t size, int persistent);
void *safe_pemalloc(size_t nmemb, size_t size, size_t offset, int persistent);
vpod *pecalloc(size_t nmemb, size_t siz, int persistent);
void *perealloc(void *ptr, size_t size, int allow_failure);
```

根据需要分配 `size` 或 `((nmemb*size)+offset)` 字节的内存。这些函数的含义通常映射到它们的 `ANSI-C` 等效函数。任何 `p*` 变体都会根据条件分配持久内存。如果 `persistent` 标志设置为 0，或者使用非 `p*` 系列的分配器，则分配的任何内存将在请求结束时自动释放。

| Argument | Purpose |
| --- | --- |
| `ptr` | 已分配的指针，将重新分配为新大小。 |
| `size` | 要分配的字节数。 |
| `nmemb` | 与 `calloc` 和 `safe_*` 系列分配器配合使用。与 `size` 相乘以分配多个等大小的连续内存块。 |
| `offset` | 加到 `size*nmemb` 计算中，用于分配额外的“奇数”字节。 |
| `allow_failure` | 通常情况下，底层 `realloc()` 函数的失败会导致 `erealloc()` 强制引擎进入退出模式（bailout mode）并结束任何中的脚本。设置此标志将允许 `erealloc` 静默失败并返回 `NULL`。 |
| `persistent` | 设置时，将使用普通的系统分配函数，而不是按请求分配的分配器。 |

```c
char *estrdup(const char *s);
char *estrndup(const char *s, unsigned int length);
char *pestrdup(const char *s, persistent);
char *zend_strndup(const char *s, unsigned int length);
```

复制以第一个 `NULL` 字节（包括该字节）或以 `length` 个字符结尾的字符串数据。与大多数内存相关的函数不同，`estrndup()` 的持久版本被命名为 `zend_strndup()`，并且没有用于交互式禁用持久性的标志位。

| Argument | Purpose |
| --- | --- |
| `s` | 要复制的字符串。 |
| `length` | 要复制的数据长度，如果已知的话。 |
| `persistent` | 设置时，将使用普通的系统分配函数，而不是按请求分配的分配器。 |

```c
void efree(void *ptr);
void pefree(void *ptr, int persistent);
```

释放之前分配的内存块。如果该内存是持久性分配的，则必须以相同的方式释放，反之亦然。在非持久内存块上使用持久释放或反之，将导致内存损坏并可能引发段错误（segfault）。

```c
int zend_set_memory_limit(unsigned int memory_limit);
```

修改 `php.ini` 中指定的内存限制。如果实际上没有启用内存限制，此函数将返回 `FAILURE`。

### Constants

```c
int zend_get_constant(char *name, uint name_len, zval *result TSRMLS_DC);
```

查找已注册常量的值。如果找到，该值将复制到 `result` 中，函数返回 `0` 表示成功。

| Argument | Purpose |
| --- | --- |
| `name` | 要获取的常量的 `NULL` 结尾的名字。也可以是 `CLASSNAME::CONSTANT` 的形式以获取类常量。 |
| `name_len` | 不包括结尾 `NULL` 字节的常量名长度。 |
| `result` | 预分配的 `zval` 容器，用于填充常量的副本。 |

```c
void zend_register_long_constant(char *name, uint name_len, long value,
                      int flags, int module_number TSRMLS_DC);
void zend_register_double_constant(char *name, uint name_len, double value,
                      int flags, int module_number TSRMLS_DC);
void zend_register_string_constant(char *name, uint name_len, char *value,
                      int flags, int module_number TSRMLS_DC);
void zend_register_stringl_constant(char *name, uint name_len,
                      char *value, uint value_len,
                      int flags, int module_number TSRMLS_DC);
int zend_register_constant(zend_constant *c TSRMLS_DC);
```

使用传递的值注册指定类型的常量。其他其他类型的常量（不包括数组和对象）也可以通过手动构建 `zend_constant` 并将其传递给 `zend_register_constant()` 来注册。

| Argument | Purpose |
| --- | --- |
| `name` | 要注册的常量的 `NULL` 结尾的名字。 |
| `name_len` | 包括结尾 `NULL` 字节的常量名长度。 |
| `value` | 用于初始化常量的值。 |
| `value_len` | 专门用于字符串，不包括结尾 `NULL` 字节的字符串值长度。 |
| `flags` | `CONST_CS` 和/或 `CONST_PERSISTENT` 的任何组合。 |
| `module_number` | 从 `MINIT` 或 `RINIT` 原样传递的。 |
| `c` | 初始化的 `zend_constant` 结构。更多信息请参阅第 12 章](#ch12.html#ch12)“启动、关闭以及之间的几点”。 |

![](img/30011536.html)

### Variables

```c
void zval_add_ref(zval **ppzval);
```

增加 `ppzval` 的引用计数（`refcount`）。此函数等同于命令：`(*ppzval)->refcount++;`。与其它访问函数和宏一样，建议使用该函数而不是直接访问。

```c
void zval_copy_ctor(zval *zvalue);
```

复制一个 zval。详细用法请参阅第 8 章](ch08.html#ch08)。

```c
void zval_ptr_dtor(zval **ppzval);
```

将 `ppzval` 的引用计数减一。如果引用计数为零，则销毁内部结构。

```c
void zval_dtor(zval *zvalue);
```

释放 zval 的所有结构，无论引用计数如何。

```c
char *zend_zval_type_name(zval *arg);
```

将 zval 的数值类型转换为可读名称。例如，如果 `arg` 是 `IS_LONG` zval，此函数将返回 `integer`。

```c
int zend_is_true(zval *arg);
```



测试 `arg` 的真值。也就是说，如果用户态条件语句中使用变量，它会产生 `true` 还是 `false` 的结果？假值可能来自 `IS_NULL` 变量以及字面量 `FALSE`，或数值 `0` 或 `0.0`。空字符串、空数组以及一些特殊设计的对象也可以导致假值结果。

```
int zend_register_auto_global(char *name, uint name_len,
                      zend_auto_global_callback callback TSRMLS_DC);
```

注册一个自动（超级）全局变量。在此命名的任何变量将自动解析到全局作用域，就像访问 `$GLOBALS['name']` 一样。

| Argument | Purpose |
| --- | --- |
| `name` | 要全局化的 `NULL` 结尾且区分大小的变量名。 |
| `name_len` | 不包括结尾 `NULL` 的 `name` 长度。 |
| `callback` | 脚本中使用自动全局变量时执行额外代码的编译器钩子。 |

## Miscellaneous API Function

```
char *get_zend_version(void);
```

报告当前 Zend Engine 版本的文本字符串。该字符串由引擎所有，调用者不得将其释放。

```
char *zend_get_module_version(char *module_name);
```

报告与指定模块关联的扩展特定版本。此 API 调用返回的字符串直接来自由指定扩展声明的 `zend_module_entry` 结构。如果指定的扩展未加载，则返回 `NULL`。

```
int zend_disable_function(char *function_name,
                      uint function_name_length TSRMLS_DC);
int zend_disable_class(char *class_name, uint class_name_length TSRMLS_DC);
```

这些 API 通常由引擎本身调用，将现有的函数处理程序替换为旨在报告致命错误的存根（stub）定义。这些 API 调用应仅在执行的启动（`MINIT`）阶段进行。

```
void zend_qsort(void *base, size_t nmemb, size_t size,
                      compare_func_t compare TSRMLS_DC);
```

通用的 `qsort` 算法，旨在配合哈希和链表排序函数使用，也可以单独使用。

| Argument | Purpose |
| --- | --- |
| `base` | 包含 `nmemb` 个成员、每个成员大小为 `size` 字节的向量位置。 |
| `nmemb` | `base` 所指向量中的元素数量。 |
| `size` | 待排序每个单独元素的大小。 |
| `compare` | 比较回调，用于判断给定的两个元素中哪一个更大。 |

```
void zend_bailout(void);
```

立即结束当前的 `zend_try` 块（通常是活跃的脚本/请求）。CPU 将立即执行 `longjmp()` 并跳转到最近的 `zend_catch` 或 `zend_end_try` 块。

## 总结

尽管前面的 API 调用列表看起来很详尽，但与 Zend 引擎中发现的包装宏、可覆盖回调和其他珍宝相比，它们仍然显得相形见绌。许多包装宏在之前的章节中已经介绍过，例如操作变量的 `ZVAL_*()` 族，以及通过 TSRM 访问的 `*G()` 族。花些时间查看源码和其他扩展，你一定能发现更多隐藏的宝藏。

在 附录 B “PHPAPI”中，你将通过对 PHP 核心及其所有扩展（标准、可选和 PECL）中找到函数进行列表，完善核心 API 参考。

![](img/30011536.html)

## B. PHPAPI

PHP 核心和扩展层导出了一系列函数，旨在访问 SAPI、TSRM 和引擎层，并解决大多数 PHP 实现中常见的 Web 环境通用需求。这些 API 调用涵盖了简单的字符串操作、文件和控制台 I/O、以及请求资源管理等主题。在本附录中，你将看到核心 API 方法的详细目录、同样巨大的流层分支，以及扩展 API 标准部分。

![](img/30011536.html)

### 核心 PHP

PHP 核心内部的 API 函数始终可用，不需要额外的包含文件。其中某些方法提供了独特的功能，而另一些则仅作为底层 Zend API 函数的 PHP 映射。

### 输出

```
int php_printf(const char *format, ...);
int php_write(void *buf, uint size TSRMLS_DC);
int PHPWRITE(void *buf, uint size);
void php_html_puts(const char *buf, uint size TSRMLS_DC)
```

生成输出。这三个方法中，`PHPWRITE()` 与 `php_write()` 相同，将数据推入当前输出缓冲区。这些方法的最后一个版本 `php_html_puts()` 通过转义 HTML 实体并对制表符、换行符等特殊字符进行编码来执行额外工作，确保非 HTML 格式数据在使用 HTML 驱动的 SAPI 时显示保持一致。

| Argument | Purpose |
| --- | --- |
| `buf` | 要输出的任意数据的指针 |
| `size` | `buf` 所指数据的长度，以字节为单位 |
| `format` | `sprintf()` 风格的格式字符串 |
| `...` | 与 `format` 格式说明对应的特定类型参数 |

```
int php_start_ob_buffer(zval *output_handler, uint chunk_size,
                      zend_bool erase TSRMLS_DC);
int php_start_ob_buffer_named(const char *handler_name,
                      uint chunk_size, zend_bool erase TSRMLS_DC);
```

初始化一个新的输出缓冲区。注意输出缓冲区是可以堆叠的；因此，此新输出缓冲区产生的任何数据将被任何之前初始化的输出缓冲区重新缓冲。这些方法与其用户态的对应项 `ob_start()` 相同的含义和用法。

| Argument | Purpose |
| --- | --- |
| `output_handler` | 通用回调值。当为此缓冲区生成输出时，将带有单个 `IS_STRING` 参数调用的函数或方法名称。此回调函数不需要处理缓冲的实际工作；它只是在显示之前修改内容的机会。回调函数应返回一个 `IS_STRING` 值。 |
| `chunk_size` | 使用的缓冲区块的大小，单位为字节。 |
| `erase` | 如果缓冲区在消费时应擦除，则设置为非零值。 |
| `handler_name` | `php_start_ob_buffer_named()` 是便利包装器，它将 `handler_name` 加载到 `zval` 中，然后分发给带有其他参数的 `php_start_ob_buffer()`。 |

```
void php_end_ob_buffer(zend_bool send_buffer,
                      zend_bool just_flush TSRMLS_DC);
```

终止或刷新活跃的输出缓冲区。尽管名称如此，此函数并不一定让当前缓冲区结束。

| Argument | Purpose |
| --- | --- |
| `send_buffer` | 将当前缓冲区的内容传递给下一个缓冲区。 |
| `just_flush` | 如果设置为非零值，当前输出缓冲区将保留；否则它将终止。 |

```
void php_end_ob_buffers(zend_bool send_buffer);
```

结束所有输出缓冲，如果 `send_buffer` 设置为零。当此方法完成后，将没有活跃的输出缓冲区，所有输出将直接进入 SAPI 机制。

```
int php_get_buffer(zval *p TSRMLS_DC);
int php_get_length(zval *p TSRMLS_DC);
```

将当前缓冲的内容或其长度拷贝到分配但未初始化的 zval 中。注意此操作不会消耗缓冲区的内容；它只是一个被动拷贝。

```
void php_start_implicit_flush(TSRMLS_D);
void php_end_implicit_flush(TSRMLS_D);
```

切换隐式刷新模式。调用 `php_start_implicit_flush()` 等同于在 `php.ini` 中设置 `implicit_flush`。

```
const char *php_get_output_start_filename(TSRMLS_D);
int php_get_output_start_lineno(TSRMLS_D);
```

获取当前请求开始输出非头部数据的文件名和行号。这通常用于开始输出后尝试使用用户态 `header()` 函数时的错误消息，但也可能被扩展或 SAPI 调用执行其他任务。

### 错误报告

```
void php_set_error_handling(error_handling_t error_handling,
                      zend_class_entry *exception_class TSRMLS_DC)
```

切换当前的错误处理模式。默认情况下，所有内部生成的错误都是作为传统的非异常错误。通过 `EH_THROW` 调用此方法将导致非关键错误（`E_CORE_ERROR`、`E_COMPILE_ERROR`、`E_PARSE`）和非平凡错误（`E_NOTICE`、`E_USER_NOTICE`）作为指定异常类的实例被抛出。

| Argument | Purpose |
| --- | --- |
| `error_handling` | 三种错误处理常量之一：`EH_NORMAL`、`EH_SUPRESS` 或 `EH_THROW`。 |
| `exception_class` | 当发生可抛出错误时，作为错误异常实例特定异常类。通常为 `zend_get_error_exception()`。 |

```
void php_log_err(char *log_message TSRMLS_DC);
```

将错误消息发送到 PHP 错误日志设施。此消息将附加到 `php.ini` 中指定的日志文件中，或如第 20 章“高级嵌入”中所讨论的那样，传递给 SAPI 的 `log_message` 回调函数。

```
void php_error(int type, const char *format, ...);
void php_error_docref(const char *docref TSRMLS_DC,
                      int type, const char *format, ...);
void php_error_docref0(const char *docref TSRMLS_DC,
                      int type, const char *format, ...);
void php_error_docref1(const char *docref TSRMLS_DC, const char *param1,
                      int type, const char *format, ...);
void php_error_docref2(const char *docref TSRMLS_DC,
                      const char *param1, const char *param2,
                      int type, const char *format, ...);
void php_verror(const char *docref, const char *params,
                      int type, const char *format, va_list args TSRMLS_DC) ;
```

产生标准的 PHP 错误消息。注意，此方法的所有形式最终都会通过 `php_verror()` 派发。

| 参数 | 目的 |
| --- | --- |
| `docref` | 手动章节片段，或可以找到错误主题帮助信息的完整 URL。例如，如果抛出的错误与核心函数 `mysql_connect()` 有关，指定 docref 为 `function.mysql-connect`。对于第三方扩展，使用完整的 URL，如 [`myext.example.com/doc/myext_foo.html`](http://myext.example.com/doc/myext_foo.html)。 |
| `params` | 传递给函数的参数逗号分隔列表。注意不要泄露敏感信息，因为错误可能会显示在浏览器中。 |
| `param1`,`param2` | 在期望这些参数的方法中，它们将用逗号连接起来形成单个参数列表，然后作为 `params` 参数传递给 `php_verror()`。 |
| `type` | 抛出的错误类型。可以是任何 `E_*` 常量。通常设置为以下之一：`E_ERROR`、`E_WARNING` 或 `E_NOTICE`。 |
| `format` | `sprintf()` 风格格式说明符。 |
| `...` | 与 `format` 提供的格式说明符对应的变参数列表。 |
| `args` | 由 `va_start()` 产生的编译变参数对象。 |

### 启动、关闭和执行

```
int php_request_startup(TSRMLS_D);
void php_request_shutdown(void *dummy);
```

启动或关闭脚本请求。这几乎完全由 SAPI 或使用嵌入 SAPI 的主机应用程序完成。`dummy` 参数完全没有使用，可能会传递 `NULL` 值。

```
int php_register_extensions(zend_module_entry **list, int count TSRMLS_DC);
int php_register_extension(zend_module_entry *ptr);
```

手动注册一个或多个额外的扩展。

| 参数 | 目的 |
| --- | --- |
| `count` | 要注册的扩展数量 |
| `list` | `count` 个扩展条目的向量向量 |
| `ptr` | 指向单个 `zend_module_entry` 结构体的指针，作为一次初始化一个扩展的便利封装器 |

```
int php_execute_script(zend_file_handle *primary_file TSRMLS_DC);
int php_lint_script(zend_file_handle *file TSRMLS_DC);
```

编译并（可选地）执行脚本文件。两种方法都会通过词法器处理命名脚本以产生标记，并使用解析器将这些标记组装操作码。但只有 `php_execute_script()` 将编译后的操作码派发给执行器。请参考第 19 章“设置”。

注意此方法的所有形式最终都会通过 `php_verror()` 派发。

作为 `php_verror()` 的副作用，使用 `va_start()` 来初始化参数列表。请参考第 19 章“设置”。

注意此方法的所有形式最终都会通过 `php_verror()` 派发。

作为 `php_verror()` 的副作用，使用 `va_start()` 来初始化参数列表。请参考第 19 章“设置”。

### 安全模式

作为 `php_verror()` 的副作用，使用 `va_start()` 来初始化参数列表。请参考第 19 章“设置”。

作为 `php_verror()` 的副作用，使用 `va_start()` 来初始化参数列表。请参考。设置设置，

作为 `php_verror()` 的副作用，使用 `va_start()` 来初始化参数列表。请参考。

```
void php_error_docref(const char *docref TSRMLS_DC,
                      int type, const char *format, ...);
void php_error_docref0(const char *docref TSRMLS_DC,
                      int type, const char *format, ...);
void php_error_docref1(const char *docref TSRMLS_DC, const char *param1,
                      int type, const char *format, ...);
void php_error_docref2(const char *docref TSRMLS_DC,
                      const char *param1, const char *param2,
                      int type, const char *format, ...);
```



`int type, const char *format, ...);`

```c
void php_verror(const char *docref, const char *params,
                      int type, const char *format, va_list args TSRMLS_DC);
```

作为 `php_verror()` 的副作用，使用 `va_start()` 来初始化参数列表。请参考第 19 章“设置”。

### 字符串格式化

```c
int spprintf(char **buf, size_t max_len, const char *format, ...);
int vspprintf(char **buf, size_t max_len, const char *format, va_list ap);
```

类似于 `snprintf()` 和 `vsprintf()`，不同之处这些方法处理非持久缓冲区。记住将这些字符串赋值给 `zval`，或手动使用 `efree()` 释放它们以避免泄漏。请参考本章后面的字符串处理部分。

### 重入安全

```c
struct tm *php_localtime_r(const time_t *timep, struct tm *tm);
char *php_ctime_r(const time_t *clock, char *buf);
char *php_asctime_r(const struct tm *tm, char *buf);
struct tm *php_gmtime_r(const time_t *timep, struct tm *tm);
int php_rand_r(unsigned int *seed);
char *php_strtok_r(char *s, const char *delim, char **last);
```

这些函数遵循其 `POSIX` 对应的原型并增加了重入安全性。为了线程安全，始终建议这些变体。请参考它们的 `man` 页面了解字段的含义和目的。

### 杂项

```c
int php_register_info_logo(char *logo_string, char *mimetype,
                      unsigned char *data, int size);
int php_unregister_info_logo(char *logo_string);
```

这两个方法允许扩展或 SAPI 声明 logo 或“彩蛋”内容。当从开启了 `expose_php` 选项的服务器请求 PHP 页面，且查询字符串为 `=logo_string`，将提供 `data` 指向的内容而不是原本请求的页面。这就是 PHP 致谢页面（`logo_string=PHPB8B5F2A0-3C92-11d3-A3A9-4C7B08C10000`）、彩蛋图片（`logo_string=PHPE9568F36-D428-11d2-A769-00AA001ACF42`）以及其他嵌入内容使用的机制。

| 参数 | 目的 |
| --- | --- |
| `mimetype` | 输出 `data` 时作为头部发送的 Mime-type 字符串。 |
| `data` | 与 `logo_string` 关联的任意数据。注意，注册过程不会复制数据，仅复制其位置的指针；因此，该指针必须在 PHP 关闭或 `logo_string` 标识符被注销之前保持有效。 |
| `size` | `data` 所指向的内容的大小，以字节为单位。 |

```c
void php_add_tick_function(void (*func)(int));
void php_remove_tick_function(void (*func)(int));
```

添加或移除用于用户空间指令 `declare(ticks=count)` 的滴答函数（tick function）。注意，可以注册多个滴答处理器，它们将按照被添加的顺序被调用。

### 流 API

流处理层无疑是 PHP 核心 API 中最大的部分。为了帮助在海量的方法调用中导航，附录的这部分尝试将它们划分为功能组，涵盖创建、访问、操作和销毁。

#### 流的创建与销毁

```c
php_stream *php_stream_alloc(php_stream_ops *ops, void *abstract,
                      const char *persistent_id, const char *mode);
```

分配一个与标识流 `ops` 关联的 PHP 流实例。此方法通常由流或包装器实现使用；请参阅第 15 章。

| 参数 | 目的 |
| --- | --- |
| `ops` | 包含回调操作列表的结构，用于执行读、写、刷新、关闭和其他操作。 |
| `abstract` | 将任意数据结构附加到流实例上，通常指向底层数据资源。 |
| `persistent_id` | 此流资源的唯一标识符，用于检索持久化流实例。 |
| `mode` | 与此流实例关联的 `fopen` 模式（例如 `r`、`w`、`a`、`r+` 等）。 |

```c
int php_stream_from_persistent_id(const char *persistent_id,
                      php_stream **stream TSRMLS_DC);
```

根据其持久化 ID（如提供给 `php_stream_alloc()` 的）恢复流实例。

```c
int php_stream_free(php_stream *stream, int close_options);
int php_stream_close(php_stream *stream);
int php_stream_pclose(php_stream *stream);
```

关闭流并释放与其关联的资源。`close_options` 可以是以下标志的任意组合。`php_stream_close()` 在调用 `php_stream_free()` 时会将 `close_options` 设置为 `PHP_STREAM_FREE_CLOSE`，而 `php_stream_pclose()` 则将其设置为 `PHP_STREAM_FREE_CLOSE_PERSISTENT`。

| `close_options` 标志 | 说明 |
| --- | --- |
| `PHP_STREAM_FREE_CALL_DTOR` | 调用流的 `ops->close()` 方法 |
| `PHP_STREAM_FREE_RELEASE_STREAM` | 释放为存储流实例分配的内存 |
| `PHP_STREAM_FREE_PRESERVE_HANDLE` | 传递给 `ops->close()` 以指示其不要关闭底层句柄 |
| `PHP_STREAM_FREE_RSRC_DTOR` | 流层内部使用，用于在销毁流关联资源时避免递归 |
| `PHP_STREAM_FREE_PERSISTENT` | 显式关闭一个原本持久化的流实例 |
| `PHP_STREAM_FREE_CLOSE` | `PHP_STREAM_FREE_CALL_DTOR` 和 `PHP_STREAM_FREE_RELEASE_STREAM` 的组合 |
| `PHP_STREAM_FREE_CLOSE_CASTED` | `PHP_STREAM_FREE_CLOSE` 和 `PHP_STREAM_FREE_PRESERVE_HANDLE` 的组合 |
| `PHP_STREAM_FREE_CLOSE_PERSISTENT` | `PHP_STREAM_FREE_CLOSE` 和 `PHP_STREAM_FREE_PERSISTENT` 的组合 |

```c
php_stream_wrapper *php_stream_locate_url_wrapper(const char *path,
                      char **path_for_open, int options TSRMLS_DC);
```

检索与给定 URI 关联的当前注册的包装器结构体。通常 `path_for_open` 将仅填充 `path` 的值；然而，当给定基于文件的 URI 时，开头的 `file://` 方案标识符将被自动删除，以便对底层 `open()` 系统调用能够正常工作。

| 参数 | 目的 |
| --- | --- |
| `path` | 要映射到其包装器结构的资源完整 URI。 |
| `path_for_open` | 填充（可能修改过的）`path` 版本，用于实际的调用。 |
| `options` | 包含零或多个以下选项的位掩标志：`IGNORE_URL`、`STREAM_LOCATE_WRAPPERS_ONLY` 和 `REPORT_ERRORS`。这些标志的解释请参阅第 14 章。 |

```c
php_stream *php_stream_open_wrapper(char *path, char *mode,
                      int options, char **opened_path);
php_stream *php_stream_open_wrapper_ex(char *path, char *mode,
                      int options, char **opened_path,
                      php_stream *context);
FILE *php_stream_open_wrapper_as_file(char *path, char *mode,
                      int options, char **opened_path,
                      php_stream *context);
```

根据给定的 `path` 创建流实例或 stdio 文件。`php_stream_open_wrapper()` 变体与向 `context` 传递 `NULL` 的扩展版本等效。

#### 流 I/O

```c
size_t php_stream_read(php_stream *stream, char *buf, size_t maxlen);
char *php_stream_get_record(php_stream *stream, size_t maxlen,
                      size_t *returned_len, char *delim,
                      size_t delim_len TSRMLS_DC);
char *php_stream_get_line(php_stream *stream, char *buf, size_t maxlen,
                      size_t *returned_len);
char *php_stream_gets(php_stream *stream, char *buf, size_t maxlen);
int php_stream_getc(php_stream *stream);
```

从流实例读取数据。`php_stream_read()` 在不考虑内容的情况下读取原始字节，并仅尝试对底层进行一次读取。这意味着，取决于底层实现的语义，即使有更多数据，返回的字节数也可能少于 `maxlen`。相反，三个行数据检索操作（`get_record`、`get_line` 和 `gets`）会执行贪婪读取，缓存流中的必要数据直到定位行结束序列或填充提供的缓冲区到 `maxlen` 字节。`php_stream_getc()` 将从流中读取单个字节。

| 参数 | 目的 |
| --- | --- |
| `stream` | 要读取的流实例。 |
| `buf` | 用于存储结果的缓冲区。对于返回 `char*` 的方法，如果传递的是 `NULL`，则将使用 `emalloc` 分配一个大小合适的缓冲区。 |
| `maxlen` | 从流中读取的最大字节数。 |
| `delim` | 行结束分隔符。停止从流中读取的序列。不需要结尾的 `NULL` 字节。 |
| `delim_len` | 分隔符字符串的长度，不包括任何可选的结尾 `NULL` 字符。 |
| `returned_len` | 对于其他返回 `char*` 缓冲区的方法返回的字符串长度。 |

```c
size_t php_stream_write(php_stream *stream, const char *buf, size_t count);
size_t php_stream_write_string(php_stream *stream, const char *buf);
int php_stream_puts(php_stream *stream, char *buf);
size_t php_stream_printf(php_stream *stream TSRMLS_DC, const char *fmt, ...);
int php_stream_putc(php_stream *stream, int c);
```

向流实例写入数据。`php_stream_puts()` 与 `php_stream_write()` 的区别在于它在写入 `buf` 内容后额外追加一个换行符。`putc` 和 `puts` 版本在成功时返回 `1`，失败时返回 `0`，其余版本返回实际写入流的字节数，该字节可能少于请求写入的字节数。

| 参数 | 目的 |
| --- | --- |
| `stream` | 要写入数据的流 |
| `buf` | 包含要写入流的数据缓冲区 |
| `count` | `buf` 中包含的数据字节数 |
| `c` | 要写入流的单个字符 |
| `fmt` | `sprintf()` 风格的格式说明符 |
| `...` | 与 `fmt` 格式说明符对应的变参数列表 |

```c
int php_stream_eof(php_stream *stream);
```

如果流的文件指针已到达末尾，则返回非零值。

```c
int php_stream_flush(php_stream *stream, int closing);
```

指示底层流实现将任何内部缓冲的数据刷新到目标资源。

```c
size_t php_stream_copy_to_stream(php_stream *src,
                      php_stream *dest, size_t maxlen);
```

从 `src` 流读取最多 `maxlen` 字节的剩余内容，并将其写入 `dest` 流。

```c
size_t php_stream_copy_to_mem(php_stream *src, char **buffer,
                      size_t maxlen, int persistent);
```

从 `src` 流读取最多 `maxlen` 字节的剩余内容，并将其放入新分配的 `buffer` 中。如果 `persistent` 为非零，则将使用持久内存分配器；否则将为 `buffer` 分配非持久内存。

```c
size_t php_stream_passthru(php_stream *src);
```

从 `src` 流读取剩余内容并将其输出到浏览器、命令行或其他适当目标。

```c
char *php_stream_mmap_range(php_stream *stream, size_t offset,
                      size_t length, php_stream_mmap_operation_t mode,
                      size_t *mapped_len);
int php_stream_mmap_unmap(php_stream *stream TSRMLS_DC);
int php_stream_mmap_supported(php_stream *stream);
int php_stream_mmap_possible(php_stream *stream);
```

将流内容的一部分映射或取消映射到内存。注意，PHP 对内存映射操作施加了 2MB 的人工限制。返回整数的函数失败时返回零或表示负向响应，否则返回非零。`php_stream_mmap_range()` 成功时返回内存映射区域的指针，失败时返回 `NULL`。

| 参数 | 目的 |
| --- | --- |
| `stream` | 要映射的流 |
| `offset` | 从流内容开始映射的偏移量 |
| `length` | 要映射的字节数；使用 `PHP_STREAM_COPY_ALL` 映射所有剩余数据（无论有多少） |
| `mode` | 设置为 `PHP_STREAM_MMAP_MAP_RANGE`；其他值由流层内部使用 |
| `mapped_len` | 填充映射到此方法返回指针的实际映射字节数 |

### 流操作

```c
int php_stream_seek(php_stream *stream, off_t offset, int whence);
int php_stream_rewind(php_stream *stream);
off_t php_stream_tell(php_stream *stream);
```



在可寻址流内移动文件指针（`seek`）或报告其当前位置（`tell`）。`php_stream_rewind()` 是一个便利宏，映射到 `php_stream_seek(stream,0, SEEK_SET);`。

| 参数 | 目的 |
| --- | --- |
| `stream` | 要寻址或报告位置的流 |
| `offset` | 相对于 `whence` 的寻址位置 |
| `whence` | `SEEK_SET`（相对于流的开头）、`SEEK_CUR`（相对于当前位置）或 `SEEK_END`（相对于文件末尾）之一 |

```
int php_stream_stat(php_stream *stream, php_stream_statbuf *ssb);

int php_stream_stat_path(char *path, int flags, php_stream_statbuf *ssb,

                      php_stream_context *context);
```

分别从打开的流或 URI 路径报告 `fstat()` 或 `stat()` 风格的信息。

| 参数 | 目的 |
| --- | --- |
| `stream` | 用于从中检索 `fstat()` 信息的活动流实例。 |
| `path` | 本地或远程文件资源的 URL，用于检索 `stat()` 数据。 |
| `flags` | 如果设置为 `PHP_STREAM_URL_STAT_LINK`，则仅检查 `path` 指向的直接资源。如果未设置此标志，将遵循符号链接到真实资源。 |
| `ssb` | 用于填充文件状态信息的统计缓冲区。 |
| `context` | 尝试定位本地或远程资源时应用的流上下文。 |

```
int php_stream_set_option(php_stream *stream, int option,

                      int value, void *ptrparam);

int php_stream_truncate_set_size(php_stream *stream, size_t newsize);
```

在 PHP 流上执行 `ioctl()` 风格的操作。`php_stream_truncate_set_size()` 是 `php_stream_set_option(stream, PHP_STREAM_OPTION_TRUNCATE_API, PHP_STREAM_TRUNCATE_SET_SIZE, &newsize)` 的便利封装器，它指示底层流实现更改关联文件资源的大小。选项的完整列表是一个独立的话题。参考 `main/streams/plain_wrapper.c` 和 `main/streams/socket.c` 等实现代码以查看这些控制。

```
int php_stream_can_cast(php_stream *stream, int castas);

int php_stream_cast(php_stream *stream, int castas, void **ret, int show_err);
```

将流暴露为更基础的类型，例如文件描述符或流。`castas` 必须是以下之一：`PHP_STREAM_AS_STDIO`、`PHP_STREAM_AS_FD`、`PHP_STREAM_AS_SOCKET` 或 `PHP_STREAM_AS_FD_FOR_SELECT`，可选通过按位或组合 `PHP_STREAM_CAST_RELEASE`，这将使流失效。要在不执行操作的情况下测试流是否可以转换，请调用 `php_stream_can_cast()`。两种方法均返回 `SUCCESS` 或 `FAILURE`。

| 参数 | 目的 |
| --- | --- |
| `stream` | 要转换的流。 |
| `castas` | 类型。 |
| `ret` | 用于存储转换流的局部变量指针。 |
| `show_err` | 如果遇到错误时 `php_errors()`，则设置为非零值。 |

```
int php_stream_make_seekable(php_stream *origstream,

                      php_stream **newstream, int flags);
```

如果 `origstream` 已经是可寻址的且 `flags` 不包含 `PHP_STREAM_FORCE_CONVERSION`，则 `newstream` 将简单赋值为 `origstream` 此方法返回 `PHP_STREAM_UNCHANGED`。否则，将创建一个临时流并将 `origstream` 的剩余内容复制到 `newstream`。注意，调用此方法后，任何从 `origstream` 读取的内容将不再可用。如果方法成功，`origstream` 将关闭且调用返回 `PHP_STREAM_RELEASED`。如果失败，将返回 `PHP_STREAM_FAILURE` 表示无法创建临时流，或返回 `PHP_STREAM_CRITICAL` 表示无法将 `origstream` 内容复制到 `newstream`。注意复制失败可能会导致 `origstream` 的部分或全部丢失。除了 `PHP_STREAM_FORCE_CONVERSION` 之外，`flags` 还可以组合 `PHP_STREAM_PREFER_STDIO`，这将创建一个 STDIO 临时文件而非临时文件描述符。

## 目录访问

```
int php_stream_mkdir(char *path, int mode, int options,

                      php_stream_context *context);

int php_stream_rmdir(char *path, int options,

                      php_stream_context *context);
```

创建一个新目录或删除一个目录。创建或删除目录的标准和方法取决于具体的封装器（wrapper）；然而，所有实现 `mkdir()` 方法的封装器都应该遵守 `PHP_STREAM_MKDIR_RECURSIVE` 选项。请注意，`php_stream_rmdir()` 实际上没有定义任何 `options` 标志。该参数存在完全是为了向后兼容。

| 参数 | 目的 |
| --- | --- |
| `path` | 描述要创建或删除目录的 URI。 |
| `mode` | 应用到新创建目录的 POSIX 访问模式。 |
| `options` | `Bitmask` 标志参数，当前有一个选项：`PHP_STREAM_MKDIR_RECURSIVE`，它仅适用于这些方法的 `mkdir()` 变体。使用时，给定 `path` 所需的任何不存在的父目录将被隐式创建。 |
| `context` | 应用于封装器执行的流上下文。 |

```
php_stream *php_stream_opendir(char *path, int options,

                      php_stream_context *context);

php_stream_dirent *php_stream_readdir(php_stream *stream,

                      php_stream_dirent *ent);

int php_stream_rewinddir(php_stream *stream);

int php_stream_close(php_stream *stream);
```

打开、迭代读取目录项并关闭目录资源。目录项以等大小的块为增量进行读取。可以通过 `ent->d_name` 访问目录项的内容。

| 参数 | 目的 |
| --- | --- |
| `path` | 指向要检查目录的 URI。 |
| `options` | 在流创建期间传递的可选参数。请参阅第 14 章获取这些选项的列表及其作用。 |
| `context` | 在打开此目录资源时应用的流上下文。 |
| `stream` | 用于读取、重置或关闭的活动目录流实例。 |
| `ent` | 目录项缓冲区，将填充下一个目录项名称。 |

```
int php_stream_scandir(char *path, char **namelist[],

                      php_stream_context *context,

                      int (*compare) (const char **a, const char **b));

int php_stream_dirent_alphasort(const char **a, const char **b);

int php_stream_dirent_alphasortr(const char **a, const char **b);
```

`php_stream_scandir()` 将给定目录内的所有项读取到 `char*` 字符串向量中。如果提供了 `compare` 函数（如所示的 `alphasort` 方法之一），这些项将在读取后进行排序。`namelist` 向量和每个单独项的空间将由 `php_stream_scandir()` 方法使用非持久性存储自动分配，并在使用后必须手动释放。例如，包含 10 个项的 `namelist` 将有 11 处不同的分配：一个用于向量本身，另一个用于单独的字符串。

| 参数 | 目的 |
| --- | --- |
| `path` | 指向要扫描目录的 URI。 |
| `namelist` | 作为本地 `char**` 存储的指针传递。这将由 `scandir` 方法通过引用修改。 |
| `context` | 扫描目录时使用的流上下文。 |
| `compare` | 用于排序的比较函数。可以是之前给出的 `alphasort` 方法之一，也可以任何接受两个元素作为输入并返回 -1、0 或 1（分别表示小于、等于或大于）的回调函数。 |

## 用户态转换

```
int php_file_le_stream(void);

int php_stream_p(void);

int php_file_le_filter(void);

int php_le_stream_context(void);
```

返回标准流、持久流和上下文的列表项类型。这些值对应于 `zend_register_list_destructors()` 分配的值，并用于如 `php_stream_from_zval()` 等辅助宏。

```
void php_stream_to_zval(php_stream *stream, zval *zstream);

void php_stream_from_zval(php_stream *stream, zval *zstream);

void php_stream_from_zval_no_verify(php_stream *stream, zval *zstream);
```

这些辅助宏将分配的流编码为用户态 `zval`，或将其解码回。请注意这些是宏而不是普通函数，因此传递给 `php_stream_from_zval()` 的 `stream` 变量会被原地修改。注意在存储值时，流层会显式分离（复制）`zval`，从而脱离其调用作用域的所有权。请参阅第 9 章“资源类型”获取更多信息。

## 上下文

```
php_stream_context *php_stream_context_alloc(void);

void php_stream_context_free(void);
```

分配或释放流上下文。请参阅第 16 章“流”获取关于使用上下文的完整说明。由于大多数上下文选项在流打开时生效，因此此操作与在流创建方法时指定上下文相比，影响通常要小得多。

```
int php_stream_context_set_option(php_stream_context *context, const char *wrappername, zval *optionvalue);

int php_stream_context_get_option(php_stream_context *context, const char *wrappername, zval ***optionvalue);
```

设置或检索上下文选项。上下文选项存储在 `zval*` 的二维数组中。封装器的名称定义第一个维度，而封装器特定的选项名称定义第二个。具有双重职责的封装器（如 `http`）通常使用一个名称来存储其选项。

| 参数 | 目的 |
| --- | --- |
| `context` | 设置或检索选项的容器。 |
| `wrappername` | 此选项适用于封装器名称。 |
| `optionname` | 要获取或设置的封装器特定选项名称。 |
| `optionvalue` | 根据调用的特定方法，用于存储的 `zval*` 值，或用于获取存储值的 `zval**` 变量指针。 |

```
php_stream_context_set(php_stream *stream, php_stream_context *context);
```

将 `context` 与已激活的 `stream` 实例关联。

### 通知器

```
php_stream_notifier *php_stream_notification_alloc(void);

void php_stream_notification_free(php_stream_notifier *notifier);

void php_stream_notification_notify(php_stream_context *context, int notifycode, int severity, char *xmsg, int xcode, size_t bytes_sofar, size_t bytes_max, void * ptr TSRMLS_DC);
```

请参阅第 16 章获取关于这些方法的详情。

### 过滤器

```
php_stream_filter *php_stream_filter_create(const char *filtername, zval *filterparams, int persistent TSRMLS_DC);
```

使用提供的过滤器特定参数实例化过滤器。当实例化放置在持久流上的过滤器对象时，必须设置 `persistent` 标志。这通常可以通过使用 `php_stream_is_persistent()` 方法来实现。

| 参数 | 目的 |
| --- | --- |
| `filtername` | 要实例化的过滤器的名称。 |
| `filterparams` | 过滤器特定参数的可选 `zval*`。请参阅被实例化的过滤器的文档以了解接受的类型和值。 |
| `persistent` | 二进制标志，表示过滤器是否将放置在持久化流上。 |

```php
php_stream_filter *php_stream_filter_alloc(php_stream_filter_ops *fops,

                      void *abstract, int persistent);

void php_stream_filter_free(php_stream_filter *filter TSRMLS_DC);
```

分配或释放过滤器结构体。`php_stream_filter_alloc()` 通常由过滤器实现在实例化期间调用。释放方法会自动调用过滤器的 `dtor` 方法来以清理任何内部资源。

| 参数 | 目的 |
| --- | --- |
| `fops` | 过滤器操作结构体，包含与此过滤器实例一起使用的回调函数。 |
| `abstract` | 与过滤器实例关联的任意数据指针。 |
| `persistent` | 标志，表示过滤器是否将放置在持久化流上。 |

```php
void php_stream_filter_prepend(php_stream_filter_chain *chain,

                      php_stream_filter *filter);

void php_stream_filter_append(php_stream_filter_chain *chain,

                      php_stream_filter *filter);

int php_stream_filter_flush(php_stream_filter *filter, int finish);

php_stream_filter *php_stream_filter_remove(php_stream_filter *filter,

                      int call_free TSRMLS_DC);
```



将过滤器添加到流过滤器栈的开头或末尾，刷新其内部缓冲区，或从活动流中移除过滤器。通常在移除过滤器之前会对其进行刷新，以便内部缓冲的数据可以根据需要传递给后续过滤器或读缓冲区/写操作。

| 参数 | 目的 |
| --- | --- |
| `chain` | 要将命名为 `filter` 的过滤器添加进去的过滤器链。通常是 `stream->readfilters` 或 `stream->writefilters` 之一。 |
| `filter` | 要添加、刷新或移除的过滤器实例。 |
| `finish` | 当设置为非零值时，指示过滤器尽可能从其内部缓冲区中刷新所有数据。否则，过滤器可以选择只刷新当前数据块，而为下一次循环保留部分数据。 |
| `call_free` | 在从流的过滤器链中移除过滤器后，自动调用 `php_stream_filter_free()`。 |

```php
int php_stream_filter_register_factory(const char *filterpattern,
                      php_stream_filter_factory *factory TSRMLS_DC);

int php_stream_filter_unregister_factory(
                      const char *filterpattern TSRMLS_DC);

int php_stream_filter_register_factory_volatile(const char *filterpattern,
                      php_stream_filter_factory *factory TSRMLS_DC);

int php_stream_filter_unregister_factory_volatile(
                      const char *filterpattern TSRMLS_DC);
```

注册或注销流过滤器。这些方法的 `volatile` 变体允许包装器在单个请求生命周期内覆盖，而非 volatile 版本处理永久注册和注销。与包装器一样，临时过滤器应仅在请求阶段 `ACTIVATE`、`RUNTIME`、`DEACTIVATE` 中注册和注销；同样，永久过滤器应仅在 `STARTUP` 和 `SHUTDOWN` 阶段注册和注销。

## 桶 (Buckets)

```php
php_stream_bucket *php_stream_bucket_new(php_stream *stream,
                      char *buf, size_t buflen, int own_buf,
                      int buf_persistent TSRMLS_DC);
```

实例化一个放置在过滤器队列中的桶对象。有关在自定义过滤器实现中使用桶，请参考第 16 章。

| 参数 | 目的 |
| --- | --- |
| `stream` | 此桶最终将关联的流引用。 |
| `buf` | 分配给此桶的数据缓冲区。 |
| `buflen` | `buf` 的长度（字节）。 |
| `own_buf` | 如果 `buf` 可以被其他过滤器或流层安全修改或释放，则设置为非零值。如果此项和 `buf_persistent` 都设置为 0 且目标流不是持久的，则将自动复制 `buf` 以便桶拥有它。 |
| `buf_persistent` | 标志，表示过滤器是否将放置在持久化流上。 |

| `length` | `buf` 的字节数（bytes）。 |

```php
char *expand_filepath(const char *filepath, char *real_path TSRMLS_DC);
```

将提供的 `filepath` 中的符号链接和父级引用解析为真实目标。此方法提供了标准 `realpath()` 方法的线程安全替代方案。

## 传输 (Transports)

```php
php_stream *php_stream_xport_create(const char *name, long namelen,
                      int options, int flags, const char *persistent_id,
                      struct timeval *timeout, php_stream_context *context,
                      char **error_string, int *error_code);
```

实例化套接字传输流。根据传递的 `flags`，可以是客户端或服务器套接字，并且可能不会立即连接或开始监听。

| 参数 | 目的 |
| --- | --- |
| `name` | 传输 URI。如果没有提供协议指定符，为了兼容用户态的 `fsockopen()` 命令，假设为 `tcp://`。 |
| `namelen` | `name` 参数的长度，不包括其末尾的 `NULL`。 |
| `options` | 与 `php_stream_open_wrapper()` 使用相同的 options 参数。 |
| `flags` | `STREAM_XPORT` 标志的按位或组合。 |
| `persistent_id` | 与此传输关联的持久性 ID。如果可用且套接字仍然活跃，则将重用现有流而不是打开新的。 |
| `timeout` | 执行同步连接时阻塞的最大时间。 |
| `context` | 可选的流上下文（context）。 |
| `error_string` | 如果发生错误，将填充描述性错误信息。 |
| `error_code` | 如果发生错误，将填充数值错误代码。 |

`flags` 参数可以由 `STREAM_XPORT_CLIENT` 或 `STREAM_XPORT_SERVER` 组成。客户端传输可以选择可选指定 `STREAM_XPORT_CONNECT` 或 `STREAM_XPORT_CONNECT_ASYNC`。服务器传输可以指定 `STREAM_XPORT_BIND` 和 `STREAM_XPORT_LISTEN`。

| 标志 | 含义 |
| --- | --- |
| `STREAM_XPORT_CLIENT` | 创建客户端风格的传输。 |
| `STREAM_XPORT_SERVER` | 创建服务器风格的传输。 |
| `STREAM_XPORT_CONNECT` | 使用阻塞（同步）调用立即连接到指定的资源。 |
| `STREAM_XPORT_BIND` | 绑定到指定的本地资源。 |
| `STREAM_XPORT_LISTEN` | 在传输套接字上监听入站连接。通常需要包含 `STREAM_XPORT_BIND`。默认情况下，将队列五个连接的积压（backlog）。 |
| `STREAM_XPORT_CONNECT_ASYNC` | 开始异步连接到指定的资源。 |

```php
int php_stream_xport_connect(php_stream *stream, const char *name, long namelen,
                      int asynchronous, struct timeval *timeout,
                      char **error_text, int *error_code TSRMLS_DC);
```

将传输流连接到指定的资源。

| 参数 | 目的 |
| --- | --- |
| `stream` | 连接到指定资源的传输流 |
| `name` | 要连接的特定传输协议资源 |
| `namelen` | 资源指定符的长度 |
| `asynchronous` | 设置为非零以异步连接 |
| `timeout` | 等待成功连接的最大长度 |
| `error_text` | 失败时填充描述性错误消息 |
| `error_code` | 填充数值错误代码 |

```php
int php_stream_xport_bind(php_stream *stream, const char *name, long namelen,
                      char **error_text TSRMLS_DC);
```

将已建立的流绑定到本地资源。这可以用于绑定服务器套接字或在连接之前对客户端进行源绑定。

| 参数 | 目的 |
| --- | --- |
| `stream` | 绑定到本地资源的传输流 |
| `name` | 说明要绑定的本地资源的字符串 |
| `namelen` | `name` 的长度，不包括其末尾的 `NULL` 字节 |
| `error_test` | 如果绑定失败，填充文本错误消息 |

```php
int php_stream_xport_listen(php_stream *stream, int backlog,
                      char **error_text TSRMLS_DC);
```

开始在之前绑定的传输套接字上监听。

| 参数 | 含义 |
| --- | --- |
| `stream` | 绑定到本地资源的传输流 |
| `backlog` | 在拒绝额外的连接尝试之前要队列的未接受连接数 |
| `error_test` | 如果绑定失败，填充文本错误消息 |

```php
int php_stream_xport_accept(php_stream *stream, php_stream **client,
                      char **textaddr, int *textaddrlen,
                      void **addr, socklen_t *addrlen,
                      struct timeval *time_out, char **error_text TSRMLS_DC);
```

在之前指示监听的传输套接字上接受队列中的连接。如果目前没有连接在队列中，此方法将阻塞 `time_out` 指定的时间段。

| 参数 | 目的 |
| --- | --- |
| `stream` | 之前绑定并监听的服务器传输。将从该积压中接受连接。 |
| `client` | 新创建的传输流。 |
| `textaddr` | 填充 `addr` 的文本表示。 |
| `textaddrlen` | 填充 `textaddr` 的长度。 |
| `addr` | 填充特定传输的地址。 |
| `addrlen` | 填充 `addr` 的长度。 |
| `time_out` | 等待入站连接的最大长度。 |
| `error_text` | 如果发生错误，填充文本错误消息。 |

```php
int php_stream_xport_get_name(php_stream *stream, int want_peer,
                      char **textaddr, int *textaddrlen,
                      void **addr, socklen_t *addrlen);
```

探测本地或远程端点（套接字）名称。

| 参数 | 目的 |
| --- | --- |
| `stream` | 连接的传输流 |
| `want_peer` | 设置为非零以检索远程端点信息 |
| `textaddr` | 填充地址的文本表示 |
| `textaddrlen` | 填充 `textaddr` 的长度 |
| `addr` | 填充特定传输地址信息 |
| `addrlen` | 填充 `addr` 的长度 |

```php
int php_stream_xport_sendto(php_stream *stream, const char *buf, size_t buflen,
                      long flags, void *addr, socklen_t addrlen);

int php_stream_xport_recvfrom(php_stream *stream, char *buf, size_t buflen,
                      long flags, void **addr, socklen_t *addrlen,
                      char **textaddr, int *textaddrlen TSRMLS_DC);
```

无连接的发送和接收方法。

| 参数 | 含义 |
| --- | --- |
| `stream` | 用于发送或接收的传输流。 |
| `buf` | 要发送的数据或填充接收数据的缓冲区。 |
| `buflen` | 发送的数据长度或接收数据的缓冲区长度。 |
| `flags` | 可以设置为 `STREAM_OOB` 以发送或接收带外数据。接收时，也可以设置或结合 `STREAM_PEEK` 来检查数据而不消耗它。 |
| `addr` | 发送时：要发送的特定传输地址记录。接收时：填充特定传输源地址记录。 |
| `addrlen` | `addr` 的字节长度。 |
| `textaddr` | 填充源地址的文本表示。 |
| `textaddrlen` | 填充 `textaddr` 的长度。 |

在指定的传输流上设置并激活/停用加密。在实践中，仅实现了 `SSL/TLS` 加密方法，且这些方法通常仅与 `TCP` 传输配合使用。

| 参数 | 目的 |
| --- | --- |
| `stream` | 要设置加密的传输流。 |
| `crypto_method` | 以下之一：`STREAM_CRYPTO_METHOD_SSLv2_CLIENT`, `STREAM_CRYPTO_METHOD_SSLv3_CLIENT`, `STREAM_CRYPTO_METHOD_SSLv23_CLIENT`, `STREAM_CRYPTO_METHOD_TLS_CLIENT`, `STREAM_CRYPTO_METHOD_SSLv2_SERVER`, `STREAM_CRYPTO_METHOD_SSLv3_SERVER`, `STREAM_CRYPTO_METHOD_SSLv23_SERVER` 或 `STREAM_CRYPTO_METHOD_TLS_SERVER`。 |
| `session_stream` | 如果提供，新的加密设置将从之前已启用加密的传输流继承会话参数。 |
| `activate` | 设置非零值时，将启用加密层；设置为零时，将将其关闭。 |

```php
int php_stream_xport_register(char *protocol,
                      php_stream_transport_factory factory TSRMLS_DC);

typedef php_stream *(*php_stream_transport_factory)(
                      const char *proto, long protolen,
                      char *resourcename, long resourcenamelen,
                      const char *persistent_id, int options, int flags,
                      struct timeval *timeout, php_stream_context *context
                      STREAMS_DC TSRMLS_DC);

int php_stream_xport_unregister(char *protocol TSRMLS_DC);
```

注册或注销流传输工厂。传输工厂方法遵循与流协议包装器打开函数相同的模式。请参阅第 15 章获取流创建方法的概述。

| 参数 | 目的 |
| --- | --- |
| `protocol` | 要注册或注销的协议名称。 |
| `factory` | 当实例化指定协议的传输层时被调用的工厂方法。 |
| `proto` | 正在实例化的传输协议名称。 |
| `protolen` | `proto` 的长度。 |
| `resourcename` | 指向要连接资源的特定 URI。 |
| `resourcenamelen` | `resourcename` 的长度。 |
| `persistent_id` | 与实例化的传输流相关的持久 ID。 |
| `options` | 传递给 `php_stream_xport_create()` 的选项值。 |
| `flags` | 传递给 `php_stream_xport_create()` 的标志值。 |
| `timeout` | 传输的默认超时值。 |
| `context` | 与流关联的可选上下文参数。 |

```php
HashTable *php_stream_xport_get_hash(void);
```

返回指向内部传输注册哈希表的指针。

```php
int php_network_parse_network_address_with_port(const char *addr, long addrlen,
                      struct sockaddr *sa, socklen_t *sl TSRMLS_DC);
```

将 `inet` 族传输 URI 解析为其组成部分。如果 URI 的主机部分是主机名，它将自动解析为其 IP 地址。适当的族、地址和端口数据将加载到 `sa` 结构中，其最终大小将填充到 `sl`。

## 杂记



`int php_register_url_stream_wrapper(char *protocol, php_stream_wrapper *wrapper TSRMLS_DC);`

`int php_unregister_url_stream_wrapper(char *protocol TSRMLS_DC);`

`int php_register_url_stream_wrapper_volatile(char *protocol, php_stream_wrapper *wrapper TSRMLS_DC);`

`int php_unregister_url_stream_wrapper(char *protocol TSRMLS_DC);`

注册或注销 URL 流包装器。注册变性的 URL 流包装器。注册或注销 URL 流包装器的变性方法必须是之前已启用加密的传输流的。变性的 URL 流包装器在 `STARTUP`、`RUNTIME` 和 `SHUTDOWN` 阶段被注册；相反，非变性的 URL 流包装器在 `ACTIVATE` 阶段被注销。请参阅第 15 章 ](ch15.html#ch15) 获取更多信息。

```
int php_register_url_stream_wrapper(char *protocol,
                      php_stream_wrapper *wrapper TSRMLS_DC);
```

注册性的 URL 流包装器。

```
int php_copy_file(char *src, char *dest TSRMLS_DC);
```

将 `src` 的内容复制到 `dest`。此方法是用户空间 `copy()` 用的底层内部实现。

## `ext/standard/flock_compat.h`

```
int php_flock(int fd, int operation);
```

在已打开的描述符上创建或清除文件锁。`operation` 可以恰好是下面列出的模式之一；可选地通过按位或操作与 `LOCK_NB` 组合，以防止在文件锁期间发生阻塞。

| 操作 | 含义 |
| --- | --- |
| `LOCK_SH` | 共享锁，允许互斥读访问 |
| `LOCK_EX` | 独占锁，防止其他进程访问 |
| `LOCK_UN` | 停止阻塞 |

## `ext/standard/head.h`

```
int php_setcookie(char *name, int name_len, char *value, int value_len,
                      time_t expires, char *path, int path_len,
                      char *domain, int domain_len, int secure,
                      int url_encode TSRMLS_DC);
```

发送 cookie。此方法是用户空间 `set_cookie()` 函数的内部实现。`value` 可以传递为 `NULL` 以发送清除 cookie 的请求。`path` 和/或 `domain` 可以传递为 `NULL` 以防止在生成的 cookie 头部中使用它们。

| 参数 | 用途 |
| --- | --- |
| `name` | `NULL` 终止的 cookie 名称。 |
| `name_len` | `name` 的长度，不包括结尾的 `NULL`。 |
| `value` | 要设置 cookie 的 `NULL` 终止的内容。 |
| `value_len` | `value` 的长度，不包括结尾的 `NULL`。 |
| `expires` | cookie 过期的 UNIX 时间戳值。 |
| `path` | 如果提供，浏览器将被指示仅在请求指定路径下的页面时提供 cookie。 |
| `path_len` | `path` 的长度，不包括结尾的 `NULL`。 |
| `domain` | 如果提供，浏览器将被指示仅为指定的主机名或子域名提供 cookie；受 HTTP 协议定义的域名安全限制。 |
| `domain_len` | `domain` 的长度，不包括结尾的 `NULL`。 |
| `secure` | 设置为非零值时，浏览器将被指示仅在通过安全连接 (https) 执行请求时发送 cookie 数据。 |
| `url_encode` | 设置为非零值时，`value` 的内容在发送到浏览器之前将自动自动进行 URL 编码。 |

## `ext/standard/html.h`

```
char *php_escape_html_entities(unsigned char *old, int oldlen, int *newlen,
                      int all, int quote_style, char *hint_charset TSRMLS_DC);

char *php_unescape_html_entities(unsigned char *old, int oldlen, int *newlen,
                      int all, int quote_style, char *hint_charset TSRMLS_DC);
```

通过将某些字符插值为 HTML 实体反反之来转换输入字符串。PHP 将尝试确定合适的字符集；可以在最后一个参数中提供提示。

| 参数 | 用途 |
| --- | --- |
| `old` | 要转换的源字符串。 |
| `oldlen` | 源字符串的长度。 |
| `newlen` | 新分配的 `NULL` 终止字符串的长度，不包括结尾的 `NULL`。 |
| `all` | 设置为非零值时，转换字符集特定的实体以及通用的 HTML 实体。 |
| `quote_style` | 之一：`ENT_NOQUOTE` 避免转换引号类型实体，`ENT_QUOTES` 强制转换引号实体，或 `ENT_COMPAT` 仅转换双引号但保留单引号。 |
| `hint_charset` | 在转换 `all` 实体时，假设源或目标文本编码的字符集。 |

## `ext/standard/info.h`

```
void php_print_info(int flag TSRMLS_DC);
```

输出 PHP 核心、Zend 引擎和/或扩展信息。此方法是用户空间 `phpinfo()` 函数的内部实现。`flag` 可以是以下任何常量按位或组合的组合，或简单的 `PHP_INFO_ALL` 以显示所有内容。

| 常量 | 含义 |
| --- | --- |
| `PHP_INFO_GENERAL` | 序言，包括 API 版本号、`./configure` 行、注册的流组件和 Zend 归属 |
| `PHP_INFO_CREDITS` | 著名的 PHP 引擎、核心和扩展开发者的列表 |
| `PHP_INFO_CONFIGURATION` | 显示核心 `php.ini` 设置的当前和全局值 |
| `PHP_INFO_MODULES` | 显示所有加载模块的 `MINFO` 部分 |
| `PHP_INFO_ENVIRONMENT` | 打印环境变量 |
| `PHP_INFO_VARIABLES` | 打印变量 |
| `PHP_INFO_LICENSE` | 显示许可信息 |

```
void php_print_info_htmlhead(TSRMLS_D);
void php_info_print_style(TSRMLS_D);
```

PHP 核心、Zend 引擎和/或扩展信息。

| `FS_IS_X` | `IS_BOOL`，如果文件可执行，则为真。 |
| `FS_IS_FILE` | `IS_BOOL`，如果 `filename` 是普通文件则为真。 |
| `FS_IS_DIR` | `IS_BOOL`，如果 `filename` 是目录则为真。 |
| `FS_IS_LINK` | `IS_BOOL`，如果 `filename` 是符号链接则为真。 |
| `FS_EXISTS` | `IS_BOOL`，如果 `filename` 在文件系统中存在则为真。 |
| `FS_LSTAT` | `IS_ARRAY`，上述每个元素均从直接资源中读取（不跟随符号链接）。还包括远程设备号、块大小和块计数（如果可用）。 |
| `FS_STAT` | `IS_ARRAY`，与 `FS_LSTAT` 相同，不同之处在于跟踪所有的符号链接直到到达终止资源。 |

### `ext/standard/php_http.h`

```
int php_url_encode_hash_ex(HashTable *ht, smart_str *formstr,
                      const char *num_prefix, int num_prefix_len,
                      const char *key_prefix, int key_prefix_len,
                      const char *key_suffix, int key_suffix_len,
                      zval *type, char *arg_sep TSRMLS_DC);
```

将数组的内容转换为 URL 编码字符串。该方法是用户态函数 `http_build_query()` 的内部实现。该函数的大多数参数由函数本身用于处理嵌套数组时进行递归调用。

| 参数 | 目的 |
| --- | --- |
| `ht` | 要转换为 URL 编码字符串的 `HashTable`。 |
| `formstr` | 空的智能字符串对象，用于追加 `ht` 的元素。 |
| `num_prefix` | 可选字符串，用于在数字索引条目前添加，以形成有效的变量名。 |
| `num_prefix_len` | `num_prefix` 的长度。 |
| `key_prefix` | 内部使用的变量包装器前缀。通常在初始调用时传递 `NULL`。 |
| `key_prefix_len` | `key_prefix` 的长度。 |
| `key_suffix` | 内部使用的变量包装器后缀。通常在初始调用时传递 `NULL`。 |
| `key_suffix_len` | `key_suffix` 的长度。 |
| `type` | 如果 `ht` 来源于对象的属性表，则应在此处传递对象的 `zval*` 以处理私有和保护属性的访问检查。 |
| `arg_sep` | 分隔多个 `HashTable` 元素时使用的分隔符。如果传递 `NULL`，则使用 `php.ini` 中的值 `arg_separator.output`。 |

### `ext/standard/php_mail.h`

```
int php_mail(char *to, char *subject, char *message, char *headers,
                      char *extra_cmd TSRMLS_DC);
```

发送电子邮件。该方法是用户态函数 `mail()` 的内部实现。

| 参数 | 目的 |
| --- | --- |
| `to` | 收件者电子邮件地址。多个电子邮件地址可以用以逗号分隔的列表组合。 |
| `subject` | 邮件主题行。 |
| `message` | 消息主体。 |
| `headers` | 发送此邮件时使用的额外标头。 |
| `extra_cmd` | 传递给由 `php.ini` 设置 `sendmail_path` 指定的 sendmail 兼容包装器的可选参数。 |

### `ext/standard/php_math.h`

```
char *_php_math_number_format(double num, int dec, char dec_point,
                      char thousand_sep);
```

根据与用户态函数 `number_format()` 相同的规则格式化浮点数。

| 参数 | 目的 |
| --- | --- |
| `num` | 要格式化的数字 |
| `dec` | 小数点保留的位数 |
| `dec_point` | 用于小数点分隔符的字符 |
| `thousand_sep` | 用于千分位分隔符的字符 |

### `ext/standard/php_rand.h`

```
void php_srand(long seed TSRMLS_DC);
void php_mt_srand(php_uint32 seed TSRMLS_DC);
```

为 `system` 或 `Mersenne-Twister` 随机数生成器设置。`seed` 值本身应具有某种程度的不确定性，并可以使用内置宏 `GENERATE_SEED()` 生成。

```
long php_rand(TSRMLS_D);
php_uint32 php_mt_rand(TSRMLS_D);
```

使用 `system` 或 `Mersenne-Twister` 随机数生成器生成随机数。

### `ext/standard/php_string.h`

```
char *php_strtoupper(char *s, size_t len);
char *php_strtolower(char *s, size_t len);
```

将提供的字符串转换为大写或小写。注意，这些方法直接修改提供的字符串，而不分配新的存储空间。

```
char *php_addslashes(char *str, int length, int *new_length,
                      int freeit TSRMLS_DC);
char *php_addslashes_ex(char *str, int length, int *new_length,
                      int freeit TSRMLS_DC);
```

向单引号、双引号添加反斜杠，除非启用了 `magic_quotes_gpc`。与 `addslashes()` 不同，该方法直接修改 `str` 的值。

```
void php_stripslashes(char *str, int length);
```

反转 `php_addslashes()` 的效果。与 `addslashes()` 不同，该方法直接修改 `str` 的值。

```
char *php_cslashes(char *str, int length, int *new_length,
                      int freeit TSRMLS_DC);
```

类似于 `addslashes()` 和 `stripslashes()`，但这些版本将转义 `what` 中列出的字符。控制字符（值小于 32）将被替换为常用序列（如 `\r`、`\n`、`\t`），扩展 ASCII 值（大于 127）将被编码为八进制值。

| 参数 | 目的 |
| --- | --- |
| `str` | 要转义或取消转义的字符串。 |
| `length` | `str` 的长度。 |
| `new_length` | 填充转义后的新长度。 |
| `freeit` | 设置为非零值时，在返回前会自动释放 `str`。 |
| `what` | 要转义的字符列表。 |
| `wlength` | 字符列表的长度。 |

```
char *php_str_to_str(char *haystack, int keystack_len,
                      char *needle, int needle_len,
                      char *str, int str_len, int *new_length);
char *php_str_to_str_ex(char *haystack, int keystack_len,
                      char *needle, int needle_len,
                      char *str, int str_len, int *new_length,
                      int case_sensitivity, int *replace_count);
```

将 `haystack` 中所有的 `needle` 替换为 `str`。该方法的非 ex 版本默认执行区分敏感的搜索和替换。返回新分配的非持久性字符串。

```
int php_char_to_str(char *haystack, uint haystack_len,
                      char needle,
                      char *str, int str_len, zval *result);
int php_char_to_str_ex(char *haystack, uint heystack_len,
                      char needle,
                      char *str, int str_len, zval *result,
                      int case_sensitivity, int *replace_count);
```

这些方法与 `php_str_to_str()` 对应的方法相同，它们将单个字符 `needle` 替换为替换字符串，并将结果放入预分配的 `zval*` 容器中。



`char *php_strtr(char *str, int len, char *str_from, char *str_to, int trlen);`

在原地修改 `str`（不进行复制），将 `str` 中出现的任何 `str_from` 中的字符替换为其在 `str_to` 中对应的索引。这是用户态函数 `strtr()` 的内部实现。

| 参数 | 目的 |
| --- | --- |
| `str` | 需要修改的字符串。 |
| `len` | `str` 的长度。 |
| `str_from` | 用于在 `str` 中搜索的字符列表。 |
| `str_to` | 用于替换到 `str` 中的对索引字符列表。 |
| `TRlen` | `str_from` 和 `str_to` 的长度。注意这两个字符串的长度必须相同。 |

`char *php_trim(char *str, int len, char *what, int what_len, zval *return_value, int mode TSRMLS_DC);`

从字符串的开头或结尾修剪空格或其他无关字符。`what` 参数包含的任何字符都可以用于此操作修剪。如果为 `what` 传递 `NULL`，则使用默认字符集（空格、换行、回车、制表符或垂直制表符）。

| 参数 | 目的 |
| --- | --- |
| `str` | 需要修剪的字符串。 |
| `len` | 需要修剪的字符串的长度。 |
| `what` | 要修剪的字符列表，或传递 `NULL` 使用默认字符列表。 |
| `what_len` | `what` 的长度。 |
| `return_value` | 如果为 `NULL`，结果将被复制并由函数返回。如果传递 `zval` 指针，则该结构将使用结果字符串填充为 `IS_STRING` 变量，并改为返回空字符串。 |
| `mode` | 取以下值之一：`1`（修剪字符串开头）、`2`（修剪字符串结尾）或 `3`（修剪两端）。 |

`size_t php_strip_tags(char *buf, int len, int *state, char *allow, int allow_len);`

从提供的字符串中移除 HTML 和 PHP 标签。注意 `buf` 是原地修改的。通过在调用之间维护状态值，可以分阶段剥离要修改的字符串。参考用户态函数 `fgetss()` 的实现以获取该指针使用的示例。

| 参数 | 目的 |
| --- | --- |
| `buf` | 用于处理禁用标签的字符串 |
| `len` | `buf` 的长度 |
| `state` | 在调用之间填充的标签标签解析器内部状态的状态值 |
| `allow` | 允许的标签列表，遵循用户态 `strip_tags()` 函数使用的惯例 |
| `allow_len` | `allow` 的长度 |

`size_t php_strspn(char *s1, char *s2, char *s1_end, char *s2_end);`
`size_t php_strcspn(char *s1, char *s2, char *s1_end, char *s2_end);`

`php_strspn()` 定位 `s1` 中第一个包含在 `s2` 中找到字符的段。返回在该序列中找到的 `s2` 字符数量。`php_strcspn()` 执行相反的任务，在 `s1` 中定位第一个不包含 `s2` 所定义类中字符的段。这些方法分别是用户态 `strspn()` 函数和 `strcspn()` 函数的内部实现。

| 参数 | 目的 |
| --- | --- |
| `s1` | 搜索字符串的起始位置 |
| `s2` | 定义字符类的字符串起始位置 |
| `s1_end` | 搜索字符串的结束位置 |
| `s2_end` | 定义字符类的字符串结束位置 |

`void php_implode(zval *delim, zval *arr, zval *return_value);`
`void php_explode(zval *delim, zval *str, zval *return_value, int limit);`

将数组合并为由分隔符分隔的字符串，或将分隔符字符串分解为数组。注意 `arr` 的类型必须是 `IS_ARRAY`，且 `str` 的类型必须是 `IS_STRING`。无论输入类型如何，`delim` 都将自动类型转换为字符串值。

| 参数 | 目的 |
| --- | --- |
| `delim` | 应用的分隔字符串 |
| `arr` | 要合并的 `IS_ARRAY` 变量 |
| `str` | 要分解的 `IS_STRING` 变量 |
| `return_value` | 根据情况填充 `IS_STRING` 或 `IS_ARRAY` 变量 |
| `limit` | 从输入字符串中提取的数组元素最大数量 |

`char *php_stristr(unsigned char *haystack, unsigned char *needle, size_t haystack_len, size_t needle_len);`

系统调用 `strstr()` 的不区分大小写的对应版本。

| 参数 | 目的 |
| --- | --- |
| `haystack` | 搜索 `needle` 的字符串 |
| `needle` | 在 `haystack` 中搜索的字符串 |
| `haystack_len` | `haystack` 的长度 |
| `needle_len` | `needle` 的长度 |

`void php_basename(char *str, size_t len, char *sfx, size_t sfx_len, char **ret, size_t *ret_len TSRMLS_DC);`
`size_t php_dirname(char *str, size_t len);`

将 `basename`（路径文件名）从 `dirname`（目录路径）中分离出来。`php_basename()` 将基本文件名复制到新存储中；相反，`php_dirname()` 返回目录路径的长度。

`int strnatcmp_ex(char const *a, size_t a_len, char const *b, size_t b_len, int fold_case);`

执行“自然”字符串比较。自然比较与 `strcmp()` 式的区别在于忽略领先空格并根据整数值而非 ASCII 值排序。

| 参数 | 目的 |
| --- | --- |
| `a` | 两个字符串之一 |
| `a_len` | `a` 的长度 |
| `b` | 两个字符串的另一个 |
| `b_len` | `b` 的长度 |
| `fold_case` | 设置为非零时，将以不区分大小写的方式比较。 |

#### `ext/standard/php_smart_str.h`

```c
typedef struct {
    char *c;
    size_t len;
    size_t a;
} smart_str;
```

智能字符串随着内容的添加动态增长。初始化一个新的智能字符串只需将其字符串成员 (`c`) 设置为 `NULL`。使用智能字符串库的示例参见附录 C。

```c
void smart_str_appendc(smart_str *str, char ch);
void smart_str_appends(smart_str *str, char *buf);
void smart_str_appendl(smart_str *str, char *buf, int buflen);
void smart_str_appends(smart_str *str, smart_str *appe);
```

将字符、字符串或其他智能字符串追加到初始化的智能字符串。如果内部字符串成员尚未分配，则将分配。如果已经分配但大小不足以容纳新追加，则将增大。智能字符串总是过度分配（多达 128 字节），以避免频繁调用 `realloc`。

```c
void smart_str_append_long(smart_str *str, long val);
void smart_str_append_off_t(smart_str *str, off_t val);
void smart_str_append_unsigned(smart_str *str, unsigned long val);
```

向之前初始化的智能字符串（smart string）追加一个数值。数字始终以十进制整数表示。要追加任何其他类型的数字，请使用带有 `sprintf()` 的本地缓冲区，然后追加生成的字符串。

`void smart_str_0(smart_str *str);`

`NULL` 终止智能字符串。始终可以通过 `str->c` 和 `str->len` 访问智能字符串的内容；但然而，`str->str` 仅在调用此函数后才会被 `NULL` 终止，在此之前不应与 `strlen()` 或其他期望 `NULL` 终止字符串的方法配合使用。

`void smart_str_free(smart_str *str);`

释放智能字符串使用的内部缓冲区（`str->c`）。

### `ext/standard/php_uuencode.h`

`int php_uudecode(char *src, int src_len, char **dest);`
`int php_uuencode(char *src, int src_len, char **dest);`

对字符串值进行 UU 编码或解码。每个方法都返回新分配字符串的长度，并将字符串指针填充到 `dest` 中。

| 参数 | 目的 |
| --- | --- |
| `src` | 待编码或解码的字符串 |
| `src_len` | 待编码或解码的字符串长度 |
| `dest` | 填充新分配的字符串指针 |

### `ext/standard/php_var.h`

`void php_var_serialize(smart_str *buf, zval **struc, php_serialize_data_t *var_hash TSRMLS_DC);`
`void PHP_VAR_SERIALIZE_INIT(php_serialize_data_t var_hash);`
`void PHP_VAR_SERIALIZE_DESTROY(php_serialize_data_t var_hash);`

将 PHP 变量序列化为简单的字符串值。`php_var_serialize()` 使用特殊的中间存储变量 `var_hash` 来管理引用并减少开销。在序列化之前调用 `PHP_VAR_SERIALIZE_INIT()` 宏，之后调用 `PHP_VAR_SERIALIZE_DESTROY()`。

| 参数 | 目的 |
| --- | --- |
| `buf` | 目标智能字符串缓冲区 |
| `struct` | 待序列化的 PHP 变量 |
| `var_hash` | 中间序列化存储变量 |

`int php_var_unserialize(zval **rval, const unsigned char **str, const unsigned char *str_end, php_unserialize_data_t *var_hash TSRMLS_DC);`
`void PHP_VAR_UNSERIALIZE_INIT(php_unserialize_data_t var_hash);`
`void PHP_VAR_UNSERIALIZE_DESTROY(php_unserialize_data_t var_hash);`

将简单的字符串值反序列化为 PHP 变量。`php_var_unserialize()` 使用特殊的中间存储变量 `var_hash` 来管理引用并减少开销。在反序列化之前调用 `PHP_VAR_UNSERIALIZE_INIT()` 宏，之后调用 `PHP_VAR_UNSERIALIZE_DESTROY()`。

| 参数 | 目的 |
| --- | --- |
| `rval` | 存储的目标 zval |
| `str` | 序列化字符串的起始位置。将随着反序列化而更新，并用于指示错误发生的位置。 |
| `str_end` | 序列化字符串的结束。 |
| `var_hash` | 中间反序列化存储变量。 |

`void php_var_export(zval **struc, int level TSRMLS_DC);`
`void php_var_dump(zval **struc, int level TSRMLS_DC);`
`void php_debug_zval_dump(zval **struc, int level TSRMLS_DC);`

以不同的详细程度输出 PHP 变量的内容。`level` 参数在内部用于创建渐进式输出，通常在初始调用时应设置为 `0`。

### `ext/standard/php_versioning.h`

`int php_version_compare(const char *v1, const char *v2);`

`strcmp()` 的特殊变体，设计用于比较版本字符串。该方法是用户态 `version_compare()` 函数的内部实现。

### `ext/standard/reg.h`

`char *php_reg_replace(const char *pattern, const char *replace, const char *string, int icase, int extended);`

执行正则表达式替换。这是用户态 `ereg_replace()` 和 `preg_replace()` 函数的内部实现。

| 参数 | 目的 |
| --- | --- |
| `pattern` | 用于匹配的正则表达式 |
| `replace` | 用于替换匹配项 `pattern` 的字符串 |
| `string` | 用于搜索 `pattern` 并进行替换的字符串 |
| `icase` | 设置为非零以便在替换期间使用不区分大小写的匹配 |
| `extended` | 设置为非零以执行扩展正则表达式替换 |

### `ext/standard/md5.h`

`void PHP_MD5Init(PHP_MD5_CTX *context);`
`void PHP_MD5Update(PHP_MD5_CTX *context, const unsigned char *buf, unsigned int buf_len);`
`void PHP_MD5Final(unsigned char output[16], PHP_MD5_CTX *context);`

初始化、更新并完成 MD5 摘要操作。请参考附录 C 获取使用 PHP 哈希算法的示例。

| 参数 | 目的 |
| --- | --- |
| `context` | 哈希上下文 |
| `buf` | 待处理的数据缓冲区 |
| `buf_len` | `buf` 的长度 |
| `output` | 存储最终结果的缓冲区 |

`void make_digest(char md5str[33], unsigned char digest[16]);`

将二进制结果转换为可读的十六进制字符。`md5str` 必须包含 `NULL` 。

### `ext/standard/sha1.h`

`void PHP_SHA1Init(PHP_SHA1_CTX *context);`
`void PHP_SHA1Update(PHP_SHA1_CTX *context, const unsigned char *buf, unsigned int buf_len);`
`void PHP_SHA1Final(unsigned char output[20], PHP_SHA1_CTX *context);`

初始化、更新并完成 SHA1 摘要操作。参考附录 C 获取使用 PHP 哈希算法的示例。这些方法的含义与 MD5 操作一致。

### `ext/standard/url.h`

```c
php_url *php_url_parse(char const *str);
php_url *php_url_parse_ex(char const *str, int length);
typedef struct php_url {
    /* scheme://user:pass@host:port/path?query#fragment */
    char *scheme;
    char *user;
    char *pass;
    char *host;
    unsigned short port;
    char *path;
    char *query;
    char *fragment;
} php_url;
void php_url_free(php_url *url);
```



解析 URL 的组成部分。方法的第一次期望 `NULL` 终止字符串，而 `ex` 版本允许包含 `NULL` 字节的二进制安全字符串（通过显式 `length` 参数）。`php_url` 结构成员可以作为字符串或数值使用，并且必须通过 `php_url_free()` 显式释放。参考第 15 章获取这些方法的用法示例。

附录 D，“附加资源”，将重点介绍这些类型的“他们是如何做到的？”这种通过示例进行学习的方法。不过，你将首先查看一组用于执行最常见任务的样板模板，你可以在你自己的项目中对其进行自由修改和使用。

![](img/30011536.html)

## C. 扩展与嵌入食谱库

就像一个配备妥当的厨房一样，PHP 提供了创建任何大师作的环境和原料，大练的厨师可以根据自己的心意进行创作。然而，正如任何在炉灶旁待过时间的人所知，简单地随机将一些食材扔进搅拌机，然后把产生的糊状放入微波炉是不够的。一顿愉快的餐饭，就像一个实用的扩展一样，需要配方。在之前的几个章节中，你学习了从零开始创建这些配方所需的基础技能，但在大多数任务中，没有理由从零开始。本附录提供了一些常用代码示例，你可以在你自己的扩展或嵌入项目中复用这些代码。

![](img/30011536.html)

![](img/30011536.html)

### 骨架

本节提供的示例将作为构建或布局更大型扩展的起点。通过在标记的地方填入你自己的代码，你可以专注于功能部分，而无需担心格式化以及其他无聊的重复性工作。

除非另有说明，此处提供的所有模板均命名为中性名称 `cookbook`，在实现它们时应更改为更合适的名称。在所有情况下，请假设大小写是敏感的，例如，`cookbook` 不等于 `COOKBOOK`。

### 释

本节涵盖的内容只是对本书正文中核心材料的整合重述。如果你已经对它了如，请直接跳到本附录后半部分的“代码库”（Code Pantry）。

### 极简扩展

如果你已经读了这本书的大部分内容，这个框架看起来会非常眼熟。这是你在第 5 章中看到的第一个扩展，形象地命名为“你的第一个扩展”。

Listing C.1、C.2 和 C.3 中显示的三个文件代表了构建一个可加载 PHP 扩展所需的最少代码和配置数据。请回看第 5 章以复习如何将其作为可加载模块进行构建。

#### Listing C.1. `config.m4` 简单的配置脚本

```php
PHP_ARG_ENABLE(cookbook,
  [是否启用 "cookbook" 扩展],
  [  enable-cookbook         启用 "cookbook" 扩展支持])

if test $PHP_COOKBOOK != "no"; then
  PHP_SUBST(COOKBOOK_SHARED_LIBADD)
  PHP_NEW_EXTENSION(cookbook, cookbook.c, $ext_shared)
fi
```

#### Listing C.2. `php_cookbook.h` 简单的头文件

```php
#ifndef PHP_COOKBOOK_H
#define PHP_COOKBOOK_H
#define PHP_COOKBOOK_EXTNAME      "cookbook"
/* 此常数的值由你任意选择。
   PHP 实际上并不使用此值；但是
   在每次发布时增加它是有意义的。 */
#define PHP_COOKBOOK_EXTVER      "1.0"
#ifdef HAVE_CONFIG_H
#include "config.h"
#endif
#include "php.h"
extern zend_module_entry cookbook_module_entry;
#define phpext_cookbook_ptr &cookbook_module_entry
#endif
```

#### Listing C.3. `cookbook.c` 简单的源文件

```php
#include "php_cookbook.h"
zend_module_entry cookbook_module_entry = {
    STANDARD_MODULE_HEADER
#ifdef PHP_WIN32
    "NULL",
#endif
    NULL
};
PHP_GET_MODULE(cookbook)
#ifdef COMPILE_DL
}
#endif
```

用户空间函数的内部实现通过一组 `zend_function_entry` 结构体向引擎声明，具体如第 5 章“你的第一个扩展”中所述。将列表 C.7 所示的结构体放在你的 `zend_module_entry` 结构体上方。

### 列表 C.7. 空函数条目列表

```
zend_function_entry php_cookbook_functions[] = {
    /* Function entry macros such as
       PHP_FE(), PHP_FALIAS, and PHP_NAMED_FE() go here */
    { NULL, NULL, NULL }
};
```

现在，通过将对应函数列表的 `NULL` 替换为 `php_cookbook_functions`，将该新结构体链接到你的模块条目。

在 `zend_function_entry` 结构体就绪后，使用 `PHP_FUNCTION()` 宏定义实际的函数实现，如列表 C.8 所示。

### 列表 C.8. 空函数声明

```c
PHP_FUNCTION(cookbook_dosomething)
{
    /* Code to be executed when cookbook_dosomething()
       is called from userspace goes here */
}
```

现在，在你的 `zend_function_entry` 结构体中的终止 `NULL` 条目之前，放入一个匹配的条目：`PHP_FE(cookbook_dosomething, NULL)`。

#### 添加资源

PHP 使用资源（resource）数据类型来存储无法或不能映射到 PHP 用户空间数据的透明或复杂数据类型（参见列表 C.9）。这些类型在扩展的 `MINIT` 回调中声明，该回调在启动（Startup）阶段被调用。请参考第 9 章“资源数据类型”了解其使用的详细说明。

### 列表 C.9. 声明资源类型

```c
/* List Entry type IDs are registered in a common pool shared by all threads
   And therefore can be stored in a true-global scope */
int le_cookbook_type;

/* The name of your resource type may be arbitrarily assigned and
   does not necessarily have to be unique,
   although good practices dictate it should be. */
#define PHP_COOKBOOK_RESOURCE_NAME "Cookbook Resource"

/* Don't forget: Since MINIT is being used,
   it must be referenced from the zend_module_entry structure */
PHP_MINIT_FUNCTION(cookbook)
{
    le_cookbook_type = zend_register_list_destructors_ex(
                       NULL, /* Non-persistent destructor */
                       NULL, /* Persistent destructor */
                       PHP_COOKBOOK_RESOURCE_NAME, module_number);
    return SUCCESS;
}
```

当资源变量在停用（Deactivation）阶段或请求过程中由于被 `unset()` 或超出作用域隐式释放时，其非持久析构函数（nonpersistent destructor）会被调用。对于持久资源（参见第 9 章），当资源从持久列表中移除时（通常是对显式关闭或停止命令的响应），持久析构函数也会被调用。

这两个析构函数的原型是完全相同的（参见列表 C.10）：

### 列表 C.10. 资源析构回调

```c
void php_cookbook_resource_dtor(zend_rsrc_list_entry *rsrc TSRMLS_DC)
{
    /* The registered data to be destructed can be found in rsrc->ptr */
}
```

一旦定义定义，析构回调的名称（`php_cookbook_resource_dtor`）就可以添加到 `zend_register_list_destructors_ex()` 调用中，根据需要替换其中一个或两个 `NULL` 占位符。

#### 添加对象

简单的实用对象声明始于 `MINIT` 回调中的几行代码以及至少一个方法的声明（参见列表 C.11

```c
{
    /* Code added here will be executed in response to calling
       Cookbook_Class::__construct(), including in response to
       new Cookbook_Class() which implicitly calls the constructor */
}

zend_function_entry php_cookbook_methods[] = {
    /* Refer to Chapter 11, "PHP5 Objects," for the meaning of
       the ZEND_ACC_* constants */
    PHP_ME(Cookbook_Class,__construct, NULL, ZEND_ACC_PUBLIC | ZEND_ACC_CTOR)
    { NULL, NULL, NULL }
};

/* Don't forget: Because MINIT is being used,
   it must be referenced from the zend_module_entry structure */
PHP_MINIT_FUNCITON(cookbook)
{
    zend_class_entry ce;
    INIT_CLASS_ENTRY(ce, "Cookbook_Class", php_cookbook_methods);
    zend_register_internal_class(&ce TSRMLS_CC);
    return SUCCESS;
}
```

### 代码库

本附录中的剩余示例处理现实世界的问题。`eval()` 函数直接映射到一个几乎同名的内部调用。尽管 Zend 引擎使用的实际实现看起来非常不同，但你的扩展或嵌入环境可以使用列表 C.13 所示的函数来复刻该功能。

#### 调用用户空间

有时内部函数会选择使用第 20 章“高级嵌入”中描述的 `call_user_function()` API 回调用户空间。

### 列表 C.12. 调用用户空间

```c
PHP_FUNCTION(cookbook_call_foo)
{
    zval fname, params[2];
    ZVAL_STRING(&fname, "foo", 1);
    ZVAL_STRING(&params[0], "bar", 1);
    ZVAL_STRING(&params[1], "baz", 1);

    /* Call: foo("bar", "baz") */
    if (call_user_function(EG(function_table), NULL,
                      &fname, return_value, 2, &params TSRMLS_CC) == FAILURE) {
        php_error_docref(NULL TSRMLS_CC, E_WARNING,
                      "Unable to call foo(), is it defined?");
        RETVAL_FALSE;
        goto cleanup;
    }

    /* Call succeeded,
       return_value will already have been set
       because it was passed through foo(),
       all that's left is to clean up */
cleanup:
    zval_free(&fname);
    zval_dtor(&params[0]);
    zval_dtor(&params[1]);
}
```

#### 计算并执行代码

用户空间的 `eval()` 函数直接映射到一个几乎同名的内部调用。尽管 Zend 引擎使用的实际实现看起来非常不同，但你的扩展或嵌入环境可以使用所示函数来复刻：

### 列表 C.13. 重造 `eval()`

```c
PHP_FUNCTION(cookbook_eval)
{
    char *code;
    int code_len;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "s",
                      &code, &code_len) == FAILURE) {
        return;
    }

    if (zend_eval_string(code, return_value, "Cookbook eval'd code") == FAILURE) {
        php_error_docref(NULL TSRMLS_CC, E_WARNING, "Error executing provided
code");
        RETVAL_FALSE;
    }
}
```

#### 测试和链接外部库

让 PHP 链接额外的外部库只需要一行代码。然而，要做一些工作以确保该库在编译和执行期间都能正常工作。[列表 C.14]所示的 `config.m4` 将搜索并链接一个理论上的 `libexample` 库。

### 列表 C.14. 测试和链接

```
PHP_ARG_WITH(cookbook,
  [是否启用 "cookbook" 扩展],
  [ enable-cookbook[=DIR] 使用 libexample 启用 "cookbook" 扩展])

if test $PHP_COOKBOOK != "no"; then
  AC_MSG_CHECKING([for libexample headers])
  dnl Look in a couple default locations and whatever is passed to ./configure
  dnl Note, lines beginning with "dnl" are config.m4 comments
  for i in /usr /usr/local $PHP_COOKBOOK; do
    if test -r $i/include/example.h; then
      EXAMPLE_DIR=$i
      AC_MSG_RESULT(found in $i)
    fi
  done

  if test -z "$EXAMPLE_DIR"; then
    dnl This will cancel configuration if the required headers aren't found
    AC_MSG_ERROR(example.h not found)
  fi

  dnl Make sure the library exists as well
  dnl and that it contains expected symbol
  PHP_CHECK_LIBRARY(example, example_sort_function,
    PHP_ADD_LIBRARY(example, $EXAMPLE_DIR/lib, COOKBOOK_SHARED)
    AC_DEFINE(HAVE_LIB, 1, Have lib),
    AC_MSG_ERROR(lib not found),
    $EXAMPLE_DIR/lib)

  PHP_SUBST(COOKBOOK_SHARED)
  PHP_NEW_EXTENSION(cookbook, cookbook.c, $ext_shared)
```



#### 将数组映射到字符串

由于 PHP 是一种胶水语言，最常见的任务之一是获取用户数据，将其格式化以供外部库使用，然后从反方向处理结果。列表 C.15 所示的短函数假设第三方库已经按照第 17 章“配置与链接”中概述的步骤进行了链接，并接受一个数字、一个字符串和一个值数组。较简单的数字和字符串值将相对不变地传递；然而，数组会被重新映射为库函数通常接受的字符串向量。

##### 列表 C.15.外部函数调用

```c
/* 包含第三方库的头文件 */
#include <example.h>

PHP_FUNCTION(cookbook_sort_strings)
{
    /* 输入参数 */
    long lparam;
    char *sparam;
    int sparam_len;
    zval *arr_data;

    /* 中间值 */
    char **str_vector;
    int str_count, str_index = 0;
    Hash pos;
    zval **current;
    int result;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "sa", &lparam,
                      &sparam, &sparam_len, &arr_data) == FAILURE) {
        return;
    }

    /* 将 arr_data 转换为字符串向量 */
    str_count = zend_hash_num(Z_ARRVAL_P(arr_data));
    str_vector = ecalloc(str_count + 1, sizeof(char));
    for(zend_hash_pointer_reset(Z_ARRVAL_P(arr_data), &pos);
        zend_hash_get_current_data(Z_ARRVAL_P(arr_data), (void)&current) == SUCCESS) {
        zval duplicate = **current;
        /* 复制当前 zval 的内容，以便可以安全地
           转换为字符串类型并在稍后重新填充到新的 zval 中 */
        zval_copy(&duplicate);
        convert_to_string(&duplicate);
        str_vector[str_index++] = Z_STRVAL(duplicate);
    }

    /* 调用第三方库的方法，在此情况下
     排序函数不会改变
     字符串向量条目的内容，
     只会重新排列它们的顺序。 */
    result = example_sort_function(lparam, sparam, str_count, str_vector);
    if (result < 0) {
        /* 发生错误 */
        /* 释放单个字符串元素 */
        while (str_index) {
            if (str_vector[str_index]) {
                efree(str_vector[str_index]);
            }
        }
        /* 释放向量容器 */
        efree(str_vector);
        /* 抛出错误 */
        php_error_docref(NULL TSRMLS_CC, E_WARNING,
                      "无法执行排序操作，"
                      "libexample 返回 %d", result);
        RETURN_FALSE;
    }

    /* 将结果字符串存回 zval 数组中
       并返回给应用程序 */
    array_init(return_value);
    while (str_index) {
        if (str_vector[str_index]) {
            add_next_index_string(return_value, str_vector[str_index], 0);
        }
    }
}
```

#### 访问流

列表 C.16 显示了在单个函数内部基本的 `fopen`/`fread`/`fwrite`/`fclose` 功能。有关流访问的更详细的分析，请参阅第 14 章“访问流”。

##### 列表 C.16. 读取和写入流内容

```c
#include <ctype.h>

/* 强制将文件的第一个字符转为大写 */
PHP_FUNCTION(cookbook_first)
{
    char *filename, c;
    int filename_len;
    php_stream *stream;
    int options = ENFORCE_SAFE_MODE | REPORT_ERRORS;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "s",
                      &filename, &filename_len) == FAILURE) {
        return;
    }

    stream = php_stream_open(filename, "r+", options);
    if (!stream) {
        /* 无法打开文件 */
        RETURN_FALSE;
    }

    /* 获取字符 */
    c = php_stream_getc(stream);
    if (c < 'a' || c > 'z') {
        /* 无需操作，不是小写的 */
        php_stream_close(stream);
        RETURN_TRUE;
    }

    php_stream_rewind(stream);
    php_stream_putc(stream, toupper(c));
    php_stream_close(stream);
    RETURN_TRUE;
}
```

#### 访问传输层

传输层是用于与套接字风格资源通信的特殊流类型。列表 C.17 显示了从 whois 服务器请求数据的 `fsockopen`/`fwrite`/`stream_get_contents` 功能。有关流的更详细分析，请参阅第 14 章。

##### 列表 C.17. 访问传输层

```c
/* 包含第三方库的头文件 */
PHP_FUNCTION(cookbook_whois)
{
    char *host, *query, *xport, *contents;
    int host_len, query_len, xport_len, contents_len;
    php_stream *stream;
    int options = ENFORCE_SAFE_MODE | REPORT_ERRORS;
    int flags = STREAM_XPORT_CLIENT | STREAM_XPORT_CONNECT;

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "ss",
                      &host, &host_len, &query, &query_len) == FAILURE) {
        return;
    }

    xport_len = spprintf(&xport, 0, "tcp://%s:43", host);
    stream = php_stream_xport_create(xport, xport_len, options, flags,
                                     NULL, NULL, NULL, NULL);
    efree(xport);
    if (!stream) {
        /* 无法打开文件 */
        RETURN_FALSE;
    }

    /* 发送查询 */
    php_stream_write(stream, query, query_len);
    php_stream_write(stream, "\r\n", 2);

    /* 获取结果 */
    contents_len = php_stream_copy_to_mem(stream, &contents,
                                          PHP_STREAM_COPY_ALL, 0);
    php_stream_close(stream);
    if (contents_len < 0) {
        /* 发生错误 */
        RETURN_FALSE;
    } else if (contents_len == 0) {
        /* 无数据 */
        RETURN_EMPTY_STRING();
    } else {
        /* 将 WHOIS 响应返回给用户 */
        RETURN_STRINGL(contents, contents_len, 0);
    }
}
```

#### 计算消息摘要

消息摘要是通过初始化摘要上下文、将数据泵入上下文，然后将上下文完成为摘要块来计算的。列表 C.18 所示的函数复制了用户态 `md5()` 函数的功能。

```c
#include "ext/standard/md5.h"

PHP_FUNCTION(cookbook_md5)
{
    char *message;
    int message_len;
    zend_bool raw_output = 0;
    PHP_MD5_CTX context;
    char digest[16];

    if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "s|b",
                      &message, &message_len, &raw_output) == FAILURE) {
        return;
    }

    PHP_MD5Init(&context);
    PHP_MD5Update(&context, message, message_len);
    PHP_MD5Final(digest, &context);

    if (raw_output) {
        RETURN_STRINGL(digest, 16, 1);
    } else {
        char hexdigest[33];
        make_digest(hexdigest, digest);
        RETURN_STRINGL(hexdigest, 32, 1);
    }
}
```

通过将列表 C.18 中的 MD5 替换为 SHA1，即可计算 SHA1 摘要。注意，`make_digest()` 方法适用于 MD5，因此你需要手动转换较长的 SHA1 摘要。

### 总结

编程语言以其语法的严谨性和解释的一致性而闻名。对于不熟悉某种语言惯用法和特殊之处的新开发者来说，这通常会让他们感到沮丧；而在像 PHP 内部机制这样复杂的环境中，它们实际上通过其庞大的基础设施有效地改变了其父语言的方言。通过使用本附录中这类简单且经过良好测试的模板，你可以专注于熟悉真正有趣的部分，并避免那种不受欢迎的初始挫败感。

在本书的最后一个附录中，你将看到如何通过整合开源开发者的工作并获取那些无法挤在这几百页书中的问题的答案，从而超越本书的限制。

## D. 额外资源

在尝试解决新问题时，最好的方法是问：“这真的是新的吗？”很有可能，某人已经做过类似的事情，并发布了代码供公开使用。因此，值得利用你最喜欢的搜索引擎来查找是否存在可以借用的现有实现，并根据你的需求进行调整。毕竟，既然别人已经发现它们应该是圆的，你又何必重复轮子呢？

### 开源项目

从其他开发者那里借用实现时，务必确保相关代码的许可协议允许你重用该工作。某些许可允许在不注明来源的情况下完全包含他人的实现，而另一些许可甚至会对你的大型作品实施严格限制，即使该作品可能只包含了一小部分被导入的代码。请仔细阅读所有许可文档，如有疑问，请联系原作者获取许可。

### PHP 源码树

虽然这不言而喻，但 PHP 源码树本身就是一个巨大的示例代码库，随供挑选取用。由于所有内置的扩展在 PHP 在线手册中都有详尽的文档，你不需要猜测某个 `PHP_FUNCTION()` 块的作用。如果某些地方看起来不通，你可以相信，关注 PHP 邮件列表的人会熟悉它并能够为你解释。最棒的是，除了少数内置库和一些分散的副本外，PHP 源码树的大部分都是极其宽松且友好的 PHP 许可发布的。

在这些易于获取的源码文件中，你将找到几乎每个你想实现的任务的详细示例。毕竟，与 PHP 交互并扩展它的大多数功能，都是因为某个内置扩展的需求而存在的。

如果需要处理 PHP 源码树的帮助，请查看 [`lxr.php.net`](http://lxr.php.net)。这个实用的工具从 CVS 中的源码中定期重新生成，显示 PHP 源码文件时提供了与源码树相关部分的直接上下文链接。例如，假设你正在查看以下代码块并好奇它的作用是什么：

```c
void *php_hacer_una_thingamajig(int foo, double bar) {
    return ZEND_GROK_THE_CASBAH(foo + foo * bar);
}
```



你可以翻阅数页 `grep` 输出来寻找 `ZEND_GROK_THE_CASBAH()` 的定义，但当你需要跨数十个源文件追踪定义时，这会变得非常枯燥。LXR 通过将每个宏、函数调用、常量或难以追踪的符号显示为指向其定义源文件和行的超链接，解决了这个问题。

## 链接第三方库

正如你已经在第 17 章中看到的，“配置与链接”，如 `zlib` 等扩展可以作为设计 `config.m4` 和 `config.w32` 文件的有用模板，这些文件可以搜索、测试并链接所需的第三方库。该扩展以及 `mysql`、`bcmath` 等，为探索可选功能以及根据当前主机环境启用一系列变量功能集提供了极佳的示例。

## 导出资源

第 9 章，“资源数据类型”涵盖了注册、获取和清理资源数据类型的成熟 API。因为在 Zend Engine 2 对象出现之前，这是存储复杂内部数据结构的唯一方法，你发现在许多 PHP 内置扩展中以某种形式使用了它们。

首先，可以考虑看一眼结构简单的 `sockets` 扩展，作为使用这一核心功能的参考。由于该扩展与 PHP 核心其他部分的共享 API 调用较少，且除了 `libc` 之外不链接任何外部库，因此它为使用这一基本功能提供了非常直观的参考。

## 实现流

PHP 的标准发行版包含了 FTP 和 HTTP 层的包装实现，其源码可以在 `ext/standard` 文件夹下的 `ftp_wrapper.c` 和 `http_wrapper.c` 中找到。与这些相关的 `php_stream_wrapper` 结构在 `basic_functions.c` 中注册。

HTTP 包装实现为使用上下文选项在打开阶段修改流的行为提供了详尽且易于理解的演示。而 FTP 包装则由于其涵盖了所有的可选操作，提供了更完整的参考价值。

在开发早期阶段，作为参考时最有用的扩展将是那些自 PHP 语言诞生起就具有标记性的扩展：基础胶水扩展（basic glue extension）。

在此类别中，像 `expect` 和 `openal` 这样的扩展展示了 PHP 用户空间函数到其库实现的简单的一对一映射。在这里，你可以找到数据类型映射、链接和通用资源管理的示例。

### PHP5 对象实现

ZE2 对象模型相比其早期的版本具有显著优势；遗憾的是，在现实中很少有这种用用示例。`flitetts` 在一个相当小且易于解析的包中提供了此类一种实现。`pdo` 和其他扩展中也存在更健壮的实现，但它们被绑定到了更复杂的应用程序逻辑中。在设计内部类实现时，最好从最基础的功能开始并在此基础上构建。

### 字节码缓存 (Opcode Caches)

许多项目已经实现了字节码缓存，通过保存脚本编译后的字节码形式，并仅在源脚本发生变化时才进行重新编译，从而提高网站的性能。[www.php.net](http://www.php.net) 使用的字节码缓存以及你最容易学习到的是 `APC`，即高级 PHP 缓存。

`APC` 通过将内置编译器替换为缓存系统来挂钩 Zend 引擎，仅当内存中已没有已编译的版本时才重新分发请求。该实现还通过其自己的跨平台兼容分配系统大量利用了共享内存。这并不是一个在你第一天就应该深入的话题，但它最终会为你提供大量可靠且可复用的思路。

### 奇技领域 (The Wilder Side)

如果想了解本书未涵盖且可能在其他任何地方找到的主题，请参考 `runkit`，它暴露了函数和类注册表，并使用 TSRM 层将请求嵌套在一起。其他操作 PHP 解释器的不寻示例包括 `operator`（它重写了几个字节码的含义）以及 `VLD`（“Vulcan 逻辑解码器”，它将编译后的脚本转换为人类可读的表示）。特别是 `VLD`，它让你能够独特地观察引擎的运行机制，并可能为未来开发那些尚未想象的道路提供其自身的灵感。

这些冷门扩展所涵盖的主题远超本书的范围，并且通常不适用于现实世界，尽管它们展示了 PHP 和 Zend 引擎在多大程度上允许被定制以适应第三方的需求。

### PECL 作为设计平台

PECL 不仅是查看他人代码的来源。如果你计划将扩展作为开源项目发布，你可能会找到比这里更糟糕的去处。除了提供快速且可靠的 CVS 仓库外，PECL 扩展和 SAPI 实现还有机会在官方的 php.net 手册中托管其文档。更令一说的是，托管在 PECL 内部且具有有效 `config.w32` 文件的扩展，将由 `pecl4win` 编译系统自动构建为可用的 `DLL`s，并在 [`pecl4win.php.net`](http://pecl4win.php.net) 提供。

#### PHP CVS 仓库的其他地方

在第 4 章“设置构建环境”中，你看到了从 `cvs.php.net` 的 `php-src` 模块检出 PHP 源码树的指令。在该服务器上可以找到的其他模块包括 `pear` 和 `pecl`、`phpdoc` 手册及其所有的翻译，以及 `embed` 仓库中一个几乎格格不入的项目：`php-irssi`。

该项目被设计用于第 19 章“设置主机环境”中引入的 embed SAPI 的范例。它演示了如何链接 `libphp5.so` 以在流行的 IRC 客户端 `irssi` 访问 PHP 解释器。在这个简单且稳定的存根库中，可以找到优雅错误处理、输出捕获与重定向以及同时扩展和嵌入的示例。

### 寻求帮助的地方

针对 PHP 这样的开源项目进行开发的缺点之一是缺乏付费支持渠道。对于查询，无法保证响应时间，也无法保证回答你的人真的知道自己在说什么。

针对 PHP 这样的开源项目进行开发的巨大优势之一也是缺乏付费支持渠道。因为 PHP 被许多实际上熟悉其内部机制的个人广泛使用，寻找某个特定主题的可靠信息源通常只需要提问。

请记住，这些资源中的大多数是志愿者，他们提供帮助仅仅是为了传递知识的满足感。礼貌地请求并耐心等待答案；用蜂蜜比用醋更容易引来蜜蜂。

#### PHP 邮件列表

这些信息资源中最正式的是 PHP 项目本身托管的邮件列表。如 `internals@lists.php.net` 和 `pecl-dev@lists.php.net` 等邮件列表由 PHP 语言开发者本人定期监控，任何提问良好的问题通常可以在一天内得到答案，甚至在一个小时内得到答案。

`pecl-dev` 列表通常是获取如何在扩展或嵌入项目中完成特定任务指导的最佳去处。不要被列表的名字吓跑了；在开发闭源和专有代码时寻求帮助是完全可以。PECL 仅仅是这里开发的大多数项目的驱动力。

另一方面，`internals` 列表专注于语言本身的发展。在本书出版时，`internals` 列表关注的是语言本身的发展。

#### IRC

几个网络提供通用支持。在某些网络中，例如 Freenode `#php` 频道，你会发现一些具有 PHP 开发经验的个人。

### 总结

你不是第一个踏上 PHP 开发道路的人，先你走过的人通常以 HOWTO 或教程的形式留下了印记。花些时间搜索网络、参考现有代码并寻找同行，你将能够节省无数小时的烦恼。

- `$_FILE` 变量
- `$_GET` 变量
- `$_POST` 变量
- `$_SESSION` 变量
- `$GLOBALS` 变量
- `&` (连接符号)
- *nix (Unix 类环境)
    - 编译器
    - 扩展
        - 编译
        - 静态编译
    - 工具
- `php_localtime_r()` 函数
- `./configure`
    - `enable-debug`
    - `enable-embed` (第 2)
    - `enable-maintainer-zts`
    - `enable-sample`
    - `with-extname`
- `/` 修符 (`zend_parse_parameters()` 函数)
- `enable-debug` 开关 (`./configure`)
- `enable-embed` 开关 (`./configure`) (第 2)
- `enable-maintainer-zts` 开关 (`./configure`)
- `enable-sample` 开关 (`./configure`)
- `with` 选项 (`PECL_Gen`)
- `with-extname` 选项 (`./configure`)
- `__call()` 方法
- `__clone()` 方法
- `__construct()` 方法
- `__destruct()` 方法
- `__get()` 方法
- `__isset()` 方法
- `__set()` 方法
- `__toString()` 方法
- `__unset()` 方法
- `_STREAM_NOTIFY_SEVERITY_ERR` 码
- `_STREAM_NOTIFY_SEVERITY_INFO` 码
- `_STREAM_NOTIFY_SEVERITY_WARN` 码
- `|` 修符 (`zend_parse_parameters()` 函数)

### 索引

[SYMBOL] [A] [B] [C] [D] [E] [F] [G] [H] [I] [K] [L] [M] [N] [O] [P] [Q] [R] [S] [T] [U] [V] [W] [X] [Z]

- 启动与关闭抽象
- `AC_DEFINE()` 宏
- `AC_MSG_ERROR()` 宏
- `AC_MSG_WARNING()` 宏
- `AC_TRY()` 宏
- 接受实例
- 访问
    - 扩展全局变量
    - 级别，INI 设置
    - 流
        - 关闭
        - 转换为 zvals
        - 刷新
        - 读取
        - 寻求
        - 报告位置
        - 写入
    - 传输
- `active_symbol_table`
- `add_assoc()` 函数 (第 2)
- `ADD_EXTENSION_DEP()` 宏
- `add_index()` 函数 (第 2)
- `add_next_index()` 函数 (第 2)
- `add_property()` 函数 (第 2)
- `add_ref()` 处理器
- 别名 (函数)
- `ALLOC_HASHTABLE()` 宏
- `ALLOC_INIT_ZVAL()` 宏
- 分配
    - 过滤器
    - 内存（参见内存管理）
    - 流 (第 2)
- 连接符号 (`&`)
- 应用，构建与编译
- `apt-get source php5` 命令
- `ARG_ENABLE()` 宏
- `arg_info` 结构体
- `ARG_WITH()` 宏
- `array_init()` 函数 (第 2)
- 数组
    - 向添加元素
    - 创建
    - 将带分隔符的字符串拆分为
    - 合并为带分隔符的字符串
    - 初始化
    - 映射向量
    - 填充
    - 转换为 URL 编码字符串
    - Zend API 调用
- `auto_global_callback`
- autoconf

### 索引

[SYMBOL] [A] [B] [C] [D] [E] [F] [G] [H] [I] [K] [L] [M] [N] [O] [P] [Q] [R] [S] [T] [U] [V] [W] [X] [Z]

- `base64.h`
- 绑定
    - 将 INI 设置到扩展全局变量
    - 传输流
- 块
- 缓冲区，输出
    - 拷贝
    - 结束
    - 刷新
    - 隐式刷新模式
    - 初始化
- 构建扩展
    - 在 *nix 下 (第 2)
    - 在 Windows 下
- 构建 PHP
    - *nix 工具
    - `./configure` 开关
        - `enable-debug`
        - `enable-embed`
        - `enable-maintainer-zts`
    - CVS 检出
    - PHP 编译
        - 在 UNIX 上
        - 在 Win32 上
    - 获取 PHP 源码
    - Win32 工具
- `BYREF_ALLOW` 常量
- `BYREF_FORCE` 常量
- `BYREF_FORCE_REST` 常量
- `BYREF_NONE` 常量

### 索引

[SYMBOL] [A] [B] [C] [D] [E] [F] [G] [H] [I] [K] [L] [M] [N] [O] [P] [Q] [R] [S] [T] [U] [V] [W] [X] [Z]

- `cache`, `opcode`
- `call-time pass-by-ref`
- `CALL_DTOR` 标志 (`php_stream_free()` 函数)
- `call_function()` 函数
- `call_method()` 处理器
- `call_user_function()` 函数 (第 2, 第 3)
- `call_user_function_ex()` 函数 (第 2)
- 回调到 PHP 中
    - 脚本文件包含的替代方案
    - 调用用户态函数 (第 2, 第 3)
- `calloc()` 函数
- 捕获输出
    - 输出缓冲
    - `log_message` 回调
    - `sapi_error`
    - 标准输出
- `cast_object()` 处理器
- 转换流
- `cc version` 命令
- `CG()` 宏
- 写时复制 (change on write)
- `char *php_info_html_esc()` 函数
- `CHECK_LIB()` 宏

### classes

- lookups
- PHP4 类
    - 构造函数
    - 声明
    - PHP 对象类型的演变
    - 继承
    - 初始化
    - 实例
    - 方法实现
    - 注册
    - 示例代码文件
- PHP5 类
    - 常量
    - 处理器
    - 接口
    - 方法
    - 属性
    - `zend_class_entry`
    - Zend API 调用
- 清理 HashTables
- CLI 周期
- `CLOSE_CASTED` 标志 (`php_stream_free()` 函数)
- `CLOSE_PERSISTENT` 标志 (`php_stream_free()` 函数)
- 关闭目录
- streams (第 2)
- 命令行，包括脚本 (第 2)；参见 `functions`，声明 `F.html`；`methods`，`tor.M`。
- `compare_objects()` 处理器
- 比较 HashTable
- 编译时引用传递
- 编译器
    - `gcc` (GNU 编译器集合)
    - Win32/PHP5 构建
- 编译宿主应用程序
- PHP
    - 在 UNIX 上
    - 在 Win32 上
- `config.m4` 文件 (第 2, 第 3, 第 4)
    - autoconf
    - 配置模块依赖
    - 强制执行模块依赖
    - 可选功能
    - 运行时模块依赖
    - 扫描头文件
    - 测试实际行为
    - 功能测试
- `config.w32` 文件
- 配置
    - autoconf
    - 配置文件
    - 可选功能
    - 扫描头文件
    - 测试实际行为
    - 功能测试
    - 强制执行模块依赖
    - 配置模块依赖
    - 运行时模块依赖
    - PHP
    - Windows config.w32 文件
- 配置模块依赖
- 常量
    - 声明
    - 查找...的值
    - PECL_Gen
- PHP5 对象
    - 注册
    - Zend API 调用
- 构造函数 (流)
- 默认上下文
    - 检索
    - 设置
    - 参数
- `convert_to_()` 函数
- `convert_to_string()` 函数
- 数据类型
- INI 设置
- 变量
- `cookbook.c` 文件 (第 2)
- `cookbook_call_foo()` 函数
- `cookbook_dosomething()` 函数
- `cookbook_eval()` 函数
- `cookbook_md5()` 函数
- `cookbook_sort_strings()` 函数
- `cookbook_ucfirst()` 函数
- `cookbook_whois()` 函数
- cookies, 发送
- 写时复制
- 复制
    - 哈希表元素
    - HashTables
    - 链表元素
    - 输出缓冲
- 访问核心全局变量
- 核心 PHP 函数 (参见特定函数。)
    - 错误报告
    - 杂项函数
    - open basedir
    - 输出
    - 重入性安全
    - 安全模式
- 启动/关闭
    - 字符串格式化
- `count()` 函数
- `count_elements()` 处理器
- 计数引用
- `current()` 函数
- 自定义代码, PECL_Gen
- CVS 仓库
    - PHP 源码，检出
- `cvsread` 账户

符号 A B C D E F G H I K L M N O P Q R S T U V W X Z

### 数据转换

- 数据转换
- 数据池、线程安全
- 数据检索
- 数据存储

### 数据类型

- 数据类型
- 转换
- 确定
- `IS_ARRAY`
- `IS_BOOL`
- `IS_DOUBLE`
- `IS_LONG`
- `IS_NULL`
- `IS_OBJECT`
- `IS_RESOURCE`
- `IS_STRING`
- 弱类型
- 资源
    - 解码
    - 定义
    - 延迟销毁
    - 销毁
    - 提前退出
    - 强制销毁
    - 存性检查
    - 长久注册
    - 内存分配
    - 引用计数器
    - 注册
    - 检索
    - 复用
    - 类型提示
- 数据值

#### 声明

- `$EMBED`
- 常量
- 扩展全局变量
- 函数
- INI 设置
- 接口
- 方法
- 模块信息
- 对象
- 属性
- 资源
- 超全局变量

## 解码

- base64 字符串
- 资源
- URL
- 默认流上下文
- `DEFINE()` 宏
- `del_ref()` 处理程序
- 延迟销毁
- 删除 (另见 [销毁], 哈希表)
- 目录
- 哈希表元素
- 链表元素

## 依赖关系

- 查找依赖的库
- 可选功能
- 扫描头文件
- 测试实际行为
- 测试功能性

## 强制执行

- 配置时模块依赖
- 运行时模块依赖
- PECL_Gen
- 销毁 (另见 删除、哈希表元素)
- 哈希表
- 资源
- 延迟销毁
- 强制销毁

## 析构函数

- 析构函数
- 为 PHP 配置
- 摘要
- `dir()` 函数

## 目录

- 关闭
- 创建
- 打开
- 读取
- 移除
- 流访问
- INI 设置

## 分流

- 应用
- 定义
- 上下文
- 检索
- 设置
- `dl()` 函数
- 双向列表
- 源码
- 生命周期

### 索引

符号 A B C D E F G H I K L M N O P Q R S T U V W X Z

- 早期退出
- 资源
- 声明
- `emalloc()` 函数
- `efree()` 函数
- `EG()` 宏
- 发送
- `emalloc()` 函数
- 生命周期
- 嵌入 SAPI
- 嵌入启动、覆盖
- 嵌入 1.c 应用
- 嵌入 2.c 文件
- 嵌入 3.c 文件
- 嵌入 4.c 文件
- `embed4_log_message()` 函数
- 嵌入 5.c 文件

## 嵌入

- 回调 PHP
- 脚本包含替代方案
- 调用用户空间函数
- 捕获输出
- 缓冲输出
- `log_message` 回调
- `sapi_error`
- 标准输出
- 嵌入启动、覆盖
- 错误处理
- 同时扩展和嵌入

## 宿主机环境设置

- 嵌入 SAPI
- 宿主机应用、构建和编译

# 实例化

# 注册/注销

# 流过滤器

## 应用

## 定义

# 查找 `tsrm_ls` 指针

# `CLOSE` 标志 (`php_stream_free()` 函数)

# `flags` 参数 (`php_stream_xport_create()` 函数)

# 浮点数，格式化

# `flock_compat.h`

# `flush()` 函数

# 刷新

## 过滤器

## 输出缓冲区

## 流 (第 2 次)

# `fopen()` 函数 (第 2, 第 3 次)

### 强制分离

# 强制销毁资源

# 格式化

## 浮点数

## 字符串

# `free()` 函数

# 释放

## 过滤器

## 流上下文

## 流

# `fsockopen()` 函数

## 函数

另见 [处理器, `add_ref()`]; [宏, `OBJCE`; [方法, `dtor`]。]

- `php_localtime_r()`
- `add_assoc_*()` (第 2 次)
- `add_index_*()` (第 2 次)
- `add_next_index_*()` (第 2 次)
- `add_property_*()` (第 2 次)
- 别名
- `array_init()` (第 2 次)
- `call_user_function()` (第 2 次, 第 3 次)
- `call_user_function_ex()` (第 2 次)
- `char *php_info_html_esc()`
- 检查是否可调用
- `cookbook_call_foo()`
- `cookbook_dosomething()`
- `cookbook_eval()`
- `cookbook_md5()`
- `cookbook_sort_strings()`
- `cookbook_ucfirst()`
- `cookbook_whois()`
- `current()`
- 声明 (第 2 次)
- `dir_opener()`
- `each()`
- `ecalloc()`
- `emalloc()`
- `embed4_log_message()`
- `end()`
- `realloc()`
- `estrdup()`
- `estrndup()`
- `eval()`
- `expand_filepath()`
- `fclose()`
- `flush()`
- `fopen()` (第 2 次)
- `fsockopen()`
- `get_zend_version()`
- `gzread()`
- `ini_set()` (第 2 次)
- `key()`
- `make_digest()` (第 2 次)
- `md5()`
- `mkdir()`
- 命名
- `next()`
- `object_and_properties_init()`
- `object_init()`
- `object_init_ex()` (第 2 次)
- `opendir()` (第 2 次)

### 参数

### 使用 `zend_parse_parameters()` 进行自动类型转换

## 类型提示

## `zend_get_parameters()` 函数

## `zend_get_parameters_ex()` 函数

# `pecalloc()`

#### PECL_Gen

## 自定义代码

## 内部函数

## 公共函数

- `pemalloc()`
- `perealloc()`
- `pestrdup()`
- `php_add_tick_function()`
- `php_addcslashes()`
- `php_addslashes()` (第 2 次)
- `php_addslashes_ex()`
- `php_asctime_r()`
- `php_base64_decode()`
- `php_base64_encode()`
- `php_basename()`
- `php_to_str()`
- `php_to_str_ex()`
- `php_check_based()`
- `php_check_based_ex()`
- `php_check_uid()`
- `php_check_uid_ex()`
- `php_resource`
- `php_copy()`
- `php_dirname()`
- `php_init()`
- `php_embed_shutdown()`
- `php_end_implicit_flush()`
- `php_end_ob()`
- `php_end_ob_buffers()`
- `php_error()`
- `php_error_ref()`
- `php_error_ref0()`
- `php_error_ref1()`
- `php_error_ref2()`
- `php_escape_html()`
- `php_escape_shell_arg()`
- `php_escape_shell_cmd()`
- `php_execute_script()`
- `php_explode()`
- `php_file_le_pstream()`
- `php_file_le_stream()`
- `php_file_le_stream_filter()`
- `php_flock()`
- `PHP_FUNCTION()` 宏
- `php_get_current_user()`

- `php_get_output_start_filename()`
- `php_get_output_start_lineno()`
- `php_get_stream_filters_hash()`
- `php_get_stream_filters_hash_global()`
- `php_gmtime_r()`
- `php_html_puts()`
- `php_implode()`
- `php_info_html_esc()`
- `php_info_print_box_end()`
- `php_info_print_box_start()` (2nd)
- `php_info_print_hr()` (2nd)
- `php_info_print_style()`
- `php_info_print_table_colspan_header()`
- `php_info_print_table_end()`
- `php_info_print_table_header()` (2nd)
- `php_info_print_table_row()` (2nd)
- `php_info_print_table_row_ex()`
- `php_info_print_table_start()` (2nd)
- `php_is_url()`
- `php_le_stream_context()`
- `php_lint_script()`
- `php_log_err()`
- `php_logo_guid()`
- `php_mail()`
- `php_math_number_format()`
- `PHP_MINIT_FUNCTION()`
- `php_mt_rand()`
- `php_mt_srand()`
- `php_ob_get_buffer()`
- `php_ob_get_length()`
- `php_print_info()`
- `php_print_info_htmlhead()`
- `php_printf()` (2nd)
- `php_rand()`
- `php_rand_r()`
- `php_raw_url_decode()`
- `php_raw_url_encode()`
- `php_reg_replace()`
- `php_register_extension()`
- `php_register_extensions()`
- `php_register_info()`
- `php_register_url_stream()`
- `php_register_url_stream_volatile()`
- `php_remove_tick_function()`
- `php_request_shutdown()`
- `php_request_startup()`
- `php_sample4_fd_is_fifo()`
- `php_sample4_register_boolean_constant()`
- `php_sample4_stream_is_fifo()`
- `php_sample6_fopen_read_ucase()`
- `php_sample6_get_homepage()`
- `php_sample_print_var_hash()`
- `php_set_error_handling()`
- `php_set_cookie()`
- `PHP_SHA1Final()`
- `PHP_SHA1Init()`
- `PHP_SHA1Update()`
- `php_srand()`
- `php_start_implicit_flush()`
- `php_start_ob_buffer()`
- `php_start_ob_buffer_named()`
- `php_stat()`
- `php_str_to_str()`
- `php_str_to_str_ex()`
- `php_strcspn()`
- `php_stream_alloc()`
- `php_stream_bucket_addref()`
- `php_stream_bucket_append()` (2nd)
- `php_stream_bucket_delref()` (2nd)
- `php_stream_bucket_make_writeable()` (2nd)
- `php_stream_bucket_new()` (2nd)
- `php_stream_bucket_prepend()` (2nd)
- `php_stream_bucket_split()` (2nd)
- `php_stream_bucket_unlink()` (2nd)
- `php_stream_can_cast()`
- `php_stream_cast()`
- `php_stream_close()` (2nd, 3rd)
- `php_stream_context_alloc()` (2nd)
- `php_stream_context_free()`
- `php_stream_context_from_zval()`
- `php_stream_context_get_option()` (2nd)
- `php_stream_context_set()`
- `php_stream_context_set_option()` (2nd)
- `php_stream_copy_to_mem()`
- `php_stream_copy_to_stream()`
- `php_stream_dirent_alphasort()`
- `php_stream_dirent_alphasortr()`
- `php_stream_eof()`
- `php_stream_filter_alloc()`
- `php_stream_filter_append()` (2nd)
- `php_stream_filter_create()` (2nd)
- `php_stream_filter_flush()`
- `php_stream_filter_free()`
- `php_stream_filter_prepend()` (2nd)
- `php_stream_filter_register_factory()` (2nd)
- `php_stream_filter_remove()`
- `php_stream_filter_unregister_factory()` (2nd)
- `php_stream_filter_unregister_factory_volatile()`
- `php_stream_flush()`
- `php_stream_fopen()`
- `php_stream_fopen_from_fd()` (2nd)
- `php_stream_fopen_from_file()` (2nd)
- `php_stream_fopen_from_pipe()` (2nd)
- `php_stream_fopen_temporary_file()`
- `php_stream_fopen_tmpfile()`
- `php_stream_fopen_with_path()`

- `php_stream_free()`
- `php_stream_from_persistent_id()`
- `php_stream_from_zval()`
- `php_stream_from_zval_no_verify()`
- `php_stream_get_line()`
- `php_stream_get_record()`
- `php_stream_get_url_stream_wrappers_hash()`
- `php_stream_get_url_stream_wrappers_hash_global()`
- `php_stream_getc()`
- `php_stream_gets()`
- `php_stream_is()`
- `php_stream_is_persistent()`
- `php_stream_locate_url_wrapper()`
- `php_stream_make_seekable()`
- `php_stream_mkdir()`
- `php_stream_mmap_possible()`
- `php_stream_mmap_range()`
- `php_stream_mmap_supported()`
- `php_stream_mmap_unmap()`
- `php_stream_notification_alloc()`
- `php_stream_notification_free()`
- `php_stream_notification_func()`
- `php_stream_notification_notify()`
- `php_stream_open_wrapper()`
- `php_stream_open_wrapper_as_file()`
- `php_stream_open_wrapper_ex()`
- `php_stream_opendir()`
- `php_stream_passthru()`
- `php_stream_pclose()`
- `php_stream_printf()`
- `php_stream_putc()`
- `php_stream_puts()`
- `php_stream_read()`
- `php_stream_readdir()`
- `php_stream_rewind()`
- `php_stream_rewinddir()`
- `php_stream_rmdir()`
- `php_stream_scandir()`
- `php_stream_seek()`
- `php_stream_set_option()`
- `php_stream_sock_open_from_socket()`
- `php_stream_stat()`
- `php_stream_stat_path()`
- `php_stream_stat_path_ex()`
- `php_stream_tell()`
- `php_stream_temp_create()`
- `php_stream_temp_open()`
- `php_stream_to_zval()`
- `php_stream_truncate_set_size()`
- `php_stream_wrapper_log_error()`
- `php_stream_write()`
- `php_stream_write_string()`
- `php_stream_xport_accept()`
- `php_stream_xport_bind()`
- `php_stream_xport_connect()`
- `php_stream_xport_create()`
- `php_stream_xport_crypto_enable()`
- `php_stream_xport_crypto_setup()`
- `php_stream_xport_get_hash()`
- `php_stream_xport_get_name()`
- `php_stream_xport_listen()`
- `php_stream_xport_recvfrom()`
- `php_stream_xport_register()`
- `php_stream_xport_sendto()`
- `php_stream_xport_unregister()`
- `php_stream_strip_tags()`
- `php_stream_strip_url()`
- `php_stream_strip_slashes()`
- `php_stream_stripslashes()`
- `php_stream_istr()`
- `php_stream_strspn()`
- `php_stream_strtok_r()`
- `php_stream_strtolower()`
- `php_stream_strtoupper()`
- `php_stream_strtr()`
- `php_stream_trim()`
- `php_stream_unescape_html_entities()`
- `php_stream_unregister_info_logo()`
- `php_stream_unregister_url_stream_wrapper()`
- `php_stream_unregister_url_stream_wrapper_volatile()`
- `php_url_decode()`
- `php_url_encode()`
- `php_url_encode_hash_ex()`
- `php_url_parse()`
- `php_url_parse_ex()`
- `php_uudecode()`
- `php_uuencode()`
- `php_var_serialize()`
- `php_var_unserialize()`
- `php_varstream_closedir()`
- `php_varstream_dirseek()`
- `php_varstream_mkdir()`
- `php_varstream_readdir()`
- `php_varstream_rename()`
- `php_varstream_rmdir()`
- `php_varstream_unlink()`
- `php_verror()`
- `php_version_compare()`
- `php_write()`
- `php_zlib_read()`
- `PHPWRITE()`
- `prev()`
- `prototypes, generating`
- `read()`
- `rename()`
- `reset()`

从查看返回值返回值。

- `rmdir()`
- `safe_emalloc()`
- `safe_pemalloc()`
- `smart_str_0()`
- `smart_str_append_long()`
- `smart_str_append_off_t()`
- `smart_str_append_unsigned()`
- `smart_str_appendc()`
- `smart_str_appendl()`
- `smart_str_appends()`
- `smart_str_free()`
- `spprintf()`
- `startup_php()`
- `stat()`
- `stream_closer()`
- `stream_context_set_option()`
- `stream_opener()`
- `stream_stat()`
- `strnatcmp_ex()`
- `ts_allocate_id()`
- `ub_write()`
- `unlink()`
- `unset()`
- `url_stat()`
- 用户态函数，调用（第 2, 第 3 次）
- `var_dump()`
- `volatile()`
- `vsrintf()`

#### Zend 内部函数

- `zend_alter_ini_entry()`（第 2 次）
- `zend_bailout()`
- `zend_class_implements()`
- `zend_copy_parameters_array()`
- `zend_declare_class_constant()`
- `zend_declare_class_constant_bool()`
- `zend_declare_class_constant_double()`
- `zend_declare_class_constant_long()`
- `zend_declare_class_constant_string()`
- `zend_declare_class_constant_stringl()`
- `zend_declare_property()`
- `zend_declare_property_bool()`
- `zend_declare_property_double()`
- `zend_declare_property_ex()`
- `zend_declare_property_long()`
- `zend_declare_property_null()`
- `zend_declare_property_string()`
- `zend_declare_property_stringl()`
- `zend_disable_class()`
- `zend_disable_function()`
- `zend_eval_string()`（第 2 次）
- `zend_eval_string_ex()`
- `zend_exception_get_default()`
- `zend_execute_scripts()`
- `zend_fetch_class()`
- `zend_fetch_list_dtor_id()`
- `zend_fetch_resource()`（第 2, 第 3 次）
- `zend_get_class_entry()`
- `zend_get_constant()`
- `zend_get_error_exception()`
- `zend_get_hash_value()`
- `zend_get_module_version()`
- `zend_get_object_classname()`
- `zend_get_parameters()`
- `zend_get_parameters_array()`
- `zend_get_parameters_array_ex()`（第 2 次）
- `zend_get_parameters_ex()`（第 2 次）
- `zend_get_std_object_handlers()`
- `zend_hash_add()`（第 2 次）
- `zend_hash_apply()`（第 2 次）
- `zend_hash_apply_with_argument()`（第 2 次）
- `zend_hash_apply_with_arguments()`（第 2 次）
- `zend_hash_clean()`（第 2 次）
- `zend_hash_compare()`（第 2 次）
- `zend_hash_copy()`（第 2 次）
- `zend_hash_del()`（第 2 次）
- `zend_hash_destroy()`（第 2 次）
- `zend_hash_exists()`（第 2 次）
- `zend_hash_find()`（第 2 次）
- `zend_hash_func()`
- `zend_hash_get_current_data_ex()`
- `zend_hash_get_current_key()`
- `zend_hash_get_current_key_ex()`（第 2 次）
- `zend_hash_get_current_key_type_ex()`
- `zend_hash_graceful_destroy()`
- `zend_hash_index_del()`（第 2 次）
- `zend_hash_index_exists()`（第 2 次）
- `zend_hash_index_find()`（第 2 次）
- `zend_hash_index_update()`（第 2 次）
- `zend_hash_init()`（第 2 次）
- `zend_hash_init_ex()`
- `zend_hash_internal_pointer_end()`
- `zend_hash_internal_pointer_reset_ex()`
- `zend_hash_merge()`（第 2 次）
- `zend_hash_merge_ex()`（第 2 次）
- `zend_hash_minmax()`（第 2 次）
- `zend_hash_move_backwards_ex()`
- `zend_hash_move_forward_ex()`
- `zend_hash_next_free_element()`（第 2 次）
- `zend_hash_next_index_insert()`
- `zend_hash_next_insert()`
- `zend_hash_num_elements()`
- `zend_hash_quick_add()`（第 2 次）
- `zend_hash_quick_exists()`（第 2 次）

- `zend_hash_quick_find()` 第 2 次
- `zend_hash_quick_update()` 第 2 次
- `zend_hash_reverse_apply()`
- `zend_hash_sort()` 第 2 次
- `zend_hash_update()` 第 2 次
- `zend_hash_update_current_key_ex()`
- `zend_ini_double()`
- `zend_ini_long()`
- `zend_ini_string()`
- `zend_is_callable()`
- `zend_is_callable_ex()`
- `zend_is_true()`
- `zend_list_addref()`
- `zend_list_delete()` 第 2 次
- `zend_list_find()` 第 2 次
- `zend_list_insert()`
- `zend_llist_add_element()`
- `zend_llist_apply()`
- `zend_llist_apply_with_argument()`
- `zend_llist_apply_with_arguments()`
- `zend_llist_apply_with_del()`
- `zend_llist_clean()`
- `zend_llist_copy()`
- `zend_llist_count()`
- `zend_llist_del_element()`
- `zend_llist_destroy()`
- `zend_llist_get_first_ex()`
- `zend_llist_get_last_ex()`
- `zend_llist_get_next_ex()`
- `zend_llist_get_prev_ex()`
- `zend_llist_init()`
- `zend_llist_prepend_element()`
- `zend_llist_remove_tail()`
- `zend_llist_sort()`
- `zend_lookup_class()`
- `zend_lookup_class_ex()`
- `zend_make_callable()`
- `zend_mangle_property_name()` 第 2 次
- `zend_object_store_get_object()`
- `objects_get_address()`
- `zend_parse_method()`
- `zend_parse_method_ex()`
- `zend_parse_parameters()` 第 2 次 第 3 次
- `zend_q()`
- `zend_read_property()`
- `zend_read_static()`
- `zend_register_global()` 第 2 次
- `zend_register_double()`
- `zend_register_long()`
- `zend_register_class()` 第 2 次
- `zend_register_internal()`
- `zend_register_internal_ex()`
- `zend_register_list_destruct()`
- `zend_register_list_destruct_ex()`
- `zend_register_resource()`
- `zend_register_string()`
- `zend_restore_ini()`
- `zend_set_memory_limit()`
- `zend_set_timeout()`
- `zend_strnd()`
- `zend_throw_error()`
- `zend_throw_exception()`
- `zend_throw_exception_ex()`
- `zend_throw_exception_object()`
- `zend_unset_timeout()`
- `zend_update_property()`
- `zend_update_property_bool()`
- `zend_update_property_double()`
- `zend_update_property_long()`
- `zend_update_property()`
- `zend_update_property()`
- `zend_zval_type()`
- `zval_addref()`
- `zval_copy()`
- `zval_dtor()`
- `zval_ptr_dtor()`

## Index

A B C D E F G H I K L M N O P Q R S T U V W X Z

### gcc (GNU Compiler Collection)

gcc (GNU Compiler Collection)

### gcc version

gcc version

### get_class_name() handler

`get_class_name()` handler

### get_var_and_separate() function

`get_var_and_separate()` function

### get_zend_version() function

`get_zend_version()` function

符号 A B C D E F G H I K L M N O P Q R S T U V W X Z

处理器 另另阅 [函数, 声明; 宏, OBJCE; 方法, 析函数。]

- `add_ref()`
- `call_method()`
- `cast_object()`
- `compare_objects()`
- `count_elements()`
- 自定义处理器
- `del_ref()`
- `get_class_name()`
- `has_dimension()`
- `has_property()`
- `HashTable*get_properties()`
- 标准处理器
- `union_zend_function*get_constructor()`
- `union_zend_function*get_method()`
- `unset_property()`
- `zend_class_entry*get_class_entry()`
- `zend_object_value_clone()`
- `zval**get_property_ptr_ptr()`
- `zval*get()`
- `zval*read_dimension()`
- `zval*read_property()`
- `has_dimension()` 处理器
- `has_property()` 处理器
- hash apply
- 哈希表
- 更改键/索引
- 复制
- 创建 第二个
- ...的定义
- 从...中删除元素
- 确定键的类型
- 清空
- 在...中获取元素
- 在...中检查元素
- 遍历...
- 填充
- 排序
- 遍历
- Zend API 调用
- `HASH_KEY_IS_LONG` 常量
- `HASH_KEY_IS_STRING` 常量
- `HASH_KEY_NON_EXISTANT` 常量
- `HASH_OF()` 宏
- `HashTable*get_properties()` 处理器
- 哈希表 查看 [哈希表]
- header.h
- 头部
- 头部, PECL_Gen
- 头部, 扫描...
- header.h

### 索引

SYMBOL A B C D E F G H I K L M N O P Q R S T U V W X Z

I/O 另阅 [函数, 声明; 宏, OBJCE; 方法, 析函数。]

- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径 第二个
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径
- I/O 路径

哈希表 [查看 [哈希表]
I/O 路径
I/O 路径
I/O 路径
I/O 路径
I/O 路径

SYMBOL A B C D E F G H I K L M N O P Q R S T U V W X Z

## `key()` 函数

#### 关键字

- `return`
- `static`

### 索引

符号 A B C D E F G H I K L M N O P Q R S T U V W X Z

### leaks (内存)

### 库

- 外部库
    - linking
    - testing
- 查找
    - optional functionality
    - scanning for headers
    - testing actual behavior
    - testing for functionality
- PECL (PHP 扩展代码库)
- PECL_Gen
- third-party libraries, linking against

### life cycles 2nd

- CLI
- constants
- embed
- 扩展全局变量
    - accessing
    - declaring
    - per-thread initialization and shutdown
- extension life cycle methods
- hash tables
- MINFO (模块信息) method
- module cycle
- multiprocess
- multithreaded
- request cycle
- 文件
    - `config.m4`
    - `php_sample.h`
    - `sample4.c`
- thread cycle
- 用户态全局变量
    - `auto_global_callback`
    - declaring

### LINK flag (php_stream_path_ex())

### linked lists

- adding elements to
- copying elements in
- finding number of elements in
- initializing
- iterating through
- manually stepping through
- removing elements from
- sorting
- Zend API calls

- linking 另见 lists.
- autoconf
- external libraries
- 库
    - optional functionality
    - scanning for headers
    - testing actual behavior
    - testing for functionality
- 模块依赖
    - configure time dependency
    - runtime dependency
- third-party libraries, linking against
- Windows config.w3 file

### listening to transport streams

#### 列表

- linked lists
    - adding elements to
    - copying elements in
    - finding number of elements in
    - initializing
    - iterating through
    - manually stepping through
    - removing elements from
    - sorting
    - Zend API calls
    - registering
    - Zend API calls
- liveness checking
- loading extensions
- log_message callback
- logos, declaring
- long-term registration (resources)
- longjmp()
- lookups
- loose typing

### 索引

符号 A B C D E F G H I K L M N O P Q R S T U V W X Z

- macros 另见 functions, declaring; handlers, add_ref; methods, dtor.
- `AC_DEFINE`
- `AC_MSG_ERROR`
- `AC_MSG_WARNING`
- `AC_TRY_RUN`
- `ADD_EXTENSION_DEP`
- `ALLOC_HASHTABLE`
- `ARG_ENABLE`
- `ARG_WITH`
- `CG`
- `CHECK_LIB`
- `DEFINE`
- `EG`
- `ERROR`
- `EXTENSION`
- `FG`
- `INIT_CLASS_ENTRY` 第 2 版
- `INIT_OVERLOADED_CLASS_ENTRY`
- `INIT_OVERLOADED_CLASS_ENTRY_EX`
- `OBJ_HANDLE`
- `OBJ_HANDLER`
- `OBJ_HT`
- `OBJCE`
- `OBJPROP`
- `PG`
- `PHP_ABSTRACT_ME` 第 2 版
- `PHP_ADD_EXTENSION_DEP`
- `PHP_ARG_ENABLE` 第 2 版
- `PHP_ARG_WITH` 第 2 版 第 3 版
- `PHP_CHECK_LIBRARY` 第 2 版

### 索引

- `PHP_EMBED_END_BLOCK()` (第 2)
- INI 选项，覆盖
- 初始变量，设置
- 全局变量，声明
- `PHP_EMBED_START_BLOCK()` (第 2)
- INI 选项，覆盖
- 初始变量，设置
- 全局变量，声明
- `PHP_FALIAS()`
- `PHP_FE()`
- `PHP_FUNCTION()`
- `PHP_INI_BEIGN()`
- `PHP_INI_DISP()`
- `PHP_INI_END()`
- `PHP_INI_ENTRY()` (第 2)
- `PHP_MD5Final()`
- `PHP_MD5Init()`
- `PHP_MD5Update()`
- `PHP_ME()`
- `PHP_ME_MAPPING()`
- `PHP_METHOD()`
- `PHP_MINFO_FUNCTION()` (第 2)
- `PHP_MINIT_FUNCTION()` (第 2, 第 3, 第 4)
- `PHP_MSHUTDOWN_FUNCTION()` (第 2, 第 3)
- `PHP_NAMED_FE()`
- `PHP_NEW_EXTENSION()`
- `PHP_RINIT_FUNCTION()`
- `PHP_RSHUTDOWN_FUNCTION()`
- `PHP_VAR_SERIALIZE_DESTROY()`
- `PHP_VAR_SERIALIZE_INIT()`
- `PHP_VAR_UNSERIALIZE_DESTROY()`
- `PHP_VAR_UNSERIALIZE_INIT()`
- `PHPWRITE()`
- `REGISTER_CONSTANT()`
- `REGISTER_INI_ENTRIES()`
- `return_value` 变量
- `SEPARATE_ZVAL()`
- `STD_PHP_INI_ENTRY()`
- `STD_PHP_INI_ENTRY_EX()`
- `TSRMG()`
- `UNREGISTER_INI_ENTRIES()`
- `WARNING()`
- `Z_OBJ()`
- `Z_OBJPROP()`
- `ZEND_BEGIN_MODULE_GLOBALS()`
- `ZEND_END_MODULE_GLOBALS()`
- `ZEND_FETCH_RESOURCE()`
- `ZEND_FETCH_RESOURCE2()`
- `ZEND_INI_MH()`
- `ZEND_NUM_ARGS()`
- `ZEND_VERIFY_RESOURCE()`

### 魔法方法

- 邮件列表
- `make` 命令 (第 2)
- `make_digest()` 函数 (第 2)
- `MAKE_STD_ZVAL()` 宏 (第 2)
- makefiles
- `malloc()` 函数
- 手动初始化 PHP
- 手动遍历链表

### 映射

- 数组到字符串向量
- 流到内存
- 最大值，查找
- MD5 摘要操作
- `md5()` 函数
- `md5.h`

### 内存管理 (第 2, 第 3)

- 写时复制
- 写时复制
- 错误处理
- 释放内存
- 将流映射到内存
- 内存泄漏
- opcode 缓存
- 持久资源
- 引用计数
- 分离
- Zend API
- ZendMM (Zend 内存管理)
- 分配器函数
- `memory_limit` (php.ini)
- 持久性分配
- `memory_limit` (php.ini)

### 合并哈表

- 消息摘要，计算

### 方法

(另参见 `functions, declaring`, `handlers, add_ref()`, `macros, OBJCE`)

- `__call()`
- `__clone()`
- `__construct()`
- `__destruct()`
- `__get()`
- `__isset()`
- `__set()`
- `__toString()`
- `__unset()`
- 声明 (第 2)
- dtor
- 魔法方法
- MINFO (模块信息)
- MSHUTDOWN
- OnUpdateStringUnempty

### MINFO (模块信息) 方法

- 最小扩展骨架代码
- 最小值，查找
- MINIT (模块初始化) 方法
- `mkdir()` 函数
- 修改事件 (INI 设置)
- 模块周期
- 模块信息 (MINFO) 方法
- 模块初始化 (MINIT) 方法
- 模块关闭 (MSHUTDOWN) 方法 (第 2)

### 模块

- 声明
- 依赖，强制
- 配置时间模块依赖
- 运行时模块依赖
- 共享模块，加载
- 模块关闭 (MSHUTDOWN) 方法 (第 2)
- 多进程模型
- 多线程生命周期
- `MYEXT_G()` 宏
- `myext_samplefunc()` 函数

SYMBOL A B C D E F G H I K L M N O P Q R S T U V W X Z

### 命名函数

### next() 函数

### nmake 命令

### 非线程构建

### 通知器

### NULL 参数 (zend_parse_parameters() 函数)

### 索引

SYMBOL A B C D E F G H I K L M N O P Q R S T U V W X Z

### OBJ_HANDLE 宏

### OBJ_HANDLER 宏

### OBJ_HT 宏

### OBJCE 宏

### object_and_properties_init() 函数

### object_init() 函数

### object_init_ex() 函数 第 2 次

### 对象 另见 [属性]

- 声明
- 实例化
- 名称，检索
- 接受
- 类构造函数
- 类声明
- 类继承
- 类初始化
- 类注册
- PHP 对象类型的演进
- 实例化 第 2 次
- 方法实现
- 属性
- 样本代码文件
- PHP5 对象 第 2 次
- 常量
- 处理器
- 接口
- 方法
- 属性
- `zend_class_entry`
- 检索指针
- Zend API 调用

### OBJPROP 宏

### OnUpdateString 方法

### 透明结构

### opcode 缓存

### open based

### Open Source 项目

- PECL (PHP Extension Library)
- PHP 源码树

### opendir() 函数 第 2 次

#### 打开

- 目录
- 流
- 目录访问
- `fopen()` 函数
- 特殊流类型
- 传输层
- 运算符
- 选项 (`php_stream_create()`)

#### 输出

- 检查 PHP 源码
- 捕获输出
- 缓冲输出
- `log_message` 回调
- `sapi_error`
- 标准输出
- 生成缓冲区
- 复制
- 结束
- 刷新
- 隐式刷新模式
- 初始化
- PHPAPI 调用

#### 覆盖

- 默认 php.ini 文件
- 嵌入启动
- INI 选项

### 索引

SYMBOL A B C D E F G H I K L M N O P Q R S T U V W X Z

### package.xml 文件

### 参数

- 使用 `zend_parse_parameters()` 进行自动类型转换
- 数据类型
- 强制分离
- IS_NULL 与 NULL
- 修饰符
- 可选
- 规格器
- 检索
- 类型提示
- `zend_parameters_ex()`

#### 传递

- 传递
- 第 2 次
- 引用传递
- 调用时传递
- 编译时传递
- `pealloc()`
- 第 2 次

#### PECL (PHP Extension Library)

- 扩展
- pecl 开发列表

#### PECL 扩展

- 常量
- 依赖项
- 函数
- 自定义代码
- 内部
- 公共
- 全局变量
- INI 选项
- `package.xml` 文件
- `specfile.xml` 文件

#### pefree() 和 pemalloc()

- `pefree()`
- `pemalloc()`
- 第 2 次

#### 每线程初始化和关闭

- 每线程初始化和关闭
- PERDIR 访问 (INI 设置)
- `perealloc()` 函数 第 2 次

#### PERSISTENT 标记

- PERSISTENT 标记 (`php_stream_free()` 函数)
- 持久性资源
- 延迟销毁
- 提前退出
- 活跃检查
- 长期注册

### 内存分配

- 第二部分
- 检索
- 重用

# persistent_id 参数 (`php_stream_xport_create()` 函数)

# `pestrdup()` 函数

- 第二部分

# `PG()` 宏

# PHP 编译

- *nix* 工具
- `./configure` 选项
- 编译 PHP
  - 在 UNIX 上
  - 在 Win32 上
- CVS 检
- 获取 PHP 源代码
- Win32 工具

# PHP 配置

# PHP 扩展代码库 (PECL)

# PHP 初始化

# PHP 邮件列表

# PHP 源码树

## php.ini 设置

- 访问级别
- 绑定到扩展全局变量
- 声明
- 这里的
- `memory_limit` 设置
- 修改事件
- 覆盖

## PHP4 类

- 构造函数
- 声明
- PHP 对象类型的演进
- 继承
- 初始化
- 实例
  - 接收
  - 创建
  - 属性
  - 方法实现
  - 注册
  - 示例文件
    - `config.m4` 文件
    - `php_sample2.c` 文件
    - `php_sample2.h` 文件

## PHP5 类

- 常量
- 处理器
  - 自定义处理器
  - 标准处理器

## 接口

- 声明
- 实现
- 方法
- 声明
- 魔术方法
- 属性
- `zend_class_entry`

# `PHP_ABSTRACT_ME()` 宏

- 第二部分

# `PHP_ADD_EXTENSION_DEP()` 宏

# `php_add_tick_function()` 函数

# `php_addcslashes()` 函数

# `php_addslashes()` 函数

- 第二部分

# `php_addslashes_ex()` 函数

# `PHP_ARG_ENABLE()` 宏

- 第二部分

# `PHP_ARG_WITH()` 宏

- 第二部分
- 第三部分

# `php_asctime_r()` 函数

# `php_base64_decode()` 函数

# `php_base64_encode()` 函数

# `php_basename()` 函数

# `php_char_to_str()` 函数

# `php_char_to_str_ex()` 函数

# `PHP_CHECK_LIBRARY()` 宏

- 第二部分

# `php_check_open_basedir()` 函数

# `php_check_open_basedir_ex()` 函数

# `php_check_uid()` 函数

# `php_check_uid_ex()` 函数

# `php_cookbook.h`

# `php_cookbook_resource_dt()` 函数

# `php_copy_file()` 函数

# `php_ctime_r()` 函数

# `php_dirname()` 函数

# `PHP_EMBED_END_BLOCK()` 宏

- 第二部分
  - INI 选项
  - 初始变量
  - 全局变量

# `php_embed_init()` 函数

# `php_embed_log_message()` 函数

# `php_embed_shutdown()` 函数

# `PHP_EMBED_START_BLOCK()` 宏

- 第二部分
  - INI 选项
  - 初始变量
  - 全局变量

# `php_end_implicit_flush()` 函数

# `php_end_ob_buffer()` 函数

# `php_end_ob_buffers()` 函数

# `php_error()` 函数

# `php_error_docref()` 函数

- 第二部分

# `php_error_docref0()` 函数

# `php_error_docref1()` 函数

# `php_error_docref2()` 函数

# `php_escape_html_entities()` 函数

# `php_escape_shell_arg()` 函数

# `php_escape_shell_cmd()` 函数

# `php_execute_script()` 函数

# `php_explode()` 函数

# `PHP_FALIAS()` 宏

# `PHP_FE()` 宏

- 第二部分

# `php_file_le_pstream()` 函数

# `php_file_le_stream()` 函数

# `php_file_le_stream_filter()` 函数

# `php_filestat`

# `php_flock()` 函数

# `PHP_FNAME()` 宏

# `PHP_FUNCTION()` 宏

- 第二部分
- 第三部分

# `php_get_current_user()` 函数

# `php_get_output_start_filename()` 函数

# `php_get_output_start_lineno()` 函数

# `php_get_stream_filters_hash()` 函数

# `php_get_stream_filters_hash_global()` 函数

# `php_gmtime_r()` 函数

# `php_html_puts()` 函数

# `php_http.h`

# `php_implode()` 函数

# `php_info_html_esc()` 函数

# `php_info_print_box_end()` 函数

# `php_info_print_box_start()` 函数

- 第二部分

# `php_info_print_hr()` 函数

- 第二部分

# `php_info_print_style()` 函数

- `php_info_print_table_colspan_header()` 函数
- `php_info_print_table_end()` 函数
- `php_info_print_table_header()` 函数 (第 2)
- `php_info_print_table_row()` 函数 (第 2)
- `php_info_print_table_row_ex()` 函数
- `php_info_print_table_start()` 函数 (第 2)
- `PHP_INI_BEIGN()` 宏
- `PHP_INI_DISP()` 宏
- `PHP_INI_END()` 宏
- `PHP_INI_ENTRY()` 宏 (第 2)
- `php_is_url()` 函数
- `php_le_stream_context()` 函数
- `php_lint_script()` 函数
- `php_log_err()` 函数
- `php_logo_guid()` 函数
- `php_mail()` 函数
- `php_mail.h`
- `php_math.h`
- `php_math_number_format()` 函数
- `PHP_MD5Final()` 宏
- `PHP_MD5Init()` 宏
- `PHP_MD5Update()` 宏
- `PHP_ME()` 宏
- `PHP_ME_MAPPING()` 宏
- `PHP_METHOD()` 宏
- `PHP_MINFO_FUNCTION()` 宏 (第 2)
- `PHP_MINIT_FUNCTION()` 函数
- `PHP_MINIT_FUNCTION()` 宏 (第 2, 第 3, 第 4)
- `PHP_MSHUTDOWN_FUNCTION()` 宏 (第 2, 第 3)
- `php_mt_rand()` 函数
- `php_mt_srand()` 函数
- `PHP_NAMED_FE()` 函数
- `PHP_NAMED_FE()` 宏 (第 2)
- `PHP_NAMED_FUNCTION()` 宏
- `PHP_NEW_EXTENSION()` 宏 (第 2)
- `php_ob_get_buffer()` 函数
- `php_ob_get_length()` 函数
- `php_print_info()` 函数
- `php_print_info_head()` 函数
- `php_printf()` 函数 (第 2, 第 3)
- `php_rand()` 函数
- `php_rand.h`
- `php_rand_r()` 函数
- `php_raw_url_decode()` 函数
- `php_raw_url_encode()` 函数
- `php_reg_replace()` 函数
- `php_register_extension()` 函数
- `php_register_extensions()` 函数
- `php_register_info_logo()` 函数
- `php_register_url_stream()` 函数
- `php_register_url_stream_volatile()` 函数
- `php_remove_tick_function()`
- `php_request_shutdown()` 函数
- `php_request_startup()` 函数
- `PHP_RINIT_FUNCTION()` 宏
- `PHP_RSHUTDOWN_FUNCTION()` 宏
- `php_sample2.h`
- `php_sample4.h`
- `php_sample4_fd_is_fifo()` 函数
- `php_sample4_register_constant()` 函数
- `php_sample4_stream_is_fifo()` 函数
- `php_sample6_fopen_read_ucase()` 函数
- `php_sample6_get_homepage()` 函数
- `php_sample_byref_arginfo` 结构体
- `php_sample_functions` 结构体 (第 2)
- `php_sample_print_var_hash()` 函数
- `php_sample_print_var_hash()` 函数
- `php_set_error_handling()` 函数
- `php_set_cookie()` 函数
- `PHP_SHA1Final()` 函数
- `PHP_SHA1Init()` 函数
- `PHP_SHA1Update()` 函数
- `php_smart_str.h`
- `php_srand()` 函数
- `php_start_implicit_flush()` 函数
- `php_start_ob_buffer()` 函数
- `php_start_ob_buffer_named()` 函数
- `php_stat()` 函数
- `php_str_to_str()` 函数
- `php_str_to_str_ex()` 函数
- `php_strcspn()` 函数
- `php_stream` 结构体
- `php_stream_alloc()` 函数
- `php_stream_bucket_addref()` 函数
- `php_stream_bucket_append()` 函数 (第 2)
- `php_stream_bucket_delref()` 函数 (第 2)
- `php_stream_bucket_make_writeable()` 函数 (第 2)
- `php_stream_bucket_new()` 函数 (第 2)
- `php_stream_bucket_prepend()` 函数 (第 2)
- `php_stream_bucket_split()` 函数 (第 2)
- `php_stream_bucket_unlink()` 函数 (第 2)
- `php_stream_can_cast()` 函数
- `php_stream_cast()` 函数
- `php_stream_close()` 函数 (第 2, 第 3)
- `php_stream_context_alloc()` 函数 (第 2)
- `php_stream_context_free()` 函数
- `php_stream_context_from_zval()` 函数
- `php_stream_context_get_option()` 函数 (第 2)
- `php_stream_context_set()` 函数
- `php_stream_context_set_option()` 函数 (第 2)
- `php_stream_copy_to_mem()` 函数
- `php_stream_copy_to_stream()` 函数
- `php_stream_dirent_alphasort()` 函数
- `php_stream_dirent_alphasortr()` 函数
- `php_stream_eof()` 函数
- `php_stream_filter_alloc()` 函数

- `php_stream_filter_append()` function (2nd)
- `php_stream_filter_create()` function (2nd)
- `php_stream_filter_flush()` function
- `php_stream_filter_free()` function
- `php_stream_filter_prepend()` function (2nd)
- `php_stream_filter_register_factory()` function (2nd)
- `php_stream_filter_register_factory_volatile()` function
- `php_stream_filter_remove()` function
- `php_stream_filter_unregister_factory()` function (2nd)
- `php_stream_filter_unregister_factory_volatile()` function
- `php_stream_flush()` function (2nd)
- `php_stream_fopen()` function
- `php_stream_fopen_from_fd()` function (2nd)
- `php_stream_fopen_from_file()` function (2nd)
- `php_stream_fopen_from_pipe()` function (2nd)
- `php_stream_fopen_temporary_file()` function
- `php_stream_fopen_tmpfile()` function
- `php_stream_fopen_with_path()` function
- `php_stream_free()` function (2nd)
- `php_stream_from_persistent_id()` function
- `php_stream_from_zval()` function (2nd)
- `php_stream_from_zval_no_verify()` function (2nd)
- `php_stream_get_line` view
- `php_stream_get_line()` function (2nd)
- `php_stream_get_record()` function (2nd)
- `php_stream_get_url_stream_wrappers_hash()` function
- `php_stream_get_url_stream_wrappers_hash_global()` function
- `php_stream_getc()` function (2nd)
- `php_stream_gets()` function (2nd)
- `php_stream_is()` function
- `php_stream_is_persistent()` function (2nd)
- `php_stream_locate_wrapper()` function
- `php_stream_make_seekable()` function
- `php_stream_mkdir()` function (2nd)
- `php_stream_mmap_possible()` function
- `php_stream_mmap_range()` function
- `php_stream_mmap_supported()` function
- `php_stream_mmap_unmap()` function
- `php_stream_notification_alloc()` function
- `php_stream_notification_free()` function
- `php_stream_notification_func()` function
- `php_stream_notify()` function
- `php_stream_notifier` struct
- `PHP_STREAM_NOTIFY_AUTH_REQUIRED` code
- `PHP_STREAM_NOTIFY_AUTH_RESULT` code
- `PHP_STREAM_NOTIFY_COMPLETED` code
- `PHP_STREAM_NOTIFY_CONNECT` code
- `PHP_STREAM_NOTIFY_FAILURE` code
- `PHP_STREAM_NOTIFY_FILE_SIZE_IS` code
- `PHP_STREAM_NOTIFY_MIME_TYPE_IS` code
- `PHP_STREAM_NOTIFY_PROGRESS` code
- `PHP_STREAM_NOTIFY_REDIRECTED` code
- `PHP_STREAM_NOTIFY_RESOLVE` code
- `php_stream_open_wrapper()` function (2nd, 3rd)
- `php_stream_open_wrapper_as_file()` function
- `php_stream_open_wrapper_ex()` function
- `php_stream_opendir()` function (2nd)
- `php_stream_ops` struct
- `php_stream_passthru()` function
- `php_stream_pclose()` function (2nd)
- `php_stream_printf()` function (2nd)
- `php_stream_putc()` function (2nd)
- `php_stream_puts()` function (2nd)
- `php_stream_read()` function (2nd, 3rd)
- `php_stream_readdir()` function (2nd)
- `php_stream_rewind()` function (2nd)
- `php_stream_rewinddir()` function (2nd)
- `php_stream_rmdir()` function (2nd)
- `php_stream_scandir()` function
- `php_stream_seek()` function (2nd)
- `php_stream_set_option()` function
- `php_stream_sock_open_from_socket()` function
- `php_stream_stat()` function (2nd)
- `php_stream_stat_path()` function (2nd)
- `php_stream_stat_path_ex()` function
- `php_stream_tell()` function (2nd)
- `php_stream_temp_create()` function
- `php_stream_temp_open()` function
- `php_stream_to_zval()` function (2nd)
- `php_stream_truncate_set_size()` function
- `PHP_STREAM_URL_STAT_LINK` code
- `PHP_STREAM_URL_STAT_QUIET` code
- `php_stream_wrapper_log_error()` function (2nd)
- `php_stream_wrapper_ops` struct
- `php_stream_write()` function (2nd, 3rd)
- `php_stream_write_string()` function (2nd)
- `php_stream_xport_accept()` function
- `php_stream_xport_bind()` function
- `php_stream_xport_connect()` function
- `php_stream_xport_create()` function (2nd)
- `php_stream_xport_crypto_enable()` function

`php_stream_xport_crypto_setup()` function
- `php_stream_xport_get_hash()` function
- `php_stream_xport_get_name()` function
- `php_stream_xport_listen()` function
- `php_stream_xport_recvfrom()` function
- `php_stream_xport_register()` function
- `php_stream_xport_sendto()` function
- `php_stream_xport_unregister()` function
- `php_string.h`
- `php_strip_tags()` function
- `php_strip_url_passwd()` function
- `php_stripcslashes()` function
- `php_stripslashes()` function
- `php_stristr()` function
- `php_strspn()` function
- `php_strtok_r()` function
- `php_strtolower()` function
- `php_toupper()` function
- `php_strtr()` function
- `PHP_SUBST()` macro
- `php_trim()` function
- `php_unescape_html_entities()` function
- `php_unregister_info()` function
- `php_unregister_url_stream()` function
- `php_unregister_url_stream_volatile()` function
- `php_url` structure
- `php_url_decode()` function
- `php_url_encode()` function
- `php_url_encode_hash_ex()` function
- `php_url_parse()` function
- `php_url_parse_ex()` function
- `php_udecode()` function
- `php_uuencode()` function
- `php_uuencode.h`
- `php_var.h`
- `php_var_serialize()` function
- `PHP_VAR_SERIALIZE_DESTROY()` macro
- `PHP_VAR_SERIALIZE_INIT()` macro
- `php_var_unserialize()` function
- `PHP_VAR_SERIALIZE_DESTROY()` macro
- `PHP_VAR_SERIALIZE_INIT()` macro
- `php_varstream.h`
- `php_varstream_closed()` function
- `php_varstream_dirseek()` function
- `php_varstream_mkdir()` function
- `php_varstream_readdir()` function
- `php_varstream_rename()` function
- `php_varstream_rmdir()` function
- `php_varstream_unlink()` function
- `php_verror()` function
- `php_version_compare()` function
- `php_versioning.h`
- `php_write()` function
- `php_zlib_read()` function
- `phpize` program
- `PHPWRITE()` macro
- pipe character (`|`)
- `plainfiles`
- `Platform SDK`

### 指针

- 内部指针，保留
- `tsrm_ls` 指针，查找

### 填充

- 数组
- `HashTables`
- 字符串变量

### `PRESERVE_HANDLE` flag (`php_stream_free()` function)

- `prev()` function
- `printf()` function

### 属性

- 添加
- 声明
- 带有作用域可见性信息的名称
- `PHP4` 属性
- `PHP5` 对象
- 静态属性
- `Zend API` 调用

### 原型（生成）

- 公有函数

### 索引 (符号)

A, B, C, D, E, F, G, H, I, K, L, M, N, O, P, Q, R, S, T, U, V, W, X, Z

### `QUIET` flag (`php_stream_stat_ex()` function)

### 索引 (符号)

A, B, C, D, E, F, G, H, I, K, L, M, N, O, P, Q, R, S, T, U, V, W, X, Z

### 随机数，生成

- `read()` function

#### 读取

- 目录
- 属性
- 流

- `realloc()` function
- 回调 `HashTable` 信息
- 恢复流
- 重入性安全
- 引用计数
- 引用值的返回
- 引用的传递
- 运行时引用传递
- 编译时引用传递

### 引用

- 写时修改
- 写时复制
- 计数
- 分离

### `reg.h`

- `REGISTER_*CONSTANT()` 宏
- `REGISTER_INI_ENTRIES()` 宏

### 注册

- 常量
- 过滤器
- 列表
- `PHP4` 类
- 资源
- 长期注册
    - 重用
- 流过滤器
- 传输流
- `zend_class_entry` 结构

### 正则表达式

- 移除 `HashTable` 元素
- `rename()` function

# `REPORT_ERRORS` (`php_stream_open_wrapper()` 函数)

# 错误报告

# 存储库 (CVS)

### 请求周期

# 请求初始化 (RINIT) 方法

# 请求关闭 (RSHUTDOWN) 方法

# `reset()` 函数

# 资源

#### 声明

### 解码

### 定义

### 延迟销毁

### 销毁

#### 延迟破坏

#### 强制破坏

### 析构函数回调

### 提前退出

### 导出

### 强制销毁

### IRC (互联网实时聊天)

### 活跃检查

### 长期注册

### 内存分配

#### 开源项目

##### PECL (PHP 扩展代码库)

##### PHP 源码树

#### PHP 邮件列表

### 引用计数

#### 注册

#### 第二次

#### 检索

#### 重用

#### Zend API 调用

### 恢复 INI 设置

### 获取参数

### 变量

#### return 关键字

#### `RETURN_LONG()` 宏

#### `return_value_ptr` 变量

#### `return_value_used` 变量

#### 返回值

#### 引用传递

#### 调用时引用传递

#### 编译时引用传递

#### 引用值

#### `return_value_ptr` 变量

#### `return_value_used` 变量

### 重用资源

### RINIT (请求初始化) 方法

### `rmdir()` 函数

### RSHUTDOWN (请求关闭) 方法

### `RSRC_DTOR` 标志 (`php_stream_free()` 函数)

# runkit

# 运行时模块依赖

### 索引

[符号] [A] [B] [C] [D] [E] [F] [G] [H] [I] [K] [L] [M] [N] [O] [P] [Q] [R] [S] [T] [U] [V] [W] [X] [Z]

### 安全模式

### `safe_emalloc()` 函数 第二次

### `safe_pemalloc()` 函数

### sample2.c 文件

### sample4.c 文件

### `sample_array_range()` 函数

### `sample_byref_calltime()` 函数

### `sample_byref_compiletime()` 函数

### `SAMPLE_G()` 宏

### `sample_hello_world()` 函数

#### 全局变量访问

#### 线程

#### `ts_ls` 指针，查找

### 周期

#### CLI

#### 嵌入

#### 多进程

#### 多线程

#### 进程

#### 启动进程

#### 线程安全

#### 线程安全数据

#### 何时不使用线程

### `sapi_error`

### `sapi_module_struct` 结构 第二次

### 扫描头

脚本

#### 回调 PHP

#### 脚本包含的替代方案

#### 调用用户空间函数 第二次 次

## 错误处理

#### 在命令行中包含

#### 超时设置

### `SEEK_CUR` 标志

### `SEEK_END` 标志

### `SEEK_SET` 标志

### 移动流

### 发送

#### cookies

#### 邮件

### `SEPARATE_ZVAL()` 宏

### 分离

### 强制分离

### 将变量序列化为字符串值

### SHA1 摘要操作

### `sha1.h`

### 共享模块，加载

### 进程关闭（另见启动/关闭周期。）

#### MSHUTDOWN (模块关闭) 方法

#### PHPAPI 调用

#### RSHUTDOWN (请求关闭) 方法

### `sizeof()` 函数

### 骨架代码

#### 扩展生命周期

#### 函数声明

#### 最小扩展

#### 模块声明

#### 对象声明

#### 资源声明

#### 资源回调

### `/`

### 智能字符串

### `smart_str_0()` 函数

### `smart_str_append_long()` 函数

### `smart_str_append_off_t()` 函数

### `smart_str_append_unsigned()` 函数

### `smart_str_appendc()` 函数

### `smart_str_appendl()` 函数

### `smart_str_appends()` 函数

### `smart_str_free()` 函数

排序

#### 哈希表 第二次

#### 链表

### 获取源码

### 源码骨架文件

### specfile.xml 文件

# 特殊方法

# 特殊流类型，打开

# `spprintf()` 函数

# 标准 I/O

# START/END 块

# 启动过程 另阅 [启动/关闭周期。]

## 嵌入启动，覆盖

## MINIT (模块初始化) 方法

## PHP 初始化

## PHPAPI 调用

## RINIT (请求初始化) 方法

# 启动/关闭周期 另阅 [生命周期。]

### 常量

### 扩展全局变量

#### 访问

#### 声明

#### 线程线程初始化与关闭

## MINFO (模块信息) 方法

### 模块周期

### 请求周期

## 示例源文件

#### config.m4

#### php\_sample4.h

#### sample4.c

### 线程周期

## 用户态超级全局

#### auto\_global\_callback

#### 声明

# `startup_php()` 函数

# `stat()` 函数

# `static` 关键字

# 静态属性

# 静态流操作

# 静态构建扩展

## 在 *nix 下

## 在 Windows 下

# `std_object_handlers`

# `STD_PHP_INI_ENTRY()` 宏

# `STD_PHP_INI_ENTRY_EX()` 宏

# 在结构中存储数据

### 哈希表

#### 比较元素元素

### 复制与合并

### 创建

#### 定义的

#### 销毁

#### 清空

#### 内部指针，保留

### 通过哈希应用迭代

#### 向前移动迭代

# 生命周期

#### 返回最大/最小值

### 填充

#### 快速填充与召回

#### 从...中召回信息

#### 从...中移除元素

#### 排序

#### zval* Array

#### 链表

#### 变量

#### 向量

# `strdup()` 函数 第 2 部分

# `stream_closer()` 函数

# `stream_context_set_option()` 函数

# `STREAM_DISABLE_OPEN_BASEDIR` (`php_stream_open_wrapper()` 函数)

# `STREAM_MUST_SEEK` (`php_stream_open_wrapper()` function)

# `STREAM_ONLY_GET_HEADERS` (`php_stream_open_wrapper()` function)

# `STREAM_OPEN_PERSISTENT` (`php_stream_open_wrapper()` function)

# `stream_opener()` 函数

# `stream_stat()` 函数

# `STREAM_USE_URL` (`php_stream_open_wrapper()` function)

# `STREAM_WILL_CAST` (`php_stream_open_wrapper()` function)

# `STREAM_XPORT_BIND`

# `STREAM_XPORT_CLIENT`

# `STREAM_XPORT_CONNECT`

# `STREAM_XPORT_CONNECT_ASYNC`

# `STREAM_XPORT_LISTEN`

# `STREAM_XPORT_SERVER`

# 流

## 访问

#### 分配

#### 类型转换

#### 关闭/释放 第 2 部分

#### 上下文 第 2 部分

### 默认上下文

#### 获取选项

### 设置选项

### 参数

### 创建

#### 文件结束

#### 交换 zvals

#### 文件指针，移动移动

### 过滤器

#### 添加/移除

#### 分配

#### 应用

#### 桶

#### 定义

#### 冲刷

#### 释放

#### 实例化

#### 注册/注销

## 冲刷 第 2 部分

## fstat() 和 stat() 风格信息，报告

## 实现 第 2 部分

### 检查

#### `stat()` 函数

#### `url_stat()` 函数

## ioctl() 风格操作

## 使其可寻

## 到内存映射/取消映射

## 通知器

## 打开

### 目录访问

#### `fopen()` 函数

#### 特殊流类型

#### 传输层

# 普通文件和标准 I/O

## 读取 第 2 部分 第 3 部分

## 从...中读取

## 恢复

## 寻址

## 静态流操作

## 流 API [另阅特定函数。]

#### 桶

### 上下文

### 目录访问

#### 过滤器

#### 内部/用户态转换

#### 杂项

#### 通知器

#### 普通文件和标准 I/O

# 流的创建与销毁

# 流 I/O

# 流操作

# 传输层

# 计数

## 传输层

- 绑定资源
- 连接资源
- 无连接发送与接收方法
- 加密
- 端点（套接字）名称
- 实例化
- 监听
- 注册/注销

## URL 包装器，检索

### 包装器操作

- `dir_opener()`
- 实现
- `mkdir()`
- `opendir()`
- `php_varstream_mkdir()`
- `php_varstream_rename()`
- `php_varstream_rmdir()`
- `php_varstream_unlink()`
- `rename()`
- `rmdir()`
- `stream_closer()`
- `stream_opener()`
- `stream_stat()`
- `unlink()`
- URL 解析
- `url_stat()`
- 包装器
- 写入
- 第二 2
- 第 3

## 流 API（参见特定函数）

- 桶 (Buckets)
- 上下文 (Contexts)
- 目录访问
- 过滤器 (Filters)
- 内部/用户态转换
- 杂项
- 通知器 (Notifiers)
- 普通文件与标准 I/O
- 流的创建与销毁
- 流 I/O
- 流操作
- 传输层

## 字符串

- Base64 字符串
- 转换为大写或小写
- 转义字符
- 将分隔符字符串拆分为数组
- 格式化
- 将数组合并为分隔符字符串
- 自然比较
- 填充
- HTML 和 PHP 标签
- 替换字符
- 将变量序列化为字符串值
- 智能字符串
- 字符串向量，将数组映射到
- 将数组转换为 URL 编码字符串
- 修剪
- 反序列化为 PHP 变量
- UU 编码

## 函数

- `strr()`
- `strlen()` 函数
- `strnat_ex()` 函数
- 结构（参见数据类型，定义）
- `arg_info`（参见全局变量）
- 不透明结构
- `php_sample_byref_arginfo`
- `php_sample_functions` (第二 2)
- `php_stream`
- `php_stream_notifier`
- `php_stream_ops`
- `php_stream_wrapper_ops`
- `php_url`
- `sapi_module_struct`
- 在哈希表中存储数据（参见哈表）
- 链表
- 向量

### `zend_class_entry`

- 初始化
- 注册
- `zend_function_entry`
- `zend_ini_entry`
- `zend_module_entry` (第二 2)

### 全局变量

- `auto_global_callback`
- 声明（第二 2）
- `symbol_table` 元素

## 系统访问（INI 设置）

### 索引

[SYMBOL] [A] [B] [C] [D] [E] [F] [G] [H] [I] [K] [L] [M] [N] [O] [P] [Q] [R] [S] [T] [U] [V] [W] [X] [Z]

## 计数（参见哈表）

- 实际行为
- 外部库
- 第三方库
- 线程安全
- 线程初始化与关闭
- 线程安全池
- 何时不使用
- 抛出异常
- Tick 函数
- `php_stream_x_create()` 函数
- 超时设置

`TSRMLS_CC` 指令

`TSRMLS_FETCH()` 宏

类型标志（方法）

类型提示

### 索引

[SYMBOL] [A] [B] [C] [D] [E] [F] [G] [H] [I] [K] [L] [M] [N] [O] [P] [Q] [R] [S] [T] [U] [V] [W] [X] [Z]

`ub_write()` 函数

union `_zend_function *get_constructor()` 处理器

union `_zend_function *get_method()` 处理器

union 结构

在 UNIX 上编译 PHP

Unix-like 环境 参阅 [*nix (Unix-like environments).]

`unlink()` 函数

从内存中取消映射流

`UNREGISTER_INI_ENTRIES()` 宏

`unset()` 函数 第 2

`unset_property()` 处理器

URL 编码字符串，将数组转换为

`url.h`

`url_stat()` 函数 第 2

URLs

- 解码
- 编码
- 解析 第 2

`USE_PATH` 选项（`php_stream_open_wrapper()` 函数）

用户访问（INI 设置）

调用用户空间函数 第 2 第 3

用户空间超全局变量

- `auto_global_callback`
- `declaring`

UU 编码

### 索引

[SYMBOL] [A] [B] [C] [D] [E] [F] [G] [H] [I] [K] [L] [M] [N] [O] [P] [Q] [R] [S] [T] [U] [V] [W] [X] [Z]

V$

返回值

- 按引用传递
- 调用时引用传递 (pass-by-ref)
- 编译时引用传递 (pass-by-ref)
- 引用值
- `return_value_ptr` 变量
- `return_value_used`

`var_dump()` 函数 第 2

变量

- `$_FILE`
- `$_GET`
- `$_POST`
- `$GLOBALS`
- 转换
- 创建
- 数据类型
- 使用 `zend_parse_parameters()` 自动转换
- 确定
- `IS_ARRAY`
- `IS_BOOL`
- `IS_DOUBLE`
- `IS_LONG`
- `IS_NULL`
- `IS_OBJECT`
- `IS_RESOURCE`
- `IS_STRING`
- 类型提示
- 数据值
- 初始变量
- 弱类型
- 获取
- `return_value_ptr`
- `return_value_used`
- 序列化到值
- 存储
- 字符串、填充
- 将值序列化
- Zend API 调用

`varstream.c`

向量

视图, `php_stream_get_line`

可见性标志（方法）

`VLD (Vulcan Decoder)`

`vsprintf()` 函数

`Vulcan Decoder (VLD)`

### 索引

[SYMBOL] [A] [B] [C] [D] [E] [F] [G] [H] [I] [K] [L] [M] [N] [O] [P] [Q] [R] [S] [T] [U] [V] [W] [X] [Z]

`WARNING()` 宏

`win32build.zip` 文件

Windows 系统

- 编译器
- 在 Windows 上编译 PHP
- `config.w32` 文件
- 静态扩展
- 工具

包装器（流） 第 2

- `dir_opener`
- 实现
- `mkdir`
- `opendir` 第 2
- `php_varstream_mkdir`
- `php_varstream_rename`
- `php_varstream_rmdir`
- `php_varstream_unlink`
- `rename`
- `rmdir`
- `closer`
- `opener`
- `stat`
- `unlink`
- URL 解析
- `url_stat()`

写入

- 写时更改
- 写时复制 (copy on write)
- 流 第 2 第 3

`WRONG_PARAM_COUNT` 宏

xport 参数（`php_stream_xport_create()` 函数）

[SYMBOL] [A] [B] [C] [D] [E] [F] [G] [H] [I] [K] [L] [M] [N] [O] [P] [Q] [R] [S] [T] [U] [V] [W] [X] [Z]

- `Z_ARRVAL()` 宏
- `Z_ARRVAL_P()` 宏
- `Z_ARRVAL_PP()` 宏
- `Z_OBJCE()` 宏
- `Z_OBJCE_P()` 宏
- `Z_OBJPROP()` 宏
- `Z_TYPE()` 宏
- `Z_TYPE_P()` 宏
- `Z_TYPE_PP()` 宏

`Zend` 另参 [宏, `OBJCE`; 特定函数。]

- 数组操作
- 类
- 常量
- 异常
- 执行
- 哈表
- INI 设置
- 链列表
- 内存
- 杂项函数
- 对象
- 参数获取
- 属性
- 资源/列表
- 线程安全
    - 线程安全数据池
    - 何时不使用线程
- 变量
- ZendMM (Zend 内存管理)
    - 分配器函数
    - `memory_limit` 设置 (php.ini)
    - 持久分配

`Zend Value` 查看 [`zval` (Zend Value)。]

- `ZEND_ACC_ABSTRACT` 标记
- `ZEND_ACC_FINAL` 标记
- `ZEND_ACC_PRIVATE` 标记
- `ZEND_ACC_PROTECTED` 标记
- `ZEND_ACC_PUBLIC` 标记
- `ZEND_ACC_STATIC` 标记
- `zend_alter_ini_entry()` 函数 [第 2]
- `ZEND_ARG_ARRAY_INFO()` 宏
- `ZEND_ARG_INFO()` 宏
- `ZEND_ARG_OBJ_INFO()` 宏
- `ZEND_ARG_PASS_INFO()` 宏
- `zend_bail_out()` 函数
- `ZEND_BEGIN_ARG_INFO()` 宏 [第 2]
- `ZEND_BEGIN_ARG_INFO_EX()` 宏 [第 2]
- `ZEND_BEGIN_MODULE_GLOBALS()` 宏
- `zend_catch` 块
- `zend_class_entry`
- `zend_class_entry_get_class_entry()` 处理器
- `zend_class_entry` 结构 初始化
- `zend_class_entry` 注册
- `zend_class_implements()` 函数
- `zend_copy_parameters_array()` 函数
- `zend_declare_class_constant()` 函数
- `zend_declare_class_constant_bool()` 函数
- `zend_declare_class_constant_double()` 函数
- `zend_declare_class_constant_long()` 函数
- `zend_declare_class_constant_string()` 函数
- `zend_declare_class_constant_string()` 函数
- `zend_declare_property()` 函数
- `zend_declare_property_bool()` 函数
- `zend_declare_property_double()` 函数
- `zend_declare_property_ex()` 函数
- `zend_declare_property_long()` 函数
- `zend_declare_property_null()` 函数
- `zend_declare_property_string()` 函数
- `zend_declare_property_string()` 函数
- `zend_disable_class()` 函数
- `zend_disable_function()` 函数
- `ZEND_END_ARG_INFO()` 宏 [第 2]
- `ZEND_END_MODULE_GLOBALS()` 宏
- `zend_end_try` 块
- `zend_error()` 函数
- `zend_eval_string()` 函数 [第 2]
- `zend_eval_string_ex()` 函数
- `zend_exception` 函数
- `zend_execute()` 函数
- `zend_fetch()` 函数
- `zend_fetch_list` 函数
- `zend_fetch_resource()` 函数
- `zend_fetch` 函数 [第 2]
- `zend_fetch` 函数 [第 3]
- `zend_fetch` 函数 [第 4]
- `ZEND_FETCH_RESOURCE` 宏
- `zend_class_entry`
- `zend_class_entry` 处理器
- `zend_class_constant` 函数
- `zend_class_module` 函数
- `zend_class_module` 函数
- `zend_class_module` 函数
- `zend_class_module` 函数
- `zend_std_object` 函数
- `zend_hash_add` 函数
- `zend_hash_add` 函数
- `zend_hash_apply` 函数
- `zend_hash_copy` 函数
- `zend_hash_del` 函数
- `zend_hash_del` 函数
- `zend_hash_del` 函数
- `zend_hash_object` 函数
- `zend_hash_add` 函数
- `zend_hash_apply` 函数
- `zend_hash_apply` 函数
- `ZEND_HASH_APPLY_KEEP` 宏
- `ZEND_HASH_APPLY_REMOVE` 宏
- `ZEND_HASH_APPLY_STOP` 宏
- `zend_hash_apply_with_argument()` 函数 [第 2]
- `zend_hash_apply_with_arguments()` 函数 [第 2]
- `zend_hash_clean` 函数 [第 2]
- `zend_hash_compare` 函数 [第 2]
- `zend_hash_copy` 函数 [第 2]
- `zend_hash_del` 函数 [第 2]
- `zend_hash_del` 函数 [第 2]
- `zend_hash_del` 函数 [第 2]
- `zend_hash_del` 函数 [第 2]
- `zend_hash_del` 函数 [第 2]
- `zend_hash_del` 函数 [第 2]
- `zend_hash_del` 函数 [第 2]
- `zend_hash_del` 函数 [第 2]
- `zend_hash_del` 函数 [第 2]

- `zend_hash_destroy()` 第 2
- `zend_hash_exists()` 第 2
- `zend_hash_find()` 第 2
- `zend_hash_func()`
- `zend_hash_get_current_data_ex()`
- `zend_hash_get_current_key()`
- `zend_hash_get_current_key_ex()` 第 2
- `zend_hash_get_current_key_type_ex()`
- `zend_hash_graceful_destroy()`
- `zend_hash_graceful_reverse_destroy()`
- `zend_hash_index_del()` 第 2 第 3
- `zend_hash_index_exists()` 第 2
- `zend_hash_index_find()` 第 2
- `zend_hash_index_update()` 第 2
- `zend_hash_init()` 第 2
- `zend_hash_init_ex()`
- `zend_hash_internal_pointer_end_ex()`
- `zend_hash_internal_pointer_reset_ex()`
- `zend_hash_merge()` 第 2
- `zend_hash_merge_ex()` 第 2
- `zend_hash_minmax()` 第 2
- `zend_hash_move_backwards_ex()`
- `zend_hash_move_forward_ex()`
- `zend_hash_next_free_element()` 第 2
- `zend_hash_next_index_insert()`
- `zend_hash_next_insert()`
- `zend_hash_num_elements()`
- `zend_hash_quick_add()` 第 2
- `zend_hash_quick_exists()` 第 2
- `zend_hash_quick_find()` 第 2
- `zend_hash_quick_update()` 第 2
- `zend_hash_reverse_apply()`
- `zend_hash_sort()` 第 2
- `zend_hash_update()` 第 2
- `zend_hash_update_current_key()`
- `zend_ini_double()`
- `zend_ini`
- `zend_ini_long()`
- `ZEND_INI()`
- `zend_ini_string()`
- `zend_is_callable()`
- `zend_is_callable_ex()`
- `zend_is_true()`
- `zend_list_addref()`
- `zend_list_delete()` 第 2
- `zend_list_find()` 第 2
- `zend_list_insert()`
- `zend_list_add_element()`
- `zend_list_apply()`
- `zend_list_apply_with_argument()`
- `zend_list_apply_with_arguments()`
- `zend_list_apply_with_del()`
- `zend_list_clean()`
- `zend_list_copy()`
- `zend_list_count()`
- `zend_list_del_element()`
- `zend_list_destroy()`
- `zend_list_get_first_ex()`
- `zend_list_get_last_ex()`
- `zend_list_get_next_ex()`
- `zend_list_get_prev_ex()`
- `zend_list_init()`
- `zend_list_prepend_element()`
- `zend_list_remove_tail()`
- `zend_list_sort()`
- `zend_lookup_class()`
- `zend_lookup_class_ex()`
- `zend_make_callable()`
- `zend_mangle_property_name()` 第 2
- `zend_module_entry` 结构 第 2 第 3
- `ZEND_NUM_ARGS()` 宏 第 2
- `zend_object_store_get_object()` 函数
- `zend_object` 结构
- `zend_objects_get()`
- `zend_parse_method()` 函数
- `zend_parse_method_ex()` 函数
- `zend_parse_parameters()` 函数 第 2 第 3
- `zend_register_auto()` 函数
- `zend_qsort()` 函数
- `zend_read_property()` 函数
- `zend_read_static_property()` 函数
- `zend_register_global()` 函数 第 2
- `zend_register_constant()` 函数
- `zend_register_double_constant()` 函数
- `zend_register_internal_class()` 函数 第 2
- `zend_register_internal_class_ex()` 函数
- `zend_register_internal_interface()` 函数
- `zend_register_list_destructors()` 函数
- `zend_register_list_destructors_ex()` 函数 第 2
- `zend_register_long_constant()` 函数
- `zend_register_resource()` 函数
- `zend_register_string_constant()` 函数
- `zend_register_stringl_constant()` 函数
- `zend_restore_ini_entry()` 函数
- `zend_rsrc_list_get_rsrc_type()` 函数
- `zend_set_memory_limit()` 函数
- `zend_set_timeout()` 函数

# `zend_strndup()` 函数

# `zend_throw_error_exception()` 函数

# `zend_throw_exception()` 函数

# `zend_throw_exception_ex()` 函数

# `zend_throw_exception_object()` 函数

# `zend_try` 块

# `zend_unset_timeout()` 函数

# `zend_update_property()` 函数

# `zend_update_property_bool()` 函数

# `zend_update_property_double()` 函数

# `zend_update_property_long()` 函数

# `zend_update_property_null()` 函数

# `zend_update_property_string()` 函数

# `zend_update_property_stringl()` 函数

# `zend_update_static_property()` 函数

# `zend_update_static_property_bool()` 函数

# `zend_update_static_property_double()` 函数

# `zend_update_static_property_long()` 函数

# `zend_update_static_property_null()` 函数

# `zend_update_static_property_string()` 函数

# `zend_update_static_property_stringl()` 函数

# `ZEND_VERIFY_RESOURCE()` 宏

# `zend_zval_type_name()` 函数

# `ZendMM` (Zend 内存管理)

## 分配器函数

## `memory_limit` 设置 (`php.ini`)

## 持久化分配

# `zval` (Zend 值)

## 转换

### 创建

### 数据类型

#### 确定

- `IS_ARRAY`
- `IS_BOOL`
- `IS_DOUBLE`
- `IS_LONG`
- `IS_NULL`
- `IS_OBJECT`
- `IS_RESOURCE`
- `IS_STRING`

### 数据值

- 交换流以
- 获取
- 存储
- `zval*get_property_ptr_ptr()` 处理器
- `zval*get()` 处理器
- `zval*read_dimension()` 处理器
- `zval*read_property()` 处理器

`zval*` 数组 API

- 数组创建
- 数组填充

# `zval_add_ref()` 函数

# `ZVAL_BOOL()` 宏

# `zval_copy_ctor()` 函数

# `ZVAL_DOUBLE()` 宏

# `zval_dtor()` 函数

# `ZVAL_LONG()` 宏

# `zval_ptr_dtor()` 函数

# `ZVAL_RESOURCE()` 宏

# `ZVAL_STRINGL()` 宏

# `ZVAL_TRUE()` 宏

