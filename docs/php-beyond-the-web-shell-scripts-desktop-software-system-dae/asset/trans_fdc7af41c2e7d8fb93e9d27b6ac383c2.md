

# 使用 PHP 进行大数据处理

在继续之前，我们先澄清一下我们所说的 `big` 数据是什么意思。Hadoop 和其他 MapReduce 算法在其工作方式上存在固有的开销。这意味着，只有当数据集足够大时，它们才会开始产生好处（至少在性能方面）。你的具体情况将取决于你想要应用于数据的算法以及可用的替代方法，但通常你的数据集需要达到 Gb 级别才能开始看到明显的好处，并且需要显著更大才能使这些好处超过在你的任务中实现 MapReduce 所需的工程工作量。

如果你的数据符合这种特定的“大数据”定义，那么你可以利用 PHP 来发挥 Hadoop 的强大功能。虽然 Hadoop 是用 Java 编写的，但在编写驱动数据处理的 map 和 reduce 作业时，它是与语言无关的。它还使用标准流（`STDIN` 等）进行数据交换，我们在前面的章节中看到，在 PHP 中原生处理这些流非常容易。甚至有一个 PHP 框架可以帮助编写这些 map 和 reduce 作业。

如果你认为你的数据集符合“大数据”的标准，以下链接应该能帮助你开始在 PHP 中进行大数据处理。

