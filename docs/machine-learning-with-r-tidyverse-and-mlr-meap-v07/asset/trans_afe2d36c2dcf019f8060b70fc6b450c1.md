...[/content] as per instructions. Also need to keep bold/italic symbols, code unchanged, links translation. The text includes images, code blocks, etc. Must translate content but keep code unchanged. Also need to translate the caption text (Figure 14.6, 14.7). Also need to translate the "IMPORTANT" note. Also need to translate the description of UMAP, etc. Also need to translate the "TIP" note. Also need to translate the "Listing 14.1 Running t-SNE" caption? The code block itself stays unchanged. The surrounding description should be translated.

We must ensure we don't miss any lines. Also ensure we don't output any extra text outside [content]...[/content].

Let's parse the content:

First line: `![](img/a22105d68c35e8d5bd3c7bafb4644881_351_0.png)` - This is an image, not text, but we need to translate? It's an image, no text to translate. Probably keep as is (no translation). But maybe we need to translate the caption "Figure 14.6 ..." which follows.

Next: "Figure 14.6 The effect of changing max_iter (row facets) and eta (column facets) using the default values of theta and perplexity, on the final t-SNE embedding of the swissTib dataset."

We need to translate that caption into Chinese, preserving "Figure 14.6". So Chinese: "图 14.6 更改 max_iter（行 facetas）和 eta（列 facetas）的影响，使用默认的 theta 和 perplexity，在 swissTib 数据集的最终 t-SNE 嵌入中。" Something like that.

Then the paragraph: "So now that we’re a little more clued up about how t-SNE’s hyperparameters affect its performance, let’s run t-SNE on our Swiss banknote dataset. Just like for PCA, I first select all the columns except the categorical variable (t-SNE also cannot handle categorical variables), and pipe this data into the `Rtsne()` function. I manually set the values of the perplexity, theta, and max_iter hyperparameters (honestly, I rarely alter eta), and set the argument `verbose = TRUE` so the algorithm prints a running commentary on what the Kullback–Leibler divergence is at each iteration."

Translate to Chinese, preserving code formatting.

Next: "### Listing 14.1 Running t-SNE" - This is a section header. Should translate? The instruction: "列表，表格，引用块保留格式，翻译内容". For headings, likely translate as well. So "### 运行 t-SNE 列表 14.1"? Actually "Listing 14.1 Running t-SNE" is a caption for a code listing. In Chinese we might translate to "### 运行 t-SNE 列表 14.1". But maybe keep "Listing 14.1" as is? The instruction says translate content, but keep format. I'd translate the caption: "### 运行 t-SNE 列表 14.1". However maybe better: "### 运行 t-SNE 示例 14.1". Let's decide: "### 运行 t-SNE 列表 14.1". Keep the "###" heading.

Then code block:

```r
swissTsne <- select(swissTib, -Status) %>%
  Rtsne(perplexity = 30, theta = 0, max_iter = 5000, verbose = TRUE)
```

We keep unchanged.

Then a blockquote:

> **TIP**  By default, the `Rtsne()` function reduces the dataset down to two dimensions. If you want to return another number, you can set this using the `dims` argument.

Translate: "**TIP** 默认情况下，`Rtsne()` 函数会将数据集降维到两个维度。如果您想返回其他数值，可以使用 `dims` 参数进行设置。" Also keep bold.

Next paragraph: "That didn’t take too long did it? For a small dataset like this, t-SNE takes only a few seconds. But it gets slow quickly (see what I did there?) as the dataset increases in size."

Translate.

Next: "Next, let's plot the two t-SNE dimensions against each other to see how well they separated the genuine and counterfeit banknotes."

Translate.

Next: "As we can't interpret the axes in terms of how much each variable correlates with them, it's common for people to color their t-SNE plots by the values of each of their original variables, to help identify which clusters have higher and lower values. To do this, I first use the mutate_if() function to center the numeric variables in our original dataset (by setting .funs = scale, and .predicate = is.numeric). I include scale = FALSE to only center the variables, not divide by their standard deviations. The reason I center the variables is that I'm going to shade by their value on the plots, and I don't want variables with larger values dominating the color scales (omit this line and see the difference in the final plot for yourself)."

Translate.

Next: "Next, I mutate two new columns that contain the t-SNE axes values for each case. Finally, I gather the data so that I can facet by each of the original variables. I plot this data, mapping the value of each original variable to the color aesthetic, the status of each banknote (genuine vs counterfeit) to the shape aesthetic, and facet by the original variables. I add a custom color scale gradient to make the color scale more readable in print."

Translate.

Then code block:

```r
swissTibTsne <- swissTib %>%
mutate_if(.funs = scale, .predicate = is.numeric, scale = FALSE) %>%
mutate(tSNE1 = swissTsne$Y[, 1], tSNE2 = swissTsne$Y[, 2]) %>%
gather(key = "Variable", value = "Value", c(-tSNE1, -tSNE2, -Status))
ggplot(swissTibTsne, aes(tSNE1, tSNE2, col = Value, shape = Status)) +
facet_wrap(~ Variable) +
geom_point(size = 3) +
scale_color_gradient(low = "dark blue", high = "cyan") +
theme_bw()
```

We keep unchanged.

Next paragraph: "The resulting plot from code listing 14.2 is shown in figure 14.7. Wow! Notice how much better a job t-SNE does of representing the differences between the two clusters in a two-dimensional space than PCA? The clusters are well resolved, although if you look closely you can see a couple of cases that seem to be in the wrong cluster. Shading the points by the value of each variable also helps us identify that counterfeit notes tend to have lower values of the Diagonal variable, and higher values of the Bottom and Top variables. It also seems like there might be a small, second cluster of counterfeit notes. This could be a set of notes made by a different counterfeiter, or it could be an artefact of an imperfect combination of hyperparameters. More investigation would be needed to tell if these are actually a distinct cluster or not."

Translate.

Next: "### IMPORTANT" - maybe translate to "### 重要". Keep the marker.

Then: "Do your plots look a little different to mine? Of course they do! Remember that the initial embedding is random (stochastic), so each time you run t-SNE on the same data and with the same hyperparameters, you’ll get a slightly different embedding."

Translate.

Next: image line: `![](img/a22105d68c35e8d5bd3c7bafb4644881_353_0.png)` keep.

Then caption: "Figure 14.7 tSNE1 and tSNE2 axes plotted against each other, faceted and shaded by the original variables, and shaped by whether each case was a genuine or counterfeit banknote."

Translate: "图 14.7 tSNE1 和 tSNE2 轴对角线上绘制，按原始变量分面并按颜色显示原始变量，按形状显示是否为真实或伪造银行钞。" Something like that.

Next paragraph: "Recreate the plot in figure 14.7, but this time don’t center the variables before running t-SNE on them (just remove the mutate_if() layer. Can you see why scaling was necessary?)"

Translate.

Next: "In this section, I’ll show you what UMAP is, how it works, and why it’s useful. Uniform manifold approximation and projection, thankfully shortened to UMAP, is a non-linear dimension reduction algorithm like t-SNE. UMAP is state of the art, having only been published in 2018, and has a few benefits over the t-SNE algorithm."

Translate.

Next: "Firstly, it’s considerably faster than t-SNE, where the length of time it takes to run increases less than the square of the number of cases in the dataset. To put this in perspective, a dataset that might take t-SNE hours to compress, will take UMAP minutes."

Translate.

Next: "The second benefit (and the main benefit in my eyes) is that UMAP is a deterministic algorithm. In other words, given the same input, it will always give the same output. This means that, unlike t-SNE, we can project new data onto the lower-dimensional representation, allowing us to incorporate UMAP into our machine learning pipelines."

Translate.

