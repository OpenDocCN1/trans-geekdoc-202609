the figure! By squaring those numbers and plotting them in another hyper plan, you can perfectly separate each group of points.

![](bbox=[0.13, 0.155, 0.87, 0.38])

Figure 4.7 – Exponential transformation in action

You might be thinking that there are infinite ways in which you can deal with your data. Although this is true, you should always take the business scenario you are working on into account and plan the work accordingly. Remember that model improvements or exploration is always possible, but you have to define your goals (remember the CRISP-DM methodology) and move on.

By the way, data transformation is important, but it is just one piece of your work as a data scientist. Your modeling journey still needs to move to other important topics, such as missing values and outliers handling. However, before that, you may have noticed that you were introduced to Gaussian distributions during this section, so why not go deeper into it?

# Understanding data distributions

Although the Gaussian distribution is probably the most common distribution for statistical and machine learning models, you should be aware that it is not the only one. There are other types of data distributions, such as the Bernoulli, binomial, and Poisson distributions.

The Bernoulli distribution is a very simple one, as there are only two types of possible events: success or failure. The success event has a probability p of happening, while the failure one has a probability of 1-p.

Some examples that follow a Bernoulli distribution are rolling a six-sided die or flipping a coin. In both cases, you must define the event of success and the event of failure. For example, assume the following success and failure events when rolling a die: