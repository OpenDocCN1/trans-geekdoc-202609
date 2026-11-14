

## 标记化

我们通常将文档拆分为更小的单元来表示文档内容。最小的单元称为**标记**，该过程称为标记化。^3 当我们想到“单词”时，脑海中想到的通常就是这些子文档单元；然而，我们可以将文档标记化为更复杂的单元，例如 n-gram——例如，二元语法（bigrams，每两个连续单词）或三元语法（trigrams，每三个连续单词）。^4 我们也可以按字符 n-gram 进行标记化——例如，每两个连续字符。

最简单的做法是假设“单词”就是我们的标记。但想要制定一条清晰的“规则”，让算法知道每个单词在哪里开始和结束，可能会很棘手。同样出于简化考虑，假设所有单词两侧都由单个空白字符清晰分隔。这一假设最适用于基于拉丁文字的书写系统，例如英语。^5 即便如此，也很容易找到我们规则的例外。“New York City”、“merry-go-round”还是“to and fro”，是一个标记还是三个标记？“I’ve”和“don’t”是一个还是两个？

让我们通过一个示例来演示。我们使用 `rtrek` 准备了《星际迷航：下一代》（Star Trek: The Next Generation）的电视剧脚本。第 5 季的脚本可在 `text2map.corpora` 中获取。下面我们将标记化首播集（标题为“Redemption, Part 2”）的第 17 行。我们将使用字符间的空格进行标记化。在任何标记化过程中，这通常是最快的选项。

```
data("corpus_tng_season5", package = "text2map.corpora")
df_trek <- corpus_tng_season5 # rename so it's tidier
dim(df_trek) # how many rows and columns
```

这将按*单个空格*拆分单词进行标记化（`fixed = TRUE` 告诉 `R` 这是字面字符）。

```
strsplit(df_trek$line[17], " ", fixed = TRUE)
```

[[1]]
 [1] "Captain's"     "log,"
 [3] "stardate"      "45020.4."
 [5] "We've"         "have"
 [7] "arrived"       "at"
 [9] "Starbase"      "Two-thirty-four,"
 [11] "where"         "I"
 [13] "have"          "taken"
 [15] "the"           "opportunity"
 [17] "to"            "make"
 [19] "a"             "proposal"
 [21] "to"            "Fleet"
 [23] "Admiral"       "Shanthi."

^3 如前文所述，语言（尤其是文本）可且应当被分段，这是一个假设（Aronoff 1992），但对于计算文本分析来说是必要的假设。

^4 单个单词通常称为一元语法（unigram）。

^5 对于阿拉伯文书写系统的标记化尤其复杂，因为字符可能会根据其在单词中的位置而发生变化。一个单词可以表现为四个不同的标记，在标记化之前需要进行形态分析（Attia 2007; Farghaly and Shaalan 2009）。

反斜杠 \\ 是用于将字面字符转换为特殊字符，或者将特殊字符转换为字面字符（通常称为“转义”）。由于 `R` 也使用反斜杠进行“转义”，这可能会变得复杂。我们必须使用两个反斜杠，使 `R` 只将一个反斜杠传递给正则表达式引擎——这也意味着我们需要四个反斜杠才能匹配一个字面反斜杠！

这方法效果不错。不过，单词之间的分隔符不只有单个空格。例如，存在双空格、制表符（\t）、回车（\r）和换行（\n）。为了确保我们对字符间的*任意*空白字符进行拆分，可以使用**正则表达式**（regex）^6 \s，并添加 + 来匹配一个或多个。由于现在使用的是正则表达式模式而非字面字符，因此移除了 fixed = TRUE 。

^6 正则表达式是匹配字符模式的特殊字符序列，而非字面（即固定）字符。Unix 操作系统使正则表达式流行起来，现在已应用于各种编程语言。正则表达式有不同的“风味”，没有大量练习，这些模式通常难以读懂。

```
# tokenize by splitting into regex whitespace
strsplit(df_trek$line[17], "\\s+")
```

除了空白字符之外，我们还可以使用正则表达式模式，针对任何非单词字符（\w）进行标记化。^7 我们还可以通过将字符放入以插入符号（^）开头的括号中，*否定*匹配。例如，a-z 匹配所有小写英文字母，A-Z 匹配大写字母，0-9 匹配数字，下表达式匹配不属于这些集合的任何字符串：[^a-zA-Z0-9]+ 。

^7 在正则表达式中，大写字母通常表示“非”，即 \w 模式匹配单词字符，而 \W 匹配非单词字符。

```
# tokenize by splitting on non-word characters
strsplit(df_trek$line[17], "\\W")
# tokenize by splitting on non-alphanumerics
strsplit(df_trek$line[17], "[^a-zA-Z0-9]+")
```

我们可以继续自定义模式——例如，将带连字符的单词（如“two-thirty-four”）视为单个标记——或者可以使用 tokenizers 包中预先开发的标记化方案。该包遵循十几条规则来定义单词边界。^8 请注意，tokenize_strings() 在标记化过程中移除了大小写和标点符号。

