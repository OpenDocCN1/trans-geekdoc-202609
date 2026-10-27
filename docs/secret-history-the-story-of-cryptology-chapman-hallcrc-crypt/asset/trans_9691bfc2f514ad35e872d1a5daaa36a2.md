

| 12↔20 | 8↔2 | 7↔4 | 13↔19 | 18↔14 | 3↔9 | 10↔15 | 11↔17 | 1↔16 | 6↔5 |
|---|---|---|---|---|---|---|---|---|---|
| DG | FA | XF | XX | E | AD | E | XD | AG | DF |
| T | DA | FD | FG | E | FD | XF | FG | E | XF |
| FF | DG | GA | T | DA | DD | FD | E | DA | FD |
| FF | E | AA | FA | DA | FA | XF | XX | E | XF |
| T | DA | DF | E | T | DG | AF | E | DA | FG |
| XF | DF | DA | T | FA | E | FG | AF | XF | GG |
| E | AF | GD | FF | DG | DD | E | GG | DG | DD |
| DD | DG | GF | AG | FF | T | DG | GG | DA | DF |
| T | DG | DF | T | E | DF | GG | T | DA | GG |
| DA | XF | DF | GD | T | FA | DG | DF | XD | XF |
| AD | DA | AG | T | T | FA | E | AF | DA | DD |
| GF | DA | AG | FG | GA | E | T | FA | E | FF |
| DG | GA | T | DG | GA | AF | E | FG | E | FF |
| GD | XF | XD | XF | AF | E | DG | AA | DG | FF |
| FF | AF | XF | DX | E | DG | T | XF | DF | GG |
| T | FA | E | DF | T | E | XF | FG | DG | T |
| T | DA | FD | DG | E | GF | E | GA | XF | DF |
| GG | DD | FF | AG | GA | FA | T | FA | E | FD |
| DG | E | GF | E | GA | GG | DA | AA | DF | T |
| FA | E | T | DA | DG | FF | E | T | DG | XF |
| AF | XF | XD | DA | DA | GG | AF | XF | DF | T |
| FA | E | FF | DG | GA | T | AF | E | XF | DF |
| GA | DF | DA | T | FA | DG | DF | XD | T | FA |
| E | GF | E | FF | FF | XF | FG | AA | DG | FF |
| FF | GA | T | XF | GD | GF | FF | DA | GA | E |
| GG | DD | DA | FG | E | XX | E | FG | DG | AA |
| DG | FF | FF | DF | DA | T | DA | FD | E | DF |
| DG | T | XF | XD | XF | DG | DF | DG | GA | AA |
| E | XF | FG | AD | GD | XF | FF | FF | T | FA |
| XF | T | GA | FA | DA | FF | GD | DG | XF | AF |
| XF | XD | DA | DA | GG | AF | XF | DF | T | FA |
| E | FF | DG | GA | T | DG | GA | FF | DA | DF |
| XD | E | FG | T | FA | XF | DF | DG | FA | XF |
| GG | E | FX | FD | E | GF | T | E | GG | FX |

最后一列在第 19 位有一个 T。 当从这个矩形中读出明文时，该行的末尾会延续到第 20 行的开头，在那里我们有 HE。 这表明剩余三个列的放置很理想。

如果把 12↔20 8↔2 7↔4 放在末尾则不会得到如此理想的结果，把 7↔4 8↔2 12↔20 放在任一端也一样。 因此，我们假设现在已经得到了列的正确顺序，并且我们正确地识别出了 T、H 和 E。 请记住，这一切都是案例 1b 的一部分。 如果我们遇到僵局，我们就会回溯考虑案例 1a 甚至案例 2，但由于事情似乎进展顺利，所以没有必要。

我们填入全部 19 个 H 以得到下面的部分明文：

DG H XF XX E AD E XD AG DE
T DA FD FG E FD XF FG E XF
FF DG GA T DA DD FD E DA FD
FF E AA H DA H XF XX E XF
T DA DF E T DG AF E DA FG
XF DF DA T H E FG AF XF GG
E AF GD FF DG DD E GG DG DD
DD DG GF AG FF T DG GG DA DF
T DG DF T E DF GG T DA GG
DA XF DF GD T H DG DF XD XF
AD DA AG T T H E AF DA DD
GF DA AG FG GA E H E FF
DG GA T DG GA AF E FG E FF
GD XF XD XF AF E DG AA DG FF
FF AF XF DX E DG T XF DF GG
T H E DF T E XF GG DG T
T DA FD DG E GF E GA XF DF
GG DD FF AG GA H T H E FD
DG E GF E GA GG DA AA DF T
H E T DA DG FF E T DG XF
AF XF XD DA DA GG AF XF DF T
H E FF DG GA T AF E XF DF
GA DF DA T H DG DF XD T H
E GF E FF FF XF FG AA DG FF
FF GA T XF GD GF FF DA GA E
GG DD DA FG E XX E FG DG AA
DG FF FF DF DA T DA FD E DF
DG T XF XD XF DG DF DG GA AA
E XF FG AD GD XF FF FF T H
XF T GA H DA FF GD DG XF AF
XF XD DA DA GG AF XF DF T H
E FF DG GA T DG GA FF DA DF
XD E FG T H XF DF DG H XF
GG E FX FD E GF T E GG FX

