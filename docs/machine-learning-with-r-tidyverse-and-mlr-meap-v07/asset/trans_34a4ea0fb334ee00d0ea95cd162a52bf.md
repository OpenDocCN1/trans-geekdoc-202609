...[/content]. Must follow rules: bold and italic need translation and keep symbols. Inline code and code blocks unchanged. Links: translate content but keep URL. List, tables, quotes keep format, translate content. Ensure no duplicate original text. Also need to keep any list items etc.

We need to translate the whole content, including code blocks (they remain unchanged). Also need to translate the note about "NOTE" and "TIP" and "WARNING". Those are text, need translation but keep symbols like **NOTE**? In original they are bold? Actually they appear as **NOTE** and **TIP** and **WARNING** with bold. The rule: bold (**bold**) need translation and retain symbols. So we need to translate "NOTE" to Chinese but keep **...**? The example: "**Richard Feynman**" becomes "**Richard Feynman**"? Actually in example they translated "Richard Feynman" but kept the bold markup? Let's see: Example original: "is inspired by **Richard Feynman**, the Nobel Prize winner in physics." The translation: "的灵感源于诺贝尔物理奖获得者**理查德·费曼**。" They kept the bold markup around the name, and translated the name itself. So we need to translate the content inside bold, but keep the ** symbols. Similarly *italic* need translation and keep symbols.

Also inline code `20 min` remains unchanged. Code block unchanged.

List items: need to translate the text but keep list markers.

We need to be careful to not miss any lines. The content includes multiple paragraphs, code blocks, list items (the NOTE, TIP, WARNING). Also need to keep the "###" headings? Not present. The content includes "### Listing 17.2 Defining the cluster_metrics function" etc. Those are headings; we need to translate them? The rule says list, tables, quote blocks keep format, translate content. Headings are not list but they are part of text; we should translate them as well, preserving markdown heading syntax. So "### Listing 17.2 Defining the cluster_metrics function" -> "### 17.2 定义 cluster_metrics 函数". But need to keep "###". Also "### Listing 17.3 Creating bootstrap samples" -> "### 17.3 创建 bootstrap 样本". Also "### Listing 17.4" maybe not present but we have "### Listing 17.4" not shown but maybe later. In the given text there is "### Listing 17.2 Defining the cluster_metrics function" and "### Listing 17.3 Creating bootstrap samples". Also there is "### NOTE" etc. The "NOTE" is bold, so we need to translate "NOTE" to Chinese but keep **NOTE**? Actually it's **NOTE** in the text. The rule: bold need translation and retain symbols. So we need to translate "NOTE" to Chinese "注意" but keep the **...**? In example they kept **Richard Feynman** as **Richard Feynman**? Wait they kept the bold markup but translated the name. So for **NOTE**, we need to translate "NOTE" to Chinese, but keep the **...**? The original text: "**NOTE** Remember that `~` is just shorthand for `function()`." So we need to translate "NOTE" to Chinese, but keep the **...**? The rule: "粗体（**bold**）和斜体（*itatic*）需要翻译翻译内容并保留符号。" Means the content inside bold/italic should be translated, and keep the symbols. So **NOTE** => **注意**? But that would be **注意** which includes the symbols. However the original had **NOTE** (the word NOTE in bold). So we translate "NOTE" to "注意", resulting in **注意**. That seems right.

Similarly **TIP** => **提示**, **WARNING** => **警告**.

Also need to translate "map()" etc? Those are function names, code, keep unchanged.

Also need to translate "map_df()" etc.

Also need to translate "sample_n()" etc.

Also need to translate "the mean of our bootstrapped statistic(s) tells us the most likely value" etc.

We must ensure we don't miss any line. Let's go through the content line by line.

Original text:

"In this section, I’ll show you ways of deciding how many clusters to extract from our hierarchy. Another way of thinking about this is that we’re deciding what level of the hierarchy to use for clustering."

We need to translate.

