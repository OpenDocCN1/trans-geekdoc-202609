hope for is to control some average false discover rate. You will see throughout this text that much of contemporary data science occurs in environments that are super-high-dimensional. In such settings, you don't have the luxury of being nonparametric. Instead, to get workable results, you need to make assumptions about the model and give some reasonable *prior* guesses about the parameters of those models. Bayes is the language that facilitates this process.

Throughout the rest of this book, you will be exposed to Bayesian ideas without them being referred to as explicitly Bayesian. For example, the penalties in **Chapter 3** are interpretable as the effects of Bayesian priors, and the ensemble methods behind random forests in **Chapter 9** are a version of Bayesian model averaging. In such cases, we generally won't discuss inference directly. Rather, the methods we work with will be engineered to produce point estimates that perform well in high-dimensional environments where there is a lot of uncertainty. That is the strength of Bayes and the reason why model builders tend to think as Bayesians. To build a learning algorithm that *works* when given only messy unstructured data, you need a framework that lets you bring prior experience to bear and that is transparent about how to combine data with beliefs.

+   1. Parametric analysis quantifies uncertainty conditional on an assumed true model, while nonparametric analysis allows for model misspecification. See Chapters 5, 6, and 9 (and the material in this chapter on the bootstrap) for examples of nonparametric inference.

+   2. There are many different types of bootstrap, and we cover here only a couple main algorithms. See Davison and Hinkley [1997] for a practical guide to the full world of bootstrapping.

+   3. Matt Taddy, Hedibert Lopes, and Matt Gardner. Scalable semi-parametric inference for the means of heavy-tailed distributions. *arXiv:1602.08066*, 2016b.

+   4. See also the section on uncertainty quantification in Chapter 3, where the parametric bootstrap is used to provide inference for lasso algorithms.

+   5. Fill in all the steps of this derivation as a good exercise for contrasting population and sample expectation.

+   6. The subsample *n* = 100 is small enough that this bias will matter. At the full sample, as for most applications in this book, *n* is so big that this bias makes little difference and you don't need to worry about it.

+   7. Most introductory statistics books spend a lot of time differentiating between *z* and *t* statistics, the former having a normal distribution and the latter Student's *t* distribution. In this book, the sample sizes are large enough that things will be approximately normally distributed whenever such a distinction arises. When distributions are non-normal, they won't be Student's *t* either, and you'll rely upon bootstrapping.