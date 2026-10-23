
![](img/d5454da46c702784893ef8b0b539e5b9_376_0.png)

Feature Transformer 包含 2 个线性层后跟一个 GLU Block。 这个 GLU Block 允许我们获取注意力反馈并将其输入到我们的最后一个线性层以生成输出。

现在我们可以检查 Attention Transformer：

![](img/d5454da46c702784893ef8b0b539e5b9_376_1.png)

这里我们从一个线性层开始，然后进入被称为 GhostBatchNorm 的部分 *（在完全不同的论文中介绍过）*。 当我们将所有内容发送到模型时，我们保留之前的输入。 这就是注意力发挥作用的地方。 我们将输入 x 与之前的输入相乘。 然后我们使用 Sparsemax 激活函数。

现在我们可以制作我们的模型。

### 27.1 创建 TabNet 模型

我在实验中发现 TabNet 并没有 fastai 的表格模型那么好，但由于注意力可能很重要并且是热门话题，我们在这里使用它。 这种模型的另一个缺点是需要很多轮次才能获得不错的准确率，正如我们将看到的：

```python
from fast_tabnet.core import *
from fast_tabnet.core import TabNetNoEmbeddings
```

我们可以用此模型调整许多超参数。
现在我们可以使用我们的模型！ 我们可以传入许多不同的值，这里是一个简要总结：

- n_d: 预测层的维度（通常在 4 到 64 之间）。
- n_a: 注意力层的维度（与 n_d 类似）。
- n_steps: 我们网络中的连续步数（通常为 3 到 10）。
- gamma: 用于更新注意力的缩放因子（通常在 1.0 到 2.0 之间）。
- momentum: 所有批量归一化层中的动量。
- n_independent: 每个块中独立 GLU 层的数量（默认为 2）。
- n_shared: 每个块中共享 GLU 层的数量（默认为 2）。
- epsilon: 应保持非常低（避免 log(0)）。

首先我们决定嵌入大小：
emb_szs = get_emb_sz(to); emb_szs
[(10, 6), (17, 8), (8, 5), (16, 8), (7, 5), (6, 4), (3, 3)]

让我们构建一个与上面插图中所示模型相似的模型。为此我们将预测层的维度设置为 8，注意力层维度数设置为 32，我们的步数设置为 4：

```python
class TabNetModel(Module):
    "Attention model for tabular data."
    def __init__(self, emb_szs, n_cont, out_sz, embed_p=0., y_range=None,
                 n_d=8, n_a=8, n_steps=3, gamma=1.3,
                 n_independent=2, n_shared=2, epsilon=1e-15, virtual_batch_size=128,
                 momentum=0.02):

        self.embeds = nn.ModuleList([Embedding(ni, nf) for ni,nf in emb_szs])
        self.emb_drop = nn.Dropout(embed_p)
        self.bn_cont = nn.BatchNorm1d(n_cont)
        n_emb = sum(e.embedding_dim for e in self.embeds)
        self.n_emb, self.n_cont, self.y_range = n_emb, n_cont, y_range
        self.tab_net = TabNetNoEmbeddings(n_emb + n_cont, out_sz, n_d, n_a, n_steps,
                                          gamma, n_independent, n_shared, epsilon, virtual_batch_size, momentum)

    def forward(self, x_cat, x_cont, att=False):
        if self.n_emb != 0:
            x = [e(x_cat[:,i]) for i,e in enumerate(self.embeds)]
            x = torch.cat(x, 1)
            x = self.emb_drop(x)

        if self.n_cont != 0:
            x_cont = self.bn_cont(x_cont)
            x = torch.cat([x, x_cont], 1) if self.n_emb != 0 else x_cont
        x, m_loss, m_explain, masks = self.tab_net(x)
        if self.y_range is not None:
            x = (self.y_range[1]-self.y_range[0]) * torch.sigmoid(x) + self.y_range[0]
        if att:
            return x, m_loss, m_explain, masks
        else:
            return x
```

你还记得，我们之前将 batch-size 设置为 1 吗？ 因此我们必须为 dataloaders 重置 batch-size。

```python
dls = to.dataloaders(bs=1024)
```

现在我们可以构建 tabnet 模型，创建学习器并训练 5 个 epoch。

```python
net = TabNetModel(emb_szs, len(to.cont_names), dls.c, n_d=8, n_a=32, n_steps=1)
learn = Learner(dls, net, CrossEntropyLossFlat(), metrics=accuracy, opt_func=ranger)
learn.fit_flat_cos(5, 1e-1)
```