"To define a finite number of clusters following hierarchical clustering, we need to define a cut point on our dendrogram. If we cut the tree near the top, we’ll get fewer clusters, and if we cut the tree near the bottom, we’ll get more clusters. So how do we choose a cut point? Well, our friends the Davies-Bouldin index, the Dunn index, and the pseudo F statistic can help us here. For k-means clustering, we performed a cross-validation-like procedure for estimating the performance of different numbers of clusters. Sadly, we can’t use this approach for hierarchical clustering because unlike k-means, hierarchical clustering cannot predict cluster membership of new cases."

Then a blockquote:

"> The hierarchical clustering algorithms themselves can’t predict the cluster membership of new cases, but you could do something like assign new data to the cluster with the nearest centroid. You could use this approach to create separate training and test sets to evaluate internal cluster metrics on."

Then another blockquote:

"> Remember that a bootstrap sample is where we randomly select cases from a dataset with replacement, to create a new sample the same size as the old. Sampling "with replacement" simply means that once we sample a particular case, we put it back again, such that there is a possibility it will be drawn again."

Then:

"In the context of hierarchical clustering, we can use bootstrapping to generate multiple samples from our data, and generate a separate hierarchy for each sample. We can then select a range of cluster numbers from each hierarchy, and calculate the internal cluster metrics for each. The advantage of using bootstrapping is that calculating the internal cluster metrics on the full dataset doesn’t give us an indication as to the stability of the estimate, whereas the bootstrap sample does. The bootstrap sample of cluster metrics will have some variation around its mean, and so we can choose the number of clusters with the most optimal and stable metrics."

Then:

"Let’s start by defining our own function that takes our data and a vector of cluster memberships, and returns our three familiar internal cluster metrics for the data: the Davies-Bouldin index, the Dunn index, and the pseudo F statistic. As the function we’ll use to calculate the Dunn index expects a distance matrix, we’ll include an additional argument in our function to supply a pre-computed distance matrix too."

"Take a look at the function body in code listing 17.2 and follow it through with me so what we’re doing makes sense. I use the `function()` function to define a function, assigning it to the name `cluster_metrics` (this will allow us to call the function using `cluster_metrics()`). I define three mandatory arguments for the function:"

"- `data`, to which we will pass the data we’re clustering"

"- `clusters`, a vector containing the cluster membership of every case in `data`"

"- `dist_matrix`, to which we will pass the pre-computed distance matrix for `data`"

"The *body* of the function (the instructions that tell the function what to do) is defined inside curly brackets (`{}`). Our function will return a list with four elements, the Davies-Bouldin index (`db`), the pseudo F statistic (`G1`), the Dunn index (`dunn`), and the number of clusters. Rather than define them from scratch, I’m using pre-defined functions from other packages to compute the internal cluster metrics. The Davies-Bouldin index is computed using the `index.DB()` function from the clusterSim package, which takes the `data` and `clusters` arguments (the statistic itself is contained in the `$DB` component). The pseudo F statistic is computed using the `index.G1()` function, also from the clusterSim package, and takes the same arguments as `index.DB()`. The Dunn index is computed using the `dunn()` function from the clValid package, which takes the `dist_matrix` and `clusters` arguments."

"Our motivation for defining this function is that we’re going to take bootstrap samples from our dataset, learn the hierarchy in each, select a range of cluster numbers from each, and use our function to calculate these three metrics for each number of clusters, within each bootstrap sample."

Then a code listing:

```r
cluster_metrics <- function(data, clusters, dist_matrix) {
    list(db       = clusterSim::index.DB(data, clusters)$DB,
         G1       = clusterSim::index.G1(data, clusters),
         dunn     = clValid::dunn(dist_matrix, clusters),
         clusters = length(unique(clusters))
    )
}
```

Then:

"So now, let’s create our bootstrap samples. We’re going to create ten bootstrap samples from our gvhdScaled dataset. I’m using the `map()` function to repeat the sampling process ten times, to return a list where each element is a different bootstrap sample."

"> **NOTE** Remember that `~` is just shorthand for `function()`."

"We’re using the `sample_n()` function from the dplyr package to create our samples. This function randomly samples rows from a dataset. As this function cannot handle matrices, we first need to pipe our gvhdScaled data into the `as_tibble()` function. By setting the argument `size = nrow(.)`, we’re asking the `sample_n()` function to randomly draw a number of cases, equal to the number of rows in the original dataset (the `.` is shorthand for "the dataset that was piped in"). By setting the `replace` argument equal to `TRUE`, we’re telling the function to sample with replacement. Creating simple bootstrap samples really is as easy as this!"

