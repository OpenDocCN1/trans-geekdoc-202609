

# 加密印记

每小时创建的加密哈希字符串数量，超过了人类历史上制作的所有印记总和。数十亿次穿越数学空间的映射，用以建立、隐藏并传达身份。它们的共识现实地位，以及作为数学客体柏拉图理念世界导出物的身份，使它们成为理想的魔法素材。

完整的 32 字节 `SHA-256` 哈希值难以记忆，尽管做到这一点可能是一种仪式性的壮举。将其抽象为前几位数字可能就足够了，就像 Git 提交所做的那样。[^1] 我们不必使用十六进制（基数 16：`0123456789ABCDEF` 而非基数 10：`0123456789`）数字字符串，那是哈希函数通常的人类可读输出。HTML 风格的颜色可以用三位或六位十六进制数字表示，例如蓝色是 `0000FF` 或 `00F`。因此我们可以用哈希值的前六位数字来选择一种独特的颜色。[^2]

例如：

```
echo this is my intent | sha256sum
```

```
1b0fd74346abfe6858b12b8e3036649a63c09f2a049634dfe3c835f32422f58e –
```

作为 HTML 颜色，这是 `#1b0fd7`——看起来像这样：

![bluesq](image/bluesq.png)

我们也可以将成对的数字作为 16×16 网格上的位置，或使用更多数字构建更大的网格，或将三组数字生成三维路径[^3]，用于 3D 打印或导入虚拟现实。

这是一个简单的 Python 示例：

```python
import hashlib

digest = hashlib.sha256()
digest.update(" the spammish repetition")
digest_string = digest.hexdigest()
digest_numbers = [int(char, 16) for char in digest_string]
coords = [digest_numbers[i:i+2]
 for i in range(0, len(digest_numbers), 2)]
print "%!psnnewpath"
print "%i %i moveto" % tuple(coords[0])
for coord in coords[1:]:
 print "%s %s lineto" % tuple(coord)
print "0.25 setlinewidthnstroke"
```

你可以在本文开头看到该程序输出的渲染结果。我们可以将其与颜色结合（或将哈希的颜色渲染为彩色方块网格）。

另一种从哈希生成视觉形式的方法是使用形状文法，就像 `libvisualid` 所做的那样。[^4] 这是 `libvisualid` 渲染的“this is my intent”：

![](image/this_is_my_intent.png)

哈希值可以附加在电子邮件或推文上，以便在世界中定位和传播它们。或者，可以使用诸如 `Bitcoinproof`[^5] 之类的系统将其放入比特币区块链，随着比特币区块链的更新而不断被重新哈希。这是区块链中一个咒语的哈希值：

`1Eui1Wje41JEJ4W1QYWbSAYG4h7JBaoPXQ6`

我们可以使用类似比特币工作量证明的系统，为数据寻找吉利的哈希值——即那些以一串前导零或其他数字（或目标字符串、编码为数字的位图）开头的哈希值。

更多 Python 代码：

```python
import hashlib
import binascii

target = "0000"
complement = -1
digest_numbers = ""

while not digest_numbers.startswith(target):
 complement = complement + 1
 digest = hashlib.sha256()
 digest.update("this is my intent")
 digest.update(str(complement))
 digest_numbers = digest.hexdigest()
 print "%d %s" % (complement, digest_numbers)

print binascii.b2a_uu(str(complement))
print binascii.b2a_base64(str(complement))
```

及其输出，这是创建输入字符串吉利哈希值的关键：

```
0 eae2ffcee00aa95306e706dd4bc67ab6b9fd2ffe61b32dfe4177b76c0afd682d
1 84ba18490876919df8bbff194eeb861c6c44a27e9bfbd8db485ecf704e41fcbd
2 f53226b118fa492dc21cd4336d67b4c8ce4148e49e8e4b094baf3e5ecff688ba
[...]
74962 38d5f823e881857f031def1822a28546d29b40903959b1c9bf1f5a1bebd42d9e
74963 b906fd259413ac714de31b9acaf6f0e5268560221d07f557f0f491a081a2cd09
74964 00006dd9f148ca454d331179bd7c87b42d7ab734df7738e1ae90e25013f02a1d
%-S0Y-C0
```

`NzQ5NjQ=%-S0Y-C0` 和 `NzQ5NjQ=` 是数字 `74964` 的不同表示形式。它们可用于创建印记，或者该数字可通过记忆生成器用语言形式表示。

关于加密哈希和加密签名还有更多可做的事情，这里未一一涵盖。但希望这些示例能激发进一步的实验。

（所有代码采用 CC0 许可。）

## 注释

[^1]: <https://mirrors.edge.kernel.org/pub/software/scm/git/docs/user-manual.html#understanding-commits>
[^2]: <https://web.archive.org/web/20130423132157/http://blog.dopplr.com/2007/10/23/in-rainbows/>
[^3]: <https://hyperritual.com/blog/3d-sigil-maker/>
[^4]: <https://disambiguate.me/stickfigurator>
[^5]: <https://github.com/vog/bitcoinproof>
[^6]: <https://www.blockchain.com/btc/address/1Eui1Wje41JEJ4W1QYWbSAYG4h7JBaoPXQ>

# 我的小小便士，比特币即魔法

## 2014

留给机器的零钱。

帕特·卡迪根，《合成人》

西奥多·阿多诺将神秘学视为一种通过退行至万物有灵论来否认异化的政治静默行为。

神秘学是对一切意义主体化的一种条件反射式行动，是物化的补足。如果，对活着的人来说，客观现实似乎前所未有地聋哑，他们便试图通过念叨“阿布拉卡达布拉”从中榨取意义。意义被随意地归因于次恶之物：真实的理性不再完全令人信服，取而代之的是跳舞的桌子和从土堆中射出的光线。[^7]

这确实如此，尽管一如既往，将人类心理学的一个更普遍特征独特地归因于单一宗教总是错误的。

宗教的鲍德里亚式迪士尼乐园是货物崇拜，美拉尼西亚岛民为来访的人类学家重演早已离去的美军当年的活动，以期让运送战时物资的载具重返。对外部观察者而言，显然神秘学和货物崇拜一样，都陷入了混淆相关性与因果性的谬误。

神秘学像哲学一样，患有语义谬误。这相当于可怜谬误，但针对的是意义：将逻辑而非情感意义的认知结构投射到外部环境中。魔法通过青春期男性权力幻想延伸了这一点——直接将意志强加于现实，减少获得应得之物所需的工作量。在这方面，它类似于经济学。

现代经济学使用统计学来建模现实。从总体中抽取样本，并使用各种检验确保关于这些样本的结论能准确代表更广泛的总体。基于这些结论的政策随后可应用于大众，并确信它们几乎只会在特定百分比的时间内出错。统计学是经济学的国教，将启示与赦免从数字平面带回。

