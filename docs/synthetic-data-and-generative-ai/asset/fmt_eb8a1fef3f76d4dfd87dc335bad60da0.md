
The interactive spreadsheet named `HDTdata4Excel.xlsx` is on my GitHub repository, [here](https://github.com/VincentGranville/Machine-Learning/blob/main/Spreadsheets/HDTdata4Excel.xlsx). It uses a subset of 9 binary features. The first three are respectively “published after 2014”, “article is a forum discussion”, and “article is a blog post”. The next six are indicators of whether or not the title contains a specific character string. The six strings in question are `python`, `r`, `machine learning`, `data science`, `data`, and `analy`. The last string captures words such as “analytic” or “analyst”. These strings must be surrounded by spaces, so `r` clearly represents the R programming language. True/false are encoded as 1 and 0, respectively.

For instance, node `N-001-001110` in [Table 2.2](#Chp002_35-47_B9780443218576000060.xhtml#t0015) corresponds to blog posts published in 2014, containing the keywords “machine learning”, “data science”, and “data” in the title, but not “python”, “r”, or “analy”. The column `size` tells us that the node in question has only one article.

Table 2.2: Statistics for selected HDT nodes (Excel version).

| node | size | pv | index |
| --- | --- | --- | --- |
| N-000-000000 | 8 | 7.12 | 1.33 |
| N-000-000001 | 5 | 6.87 | 1.04 |
| N-000-000010 | 8 | 6.86 | 1.02 |
| N-000-000011 | 3 | 6.49 | 0.71 |
| N-000-000110 | 3 | 7.18 | 1.42 |
| N-001-000000 | 313 | 6.88 | 1.05 |
| N-001-000001 | 75 | 6.71 | 0.88 |
| N-001-000010 | 276 | 7.14 | 1.35 |
| N-001-000011 | 44 | 7.16 | 1.38 |
| N-001-000110 | 130 | 7.68 | 2.34 |
| N-001-000111 | 5 | 8.05 | 3.37 |
| N-001-001000 | 5 | 8.07 | 3.45 |
| N-001-001010 | 1 | 7.58 | 2.11 |
| N-001-001110 | 1 | 7.35 | 1.67 |

![Image](images/B9780443218576000060/t0015.png)

Nodes with fewer than 10 articles are classified using the regression method via the `LINEST()` Excel function, rather than the mini decision trees. Instead of standard regression, you can use a simplified logistic regression, as described in Section [1.3.1](#Chp001_1-34_B9780443218576000059.xhtml). There are ![Image](images/B9780443218576000060/fx006.jpg) observations (articles) and 74 nodes in the training set. By grouping all nodes with less than 10 observations into one node, we get down to 24 nodes. Correlations between individual features and the response `p` (logarithm of pageviews, denoted as `pv` in [Table 2.2](#Chp002_35-47_B9780443218576000060.xhtml#t0015)) is very low. Thus individual features have no predictive power. They must be combined together to gain predictive power. The full HDT method is superior to either the mini decision trees, or the regression model taken separately.

The `index` in [Table 2.2](#Chp002_35-47_B9780443218576000060.xhtml#t0015) is the `pv` of the node in question, divided by the average `pv` across all nodes. It measures the performance of the node. Finally, an article is classified as good or bad depending on whether its `index` is significantly larger or lower than one. The thresholds are user-defined. (See [Fig. 2.1](#Chp002_35-47_B9780443218576000060.xhtml#f0020).)

![Figure 2.1 Output from the Excel version of HDT.](images/B9780443218576000060/gr001.jpg)

[Figure 2.1](#Chp002_35-47_B9780443218576000060.xhtml#cf0070) Output from the Excel version of HDT.

### 2.3.3 Python code and dataset

The input dataset `HDTdata4.txt` is on my GitHub repository, [here](https://github.com/VincentGranville/Machine-Learning/blob/main/Source%20Code/HDTdata4.txt). The Python program `HDT.py` is listed below and can also be found on my GitHub repository, [here](https://github.com/VincentGranville/Machine-Learning/blob/main/Source%20Code/HDT.py). The output file `hdt-out2.txt` contains the usable key–value pairs (nodes) corresponding to popular articles, and the list of article IDs for each of these nodes. Finally, the variable `pv` represents `p`, the logarithm of the pageview count. The bivariate combinations (title keyword, article category) constitute the keys of the hash table `list_pv`, while the `pv` are the hash table values. Keywords are either one- or two-token. For one-token keywords, the second token is marked as `N/A`. In short, keyword is a bivariate entity.

As for the error rate, since the focus is on producing good articles, I am interested only in minimizing the number of bad articles flagged as good: the false positives. To reduce error rates or the proportion of unclassified nodes, use more features (for instance, more of those listed in [Table 2.1](#Chp002_35-47_B9780443218576000060.xhtml#t0010)), three-token keywords, a larger training set, a better keyword cleaning mechanism, and fine-tune the parameters.

Of course, if you choose the option `mode='perfect_fit'` in the program, your false positive rate drops to 0% on the training set, but doing may lower the performance on the validation set, and may leave many nodes unclassified. On the plus side, you have much fewer parameters to fine-tune: `pv_threshold_good`, `pv_threshold_bad`, and the minimum size of a usable node (the variable `n` in the code). The first two can be set respectively to 5% above and 10% below the global average `pv`. The minimum node size should be set above 2, and ideally above 5, though a large value results in more unclassified nodes. For `mode='robust method'`, the parameters in the conditional statements defining `good_node` and `bad_node` were set manually based on an average `pv` of 6.83. These choices can be automated.

In the end, unclassified nodes are classified via regression in the spreadsheet (see Section [2.3.2](#Chp002_35-47_B9780443218576000060.xhtml#s0055)), but this has not yet been implemented in the Python code. But for my purpose (identifying what makes an article good), I did not need to add the regression part, as the mini decision trees alone (the nodes) provide enough valuable insights.

![](images/B9780443218576000060/gr002.jpg)

## 2.4 Model-free confidence intervals and perfect nodes

Node `N-100-000000` in the spreadsheet has an average `pv` of 5.85. It consists of 10 articles with the following `pv`: 5.10, 5.10, 5.56, 5.56, 5.66, 5.69, 6.01, 6.19, 6.80, 6.80![Image](images/B9780443218576000060/si8.png). The 15th and 85th percentiles are 5.26 and 6.68, respectively, when computed with the `Percentile()` function in Excel. Thus, `[5.26, 6.68]`![Image](images/B9780443218576000060/si9.png) is a 70% **confidence interval** (CI) for `pv`, for the node in question.

The whole CI including its upper bound is below the average `pv` of 6.83. In fact this node corresponds to articles posted after 2014, not a blog or forum question (it could be a video or event announcement), and with a title containing none of the keyword features in the spreadsheet (columns K:P in the data tab). This node has a maximum predictive power, in the sense that 100% of the articles that it contains are bad, and 0% are good. This would also be true if it was the other way around, with Good swapped with Bad. Such a node is called a **perfect node**. When selecting the option `mode='Perfect fit'` in the Python code, the method looks at perfect nodes only. The concept of **predictive power** is further discussed in Section [18.4.2](#Chp018_361-386_B9780443218576000229.xhtml).

### 2.4.1 Interesting asymptotic properties of confidence intervals

I focus here on traditional model-free confidence intervals, as computed in the above paragraphs. The reader should be aware that there are other ways to define them, for instance, **credible intervals** in the context of **Bayesian inference** [[Wiki](https://en.wikipedia.org/wiki/Bayesian_inference)], or Bayesian-like **dual confidence intervals** as in Section [18.3](#Chp018_361-386_B9780443218576000229.xhtml).
