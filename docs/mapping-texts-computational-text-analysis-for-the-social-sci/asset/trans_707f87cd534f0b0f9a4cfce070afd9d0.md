

矩阵和数组如下，其中 _k_ 是主题数量，_v_ 是词汇表长度，_c_ 是内容协变量中的级别数量：

- 1. 一个 _k_-by-_v_ 矩阵，表示每个主题中每个术语相对于该术语在语料库中的速率的偏差。
- 2. 一个 _c_-by-_v_ 矩阵，表示每个协变量级别中每个术语相对于该术语在语料库中的速率的偏差。
- 3. 一个 _c_-by-_k_-by-_v_ 数组，表示主题与协变量交互作用的速率偏差。^7

每个速率偏差都取对数，因此文档在词汇表上的分布是每个术语的这些对数速率偏差的 _指数化_ 之和。

最后，我们从先前绘制的文档特定概率分布中随机选取一个主题，然后从该主题在词汇表上的概率分布中随机选择一个词。我们对文档中的每个词都重复此过程，仿佛我们是作者。

STM 使用迭代算法^8 来寻找最佳拟合参数。感兴趣的参数是 (1) 文档-主题和 (2) 主题-词概率分布，^9 还有 (3) 主题-流行率系数和 (4) 主题-内容速率偏差。

现在我们已经了解了模型的基础知识，可以问：流行率和内容协变量对我的主题模型分析有何意义？让我们先从流行率开始。

主题 **流行率** 是协变量对文档涉及某个主题程度的影响。例如，我们发现，较新的小说作品，且那些介于小说与非小说之间的“灰色地带”作品，往往在“20 世纪末美国政治惊悚小说”主题上花费更多词汇。然而，STM 在估计主题时会纳入这些协变量 _在估计时_。

为演示主题流行率，让我们使用 Bohr 和 Dunlap (2018) 的一个例子。研究人员在环境社会学文章的摘要上使用 STM，以绘制该领域的主要主题及其随时间变化的流行率（以及其他内容）。他们使用 Web of Science 的社会科学引文索引 (SSCI) 抓取了 1990 年至 2014 年间发表的、包含与环境社会学相关关键词的英文摘要。研究人员仅保留了 SSCI 在“社会学”类别下列出的期刊。^10 该语料库还为每篇文章提供了三个协变量：发表年份、每年引用次数和期刊排名。^11

让我们加载数据并进行数据处理。我们将把花括号引号替换为 ASCII 双引号，将文本音译为“基本拉丁”

^7 数组是具有任意维度的数据结构。矩阵是二维数组。这个数组是三维的。

^8 即，部分坍缩变分期望-最大化。

^9 通常，第一个矩阵称为 _beta_，但 stm 将第二个矩阵称为 _theta_，而大多数其他人称其为 _gamma_。我们称其为 gamma。

^10 我们的语料库版本包含 817 篇文章，尽管发表的文章仅包含 815 篇文章。

^11 期刊排名是作者下载文章时该期刊的 h5-index 分数 (Bohr and Dunlap 2018:3)。

ASCII 字符，将缩写替换为其全词形式，删除大写，删除标点符号，删除数字，删除多余空格，然后使用词典查找过程（即，不进行词性标注）进行词形还原，使用 Měchura 的英语词元-词典（即 `lexicon` 中的默认字典，`lemmatize_strings()` 使用），^12

```r
data("corpus_envsociology", package = "text2map.corpora")

df_env <- corpus_envsociology |>
  mutate(text = replace_curly_quote(abstract),
         text = stri_trans_general(text,
                                   id = "Any-Latin; Latin-ASCII"),
         text = replace_contraction(text),
         text = gsub("\\\\Ws\\\\W|", "", text),
         text = tolower(text),
         text = gsub("[[:punct:]]+", " ", text),
         text = gsub("[[:digit:]]+", " ", text),
         text = gsub("\\\\s+", " ", text)) |>
  mutate(lemma = lemmatize_strings(text))
```

^12 参见 Wrangling Words。

构建 DTM 后，我们将删除在语料库中只出现一次的词以及 Snowball 2014 停用词表中的词。我们还将删除“environment”和“environmental”——因为所有文章都关于环境社会学。

```r
our_sl <- c(get_stoplist("snowball2014"),
            "environment", "environmental")

dtm <- df_env |> dtm_builder(lemma, title) |>
  dtm_stopper(stop_list = our_sl, stop_hapax = TRUE)
```