Next: "The third benefit is that UMAP preserves both local *and* global structure. Practically, this means that not only can we interpret two cases close to each other in lower dimensions as being similar to each other in high dimensions, we can also interpret two *clusters* of cases close to each other as being more similar to each other in high dimensions."

Translate.

Next: "So how does UMAP work? Well, UMAP assumes the data is distributed along a *manifold*. A manifold is an n-dimensional smooth geometric shape where, for every point on this manifold, there exists a small neighborhood around that point that looks like a flat, two-dimensional plane. If that doesn’t make sense to you, consider that the world is a three-dimensional manifold, any part of which can be mapped into a flat representation, literally called a map. So UMAP searches for a surface, or a higher-dimensional space that the data are distributed along. The distances between cases *along the manifold* can then be calculated, and a lower-dimensional representation of the data can be optimized iteratively to reproduce these distances."

Translate.

Next: "Prefer a visual representation? Me too. Have a look at figure 14.8. I’ve drawn a question mark as a manifold, and randomly seeded 15 cases around the manifold across two variables. UMAP’s job is to learn the question mark manifold, so that it can measure the distances between cases along the manifold, instead of ordinary Euclidean distance, like t-SNE does. It achieves this by searching a region around each case, for another case. Where these regions encapsulate another case, the cases get connected by an edge. This is what I’ve done in the top row of figure 14.8, but can you see that the manifold is incomplete? There are gaps in my question mark. This is because the regions we searched around each case had the same radius, and the data wasn’t uniformly distributed along the manifold. If the cases were spaced out along the question mark at regular intervals, then this approach would have worked provided I selected an appropriate radius for the search regions."

Translate.

Next: "Real-world data are rarely evenly distributed, and so UMAP solves this problem in two ways. Firstly, it expands out each search region for each case until it meets its nearest neighbor. This ensures that there are no orphan cases: while there can be multiple, disconnected manifolds in a dataset, every case must connect to at least one other case. Secondly, UMAP creates an additional search region which has a larger radius in low-density areas, and a smaller radius in high-density regions. These search regions are described as "fuzzy", in that the further from the center another case finds itself, the lower the probability that an edge exists between those cases."

Translate.

We need to ensure we keep all line breaks as in original? The instruction: "原文可能有多行，不要漏掉任何一行，并且注意一定不要重复输出原文！！！" So we need to preserve line breaks as in original. That means we need to keep each line as separate line in translation, not merging paragraphs.

We must also keep code blocks unchanged, and keep image lines unchanged.

We need to wrap everything in [content]...[/content].

Let's construct the translation line by line.

Original lines:

1. `![](img/a22105d68c35e8d5bd3c7bafb4644881_351_0.png)`

2. `Figure 14.6 The effect of changing max_iter (row facets) and eta (column facets) using the default values of theta and perplexity, on the final t-SNE embedding of the swissTib dataset.`

3. `So now that we’re a little more clued up about how t-SNE’s hyperparameters affect its performance, let’s run t-SNE on our Swiss banknote dataset. Just like for PCA, I first select all the columns except the categorical variable (t-SNE also cannot handle categorical variables), and pipe this data into the `Rtsne()` function. I manually set the values of the perplexity, theta, and max_iter hyperparameters (honestly, I rarely alter eta), and set the argument `verbose = TRUE` so the algorithm prints a running commentary on what the Kullback–Leibler divergence is at each iteration.`

4. `### Listing 14.1 Running t-SNE`

5. ````r
swissTsne <- select(swissTib, -Status) %>%
  Rtsne(perplexity = 30, theta = 0, max_iter = 5000, verbose = TRUE)
````

6. `> **TIP**  By default, the `Rtsne()` function reduces the dataset down to two dimensions. If you want to return another number, you can set this using the `dims` argument.`

7. `That didn’t take too long did it? For a small dataset like this, t-SNE takes only a few seconds. But it gets slow quickly (see what I did there?) as the dataset increases in size.`

8. `Next, let's plot the two t-SNE dimensions against each other to see how well they separated the genuine and counterfeit banknotes.`

9. `As we can't interpret the axes in terms of how much each variable correlates with them, it's common for people to color their t-SNE plots by the values of each of their original variables, to help identify which clusters have higher and lower values. To do this, I first use the mutate_if() function to center the numeric variables in our original dataset (by setting .funs = scale, and .predicate = is.numeric). I include scale = FALSE to only center the variables, not divide by their standard deviations. The reason I center the variables is that I'm going to shade by their value on the plots, and I don't want variables with larger values dominating the color scales (omit this line and see the difference in the final plot for yourself).`

10. `Next, I mutate two new columns that contain the t-SNE axes values for each case. Finally, I gather the data so that I can facet by each of the original variables. I plot this data, mapping the value of each original variable to the color aesthetic, the status of each banknote (genuine vs counterfeit) to the shape aesthetic, and facet by the original variables. I add a custom color scale gradient to make the color scale more readable in print.`

11. Code block (unchanged)

12. `The resulting plot from code listing 14.2 is shown in figure 14.7. Wow! Notice how much better a job t-SNE does of representing the differences between the two clusters in a two-dimensional space than PCA? The clusters are well resolved, although if you look closely you can see a couple of cases that seem to be in the wrong cluster. Shading the points by the value of each variable also helps us identify that counterfeit notes tend to have lower values of the Diagonal variable, and higher values of the Bottom and Top variables. It also seems like there might be a small, second cluster of counterfeit notes. This could be a set of notes made by a different counterfeiter, or it could be an artefact of an imperfect combination of hyperparameters. More investigation would be needed to tell if these are actually a distinct cluster or not.`

13. `### IMPORTANT`

14. `Do your plots look a little different to mine? Of course they do! Remember that the initial embedding is random (stochastic), so each time you run t-SNE on the same data and with the same hyperparameters, you’ll get a slightly different embedding.`

15. `![](img/a22105d68c35e8d5bd3c7bafb4644881_353_0.png)`

16. `Figure 14.7 tSNE1 and tSNE2 axes plotted against each other, faceted and shaded by the original variables, and shaped by whether each case was a genuine or counterfeit banknote.`

17. `Recreate the plot in figure 14.7, but this time don’t center the variables before running t-SNE on them (just remove the mutate_if() layer. Can you see why scaling was necessary?)`

18. `In this section, I’ll show you what UMAP is, how it works, and why it’s useful. Uniform manifold approximation and projection, thankfully shortened to UMAP, is a non-linear dimension reduction algorithm like t-SNE. UMAP is state of the art, having only been published in 2018, and has a few benefits over the t-SNE algorithm.`

19. `Firstly, it’s considerably faster than t-SNE, where the length of time it takes to run increases less than the square of the number of cases in the dataset. To put this in perspective, a dataset that might take t-SNE hours to compress, will take UMAP minutes.`

20. `The second benefit (and the main benefit in my eyes) is that UMAP is a deterministic algorithm. In other words, given the same input, it will always give the same output. This means that, unlike t-SNE, we can project new data onto the lower-dimensional representation, allowing us to incorporate UMAP into our machine learning pipelines.`

21. `The third benefit is that UMAP preserves both local *and* global structure. Practically, this means that not only can we interpret two cases close to each other in lower dimensions as being similar to each other in high dimensions, we can also interpret two *clusters* of cases close to each other as being more similar to each other in high dimensions.`

22. `So how does UMAP work? Well, UMAP assumes the data is distributed along a *manifold*. A manifold is an n-dimensional smooth geometric shape where, for every point on this manifold, there exists a small neighborhood around that point that looks like a flat, two-dimensional plane. If that doesn’t make sense to you, consider that the world is a three-dimensional manifold, any part of which can be mapped into a flat representation, literally called a map. So UMAP searches for a surface, or a higher-dimensional space that the data are distributed along. The distances between cases *along the manifold* can then be calculated, and a lower-dimensional representation of the data can be optimized iteratively to reproduce these distances.`

