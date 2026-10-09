
![](img/315929ad4bddd26368466d02e06e2385_316_0.png)
![](img/315929ad4bddd26368466d02e06e2385_316_1.png)

FIGURE 7.22: OOS prediction results for (left) PLS as a function of $K$ and (right) lasso as a function of $\lambda$.

1. $K$-means is only one way to fit mixture models. One big improvement can come by accounting for uncertainty about each $k_{i}$ when updating the $\boldsymbol{\hat{\mu}}_{k}$ centers; this leads to the EM (expectation-maximization) algorithm.
2. Even though $K$ nearest neighbors and $K$-means have similar names, they have almost nothing to do with each other beyond the fact that both require careful scaling of inputs.
3. You can use $\boldsymbol{\hat{\mu}}_{k} = n_{i}/n$ to estimate the mixture component weights.
4. K. Rieder and L. Wasserman. Practical Bayesian density estimation using mixtures of normals. *Journal of the American Statistical Association*, **92**: 894-902, 1997.
5. The geographic pattern in **Figure 7.7** is striking, but these first two factors only explain $0.45\%$ of the original genetic variation. Don't be misled into overemphasizing the importance of geography on genes.
6. If you are familiar with linear algebra, $\phi_{1}$ is solvable as the first $eigenvector$ of the covariance matrix $X^{T}X$. Since arbitrary shifts and scales of $v_{i}$ will give the same $R_{i}$ after adjustment to $\phi_{j}$, we add the restriction $\sum_{j}^{I} \phi_{j}^{2} = 1$ to nail down scale.
7. If you work through the details, this definition for $v_{k}$ will be a shifted and rescaled version of the PC scores implied by the algorithms we've described elsewhere. Since the $v$'s are latent and have no inherent units, these definitions are all essentially equivalent.
8. Keith T. Poole. *Spatial Models of Parliamentary Voting*. Cambridge University Press, New York, 2005.
9. In social science, PCR is sometimes preferred when the PCA factors have clear interpretation (e.g., as in the roll-call votes example). In these cases, PCR will lead to results that are easier to communicate than those from a raw lasso regression. However, be careful: social scientists are great at interpreting factors where they don't exist.
10. Both AICc curves are unstable here and bounce around across K or $\lambda$ values. This will happen with small data samples, even when using generally stable techniques like the lasso.
11. Eric Bair, Trevor Hastie, Paul Debashis, and Robert Tibshirani. Prediction by supervised principal components. *Journal of the American Statistical Association*, 101:119–137, 2006.
12. H. Wold. Soft modeling by latent variables: The nonlinear iterative partial least squares approach. In *Perspectives in Probability and Statistics, Papers in Honour of MS Bartlett*. Academic Press, 1975.
13. Jerome H. Friedman. Greedy function approximation: a gradient boosting machine. *Annals of Statistics*, pages 1189–1232, 2001.

![](img/315929ad4bddd26368466d02e06e2385_318_0.png)

## Text as Data

The modern business environment generates vast quantities of raw unstructured text. As the costs of storage drop and as more conversations and records move to digital platforms, we accumulate massive corpora that track communications, including customer conversations, product descriptions or reviews, news, comments, blogs, and tweets. For business decision-makers, this provides an opportunity to dive into customer relationships and understand marketplaces. The information in text is a rich complement to the more structured variables contained in a traditional transaction or customer database.

Social scientists have also woken up to the potential of such data and recent years have seen an explosion in studies that make use of text as data. See Gentzkow et al. [2017] for an overview. In finance, text from financial news, social media, and company filings is used to predict asset price movements and study the causal impact of new information. In macroeconomics, text is used to forecast variation in inflation and unemployment and estimate the effects of policy uncertainty. In media economics, text from news and social media is used to study the drivers and effects of political slant. In marketing, text from advertisements and product reviews is used to study consumer decision-making. In the political economy, text from politicians' speeches is used to study the dynamics of political agendas and debate.

To analyze text, you need to transform it into data that can be input to numeric regression and factorization algorithms. This is almost always done by mapping from the raw text to counts of words or phrases. We will begin this chapter by outlining the process of *tokenization*, results of which are (very) high-dimensional *x* matrices. These text matrices can be incorporated into your analyses via methods we’ve already covered in this book (e.g., via lasso regression). Indeed, working with text data is a great way to get more familiar with modern statistical learning techniques. It is messy but also interpretable (words have known meanings) and is high dimensional in a way that stumps classical statisticians: as you accumulate more text data, the size of the vocabulary—your model dimension—will also grow. You are never in the statistician’s safe space of having many more observations than variables.

We will also cover a number of text-specific techniques, including topic modeling and multinomial inverse regression. However, the main message of this chapter is that with some standard data science tools you can tap into the information contained in messy unstructured text and use text as data in your business decisions.

### TOKENIZATION

Raw text—the language that humans read—is an incredibly rich object. It is much more than a sum of words. Meaning is built from ordered *sequences* of words that refer to each other, often separated across sentences or paragraphs. However, the vast majority of text analyses will ignore this complexity and rely solely on *counts* for language *tokens*: words, phrases, or other basic elements. Fortunately, a huge amount of information is contained in these simple counts. The lesson of the past 30 years has been that, for prediction and classification with text, it is difficult to make effective use of any statistics other than simple word counts. This is quickly changing with the commoditization of deep learning techniques (see **Chapter 10**). However, for data science and business analytics the bulk of text-as-data applications will continue to incorporate word and phrase counts for the foreseeable future—token-based learning is just too fast and effective to be made redundant, especially when you don’t have a huge number of documents to train against.

Consider a little Shakespeare:

> *All the world’s a stage,*  
> *and all the men and women merely players;*  
> *they have their exits and their entrances,*  
> *and one man in his time plays many parts . . .*

Powerful and poetic. What the data scientist sees is more pedestrian. For example, we might just count some key terms and represent the snippet as a numeric vector $x$:

| world | stage | men | women | play | exit | entrance | time |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 1 | 1 | 2 | 1 | 2 | 1 | 1 | 1 |

This is the *bag-of-words* representation of text. More precisely, the bag-of-words representation treats documents as if they were constructed by randomly drawing words with-replacement from a bucket containing the fixed vocabulary. By summarizing a document in terms of word counts, we are throwing away all information relevant to any more complex processes of document construction. The advantage of this approach is its simplicity: you can characterize relationships between language and outside variables (e.g., authorship or sentiment) by building a model for word probabilities.

There are many possible algorithms for going from raw text to a summary token-count vector $x$. A basic recipe first removes the following:

- Overly common or rare words
- Isolated punctuation (but not `:-)`) and numbers
- Common suffixes like $s$ or $ing$

You then count the remaining tokens (words or other elements separated by whitespace). The reason for doing the pruning before counting is computational and statistical efficiency: you want to only store and model the tokens that are important for the task at hand.

You should strive for a light touch in each of these steps. Since you're going to be using regularization and selection techniques in your text models, you don't need to be overly worried about including too many tokens. Words that are junk for one purpose might be crucial for another. For example, overly common words like $if$ or $but$ are called *stop words*; the frequency of $the$ in a document likely says little about the author's sentiment, so in many applications it can be dropped. However, in other applications these common words can indicate a specific author's writing style. The classic work of Mosteller and Wallace [1963] uses counts for common words to classify authorship for disputed federalist papers.² Similarly, punctuation is probably fine for removal when analyzing news articles or literature, but it provides important signals on meaning and sentiment in online corpora such as Twitter: `:-)`.

Exclusion of rare words is a necessary evil—these words are likely rich in meaning (they are rare and hence not generic) but you observe so few of them