| epoch | train_loss | valid_loss | accuracy | time |
|---:|---:|---:|---:|---:|
| 0 | 0.530212 | 0.402862 | 0.819410 | 00:02 |
| 1 | 0.433628 | 0.363029 | 0.831388 | 00:00 |
| 2 | 0.397048 | 0.364400 | 0.833538 | 00:00 |
| 3 | 0.378478 | 0.358177 | 0.832310 | 00:00 |
| 4 | 0.366250 | 0.352684 | 0.831849 | 00:00 |

## Chapter 28: Introduction to Natural Language Processing

现在我们开始使用 fastai 深入挖掘 NLP（自然语言处理）主题。首先我们给出一些 NLU 可以做什么的例子：

- **词性标注：** 识别每个词是名词、动词、形容词等）
- **命名实体识别 (NER)：** 识别人名、组织、地点、医疗代码、时间表达、数量、货币价值等
- **问答**
- **语音识别**
- **文本转语音和语音转文本**
- **主题建模**
- **情感分类**
- **语言建模**
- **翻译**

使用文本数据时请记住：

- 模型训练可能需要更长时间（对于真实数据集至少预期 1-2 小时）
- fastai 做了一些改进来加速，但 NLU 仍然是一个难以学习的任务
- 大约 20-30 分钟每个 epoch

### 28.1 我们将从计算电影评论的情感开始

文本的情感定义了（例如评论）是 intended 为积极、消极还是中性的。

为了使用 fastai 处理文本，我们导入 text 模块：

```python
from fastai.text.all import *
```

为了加快训练，我们不使用完整的 IMDB 数据集而只使用其子样本。此数据集包含一个 csv 文件，我们将其加载到 dataframe 中。

```python
path = untar_data(URLs.IMDB_SAMPLE)
path.ls()
```

```
(#1) [Path('/home/bmayr/.fastai/data/imdb_sample/texts.csv')]
df = pd.read_csv(f'{path}/texts.csv')
df.head()
label 0 negative
1 positive
2 negative
3 positive
```

4 negative text is_valid

不可置信！梅格·瑞恩在这部电影里甚至都不像她平常 False 俏皮可爱的样子，这通常会让我原谅她肤浅的刻板表演风格。难以置信她是这部烂片的制片人。再加上凯文·克莱恩：他的事业到底经历了怎样的自杀式旅程？呼……万岁！！！最后这部片子竟然是拍《寒冬》那家伙导的？必须得是好莱坞风格的琼斯镇重演。呜噢！

这是一部制作精良的电影。表演、剧本和 False 摄影都是一流的。音乐也不错，不过主要集中在电影早期，当时事情还相对愉快。演员阵容里没有真正的超级巨星，尽管有几张面孔会很熟悉。整个演员阵容都出色地演绎了剧本。但很难观看，因为像所呈现的那种情况并没有好的结局。现在流行指责英国人让印度教徒和穆斯林互相敌对，然后残酷地把他们分离成两个国家。有一点……

每隔很久就会有一部电影出现，False 如此糟糕以至于我觉得有必要警告大家。如果我劳作一生，只救下一个人不看这部电影，我的喜悦会有多大。从何谈起我的痛苦之谈。首先，每五分钟就有一个音乐蒙太奇。没有角色发展。每个角色都是刻板印象。我们有咒骂的家伙、吃甜甜圈的胖子、傻乎乎的外国人等等。剧本感觉像是电影拍摄时才在写。制作价值低得令人难以置信，感觉像……

名字就说明了一切。我 False 在它上映时和我爸爸一起看过这部电影，他曾在韩国服役，对那个人非常钦佩。这部电影令人失望的地方在于它只集中在那个人生命中的短暂时期——有趣的是，那个人的整个人生本可以拍成一部史诗般的传记片，想象制作成本就令人震惊。一些海报暗示了那个人性格上的缺陷，这都是廉价的攻击。电影的主题“职责、荣誉、国家”不仅仅是高声官僚脱口而出的空话……

这部电影成功地成为你见过最独特的电影之一 False。然而这源于你根本理不清这团乱麻。它几乎看起来像是一系列挑战，旨在判断你是否愿意走出电影院放弃刚付的钱。如果你不想感到受辱，你会硬坐完这部可怕的电影，并对其中演员产生真正的同情。他们都经历过更好的日子，但随后你意识到他们实际上为此拿了不少钱，你就会像你已经……一样对他们失去同情。

### PROCESSING

如果我们查看数据，可以看到它包含 3 列：

- 一个标签
- 文本本身和
- 一个布尔列，指示该项目属于训练集还是验证集

```python
df['text'][1]
```

> ‘这是一部制作精良的电影。表演、剧本和摄影都是一流的。音乐也不错，不过主要集中在电影早期，当时事情还相对愉快。演员阵容里没有真正的超级巨星，

