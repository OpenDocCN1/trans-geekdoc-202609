
the figure! By squaring those numbers and plotting them in another hyperplane, you can perfectly separate each group of points.

![](img/87c29232224b00f5a8bba6a66a391700_108_0.png)

Figure 4.7 – Exponential transformation in action

You might be thinking that there are infinite ways in which you can deal with your data. Although this is true, you should always take the business scenario you are working on into account and plan the work accordingly. Remember that model improvements or exploration is always possible, but you have to define your goals (remember the CRISP-DM methodology) and move on.

By the way, data transformation is important, but it is just one piece of your work as a data scientist. Your modeling journey still needs to move to other important topics, such as missing values and outliers handling. However, before that, you may have noticed that you were introduced to Gaussian distributions during this section, so why not go deeper into it?

## Understanding data distributions

Although the Gaussian distribution is probably the most common distribution for statistical and machine learning models, you should be aware that it is not the only one. There are other types of data distributions, such as the Bernoulli, binomial, and Poisson distributions.

The Bernoulli distribution is a very simple one, as there are only two types of possible events: success or failure. The success event has a probability p of happening, while the failure one has a probability of 1-p.

Some examples that follow a Bernoulli distribution are rolling a six-sided die or flipping a coin. In both cases, you must define the event of success and the event of failure. For example, assume the following success and failure events when rolling a die:

- Success: Getting a number 6
- Failure: Getting any other number

You can then say that there is a p probability of success (1/6 = 0.16 = 16%) and a 1-p probability of failure (1 - 0.16 = 0.84 = 84%).

The binomial distribution generalizes the Bernoulli distribution. The Bernoulli distribution has only one repetition of an event, while the binomial distribution allows the event to be repeated many times, and you must count the number of successes. Continue with the prior example, that is, counting the number of times you got a 6 out of our 10 dice rolls. Due to the nature of this example, binomial distribution has two parameters, n and p, where n is the number of repetitions and p is the probability of success in every repetition.

Finally, a Poisson distribution allows you to find a number of events in a period of time, given the number of times an event occurs in an interval. It has three parameters: lambda, e, and k, where lambda is the average number of events per interval, e is the Euler number, and k is the number of times an event occurs in an interval.

With all those distributions, including the Gaussian one, it is possible to compute the expected mean value and variance based on their parameters. This information is usually used in hypothesis tests to check whether some sample data follows a given distribution, by comparing the mean and variance **of the sample** against the **expected** mean and variance of the distribution.

You are now more familiar with data distributions, not only Gaussian distributions. You will keep learning about data distributions throughout this book. For now, it is time to move on to missing values and outlier detection.

## Handling missing values

As the name suggests, missing values refer to the absence of data. Such absences are usually represented by tokens, which may or may not be implemented in a standard way.

Although using tokens is standard, the way those tokens are displayed may vary across different platforms. For example, relational databases represent missing data with NULL, core Python code will use None, and some Python libraries will represent missing numbers as **Not a Number (NaN)**.

### IMPORTANT NOTE

For numerical fields, don't replace those standard missing tokens with zeros. By default, zero is not a missing value, but another number.

However, in real business scenarios, you may or may not find those standard tokens. For example, a software engineering team might have designed the system to automatically fill missing data with specific tokens, such as “unknown” for strings or “-1” for numbers. In that case, you would have to search by those two tokens to find missing data. People can set anything.

In the previous example, the software engineering team was still kind enough to give you standard tokens. However, there are many cases where legacy systems do not add any data quality layer in front of the user, and you may find an address field filled with, “I don’t want to share,” or a phone number field filled with, “Don’t call me.” This is clearly missing data, but not as standard as the previous example.

There are many more nuances that you will learn regarding missing data, all of which you will learn in this section, but be advised: before you start making decisions about missing values, you should prepare a good data exploration and make sure you find those values. You can either compute data frequencies or use missing plots, but please do something. Never assume that your missing data is represented only by those handy standard tokens.

Why should you care about this type of data? Well, first, because most algorithms (apart from decision trees implemented on very specific ML libraries) will raise errors when they find a missing value. Second (and maybe most important), by grouping all the missing data in the same bucket, you are assuming that they are all the same, but in reality, you don’t know that.

Such a decision will not only add bias to your model – it will reduce its interpretability, as you will be unable to explain the missing data. Once you know why you want to treat the missing values, then you can analyze your options.

Theoretically, you can classify missing values into two main groups: **MCAR** or **MNAR**. MCAR stands for **Missing Completely at Random** and states that there is no pattern associated with the missing data. On the other hand, MNAR stands for **Missing Not at Random** and means that the underlying process used to generate the data is strictly connected to the missing values.

Look at the following example about MNAR missing values. Suppose you are collecting user feedback about a particular product in an online survey. Your process of asking questions is dynamic and depends on user answers. When a user specifies an age lower than 18 years old, you never ask his/her marital status. In this case, missing values of marital status are connected to the age of the user (MNAR).

Knowing the class of missing values that you are dealing with will help you understand whether you have any control over the underlying process that generates the data. Sometimes, you can come back to the source process and, somehow, complete your missing data.

### IMPORTANT NOTE

Although, in real scenarios, you usually need to treat missing data via exclusion or imputation, never forget that you can always try to look at the source process and check if you can retrieve (or, at least, better understand) the missing data. You may face this option in the exam.

If you don’t have an opportunity to recover your missing data from anywhere, then you should move on to other approaches, such as **listwise deletion** and **imputation**.

Listwise deletion refers to the process of discarding some data, which is the downside of this choice. This may happen at the row level or the column level. For example, suppose you have a DataFrame containing four columns and one of them has 90% of its data missing. In such cases, what usually makes more sense is dropping the entire feature (column), since you don’t have that information for the majority of your observations (rows).

From a row perspective, you may have a DataFrame with a small number of observations (rows) containing missing data in one of its features (columns). In such scenarios, instead of removing the entire feature, what makes more sense is removing only those few observations.

The benefit of using this method is the simplicity of dropping a row or a column. Again, the downside is losing information. If you don’t want to lose information while handling your missing data, then you should go for an imputation strategy.

Imputation is also known as replacement, where you will replace missing values by substituting a value. The most common approach to imputation is replacing the missing value with the mean of the feature. Please take note of this approach because it is likely to appear in your exam:

| Age |
|---|
| 35 |
| 30 |
| |
| 25 |
| 80 |
| 75 |

Table 4.10 – Replacing missing values with the mean or median

Table 4.10 shows a very simple dataset with one single feature and five observations, where the third observation has a missing value. If you decide to replace that missing data with the mean value of the
