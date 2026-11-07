
![Figure 0.1 Statistical understanding rarely occurs linearly, but instead in leaps and bounds as indicated in the step-like function. The upward arrow represents a “Eureka” moment where new understanding seemingly occurs in an instantaneous “leap.”Return to text.⏎](images/fig0.1.jpg)

*Figure 0.1* Statistical understanding rarely occurs linearly, but instead in leaps and bounds as indicated in the step-like function. The upward arrow represents a “Eureka” moment where new understanding seemingly occurs in an instantaneous “leap.”[Return to text.⏎](#intro.xhtml#re_f0.1)

As practical advice as you embark on your learning of statistics and machine learning, *do not try to understand everything at once*. Allow for “approximation” and “iteration” as you study. Allow for fuzziness each time you look at it. *Do not let perfection be the enemy of* *good* but rather study these things often with a fresh perspective and hopefully the fuzziness will begin to be replaced by understanding.

In this respect, we follow general and excellent ideas provided by [Hubbard and Hubbard (2002)](#ref.xhtml#re_CIT000161) in their advice on how to read mathematics more generally:

> Reading mathematics is different from other reading … there are two parts to understanding a theorem: understanding the statement, and understanding the proof. The first is more important than the second … . If you’re still having trouble, skip ahead to examples. This may contradict what you have been told – that mathematics is sequential, and that you must understand each sentence before going on to the next. In reality, although mathematical writing is necessarily sequential, mathematical understanding is not: you (and the experts) never understand perfectly up to some point not at all beyond. The “beyond,” where understanding is only partial, is an essential part of the motivation and the conceptual background of the “here and now.” You may often (perhaps usually) find that when you return to something you left half-understood, it will have become clear in the light of the further things you have studied, even though the further things are themselves obscure.”
>
> (p. 2)

### 0.7.1.1 Epistemological Maturity

One focus of the book is to situate statistical models and other *ideas* within a wider *context*. For example, set theory is often regarded as one of the most unifying areas of mathematics (though many would say now that *category theory* eclipses that perspective). A sign of maturity in knowledge of statistical and related models is being aware and understanding the more *global structures* of which smaller structures are special cases. These global structures can be more difficult to “see” as one considers more complex models. However, a simple example will illustrate the concept.

Most readers familiar with the analysis of variance will readily be aware that the between-subjects `t`-test can be considered a special case of the wider between-subjects ANOVA model. This is what we mean by *maturity* – one sees the higher-order structure from which others can be deduced and situated. This process continues for increasingly complex models. While at first many users of statistical methods may prefer a “cookbook approach” for simply selecting the “correct” method for a given problem, the maturity of the user in relation to statistics becomes evident when they realize there is never only a *single* way to analyze data. The cookbook approach is not necessarily always *wrong*; it is usually simply grossly *incomplete*.

If the student understands statistics at a higher level beyond the recipe book, not only do they become aware of different possibilities when analyzing data, their ability to interpret research findings skyrockets. The student no longer assumes that PCA is *equivalent* to dimension reduction, for instance, and thus when the conference speaker reports, “Our PCA did not reveal any components with eigenvalues greater than unity on the correlation matrix we analyzed, hence, the data are not amenable to dimension reduction,” the knowledgeable researcher is immediately aware of the incorrect conclusion to the research report. *The PCA did not reveal linear dimension reduction, the bigger picture of whether underlying dimensions exist in the data has not yet been answered, and may even be unanswerable, since the underlying manifold may not yet have been uncovered*. *The discovery of dimensionality depends greatly on the tool used in the search*. This is no trivial 18difference in conclusions, it is the difference between an *incorrect* vs. *correct* interpretation of the research outcome. *The distinction matters*.

The above is a perfect example of the hierarchical thinking we are attempting to generate in this book. Statistics is slippery; you can think you know it, you can think the formula or data say one thing, but underlying that conclusion is a new *base rate*, a new *denominator*, and if you’re not aware of that underlying base, you are bound to conclude it is winter because you are standing in your walk-in freezer! The ratio `2/4 = 0.5` is with certainty, until we consider that fraction relative to the new base of 5, then `(2/4)/5 = 0.1`. We were so sure `0.5` was the final answer until we incorporated the new base. Context is everything when it comes to statistics, mathematics, and science more generally. The narrow view of looking at only a few of the many variables in existence can seriously bias the conclusion. Of course, the best of mathematicians, statisticians, scientists, and researchers know this, it is second nature to them. But to the student of these areas, this is what is most important in learning: *there is always context to any conclusion*; *change the context, and the conclusion usually changes as well.*

## 0.8 Format and Organization of Chapters

A survey of each chapter follows:

* *[Chapter 1](#c1.xhtml#c1)* features a discussion of the philosophical foundations of the methods featured in this book as well as the more broad topics of statistical learning and machine learning.

* *[Chapter 2](#c2.xhtml#c2)* features an overview of the mathematical and statistical foundations required for the rest of the book. We discuss the “pillars” of statistics and machine learning, namely probability, statistics, linear algebra, calculus.

* *[Chapter 3](#c3.xhtml#c3)* features a (very) brief introduction to `R` and `Python` software. Both software packages are used throughout the book in providing brief “snippet” demonstrations of techniques.

* *[Chapter 4](#c4.xhtml#c4)* denotes the actual beginning of the statistical and machine learning segment of the book. We begin with a discussion of familiar univariate ANOVA models.

* *[Chapter 5](#c5.xhtml#c5)* surveys simple linear and multiple linear regression models, effect sizes for such models, mediated and moderated regression models, principal components regression, partial least-squares, and canonical correlation analysis. Regression is the bedrock of many statistical and machine learning methods and much of this chapter lays the foundation for material to be discussed later in the book.

* *[Chapter 6](#c6.xhtml#c6)* features a discussion of regularization in regression. We introduce the concept of regularization, then discuss the most common ways of regularizing a model, which includes ridge, lasso, elastic net. We also survey least-angle regression.

* *[Chapter 7](#c7.xhtml#c7)* features a discussion of nonlinear regression models, including polynomial regression, splines, kernel regression, and others. We also relate some of this material to neural networks discussed later in the book.