> **进一步阅读**
> “MapReduce: Simplified Data Processing on Large Clusters” - 原始的 Google 论文  
> [http://research.google.com/archive/mapreduce.html](http://research.google.com/archive/mapreduce.html)
> “What is MapReduce” - 对 MapReduce 的非常简单的解释  
> [http://www-01.ibm.com/software/data/infosphere/hadoop/mapreduce/](http://www-01.ibm.com/software/data/infosphere/hadoop/mapreduce/)
> “Using Hadoop and PHP” - Jason Graves 的初学者教程  
> [http://collaboradev.com/2010/12/10/using-hadoop-and-php/](http://collaboradev.com/2010/12/10/using-hadoop-and-php/)
> HadooPHP - PHP Hadoop 框架  
> [https://github.com/dzuelke/HadooPHP](https://github.com/dzuelke/HadooPHP)
> “Big Data Analytics (with Hadoop and PHP)” - David Zuelke 的演示文稿  
> [https://speakerdeck.com/dzuelke/big-data-analytics-with-hadoop-and-php-dpc2013-2013-06-06](https://speakerdeck.com/dzuelke/big-data-analytics-with-hadoop-and-php-dpc2013-2013-06-06)
> 维基百科上对 MapReduce 的批评  
> [http://en.wikipedia.org/wiki/MapReduce#Criticism](http://en.wikipedia.org/wiki/MapReduce#Criticism)

## 9.18 数据缓存

在本章（以及其他地方）的各个地方，我们提到尽可能缓存数据通常是一种良好的做法。对于不熟悉的人来说，这只是意味着，当我们生成一些数据（无论是用于脚本的变量，还是文本或其他程序输出）并且我们可能想要以后再次使用时，我们不应该每次都重新生成它，而是将其存储在某个地方，直到我们再次需要它。

如何做到这一点应该是显而易见的，你可能熟悉创建变量、将文件写入磁盘或数据库等等。然而，虽然缓存数据可以加快你的程序，但它也可能带来自己的一系列问题，例如何时删除缓存的数据（缓存失效）、当磁盘空间或内存不足时如何处理缓存优先级、如何在进程甚至机器之间共享缓存数据，以及其他你（和我）可能甚至没有想到的事情。

> *“计算机科学中只有两件难事：命名事物、缓存失效和离-by-one 错误”* - 基于 Phil Karlton 的话

虽然 PHP 无法帮助我们解决第一个和最后一个问题，但在处理缓存时，它可以帮助我们一点。以下信息来源提供了一些关于 PHP 中缓存的详细信息。

> **进一步阅读**
> 使用 Memcached（高性能、分布式内存对象通用缓存系统）与 PHP  
> [http://www.php.net/manual/en/book.memcached.php](http://www.php.net/manual/en/book.memcached.php)
> MySQL 查询缓存  
> [http://php.net/manual/en/mysqlnd-qc.quickstart.caching.php](http://php.net/manual/en/mysqlnd-qc.quickstart.caching.php)
> 使用输出缓冲进行简单缓存  
> [http://www.theukwebdesigncompany.com/articles/php-caching.php](http://www.theukwebdesigncompany.com/articles/php-caching.php)
> 参见本书第 7 章中关于“虚拟文件 - tmpfs”的部分，以访问基于内存的磁盘  
> “更多 - 文件系统很慢” - Kevin Schroeder 撰写，讨论文件系统性能以及为什么操作系统缓存可能意味着使用内存驱动器对于缓存用途不一定好多少等等。  
> [http://www.eschrade.com/page/more-on-the-file-system-is-slow/](http://www.eschrade.com/page/more-on-the-file-system-is-slow/)

## 9.19 了解你的函数

在进行性能分析时，你可能会发现一些有问题的代码段，通常只有几行，运行缓慢，但无论你怎么努力都无法想出如何重写它们。值得注意的是，在 PHP 中，通常有多个函数执行相同或相似的操作，但它们的实现方式不同，因此实现相同目标所需的时间可能（有时大相径庭）。

以下是针对这种情况的两个“速查表”。第一个是一个网页（你也可以下载到自己的机器上运行），它对执行类似任务的函数组进行基准测试。这可以让你一目了然地了解哪些替代函数可能可用以及它们的性能如何。请注意，大多数函数的性能取决于周围的代码，因此请务必在你自己的应用程序上下文中对每个函数进行性能分析！

第二个链接是一个问答，尝试列出许多 PHP 函数的 Big O 时间。同样，这可以用来估计哪个函数在你的场景中可能表现更好。如果你不熟悉 Big O 表示法，它是一种描述算法所需时间（或资源）如何随数据输入大小增加而增加的方法。还提供了一个关于维基百科上 Big O 表示法文章的链接。

> **进一步阅读**
> PHP 基准测试脚本，按执行的功能分组  
> [http://maettig.com/code/php/php-performance-benchmarks.php](http://maettig.com/code/php/php-performance-benchmarks.php)
> 列出各种函数 Big O 时间的问答  
> [http://stackoverflow.com/questions/2473989/list-of-big-o-for-php-functions](http://stackoverflow.com/questions/2473989/list-of-big-o-for-php-functions)
> 维基百科上的 Big O 表示法  
> [http://en.wikipedia.org/wiki/Big_O_notation](http://en.wikipedia.org/wiki/Big_O_notation)
> 一篇展示如何以不寻常的方式使用替代函数来获得性能提升的文章  
> [http://www.puremango.co.uk/2010/06/fast-php-array_unique-for-removing-duplicates/](http://www.puremango.co.uk/2010/06/fast-php-array_unique-for-removing-duplicates/)
> 一个替代的基准测试网页  
> [http://www.phpbench.com/](http://www.phpbench.com/)

## 9.20 将代码外包给其他语言

当你真正遇到 PHP 性能的极限，并且增加硬件不是选项时，一种策略是将资源密集型代码移出到性能更好的语言中。有两种方法可以做到这一点，要么是创建你可以“shell out”到的独立程序（参见第 5 章），要么是创建 PHP 扩展（通常比单独的进程访问速度更快）。如果你打算这样做，你需要学习或利用另一种语言，因此这主要是超出本书范围的主题。以下链接应该能让你很好地了解从哪里开始。

> **进一步阅读**
> “PHP at the Core: A Hackers Guide” - 官方 PHP 文档。涵盖了与编写扩展相关的 PHP 内部机制。  
> [http://www.php.net/manual/en/internals2.php](http://www.php.net/manual/en/internals2.php)
> “Extension Writing” - Zend 开发者专区 - 编写扩展的良好入门介绍

