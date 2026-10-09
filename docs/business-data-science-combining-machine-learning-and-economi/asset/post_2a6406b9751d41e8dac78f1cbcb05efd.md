
```r
> Bdmr <- coef(glassdmr)
> round(Bdmr, 1)
```
18 × 6 sparse Matrix of class "dmrcoef"
| | WinF | WinNF | Veh | Con | Tabl | Head |
|---|---|---|---|---|---|---|
| intercept | -28.4 | 13.4 | 169.4 | 118.2 | -12.1 | -22.2 |
| RI | . | . | . | . | . | . |
| Na | -0.3 | -0.2 | -0.3 | -2.5 | 0.6 | 0.6 |
| Mg | 0.8 | . | 2.3 | -1.5 | . | -0.3 |
| Al | -1.1 | 0.4 | -0.4 | 1.4 | 0.8 | 0.9 |
| Si | 0.4 | -0.1 | -2.8 | -1.3 | . | 0.1 |
| K | . | . | -3.1 | . | -8.5 | . |
| Ca | . | -0.5 | 3.3 | 0.3 | 0.2 | . |
| Ba | . | -2.3 | . | . | -6.2 | 0.7 |
| Fe | -0.5 | 1.0 | -2.3 | 5.1 | -10.9 | . |
| RI:Na | . | . | . | 0.2 | . | . |
| RI:Mg | 0.0 | -0.1 | . | -0.1 | -0.1 | . |
| RI:Al | . | -0.1 | . | . | . | . |
| RI:Si | . | 0.0 | . | . | . | . |
| RI:K | . | 0.1 | . | . | . | . |
| RI:Ca | . | . | -0.2 | -0.2 | 0.0 | . |
| RI:Ba | . | 0.1 | . | -0.6 | . | . |
| RI:Fe | -0.4 | -0.2 | 3.1 | -1.9 | . | . |

If you run and compare to the $\mathrm{glmnet}$ results, you will find differences across coefficients. The intercepts are wildly different; however, these differences wash away after normalization in the softmax function. The regression coefficients are also different—this is largely because of the different $\lambda_k$ penalties selected for each glass type, as opposed to the single shared $\lambda$ for $\mathrm{glmnet}$ (selected at $\widehat{\lambda} \approx e^{-5}$ under the CV-min rule). When it comes to prediction, however, they give similar results. The 20-fold OOS experiment plotted in Figure 4.11 shows no change in OOS performance for $\mathrm{dmr}$ versus $\mathrm{glmnet}$ when measured in terms of multinomial deviance. In this small-data ($n = 214$) case, there are no real differences even when you consider different model selection criteria. In larger examples, we see $\mathrm{dmr}$ sometimes significantly outperform $\mathrm{glmnet}$ in such experiments, and you can attribute this to the use of class-specific $\lambda_{k}$ penalties.

![](img/315929ad4bddd26368466d02e06e2385_177_0.png)

**FIGURE 4.11:** OOS performance for dmr and glmnet on a 20-fold experiment using the glass data. All model selection (including CV) is executed without the left-out test data for each fold.

In examples like the glass data classification, the parallelization strategy of $\mathrm{dmr}$ gives a useful efficiency boost: if you have four processors, you can compute all of the model estimates in about one-fourth the time. However, the real advantage for such methods comes when you are fitting multinomial logistic regressions for a massive number of outcome classes. In that case, parallelization can make the difference between feasibility and impossibility.

The motivating example behind the development of DMR was in text analysis. As we detail in Chapter 7, it is often useful to summarize documents as counts of words. A *multinomial inverse regression* model looks to analyze these counts as a function of document attributes in a multinomial logistic regression where “word” is the outcome class. Using the approximate formulation in Equation 4.10, the task is then to estimate $\hat{\boldsymbol{\beta}}_{k}$ for $\mathbb{E}[y_{ik}\mid \boldsymbol{x}_{i}] = \mathrm{exp}(\boldsymbol{x}_{i}^{\prime}\hat{\boldsymbol{\beta}}_{k})$ where $y_{ik}$ is the count for word $k$ in document $i$ and $x_{i}$ are document attributes (author, date, etc.). This requires you to fit as many sets of regression parameters as there are words. If you are dealing with a vocabulary of, say, 500,000 words, then such a task would be impossible without large amounts of parallelization.

We will detail these ideas in more detail in Chapter 7. But they raise the point that efficient data management and parallelization is an essential (not just convenient) part of modern analysis. It turns out the DMR is not just parallel but also *distributed*, and the difference between these terms is key to large-scale computing.

## DISTRIBUTION AND BIG DATA