23. `Prefer a visual representation? Me too. Have a look at figure 14.8. I’ve drawn a question mark as a manifold, and randomly seeded 15 cases around the manifold across two variables. UMAP’s job is to learn the question mark manifold, so that it can measure the distances between cases along the manifold, instead of ordinary Euclidean distance, like t-SNE does. It achieves this by searching a region around each case, for another case. Where these regions encapsulate another case, the cases get connected by an edge. This is what I’ve done in the top row of figure 14.8, but can you see that the manifold is incomplete? There are gaps in my question mark. This is because the regions we searched around each case had the same radius, and the data wasn’t uniformly distributed along the manifold. If the cases were spaced out along the question mark at regular intervals, then this approach would have worked provided I selected an appropriate radius for the search regions.`

24. `Real-world data are rarely evenly distributed, and so UMAP solves this problem in two ways. Firstly, it expands out each search region for each case until it meets its nearest neighbor. This ensures that there are no orphan cases: while there can be multiple, disconnected manifolds in a dataset, every case must connect to at least one other case. Secondly, UMAP creates an additional search region which has a larger radius in low-density areas, and a smaller radius in high-density regions. These search regions are described as "fuzzy", in that the further from the center another case finds itself, the lower the probability that an edge exists between those cases.`

Now translate each line, preserving line breaks.

We need to keep code blocks unchanged, and image lines unchanged.

Let's translate:

1. Keep as is.

2. Translate: "图 14.6 更改 max_iter（行 facetas）和 eta（列 facetas）的影响，使用默认的 theta 和 perplexity，在 swissTib 数据集的最终 t-SNE 嵌入中。"

3. Translate: "现在我们对 t-SNE 的超参数对其性能的影响有了更深入的了解，让我们在瑞士银行钞数据集上运行 t-SNE。就像 PCA 那样，我首先选择除去类别变量（t-SNE 也无法处理类别变量）的所有列，并将这些数据管道化到 `Rtsne()` 函数中。我手动设置 perplexity、theta 和 max_iter 超参数的值（老实说，我很少改变 eta），并将 `verbose = TRUE` 参数设置为 TRUE，以便算法在每次迭代时打印 Kullback–Leibler divergence 的运行 commentary。"

Need to keep backticks for code.

