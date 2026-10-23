
虽然有几张面孔会让人感到熟悉。全体演员对剧本的处理都很出色。但观看起来很困难，因为像所呈现的那种情况并没有好的结局。现在很时髦地指责英国人挑拨印度教徒和穆斯林互相敌对，然后残酷地将他们分离成两个国家。这种观点有一定的道理，但也很真实的是，在分治时期左右，没有人强迫该地区的印度教徒和穆斯林像他们那样互相虐待。更有可能的是，英国人只是看到了宗教之间的紧张关系，并且足够聪明地利用它们为自己谋利。结果是情况中充满了残酷和非人道，这让人非常不愉快地回忆起来，也在银幕上看到。但它从来没有被描绘成非黑即白的案例。双方都有卑劣和崇高之处，同时年轻一代也怀有改变的希望。最后有某种救赎，当普罗必须在毁了她生活但也真正爱过她的男人，与抛弃了她后来又来寻找她的家人之间做出艰难选择时。但到那时，她没有任何选择是不伴随巨大痛苦的。这部电影传达的信息是，穆斯林和印度教徒都有严重的过错，同时两者都可以是体面而富有同情心的人。分治的现实使这一认识更加令人心碎，因为印巴边境之间永远不可能实现真正的和解。在这方面，它与“Mr & Mrs Iyer”相似。最后，尽管结局令人心碎，我们很高兴看到了这部电影。如果英国和美国能以这种坦率的方式处理他们自己的种族主义历史，他们肯定会好得多。’

## 28.1.1 Data Pipeline

在像 BERT 这样的模型出现之前，fastai 已经实现了 NLU 的迁移学习。文本迁移学习的主要思想是首先为给定语言训练一个语言模型，使其或多或少地理解该语言。你可以用这个语言模型来预测给定几个词之后的下一个词。但我们将此模型用作分类模型的编码器。这个概念被称为 ULM-FiT。

所以我们想构建的第一件事就是这个语言模型。我们的训练数据包含文本和标签（正面/负面）。但在创建语言模型时我们并不关心标签。我们只需要文本。因此我们用数据加载器抓取文本列。

对于这个级别我们不需要 datablock API，因为我们可以直接使用 from_csv 方法。使用 TextDataLoaders 我们可以传入一个参数 is_lm 来指示是否要创建语言模型。那么我们的 y 值将只是下一个词（即下一个标记）。

```
data_lm = TextDataLoaders.from_csv(path, 'texts.csv',  text_col='text',
is_lm=True)
```

### What is this thing called Tokenization?

好吧，即使对于文本，我们也必须将一切分解为数字才能与神经网络一起工作。分词帮助我们完成这项任务。

分词将我们所有的文本拆分为这些标记。标记可以是一个词、一组词等，对我们具有某种意义。分词通常会处理标点符号、缩写、HTML 标签等。fastai 的默认分词器是 spacy，但你也可以使用 sentence piece 分词器。

以下是 spacy 在分词时所做的一些示例：

- ‘s’ 被归为一组
- 缩写被拆分为类似 “did”、“n’t” 的形式
- 任何 HTML 符号都已被清理
- 一切都转换为小写
- 有几个特殊标记（所有以 xx 开头的标记），用于替换未知标记（见下文）或引入不同的文本字段

下一步是将所有内容转换为数字。这个过程称为 **数值化**。这意味着我们为每个标记创建一个具有数值值的字典。

如果我们想使用另一个分词器，我们必须使用 datablock api 创建数据加载器。

首先我们安装 sentencepiece 并加载分词器。

```
!pip install sentencepiece
```

```
```python
tokenizer = SentencePieceTokenizer
```
```

现在我们可以创建我们的 datablock 并传入自定义分词器：

