
6.  [6](#c09.xhtml#R_c09-note-0006) The value of a fundamental asset may not necessarily refer to its quoting price or net worth, it can stand for income generated regularly by consuming this fundamental asset.

7.  [7](#c09.xhtml#R_c09-note-0007) The dataset can be readily downloaded from [`https://www.kaggle.com/datasets/kasikrit/att-database-of-faces`](https://www.kaggle.com/datasets/kasikrit/att-database-of-faces).

8.  [8](#c09.xhtml#R_c09-note-0008) The loadings of the first PC generated from Python have the opposite sign to those generated in `R`, so the basket of 10 stocks with the smallest loadings and the basket of 10 stocks with the largest loadings are interchanged in Python and `R`. PCA can extract the factors, while the extraction itself does not take the orientation and direction into account.

9.  [9](#c09.xhtml#R_c09-note-0009) Also see `Stock Market Analytics with PCA`. Retrieved from [`https://web.archive.org/web/20210304165314/https://towardsdatascience.com/stock-market-analytics-with-pca-d1c2318e3f0e?gi=da1a691e72b`](https://web.archive.org/web/20210304165314/https://towardsdatascience.com/stock-market-analytics-with-pca-d1c2318e3f0e?gi=da1a691e72b).

10.  [10](#c09.xhtml#R_c09-note-0010) As a remark, since the loading of the first PC changes with time, often the expression of the PC now is different from that obtained in the past. To put it in real practice, a close real‐time monitoring is required to see if there is any substantial shift in the nature of the first few PCs.

11.  [11](#c09.xhtml#R_c09-note-0011) Source: [`https://www.futuhk.com/en/commissionnew`](https://www.futuhk.com/en/commissionnew).

12.  [12](#c09.xhtml#R_c09-note-0012) Most of the entries are zero as there are too many good movies missed due to limited time! Usually only about 1% of all entries are non‐zero.

13.  [13](#c09.xhtml#R_c09-note-0013) While `Netflix` makes use of collaborative filtering, `Amazon` adopts `content‐based filtering` based on purchase and browsing history.

14.  [14](#c09.xhtml#R_c09-note-0014) Typical numbers for `p` for the `Netflix Prize` ranged from 10 to 200.

15.  [15](#c09.xhtml#R_c09-note-0015) Note that the range of entries in `P` and `Q` need not be the same as that for the entries of `R`.

16.  [16](#c09.xhtml#R_c09-note-0016) In practice, the `multipliers` `Λ1` and `Λ2` are chosen in advance and are often selected via `cross‐validation`, where the available data are divided into `M` parts. Particularly, in the `i`‐th round of cross‐validation, all parts except the `i`‐th one out of these `M` portions serve as the training data, while the `i`‐th part is used for testing.

17.  [17](#c09.xhtml#R_c09-note-0017) Note that `p` is often chosen so that the product `(m + n + p) × p` is about the same as the number of entries in the large and sparse data matrix `A`.

# CHAPTER 10

Regression Learning

`Regression Learning` (a.k.a. `Regression Analysis`) is undoubtedly one of the most widely used statistical tools, and its predictive power is mostly determined by appropriate choices of independent variables or covariates, perhaps after transformations. Its name of “regression” was first coined by British statistician `Francis Galton` in 1885 [[7]](#c10.xhtml#c10-bib-0007), and its context was further consolidated by his disciple `Karl Pearson` in 1903 [[18]](#c10.xhtml#c10-bib-0018). Generally speaking, regression analysis estimates the relationship between the response (dependent) and independent variables, which is not completely known but subject to some random error caused by noisy data. To name its immediate application in finance, the celebrated Capital Asset Pricing Model (CAPM) by Markowitz in 1952 [[16]](#c10.xhtml#c10-bib-0016) is indeed a representative example. In this chapter, starting from this conventional model, we shall revisit the simple and multiple linear regression models, including the special case of polynomial regression, then we discuss several commonly used generalized linear models, namely `logistic regression` and `Poisson regression`, together with their applications in finance as well as the practical considerations for issues such as model selection and evaluation. In addition, echoing the PCA discussion in [Chapter 9](#c09.xhtml), we shall also introduce the closely related `principal component regression` and illustrate its use in practice.

## 10.1 SIMPLE AND MULTIPLE LINEAR REGRESSION MODELS AND BEYOND

CAPM, as mentioned above, is in fact a simple linear regression of an individual asset's return against the market rate of return, namely:

(10.1) `rᵢ = r_f + βᵢ(r_m - r_f) + εᵢ, i = 1, 2, ..., n`

so that
