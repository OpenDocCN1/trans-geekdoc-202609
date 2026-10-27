
### 表 2.9 在第二个方块中查找 **STAGE**

```text
L A E K A H B W A G W I P T U K V S G B
E H A R H O I E H N E E E A H R E E N I
H T E T T T S T T S E L T N T R O T T
S I N D I D N I I O I A H I D D I A O N
T S R H S E O O S S O I I L R H N S S O
A A L E A A H D A C D O T E A E H H C H
L A T G A H U T A E T U W P U G O L E U
D E I S E N A A E A A R C F C S D F A A
I W W S W U B W W G W R N O S S S N G B
R N M C N P D F N I F P A C I C C B I D
U N S I N S Y R N Y R T P R M I T R Y Y

H T E T T T S T T S E L T N T R O T T
E H A R H O I E H N E E E A H R E E N I
T S R H S E O O S S O I I L R H N S S O
S I N D I D N I I O I A H I D D I A O N
L A T G A H U T A E T U W P U G O L E U
A A L E A A H D A C D O T E A E H H C H
I W W S W U B W W G W R N O S S S N G B
D E I S E N A A E A A R C F C S D F A A
U N S I N S Y R N Y R T P R M I T R Y Y
R N M C N P D F N I F P A C I C C B I D
```

### 表 2.10 从第一个方块中的 **THE TH** 和第二个方块中的 **START** 开始

```text
L A E K A H B W A G W I P T U K V S G B
E H A R H O I E H N E E E A H R E E N I
H T E T T T S T T S E L T N T R O T T
S I N D I D N I I O I A H I D D I A O N
T S R H S E O O S S O I I L R H N S S O
A A L E A A H D A C D O T E A E H H C H
L A T G A H U T A E T U W P U G O L E U
D E I S E N A A E A A R C F C S D F A A
I W W S W U B W W G W R N O S S S N G B
R N M C N P D F N I F P A C I C C B I D
U N S I N S Y R N Y R T P R M I T R Y Y

H T E T T T S T T S E L T N T R O T T
E H A R H O I E H N E E E A H R E E N I
T S R H S E O O S S O I I L R H N S S O
S I N D I D N I I O I A H I D D I A O N
L A T G A H U T A E T U W P U G O L E U
A A L E A A H D A C D O T E A E H H C H
I W W S W U B W W G W R N O S S S N G B
D E I S E N A A E A A R C F C S D F A A
U N S I N S Y R N Y R T P R M I T R Y Y
R N M C N P D F N I F P A C I C C B I D
```

其中（在顶部矩形中）必须与 Y 组合以产生密文字母 T（表 2.11）。我们总是可以这样添加字母，但除非我们相当确信它们是正确的，或者没有其他合理选择，否则真的不应该这样做。

### 表 2.11 按需添加 Y 和 K

两个矩形字母网格，带有下划线字母 Y 和 K，标明用于密码分析的位置。

我们的两段文本现在分别读作 START THE ATTACK 和 THE THOUSAND INJ... 请再次花点时间，在继续阅读之前，在上方矩形中寻找 INJ 的延续（看看这并不难）。

当然，也可以尝试扩展 START THE ATTACK，从而沿着不同的方向进行。但一般来说，补全部分单词比寻找新单词更容易，除非前面的单词是一个著名短语的开头。说到这个，很可能已经有读者认出这里使用的密钥来源了。稍后再谈。

好了，你是否已将上方文本扩展为 THE THOUSAND INJURIES？这使得下方文本读作 START THE ATTACK AT NOO。最后再看一次下方文本，我们再多扩展一个字母，然后在顶部矩形中做同样的操作。

我们现在有了消息和密钥：

```text
THE THOUSAND INJURIES O    key
START THE ATTACK AT NOON    message
```

顺便说一下，密钥是埃德加·爱伦·坡的短篇小说《阿蒙蒂拉多酒桶》的开头。