Then code listing:

```r
gvhdBoot <- map(1:10, ~ {
  gvhdScaled %>%
    as_tibble() %>%
    sample_n(size = nrow(.), replace = TRUE)
})
```

Then:

"Now, let’s use our `cluster_metrics()` function to calculate those three internal metrics for a range of cluster numbers, for each bootstrap sample we just generated. Take a look at code listing 17.4 and don’t go cross-eyed! I’m going to take you through the code step-by-step. I start by calling the `map_df()` function, so that we can apply a function to every element of our list of bootstrap samples. I define an anonymous function, which takes boot (the current element being considered) as its only argument."

"> **TIP** The `map_df()` function is just like `map()`, but instead of returning a list, it will combine each element together row-wise to return a data frame instead."

"For each element in `gvhdBoot`, the anonymous function computes its Euclidean distance matrix and stores it as the object `d`, and performs hierarchical clustering using that matrix and Ward’s method. Once we have the hierarchy for each bootstrap sample, we then use another `map_df()` function call to select between three and eight clusters to partition the data into, and calculate the three internal clustering metrics on each result. We’re going to use this process to see which number of clusters, between three and eight, gives us the best internal cluster metric values."

"Selecting the number of clusters to retain from a hierarchical clustering model is done using the `cutree()` function. We use this function to cut our dendrogram at a place that returns a number of clusters. We can do this either by specifying a height at which to cut, using the `h` argument, or by specifying a specific number of clusters to retain, using the `k` argument (as done here). The first argument is the result of calling the `hclust()` function. The output of the `cutree()` function is a vector indicating the cluster number assigned to each case in the dataset. Once we have this vector, we can call our `cluster_metrics()` function, supplying the bootstrap data, the vector of cluster membership, and the distance matrix."

"> **WARNING** This took nearly three minutes to run on my machine!"

Now we need to translate all that, preserving formatting.

We need to wrap everything inside [content]...[/content].

Let's produce translation.

We need to keep code blocks unchanged.

We need to translate list items (the bullet points) and the note, tip, warning.

Also need to translate the headings "### Listing 17.2 Defining the cluster_metrics function" and "### Listing 17.3 Creating bootstrap samples". Also maybe "### Listing 17.4" not present.

Also need to translate "map_df()" etc but keep code unchanged.

Also need to translate "sample_n()" etc but keep code unchanged.

Also need to translate "the mean of our bootstrapped statistic(s) tells us the most likely value" etc.

Let's translate.

I'll go step by step.

First paragraph:

"In this section, I’ll show you ways of deciding how many clusters to extract from our hierarchy. Another way of thinking about this is that we’re deciding what level of the hierarchy to use for clustering."

Translate: "在本节中，我将向您展示如何从我们的层级结构中提取集群的数量。另一种思考方式是，我们决定使用层级结构的哪个层级进行聚类。"

Second paragraph:

"To define a finite number of clusters following hierarchical clustering, we need to define a cut point on our dendrogram. If we cut the tree near the top, we’ll get fewer clusters, and if we cut the tree near the bottom, we’ll get more clusters. So how do we choose a cut point? Well, our friends the Davies-Bouldin index, the Dunn index, and the pseudo F statistic can help us here. For k-means clustering, we performed a cross-validation-like procedure for estimating the performance of different numbers of clusters. Sadly, we can’t use this approach for hierarchical clustering because unlike k-means, hierarchical clustering cannot predict cluster membership of new cases."

Translate:

"要在层级聚类后定义有限数量的集群，我们需要在我们的树状图（dendrogram）上定义一个切点。如果我们在树的上部切割，将得到较少的集群；如果在树的底部切割，将得到更多的集群。那么我们如何选择切点呢？ well，我们的朋友 Davies-Bouldin 指数、Dunn 指数和伪 F 统计量可以帮助我们。对于 k-means 聚类，我们进行了类似交叉验证的程序来估计不同数量集群的性能。遗憾的是，我们无法使用这种方法进行层级聚类，因为与 k-means 不同，层级聚类无法预测新案例的集群归属。"