An algorithm is *parallel* if it does many computations at once. When each of these calculations needs to see all of the same data, the algorithm is merely parallel. When each computation is able to work with a subset of the data, the algorithm is *distributed*. Parallel computing is good for intensive computation, but for true big data you need distributed algorithms. Indeed, the oldest use of the term *big data* referred to datasets that were too big to be stored on a single machine—thus distributed algorithms were necessary for any analysis.

The idea behind contemporary big data storage and analysis is to *shard* your data into many little pieces on many machines. You then take advantage of massive bandwidth to allow communication between these machines during analysis. Systems such as Hadoop HDFS, Amazon's S3 (see Figure 4.12), or Microsoft's Azure Blob Storage split your data into little pieces (e.g., 64KB of a file) that are kept wherever is convenient (to protect against data loss, pieces of data are often kept in more than one place). As the end user, you interact only with a map of where things are.

![](img/315929ad4bddd26368466d02e06e2385_178_0.png)

**FIGURE 4.12:** An Amazon S3 console, which looks like a standard file browser, but the file content is distributed across machines (or even across data centers).

This model was originally built around unstructured data, such as text and images, that benefited less from being stored locally in a structured database with columns and fixed entry sizes. But the distributed storage model is essential to cloud computing, and it now provides the underlying logic for a vast proportion of the world's data (especially business data). There are plenty of algorithms that have been developed to facilitate statistical analysis on these massive distributed datasets. Many fit within a framework known as MapReduce (MR), a simple but powerful recipe for algorithms that was popularized in 2004 by researchers at Google.$^{10}$ To use MapReduce, you need to be able to specify a key that indexes subgroups of data that can be analyzed in isolation.

### ALGORITHM 12 MapReduce Framework

Given a key indexing data to subgroups, you proceed to do the following:

- **map**: Calculate and sort relevant statistics by key.
- **partition**: Partition and pipe the outcome of map so that outcomes with the same key end up on the same machine.
- **reduce**: Apply a summarization operation within the subgroup defined by each key.

As a simple example, imagine the task of tabulating word occurrence by date across a large database of documents (e.g., books, magazines, newspapers). The MapReduce routine is applied on the distributed corpus of documents:

- **map**: Apply a map operation for each document, extracting the date and counts for each word. The mapper outputs multiple lines containing `date|word count`. Here's an example if the document uses the word “tacos” five times on June 4, 2017:

```
2017/06/04|tacos 5
```

- **partition**: The key in this example is `date|word`, for example, `2017/06/04|tacos`. The data is sorted and streamed so that each line with the same key ends up on the same reducer machine.
- **reduce**: Reduce all lines with the same key using the sum operator, such that the output is a single line per key: `date|word total`. Here's an example if tacos was used 501 times across all documents on June 4, 2017:

This simple example can be extended into a number of more complex schemes. For example, the DMR algorithm is distributed with respect to the response counts: each regression need only see $y_{ik}$ for its respective category $k$. In the case of txt regression, $k$ refers to a word in a vocabulary. Consider the example where you are looking to understand how some time-dependent variables—for example, market data or political events—affect language choice. If this is a relatively small set of variables, the full design matrix will be small enough to pass among many machines. For example, you might have the following reported returns in the S&P 500 and VIX financial market indices on each date:

$$
\mathbf{X} = \left[ \begin{array}{ccc} \text{date} & \text{SP500} & \text{VIX} \\ 2017/06/02 & 0.0037 & -0.0142 \\ \vdots & \vdots & \vdots \end{array} \right]. \tag{4.14}
$$

The MapReduce version of DMR is then as follows:

- **map and partition** exactly as described earlier in the word-count MR so that all counts for the same `date|word` key go to the same machine.
- **broadcast** your set of date-indexed covariates so that every reducer machine contains a copy of $X$.
- **reduce** using a Poisson regression for the word counts onto the corresponding S&P 500 and VIX returns for each day. The output is the length-2 vector of word-market $\beta_{kj}$ coefficients.

After collecting all of the coefficients, you've estimated a large text model. Such results can be used to understand how, for example, news drives change in market indices.

The implementation of basic MapReduce algorithms is straightforward. One common scheme acts exactly as described earlier, with the results of the mapper streamed line by line to the reducers. Suppose you've written a mapper script (e.g., `mapper.py` since Python is good at text parsing) that takes raw input and produces single lines of key-tagged output and a reducer script (e.g., `reduce.R` since you want to run glm/r regressions in R) that takes these single lines as input. Then kicking off a big MapReduce job in the cloud is easy using, say, Amazon's EMR (elastic mapreduce) command tools.
