

检验这些数值时，似乎对所有 $n$ 都有 $li(n) > π(n)$；然而，事实并非如此。虽然这个数值大得离谱，但总有一个点，$li(n)$ 会从高估转变为低估。南非数学家斯坦利·斯皮克斯（Stanley Skewes）研究了这种转变发生的位置。他无法确定一个精确值，但确实找到了一个界限。这种转变发生在 $e^{e^{e^{79}}}$ 之前的某处。这个界限假设黎曼猜想成立。⁵ 如果不做这个假设，斯皮克斯找到了更大的界限 $10^{10^{10^{963}}}$。⁶ 在斯皮克斯进行计算之前，人们就已经知道 $li(n)$ 最终会再次变回低估。事实上，它会在高估和低估之间无限次地切换！⁷ 多年来，斯皮克斯的数字一直保持着“曾用于实际用途（即在证明中使用）的最大数字”的纪录，但后来它们被其他数值所超越。它们也在另一个方面被削弱了——对于 $li(n)$ 首次转变为低估的位置，已经找到了小得多的界限。

然而问题依然存在：我们如何找到或生成大的素数？*素性检验*关注的是判定一个给定的数是否为素数。对于最快的测试来说，揭示一个数不是素数时，不会透露任何因子。它们就像非平凡真因子存在性定理。

我们首先看一些概率性检验。这些检验有时能证明一个数是合数，但它们永远无法完全证明素性。它们最多只能以任意高的概率暗示素性。

## 16.2 费马检验

回忆一下费马小定理（1640年）：

$$\text{如果 } p \text{ 是素数且 } a \text{ 不是 } p \text{ 的倍数，则 } a^{p-1} \equiv 1 \pmod{p}.$$

这提供了一个可能显示某个数为合数的检验：如果 $(a,n)=1$ 且 $a^{n-1} \ne 1 \pmod n$，那么 $n$ 不可能是素数。然而，如果结果是 1，我们也无法断定 $n$ 是素数。费马小定理并不是一个“当且仅当”定理。

和往常一样，费马并没有给出证明。第一个给出证明验证这一点的数学家是戈特弗里德·莱布尼茨。关于 $a=2$ 的特殊情况，早在公元前500年中国人就已经知道了，但他们没有费马所提供的推广形式。

要检验一个数 $n$ 的素性，我们可以使用集合 $\{2, 3, 4, \ldots, n-1\}$ 中的值作为 $a$。如果其中任何一个产生的结果不是 1，我们就知道 $n$ 是合数。使用重复平方的指数运算技术可以加快这些计算的速度。

1910年，人们将以他的名字命名这类数。前几个卡迈克尔数¹⁰ 是 561, 1105, 1729, 2465, 2821, 6601, 8911, 10585,… 

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_496_0.png)

**图 16.1　罗伯特·卡迈克尔（Robert Carmichael, 1879–1967）。**（图片来自 [https://web.archive.org/web/2012003061628/http://www.maa.org/aboutmaa/carmichael.gif](https://web.archive.org/web/2012003061628/http://www.maa.org/aboutmaa/carmichael.gif)¹¹，版权归美国数学协会（Mathematical Association of America）所有，2012年。保留所有权利。）

小于 10²¹ 的卡迈克尔数仅有 20,138,200 个，约占总数的 0.000000000002%。¹² 因此，随机选取的一个数是卡迈克尔数的概率非常小。尽管如此，我们还是希望有一种不会被这些数欺骗的素性检验。

## 16.3 米勒–拉宾检验¹³

这是检验RSA加密所需的大数是否为素数的最流行的方法。为了检验 *n* 是否为素数，我们首先找出能整除 *n* − 1 的 2 的最高次幂。我们将这个次幂记为 *t*，然后定义 *d* = (*n* − 1)/(2ᵗ)。我们有 2ᵗ*d* = *n* − 1。（注意 *d*

¹⁰ “A002997, Carmichael numbers: composite numbers *n* such that a^(*n* − 1) = 1 (mod *n*) for every *a* coprime to *n*.” *The On-Line Encyclopedia of Integer Sequences®*, https://oeis.org/A002997.

¹¹ 这个网站是点击 https://web.archive.org/web/20120214210612/http://www.maa.org/aboutmaa/maapresidents.html 中的链接得到的。其他链接指向美国数学协会1916年至2010年历任主席的照片。卡迈克尔于1923年担任主席。

¹² Pinch, Richard G. E., *The Carmichael Numbers up to 10²¹*, May 15, 2007, 可在 http://s369624816.websitehome.co.uk/rgep/p82.pdf 在线获取。

¹³ Weisstein, Eric W., “Primality Test,” *MathWorld*, a Wolfram Web Resource, https://mathworld.wolfram.com/PrimalityTest.html 将其称为 Rabin–Miller 检验，Bruce Schneier 在《Applied Cryptography》第二版第259页也如此称呼。Richard A. Mollin 加了一个名字，将其称为 Miller–Rabin–Selfridge。他解释说 John Selfridge 应当获得这一认可，因为他在1974年就使用了这一检验，早于 Miller 发表。参见 Mollin, Richard A., *An Introduction to Cryptography*, Chapman & Hall / CRC, Boca Raton, Florida, 2001, p. 191. 如果你完全不想提及名字，它也被称为*强伪素数检验*。无论你选择怎么称呼它，主要参考文献是 Rabin, Michael O., “Probabilistic Algorithm for Testing Primality,” *Journal of Number Theory*, Vol. 12, No. 1, February 1980, pp. 128–138.

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_498_0.png)