现在我们可以估计模型。即使对于如此小的语料库，这个过程也可能需要一些时间。请做好准备。^13 我们通过将主题流行率条件化于发表年份、将主题内容条件化于期刊排名来估计主题。作者确定 25 主题解是最佳的，因此我们也将采用同样的方案。^14 我们将 `verbose` 设置为 `FALSE`，以便不查看每个期望步骤（“E 步”）和极大化步骤（“M 步”）。

^13 通过删除更多词可以加快算法速度。

^14 STM 开发人员提供了一些统计程序来帮助找到最佳 k，包括我们在前一章中介绍的一致性-排他性权衡。有关更多信息，请参阅他们在 *统计学软件期刊* (Roberts et al. 2019) 上的论文。

```r
set.seed(60601)

# this might take a while!
stm_env <- stm(
  documents = dtm,
  K = 25,
  data = df_env,
  prevalence = ~year,
  verbose = FALSE
)
```

现在让我们获取每个主题的顶级词项以开始解读。我们将使用 `tidytext` 包中的 `tidy()` 将术语-主题概率矩阵（beta）重塑为数据框。我们还将按主题分组，仅获取前五个词，然后将它们粘贴在一起。

```r
stm_beta <- tidy(stm_env, matrix = "beta") |>
  group_by(topic) |>
  slice_max(beta, n = 5, with_ties = FALSE) |>
  summarize(terms = paste0(term, collapse = ", "))
print(stm_beta, n = 15)
```

| 主题 | 词项 |
|---|---|
| 1 | scale, study, people, use, new |
| 2 | people, global, change, indigenous, much |
| 3 | research, policy, science, political, knowledge |
| 4 | change, climate, global, adaptation, community |
| . | . |
| . | . |
| . | . |
| 14 | social, movement, examine, organization, global |
| 15 | much, use, gender, policy, fish |

这些看起来像是连贯的主题。让我们看看两个主题随时间的流行率：主题 #4——我们称之为“气候变化”——以及主题 #14——我们称之为“社会运动”。“气候变化”和“社会运动”主题的参与度随时间如何变化？我们可以使用 estimateEffect() 获取估计值和置信区间，并使用 get_effects() 整理输出以便于可视化。

```r
df_effs <- estimateEffect(c(4, 14) ~ year, stm_env,
metadata = df_env)
df_effs <- get_effects(df_effs, variable = "year",
type = "continuous") |>
mutate(Topics = case_when(
topic == 14 ~ "Social Movements",
topic == 4 ~ "Climate Change"
))
```

```r
df_effs |>
ggplot(aes(x = value, y = proportion, fill = Topics)) +
geom_ribbon(aes(ymin = lower, ymax = upper), alpha = 0.5) +
geom_line(aes(linetype = Topics)) +
labs(x = "year")
```

环境社会学论文越来越多地讨论气候变化，越来越少地讨论社会运动（参见图 11.2）。此示例说明将流行率纳入主题建模如何随时间追踪一个领域的关注点。

## 基于协变量的主题内容

除了查看文档对某个主题的参与度如何随协变量变化之外，我们还可以建模主题内容如何随协变量变化。更准确地说，主题内容是协变量影响用于阐述主题的词汇的程度。也许，例如，美国

![](img/ccc0ce559da97114ef913045f55e3801_206_0.png)

## 图 11.2：主题随时间变化的流行率。

作者撰写美国政治惊悚小说的方式与非美国作者撰写同一主题的方式截然不同。或者，也许，如果环境社会学文章发表在高排名期刊上，它们在阐述气候变化时更多地使用“灾难”或“危机”。

为演示，我们将使用期刊排名。该变量针对 31 种可能排名有 31 个级别。内容协变量，尤其是具有多个级别的协变量，会显著减慢收敛速度。因此，让我们首先将期刊排名重新编码为三个级别。

```r
df_env <- df_env |>
  mutate(rank = case_when(
    journal_rank <= 18 ~ "High",
    journal_rank > 19 &
    journal_rank <= 23 ~ "Middle",
    journal_rank >= 24 ~ "Low")
  )
```

^15 预训练版本位于 text2map.pretrained 。

```r
stm_env <- stm(
  documents = dtm,
  K = 25,
  data = df_env,
  prevalence = ~year,
  content = ~rank,
  verbose = FALSE
)
```

现在我们可以从术语-主题概率矩阵（beta）中提取顶级词项，并将其重塑为数据框。请注意，有一个列用于