Third blockquote:

"> The hierarchical clustering algorithms themselves can’t predict the cluster membership of new cases, but you could do something like assign new data to the cluster with the nearest centroid. You could use this approach to create separate training and test sets to evaluate internal cluster metrics on."

Translate:

"> 层级聚类算法本身无法预测新案例的集群归属，但您可以尝试将新数据分配到最近中心的集群中。您可以使用这种方法创建独立的训练集和测试集，以评估内部集群指标。"

Fourth blockquote:

"> Remember that a bootstrap sample is where we randomly select cases from a dataset with replacement, to create a new sample the same size as the old. Sampling "with replacement" simply means that once we sample a particular case, we put it back again, such that there is a possibility it will be drawn again."

Translate:

"> 请记住，bootstrap 样本是我们从数据集中有放回地随机选择案例，以创建与原始数据集大小相同的新样本。所谓“with replacement”（有放回）仅意味着一旦我们抽取某个案例后，我们会将其放回，从而有可能再次被抽取。"

Next paragraph:

"In the context of hierarchical clustering, we can use bootstrapping to generate multiple samples from our data, and generate a separate hierarchy for each sample. We can then select a range of cluster numbers from each hierarchy, and calculate the internal cluster metrics for each. The advantage of using bootstrapping is that calculating the internal cluster metrics on the full dataset doesn’t give us an indication as to the stability of the estimate, whereas the bootstrap sample does. The bootstrap sample of cluster metrics will have some variation around its mean, and so we can choose the number of clusters with the most optimal and stable metrics."

Translate:

"在层级聚类的语境下，我们可以使用 bootstrapping 来生成多个样本，并为每个样本生成单独的层级结构。我们可以从每个层级结构中选择一个范围的集群数量，并分别计算每个结果的内部集群指标。使用 bootstrapping 的优势在于，在完整数据集上计算内部集群指标并不能表明估计的稳定性，而 bootstrap 样本可以。bootstrap 样本中的集群指标会围绕其均值出现一些变异，因此我们可以选择具有最佳且最稳定指标的集群数量。"

Next paragraph:

"Let’s start by defining our own function that takes our data and a vector of cluster memberships, and returns our three familiar internal cluster metrics for the data: the Davies-Bouldin index, the Dunn index, and the pseudo F statistic. As the function we’ll use to calculate the Dunn index expects a distance matrix, we’ll include an additional argument in our function to supply a pre-computed distance matrix too."

Translate:

"让我们先定义一个自己的函数，它接受我们的数据和集群成员向量，并返回我们熟悉的三个内部集群指标：Davies-Bouldin 指数、Dunn 指数和伪 F 统计量。由于我们用于计算 Dunn 指数的函数期望一个距离矩阵，我们还会在函数中加入一个参数，用于提供已预先计算的距离矩阵。"

Next paragraph:

"Take a look at the function body in code listing 17.2 and follow it through with me so what we’re doing makes sense. I use the `function()` function to define a function, assigning it to the name `cluster_metrics` (this will allow us to call the function using `cluster_metrics()`). I define three mandatory arguments for the function:"

Translate:

"请查看代码列表 17.2 中的函数体，并跟随我一起理解我们在做什么，这样就能清楚其意义。我使用 `function()` 函数来定义函数，并将其命名为 `cluster_metrics`（这将使我们能够使用 `cluster_metrics()` 来调用该函数）。我为函数定义了三个必需参数："

Then list items:

"- `data`, to which we will pass the data we’re clustering"

"- `clusters`, a vector containing the cluster membership of every case in `data`"

"- `dist_matrix`, to which we will pass the pre-computed distance matrix for `data`"

Translate each:

"- `data`, 我们将把要聚类的数据传递给它"

"- `clusters`, 包含 `data` 中每个案例的集群归属的向量"

"- `dist_matrix`, 我们将把已预先计算的距离矩阵传递给它"

Next paragraph:

"The *body* of the function (the instructions that tell the function what to do) is defined inside curly brackets (`{}`). Our function will return a list with four elements, the Davies-Bouldin index (`db`), the pseudo F statistic (`G1`), the Dunn index (`dunn`), and the number of clusters. Rather than define them from scratch, I’m using pre-defined functions from other packages to compute the internal cluster metrics. The Davies-Bouldin index is computed using the `index.DB()` function from the clusterSim package, which takes the `data` and `clusters` arguments (the statistic itself is contained in the `$DB` component). The pseudo F statistic is computed using the `index.G1()` function, also from the clusterSim package, and takes the same arguments as `index.DB()`. The Dunn index is computed using the `dunn()` function from the clValid package, which takes the `dist_matrix` and `clusters` arguments."

Translate:

"函数的 *body*（即告诉函数要做什么的指令）定义在花括号 (`{}`) 内。我们的函数将返回["? Wait need to translate: "Our function will return a list with four elements, the Davies-Bouldin index (`db`), the pseudo F statistic (`G1`), the Dunn index (`dunn`), and the number of clusters." => "我们的函数将返回一个包含四个元素的列表，分别是 Davies-Bouldin 指数 (`db`)、伪 F 统计量 (`G1`)、Dunn 指数 (`dunn`) 以及集群数量。"

"Rather than define them from scratch, I’m using pre-defined functions from other packages to compute the internal cluster metrics." => "与从头定义它们不同，我使用了其他包中预定义的函数来计算内部集群指标。"

"The Davies-Bouldin index is computed using the `index.DB()` function from the clusterSim package, which takes the `data` and `clusters` arguments (the statistic itself is contained in the `$DB` component)." => "Davies-Bouldin 指数使用 clusterSim 包中的 `index.DB()` 函数计算，该函数接受 `data` 和 `clusters` 参数（统计量本身位于 `$DB` 组件中）。"

"The pseudo F statistic is computed using the `index.G1()` function, also from the clusterSim package, and takes the same arguments as `index.DB()`." => "伪 F 统计量使用 clusterSim 包中的 `index.G1()` 函数计算，同样接受 `index.DB()` 的参数。"

"The Dunn index is computed using the `dunn()` function from the clValid package, which takes the `dist_matrix` and `clusters` arguments." => "Dunn 指数使用 clValid 包中的 `dunn()` 函数计算，接受 `dist_matrix` 和 `clusters` 参数。"

Next paragraph:

"Our motivation for defining this function is that we’re going to take bootstrap samples from our dataset, learn the hierarchy in each, select a range of cluster numbers from each, and use our function to calculate these three metrics for each number of clusters, within each bootstrap sample."

Translate:

"定义该函数的动机是，我们将从数据集中抽取 bootstrap 样本，在每个样本上学习层级结构，从每个结构中选择一个集群数量范围，并使用我们的函数计算每个集群数量对应的这三个指标，在每个 bootstrap 样本内部。"

Now code listing 17.2:

```r
cluster_metrics <- function(data, clusters, dist_matrix) {
    list(db       = clusterSim::index.DB(data, clusters)$DB,
         G1       = clusterSim::index.G1(data, clusters),
         dunn     = clValid::dunn(dist_matrix, clusters),
         clusters = length(unique(clusters))
    )
}
```

We need to keep code unchanged.

Now next paragraph:

"So now, let’s create our bootstrap samples. We’re going to create ten bootstrap samples from our gvhdScaled dataset. I’m using the `map()` function to repeat the sampling process ten times, to return a list where each element is a different bootstrap sample."

Translate:

"现在，让我们创建我们的 bootstrap 样本。我们将从 gvhdScaled 数据集中创建十个 bootstrap 样本。我使用 `map()` 函数重复十次采样过程，返回一个列表，其中每个元素是一个不同的 bootstrap 样本。"

Next blockquote:

"> **NOTE** Remember that `~` is just shorthand for `function()`."

Translate:

"> **注意** 记住 `~` 只是 `function()` 的简写。"

Note: need to keep **...** and translate "NOTE" to "注意". So **注意**.

Next paragraph:

"We’re using the `sample_n()` function from the dplyr package to create our samples. This function randomly samples rows from a dataset. As this function cannot handle matrices, we first need to pipe our gvhdScaled data into the `as_tibble()` function. By setting the argument `size = nrow(.)`, we’re asking the `sample_n()` function to randomly draw a number of cases, equal to the number of rows in the original dataset (the `.` is shorthand for "the dataset that was piped in"). By setting the `replace` argument equal to `TRUE`, we’re telling the function to sample with replacement. Creating simple bootstrap samples really is as easy as this!"