4. Translate heading: "### 运行 t-SNE 列表 14.1" (maybe "### 运行 t-SNE 示例 14.1"? I'll choose "### 运行 t-SNE 列表 14.1".)

5. Keep code unchanged.

6. Translate: "**TIP** 默认情况下，`Rtsne()` 函数会将数据集降维到两个维度。如果您想返回其他数值，可以使用 `dims` 参数进行设置。"

7. Translate: "这并不花费太长时间吧？对于像这样小的数据集，t-SNE 只需几秒钟即可完成。但随着数据集规模扩大，它会变得很快（参见我在这里的双关语）而变得缓慢。"

8. Translate: "接下来，让我们把两个 t-SNE 维度对角线上绘制，以观察它们如何分离真实和伪造的银行钞。"

9. Translate: "由于我们无法从轴上解释它们与每个变量相关性的程度，通常人们会用原始变量的值为 t-SNE 图表上色，以帮助识别哪些聚类的值更高或更低。为此，我首先使用 mutate_if() 函数对原始数据集中的数值变量进行中心化（通过设置 .funs = scale 并 .predicate = is.numeric）。我把 scale = FALSE 设置为仅中心化变量，而不除以标准差。中心化变量的原因是我将在图中对颜色进行阴影处理，不希望数值较大的变量主导颜色尺度（省略此行并自行观察最终图表的差异）。"

10. Translate: "接下来，我为每个案例新增两列，包含 t-SNE 轴的值。最后，我将数据聚合，以便按每个原始变量进行分面。我绘制该数据，将每个原始变量的值映射到颜色美学，银行钞的状态（真实 vs 伪造）映射到形状美学，并按原始变量进行分面。我添加了一个自定义的颜色渐变尺度，以便在打印时更易阅读颜色尺度。"

11. Keep code unchanged.

12. Translate: "代码列表 14.2 的结果图显示于图 14.7。哇！注意 t-SNE 在二维空间中比 PCA 更好地表示两个聚类之间的差异。聚类已经很好地区分，尽管仔细观察可以看到一些似乎被归到错误聚类的案例。通过按变量的值对点进行阴影处理，我们还能够识别出伪造钞票倾向于具有较低的对角线变量值，以及较高的底部和顶部变量值。此外，似乎还有一个较小的第二个伪造钞票聚类。这可能是由不同的伪造者制作的钞票，也可能是由于不完美的超参数组合造成的伪影。需要更多的调查才能判断这些是否是一个独立的聚类。"

13. Keep "### IMPORTANT" unchanged (maybe translate to Chinese "### 重要" but instruction says keep format, translate content. So translate "IMPORTANT" to "重要". So "### 重要". Keep the marker.

14. Translate: "您的图表会与我的有点不同吧？当然会！请记住，初始嵌入是随机（随机性）的，因此每次在相同的数据和相同的超参数下运行 t-SNE，您都会得到略有不同的嵌入。"

15. Keep image unchanged.

16. Translate: "图 14.7 tSNE1 和 tSNE2 轴对角线上绘制，按原始变量分面并按颜色显示原始变量，按形状显示是否为真实或伪造银行钞。"

17. Translate: "请在图 14.7 中重新创建图表，但这次在运行 t-SNE 之前不要先对变量进行中心化（只需删除 mutate_if() 层。您能看出为什么缩放是必要的吗？"

18. Translate: "在本节中，我将向您展示 UMAP 是什么，它是如何工作的，以及为什么有用。Uniform Manifold Approximation and Projection，缩写为 UMAP，是一种非线性维度减少算法，类似于 t-SNE。UMAP 是最先进的，仅在 2018 年发表，并且相较于 t-SNE 具有若干优势。"

19. Translate: "首先，它比 t-SNE 快得多，运行时间增长速度小于数据案例数的平方。为了说明这一点，一个可能需要 t-SNE 数小时才能压缩的数据集，使用 UMAP 只需几分钟。"

20. Translate: "第二个好处（在我看来也是主要好处）是 UMAP 是确定性算法。换句话说，给定相同的输入，它总会产生相同的输出。这意味着，与 t-SNE 不同，我们可以将新数据投影到低维表示中，从而将 UMAP 融入我们的机器学习管道。"

21. Translate: "第三个好处是 UMAP 同时保留局部 *和* 全局结构。实际上，这意味着我们不仅可以将两个在低维空间中靠近的案例解释为在高维空间中相似，还可以将两个 *聚类* 中靠近的案例解释为在高维空间中更相似。"

22. Translate: "那么 UMAP 如何工作呢？ well，UMAP 假设数据分布在 *多重体* 上。多重体是 n 维的光滑几何形状，对于多重体上的每一点，都存在一个小邻域，该邻域看起来像平面的二维平面。如果这对您来说不太好理解，可以考虑世界是三维的多重体，其任何部分都可以映射到平面表示，字面上称为地图。因此，UMAP 寻找一个表面，或数据分布的更高维空间。然后可以计算案例 *沿多重体* 的距离，并通过迭代优化 lower-dimensional 表示来复制这些距离。"

Need to keep italic markers * for local and global, manifold etc. In Chinese translation we need to keep the asterisks for italic markup. The original had *local* and *global* and *manifold*. We need to preserve those asterisks. So we need to keep *local* and *global* and *manifold* as italic. Also *and* maybe. Let's ensure we keep asterisks.

Original: "The third benefit is that UMAP preserves both local *and* global structure." So we need to translate while preserving *and* inside asterisks. So Chinese: "UMAP 同时保留局部 *and* 全局结构。" Keep *and*.

Also "A manifold is an n-dimensional smooth geometric shape where, for every point on this manifold, there exists a small neighborhood around that point that looks like a flat, two-dimensional plane." So translate: "多重体是 n 维的光滑几何形状，对于多重体上的每一点，都存在一个小邻域，该邻域看起来像平面的二维平面。" Keep *manifold* italic.

Also "If that doesn’t make sense to you, consider that the world is a three-dimensional manifold, any part of which can be mapped into a flat representation, literally called a map." So translate: "如果这对您来说不太好理解，可以考虑世界是三维的 *manifold*，其任何部分都可以映射到平面表示，字面上称为地图。" Keep *manifold* italic.

Also "So UMAP searches for a surface, or a higher-dimensional space that the data are distributed along." So translate: "因此，UMAP 寻找一个表面，或数据分布的更高维空间。" No italic needed.

"The distances between cases *along the manifold* can then be calculated, and a lower-dimensional representation of the data can be optimized iteratively to reproduce these distances." So translate: "然后可以计算案例 *沿多重体* 的距离，并通过迭代优化 lower-dimensional 表示来复制这些距离。" Keep *along the manifold* italic.

"Prefer a visual representation? Me too. Have a look at figure 14.8. I’ve drawn a question mark as a manifold, and randomly seeded 15 cases around the manifold across two variables." Translate: "如果您更喜欢视觉呈现，我也如此。请查看图 14.8。我把一个问号作为多重体绘制，并在两个变量之间随机种下 15 个案例。" Keep *manifold* italic.

"UMAP’s job is to learn the question mark manifold, so that it can measure the distances between cases along the manifold, instead of ordinary Euclidean distance, like t-SNE does." Translate: "UMAP 的任务是学习问号多重体，以便它能够测量案例 *沿多重体* 的距离，而不是像 t-SNE 那样使用普通欧几里得距离。" Keep *along the manifold* italic.

"It achieves this by searching a region around each case, for another case. Where these regions encapsulate another case, the cases get connected by an edge." Translate: "它通过在每个案例周围搜索一个区域，寻找另一个案例。当这些区域包围另一个案例时，案例会通过边连接在一起。"

"This is what I’ve done in the top row of figure 14.8, but can you see that the manifold is incomplete? There are gaps in my question mark." Translate: "这是我在图 14.8 的上方行中所做的，但您能看到多重体是不完整的吗？我的问号上有缺口。"

"This is because the regions we searched around each case had the same radius, and the data wasn’t uniformly distributed along the manifold." Translate: "这是因为我们在每个案例周围搜索的区域半径相同，而数据在多重体上并不均匀分布。"

"If the cases were spaced out along the question mark at regular intervals, then this approach would have worked provided I selected an appropriate radius for the search regions." Translate: "如果案例在问号上以均匀间隔分布，那么在选择合适的搜索区域半径后，这种方法就会成功。"

"Real-world data are rarely evenly distributed, and so UMAP solves this problem in two ways." Translate: "现实世界的数据很少是均匀分布的，因此 UMAP 通过两种方式解决这个问题。"

"Firstly, it expands out each search region for each case until it meets its nearest neighbor." Translate: "首先，它会扩展每个案例的搜索区域，直到它与最近的邻居相遇。"

"This ensures that there are no orphan cases: while there can be multiple, disconnected manifolds in a dataset, every case must connect to at least one other case." Translate: "这确保了没有孤立的案例：虽然数据集中可能存在多个不相连的多重体，但每个案例都必须与至少一个其他案例相连。"

"Secondly, UMAP creates an additional search region which has a larger radius in low-density areas, and a smaller radius in high-density regions." Translate: "其次，UMAP 创建一个额外的搜索区域，在低密度区域具有更大的半径，在高密度区域具有更小的半径。"

"These search regions are described as "fuzzy", in that the further from the center another case finds itself, the lower the probability that an edge exists between those cases." Translate: "这些搜索区域被描述为 \"模糊\"，即离中心更远时，另一个案例发现自己所在的概率越低，两个案例之间存在边的可能性也越低。" Keep quotes.

Now need to ensure we preserve line breaks exactly as original. Let's count lines.

Original lines list (including blank lines?). The original text includes blank lines between paragraphs. We need to keep line breaks as in original, but we can combine paragraphs as separate lines. The instruction: "原文可能有多行，不要漏掉任何一行". So we need to keep each line as separate line in output. That means we need to replicate the line breaks exactly as they appear in the original. Let's examine original text as given:

[content]

![](img/a22105d68c35e8d5bd3c7bafb4644881_351_0.png)

Figure 14.6 The effect of changing max_iter (row facets) and eta (column facets) using the default values of theta and perplexity, on the final t-SNE embedding of the swissTib dataset.

So line 1: image line.

Line 2: Figure 14.6 ... (single line)

Then blank line? There's a blank line after that? In the original, after Figure 14.6 line, there is a blank line before the next paragraph. Let's see the original snippet:

```
![](img/a22105d68c35e8d5bd3c7bafb4644881_351_0.png)

Figure 14.6 The effect of changing max_iter (row facets) and eta (column facets) using the default values of theta and perplexity, on the final t-SNE embedding of the swissTib dataset.

So now that we’re a little more clued up about how t-SNE’s hyperparameters affect its performance, let’s run t-SNE on our Swiss banknote dataset. Just like for PCA, I first select all the columns except the categorical variable (t-SNE also cannot handle categorical variables), and pipe this data into the `Rtsne()` function. I manually set the values of the perplexity, theta, and max_iter hyperparameters (honestly, I rarely alter eta), and set the argument `verbose = TRUE` so the algorithm prints a running commentary on what the Kullback–Leibler divergence is at each iteration.

### Listing 14.1 Running t-SNE

```r
swissTsne <- select(swissTib, -Status) %>%
  Rtsne(perplexity = 30, theta = 0, max_iter = 5000, verbose = TRUE)
```

> **TIP**  By default, the `Rtsne()` function reduces the dataset down to two dimensions. If you want to return another number, you can set this using the `dims` argument.

That didn’t take too long did it? For a small dataset like this, t-SNE takes only a few seconds. But it gets slow quickly (see what I did there?) as the dataset increases in size.

Next, let's plot the two t-SNE dimensions against each other to see how well they separated the genuine and counterfeit banknotes.

As we can't interpret the axes in terms of how much each variable correlates with them, it's common for people to color their t-SNE plots by the values of each of their original variables, to help identify which clusters have higher and lower values. To do this, I first use the mutate_if() function to center the numeric variables in our original dataset (by setting .funs = scale, and .predicate = is.numeric). I include scale = FALSE to only center the variables, not divide by their standard deviations. The reason I center the variables is that I'm going to shade by their value on the plots, and I don't want variables with larger values dominating the color scales (omit this line and see the difference in the final plot for yourself).

Next, I mutate two new columns that contain the t-SNE axes values for each case. Finally, I gather the data so that I can facet by each of the original variables. I plot this data, mapping the value of each original variable to the color aesthetic, the status of each banknote (genuine vs counterfeit) to the shape aesthetic, and facet by the original variables. I add a custom color scale gradient to make the color scale more readable in print.

```r
swissTibTsne <- swissTib %>%
mutate_if(.funs = scale, .predicate = is.numeric, scale = FALSE) %>%
mutate(tSNE1 = swissTsne$Y[, 1], tSNE2 = swissTsne$Y[, 2]) %>%
gather(key = "Variable", value = "Value", c(-tSNE1, -tSNE2, -Status))
ggplot(swissTibTsne, aes(tSNE1, tSNE2, col = Value, shape = Status)) +
facet_wrap(~ Variable) +
geom_point(size = 3) +
scale_color_gradient(low = "dark blue", high = "cyan") +
theme_bw()
```

The resulting plot from code listing 14.2 is shown in figure 14.7. Wow! Notice how much better a job t-SNE does of representing the differences between the two clusters in a two-dimensional space than PCA? The clusters are well resolved, although if you look closely you can see a couple of cases that seem to be in the wrong cluster. Shading the points by the value of each variable also helps us identify that counterfeit notes tend to have lower values of the Diagonal variable, and higher values of the Bottom and Top variables. It also seems like there might be a small, second cluster of counterfeit notes. This could be a set of notes made by a different counterfeiter, or it could be an artefact of an imperfect combination of hyperparameters. More investigation would be needed to tell if these are actually a distinct cluster or not.

### IMPORTANT

Do your plots look a little different to mine? Of course they do! Remember that the initial embedding is random (stochastic), so each time you run t-SNE on the same data and with the same hyperparameters, you’ll get a slightly different embedding.

![](img/a22105d68c35e8d5bd3c7bafb4644881_353_0.png)

Figure 14.7 tSNE1 and tSNE2 axes plotted against each other, faceted and shaded by the original variables, and shaped by whether each case was a genuine or counterfeit banknote.

Recreate the plot in figure 14.7, but this time don’t center the variables before running t-SNE on them (just remove the mutate_if() layer. Can you see why scaling was necessary?)

In this section, I’ll show you what UMAP is, how it works, and why it’s useful. Uniform manifold approximation and projection, thankfully shortened to UMAP, is a non-linear dimension reduction algorithm like t-SNE. UMAP is state of the art, having only been published in 2018, and has a few benefits over the t-SNE algorithm.

Firstly, it’s considerably faster than t-SNE, where the length of time it takes to run increases less than the square of the number of cases in the dataset. To put this in perspective, a dataset that might take t-SNE hours to compress, will take UMAP minutes.

The second benefit (and the main benefit in my eyes) is that UMAP is a deterministic algorithm. In other words, given the same input, it will always give the same output. This means that, unlike t-SNE, we can project new data onto the lower-dimensional representation, allowing us to incorporate UMAP into our machine learning pipelines.

The third benefit is that UMAP preserves both local *and* global structure. Practically, this means that not only can we interpret two cases close to each other in lower dimensions as being similar to each other in high dimensions, we can also interpret two *clusters* of cases close to each other as being more similar to each other in high dimensions.

So how does UMAP work? Well, UMAP assumes the data is distributed along a *manifold*. A manifold is an n-dimensional smooth geometric shape where, for every point on this manifold, there exists a small neighborhood around that point that looks like a flat, two-dimensional plane. If that doesn’t make sense to you, consider that the world is a three-dimensional *manifold*, any part of which can be mapped into a flat representation, literally called a map. So UMAP searches for a surface, or a higher-dimensional space that the data are distributed along. The distances between cases *along the manifold* can then be calculated, and a lower-dimensional representation of the data can be optimized iteratively to reproduce these distances.

Prefer a visual representation? Me too. Have a look at figure 14.8. I’ve drawn a question mark as a manifold, and randomly seeded 15 cases around the manifold across two variables. UMAP’s job is to learn the question mark manifold, so that it can measure the distances between cases along the manifold, instead of ordinary Euclidean distance, like t-SNE does. It achieves this by searching a region around each case, for another case. Where these regions encapsulate another case, the cases get connected by an edge. This is what I’ve done in the top row of figure 14.8, but can you see that the manifold is incomplete? There are gaps in my question mark. This is because the regions we searched around each case had the same radius, and the data wasn’t uniformly distributed along the manifold. If the cases were spaced out along the question mark at regular intervals, then this approach would have worked provided I selected an appropriate radius for the search regions.

Real-world data are rarely evenly distributed, and so UMAP solves this problem in two ways. Firstly, it expands out each search region for each case until it meets its nearest neighbor. This ensures that there are no orphan cases: while there can be multiple, disconnected manifolds in a dataset, every case must connect to at least one other case. Secondly, UMAP creates an additional search region which has a larger radius in low-density areas, and a smaller radius in high-density regions. These search regions are described as "fuzzy", in that the further from the center another case finds itself, the lower the probability that an edge exists between those cases.

[/content]

We need to replicate line breaks. Let's count lines:

1. `![](img/a22105d68c35e8d5bd3c7bafb4644881_351_0.png)` (line)

2. (blank line) maybe there is a blank line after image. In original, there is a blank line after image. We need to preserve blank lines. So line 2 is blank.

3. `Figure 14.6 The effect of changing max_iter (row facets) and eta (column facets) using the default values of theta and perplexity, on the final t-SNE embedding of the swissTib dataset.` (line)

4. (blank line) after that maybe there is a blank line before next paragraph. Let's see: after the figure caption line, there is a blank line then "So now that we’re..." So line 4 is blank.

5. `So now that we’re a little more clued up about how t-SNE’s hyperparameters affect its performance, let’s run t-SNE on our Swiss banknote dataset. Just like for PCA, I first select all the columns except the categorical variable (t-SNE also cannot handle categorical variables), and pipe this data into the `Rtsne()` function. I manually set the values of the perplexity, theta, and max_iter hyperparameters (honestly, I rarely alter eta), and set the argument `verbose = TRUE` so the algorithm prints a running commentary on what the Kullback–Leibler divergence is at each iteration.` (line)

6. (blank line) after that maybe there is a blank line before "### Listing 14.1 Running t-SNE". Let's see: after the long paragraph, there is a blank line then "### Listing 14.1 Running t-SNE". So line 6 is blank.

7. `### Listing 14.1 Running t-SNE` (line)

8. (blank line) after that maybe there is a blank line before code block. In original, after the heading there is a blank line then code block. So line 8 blank.

9. ```r (code start) (line)

10. `swissTsne <- select(swissTib, -Status) %>` (line)

11. `%` (line) Actually the code is split across lines: line 10: `swissTsne <- select(swissTib, -Status) %>` then line 11: `  Rtsne(perplexity = 30, theta = 0, max_iter = 5000, verbose = TRUE)` (indented). So we need to keep each line as separate.

12. ``` (closing code) (line)

13. (maybe blank line) after code block there is a blank line before > **TIP** line. Let's see: after code block, there is a blank line then > **TIP** line. So line 13 blank.

14. `> **TIP**  By default, the `Rtsne()` function reduces the dataset down to two dimensions. If you want to return another number, you can set this using the `dims` argument.` (line)

15. (blank line) after that maybe there is a blank line before "That didn’t take too long..." So line 15 blank.

16. `That didn’t take too long did it? For a small dataset like this, t-SNE takes only a few seconds. But it gets slow quickly (see what I did there?) as the dataset increases in size.` (line)

17. (blank line) after that maybe there is a blank line before "Next, let's plot..." So line 17 blank.

18. `Next, let's plot the two t-SNE dimensions against each other to see how well they separated the genuine and counterfeit banknotes.` (line)

19. (blank line) after that maybe there is a blank line before the next paragraph. Let's see: after that line, there is a blank line then "As we can't interpret..." So line 19 blank.

20. `As we can't interpret the axes in terms of how much each variable correlates with them, it's common for people to color their t-SNE plots by the values of each of their original variables, to help identify which clusters have higher and lower values. To do this, I first use the mutate_if() function to center the numeric variables in our original dataset (by setting .funs = scale, and .predicate = is.numeric). I include scale = FALSE to only center the variables, not divide by their standard deviations. The reason I center the variables is that I'm going to shade by their value on the plots, and I don't want variables with larger values dominating the color scales (omit this line and see the difference in the final plot for yourself).` (line)

20? Actually we need to keep track. Let's continue.

21. (blank line) after that maybe there is a blank line before "Next, I mutate..." So line 21 blank.

22. `Next, I mutate two new columns that contain the t-SNE axes values for each case. Finally, I gather the data so that I can facet by each of the original variables. I plot this data, mapping the value of each original variable to the color aesthetic, the status of each banknote (genuine vs counterfeit) to the shape aesthetic, and facet by the original variables. I add a custom color scale gradient to make the color scale more readable in print.` (line)

23. (blank line) after that maybe there is a blank line before code block. In original, after that paragraph there is a blank line then code block. So line 23 blank.

24. ```r (code start) (line)

25. `swissTibTsne <- swissTib %>` (line)

26. `mutate_if(.funs = scale, .predicate = is.numeric, scale = FALSE) %>` (line)

27. `mutate(tSNE1 = swissTsne$Y[, 1], tSNE2 = swissTsne$Y[, 2]) %>` (line)

28. `gather(key = "Variable", value = "Value", c(-tSNE1, -tSNE2, -Status))` (line)

29. `ggplot(swissTibTsne, aes(tSNE1, tSNE2, col = Value, shape = Status)) +` (line)

30. `facet_wrap(~ Variable) +` (line)

31. `geom_point(size = 3) +` (line)

32. `scale_color_gradient(low = "dark blue", high = "cyan") +` (line)

33. `theme_bw()` (line)

34. (blank line) after code block maybe there is a blank line before "The resulting plot..." So line 34 blank.

35. `The resulting plot from code listing 14.2 is shown in figure 14.7. Wow! Notice how much better a job t-SNE does of representing the differences between the two clusters in a two-dimensional space than PCA? The clusters are well resolved, although if you look closely you can see a couple of cases that seem to be in the wrong cluster. Shading the points by the value of each variable also helps us identify that counterfeit notes tend to have lower values of the Diagonal variable, and higher values of the Bottom and Top variables. It also seems like there might be a small, second cluster of counterfeit notes. This could be a set of notes made by a different counterfeiter, or it could be an artefact of an imperfect combination of hyperparameters. More investigation would be needed to tell if these are actually a distinct cluster or not.` (line)

36. (blank line) after that maybe there is a blank line before "### IMPORTANT". Let's see: after that paragraph, there is a blank line then "### IMPORTANT". So line 36 blank.

37. `### IMPORTANT` (line)

38. (blank line) after that maybe there is a blank line before "Do your plots..." So line 38 blank.

38. `Do your plots look a little different to mine? Of course they do! Remember that the initial embedding is random (stochastic), so each time you run t-SNE on the same data and with the same hyperparameters, you’ll get a slightly different embedding.` (line)

39. (blank line) after that maybe there is a blank line before image. So line 39 blank.

40. `![](img/a22105d68c35e8d5bd3c7bafb4644881_353_0.png)` (line)

41. (blank line) after image maybe there is a blank line before figure caption. So line 41 blank.

42. `Figure 14.7 tSNE1 and tSNE2 axes plotted against each other, faceted and shaded by the original variables, and shaped by whether each case was a genuine or counterfeit banknote.` (line)

43. (blank line) after that maybe there is a blank line before "Recreate the plot..." So line 43 blank.

44. `Recreate the plot in figure 14.7, but this time don’t center the variables before running t-SNE on them (just remove the mutate_if() layer. Can you see why scaling was necessary?)` (line)

45. (blank line) after that maybe there is a blank line before "In this section..." So line 45 blank.

46. `In this section, I’ll show you what UMAP is, how it works, and why it’s useful. Uniform manifold approximation and projection, thankfully shortened to UMAP, is a non-linear dimension reduction algorithm like t-SNE. UMAP is state of the art, having only been published in 2018, and has a few benefits over the t-SNE algorithm.` (line)

47. (blank line) after that maybe there is a blank line before "Firstly, it’s considerably faster..." So line 47 blank.

48. `Firstly, it’s considerably faster than t-SNE, where the length of time it takes to run increases less than the square of the number of cases in the dataset. To put this in perspective, a dataset that might take t-SNE hours to compress, will take UMAP minutes.` (line)

49. (blank line) after that maybe there is a blank line before "The second benefit..." So line 49 blank.

50. `The second benefit (and the main benefit in my eyes) is that UMAP is a deterministic algorithm. In other words, given the same input, it will always give the same output. This means that, unlike t-SNE, we can project new data onto the lower-dimensional representation, allowing us to incorporate UMAP into our machine learning pipelines.` (line)

51. (blank line) after that maybe there is a blank line before "The third benefit..." So line 51 blank.

52. `The third benefit is that UMAP preserves both local *and* global structure. Practically, this means that not only can we interpret two cases close to each other in lower dimensions as being similar to each other in high dimensions, we can also interpret two *clusters* of cases close to each other as being more similar to each other in high dimensions.` (line)

53. (blank line) after that maybe there is a blank line before "So how does UMAP work?" So line 53 blank.

54. `So how does UMAP work? Well, UMAP assumes the data is distributed along a *manifold*. A manifold is an n-dimensional smooth geometric shape where, for every point on this manifold, there exists a small neighborhood around that point that looks like a flat, two-dimensional plane. If that doesn’t make sense to you, consider that the world is a three-dimensional *manifold*, any part of which can be mapped into a flat representation, literally called a map. So UMAP searches for a surface, or a higher-dimensional space that the data are distributed along. The distances between cases *along the manifold* can then be calculated, and a lower-dimensional representation of the data can be optimized iteratively to reproduce these distances.` (line)

55. (blank line) after that maybe there is a blank line before "Prefer a visual representation?" So line 55 blank.

56. `Prefer a visual representation? Me too. Have a look at figure 14.8. I’ve drawn a question mark as a manifold, and randomly seeded 15 cases around the manifold across two variables. UMAP’s job is to learn the question mark manifold, so that it can measure the distances between cases along the manifold, instead of ordinary Euclidean distance, like t-SNE does. It achieves this by searching a region around each case, for another case. Where these regions encapsulate another case, the cases get connected by an edge. This is what I’ve done in the top row of figure 14.8, but can you see that the manifold is incomplete? There are gaps in my question mark. This is because the regions we searched around each case had the same radius, and the data wasn’t uniformly distributed along the manifold. If the cases were spaced out along the question mark at regular intervals, then this approach would have worked provided I selected an appropriate radius for the search regions.` (line)

57. (blank line) after that maybe there is a blank line before "Real-world data..." So line 57 blank.

58. `Real-world data are rarely evenly distributed, and so UMAP solves this problem in two ways. Firstly, it expands out each search region for each case until it meets its nearest neighbor. This ensures that there are no orphan cases: while there can be multiple, disconnected manifolds in a dataset, every case must connect to at least one other case. Secondly, UMAP creates an additional search region which has a larger radius in low-density areas, and a smaller radius in high-density regions. These search regions are described as "fuzzy", in that the further from the center another case finds itself, the lower the probability that an edge exists between those cases.` (line)

Now we need to translate each line accordingly, preserving blank lines.

We must be careful to keep code blocks unchanged (including backticks). Also need to keep image lines unchanged.

Now produce translation.

Let's go line by line.

1. Keep image line unchanged.

2. Blank line: keep as blank.

3. Translate figure caption: "图 14.6 更改 max_iter（行 facetas）和 eta（列 facetas）的影响，使用默认的 theta 和 perplexity，在 swissTib 数据集的最终 t-SNE 嵌入中。"

4. Blank line: keep blank.

5. Translate long paragraph: "现在我们对 t-SNE 的超参数对其性能的影响有了更深入的了解，让我们在瑞士银行钞数据集上运行 t-SNE。就像 PCA 那样，我首先选择除去类别变量（t-SNE 也无法处理类别变量）的所有列，并将这些数据管道化到 `Rtsne()` 函数中。我手动设置 perplexity、theta 和 max_iter 超参数的值（说实话，我很少改变 eta），并将 `verbose = TRUE` 参数设置为 TRUE，以便算法在每次迭代时打印 Kullback–Leibler divergence 的运行 commentary。" Need to keep backticks.

6. Blank line.

7. Translate: "这并不花费太长时间吧？对于像这样小的数据集，t-SNE 只需几秒钟即可完成。但随着数据集规模扩大，它会变得很快（参见我这里的双关语）而变得缓慢。"

8. Blank line.

9. Translate: "接下来，让我们把两个 t-SNE 维度对角线上绘制，以观察它们如何分离真实和伪造的银行钞。"

10. Blank line.

11. Translate: "由于我们无法从轴上解释它们与每个变量相关性的程度，通常人们会用原始变量的值为 t-SNE 图表上色，以帮助识别哪些聚类的值更高或更低。为此，我首先使用 mutate_if() 函数对原始数据集中的数值变量进行中心化（通过设置 .funs = scale 并 .predicate = is.numeric）。我把 scale = FALSE 设置为仅中心化变量，而不除以标准差。中心化变量的原因是我将在图中对颜色进行阴影处理，不希望数值较大的变量主导颜色尺度（省略此行并自行观察最终图表的差异）。"

12. Blank line.

13. Translate: "接下来，我为每个案例新增两列，包含 t-SNE 轴的值。最后，我将数据聚合，以便按每个原始变量进行分面。我绘制该数据，将每个原始变量的值映射到颜色美学，银行钞的状态（真实 vs 伪造）映射到形状美学，并按原始变量进行分面。我添加了一个自定义的颜色渐变尺度，以便在打印时更易阅读颜色尺度。"

14. Blank line.

14? Actually after that paragraph there is a blank line before code block. So line 13 blank.

14. Code block start: keep ```r unchanged.

15. `swissTsne <- select(swissTib, -Status) %>` unchanged.

16. `%` line unchanged.

17. `  Rtsne(perplexity = 30, theta = 0, max_iter = 5000, verbose = TRUE)` unchanged.

18. ``` (closing) unchanged.

19. Blank line.

20. Translate > **TIP** line: "**TIP** 默认情况下，`Rtsne()` 函数会将数据集降维到两个维度。如果您想返回其他数值，可以使用 `dims` 参数进行设置。" Keep bold and backticks.

21. Blank line.

21? Actually after TIP line there is a blank line then "That didn’t take too long..." So line 21 blank.

22. Translate: "这并不花费太长时间吧？对于像这样小的数据集，t-SNE 只需几秒钟即可完成。但随着数据集规模扩大，它会变得很快（参见我这里的双关语）而变得缓慢。"

23. Blank line.

24. Translate: "Next, let's plot the two t-SNE dimensions against each other to see how well they separated the genuine and counterfeit banknotes." => "接下来，让我们把两个 t-SNE 维度对角线上绘制，以观察它们如何分离真实和伪造的银行钞。" Wait that's same as earlier? Actually earlier we had that line (line 9). Let's verify: In original, after the TIP paragraph, there is "That didn’t take too long did it? ..." then blank, then "Next, let's plot the two t-SNE dimensions against each other to see how well they separated the genuine and counterfeit banknotes." So we need to translate that line.

So line 24 translation: "接下来，让我们把两个 t-SNE 维度对角线上绘制，以观察它们如何分离真实和伪造的银行钞。"

24. Blank line.

25. Translate: "As we can't interpret the axes in terms of how much each variable correlates with them, it's common for people to color their t-SNE plots by the values of each of their original variables, to help identify which clusters have higher and lower values. To do this, I first use the mutate_if() function to center the numeric variables in our original dataset (by setting .funs = scale, and .predicate = is.numeric). I include scale = FALSE to only center the variables, not divide by their standard deviations. The reason I center the variables is that I'm going to shade by their value on the plots, and I don't want variables with larger values dominating the color scales (omit this line and see the difference in the final plot for yourself)."

Translate to Chinese, preserving backticks and .funs etc.

"由于我们无法从轴上解释它们与每个变量相关性的程度，通常人们会用原始变量的值为 t-SNE 图表上色，以帮助识别哪些聚类的值更高或更低。为此，我首先使用 mutate_if() 函数对原始数据集中的数值变量进行中心化（通过设置 .funs = scale 并 .predicate = is.numeric）。我把 scale = FALSE 设置为仅中心化变量，而不除以标准差。中心化变量的原因是我将在图中对颜色进行阴影处理，不希望数值较大的变量主导颜色尺度（省略此行并自行观察最终图表的差异）。"

26. Blank line.

27. Translate: "Next, I mutate two new columns that contain the t-SNE axes values for each case. Finally, I gather the data so that I can facet by each of the original variables. I plot this data, mapping the value of each original variable to the color aesthetic, the status of each banknote (genuine vs counterfeit) to the shape aesthetic, and facet by the original variables. I add a custom color scale gradient to make the color scale more readable in print."

Translate: "接下来，我为每个案例新增两列，包含 t-SNE 轴的值。最后，我将数据聚合，以便按每个原始变量进行分面。我绘制该数据，将每个原始变量的值映射到颜色美学，银行钞的状态（真实 vs 伪造）映射到形状美学，并按原始变量进行分面。我添加了一个自定义的颜色渐变尺度，以便在打印时更易阅读颜色尺度。"

28. Blank line.

29. Code block start: keep ```r unchanged.

29. `swissTibTsne <- swissTib %>` unchanged.

30. `mutate_if(.funs = scale, .predicate = is.numeric, scale = FALSE) %>` unchanged.

31. `mutate(tSNE1 = swissTsne$Y[, 1], tSNE2 = swissTsne$Y[, 2]) %>` unchanged.

32. `gather(key = "Variable", value = "Value", c(-tSNE1, -tSNE2, -Status))` unchanged.

33. `ggplot(swissTibTsne, aes(tSNE1, tSNE2, col = Value, shape = Status)) +` unchanged.

34. `facet_wrap(~ Variable) +` unchanged.

35. `geom_point(size = 3) +` unchanged.

36. `scale_color_gradient(low = "dark blue", high = "cyan") +` unchanged.

37. `theme_bw()` unchanged.

38. Blank line.

39. Translate: "代码列表 14.2 的结果图显示于图 14.7。哇！注意 t-SNE 在二维空间中比 PCA 更好地表示两个聚类之间的差异。聚类已经很好地区分，尽管仔细观察可以看到一些似乎被归到错误聚类的案例。通过按变量的值对点进行阴影处理，我们还能够识别出伪造钞票倾向于具有较低的对角线变量值，以及较高的底部和顶部变量值。此外，似乎还有一个较小的第二个伪造钞票聚类。这可能是由不同的伪造者制作的钞票，也可能是由于不完美的超参数组合造成的伪影。需要更多的调查才能判断这些是否是一个独立的聚类。"

40. Blank line.

41. Translate: "### IMPORTANT" => "### 重要"

42. Blank line.

43. Translate: "Do your plots look a little different to mine? Of course they do! Remember that the initial embedding is random (stochastic), so each time you run t-SNE on the same data and with the same hyperparameters, you’ll get a slightly different embedding."

Translate: "您的图表会与我的有点不同吧？当然会！请记住，初始嵌入是随机（随机性）的，因此每次在相同的数据和相同的超参数下运行 t-SNE，您都会得到略有不同的嵌入。"

44. Blank line.

45. Image line unchanged.

46. Blank line.

47. Translate figure caption: "图 14.7 tSNE1 和 tSNE2 轴对角线上绘制，按原始变量分面并按颜色显示原始变量，按形状显示是否为真实或伪造银行钞。"

48. Blank line.

49. Translate: "请在图 14.7 中重新创建图表，但这次在运行 t-SNE 之前不要先对变量进行中心化（只需删除 mutate_if() 层。您能看出为什么缩放是必要的吗？"

50. Blank line.

51. Translate: "In this section, I’ll show you what UMAP is, how it works, and why it’s useful. Uniform manifold approximation and projection, thankfully shortened to UMAP, is a non-linear dimension reduction algorithm like t-SNE. UMAP is state of the art, having only been published in 2018, and has a few benefits over the t-SNE algorithm."

Translate: "在本节中，我将向您展示 UMAP 是什么，它是如何工作的，以及为什么有用。Uniform Manifold Approximation and Projection，缩写为 UMAP，是一种非线性维度减少算法，类似于 t-SNE。UMAP 是最先进的，仅在 2018 年发表，并且相较于 t-SNE 具有若干优势。"

52. Blank line.

53. Translate: "Firstly, it’s considerably faster than t-SNE, where the length of time it takes to run increases less than the square of the number of cases in the dataset. To put this in perspective, a dataset that might take t-SNE hours to compress, will take UMAP minutes."

Translate: "首先，它比 t-SNE 快得多，运行时间增长速度小于数据案例数的平方。为了说明这一点，一个可能需要 t-SNE 数小时才能压缩的数据集，使用 UMAP 只需几分钟。"

54. Blank line.

55. Translate: "The second benefit (and the main benefit in my eyes) is that UMAP is a deterministic algorithm. In other words, given the same input, it will always give the same output. This means that, unlike t-SNE, we can project new data onto the lower-dimensional representation, allowing us to incorporate UMAP into our machine learning pipelines."

Translate: "第二个好处（在我看来也是主要好处）是 UMAP 是确定性算法。换句话说，给定相同的输入，它总会产生相同的输出。这意味着，与 t-SNE 不同，我们可以将新数据投影到低维表示中，从而将 UMAP 融入我们的机器学习管道。"

56. Blank line.

57. Translate: "The third benefit is that UMAP preserves both local *and* global structure. Practically, this means that not only can we interpret two cases close to each other in lower dimensions as being similar to each other in high dimensions, we can also interpret two *clusters* of cases close to each other as being more similar to each other in high dimensions."

Translate: "第三个好处是 UMAP 同时保留局部 *and* 全局结构。实践中，这意味着我们不仅可以将两个在低维空间中靠近的案例解释为在高维空间中相似，还可以将两个 *clusters* 中靠近的案例解释为在高维空间中更相似。" Need to keep *and* and *clusters* italic.

58. Blank line.

59. Translate: "So how does UMAP work? Well, UMAP assumes the data is distributed along a *manifold*. A manifold is an n-dimensional smooth geometric shape where, for every point on this manifold, there exists a small neighborhood around that point that looks like a flat, two-dimensional plane. If that doesn’t make sense to you, consider that the world is a three-dimensional *manifold*, any part of which can be mapped into a flat representation, literally called a map. So UMAP searches for a surface, or a higher-dimensional space that the data are distributed along. The distances between cases *along the manifold* can then be calculated, and a lower-dimensional representation of the data can be optimized iteratively to reproduce these distances."

Translate: "那么 UMAP 如何工作呢？ well，UMAP 假设数据分布在 *manifold* 上。多重体是 n 维的光滑几何形状，对于多重体上的每一点，都存在一个小邻域，该邻域看起来像平面的二维平面。如果这对您来说不太好理解，可以考虑世界是三维的 *manifold*，其任何部分都可以映射到平面表示，字面上称为地图。因此，UMAP 寻找一个表面，或数据分布的更高维空间。然后可以计算案例 *along the manifold* 的距离，并通过迭代优化 lower-dimensional 表示来复制这些距离。" Need to keep *manifold* and *along the manifold* italic.

60. Blank line.

61. Translate: "Prefer a visual representation? Me too. Have a look at figure 14.8. I’ve drawn a question mark as a manifold, and randomly seeded 15 cases around the manifold across two variables. UMAP’s job is to learn the question mark manifold, so that it can measure the distances between cases along the manifold, instead of ordinary Euclidean distance, like t-SNE does. It achieves this by searching a region around each case, for another case. Where these regions encapsulate another case, the cases get connected by an edge. This is what I’ve done in the top row of figure 14.8, but can you see that the manifold is incomplete? There are gaps in my question mark. This is because the regions we searched around each case had the same radius, and the data wasn’t uniformly distributed along the manifold. If the cases were spaced out along the question mark at regular intervals, then this approach would have worked provided I selected an appropriate radius for the search regions."

Translate: "如果您更喜欢视觉呈现，我也如此。请查看图 14.8。我把一个问号作为多重体绘制，并在两个变量之间随机种下 15 个案例。UMAP 的任务是学习问号多重体，以便它能够测量案例 *along the manifold* 的距离，而不是像 t-SNE 那样使用普通欧几里得距离。它通过在每个案例周围搜索一个区域，寻找另一个案例。当这些区域包围另一个案例时，案例会通过边连接在一起。这是我在图 14.8 的上方行中所做的，但您能看到多重体是不完整的吗？我的问号上有缺口。这是因为我们在每个案例周围搜索的区域半径相同，而数据在多重体上并不均匀分布。如果案例在问号上以均匀间隔分布，那么在选择合适的搜索区域半径后，这种方法就会成功。"

62. Blank line.

63. Translate: "Real-world data are rarely evenly distributed, and so UMAP solves this problem in two ways. Firstly, it expands out each search region for each case until it meets its nearest neighbor. This ensures that there are no orphan cases: while there can be multiple, disconnected manifolds in a dataset, every case must connect to at least one other case. Secondly, UMAP creates an additional search region which has a larger radius in low-density areas, and a smaller radius in high-density regions. These search regions are described as \"fuzzy\", in that the further from the center another case finds itself, the lower the probability that an edge exists between those cases."

Translate: "现实世界的数据很少是均匀分布的，因此 UMAP 通过两种方式解决这个问题。首先，它会扩展每个案例的搜索区域，直到它与最近的邻居相遇。这确保了没有孤立的案例：虽然数据集中可能存在多个不相连的多重体，但每个案例都必须与至少一个其他案例相连。其次，UMAP 创建一个额外的搜索区域，在低密度区域具有更大的半径，在高密度区域具有更小的半径。这些搜索区域被描述为 \"模糊\"，即离中心更远时，另一个案例发现自己所在的概率越低，两个案例之间存在边的可能性也越低。"

Now we need to ensure we keep blank lines exactly as original. Let's verify the sequence of blank lines after each paragraph.

Original after figure caption (line 3) there is a blank line (line 4). Then the long paragraph (line 5). Then blank line (line 6). Then heading (line 7). Then blank line (line 8). Then code block (lines 9-12). Then blank line (line 13). Then TIP line (line 14). Then blank line (line 15). Then paragraph (line 16). Then blank line (line 17). Then next paragraph (line 18). Then blank line (line 19). Then next paragraph (line 20). Then blank line (line 21). Then code block (lines 24-33). Then blank line (line 34). Then paragraph (line 35). Then blank line (line 36). Then "### IMPORTANT" (line 37). Then blank line (line 38). Then paragraph (line 39). Then blank line (line 40). Then image (line 40? Actually image line 40). Then blank line (line 41). Then figure caption (line 42). Then blank line (line 43). Then paragraph (line 44). Then blank line (line 45). Then UMAP intro paragraph (line 46). Then blank line (line 47). Then first benefit paragraph (line 48). Then blank line (line 49). Then second benefit paragraph (line 50). Then blank line (line 51). Then third benefit paragraph (line 52). Then blank line (line 53). Then "So how does UMAP work?" paragraph (line 54). Then blank line (line 55). Then visual representation paragraph (line 56). Then blank line (line 57). Then real-world data paragraph (line 58).

We need to ensure we keep blank lines accordingly.

Now we need to produce final output with [content]...