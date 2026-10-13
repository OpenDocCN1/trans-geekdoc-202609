

# 网络安全：网络战、可实现性与风险

在本书中，我们还将回答我们是否面临网络战危险的问题。让我们在此明确指出：我们确实面临。我们受到网络战的威胁（在我们撰写这些文字时，网络战仍作为乌克兰战争的一部分持续进行）。唯一悬而未决的问题是此类网络战会呈现何种面貌（我们将在[第 7 章](#ch7.xhtml)中给出答案）。我们可以顺利地转入下一个问题，即网络攻击是否可能引发战争。这是一个被越来越多地谈论、也被越来越多地考量的问题。我们认为它可以。我们将在[第 7 章](#ch7.xhtml)中花费更多时间探讨这一点。我们也将探讨战争期间此类网络攻击可能呈现的面貌。

## 1.7 网络安全究竟可否实现？

网络安全是可以实现的，但需在特定条件下且以一定程度实现。我们在此涉及一个问题：是否有可能以一种方式保护系统（广义上理解：IT 系统、计算机、智能手机等），使其无法被黑客攻破。这取决于为实现目标将投入何种资源。软件的特性在于它可能包含可被系统性利用的漏洞，即以一种可以接管系统控制权的方式被利用。另一方面，网络安全之所以可实现，是因为它能导致一种局面：发动网络攻击的成本极高（成本过高，以至于希望在成本面前不再发起任何行动）。这就是我们在构建安全时必须采取的思维方式。

因此，关键在于增加潜在侵略者或潜在网络犯罪分子的成本。关键在于让网络攻击变得困难、充满挑战。让对手的“工作”付出高昂代价。这是我们需要采取的态度。这种态度既适用于普通用户、中小型或大型公司、机构，甚至军队。

增加成本——这是一条放之四海而皆准的通用法则！

## 注释

1.  [F. Cohen](#ch1.xhtml#R_en1_1), *Computer viruses: Theory and experiments*, in: *7th DoD/NBS Computer Security Conference Proceedings*, 1984, pp. 240–263.

2.  [P. Szor](#ch1.xhtml#R_en1_2), *Fighting computer virus attacks*, in: *USENIX Security Symposium*, 2004.

3.  [J.K](#ch1.xhtml#R_en1_3). Reynolds, *The helminthiasis of the Internet*, "Computer networks and ISDN systems" 1991, vol. 22, no. 5, pp. 347−361; T. Eisenberg, D. Gries, J. Hartmanis, D. Holcomb, MS Lynn, T. Santoro, *The Cornell commission: on Morris and the worm*, "Communications of the ACM" 1989, vol. 32, no. 6, pp. 706−709.

4.  [Vesselin Bontchev](#ch1.xhtml#R_en1_4), The Bulgarian and Soviet Virus Factories, 1991, [https://bontchev.nlcv.bas.bg/papers/factory.html](https://bontchev.nlcv.bas.bg/papers/factory.html)

5.  [P. Baumard](#ch1.xhtml#R_en1_5), *A brief history of hacking and cyberdefense*, in: *Cybersecurity in France*, Springer, Cham 2017, pp. 17−30.

6.  [Bulba](#ch1.xhtml#R_en1_6), Kil3r, *Bypassing StackGuard and StackShield*, "Phrack Magazine" 2000, no. 56, [http://phrack.org/issues/56/5.html](http://phrack.org/issues/56/5.html)

7.  [Hydro](#ch1.xhtml#R_en1_7), *Third quarter 2019 Report*, [https://www.hydro.com/Document/Index?name=Report%20Q3%202019.pdf&id=252245](https://www.hydro.com/Document/Index?name=Report%20Q3%202019.pdf&id=252245)

8.  [P. Ney](#ch1.xhtml#R_en1_8), K. Koscher, L. Organick, L. Ceze, T. Kohno, *Computer security, privacy, and {DNA} sequencing: compromising computers with synthesized {DNA}, privacy leaks, and more*, in: *26th USENIX Security Symposium (USENIX Security 17)*, 2017, pp. 765−779.

9.  [R. Puzis](#ch1.xhtml#R_en1_9), D. Farbiash, O. Brodt, Y. Elovici, D. Greenbaum, *Increased cyber-biosecurity for DNA synthesis*, "Nature Biotechnology" 2020, vol. 38, no. 12, pp. 1379−1381.

10.  ["philosophy](#ch1.xhtml#R_en1_10), n." OED Online. December 2022. Oxford University Press. [https://www.oed.com/view/Entry/142505?rskey=zcwcB3&result=1](https://www.oed.com/view/Entry/142505?rskey=zcwcB3&result=1) (accessed December 14, 2022).

11.  [B. Sullivan](#ch1.xhtml#R_en1_11), B. Sullivan, *Exclusive: Millions of printers open to devastating hack attack, researchers say*, November 29, 2011, [https://www.nbcnews.com/technolog/exclusive-millions-printers-open-devastating-hack-attack-researchers-say-118851](https://www.nbcnews.com/technolog/exclusive-millions-printers-open-devastating-hack-attack-researchers-say-118851)

# 第 2 章 网络威胁与必要的澄清

DOI: [10.1201/9781003408260-2](https://dx.doi.org/10.1201/9781003408260-2)

## 2.1 风险

思考网络安全时的一个关键考量因素是风险。常言道，行动伴随风险。在网络安全领域，风险可能关联许多领域和问题。它可能是业务连续性中断、数据泄露的风险，或者更广泛地说，是某种不想要事件发生的风险。风险是一种与事件发生可能性及其后果相关的现象。

存在许多风险评估方法，且它们常以专门的方式被使用。在标准情况下，我们可以使用一个公式，其中风险是影响和概率（可能性）的函数：

```
risk = impact + likelihood of occurrence
```

风险是事件发生可能性及其影响的函数。如果影响严重且概率很高，那么这种（在这种情况下为高）风险最好不要忽视。但例如，明天被 proverbial bus（意外灾祸）撞到的概率很低，尽管后果相当严重。因此——由于发生几率极低——我们将该风险评估为低。风险估算不一定非要基于简单地相加任意选定的事件权重（在最简单的情况下，概率：低、中、高；影响：低、中、高——我们可以为其分配数值：1、2、3）。关键在于风险取决于上述公式等号右侧元素的函数。这是一个非常简单的公式，尽管我们可以在其基础上构建一些非常有用的模型（包括思维模型），这些模型能提供极大帮助。例如，在确定我们应在哪些威胁上花费更多或更少时间（尤其是在无法应对所有威胁——这往往是常态——的情况下）上。这对于决定如何管理时间以及财务资源非常重要。

例如，如果风险是数据丢失，例如因网络攻击（如恶意软件感染，如勒索软件）或任何其他事件导致，那么可能的保障措施之一就是拥有这些数据的备份副本。还有其他与之相关的决策和计划。如何实施备份？如果我们是普通用户，定期将数据复制到外部硬盘是否足够？如果我们是公司，类似的解决方案是否合适？最终，或许值得考虑实施一整套备份管理系统，并决定如何配置它（例如，备份频率）。

当然，值得考虑我们想要防范的风险。如果是例如意外删除文件或实际上是勒索软件，那么外部硬盘可以物理地放在我们的电脑旁边（但不连接网络或永久连接电脑）。然而，如果我们考虑到数据中心被烧毁的风险（事故会发生，例如回顾 2021 年 OVH 数据中心火灾），甚至全面战争的威胁（回顾 2022 年乌克兰战争），那么我们的解决方案必须经过适当的设计和校准。在这种情况下，或许值得考虑地理位置分散的去中心化备份，位于远程服务器上，例如在另一大陆。这样火灾或战争的风险也会被纳入考量。

如果考虑的威胁是有人接管用户账户的控制权，安全措施之一可以是例如引入多因素认证，

