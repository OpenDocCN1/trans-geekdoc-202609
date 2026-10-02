

对于 fetch worker，你会看到：

```
php NaradaFetch.php
Local URL: http://news.google.com/news/search?pz=1&cf=all&ned=us&hl=en&q=author%3A%22Avi+Issacharoff%22&cf=all
Local URL: http://news.google.com/news/search?pz=1&cf=all&ned=us&hl=en&q=author%3A%22Avi+Issacharoff%22&scoring=d
Local URL: http://news.google.com/news/search?pz=1&cf=all&ned=us&hl=en&q=author%3A%22Avi+Issacharoff%22&cf=all&scoring=n&nolr=1
Local URL: http://news.google.com/news/search?pz=1&ned=us&hl=en&q=author%3A%22Avi+Issacharoff%22
Skipping Remote URL: http://www.haaretz.com/hasen/spages/1131613.html
Local URL: http://news.google.com/news/search?pz=1&cf=all&ned=us&hl=en&q=author%3A%22Amos+Harel%22&scoring=n
Local URL: http://news.google.com/news/search?pz=1&cf=all&ned=us&hl=en&q=author%3A%22Avi+Issacharoff%22&scoring=n
Skipping Remote URL: http://www.haaretz.com/hasen/spages/1131322.html
Skipping Remote URL: http://www.haaretz.com/hasen/spages/1131318.html
```

一旦所有这些 worker 都在运行，你就可以随意添加 URL 并尽情搜索！你可能还想运行多个相同类型的 worker。Gearman 作业服务器会使用所有可用的资源。处理作业的 worker 越多，就能完成的工作越多。

## Narada 的待办事项

如前所述，Narada 是一个开源项目，采用 BSD 许可证。你可以随意修改代码，甚至被鼓励这样做。如果你有一些功能、错误修复、增强或希望为项目贡献的其他修改，你非常受欢迎，可以贡献并获得名声和认可！或者你可以为你自己或你工作的公司进行内部使用而做出任意多的更改。Narada 是一个概念验证项目，旨在展示使用 MySQL/Drizzle、memcached、Gearman 和 Sphinx 组合的强大功能，还有许多其他事情可以做：

- PHP fetch worker 可以更好地清理它解析的内容。结果集中出现了许多非字母数字字符。Perl 版本的 fetch worker 在页面内容上执行了大量的正则表达式，而不是使用 DOM 解析方法，并且还剥离了所有 HTML 和非字母数字字符。PHP 版本的 worker 使用的 DOM 概念无疑是一种更干净的做法，因此也许可以将 Perl worker 中的一些正则表达式技巧迁移到 PHP worker 中。
- PHP fetch worker 可以具有更智能地移除页面中不相关部分的能力，只获取页面中包含的文章实际核心。例如，许多网站都有一个导航侧边栏，列出网站新闻故事的标题。这会导致页面被索引时包含大量不相关信息。
- 索引页面可以使用结果分页。Perl 版本有一个分页方法，可以很容易地转换为 PHP 来实现此功能。
- 有用的是能够控制文档抓取递归的深度。目前它是无界的，有点像第一部《星际迷航》电影中的 Vger！这可以通过某种全局计数器来实现——也许使用 memcached 变量和递增操作。

这些只是对 PHP 版本进行开发的有趣想法。正如任何项目一样，代码演进永无止境！

## 其他作业服务器系统

其他与 Gearman 类似的系统也值得提及。这些系统相似之处在于它们提供了实现分布式计算的手段。

- **Beanstalk:** 这是一个简单、快速的工作队列系统，很像 Gearman。服务器 beanstalkd 基于 C 语言构建。有包括 PHP 在内的各种语言的客户端。官方网站是 `http://kr.github.com/beanstalkd/`。
- **Hadoop:** 这是一个主要用 Java 编写的 Apache 项目，但也可以与 PHP 一起使用。Hadoop 包含各种组件，例如：
  - **HBase:** 一个支持大型数据集结构化数据存储的分布式数据库。
  - **HDFS:** 一个分布式文件系统。
  - **MapReduce:** 用于在计算集群上分布式处理大型数据集的软件框架。
  - **ZooKeeper:** 一个用于分布式应用程序的高性能协调服务。

