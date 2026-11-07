
*   Ahrens, Achim, Christian Hansen, and Mark Schaffer. 2023. “pystacked: Stacking Generalization and Machine Learning in Stata”. The Stata Journal, in process. [⏎](#chapter2.xhtml#b2ref2_1)
*   Cameron, Colin, and Pravin Trivedi. 2022. Microeconometrics Using Stata, 2nd edition. College Station, TX: Stata Press. [⏎](#chapter2.xhtml#b2ref2_2)
*   Friedman, Jerome. 1999. “Stochastic Gradient Boosting”. Technical Report, Stanford University. [⏎](#chapter2.xhtml#b2ref2_3)
*   Friedman, Milton. 1953. Essays in Positive Economics. Chicago, IL: Chicago University Press. [⏎](#chapter2.xhtml#b2ref2_4)
*   Hand, David. 2009. “Mismatched Models, Wrong Results, and Dreadful Decisions: On choosing appropriate data mining tools”. Working paper. Imperial College. [⏎](#chapter2.xhtml#b2ref2_5)
*   Haughton, Dominique, and Jonathan Haughton. 2011. Living Standards Analytics. New York, NY: Springer. [⏎](#chapter2.xhtml#b2ref2_6)
*   Hornik, Kurt, Maxwell Stinchcombe, and Halbert White. 1989. “Multilayer Feedforward Networks Are Universal Approximators”. Neural Networks, 2: 359–366. [https://cognitivemedium.com/magic\_paper/assets/Hornik.pdf](https://cognitivemedium.com/magic_paper/assets/Hornik.pdf) [⏎](#chapter2.xhtml#b2ref2_7)
*   Kim, Eric. 2013. “Everything You Wanted to Know about the Kernel Trick”. Working paper. [https://www.eric-kim.net/eric-kim-net/posts/1/kernel\_trick.html](https://www.eric-kim.net/eric-kim-net/posts/1/kernel_trick.html)
*   Larose, Daniel, and Chantal Larose. 2014. Discovering Knowledge in Data: An Introduction to Data Mining. Hoboken, NJ: Wiley. [⏎](#chapter2.xhtml#b2ref2_9)
*   Mincer, Jacob. 1974. Schooling, Experience, and Earnings. Cambridge, MA: National Bureau of Economic Research. [⏎](#chapter2.xhtml#b2ref2_10)
*   Minitab. 2023. Introducing Salford Predictive Modeler 8. [https://www.minitab.com/en-us/products/spm/](https://www.minitab.com/en-us/products/spm/) [⏎](#chapter2.xhtml#b2ref2_11)
*   Nielsen, Michael A. 2015. How the Backpropagation Algorithm Works. In Neural Networks and Deep Learning. San Francisco, CA: Determination Press. [http://neuralnetworksanddeeplearning.com/chap2.html](http://neuralnetworksanddeeplearning.com/chap2.html) [⏎](#chapter2.xhtml#b2ref2_12)
*   Tibshirani, Robert. 1996. “Regression Shrinkage and Selection via the Lasso”. Journal of the Royal Statistical Society. Series B (Methodology), 58(1): 267–288. [⏎](#chapter2.xhtml#b2ref2_13)
*   Verme, Paolo. 2023. “Predicting Poverty with Missing Incomes”. GLO Working Paper No. 1260. Global Labor Organization (GLO). [⏎](#chapter2.xhtml#b2ref2_14)
*   Wooldridge, Jeffrey. 2020. Introductory Econometrics: A Modern Approach. Andover, Hampshire, England: Cengage. [⏎](#chapter2.xhtml#b2ref2_15)
*   Zou, Hui, and Trevor Hastie. 2005. “Regularization and Variable Selection via the Elastic Net”. Journal of the Royal Statistical Society. Series B (Methodology), 67(2): 301–320. [⏎](#chapter2.xhtml#b2ref2_16)

# 3 Causality

DOI: [10.1201/9780429172588-3](https://doi.org/10.1201/9780429172588-3)

## 3.1 Introduction

Among the most important questions that businesses ask are some very simple ones: If I decide to do something, will it work? And if so, how large are the effects?

The important idea here is that we want to evaluate the impact of an intervention or treatment. This situation arises all the time. For instance:
*   A business is wondering whether to expand its loyalty program and wants to know whether it would enhance profits;
*   A retailer would like to know whether a sales campaign that emphasizes the eco-friendly nature of their clothing would boost sales; where it should advertise; whether it should open new outlets; or what new clothing features might tempt customers;
*   An airline is trying to work out what prices to charge on flights from Chicago to Denver in order to maximize revenue;
*   A bank is wondering whether greater investment in technical training would be worthwhile, as measured by higher worker productivity;
*   A university is debating whether a reduction in tuition will attract significantly more students;
*   A mobile phone operator in Latin America is considering whether to introduce a mobile banking facility;
*   A car manufacturer is trying to determine whether it should introduce a hybrid pickup.

In every case, we have one or more courses of action (“treatments”), and we want to determine whether they lead to useful results. We want to determine causality.

An important distinction needs to be made here between *observing* and *intervening*. We may observe that customers with loyalty cards are more likely to spend on our product than the average customer. Formally, we may write this conditional probability as:

`P(S|L) > P(S)`

which reads as “the probability of spending (`S`), given that one has a loyalty card (`L`), is greater than the probability of spending given that one may or may not have a loyalty card.” One might be tempted to conclude that loyalty cards cause customers to be more likely to spend, but this would be premature. Here we have only observed more frequent spending among those who have loyalty cards, but perhaps they were given loyalty cards because they spend more often, which would reverse the direction of causality. What really interests us is whether

`P(S|do(L)) > P(S)`.

Here we introduce Judea Pearl's “do operator” ([Pearl 1995](#chapter3.xhtml#ref3_23)), where we intervene to change the number of loyalty cards instead of allowing `L` to be set in the normal way ([Hitchcock 2010](#chapter3.xhtml#ref3_11), Section 3.6). If we increase `L` (i.e., “do” `L`), and sales rise as a result, we can reasonably claim that distributing more loyalty cards does cause people to be more likely to spend on our product. This is a probabilistic causation, in the sense that “causes change the probabilities of their effects” ([Hitchcock 2010](#chapter3.xhtml#ref3_11), Introduction): Intervening typically does not guarantee that there will be an effect, but it raises the likelihood of it.

It is not straightforward to identify causation with a reasonable degree of plausibility, but one can often succeed with the help of the concepts and techniques set out in this chapter and the next. We begin by stressing the importance of specifying an appropriate counterfactual, which allows us to measure treatment effects. Randomized controlled trials (RCTs) (aka experimental design) make this possible in a straightforward way, but this gold standard is rarely achievable. Quasi-experimental designs, including regression adjustment, inverse probability weighting (IPW), and covariate and propensity-score matching, are widely used and often very effective.

## 3.2 The Counterfactual

Identifying the impact of a treatment is not straightforward because it requires that we compare what actually occurred with a hypothetical *counterfactual* situation, namely what would have occurred in the presence or absence of the treatment. This is often referred to as the “potential outcomes” approach because it seeks to compare two potential outcomes (with or without treatment).

It is easy to go astray. Suppose your sales division introduces an advertising campaign for electric cars, just in the Northeast of the United States, and presents the following information:

|  || **Number of electric cars sold per million population** |
| --- | --- |
|   || **Pre-campaign (2024)** || **Post-campaign (2025)** |
| --- | --- | --- |
| Northeast US || 400 || 500 |

The 25% increase in sales is impressive, but we cannot assume that it was due to the advertising campaign unless we can rule out all other potential influences: Perhaps incomes were rising, tastes changing, or tax incentives were due to expire at the end of 2025.

We are now given some additional information about sales in the rest of the United States, where there was no advertising campaign:

|  || **Number of electric cars sold per million population** |
