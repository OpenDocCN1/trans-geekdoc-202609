

"take", "americans", "st", "us", "government", "these"
)
dtm_sotu_sub <- dtm_sotu %>% dtm_stopper(stop_list = to_remove)
# redo the LSA
lsa_sotu_sub <- lsa(t(dtm_sotu_sub))
```

```
top_names <- colnames(as.data.frame(lsa_sotu_sub$tk))
for (i in top_names) {
abs(lsa_sotu_sub$tk) |> 
as.data.frame() |>
arrange(desc(get(i))) |>
rownames() |>
head(5) |>
print()
}
```

```
[1] "years" "work" "one" "world" "tonight"
[1] "children" "say" "ask" "work" "united"
[1] "jobs" "ask" "children" "security" "iraq"
[1] "health" "care" "first" "tonight" "security"
[1] "health" "century" "welfare" "help" "care"
[1] "plan" "care" "work" "tax" "health"
[1] "challenge" "want" "ask" "help" "gun"
[1] "tax" "health" "care" "last" "world"
[1] "security" "social" "century" "challenge" "children"
```

30 此处我们可以使用任意大小的 n-grams，而不仅仅是 unigrams。

这些主题看起来更好。30 它们可能不如可能的那样彼此区分开来——例如，有些主题似乎与经济和税收削减有关，但它们之间没有区别。这可能意味着某些主题应该合并，或者有些主题过于笼统，必须进一步分解。这是一个统计标准并不总是与“直观判断”一致的示例。

通常，我们会在不同的模型规格之间进行迭代：使用不同的预处理、阈值和 k 个主题。不过，我们想避免“猜测”。我们绝不应该仅仅依靠顶部术语列表来为主题赋予含义。我们需要阅读原文文本。

让我们选一个主题作为例子。有三个主题将“children”列为顶部词汇。主题 #9 似乎主要关于儿童、教育以及他们面临的挑战。我们暂且将其称为“future of education”主题。但我们不应仅基于 5 个词的列表来进行解释。我们将做两件事：将此主题与其他主题进行比较，并找出在此主题上负载最高的演讲。

首先，是否有另一个关于“future of education”的主题？很有可能，因为还有两个主题共享关键词“children”：主题 #2 和 #3。由于 LSA 建立在 SVD 之上，我们可以将我们的主题概念化为形成一个 *潜在* 空间。为了可视化这个空间，我们将按各主题中的负载创建单词散点图。这会在 *两个维度* 上“展开”我们的术语，从而能够区分具有相似顶部词汇的主题。

为了节省篇幅，我们将比较主题 #9（我们暂定的“future of education”主题）与主题 #2。我们将绘制每个术语在主题上的原始负载，而非其绝对值。我们还将使用不同颜色对在主题上负载较高的单词进行着色（任意使用绝对值大于 0.1 的标准）。在两个主题上都负载较高的单词使用各自的颜色。在任一主题上都不负载较高的单词以透明灰色打印。图表如图 10.3 所示。

```
df_sotu_lsa <- data.frame(
  term = rownames(lsa_sotu_sub$tk),
  topic9 = lsa_sotu_sub$tk[, 9],
  topic2 = lsa_sotu_sub$tk[, 2] ) |> mutate(abs9 = abs(topic9),
       abs2 = abs(topic2),
       color = case_when(
         abs9 > .1 & abs2 <= .1 ~ "high9",
         abs9 <= .1 & abs2 > .1 ~ "high2",
         abs9 > .1 & abs2 > .1 ~ "both",
         TRUE ~ NA_character_),
       alpha = case_when(
         abs9 <= .1 & abs2 <= .1 ~ .6,
         TRUE ~ 1)
)
```

```
df_sotu_lsa |>
  ggplot(aes(topic9, topic2, label = term)) +
  geom_text(aes(color = color, alpha = alpha)) +
  geom_hline(yintercept = 0, linetype = "dashed") +
  geom_vline(xintercept = 0, linetype = "dashed") +
  labs(x = "Topic #9", y = "Topic #2") +
  guides(alpha = "none", color = guide_legend(nrow = 2)) +
  scale_colour_discrete(
    breaks = c("high9", "high2", "both", NA),
    labels = c("Loads High on #9", "Loads High on #2",
               "Loads High on Both", "Loads High on Neither"),
    na.value = "gray50"
  )
)
```

主题 #2 的一个极点涉及与主题 #9 类似的内容。主题 #2 的另一个极点似乎更关注恐怖主义、国家安全，也许还有美国例外主义。看来这个主题区分了外国问题和国内问题。虽然主题 #9 关注教育的未来，但主题 #2 可以概念化为“外国问题与国内问题”主题。

假设我们与主题 #3 的比较让我们很少有理由怀疑主题 #9 的“future of education”解释。现在我们可以阅读该主题的顶部负载文档（按绝对值），看看是否会得出不同的结果（输出在页边）。

图 10.3：比较主题 #9 与主题 #2。

![](img/ccc0ce559da97114ef913045f55e3801_189_0.png)

- "Clinton_1999"
- "Clinton_1996"
- "Clinton_2000"
- "obama_2015"

```
abs(lsa_sotu_sub$tk) |> 
as.data.frame() |> 
arrange(desc(v9)) |> 
rownames() |> 
head(4) |>
```

克林顿 1999 年的演讲在此主题上的负载最高。现在是阅读这篇演讲的好时机。儿童、教育和未来究竟是如何被讨论的？这与我们对主题的最初解释是否吻合？让我们来看看。

```
df_sotu |> filter(doc_id == "Clinton_1999") |> select(text)
```

这篇演讲很长，因此我们不会在此打印出来。但演讲的部分内容围绕如何处理当时 700 亿美元的盈余——政府收入超过债务的部分。他建议将部分资金用于社会保障和医疗保险，以加强为后代提供的安全网和福利。

在下文摘录中，我们也可以看到对教育的关注。

如今，我们的公立学校中来自更多元背景的儿童比历史上任何时候都多。他们的教育必须提供知识，并培养创造力，以使整个国家在新经济中蓬勃发展。

总而言之，这个主题确实带有“future of education”的元素——但似乎比那更为笼统。鑒于对投资于儿童未来的关注，也许“securing our children’s future”是对该主题更好的解释。

让我们再看一份文件，看看是否对我们的解释过于具体化。31 我们将使用负载较高的另一篇演讲：布什 2005 年的演讲。

```
df_sotu |> filter(doc_id == "Bush_2005") |> select(text)
```

我们这一代人蒙受了福祉——机遇的扩大、医学的进步，以及父母牺牲所换来的安全……

……在未来的几个月里，在一个又一个议题上，让我们做美国人一直所做的事，为我们的孩子和孙辈建设一个更美好的世界。

这确实看起来像是一个“securing our children’s future”主题。请回顾，LSA 试图使用尽可能少的维度来解释我们的 DTM 中的变化。这是基于意义向量空间方法的“变化”的空间解释。

LSA 作为一种主题建模形式有着悠久的历史。然而，对于大多数研究人员来说，LSA 可能不是他们想到主题建模时所想的内容。原因在于，在 2000 年代初期，一种新的主题建模形式——一种明确自称为主题建模的形式——出现了，即隐性狄利克雷分配，简称 LDA（Blei 等人，2003 年）。现在让我们探讨一下。

## 使用 LDA 进行主题建模

LDA 出现部分原因是 LSA 的不足之处。例如，在 LSA 中，没有什么能阻止奇异向量（无论是术语还是文档）中出现负值。以绝对值的方式解释奇异向量有点棘手。32 它们在潜在空间中为术语/文档定义一个点。较大的值表示术语/文档在其上负载较高，因此对于确定主题含义具有重要意义——但任何单个坐标本身都是不可解释的。33

为了解决这些问题，已提出许多 LSA 的替代方案，包括非负矩阵分解（Lee 和 Seung，1999 年）和概率 LSA（Hofmann，2001 年），但 LDA 是唯一流行下来的——至少在社会科学中是如此。34 因此，我们将在此处将注意力集中于此。

31 实际上，我们希望每个主题阅读更多文档，以便对维度所捕捉到的主题进行稳健的解释。

32 例如，术语“security”在主题 #9 上的主题负载（我们的“securing our children’s future”主题）为 -0.254，术语“challenge”在该主题上的负载为 0.221。那么，-0.254 和 0.221 究竟是什么？

33 有人认为，SVD 在某些任务上表现不佳，例如寻找词语相似性（Gamallo 和 Bordag，2011 年）。

34 例如，请参见期刊《Poetics》2013 年的专刊（Mohr 和 Bogdanov，2013 年）。