Translate:

"我们使用 dplyr 包中的 `sample_n()` 函数来创建样本。该函数会从数据集中随机抽取行。由于该函数无法处理矩阵，我们首先需要将 gvhdScaled 数据通过 `as_tibble()` 函数管道化。通过设置 `size = nrow(.)` 参数，我们要求 `sample_n()` 函数随机抽取的案例数等于原始数据集的行数（`.` 代表被管道输入的数据集）。通过将 `replace` 参数设置为 `TRUE`，我们告诉函数进行有放回抽样。创建简单的 bootstrap 样本真的很简单！"

Now code listing 17.3:

```r
gvhdBoot <- map(1:10, ~ {
  gvhdScaled %>%
    as_tibble() %>%
    sample_n(size = nrow(.), replace = TRUE)
})
```

Keep unchanged.

Next paragraph:

"Now, let’s use our `cluster_metrics()` function to calculate those three internal metrics for a range of cluster numbers, for each bootstrap sample we just generated. Take a look at code listing 17.4 and don’t go cross-eyed! I’m going to take you through the code step-by-step. I start by calling the `map_df()` function, so that we can apply a function to every element of our list of bootstrap samples. I define an anonymous function, which takes boot (the current element being considered) as its only argument."

Translate:

"现在，让我们使用我们刚刚创建的 `cluster_metrics()` 函数，为我们刚刚生成的每个 bootstrap 样本计算这三个内部指标，针对不同的集群数量范围。请查看代码列表 17.4，别眨眼！我将逐步带您理解代码。我先调用 `map_df()` 函数，以便对我们列表中的每个 bootstrap 样本应用一个函数。我定义了一个匿名函数，它只接受 `boot`（当前被考虑的元素）作为参数。"

Next blockquote:

"> **TIP** The `map_df()` function is just like `map()`, but instead of returning a list, it will combine each element together row-wise to return a data frame instead."

Translate:

"> **提示** `map_df()` 函数类似于 `map()`，但它不会返回列表，而是会按行合并每个元素，生成一个数据框。"

Next paragraph:

"For each element in `gvhdBoot`, the anonymous function computes its Euclidean distance matrix and stores it as the object `d`, and performs hierarchical clustering using that matrix and Ward’s method. Once we have the hierarchy for each bootstrap sample, we then use another `map_df()` function call to select between three and eight clusters to partition the data into, and calculate the three internal clustering metrics on each result. We’re going to use this process to see which number of clusters, between three and eight, gives us the best internal cluster metric values."

Translate:

"对于 `gvhdBoot` 中的每个元素，匿名函数会计算其欧几里得距离矩阵并将其存储为对象 `d`，然后使用该矩阵和 Ward’s 方法进行层级聚类。一旦我们拥有每个 bootstrap 样本的层级结构，我们就会再次调用 `map_df()` 函数，选择三到八个集群来对数据进行分区，并在这些结果上计算三个内部聚类指标。我们将使用这个过程来找出在三到八个集群之间，哪个数量的集群能够提供最佳的内部聚类指标值。"

Next paragraph:

"Selecting the number of clusters to retain from a hierarchical clustering model is done using the `cutree()` function. We use this function to cut our dendrogram at a place that returns a number of clusters. We can do this either by specifying a height at which to cut, using the `h` argument, or by specifying a specific number of clusters to retain, using the `k` argument (as done here). The first argument is the result of calling the `hclust()` function. The output of the `cutree()` function is a vector indicating the cluster number assigned to each case in the dataset. Once we have this vector, we can call our `cluster_metrics()` function, supplying the bootstrap data, the vector of cluster membership, and the distance matrix."

Translate:

"从层级聚类模型中选择保留的集群数量是通过 `cutree()` 函数实现的。我们使用该函数在 dendrogram 上切割，以返回一个特定数量的集群。我们可以通过指定切割的高度（使用 `h` 参数）或指定要保留的集群数量（使用 `k` 参数，如在此所示）来实现。第一个参数是 `hclust()` 函数的结果。`cutree()` 函数的输出是一个指示数据集中每个案例所属集群编号的向量。一旦我们拥有这个向量，就可以将我们的 `cluster_metrics()` 函数传入 bootstrap 数据、集群成员向量以及距离矩阵。"

