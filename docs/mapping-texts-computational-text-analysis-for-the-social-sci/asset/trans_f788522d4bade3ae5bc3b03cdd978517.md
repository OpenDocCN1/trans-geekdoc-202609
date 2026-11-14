

```r
df_trek <- df_trek |>
  group_by(number) |>
  summarize(text = paste0(line, collapse = "\n"),
            doc_id = first(title),
            airdate = first(airdate))

dim(df_trek) # how many rows and columns now?

[1] 26 4
```

## 文档特征

一个 *特征* 所指代的内容取决于我们如何对文档进行分词，以及如何对这些词元进行分类或汇总。如前所述，最常见的文档-特征矩阵是文档-术语矩阵（DTM）。它通过术语计数向量来表示文档，向量中的位置对应不同的词类型。

## 本节需要：

- tidyverse
- tidytext
- tokenizers
- reshape2
- quanteda
- text2map

分词后，每个文档都是一个词元列表。接着，我们统计每个 *唯一* 词元<sup>10</sup> 在每个文档中出现的频率。对于单个文档，我们用数字向量来表示其内容。向量中的位置引用一个唯一类型。该数字表示该类型在该文档中出现的次数。

> 这被称为 *类型*，与 *词元* 相对。

将词元列表转换为词元计数列表时，有两点需要注意。首先，我们不会保留文档中 *单词顺序*。其次，我们会合并 *精确* 相同字符的词元。例如，“The”和“the”会被视为不同的词元，“Raúl”和“Raul”也是如此。让我们使用玛丽·雪莱的 *弗兰肯斯坦* 中的一段摘录。

```
doc <- "nothing is so painful to the human mind
 as a great and sudden change the sun might
 shine or the clouds might lower but nothing
 could appear to me as it had done the day
 before a fiend had snatched from me every
 hope of future happiness no creature had ever
 been so miserable as I was so frightful an
 event is single in the history of man"
```

我们将使用 `strsplit()` 和常规的“空格”进行分词。该函数的输出是一个 **词元列表**。接下来，我们将使用 `table` 来统计每个唯一词元在文档中出现的次数，创建一个 **词元计数列表**。

```
# tokenize by splitting into words by space
docs_tokens <- strsplit(doc, " ", fixed = TRUE)

# get word frequencies
docs_freqs <- table(docs_tokens)
```

```
# look at the first few
docs_freqs[1:5]
```

| a | an | and | appear | as |
|---|---|---|---|---|
| 2 | 1 | 1 | 1 | 3 |

假设我们有多个文档，每个文档都表示为一个词元计数向量。我们将把每个向量“堆叠”在一起，构建一个 DTM。让我们使用来自 Europarl Corpus<sup>11</sup> 的法语前 5,000 个句子样本以及英语中的相同前 5,000 个句子，这些句子位于 `text2map::corpora` 中。

<sup>11</sup> Europarl 语料库是 1996 年至 2011 年欧洲议会议程的集合（Koehn 2005）。

```
data("corpus_europarl_subset", package = "text2map.corpora")
df_europarl <- corpus_europarl_subset |>
    rowid_to_column(var = "doc_id")
```

```
df_europarl <- df_europarl |>
    mutate(
        text = tolower(text), # lowercase
        text = gsub("[[:punct:]]", " ", text), # remove punctuation
        text = gsub("[[:digit:]]", " ", text), # remove numbers
        text = gsub("[[:space:]]+", " ", text) # remove excess space
    )
```

<sup>12</sup> 另请参阅“处理单词”。

如前所述，我们加载了文本数据集，并通过小写化、去除标点、去除数字以及删除多余空格来转换了文本。<sup>12</sup> 现在，每个句子看起来就像一个由小写非数字字符集组成的长字符串，它们之间由单个空格分隔。接下来，我们将通过将每个文档转换为词元列表来对其进行分词，这次使用 `tokenizer` 。

```
docs_tokens <- tokenize_words(df_europarl$text)
```

一旦我们将文档表示为词元列表，下一步就是统计每个唯一词元（又称 type）在每个文档中出现的次数。从计算角度看，这涉及确定哪些元素是精确匹配。`table()` 处理此匹配和计数。下面我们将其与 `lapply()` 一起使用，它将把一个函数“应用”到列表的每个元素上（即每个文档）。

```
docs_freq <- lapply(docs_tokens, table)
```

最终输出是一个列表的列表。请回顾，第一阶列表是每个文档，第二阶列表是每个文档的词元计数。使用 `melt()`，我们将其转换为一个由三列组成的“三元组”数据框：term、count 和 document id。下文讨论的 `tidytext` 和 `udpipe` 都将此用作主要数据结构。

