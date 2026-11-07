
Consider what overfitting would look like in this case. We could simply connect the dots ([Figure 1.3](#c1.xhtml#f1.3), (2)). That is, we are modeling the theory (curve) too closely to the training data. What would underfitting look like? Suppose we simply modeled the mean ([Figure 1.3](#c1.xhtml#f1.3), (3)). This is an example of underfitting as it essentially ignores the richness of the data. A nice compromise would be the line of best fit, typically the regression line ([Figure 1.3](#c1.xhtml#f1.3), (4)). The regression line provides an *inexact* fit, but the theory here is general enough to possibly generalize to new test data.

In all of the models we refer to in this book, the more *specific* and *detailed* the model fit to data, in general, the more likely it is to overfit. *Do not be in a hurry to produce a model that fits the (training) data perfectly. Any such model can easily be built! The interest in model/theory-building is to produce a model that not only fits the current data reasonably well, but that also generalizes to new data*.

Of all the models we will study in this book, models such as neural networks are especially prone to overfitting. Why? Because, as we will see, due to allowing complex nonlinear relationships, they tend to capitalize on small perturbations in the data that may fail to generalize to new data. This is one reason why, despite the meteoric advances in model complexity in the statistics and machine learning literatures, classic linear models are still often preferred over more complex models in many contexts.41

### 1.14.1 Solutions to Overfitting

There are usually a variety of ways to deal with and cope with overfitting. Many depend on the specific method used. Sometimes simply taking averages of predictions made by a number of different models fit to the training data is sufficient for minimizing the effects of overfitting. As we will see later in the book, such is the approach essentially advocated by such procedures as *bagging*.

Perhaps the most common strategy to deal with overfitting is simply to *regularize* a model. Regularization is a general technique in which, all else being equal, simpler models are favored over more complex models and hence in general is in the spirit of Occam’s razor. This often translates to adding a penalty term to the loss or empirical risk function. We now briefly discuss regularization and then develop it at a deeper level later in the book.

### 1.14.2 The Idea of Regularization

The idea of *regularization* permeates several models in statistics and machine learning and we will see this principle applied regularly throughout the book. The *principle of regularization*, or shall we say the *spirit* of it, is much more general than the specific instances in which it is used or the individual method to which it is applied. If the principle is understood, then every time regularization is encountered, even in different forms, the reader will more easily understand it despite the precise details of how it is being applied in the given context. But what is regularization exactly? Probably the most general idea of regularization is the following:

> *Regularization simplifies models to reduce the probability of overfitting.*

By guarding against overfitting, *generalization error* is reduced ([Goodfellow et al., 2016](#ref.xhtml#re_CIT000131)). Regularization helps *stabilize* a model, and stable learners (or models) are less likely to overfit. If small changes to input data result in large changes in outcomes, as already discussed, the model is regarded as *unstable*. As a human analogy, a good friendship can withstand turbulence; that is, the outcome does not change in the face of adverse events. The friendship still remains strong. A weaker friendship is easily changed based on an input that breaks the friendship apart.

Most often in practice, regularization involves adding a penalty term to the maximized or minimized objective function ([Murphy, 2022](#ref.xhtml#re_CIT000259)). Early stopping of an algorithm also constitutes an attempt to regularize a model. Other times, simply collecting more data on which the model is applied is a suitable solution. While a polynomial may overfit say, 20 data points, it is unlikely to overfit 200 or 2,000, and the generalizability of the model will often improve.

## 1.15 The Measurement Problem

In the age of sophisticated algorithms and terabytes of data, it can be all too easy to pay insufficient attention to *what the data actually consist of*, that is, what they actually represent. Sure, we all desire novel algorithmic fancy and modern ways of analyzing such data, *but what if the data are not representing that which we sought out to measure*? What if that number in the spreadsheet does not correspond to what we believe it represents? If the data point does not represent what we sought to measure, no sophisticated statistical or machine learning algorithm will save it. What the data point *is a function of* can be easily taken for granted, an assumption that what we sought to measure we are in fact measuring. This can be a very dangerous assumption. In this section, we briefly survey some issues related to the larger problem of measurement in the social and natural 42sciences and discuss some of the more common ways of thinking of scales of measurement. We then very briefly discuss Likert scale data.

### 1.15.1 What Is Data?

To begin a discussion of measurement and reliability and validity, we should first ask ourselves what *data* are in the first place. At a philosophical level, which as mentioned virtually *everything* boils down to sooner or later when scrutinized enough, data is simply *information*. In the age of computerized data analysis, we of course associate a piece of data with a number in a spreadsheet, but it should be recognized that that numerical representation of data is simply a special case of the wider possibility of what data *could be*. For example, learning that your friend is not trustworthy is a piece of data. Looking up in the sky and seeing a sunny day is data. Your internet connection going out momentarily is yet another piece of data. The first to walk the planet were data analysts, not very good ones we might argue from our modern point of view, but data analysts just the same. What distinguishes today’s data analyst from centuries ago is that today we are more *systematic* and *precise* in how we go about defining, storing, and analyzing data.

### 1.15.2 The Philosophy and Scales of Measurement

Measurement can be interpreted as the assignment of numbers to objects via a set of rules. Crudely, if I am much taller than you, measurement implies that we have a rule that says I should get a higher number (measurement) than you and preferably by a well-defined amount on precisely measured units (e.g., inches). The problem with measurement, at a philosophical level, is the extent to which what we are actually measuring is a reflection of the true score we wish to measure. Make no mistake, the score we obtain with whatever instrument we use is but a *measurement*. It is not a *pure* reflection of the true score. In measurement theory, the true score `T` is a function of the observed score `O` plus error `E`:

`T` = `O` + `E`

(1.2)

To cut right to the chase, the measurement of something like height or weight contains more `O` than `E`, whereas the measurement of something like personality or intelligence, likely, or at minimum *one could argue*, contains more `E` than `O`. The key to (1.2) is that just because you measure something this does not necessarily imply that you are tapping into the true score. Much of your measurement may simply be *error*. The measurement of temperature with a dysfunctional thermometer may be more error than actual temperature, for instance.

### 1.15.3 Reliability