Next blockquote:

"> **WARNING** This took nearly three minutes to run on my machine!"

Translate:

"> **警告** 这在我机器上运行 nearly three minutes（大约三分钟）！"

Now we need to ensure we wrap everything in [content]...[/content].

We must be careful not to duplicate any original text. Also ensure we keep code blocks unchanged.

Let's construct the final translation.

We need to keep line breaks as in original. Let's replicate structure.

Original content after "## 注意事项" etc. The content starts with "In this section..." So we need to include all that.

We'll produce:

[content]
-   ... (list items) etc.

But the original text is not a list; it's paragraphs. However there are list items for arguments. We need to keep list formatting.

Let's write translation.

We'll start with the first paragraph (no list). Then the next paragraph (no list). Then blockquote lines (starting with >). Then the next paragraph. Then next paragraph. Then next paragraph. Then code listing. Then paragraph about bootstrap samples. Then blockquote note. Then paragraph about sample_n. Then code listing. Then paragraph about using cluster_metrics. Then blockquote tip. Then paragraph about selecting clusters. Then paragraph about cutree. Then blockquote warning.

We need to ensure we keep list items for arguments. The list items are preceded by "- " in original. We'll translate them accordingly.

Let's write:

[content]
在本节中，我将向您展示如何从我们的层级结构中提取集群的数量。另一种思考方式是，我们决定使用层级结构的哪个层级进行聚类。

要在层级聚类后定义有限数量的集群，我们需要在我们的树状图（dendrogram）上定义一个切点。如果我们在树的上部切割，将得到较少的集群；如果在树的底部切割，将得到更多的集群。那么我们如何选择切点呢？ well，我们的朋友 Davies-Bouldin 指数、Dunn 指数和伪 F 统计量可以帮助我们。对于 k-means 聚类，我们进行了类似交叉验证的程序来估计不同数量集群的性能。遗憾的是，我们无法使用这种方法进行层级聚类，因为与 k-means 不同，层级聚类无法预测新案例的集群归属。

> 层级聚类算法本身无法预测新案例的集群归属，但您可以尝试将新数据分配到最近中心的集群中。您可以使用这种方法创建独立的训练集和测试集，以评估内部集群指标。

> 请记住，bootstrap 样本是我们从数据集中有放回地随机选择案例，以创建与原始数据集大小相同的新样本。所谓“with replacement”（有放回）仅意味着一旦我们抽取某个案例后，我们会将其放回，从而有可能再次被抽取。

在层级聚类的语境下，我们可以使用 bootstrapping 来生成多个样本，并为每个样本生成单独的层级结构。我们可以从每个层级结构中选择一个范围的集群数量，并分别计算每个结果的内部集群指标。使用 bootstrapping 的优势在于，在完整数据集上计算内部集群指标并不能表明估计的稳定性，而 bootstrap 样本可以。bootstrap 样本中的集群指标会围绕其均值出现一些变异，因此我们可以选择具有最佳且最稳定指标的集群数量。

让我们先定义一个自己的函数，它接受我们的数据和集群成员向量，并返回我们熟悉的三个内部集群指标：Davies-Bouldin 指数、Dunn 指数和伪 F 统计量。由于我们用于计算 Dunn 指数的函数期望一个距离矩阵，我们还会在函数中加入一个参数，用于提供已预先计算的距离矩阵。

请查看代码列表 17.2 中的函数体，并跟随我一起理解我们在做什么，这样就能清楚其意义。我使用 `function()` 函数来定义函数，并将其命名为 `cluster_metrics`（这将使我们能够使用 `cluster_metrics()` 来调用该函数）。我为函数定义了三个必需参数：

- `data`, 我们将把要聚类的数据传递给它
- `clusters`, 包含 `data` 中每个案例的集群归属的向量
- `dist_matrix`, 我们将把已预先计算的距离矩阵传递给它

