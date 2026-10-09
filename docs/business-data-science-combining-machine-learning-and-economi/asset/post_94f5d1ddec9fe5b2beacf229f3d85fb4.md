
The main variable of interest here will be `repshare`, the proportion of the two-party vote (Dem and GOP, excluding independents and third parties) obtained by George W. Bush in the 2004 presidential election for each member's constituency (district for representatives, states for senators). See Figure 8.2 for illustration of the relationship between `repshare` and vocabulary.

![](img/315929ad4bddd26368466d02e06e2385_327_0.png)

`ca1` and `ca2` are also interesting. These are essentially the first two principal component scores for each member in PCA of their voting record. The model used is slightly different but closely related to the roll-calling voting PCA example in Chapter 7.

Under the assumption that the average beliefs of someone's constituents provide a signal on their own beliefs (or at least how they portray their beliefs), we can use `repshare` as a surrogate for ideology and partisanship. For example, Tom Price (R GA) says the term `death.tax` often (28 times), and he is from a congressional district that voted 70% for Bush in 2004. William Jefferson (D LA) says `estate.tax` often (32 times), and his district voted strongly against Bush (24%). If this pattern repeats itself (it does), we'd model `death.tax` as a Republican term and `estate.tax` as a Democratic term.

Gentzkow and Shapiro apply this logic to build an index of *slant* that sums across a speaker's term usage weighted by the direction of slant for each term. Their method turns out to be an instance of *marginal regression* (i.e., PLS(1); see Chapter 7. They are regressing repshare on speech content to build a model that connects language to partisanship. This is then used to quantify political slant in newspapers and investigate issues around partisanship and press ownership.

We can replicate their analysis using the pls function:

```R
> x <- congress109Counts
> slant <- pls(x, congress109Ideology$repshare, K=3)
```

Figure 8.3 shows results for the first three PLS directions. The in-sample $R^2$ for each direction is 0.17, 0.32, and 0.43—there is a big increase with each extra dimension. Qualitatively, the second direction appears to be necessary for picking up the language associated with high-repshare Republicans (those likely on the right of the party).

![](img/315929ad4bddd26368466d02e06e2385_328_0.png)

The PLS fits for repshare on relative term usage in the 1000 bigram congress109 vocabulary. Points are colored by political party—grey for Republicans and black for Democrats.

As an alternative to PLS, we can also run a lasso regression for repshare on text:

```R
> Lassoslant <- cv.gam1r(x, congress109Ideology)
```

Figure 8.4 shows the results of a CV experiment used to select $\lambda$ next to an OOS experiment to evaluate the number of PLS directions. We see that the lasso generally outperforms PLS here—the best PLS results are for $K$ of one or two, and OOS MSE for these is still more variable and slightly higher than for lasso under a range of $\lambda$.

![](img/315929ad4bddd26368466d02e06e2385_329_0.png)

FIGURE 8.4: The OOS predictive performance for (left) PLS as a function of $K$ and (right) lasso as a function of $\lambda$ in prediction of $\text{repshare}$ from text.

There are a number of transformations that can be applied to $X$ before running a text regression. For example, it is common to transform $X$ from raw word counts to *proportions* that are normalized by the document lengths. You divide each row of $X$ by row totals so that, for example, it doesn’t matter how much a politician speaks but just which words they choose when they do (Gentzkow and Shapiro use this normalization in their PLS estimation). Another common transformation replaces $x_{ij}$ with the indicators $\mathbb{I}_{[x_{ip} \neq 0]}$ so that the inputs track whether a term was ever used in the document. For both of these transformations and for any other you might think to use, you won’t know which is best until you run the regressions and do an OOS experiment. Model building and selection proceeds the same as for nontext data: construct a set of candidate models, and use CV (or an IC) to choose from this set.

In this example, applying lasso regression on the indicators $\mathbb{I}_{[x_{ip} \neq 0]}$ gets us the best OOS fit yet: a minimum MSE of 0.012 versus 0.015 for lasso regression onto the raw $x_{ij}$. Working with this model, the CV-min selection rule returns a set of 64 nonzero $\hat{\beta}_{j}$ loadings. We can investigate the ten phrases most indicative of low $\text{repshare}$ (i.e., left-leaning Democrats):

```R
> names(sort(B)[1:10])
[1] "congressional.black.caucu" "family.value"
[3] "issue.facing.american" "voter.registration"
[5] "minority.owned.business" "strong.opposition"
[7] "civil.right" "universal.health.care"
[9] "congressional.hispanic.caucu" "ohio.electoral.vote"
```

And those most predictive of high repshare (i.e., right-leaning Republicans):

```R
> names(sort(-B)[1:10])
[1] "million.illegal.alien" "human.embryo" "action.lawsuit"
[4] "private.property" "war.terror" "look.forward"
[7] "global.war" "illegal.immigration" "percent.growth"
[10] "illegal.alien"
```

Although interpretation of loadings in a lasso should be done with caution, it appears that the model is picking up issues that are indeed associated with each party.

## TOPIC MODELS

Text is super high dimensional, and there is often abundant *unlabeled* text available. For these reasons, unsupervised factor modeling is a popular and useful strategy with text data. You can fit a factor model to a giant corpus and use these factors for supervised learning on a subset of labeled documents. The unsupervised dimension reduction facilitates the supervised learning.

To study text factorization, we'll switch from politics to restaurants. We have 6166 reviews, with an average length of 90 words per review, from the now-defunct travel website `we8there.com`. A useful feature of these reviews is that they contain both text and a multidimensional rating on *overall* experience, *atmosphere*, *food*, *service*, and *value*. Each aspect is rated on a five-point scale, with 1 indicating terrible and 5 indicating excellent. As an example, one user submitted a glowing review for Waffle House #1258 in Bossier City, Louisiana:

> I normally would not review a Waffle House but this one deserves it. The workers, Amanda, Amy, Cherry, James and J.D. were the most pleasant crew I have seen. While it was only lunch, B.L.T. and chili, it was great. The best thing was the 50's rock and roll music, not to loud not to soft. This is a rare exception to what you all think a Waffle House is. Keep up the good work.

Overall: 5, Atmosphere: 5, Food: 5, Service: 5, Value: 5.

Another user found Sartin's Seafood in Nassau Bay, Texas, to be all-around low quality (but it must have been cheap):

> Had a very rude waitress and the manager wasn't nice either.

Overall: 1, Atmosphere: 1, Food: 1, Service: 1, Value: 5.

Intuitively, these reviews will be constructed from a number of underlying topics, for example, the type of food, the quality of the restaurant, or the geographic location. The hope is that we can uncover these topics via factorization.

After cleaning and Porter stemming, following the same procedure as for the `congress109` text tokenization, we are left with a vocabulary of 2640 bigrams. For example, the first review in the document-term matrix has nonzero counts on bigrams indicating a pleasant meal at a rib joint:

```R
> x <- we8thereCounts
> x[1,x[1,]!=0]

even though    larg portion    mouth water    red sauc    babi back
    1               1               1               1               1
back rib    chocol    mounse    veri    satisfa
    1               1               1               1               1
```

We can apply PCA to get a factor representation of the review text. After digging through the biggest rotations in the first few factors, we find that PC1 looks like it will be big and positive for positive reviews, while PC4 will be big and negative for Italian (pizza).
