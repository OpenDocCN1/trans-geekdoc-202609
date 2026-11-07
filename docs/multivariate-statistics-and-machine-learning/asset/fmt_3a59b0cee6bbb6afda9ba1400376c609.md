
| 2 || 1.064621 || 1.056185 || 0.8483518 |
| 3 || 1.180842 || 1.074542 || 0.6439798 |
| 4 || 1.110699 || 1.053012 || 0.6782041 |

The following will visualize the classes by color, where the support vectors are indicated by crosses (code in Meyer et al., [2023](#ref.xhtml#re_CIT000251)):

```
> plot(cmdscale(dist(iris[,-5])),
+ col = as.integer(iris[,5]),
+ pch = c(“o”, “+”)[1:150 %in% model$index + 1])
```

The function `cmdscale()` is *classic multidimensional scaling* performed on the iris data with Euclidean distances, `dist()` computed on all variables except the fifth variable (`[,−5]`), which is species. The plotting character (`pch`) is for cases 1 through 150 for the model indexed by case number (`model$index` + 1 is the first column representing case number in the `iris` data). The plot appears in [Figure 9.11](#c9.xhtml#f9.11).

![Figure 9.11 Discrimination plot resulting from support vector machine on iris data.Return to text.⏎](images/fig9.11.jpg)

*Figure 9.11* Discrimination plot resulting from support vector machine on iris data.[Return to text.⏎](#c9.xhtml#re_f9.11)

The `e1071` package contains several more options (including cross-validation techniques) for running support vector machines as well as a host of other statistical and machine learning methods (e.g., clustering and Naïve Bayes). The `caret` package ([Kuhn, 2024](#ref.xhtml#re_CIT000209)) can be used as with other methods, for cross-validation and, for `svm` specifically, selecting the value for `C` (tuning parameter) that maximizes accuracy.

The `MASS` package ([Venables & Ripley, 2002](#ref.xhtml#re_CIT000376)) also has excellent `svm` visualization capabilities. For example, the following plots the classification boundaries for a support vector machine on the `cats` data ([Figure 9.12](#c9.xhtml#f9.12)), where the objective is to predict `sex` membership (`male` or `female`) based on bodyweight (`Bwt`) in kilograms and heart weight (`Hwt`) in grams:367

![Figure 9.12 Nonlinear decision boundary on the cat data.Return to text.⏎](images/fig9.12.jpg)

*Figure 9.12* Nonlinear decision boundary on the cat data.[Return to text.⏎](#c9.xhtml#re_f9.12)

```
> data(cats, package = “MASS”)
> head(cats)
```

|  || Sex || Bwt || Hwt |
| --- | --- | --- | --- |
| 1 || F || 2.0 || 7.0 |
| --- | --- | --- | --- |
| 2 || F || 2.0 || 7.4 |
| 3 || F || 2.0 || 9.5 |
| 4 || F || 2.1 || 7.2 |
| 5 || F || 2.1 || 7.3 |
| 6 || F || 2.1 || 7.6 |

```
> m <- svm(Sex~., data = cats)
> plot(m, cats)
```

We can see from the plot the nonlinear boundary separating male cats from females on the variable of `sex` based on `Bwt` and `Hwt`.

## 9.5 Chapter Review Exercises

1. 1\. What is a *maximal margin classifier* and why is the length of `β` typically set to 1.0?
2. 2\. How is a maximal margin classifier different from an ordinary least-squares regression line? Are they not both *linear*?
3. 3\. Interpret the following inequality: `y[i](β[0]+β[1]x[i][1]+β[2]x[i][2]+...+β[p]x[i][p]) > 0`.
4. 4\. How does a maximal margin classifier go about classification? Explain.
5. 5\. What is the significance of the maximum margin classifier’s solution being obtainable by *convex optimization*? What if the solution was nonconvex?
6. 6\. Why is the case of no separating hyperplane challenging to deal with? Aside from support vector machines, what are some other possible solutions to dealing with this problem?
7. 7\. What is the influence of a *slack variable* in the *support vector classifier*? How does this help define a *soft margin*?
8. 8\. What role does the kernel function play in addressing potential nonlinearity in the classification problem? Explain the *kernel trick* in relation to support vector machines.
9. 9\. Explain how the *linear kernel* reduces to simply taking the *inner product* of two vectors.
10. 10\. Perform a support vector machine on the iris data using a *sigmoid kernel*. Compare results to using a *radial kernel*. Are results similar or different?

368

# 10 Decision Trees, Bagging, Random Forests and Committee Machines

DOI: [10.4324/9781003376941-13](https://doi.org/10.4324/9781003376941-13)

Thus far in this book we have surveyed a number of *learners*. A *strong learner*, as can be said of an intelligent human being, adapts relatively quickly to new data (or *experience* more generally) and adjusts how it does things as the incoming data call for it. One touch of the hot stove psychologically conditions the individual to stay away from hot stoves – perhaps forever. A “close call” and near traffic accident on a winter road conditions you to forever drive with more care in winter, or even perhaps in all seasons. If we had the choice, *we would usually prefer strong learners*.

A *weak learner* learns much more slowly. This is the individual who has five DUI arrests yet still risks the lives of others and “never learns” (and probably belongs forever in jail). More statistically, a weak (also called a *base*) classifier is one that correctly classifies just over 50% of the time, that is, a bit better than chance ([Izenman, 2008](#ref.xhtml#re_CIT000167)). Even though we would like all learners to be strong, the truth is that many (perhaps most) times, we are confronted with weak learners. Given this is the case, the question then becomes the following:

> *How can we take a series of weak learners and combine them to produce a stronger one?*

This is what this chapter is all about. It is about how to take a number of weak learners, combine them in *some capacity*, and generate a much stronger learner. Perhaps the most amazing thing here is that by combining weak learners, we generate a *stronger learner*. This in itself is quite a remarkable idea. There are even times when choosing a set of weak learners dominates a single strong learner. Hence, though we in general prefer strong learners, sometimes combining weaker learners is actually more efficient. Five “close calls” with the hot stove (set of weak learners) may teach you to avoid hot stoves better than a single experience (strong learner) in which you undergo an actual burn.

> *Given the choice, we would generally prefer all learners be strong learners. However, by combining weak learners, it becomes possible to generate a stronger learner. Combining a set of weak learners can actually be preferable in some cases over a single stronger learner.*

## 10.1 Why Combining Weak Learners Works: Concept of Variance Reduction Using Averages

It is well known in statistics that *averaging reduces variance*. That is, when one repeatedly guesses the average income of a population, one “centers” in on a figure at the expense of a lot of variability around that figure.369

So-called *ensemble* methods or *committee machines* combine weak learners to produce stronger ones, ones that are more *stable* than not. Unstable predictors or classifiers have high variance (due to overfitting) and low bias. As we will see, methods such as *decision trees* suffer from high variance such that if we tweak the data slightly, we are likely going to see a significant change in the outcome. This is what suffering from high variance means. It means if you *perturbate* (i.e., “change”) the data in different ways, even if rather slight, it results in much *perturbated* outcomes, as [Figure 10.1](#c10.xhtml#f10.1) illustrates.

![Figure 10.1 Example of pertubating a data set. Original data set (left). Pertubated data set by adding random points (right).Return to text.⏎](images/fig10.1.jpg)

*Figure 10.1* Example of pertubating a data set. Original data set (left). Pertubated data set by adding random points (right).[Return to text.⏎](#c10.xhtml#re_f10.1)