函数的 *body*（即告诉函数要做什么的指令）定义在花括号 (`{}`) 内。我们的函数将返回一个包含四个元素的列表，分别是 Davies-Bouldin 指数 (`db`)、伪 F 统计量 (`G1`)、Dunn 指数 (`dunn`) 以及集群数量。与从头定义它们不同，我使用了其他包中预定义的函数来计算内部集群指标。Davies-Bouldin 指数使用 clusterSim 包中的 `index.DB()` 函数计算，该函数接受 `data` 和 `clusters` 参数（统计量本身位于 `$DB` 组件中）。伪 F 统计量使用 clusterSim 包中的 `index.G1()` 函数计算，同样接受 `index.DB()` 的参数。Dunn 指数使用 clValid 包中的 `dunn()` 函数计算，接受 `dist_matrix` 和 `clusters` 参数。

定义该函数的动机是，我们将从数据集中抽取 bootstrap 样本，在每个样本上学习层级结构，从每个结构中选择一个集群数量范围，并使用我们的函数计算每个集群数量对应的这三个指标，在每个 bootstrap 样本内部。

```r
cluster_metrics <- function(data, clusters, dist_matrix) {
    list(db       = clusterSim::index.DB(data, clusters)$DB,
         G1       = clusterSim::index.G1(data, clusters),
         dunn     = clValid::dunn(dist_matrix, clusters),
         clusters = length(unique(clusters))
    )
}
```

现在，让我们创建我们的 bootstrap 样本。我们将从 gvhdScaled 数据集中创建十个 bootstrap 样本。我使用 `map()` 函数重复十次采样过程，返回一个列表，其中每个元素是一个不同的 bootstrap 样本。

> **注意** 记住 `~` 只是 `function()` 的简写。

我们使用 dplyr 包中的 `sample_n()` 函数来创建样本。该函数会从数据集中随机抽取行。由于该函数无法处理矩阵，我们首先需要将 gvhdScaled 数据通过 `as_tibble()` 函数管道化。通过设置 `size = nrow(.)` 参数，我们要求 `sample_n()` 函数随机抽取的案例数等于原始数据集的行数（`.` 代表被管道输入的数据集）。通过将 `replace` 参数设置为 `TRUE`，我们告诉函数进行有放回抽样。创建简单的 bootstrap 样本真的很简单！

```r
gvhdBoot <- map(1:10, ~ {
  gvhdScaled %>%
    as_tibble() %>%
    sample_n(size = nrow(.), replace = TRUE)
})
```

现在，让我们使用我们刚刚创建的 `cluster_metrics()` 函数，为我们刚刚生成的每个 bootstrap 样本计算这三个内部指标，针对不同的集群数量范围。请查看代码列表 17.4，别眨眼！我将逐步带您理解代码。我先调用 `map_df()` 函数，以便对我们列表中的每个 bootstrap 样本应用一个函数。我定义了一个匿名函数，它只接受 `boot`（当前被考虑的元素）作为参数。

> **提示** `map_df()` 函数类似于 `map()`，但它不会返回列表，而是会按行合并每个元素，生成一个数据框。

对于 `gvhdBoot` 中的每个元素，匿名函数会计算其欧几里得距离矩阵并将其存储为对象 `d`，然后使用该矩阵和 Ward’s 方法进行层级聚类。一旦我们拥有每个 bootstrap 样本的层级结构，我们就会再次调用 `map_df()` 函数，选择三到八个集群来对数据进行分区，并在这些结果上计算三个内部聚类指标。我们将使用这个过程来找出在三到八个集群之间，哪个数量的集群能够提供最佳的内部聚类指标值。

从层级聚类模型中选择保留的集群数量是通过 `cutree()` 函数实现的。我们使用该函数在 dendrogram 上切割，以返回一个特定数量的集群。我们可以通过指定切割的高度（使用 `h` 参数）或指定要保留的集群数量（使用 `k` 参数，如在此所示）来实现。第一个参数是 `hclust()` 函数的结果。`cutree()` 函数的输出是一个指示数据集中每个案例所属集群编号的向量。一旦我们拥有这个向量，就可以将我们的 `cluster_metrics()` 函数传入 bootstrap 数据、集群成员向量以及距离矩阵。

> **警告** 这在我机器上运行 nearly three minutes（大约三分钟）！

