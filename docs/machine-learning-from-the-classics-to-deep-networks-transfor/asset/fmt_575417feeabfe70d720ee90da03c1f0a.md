
* [68] B. Yang, A note on the error propagation analysis of recursive least-squares algorithms, *IEEE Trans. Signal Process.* 1994;42:3523–3525.

---

# Chapter 7: Classification: a tour of the classics

## Chapter Outline

* 7.1 [Introduction](#Chp007_293-342_B9780443292385000135.xhtml#s0010)
* 7.2 [Bayesian classification](#Chp007_293-342_B9780443292385000135.xhtml#s0015)
    * [The Bayesian classifier minimizes the misclassification error](#Chp007_293-342_B9780443292385000135.xhtml#s0020)
    * 7.2.1 [Average risk](#Chp007_293-342_B9780443292385000135.xhtml#s0025)
* 7.3 [Decision (hyper)surfaces](#Chp007_293-342_B9780443292385000135.xhtml#s0030)
    * 7.3.1 [The Gaussian distribution case](#Chp007_293-342_B9780443292385000135.xhtml#s0035)
        * [Minimum distance classifiers](#Chp007_293-342_B9780443292385000135.xhtml#s0040)
* 7.4 [The naive Bayes classifier](#Chp007_293-342_B9780443292385000135.xhtml#s0045)
* 7.5 [The nearest neighbor rule](#Chp007_293-342_B9780443292385000135.xhtml#s0050)
* 7.6 [Logistic regression](#Chp007_293-342_B9780443292385000135.xhtml#s0055)
* 7.7 [Fisher's linear discriminant](#Chp007_293-342_B9780443292385000135.xhtml#s0060)
    * 7.7.1 [Scatter matrices](#Chp007_293-342_B9780443292385000135.xhtml#s0065)
    * 7.7.2 [Fisher's discriminant: the two-class case](#Chp007_293-342_B9780443292385000135.xhtml#s0070)
    * 7.7.3 [Fisher's discriminant: the multiclass case](#Chp007_293-342_B9780443292385000135.xhtml#s0075)
* 7.8 [Classification trees](#Chp007_293-342_B9780443292385000135.xhtml#s0080)
* 7.9 [Combining classifiers](#Chp007_293-342_B9780443292385000135.xhtml#s0085)
    * [No free lunch theorem](#Chp007_293-342_B9780443292385000135.xhtml#s0090)
    * [Some experimental comparisons](#Chp007_293-342_B9780443292385000135.xhtml#s0095)
    * [Schemes for combining classifiers](#Chp007_293-342_B9780443292385000135.xhtml#s0100)
* 7.10 [The boosting approach](#Chp007_293-342_B9780443292385000135.xhtml#s0105)
    * [The AdaBoost algorithm](#Chp007_293-342_B9780443292385000135.xhtml#s0110)
    * [The log-loss function](#Chp007_293-342_B9780443292385000135.xhtml#s0115)
* 7.11 [Boosting trees](#Chp007_293-342_B9780443292385000135.xhtml#s0120)
* [Problems](#Chp007_293-342_B9780443292385000135.xhtml#s0125)
    * [Computer exercises](#Chp007_293-342_B9780443292385000135.xhtml#s0130)
* [References](#Chp007_293-342_B9780443292385000135.xhtml#bl0010)

## 7.1 Introduction

The classification task was introduced in Chapter [3](#Chp003_65-117_B9780443292385000093.xhtml). There, it was pointed out that, in principle, one could employ the same loss functions as those used for regression in order to optimize the design of a classifier; however, for most cases in practice, this is not the most reasonable way to attack such problems. This is because in classification the output random variable, `y`, is of a *discrete nature*; hence, different measures than those used for the regression task are more appropriate for quantifying performance quality.

The goal of this chapter is to present a number of widely used loss functions and methods. Most of the techniques covered are conceptually simple and constitute the basic pillars on which classification is built. Besides their pedagogical importance, these techniques are still in use in a number of practical applications and often form the basis for the development of more advanced methods, to be covered later in the book.

The classical Bayesian classification rule, the notion of minimum distance classifiers, the logistic regression loss function, Fisher's linear discriminant, classification trees, and the method of combining classifiers, including the powerful technique of boosting, are discussed. The perceptron rule, although it boasts to be among the most basic classification rules, will be treated in Chapter [18](#Chp018_885-995_B978044329238500024X.xhtml) and it will be used as the starting point for introducing neural networks and deep learning techniques. Support vector machines are treated in the framework of reproducing kernel Hilbert spaces in Chapter [11](#Chp011_519-582_B9780443292385000172.xhtml).

In a nutshell, this chapter can be considered a beginner's tour of the task of designing classifiers.

## 7.2 Bayesian classification

In Chapter [3](#Chp003_65-117_B9780443292385000093.xhtml), a linear classifier was designed via the least-squares (LS) method. However, the squared error criterion cannot serve well the needs of the classification task. In Chapters [3](#Chp003_65-117_B9780443292385000093.xhtml) and [6](#Chp006_249-291_B9780443292385000123.xhtml), we have proved that the LS estimator is an efficient one only if the conditional distribution of the output variable `y`, given the feature values `x`, follows a Gaussian one of a special type. However, in classification, the dependent variable is discrete, hence it is not Gaussian; thus, the use of the squared error criterion cannot be justified, in general. We will return to this issue in Section [7.10](#Chp007_293-342_B9780443292385000135.xhtml#s0105) ([Remarks 7.7](#Chp007_293-342_B9780443292385000135.xhtml#enun0065)), where the squared error is discussed against other loss functions used in classification.

In this section, the classification task will be approached via a different path, inspired by the *Bayesian decision theory*. In spite of its conceptual simplicity, which ties very well with common sense, Bayesian classification possesses a strong optimality flavor with respect to the probability of error, that is, the probability of wrong decisions/class predictions that a classifier commits.

**Bayesian classification rule**: Given a set of `M` classes, `ω[i]`, `i = 1, 2, …, M`, and the respective *posterior probabilities* `P(ω[i]|x)`, classify a feature vector, `x`, according to the following rule:^([^(44)](#fn44))

```
Equation (7.1)
```

In words, the pattern represented by `x` is assigned to the class for which the posterior probability becomes maximum. Sometimes, we refer to this rule, also, as the *Bayes classifier*.

Note that prior to receiving any observation, our uncertainty concerning the classes is expressed via the prior class probabilities, denoted by `P(ω[i])`, `i = 1, 2, …, M`. Once the feature vector, `x`, has been obtained, this extra information removes part of our original uncertainty, and the related statistical information is now provided by the posterior probabilities, which are then used for the classification.