从这里开始解密有许多种方法。 问题已简化为没有词间隔的波利比乌斯密码。 可以应用元音识别算法（如第 1.11 节所示），也许在几次猜测后，所有的 A、O 和 I 都可以填入。 从那里开始，应该很容易猜出几个词。 解密过程随后会迅速加速。 其他方法也是可能的。 最终，这取决于你，因为最后的步骤被留作练习。

如果矩形没有完全填满，本例中使用的方法就不会如此理想地奏效（尽管可以修补）。 然而，如果换位密钥的长度为 20，则 5% 的消息碰巧会完成一个矩形。 在不知道密钥长度的情况下，可以对每条消息尝试这种攻击，一旦找到密钥，其他消息可能很容易被破解。 考虑到每场战争中流动的大量消息，5% 将为密码分析员提供大量工作。

直到 1966 年，ADFGVX 的创造者 Fritz Nebel 才得知他的系统已被破解。 他评论道：^16

> 我个人更希望第二阶段采用双重换位而不是单次换位，但在与无线电报和破译主管的讨论中，这一想法被否决了。 结果是技术和战术考虑之间的妥协。 双重换位会更安全，但实践中太慢也太困难。

Nebel 于 1968 年会见了 Painvin。 他将其描述为“昨日的敌人作为今日的朋友相会”。 在这次会议上，Painvin 回忆道，“我告诉他，如果他得逞并且他们使用了双重换位，我就永远无法取得突破。”^17

在之前的战争之后，美国的间谍和密码破译员回到了服役前所过的生活，但美国现在正进入一个设立永久机构来处理此类活动的时代。 在这方面，美国落后于欧洲人，道路上仍会有一些坎坷，但该国正在建立情报帝国的道路上。

William Friedman 在他从 Riverbank Laboratories 的工作过渡到政府时将发挥重要作用。 我们很快会再谈到他，但现在我们先来看看 Herbert O. Yardley 的贡献和争议。

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_208_0.png)

**Figure 5.4**  **Herbert O. Yardley（1889–1958）。** (http://www.nsa.gov/about/_images/pg_hi_res/yardley.jpg.)

## 5.4 Herbert O. Yardley

我们现在来到密码学世界中也许最具色彩的人物。 Herbert O. Yardley（图 5.4）可以被称为密码学的 Han Solo。 他常被描述为赌徒、酒鬼和花花公子，关于他对美国的忠诚度的争论仍在继续。 虽然两人对美国都有重要的密码分析工作，但 Yardley 和 Friedman 在几乎每个方面都形成鲜明对比。 Friedman 非常整洁，甚至可以说是衣冠楚楚。 Yardley 常常邋遢，有时会穿着内裤浇花。 他去世时甚至没有一条领带；
一条被给了他的遗孀，让 Yardley 穿着下葬。<sup>18</sup> Yardley 是反犹太的，而 Friedman 是犹太人。<sup>19</sup> Friedman 有一段长久、看似幸福的婚姻，但给人的印象是他与女性相处并不很有自信。 另一方面，Yardley 完全不害羞。 他甚至吹嘘自己懂得在中国妓院中游走，并在中国期间为来访的记者和外交官举办群交派对。<sup>20</sup> 虽然这通常不是一个好的指标，但即使他们的笔迹也体现了他们截然不同的个性（图 5.5 和 5.6）。

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_209_0.png)

**Figure 5.5** Friedman 家族精确的笔迹。 *(摘自作者收藏。)*

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_209_1.png)

**Figure 5.6** Yardley 粗糙的潦草字迹。 *(摘自作者收藏。)*

Yardley 在国务院起步时担任非密码职位； 他只是电报员和密码文员，但由于能够接触到加密消息，包括发给威尔逊总统的消息，他尝试破解它们。 他最终为他的上司制作了一份报告“Solution of American Diplomatic Codes”。 他的成功有力地证明了需要改进美国密码局，或黑室的需求，而他的自我推销技巧使他在 1917 年被提拔为战争部下属这个新组织的负责人，正式称为密码局。 黑室在欧洲历史上发挥过重要作用，但在美国此类密码分析单位是新的。 在 18 个月内，Yardley 的团队（军事情报第 8 部分，或 MI-8）阅读了 579 种密码系统中近 11,000 条消息。 这甚至更令人惊讶

<sup>18</sup> Kahn, David, *绅士邮件的阅读者*, 耶鲁大学出版社, New Haven, Connecticut, 2004, p. 288.<br><sup>19</sup> Kahn, David, *绅士邮件的阅读者*, 耶鲁大学出版社, New Haven, Connecticut, 2004, pp. 88 and 146.<br><sup>20</sup> Kahn, David, *绅士邮件的阅读者*, 耶鲁大学出版社, New Haven, Connecticut, 2004, p. 196.

^16 Norman, Bruce, “ADFGVX 的人,” *星期日泰晤士报杂志*, August 11, 1974, pp. 8–15, p. 11 此处引用。
^17 Norman, Bruce, “ADFGVX 的人,” *星期日泰晤士报杂志*, August 11, 1974, pp. 8–15, p. 15 此处引用。