```
```python
sp_lm = DataBlock(blocks=TextBlock.from_df('text',
is_lm=True, tok_func=tokenizer),
```
```

```
```python
get_x=ColReader('text'),
splitter=RandomSplitter(0.1)
dls = sp_lm.dataloaders(df, bs=64, seq_len=72)
```
```

处理中

## 28.1.2 Training our Language Model

理想情况下我们会用完整数据集训练模型，但为了加快速度我们保留小子集。我们使用的预训练模型是 wikitext-103。这是一个在英语维基百科文章上训练的模型。

```
```python
dls = sp_lm.dataloaders(df, bs=64, seq_len=72)
learn = language_model_learner(dls, AWD_LSTM, drop_mult=0.3)
```
```

现在让我们看看我们正在使用的模型的架构：

![](img/d5454da46c702784893ef8b0b539e5b9_384_0.png)

我们从嵌入开始，然后是三个 RNN，最后通过解码器得到输出。

对于训练过程，我们可以切换到混合精度来加快训练时间。为此，我们需要所有内容都是 8 的倍数，因此我们的 BS 为 8。这有助于最大限度地利用 CUDA 核心（张量核心）。

```
```python
learn = learn.to_fp16()
learn.lr_find()
```
```

SuggestedLRs(lr_min=0.19054607152938843,
lr_steep=0.04786301031708717)

![](img/d5454da46c702784893ef8b0b539e5b9_385_0.png)

learn.fit_one_cycle(1, 1e-2)
epoch train_loss valid_loss time
0 6.790908 6.128580 00:11

对于我们的语言模型，我们需要大约 30-40% 的准确率。我们不需要将模型训练到更高的准确率，因为我们不会用它来预测句子的下一个词，而是用于迁移学习。

所以现在我们可以解冻并训练更多：
learn.unfreeze()
learn.fit_one_cycle(5, 1e-3)
epoch train_loss valid_loss time

0 5.972351 5.723276 00:14
1 5.709247 5.377630 00:14
2 5.475660 5.233379 00:14
3 5.308859 5.180630 00:14
4 5.217210 5.166652 00:14

learn.save('27-language-model-fine_tuned')
记住我们能用这个模型做的唯一事情就是预测句子的下一个词

我们试试这个：

```
text = 'I liked this movie because'
n_words = 20
n_sentences=3
print('\n'.join(learn.predict(text, n_words) for _ in
→ range(n_sentences)))
```

我们必须保存编码器以供以后与分类器一起使用！

```
learn.save_encoder('27-fine-tuned-encoder')
```

让我们看看我们正在使用的模型的架构。

## 28.1.3 Create the Classifier

现在我们已经训练好语言模型，我们可以开始构建分类器。这是用迁移学习构建分类器的过程如下：

![](img/d5454da46c702784893ef8b0b539e5b9_386_0.png)

处理中

我们从预训练的语言模型开始，并在我们的语料文本上进行训练。下一步是基于此微调的语言模型创建分类器。

我们构建我们的 datablock，并且我们要确保它具有相同的序列长度，因为我们使用一个模型用于另一个。

```
blocks = (TextBlock.from_df('text',
seq_len=dls.seq_len,
vocab=dls.vocab),
```

```
CategoryBlock()
```

```
imdb_clas = DataBlock(blocks=blocks,
 get_x=ColReader('text'),
 get_y=ColReader('label'),
 splitter=ColSplitter())
```

```
dls = imdb_clas.dataloaders(df, bs=64)
```

现在我们可以训练我们的最终模型。ULMfit 的主干架构是 AWD_LSTM。为了使用我们的预训练权重，我们将重新加载此编码器。

```
learn = text_classifier_learner(dls,
 AWD_LSTM,
 drop_mult=0.5,
 metrics=accuracy).to_fp16()
```

```
learn.load_encoder('27-fine-tuned-encoder');
learn.fine_tune(5)
epoch train_loss
```

0 0.849227 valid_loss 0.687484 accuracy time 0.550000 00:03

epoch train_loss

0 0.750340
1 0.706977
2 0.676277
3 0.649858
4 0.626770
valid_loss

0.662187
0.631181
0.586847
0.570621
0.569212