^8 这些规则由 Unicode 国际组件开发（site.icu-project.org）。

```
tokenize_words(df_trek$line[17])
```

[[1]]
 [1] "captain's" "log"
 [3] "stardate" "45020.4"
 [5] "we" "have"
 [7] "arrived" "at"
 [9] "starbase" "two"
[11] "thirty" "four"
[13] "where" "i"
[15] "have" "taken"
[17] "the" "opportunity"
[19] "to" "make"
[21] "a" "proposal"
[23] "to" "fleet"
[25] "admiral" "shanthi"

^9 相关但较少见的一种标记化方式是跳格 n-gram，其中允许两个或多个单词之间存在一定数量的单词。

我们还可能希望将原本分开的单词视为一个整体。例如，也许我们希望将文档分割成文本中的每个两词序列，即二元语法（bigram）。我们可以包含最多任何 n 尺寸的 n-gram。^9

```
# tokenize into bigrams
tokenize_ngrams(df_trek$line[3], n = 2L)
# tokenize into unigrams and bigrams
tokenize_ngrams(df_trek$line[3], n = 2L, n_min = 1L)
```

[[1]]
[1] "aft shields" "shields are"
[3] "are gone"

[[1]]
[1] "aft" "aft shields" "shields are"
[3] "shields" "shields are" "are gone"
[5] "are" "are gone"
[7] "gone"

最后，我们也可以采取相反方向，使用*字符*而非完整单词或短语进行标记化，方法是将单词分解为音素/语素甚至单个字符。基于字符的 n-gram 有时用于表意文字书写系统，例如中文或韩文（Lee and Ahn 1996; Nie and Ren 1999）。

```
# tokenize by each character
tokenize_characters(df_trek$line[3])
# tokenize by clusters of 3 characters
tokenize_character_shingles(df_trek$line[3],
    n = 3,
    n_min = 3
)
```

[[1]]
[1] "a" "f" "t" "s" "h" "i" "e" "l" "d" "s"
[11] "a" "r" "e" "g" "o" "n" "e"
[[1]]
[1] "aft" "fts" "tsh" "shi" "hie" "iel"
[7] "eld" "lds" "dsa" "sar" "are" "reg"
[13] "ego" "gon" "one"

无论使用哪些规则进行标记化，任何计算文本分析都始于标记化。标记化的输出是一个列表。通常，这是一个列表的列表，其中第一层列表是每个“文档”，第二层列表是每个标记。这种列表的列表通常是一个必要的，但*中间的*数据结构。

## 分块

如前文所述，我们的“文档”可以是任何长度的文本。通常，我们按收集时的形式使用文档：每条推文、每篇文章或每本书都是一个文档。文本产生的上下文决定了这些文档的起止位置。不过，有时我们会从大型作品中提取一段文本。也许我们有一整本书，但需要将章节甚至段落作为文档，或者希望标准化文本大小以便比较。

正如我们使用正则表达式模式来标记化文本一样，可以使用正则表达式模式将较大的文档拆分为较小的块。例如，可以使用标点符号将文本分割为句子，也可以使用那些表示不同类型空白字符的特殊字符——制表符（\t）、回车（\r）和换行（\n）。我们还可以按特定标记数量对文档进行分块。

```
# chunk by punctuation
strsplit(df_trek$line[17], "[!.?,]")

# chunk by newlines
strsplit(df_trek$line[17], "[\n]")

# chunk by every N tokens
chunk_text(df_trek$line[17], chunk_size = 10)
```

最后，有时我们希望使用“移动窗口”——即瓦片（shingle）——其中每个文本块与前一个块部分重叠。这相当于上面讨论的按 n-gram 进行标记化。区别在于我们打算如何使用输出。在标记化时，我们寻找表示文档内容的方式；而在分块时，我们实际上是在创建文档。

```
# chunk text into a moving window of 3 tokens
tokenize_ngrams(df_trek$line[17], n = 3L, n_min = 3L)
```

[[1]]
[1] "captain's log stardate" "log stardate 45020.4"
[3] "stardate 45020.4 we" "45020.4 we have"
[5] "we have arrived at" "have arrived at"
[7] "arrived at starbase" "at starbase two"
[9] "starbase two thirty" "two thirty four"
[11] "thirty four where" "four where i"
[13] "where i have" "i have taken"
[15] "have taken the" "taken the opportunity"
[17] "the opportunity to" "opportunity to make"
[19] "to make a" "make a proposal"
[21] "a proposal to" "proposal to fleet"
[23] "to fleet admiral" "fleet admiral shanthi"

或者，我们不想将较大的文本拆分为章节、段落、句子、n-gram 窗口等，而是希望从这些较小的块进行聚合。例如，也许我们有句子，但想要段落甚至整本书。例如，rtrek 提供的是行，但我们想要完整集的脚本。首先，按集数对所有行进行分组，然后对该分组进行“汇总”。其次，使用 paste0() 和表示换行的空白字符（\n）将行合并。现在，我们应该为每个集拥有一行。

