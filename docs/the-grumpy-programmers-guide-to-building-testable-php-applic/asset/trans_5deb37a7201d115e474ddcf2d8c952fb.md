
![《爱发牢骚的程序员构建可测试 PHP 应用指南》](images/title_page.jpg)

# 《爱发牢骚的程序员构建可测试 PHP 应用指南》

## Chris Hartjes

本书可在 [http://leanpub.com/grumpy-testing](http://leanpub.com/grumpy-testing) 购买

本版本发布于 2013-10-15

![出版社标志](images/leanpub-logo.png)

\*   \*   \*   \*   \*

这是一本 [Leanpub](http://leanpub.com) 书籍。Leanpub 赋能作者和出版商使用精益出版流程。[Lean Publishing](http://leanpub.com/manifesto) 是指使用轻量级工具并通过多次迭代发布进行中的电子书，以获取读者反馈，在拥有合适的书籍后调整方向并建立势头。

\*   \*   \*   \*   \*

© 2012 - 2013 Chris Hartjes

## 目录

*   [1 版权](#chap00.xhtml#leanpub-auto-copyright)
*   [2 致谢](#chap01.xhtml#leanpub-auto-thanks)
*   [3 测试很重要，可测试的应用更好](#chap02.xhtml#leanpub-auto-testing-is-good-testable-applications-are-better)
*   [4 构建可测试应用很困难](#chap03.xhtml#leanpub-auto-building-testable-applications-is-hard)
*   [5 环境一致性](#chap04.xhtml#leanpub-auto-environmental-consistency)
*   [6 静态代码分析](#chap05.xhtml#leanpub-auto-static-code-analysis)
*   [7 使用依赖注入解耦你的对象](#chap06.xhtml#leanpub-auto-decoupling-your-objects-using-dependency-injection)
*   [8 像洋葱一样，你的应用有层次](#chap07.xhtml#leanpub-auto-like-an-onion-your-application-has-layers)
*   [9 外壳与沙箱](#chap08.xhtml#leanpub-auto-shells-and-sandboxes)
*   [10 重建你的编程与部署环境](#chap09.xhtml#leanpub-auto-rebuilding-your-programming-and-deployment-environments)
*   [11 面向 PHP 开发者的持续集成生态](#chap10.xhtml#leanpub-auto-continuous-integration-landscape-for-php-developers)
*   [12 基础设施债务](#chap11.xhtml#leanpub-auto-infrastructure-debt)
*   [13 恐惧是心灵的杀手](#chap12.xhtml#leanpub-auto-fear-is-the-mind-killer)
*   [14 测试在哪里？](#chap13.xhtml#leanpub-auto-where-are-the-tests)
*   [15 元测试：理解模拟对象](#chap14.xhtml#leanpub-auto-metatesting-understanding-mock-objects)
*   [16 来自一个爱发牢骚程序员的建议](#chap15.xhtml#leanpub-auto-advice-from-a-grumpy-programmer)

### 1 版权

本书记载的所有内容，除另有说明外，均受 (c) 2012 Chris Hartjes 版权保护。鉴于电子版书籍不使用 DRM，我请求读者尊重我的版权，不要在未经我明确书面同意的情况下分发本书的部分内容。如果你帮助组织 PHP 用户组，请联系我以获取免费赠送给成员的副本。

ISBN: 978-1-105-45488-2

### 2 致谢

首先，我要感谢我的技术审阅者。他们抓住了我遗漏的所有细节，使本指南成为现在的样子。因此感谢（无特定顺序）Peter Meth、Joel Perras、Matthew Turland 和 Remi Woler 的帮助。更好的指南来自他人的贡献。

其次，我要感谢 PHP 社区中那些不断突破界限、始终大声清晰地谈论最佳实践重要性，同时努力回馈社区的人们。那些人激励我继续撰写和演讲关于我感兴趣且希望你也感兴趣的话题。我有时会觉得与“主流”PHP 社区脱节，但如果我的网络上的牢骚和抱怨激励了其他程序员提升自己的水平，那么我很感激自己产生了影响。

最后，我要感谢我的妻子 Claire，她在我从大学毕业的新手程序员到今天这个全面、经验丰富、极其爱发牢骚的程序员的旅程中一直陪伴着我。感谢她容忍程序员长时间盯着屏幕，而不是凝视伴侣美丽的眼睛。我的妻子是我做的一切事情的伙伴。

如 always，我欢迎你对本指南中的任何内容发表评论，有任何问题，或只是想听听我对编程相关各种话题的看法。棒球也是。

本指南是在 [Leanpub](http://leanpub.com) 的优秀人士帮助下构建的。我最初决定以文本加一些 [`AsciiDoc`](http://www.methods.co.nz/asciidoc/) 标记的方式撰写指南，这使得将其转换为 Leanpub 所要求的 [`Markdown`](https://en.wikipedia.org/wiki/Markdown) 变得更容易。我还使用 [`Pandoc`](http://johnmacfarlane.net/pandoc/) 来调整本指南中包含的三篇附赠文章的部分内容。

特别感谢 Elizabeth Gauthier 制作的精彩封面。我的妻子评论说它非常逼真。

不幸的是，本指南并不面向初学者程序员。编写可测试的应用是一件困难的事情，需要你已经具备扎实的编程背景。本指南面向的是有过编写测试经验、希望将技能提升到下一水平的 intermediate 级程序员。

如果你正在寻找编写单元测试的入门指南，我强烈推荐 [`PHPUnit` documentation](http://www.phpunit.de/manual/3.6/en/phpunit-book.html)。它涵盖了所有基础知识。

你可以通过电子邮件 chartjes@littlehart.net 联系到我，Twitter 上是 @grmpyprogrammer。我定期在 http://www.littlehart.net/atthekeyboard 上写博客。感谢你花时间查看本指南，希望你能从中获得帮助，更好地掌握测试 PHP 应用的能力。

### 3 测试很重要，可测试的应用更好

毫无疑问，PHP 世界在测试态度方面终于赶上了其他编程社区。因此，你可以从网上或你喜欢的零售商的书籍中找到大量非常好的资源。

这些信息大多集中在实际编写测试以及你需要编写的测试类型策略上。我发现大多数资源中缺少的是如何编写可以真正进行测试的应用。听起来很明显，至少对我来说是这样。

那里有一个公开的秘密：有些应用永远无法使用自动化测试工具进行测试。它们是以一种你只能编写检查其 HTML 输出的测试的方式构建的。这真的很遗憾，因为这种情况从不是有意为之。就像代码中的技术债务一样，它会随着时间的推移而积累，最终你会得到一个几乎像黑盒子的应用：你向其中输入数据，得到输出返回，却没有简单的方法来确定如果返回了你不期望的结果该如何修复。

但请不要误会：构建一个非平凡的可测试应用确实需要经验。很多经验。你会犯错。你需要在以后重构东西，并且经常会发现重构很痛苦，与你试图实现看似简单的功能请求相比更是如此。

我坚信自动化测试的力量可以给你一个可维护、可扩展且性能良好的应用。我并不总是能参与到致力于可测试性的应用开发中。这确实是对整个测试过程的一种不同看法。知道如何编写断言语句，或理解如何使用模拟对象来隔离正在测试的模块的组件是一回事；要创建一个可以从头到尾进行测试的应用又是另一回事。
