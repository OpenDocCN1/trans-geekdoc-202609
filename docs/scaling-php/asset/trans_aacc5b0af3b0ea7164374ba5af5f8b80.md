
*   [安装 Memcached](#chap15.xhtml#leanpub-auto-installing-memcached)

*   [将 PHP 与 Memcached 连接起来](#chap15.xhtml#leanpub-auto-hook­ing-up-php-to-memcached)

*   [协议](#chap15.xhtml#leanpub-auto-protocols)

*   [压缩和序列化](#chap15.xhtml#leanpub-auto-compression-and-serialization)

*   [服务器池](#chap15.xhtml#leanpub-auto-server-pools)

*   [原子计数器](#chap15.xhtml#leanpub-auto-atomic-counters)

*   [避免竞争：CAS 令牌](#chap15.xhtml#leanpub-auto-avoiding-the-rat-race-cas-tokens)

*   [注意超时](#chap15.xhtml#leanpub-auto-watch-out-for-timeouts)

*   [使用 Memcached 进行会话管理](#chap15.xhtml#leanpub-auto-using-memcached-for-sessions)

*   [通过 Telnet 调试 Memcached](#chap15.xhtml#leanpub-auto-debugging-memcached-from-telnet)

*   [我的 Memcached 配置](#chap15.xhtml#leanpub-auto-my-memcached-setup)

*   [进一步阅读和工具](#chap15.xhtml#leanpub-auto-further-reading-and-tools)

*   [案例研究：HTTP 缓存和 Nginx FastCGI 缓存](#chap16.xhtml#leanpub-auto-case-study-http-caching-and-the-nginx-fastcgi-cache)

    *   [缓存静态资源](#chap16.xhtml#leanpub-auto-caching-static-assets)

    *   [缓存代理](#chap16.xhtml#leanpub-auto-caching-proxy)

*   [案例研究：CakePHP 框架缓存](#chap17.xhtml#leanpub-auto-case-study-cakephp-framework-caching)

    *   [CakePHP，你这个邪恶的甜点](#chap17.xhtml#leanpub-auto-cakephp-you-devilish-dessert)

    *   [CakePHP 请求的生死存亡](#chap17.xhtml#leanpub-auto-the-life-and-death-of-a-cakephp-request)

    *   [如果它看起来像竞争条件……](#chap17.xhtml#leanpub-auto-if-it-smells-like-a-race-condition)

    *   [打破假设](#chap17.xhtml#leanpub-auto-busting-the-assumptions)

    *   [现在怎么办？我没主意了](#chap17.xhtml#leanpub-auto-now-what-im-out-of-ideas)

    *   [解决方案](#chap17.xhtml#leanpub-auto-the-solutions)

*   [案例研究：优化 PHP 中的图像处理](#chap18.xhtml#leanpub-auto-case-study-optimizing-image-handling-in-php)

    *   [笨拙的“PHP 教程”方法](#chap18.xhtml#leanpub-auto-the-naive-php-tutorial-way)

    *   [ImageMagick vs GraphicsMagick](#chap18.xhtml#leanpub-auto-imagemagick-vs-graphicsmagick)

    *   [允许大文件上传](#chap18.xhtml#leanpub-auto-allowing-large-file-uploads)

    *   [删除 EXIF 元数据](#chap18.xhtml#leanpub-auto-stripping-exif-metadata)

    *   [自动旋转](#chap18.xhtml#leanpub-auto-autorotation)

*   [案例研究：基准测试和 Web 服务负载测试](#chap19.xhtml#leanpub-auto-case-study-benchmarking-and-load-testing-web-services)

    *   [设置测试环境](#chap19.xhtml#leanpub-auto-setting-up-a-test-environment)

    *   [著名的 `ab`（Apache Benchmark）](#chap19.xhtml#leanpub-auto-the-famous-ab-apache-benchmark)

    *   [Siege，一个更现代的 `ab`](#chap19.xhtml#leanpub-auto-siege-a-more-modern-ab)

    *   [带机枪的蜜蜂](#chap19.xhtml#leanpub-auto-bees-with-machine-guns)

    *   [Sysbench]

*   [赞助商](#chap20.xhtml#leanpub-auto-sponsors)

### 前言

#### 这本书是如何写成的

2009 年，我通过在 Twitter 上看到 Noah Everett（Twitpic 创始人兼 CEO）的帖子，与他取得了联系。Noah 是个聪明、自学成才的程序员，当 Twitpic 在“ Hudson 奇迹”（即 US Airways Flight 1549 的第一张照片）发布后瞬间走红时，他被迫立即承担起规模扩展的任务。[US Airways Flight 1549](http://en.wikipedia.org/wiki/US_Airways_Flight_1549) 的照片随后在 [Twitpic](http://twitpic.com/135xa) 上传。

随后，我们的第一次对话并不是正式的“访谈”，而是我向 Noah 介绍了 memcache，并向他展示了如何在一小时内完成 memcache 的安装——在此之前，该站点经常崩溃，而在我们通话时它已经宕机。我当时不在场，但我想象他正在焦急地敲键盘，一边输入 `apt-get install memcache`，一边有数百个愤怒的“beiber”粉丝向他发送负能量（以及抱怨的推文）。我免费为他提供一小时咨询，帮助他解决一个让他有机会成为互联网前 100 名网站之一的技术难题。听起来不错。那时在 Twitpic 工作是件很棒的事。

![There's a plane in the Hudson. I'm on the ferry going to pick up the people. Crazy. - Janis Krums (@jkrums)](images/01----hudson.png)

有一架飞机在 Hudson 河里。我坐渡轮去接人，这太疯狂了。- Janis Krums (@jkrums)

我加入 Twitpic 时，很快就发现那里的情况非常混乱。基础设施由不同的服务器和 FreeBSD 版本组成，后端是一堆用 PHP 内联 HTML 编写的“烂摊子”。记住，Twitpic 是在一次 Red Bull 驱动的周末里作为 Noah 与几位朋友分享照片的副业项目搭建的，它并不是为了参加“最漂亮代码”评选。但，哇，它真的很烂。想象一下你 14 岁小弟可能写的 PHP 代码——乱七八糟，`pagename.php` 文件，没有 MVC 框架，顶部只有少量的 `include_once` 语句。

起初，Noah 和我必须围绕笔记本电脑安排生活。去超市？带上笔记本电脑。要出去约会？别忘了带上笔记本电脑。

> “嘿，我知道这约会会很棒，但我需要暂停一下，马上去用笔记本电脑解决点事。你觉得这里有免费 WiFi 吗？”

Twitpic 就像一个妒忌的女朋友，随时准备在你毫无防备时毁掉你的一天。我从不清楚何时需要冲进一家 Starbucks 重启 Apache。

主要是出于 necessity（必然性），而且没有人愿意在晚上和笔记本电脑依偎着睡觉，我们学会了。我们扩展了规模，改进了基础设施。虽然我们的设置并不完美，但我们学到了 incredible（惊人的）东西，三年后，我已经构建了一个相当稳固的架构。当服务器在今晚中午 12 点钟出现故障时，什么也不会发生——因为我们构建了水平扩展、复制的系统，它设计用于容忍失败。

#### 这本书的设计

这本书虽然以 PHP 为中心，但可以应用于任何语言。大多数技巧、方法和设计模式都能顺利应用于 Ruby、Python、Java，甚至除 Visual Basic 之外的所有语言（好吧，也许连 VB 也可以）。

请把它当作食谱，或者也许是一本“你选择你的冒险”故事——你不需要按顺序或从头到尾阅读。随意跳转到感兴趣的章节或部分，深入探索最吸引你的内容。或者，如果你像 Noah，现在就需要一本能让你的网站立刻上线的书。

我安排章节的方式是从栈的外层开始，逐层深入，直到我们到达代码。是的，代码是最后的部分。为什么？因为它通常是堆栈中最快的部分。我明白，你不是系统管理员，也不在电视上扮演系统管理员，但 80% 的规模扩展收益都来自代码之外，而一点点 Linux 经验可以事半功倍。

#### 谁应该阅读这本书？

这本书面向创业公司、创业者以及热衷于打拼、正确构建事物的聪明人。

你应该了解 PHP，了解你当前的技术栈，并且熟悉 Linux 环境。示例假设使用 Ubuntu Server，但任何 Linux 发行版都能工作。如果你能使用包管理工具（`apt-get`、`yum`）并编辑文本文件，你就能在本书中实现大多数示例。

我的读者是聪明、 intelligent（聪明）的人，他们不需要手把手的指导。我会解释复杂的主题并提供详尽的示例，但这 **不是** 简单地重复文档。我尽可能包含了大量的实用知识和案例研究，但讨论的主题并不全面。如果你想要文档，直接去 Google 搜索即可，因为我最讨厌的就是买一本里面充满 150 页垃圾内容的书。

#### 你需要为这本书准备什么