**图 16.2** 迈克尔·O·拉宾（Michael O. Rabin, 1931–）。拉宾与其他两人分享了100万美元的丹·大卫奖（Dan David Prize）。（来自 SEAS，Michael O. Rabin Wins Dan David Prize: Computer Science Pioneer Shares $1 Million Prize for Outstanding Achievements in the Field [新闻稿]，哈佛工程与应用科学学院，2010年2月16日。）

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_498_1.png)

**图 16.3** 加里·L·米勒（Gary L. Miller）。（[http://www.cs.cmu.edu/~glmiller/](http://www.cs.cmu.edu/~glmiller/)）。

ScratchPad.<sup>14</sup> 这类实现将检验应用于一小组基。通过所有这些检验的合数是 1195068768795265792518361315725116351898245581。然而，Arnault 指出，在他找到这个例外之后，ScratchPad 得到了改进，并更名为 Axiom，采用了一种新的素性检验，不单纯是 Miller–Rabin 检验，并且能识别出上述数是合数。

<sup>14</sup> Arnault, François, “Rabin-Miller Primality Test: Composite Numbers Which Pass It,” *Mathematics of Computation*, Vol. 64, No. 209, January 1995, pp. 355–361.

一个引人入胜的可能性是，可能存在一个能捕获所有合数的混合系统。换句话说，我们可能有两个检验，每个都会漏掉某些数，但如果这些漏掉的数集之间没有交集，那么同时通过两个检验就能保证素性。

### 16.3.1 生成素数

用于RSA的大素数的实际生成通常按以下步骤进行：

- 1. 生成所需位数的随机比特串。确保第一位是 1，以保证该数具有最小大小；并确保最后一位是 1，这样该数就不是偶数（因而不是合数）。
- 2. 检验该数，确保它不能被任何小素数（例如小于一百万的素数）整除。
- 3. 应用米勒–拉宾检验足够多轮，以获得接近 1 的素性概率。

现在我们来看一些保证能给出正确答案的检验。这些被称为*确定性检验*。与概率性检验不同，它们没有不确定性。缺点是它们没有米勒–拉宾检验那么快。

## 16.4 确定性的素性检验

一个引向确定性素性检验的古老结果是威尔逊定理：

设 *n* 为正整数。那么 *n* 是素数，当且仅当 $(n−1)! \equiv −1 \pmod n$。

这个结果以英国数学家约翰·威尔逊（John Wilson, 1741–1793）的名字命名，尽管他不是第一个发现、发表或证明它的人。这些成就分别归于莱布尼茨、华林¹⁵ 和拉格朗日¹⁶。

威尔逊定理很优雅，但它并不是一种快速的素性检验方法！概率性检验虽然不那么令人满意，但在时间节省巨大的情况下更为实用。

伦纳德·阿德尔曼（Leonard Adleman）与卡尔·波梅兰斯（Carl Pomerance）和罗伯特·S·鲁梅利（Robert S. Rumely）在1983年开发了一种确定性的素性检验，在一段时间内是同类算法中最快的。它没有米勒–拉宾检验快，但确实提供了绝对的确定性。¹⁷ 阿德尔曼和黄（Huang）使用椭圆曲线提供了另一种确定性检验，但与概率性检验相比，该检验耗时过长，难以接受。

### 16.4.1 AKS素性检验（2002年）

最终在2002年，第一个确定性的多项式时间素性检验由曼indra·阿格拉瓦尔（Manindra Agrawal）教授和他的两个学生尼拉杰·卡亚尔（Neeraj Kayal）和尼廷·萨克塞纳（Nitin Saxena）（图16.4）在印度

