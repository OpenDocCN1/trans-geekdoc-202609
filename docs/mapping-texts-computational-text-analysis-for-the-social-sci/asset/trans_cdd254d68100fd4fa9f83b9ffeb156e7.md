

## 图 11.8：ATN 语料库中的公民身份–移民

![](img/ccc0ce559da97114ef913045f55e3801_231_0.png)

```
imm_cen <- get_centroid(anchors = anchors$add, wv = atn_vectors)
sims <- sim2(atn_vectors, imm_cen, method = "cosine")
names(head(sort(sims[,1], decreasing = TRUE)))
```

外星人 移民 外国人 外国 移民 外星人 移民

如我们所见，该质心的上下文词与考虑移民相对于公民身份时得到的词并无太大区别。思考方向和质心之间差异的一个好方法是：方向更适合捕捉关系性偏见（即，倾向于一极而排斥另一极的术语），而质心更适合识别一般上下文或上下文的交集。

不过，归根结底，这取决于我们试图衡量的意义。有些意义被紧密组织成二元光谱；有些则不是。考虑质心与方向之间对比的更理论化的方法是使用语言学家格雷马的“符号学方阵”（Greimas 1983）。格雷马将意义组织为四个极点。在我们的示例中，这些极点将是“移民”和“公民身份”，以及“非移民”和“非公民身份”。虽然语义方向捕捉的是移民/公民身份的并置，但质心更接近移民/非移民或公民身份/非公民身份的对立。在这里，理论动机和学科专长将决定哪种策略最适合我们的研究目标。

## 词移动距离

词嵌入最容易用于词级和意义级分析。我们通常想了解文档或作者的某些信息。例如，我们能否衡量某一文档写的内容和方式与语料库中其他文档有多大程度相同？

我们为此使用词移动距离（WMDs）（Kusner 等人，2015）。67 WMD 是衡量将一份文档中的所有词移动到另一份文档中词所在位置所需的最小成本的指标。68

更具体地说，文档 i 与文档 j 之间的 WMD 是两个文档中每一对词的两个数值乘积的最小和：余弦距离以及该词对在所谓“流矩阵”中的单元格条目。69 WMD 在以下约束下查找单元格条目：（1）行词的总和是该词在 i 中的相对频率，以及（2）列词的总和是该词在 j 中的相对频率。寻找最小成本在计算上要求很高，因此 Kusner 及其同事（2015:4）提出了松弛词移动距离（RWMD）。无论如何计算，结果都是一个距离得分，较大值表示两份文档之间的上下文相似性较低，较小值表示上下文相似性较高。鉴于 WMD 的计算复杂性（参见 Brunila 和 LaViolette 2021），我们将继续使用 RWMD。

假设我们想了解我们的新闻文章（均至少提及一次“immigrant”和“immigration”）与一群致力于移民相关问题的公民社会组织发布的一系列新闻稿之间的上下文相似性。70 遵循我们之前的工作（Stoltz 和 Taylor 2021），让我们考察左翼和右翼新闻来源使用与这些专注于移民的公民社会组织相似语言的程度。

我们已经处理了文章和预训练向量；现在需要处理新闻稿。让我们使用与处理“所有新闻”（ATN）文章相同的预处理工作流来加载和处理它们。

67 还有其他策略。参见 Lix 及其同事（2022）以了解一种方法。
68 它是土壤移动距离（EMD）的一个分支，EMD 比较两个概率分布的相似程度。
69 查找此矩阵称为运输问题。
70 新闻稿随 text2map.corpora 提供，并从两家右翼组织（移民研究中心和美国移民改革联合会）及两家左翼组织（移民和难民权利全国网络和妇女难民委员会）的网站上抓取。

```
data("corpus_itpr", package = "text2map.corpora")
data("contractions", package = "qpadDictionaries")
```

```
df_itpr <- corpus_itpr |>
  mutate(text = replace_non_ascii(text),
         text = replace_url(text, replacement = " "),
         text = replace_html(text, replacement = " "),
         text = replace_contraction(text,
                                  contraction.key = contractions,
                                  ignore.case = TRUE),
         text = str_replace_all(text, "[[:punct:]]", " "),
         text = replace_ordinal(text),
         text = str_replace_all(text, "[\\s]+", " "),
         text = tolower(text)
  )
```

