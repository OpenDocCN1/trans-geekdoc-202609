
这项研究基于尝试通过互联网流量公司[`alexa.com`](http://alexa.com)以及其他来源提供的互联网数据（Alexa, 2019）来对 DDoS 攻击进行特征描述。由于该服务提供了大量数据，我们尝试建立一个数据库，不仅提供有关 DDoS 攻击行为的信息，还提供有关网站流量其他异常行为的信息。图 25.2 显示了[`alexa.com`](http://alexa.com)报告中“访问量”的结果，即全球互联网用户的估计百分比。流量报告中的参数是横轴上的时间（`t`），以天为单位，以及访问量（`r`），根据[`Alexa.com`](http://Alexa.com)，代表访问[`doj.gov`](http://doj.gov)（即美国司法部网站）的用户比例。

![](img/93419.jpg)

特别是图 25.2 显示了 2011 年六个月内司法部网站的流量水平。

很容易看到 2012 年下半部分的流量中存在明显的异常。我们在书前面的章节（第 1 章）描述过，在维基发布了来自美国陆军士兵切尔西·曼宁的大量文件后，由于攻击者试图通过 DDoS 攻击击垮维基，引发了一场“网络战争”。在失败后，维基的支持者为了报复发动了 DDoS 攻击并击垮了司法部网站，如图 25.2](#33_Chapter_25.xhtml#Anchor-6)所示。

该 DDoS 攻击在同一时期也针对 FBI 网站被复制，如图 25.3](#33_Chapter_25.xhtml#Anchor-7)所示。

![](img/93454.jpg)

## 25.4 魔幻数字七 (#06_Contents.xhtml#r_idParaDest-332)

在计算机普及很久很久，哈佛大学心理学家乔治·米勒（George Miller）写的一篇论文就证明了一些原则，这些原则在多年后对网络安全产生了巨大的影响。

这篇名为《神奇数字七，加减二》（Miller, 1956）的论文最初对电话系统的号码分配设计产生了影响，随后又影响了计算机密码制定规则的设计。

米勒证明了，普通人类记忆随机信息片段或“块”（chunks）的能力集中在七个不同的信息单元上。

追溯到 20 世纪 40 年代，大多数电话系统的号码由四位数组成，然后是五位数，再接着加上一个指示电话所在地所在区域的两个字母代码。

在旧的电影、电视和音乐中，仍留有该系统分配的电话号码残迹。经常重播的电视喜剧《我爱露西》（I Love Lucy）中里卡多住所使用了一个虚构的电话号码`MU 5-9975`（`MU`代表 Murray Hill，是曼哈顿一个真实的电话交换区）；20 世纪 40 年代的一首流行歌曲是《`PE 6-5000`》（读作`PEnnsylvania 6-5000`或“宾夕法尼亚-六-五-零-零”）；以及 20 世纪 50 年代由伊丽莎白·泰勒主演的热门电影《巴特菲尔德》（Butterfield 8）使用的是虚构电话交换机`BU 8-xxxx`。

该系统的优势在于，用户基本上只需要记住六个信息“块”：交换区名称以及后续五个数字。

到了 20 世纪 50 年代，开头的两个字母代码被两个数字取代（通常是与字母代码对应的电话拨号数字——因此 Murray Hill 的`MU`变为了“68”，使得里卡多住所的`MU 5-9975`变为了`685-9975`）。但对于新用户来说，这意味着要记住七个信息块，而不是旧系统中的六个。根据米勒的研究，这仍然意味着记忆电话号码七个独立信息单元的能力在正常记忆范围内。20 世纪 60 年代又引发了更复杂的情况，当时长途直拨变得可能，电话号码现在变成了 10 位 de- 位数字。根据米勒的研究，这会造成困难，除非拨打同一区号的用户不需要为他们经常拨打的区域学习新的三位代码。

米勒的研究及后续观察的本质是一系列先前的实验，要求受试者在对象数量逐渐增加的情况下区分或识别不同的对象。在他所报告的几乎所有研究中，当呈现的对象数量接近七时，受试者识别所观察到的对象精确数量的能力往往会迅速下降。他研究中的几个例子包括：

1. `Pollack (1953)`要求听者通过为音调分配数字来识别听觉音。当每个音调播放时，听者用数字做出反应。当实验仅包含`2`到`4`个不同音调时，很少出现识别错误。随着音调数量增加到`5`到`14`之间，听者犯了许多错误。正确识别的数量达到大约六的水平；作者将此称为受试者音高判断判断通道容量。

2. `Garner (1953)`：在这个例子中，测试针对的是声音的响度。他在`15`到`110 dB`（分贝）之间设置了若干强度不同的音调，并使用了`4`到`20`种不同的强度。

3. `Beebe, et al. (1955)`：在这种情况下，测试针对的是味觉。

4. `Hake and Garner (1951)`：在这个例子中，测试针对的是位置。

总而言，在网络安全背景下，密码的性至关重要。

- **密码句（Passphrases）**：与其使用上述长字符串，不如创建一个短表达式，例如使用短语中每个单词的首字母。因此，Abe 的长密码将变成`fsasyaof`（或者，另一种变体为`fsa7yaof`）。现在这个密码足够短，可以记住看起来像随机字符串的内容，但用户在人类记忆中拥有了那个更著名的长表达式，并记得只取短语中每个单词的首字母的规则。如果用户选择的短语很容易根据对该用户的了解而推断出来，这里就会出现缺陷。

也可以成为一名“电影评测员”，学习关于密码正确构建的其他观点。例如，在 YouTube 上可以找到几个视频。

### 身份盗窃宣言：

[`www.youtube.com/watch?v=LOJnBI1HDn4`](https://www.youtube.com/watch?v=LOJnBI1HDn4)

### Kelsey Dobish 和 Trey Shafto：

[`www.youtube.com/watch?v=jWablPsy6ng`](https://www.youtube.com/watch?v=jWablPsy6ng)

### Endsight Corporation：

[`www.youtube.com/watch?v=UnmdxReVoNc`](https://www.youtube.com/watch?v=UnmdxReVoNc)

### Sophos Corporation 的 Graham Cluley：

[`www.youtube.com/watch?v=VYzguTdOmmU`](https://www.youtube.com/watch?v=VYzguTdOmmU)

我们的学生对其中许多网站进行了“评测”，正如我们将在下一节中描述。

我们倾向于使用的建议是选择一个相对短但容易记忆的事件，这样它就会被深深地烙印在我们的意识中，但对于那些想要研究我们历史的人来说，它并不广为人知。假设多年前，我与某人、某地或某物有过一次难忘的相遇——假设是“Penobscot”，这实际上是缅因州的一条河。

此外，在这种情况下，我没有告诉任何人我在那条特定的河流度过一些时间——所以任何认识我的人都不会产生这样的联系。所以现在这是一个我不可能忘记的密码——但遗憾的是，有针对河流名的字典可以用于随机攻击以获取我的密码。为了仍然使用“Penobscot”但将其从此类攻击隔离开来，我可以在密码中插入其他字符，这样只需通过河流名称字典测试密码，我们可能就可以使用例如`penob7scot`作为密码来偏转这种攻击。

除了这个例子之外，任何用户开发一个此类易记忆的单词列表都是明智的，而且当以上述方式对其进行修改时，它们将击败任何基于某些常用字典词汇的攻击。

## 25.6 密码创建视频：电影评测

很清楚，使用密码进行身份验证的主要问题与人类记忆面临的挑战有关，即如何深层嵌入密码的选择，或者在某个特定用户所需的多个密码中进行选择的挑战。我们在上面已经介绍了一些选择良好密码的原则。

此外，通过无处不在的 YouTube，许多个人和组织拍摄并发布了他们关于如何创建良好密码的自己的处方。最后统计，可以找到至少 14 个独立的 YouTube 视频，解释了选择良好密码的方法。

我们将问题抛给我们的学生，以评估 YouTube 网站上易于获取的信息质量和视频质量。

我们提供了学生对其中许多视频的批评总结（参见图 25.5 到 25.8）。

![](img/025x005_fmt.jpeg)

（来自 身份盗窃宣言）

- 这个视频提供了很多有用信息。它讨论了可猜测的信息不是一个良好的密码，还讨论了大小写字母以及符号、字母和数字的组合是良好的密码。PH

- 但是，他们告诉你要把它写下来，这并不是一个那么好的主意。

- 差评。视频太长了。视频看起来制作得很糟糕（从歌曲到视频剪辑以及中间的一切）。OO

- 她太夸张了。

- 她的语气很烦人。

- 我觉得这些信息太明显了。

- 背景音乐让人分心。SS 

![](img/025x006_fmt.jpeg)

（来自 Kelsey Dobish 和 Trey Shafto）

- 这个视频提供了我目前为止听过的关于密码最好的主意：使用与你相关/易记忆的短语。PH

- 视频不是最好的，但内容很不错。它确实为观众提供了一种创建安全密码的体面方法。OO

- 视频很抖。SS

![](img/025x007_fmt.jpeg)

（来自 Endsight Corporation）

- 创建者提供了一种创建相对安全密码的体面方法。我觉得趣的是：使用提供的网站查找密码的强度，短语“我 1972 年出生在旧金山”需要计算机“402 万亿（QUINDECILLION）年”来破解，而`IwbiSFi1972.`则需要“6 万年”来破解。OO

- 一个非常好的视频！

![](img/025x008_fmt.jpeg)

（来自 Sophos Corporation 的 Graham Cluley）

- 视频制作得很好。和第二个、三个视频一样，它提供了创建密码的方法。OO

- 有用信息。

- 他的口音可能让人困惑。SS

（感谢学生 Portia Herndon, Ougo 和 Shanay Saddler。）

## 25.7 密码检测

另一种创建和使用安全密码的方法是通过互联网网站上的许多所谓的“密码检测器”。

特别是，我们检查了五个密码检测器候选。在每种情况下，通过特定的网站输入密码，并生成关于密码强度的报告。它们显示在表 25.3 中。

| 表 25.3 密码检测器网站 |

| --- |

| 密码器标识 | 名称 |

| A | [`passwordmeter.com`](https://passwordmeter.com) |

| B | [`lastpass.com/howsecure.php`](https://lastpass.com/howsecure.php) |

| C | [`my1login.com/resources/password-test/`](https://my1login.com/resources/password-test/) |

| D | [`thycotic.com/resources/password-checker/`](https://thycotic.com/resources/password-checker/) |

| E | [`howsecureypassword.net/`](https://howsecureypassword.net/) |

遗憾的是，我们经常发现，由任何一个密码检测器判断的密码强度，与一个或多个其他候选对象对相同密码的判断可能完全不同。

测试建议的密码检测器有效性的一种方法是向每个候选者提交一些可能的密码并检查结果的一致性。

为了测试，假设我们使用表 25.4 中的密码选择。

| 表 25.4 用于评估密码检测器的密码 |

| --- |

| 测试密码 | 特征 |

| 11111111111111111111 | 一个相当简单但很长的字符串。输入很麻烦。 |

| Penob7scot | 在某些类型的字典中找到的单词，例如美国地名字典，插入了数字以击字典攻击。 |

| x3p9q!m | 看起来是随机的字符串，但可能很难记忆。 |

| brittttany | 人的名字，某个字母重复（T）。可能容易记忆。 |

| onomatopoeia | 一个长词，但在大多数字典中都有。 |

| aBc123xYz | 遵循模式，但字母、数字和大小写的混合可能证明很强，且在这种情况下可能容易记忆。 |

Merriam-Webster 对 onomatopoeia 的定义

1. 通过模仿与其相关的声音对某物或动作进行命名（例如`buzz`嗡嗡声、`hiss`嘶声），也称为：由拟声词组成的词。在漫画书中，当你看到有人拿着枪时，只有当你读到拟声词时才知道它正在开火。“Christian Marclay。

2. 使用其声音暗示意义的词汇：对诗人拟声词的研究。

上述所建议的这些密码在五个密码强度计网站（A–E）上的测试结果如 表 25.5 所示。我们将在“黑客实验室 4”中回到这一部分，第 26 章 (表 25.5)。

| 表 25.5 密码强度计比较 |

| --- |

| ![94564.jpg](img/94564.jpg) |

| 注意：每个密码强度计通常显示密码强度的非数值度，例如“弱”、“中等强度”、“良好”等。此外，强度计还会显示一个代表破解密码预计所需时间的数值。 |

## 参考文献

- Alexa. 2019. [`www.alexa.com`](http://www.alexa.com)

- Banks, K. et al. 2012. 选择国家的 DDoS 和其他异常网络流量行为。Proceedings of IEEE SoutheastCon 2012, 2012 年 3 月 15–18 日, 佛罗里达州奥兰多。

- Beebe-Center, J. G., Rogers, M. S., and O’Connell, D. N. 1955. 通过味觉传输关于蔗糖和盐水的信息。The Journal of Psychology, 39, 157–160。

- Dominguez, K. 2011. 发现 DDoS 能力的比特币矿僵尸网络。Malware Blog, 9 月 4 日。[`blog.trendmicro.com/bitcoin-mining-botnet-found-with-ddoscapabilities/`](http://blog.trendmicro.com/bitcoin-mining-botnet-found-with-ddoscapabilities/)

- Garner, W. R. 1953. 绝对响度判断的信息学分析。The Journal of Experimental Psychology, 46, 373–380。

- Hake, H. W. and Garner, W. R. 1951. 呈现不同数量离散步骤对刻度读取准确性的影响。The Journal of Experimental Psychology, 42, 358–366.

- Mick, J. 2011. LulzSec 攻击 CIA 公共网站，似乎是陷阱尝试的目标。Daily Tech, 6 月 15 日,[`www.dailytech.com/LulzSec+Downs+CIAs+Public+Site+Appears+to+be+Subject+of+Framing+Attempt/article21916.htm`](http://www.dailytech.com/LulzSec+Downs+CIAs+Public+Site+Appears+to+be+Subject+of+Framing+Attempt/article21916.htm)

- Miller, G. 1956. 魔法数字，加或减二：我们处理能力的某些限制。Psychological Review, 63, 81–97.

- Mutton, P. 2011. LiveJournal 遭受 DDoS 攻击。Performance, 4 月 4 日,[`news.netcraft.com/archives/2011/04/livejournal-under-ddosattack`](http://news.netcraft.com/archives/2011/04/livejournal-under-ddosattack)

- Pollack, I. 1953. 编码信息的同化。American Journal of Psychology, 66, 421–435.

- Poulson, K. 2010. 针对 WikiLeaks 的网络攻击很弱。wired.com, 11 月。

- Singel, R. 2011. FBI 针对支持 WikiLeaks 的攻击追踪匿名者。Wired.com, 1 月 28 日。[`arstechnica.com/tech-policy/2011/01/fbi-goes-after-anonymous-for-pro-wikileaks-attacks/?comments=1`](https://arstechnica.com/tech-policy/2011/01/fbi-goes-after-anonymous-for-pro-wikileaks-attacks/?comments=1)

- WISC. 2011. 2010 年全球基础设施安全报告。马萨诸塞州切尔姆斯福德: Arbor Networks。

- WISC. 2012. 2011 年全球基础设施安全报告。马萨诸塞州切尔姆斯福德: Arbor Networks。

### 问题

#### 25.1 使用 ABCD 方法对以下内容分类：

| 犯罪/恶意软件 | A, B, C 或 D |

| --- | --- |

| 扒手 | |

| 伪造学生成绩 | |

| 莫里斯蠕蠕虫 | |

| 脚本小子 (Script kiddies) | |

#### 25.2 在司法部网站 ([https://www.justice.gov/news?f[0]=field_topic:3911](https://www.justice.gov/news?f[0]=field_topic:3911)) 上，找到 2017–2018 年涉及以下内容的案件数量：

a. 黑客攻击

b. 钓鱼

c. DDoS

d. 勒索软件