上面选择用来说明这种攻击的示例比平常稍微容易一些。二十次中有九次（45%），最有可能产生特定密文字母的字母对确实产生了该字母。实验表明，平均而言这种情况发生的概率不到三分之一。此外，该示例中只有一个密文字母（占密文的 5%）不是来自五种最可能的配对之一。这个百分比低于通常水平。

尽管如此，这是一个很棒的攻击方法。弗里德曼通过剪下各列使攻击变得更快。这允许他上下移动单个列。当他在顶部矩形的字母间看到一个单词或短语时，他可以向下瞥一眼底部矩形，并直接横着读出那里对应的字母。我使用了粗体和下划线，因为在书中这样呈现更容易，但滑动纸条在课堂演示中效果更好。

尽管弗里德曼没有进一步研究，但他的攻击方法可以扩展。可以考虑按组处理，而不是一次一个地取出密文字符。例如，假设密文以 MOI 开头。我们的表格表明：

- M 最可能是 E + I。
- O 最可能是 A + O。
- I 最可能是 E + E。

但这些表格没有考虑上下文。为 O 建议的顶部配对没有考虑密文中在其之前或之后出现的字母。将字母 MOI 作为一个组，并使用三字母组频率对可能性进行排序，我们看到它最有可能来自 THE + THE。

当时还是本科生的克里斯蒂安·N.S. 泰特和我研究了这种新攻击。我们将密文分成字符组，并使用该组大小的字母组合频率对我们的配对进行排序。例如，如果密文是 HYDSPLTGQ，并且我们使用三个字符一组来发起攻击，我们会将密文拆分为 HYD SPL TGQ，并用最有可能产生每个三字母组的配对替换它。

这个想法需要验证，而最简单的验证方式是编写计算机程序进行计算并分析结果。我们测试了单字符分析（如弗里德曼所做）、双字母组、三字母组、四字母组、五字母组和六字母组。

我原本以为，结果出来后，我可以将新攻击与弗里德曼的攻击进行比较，并说：“我所做的是件好得多得多的事。”然而，事实并非如此。结果只是略有改善！我们试图在报告中尽可能以最佳方式呈现结果。考虑到即使对弗里德曼的工作有最微小的改进也值得发表，我们提交了论文。一位好心的编辑在稍作修改后接受了它。

幸运的是，北卡罗来纳州立大学生物信息学博士项目的学生亚历山大·格里芬看到了这篇论文，并将这种攻击变成了真正成功的方法。他这样做不仅仅是将密文字符块一个接一个地取出来，而是在计算最可能的解时还考虑它们的重叠部分。25 因此，在考虑密文 HYDSPLTGQ 时，格里芬的方法不仅仅关注 HYD、SPL 和 TGQ 如何产生，而是关注 HYD、YDS、DSP、SPL、PLT、LTG 和 TGQ。他的论文中复制的图如图 2.15 所示。它表明，对于所考虑的每一种大小的字母组，他的方法都比泰特和我提出的方法更好，并且在使用五字母组和六字母组时效果显著更好。

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_118_0.png)

图 2.15 格里芬的结果（实线）与其他人早期尝试（虚线）的比较。

利用本章讨论的技术，任何长度的滚动密钥密码都可以被破解；然而，极短的消息不太可能有唯一解。图 2.16 中的图显示了潜在解的数量如何随消息长度的变化而变化。超过八个字符，我们预计只有一个解。

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_118_1.png)

图 2.16 虚假解译数量与消息大小的函数关系。（引自 Deavours, Cipher A., “Unicity Points in Cryptanalysis,” Cryptologia, Vol. 1, No. 1, January 1977, pp. 46-68, 此处引用第 62 页。）

## 2.7 一次性密码本或弗纳姆密码

众所周知，维吉尼亚密码很容易被破解，因为关键词重复造成了弱点。修改该系统使密钥永不重复，就得到滚动密钥密码。虽然针对维吉尼亚密码成功的攻击无法击败新系统，但正如我们所见，还有其他有效的攻击。这次的弱点是密钥和消息都由有意义的单词组成。因此，对于那些寻求使密码安全的人来说，下一步似乎显而易见——使用由随机选择的字母组成的滚动密钥。这样的系统能够抵抗