```
df_triplet <- melt(docs_freq)
colnames(df_triplet) <- c("term", "freq", "doc_id")

length(unique(df_triplet$doc_id)) # should equal N documents
tail(df_triplet) # have a quick look at the bottom
```

| | term | freq | doc_id |
|---|---|---|---|
| 228725 | not | 1 | 100000 |
| 228726 | should | 1 | 100000 |
| 228727 | there | 1 | 100000 |
| 228728 | this | 1 | 100000 |
| 228729 | want | 1 | 100000 |
| 228730 | we | 1 | 100000 |

与三元组数据框不同，我们可以将每个词元计数列表放入一个矩阵中，其中行是所有文档，列是语料库中的唯一单词。以下是实现此目的的 base R 方法。

首先，我们需要所有唯一词元。可选地，我们可以按字母顺序排序。

```
vocab_unique <- sort(unique(unlist(docs_tokens)))
```

第二步是用正确的维度、列名和行名初始化一个空矩阵。

```
dtm <- matrix(
  data = 0,
  ncol = length(vocab_unique),
  nrow = length(docs_freq),
  dimnames = list(df_europarl$doc_id, vocab_unique)
)
```

最后，每当文档词元列表中的单词与列中的单词匹配时，我们就会填充空单元格。使用循环，我们将用找到的匹配次数替换该单元格。

```
for (i in seq_along(docs_freq)) {
  freqs <- docs_freq[[i]]
  words <- names(freqs)
  dtm[i, words] <- as.integer(freqs)
}
```

检查我们的矩阵维度。第一个数字是行数（即文档数），第二个数字是列数（即词汇表数量）。

```
dim(dtm)
```

> 13 唯一词元称为 type，而类型的集合称为 vocabulary、vocab 或 V。

```
selection <- c("resumption", "session", "european", "you")
dtm[5001:5005, selection]
```

| | resumption | session | european | you |
|---|---|---|---|---|
| 5001 | 1 | 1 | 0 | 0 |
| 5002 | 0 | 1 | 1 | 2 |
| 5003 | 0 | 0 | 0 | 1 |
| 5004 | 0 | 1 | 0 | 1 |
| 5005 | 0 | 0 | 1 | 0 |

DTM 是一种结构化且高效的方法，用于表示文档内容，并易于按标准化特征（在此例中，语料库中的每个唯一术语）比较每个文档。

## 稀疏性

有多个专门用于构建 DTM 的函数。不过，这些函数生成的对象与我们的 base `R` 矩阵略有不同。这是因为 DTM 是包含大量零值的矩阵，或者词汇表中未出现在文档中的单词。让我们计算矩阵的“稀疏性”（即零单元格的百分比）以及语料库中只出现一次的单词数量。

```
# calculate the overall sparsity of a matrix:
total_cells <- ncol(dtm) * nrow(dtm)
zero_cells <- sum(dtm == 0)
zero_cells / total_cells
```

```
[1] 0.9985835
```

```
# how many terms in our vocabulary occur just once?
total_vocab <- ncol(dtm)
total_hapax <- sum(colSums(dtm) == 1)
total_hapax / total_vocab
```

```
[1] 0.3944386
```

超过 99% 的单元格为空！超过三分之一的唯一单词在任何文档中只出现一次，也就是说，列中只有一行会有非零值。<sup>14</sup> 这并非欧洲议会句子所特有，而是任何语料库的标准特征。

稀疏矩阵也是一种专为高稀疏性矩阵设计的 R 对象类。稀疏类不为数字零分配内存，而是假设未分配内存的位置即为零。稀疏类的内存效率高出多少取决于矩阵的稀疏性和表示类型（整数、实数或逻辑值）。例如，作为 base `R` 密集矩阵，我们的 DTM 大约占用 1200 Mbs（1.2 Gb），但作为 `Matrix` 稀疏矩阵，它会缩减到 4.4 Mbs。<sup>15</sup>

<sup>14</sup> 在语料库语言学中，语料库中只出现一次的任何单词都称为 hapax legomenon。如果一个 type 出现两次，则称为 dis legomenon。

<sup>15</sup> 作为 `R` 对象，这些特殊矩阵的类为 `dgCMatrix`、`dgTMatrix`、`lgCMatrix`（如果使用 `Matrix` 构建），或 `simple_triplet_matrix`（如果使用 `slam` 构建）。