```
dtm_itpr <- df_itpr |>
  dtm_builder(text, doc_id) |>
  dtm_stopword(stop_list = get_stoplist("snowball2014"),
               stop_docprop = c(.01, Inf))
```

现在我们希望将 ATN DTM 子集化，仅包含我们左翼和右翼来源的文章。我们将 Talking Points Memo、《纽约时报》、Buzzfeed News 作为左翼来源，将 Breitbart、Fox News 和 National Review 作为右翼来源。

```
df_atn_sub <- df_atn |>
  select(doc_id, lean, date, publication, text) |>
  filter(publication == "Talking Points Memo" |
         publication == "New York Times" |
         publication == "Buzzfeed News" |
         publication == "Breitbart" |
         publication == "Fox News" |
         publication == "National Review")
```

```
dtm_atn_sub <- df_atn_sub |> dtm_builder(text, doc_id)
```

三个项目——ATN DTM、新闻稿 DTM 和嵌入空间——中的词汇表必须相同。让我们现在确保这一点。

```
vocab <- intersect(rownames(atn_vectors), colnames(dtm_atn_sub))
vocab <- intersect(vocab, colnames(dtm_itpr))
```

```
atn_vecs_sub <- atn_vectors[vocab, ]
dtm_atn_sub <- dtm_atn_sub[, vocab]
dtm_itpr <- dtm_itpr[, vocab]
```

现在，我们可以使用 text2vec 查找 WMD 得分。71

```
wmd_mod <- RWMD$new(x = dtm_itpr, embeddings = atn_vecs_sub)
wmd_dis <- wmd_mod$sim2(x = dtm_atn_sub)
```

这给我们留下了一个 a×p 矩阵，其中 a 是文章数量，p 是新闻稿数量。每个 a、p 单元格告诉我们 a 到 p 的相似度，较高值表示更高的相似度。72

我们可以用这个矩阵做很多事。如果新闻稿都在新闻文章之前发布（事实并非如此），我们可以使用扩散建模。尽管如此，我们可以了解哪些文章更有可能就相同的事物——并且以相同的方式——撰写，就像这些移民民间团体一样。让我们看看，例如，左翼或右翼新闻组织与左翼或右翼移民团体的相似度是否更高。我们将为此使用简单的可视化——尽管我们可以采用统计检验。

我们首先将 a×p 距离矩阵转换为数据框，添加一些行名，然后使用这些行名将一些 ATN 元数据合并到相似度中。这样我们就可以看到相似度如何随文章特征而变化。

```
df_sim <- wmd_dis |> 
  as.data.frame() |> 
  rownames_to_column(var = "doc_id")
df_sim <- left_join(df_sim, df_atn_sub, by = "doc_id")
```

接下来，我们将计算每篇文章与右翼和左翼新闻稿的平均相似度。距离矩阵的列按新闻稿的顺序排列。我们将创建一个 TRUE 和 FALSE 索引以正确地对其进行子集化。

```
r_idx <- df_itpr$lean == "Right"
l_idx <- df_itpr$lean == "Left"
df_atn_sub$wmd_r <- rowMeans(wmd_dis[, r_idx])
df_atn_sub$wmd_l <- rowMeans(wmd_dis[, l_idx])
```

然后将数据框重塑为“长格式”，然后绘制图表。

```
df_plot <- df_atn_sub |> 
  select(doc_id, lean, date, wmd_r, wmd_l) |> 
  pivot_longer(cols = c("wmd_r", "wmd_l")) |> 
  mutate(name = case_when(
    grepl("wmd_r", name) ~ "Right-Wing Press Releases",
    grepl("wmd_l", name) ~ "Left-Wing Press Releases"
  ))
```

```
df_plot |> 
  ggplot(aes(x = as.Date(date), y = value, color = name)) + 
  geom_smooth(aes(linetype = name)) + 
  scale_linetype_manual(values=c("twodash", "solid"))+ 
  labs(x = NULL, y = "Average Similarity to Press Releases") + 
  guides(linetype = guide_legend(nrow = 2)) + 
  theme(legend.position = c(.65, .1)) + 
  facet_wrap(~lean)
```

图 11.9 表明，除其他外，左翼新闻来源在讨论移民时与左翼和右翼移民组织使用相似语言的数量相等，而右翼新闻在移民话语方面总体上稍微偏右。

