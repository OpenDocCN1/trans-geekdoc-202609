

# 章节概览

- [Chapter 3](#text00065.html) , *Using Linked Lists* , 涵盖不同类型的链表。重点介绍链表不同变体的分类及其构建过程，并附带示例。
- [Chapter 4](#text00098.html) , *Constructing Stacks and Queues* , 重点介绍本章中最重要的两个数据结构——栈和队列。我们将了解如何使用不同方法构建栈和队列，并通过示例讨论它们的操作和用法。
- [Chapter 5](#text00118.html) , *Applying Recursive Algorithms - Recursion* , 重点介绍算法中的一个重要主题——递归。我们将介绍使用递归算法解决问题的不同方式，以及使用该技术的优缺点。我们还将介绍一些可以使用递归解决的基本日常编程问题。
- [Chapter 6](#text00138.html) , *Understanding and Implementing Trees* , 谈论一种非层级数据结构——树。我们将介绍树的属性及其构建方法，并理解树数据结构在哪些情况下对我们很重要。
- [Chapter 7](#text00165.html) , *Using Sorting Algorithms* , 演示如何实现不同的排序算法及其复杂度，因为排序是编程世界中非常重要的主题，对高效排序算法的探索从未停止。在本章末尾，我们还将介绍 PHP 内置的排序算法。
- [Chapter 8](#text00187.html) , *Exploring Search Options* , 说明搜索在编程世界中的重要性。在本章中，我们将重点介绍不同的搜索技术以及何时使用哪种算法。我们还将讨论是否应该在搜索前进行排序。本章包含大量不同算法的示例和实现。
- [Chapter 9](#text00202.html) , *Putting Graphs into Action* , 解释图算法是编程范式中应用最广泛的算法之一。在本章中，我们将重点介绍不同的图相关问题，并使用不同算法求解。我们将通过示例和解释介绍最短路径算法和最小生成树的实现。
- [Chapter 10](#text00229.html) , *Understanding and Using Heaps* , 谈论本书中最后一个数据结构主题——堆。它是一种非常高效的数据结构，在现实世界的许多实现中都有使用。我们将展示如何构建堆及其用途，包括堆排序算法的实现。
- [Chapter 11](#text00238.html) , *Solving Problems with Advanced Techniques* , 重点介绍解决问题的不同技术。我们将重点讨论备忘录模式、动态规划、贪心算法和回溯等主题，并附带实际问题的示例和解决方案。
- [Chapter 12](#text00252.html) , *PHP’s Built-In Support for Data Structures and Algorithms* , 展示 PHP 对数据结构和算法的内置支持。我们将介绍 PHP 的函数、PECL 库，以及一些在线资源参考。
- [Chapter 13](#text00263.html) , *Functional Data Structures with PHP* , 揭示函数式编程和使用 PHP 的函数式数据结构，因为函数式编程近来备受关注。我们将介绍一个名为 Tarsana 的函数式编程库，并展示使用它的不同示例。

# 本书所需环境

您只需在机器上安装最新版本的 PHP（最低要求为 PHP 7.x）即可。您可以从命令行运行示例，这不需要 Web 服务器。不过，如果您愿意，也可以安装 Apache 或 Nginx，或以下组件：

*   PHP 7.x+
*   Nginx/Apache（可选）
*   PHP IDE 或代码编辑器

# 读者对象

本书适合那些希望通过 PHP 学习数据结构和算法，以便更好地控制应用程序解决方案、效率和优化的读者。

需要具备对 PHP 数据类型、控制结构和其他基本特性的基本理解。

# 约定

在本书中，您将看到多种文本样式，用于区分不同类型的信息。以下是这些样式的一些示例及其含义的解释。

代码采用与本书正文字体不同的字体编写，以突出显示代码块。

代码块设置如下：

```php
[default]

class TreeNode {

    public $data = NULL;

    public $children = [];

    public function __construct(string $data = NULL) {

         $this->data = $data;

    }

    public function addChildren(TreeNode $node) {

         $this->children[] = $node;

    }

}
```

当我们希望在解释过程中引起您对代码块特定部分的注意时，该代码会在文本中高亮显示，如下所示：`addChildren` 。

任何命令行输入或输出均按如下方式编写：

```
Final



-Semi Final 1



--Quarter Final 1



--Quarter Final 2



-Semi Final 2



--Quarter Final 3



--Quarter Final 4
```

新术语和重要单词以**粗体**显示。您在屏幕上看到的单词（例如菜单或对话框中的单词）在文本中显示如下："Clicking the Next button moves you to the next screen."

警告或重要提示显示在如下框中。技巧和窍门显示如下。

# 读者反馈

我们始终欢迎读者的反馈。请让我们知道您对本书的看法——您喜欢或不喜欢的地方。读者反馈对我们很重要，因为它有助于我们开发出您真正能从中获益良多的书籍。

要发送一般反馈，只需发送电子邮件至 `feedback@packtpub.com` ，并在邮件主题中注明书名。

如果您在某个主题上有专长，并有兴趣撰写或为书籍做贡献，请参阅 [www.packtpub.com/authors](http://www.packtpub.com/authors) 上的作者指南。

# 客户支持

既然您已成为 Packt 图书的荣幸拥有者，我们准备了一系列资源帮助您从购买中获得最大收益。

# 下载示例代码

您可以从 [http://www.packtpub.com](http://www.packtpub.com) 的账户中下载本书的示例代码文件。如果您在别处购买了本书，可以访问 [http://www.packtpub.com/support](http://www.packtpub.com/support) 并注册，以便将文件直接发送到您的邮箱。

您可以按照以下步骤下载代码文件：

1.  使用您的电子邮件地址和密码登录或注册我们的网站。
2.  将鼠标指针悬停在顶部的 SUPPORT 选项卡上。
3.  单击 Code Downloads & Errata（代码下载与勘误）。
4.  在搜索框中输入书名。
5.  选择您要下载代码文件的书籍。
6.  从下拉菜单中选择您购买本书的渠道。
7.  单击 Code Download（代码下载）。

文件下载完成后，请确保使用以下工具的最新版本解压或提取文件夹：

*   WinRAR / 7-Zip for Windows
*   Zipeg / iZip / UnRarX for Mac
*   7-Zip / PeaZip for Linux

本书的代码包也托管在 GitHub 上：[https://github.com/PacktPublishing/PHP7-Data-Structures-and-Algorithms](https://github.com/PacktPublishing/PHP-7-Data-Structures-and-Algorithms) 。我们在 [https://github.com/PacktPublishing/](https://github.com/PacktPublishing/) 还提供了来自我们丰富图书和视频目录的其他代码包。快去看看吧！

# 下载本书的彩色图片

我们还提供了一个 PDF 文件，其中包含本书使用的屏幕截图/图表的彩色图片。彩色图片将帮助您更好地理解输出结果的变化。您可以从 [https://www.packtpub.com/sites/default/files/downloads/PHP7DataStructuresandAlgorithms_ColorImages.pdf](https://www.packtpub.com/sites/default/files/downloads/Bookname_ColorImages.pdf) 下载此文件。

# 读累了记得休息一会哦~

**公众号：古德猫宁李**

*   电子书搜索下载
*   书单分享