## SUMMARY

在本章中，你学习了使用 PHP 应用程序的多任务处理。你看到了如何使用 Gearman 来处理传统上在 Web 应用程序中发现的功能。你现在可以从 Web 应用程序外部实现这些功能，从而在仍支持应用程序中大量功能的同时实现更好的性能。Narada 应用程序展示了使用 Gearman 以及本书中讨论的各种其他组件的分布式应用程序概念。

## 11

## 重写规则

### 本章内容？

- 基本重写规则，考虑到第 1 章中回顾的正则表达式
- 根据可用数据显示或拒绝访问内容的条件规则
- 记录重写事件并优化规则和条件
- 使用内置重写映射，其中一对一的数据关系可作为更改 URL 的基础
- 使用 PHP 构建自定义重写映射

对 Web URL 重写有深入的理解对于几乎任何 Web 应用程序都至关重要。本章是本书中唯一涉及 Apache Web 服务器特定概念的章节之一。其他 Web 服务器也存在兼容模块；然而，它们超出了本书的范围。

本章的各节不仅包括 mod_rewrite 的传统概述，还涵盖了使用 PHP 和 MySQL 扩展重写功能。

重写规则是 PHP 和 MySQL 拼图的最后几块之一，可以在几乎每个使用 PHP 的主要应用程序中找到。重写规则有两个主要用途：

- 隐藏 PHP 的底层功能，从而暴露更少的站点内部信息
- 创建干净且可读的 URL，使其更容易记住并有助于搜索引擎优化

使用所有可用工具来拥有一个连贯、易于导航且易于维护的应用程序非常重要。对 mod_rewrite 有坚实的掌握是任何工具箱的欢迎补充。完美的应用程序是用户可以在完全不知道底层系统工作原理的情况下成为专家的应用程序。

## 使用重写规则

重写规则必须定义在 Apache 配置文件或，如果启用了 override，则定义在被重写的 URL 路径中的 .htaccess 文件中。互联网上有大量教程可供设置重写规则，到现在你可能已经相当熟悉它们了。调试重写规则可能很困难。当你遇到规则无法工作的问题时，通常有益的做法是简化规则，然后重建它，直到它完全功能正常并产生所需的效果。

### 理解重写规则的目的和结构

重写规则最常用于掩盖否则复杂的 URL，以改善搜索引擎优化并使 URL 更易于阅读。搜索引擎通常会在文档的 URL 中查找关键字，以帮助确定其相关性。相比之下，URL 的查询字符串部分在搜索引擎确定相关性时通常会被忽略。考虑这两个 URL：

```
http://example.com/view.php?nodeid=123
http://example.com/2009/9/using-rewrite-rules/
```

第二个 URL 更容易阅读，并且包含搜索引擎可以提取的关键字。它还有一个额外的好处，即不对客户端暴露 PHP。通过不直接暴露 PHP，URL 隐藏了潜在攻击者的一个潜在入口点。然而，如果 view.php 仍然直接由 Web 服务器公开，这种方法就毫无用处，因此它只提供了安全性的假象。以下三行代码可以放在 .htaccess 文件中，允许读者通过友好名称访问节点，但不能直接通过视图脚本访问：

```
RewriteEngine On
RewriteRule ^([0-9]{4})/([0-9]{0,2})/([^/]+)/$  /view.php?y=$1&m=$2&t=$4 [S]
RewriteRule ^view\.php  -  [F]
```

这是一个典型的重写规则示例。每行称为一个指令。第一个指令打开重写引擎。第二个指令将模式匹配到 URL（参见第 1 章关于正则表达式），如果模式匹配，则将 URL 重写为视图脚本。第三行检测 URL 是否为视图脚本，如果 URL 与 PHP 文件匹配，则强制返回 403（Forbidden）响应。

