
compute from data that is like this dataset. Now, there are some theoretical answers that describe the distribution of the mean— you can find them in any introductory statistics textbook. But, for other statistics— up to and including something as fancy as trained classifiers— we don’t have nice, pre-canned answers calculated by easy formulas. Bootstrapping provides a direct alternative. To figure out how to compute a bootstrapped value, let’s look at some code and some graphics that explain this process.

## Sampling with and without Replacement

We need one other idea before we describe the bootstrap process. There are two ways to sample, or select, values from a collection of data. The first is sampling without replacement. Imagine we put all of our data in a bag. Suppose we want one sample of five examples from our dataset. We can put our hand in the bag, pull out an example, record it, and set it to the side. In this case— without replacement— it does not go back in the bag. Then we grab a second example from the bag, record it, and put it to the side. Again, it doesn’t go back in the bag. We repeat these selections until we’ve recorded five total examples. It is clear that what we select on the first draw has an effect on what is left for our second, third, and subsequent draws. If an example is out of the bag, it can’t be chosen again. Sampling without replacement makes the choices dependent on what happened earlier— the examples are not independent of one another. In turn, that affects how statisticians let us talk about the sample.

The other way we can sample from a dataset is by sampling with replacement: we pull out an example from the dataset bag, record its value, and put the example back in the bag. Then we draw again and repeat until we have the number of samples we want. Sampling with replacement, as in Figure 12.3, gives us an independent sequence of examples.

So, how do we use bootstrapping to compute a bootstrap statistic? We randomly sample our source dataset, with replacement, until we generate a new bootstrap sample with the same number of elements as our original. We compute our statistic of interest on that bootstrap sample. We do that several times and then take the mean of those individual bootstrap sample statistics. Figure 12.4 shows the process visually for calculating the bootstrap mean.

Let’s illustrate that idea with some code. We’ll start with the classic, nonbootstrap formula for the mean.

```
In [3]:

dataset = np.array([1,5,10,10,17,20,35])
def compute_mean(data):
    return np.sum(data) / data.size
compute_mean(dataset)
```

Out[3]:

14.0

Nothing too difficult there. One quick note: we could apply that calculation to the entire dataset and get the usual answer to the question, “What is the mean?” We could also apply compute_mean to other, tweaked forms of that dataset. We’ll get different answers to different questions.

![](img/d94e4cd766940d79abed0bc6ba4e4344_420_0.png)

Figure 12.3 When we sample with replacement, examples are selected, recorded, and then returned to the cauldron.

Now, let's pivot to the bootstrap technique. We'll define a helper function to take a bootstrap sample—remember, it happens with replacement—and return it.

In [4]:

```
def bootstrap_sample(data):
    N  = len(data)
    idx = np.arange(N)
    bs_idx = np.random.choice(idx, N,
                              replace=True) # default added for clarity
    return data[bs_idx]
```

Now we can see what several rounds of bootstrap sampling and the means for those samples look like:

![](img/d94e4cd766940d79abed0bc6ba4e4344_421_0.png)

Figure 12.4 We repeatedly calculate the value of the mean on bootstrap samples. We combine those values by taking their mean.

```
In [5]:

bsms = []
for i in range(5):
    bs_sample = bootstrap_sample(dataset)
    bs_mean = compute_mean(bs_sample)
    bsms.append(bs_mean)

    print(bs_sample, "{:5.2f}".format(bs_mean))
```

[35 10 1 1 10 10 10] 11.00
[20 35 20 20 20 20 20] 22.14
[17 10 20 10 10 5 17] 12.71
[20 1 10 35 1 17 10] 13.43
[17 10 10 10 1 1 10] 8.43

From those bootstrap sample means we can compute a single value—the mean of the means:

```
In [6]:

print("{:5.2f}".format(sum(bsms) / len(bsms)))
```

13.54

Here is the bootstrap calculation rolled up into a single function:

```
In [7]:
def compute_bootstrap_statistic(data, num_boots, statistic):
    'repeatedly calculate statistic on num_boots bootstrap samples'
    # no comments from the peanut gallery
    bs_stats = [statistic(bootstrap_sample(data)) for i in range(num_boots)]
    # return the average of the calculated statistics
    return np.sum(bs_stats) / num_boots

bs_mean = compute_bootstrap_statistic(dataset, 100, compute_mean)
print("{:.2f}".format(bs_mean))
```

13.86

The really interesting part is that we can compute just about any statistic using this same process. We'll follow up on that idea now.

### 12.3.2 From Bootstrapping to Bagging

When we create a bagged learner, we are constructing a much more convoluted statistic: a learner in the form of a trained model. In what sense is a learner a statistic? Broadly, a statistic is any function of a group of data. The mean, median, min, and max are all calculations that we apply to a dataset to get a result. They are all statistics. Creating, fitting, and applying a learner to a new example—while a bit more complicated—is just calculating a result from a dataset.

I'll prove it by doing it.

```
In [8]:
def make_knn_statistic(new_example):
    def knn_statistic(dataset):
        ftrs, tgt = dataset[:,:-1], dataset[:,-1]
        knn = neighbors.KNeighborsRegressor(n_neighbors=3).fit(ftrs, tgt)
        return knn.predict(new_example)
    return knn_statistic
```

The one oddity here is that we used a closure—we discussed these in Section 11.1. Here, our statistic is calculated with respect to one specific new example. We need to hold that test example fixed, so we can get down to a single value. Having done that trick, we have a calculation on the dataset—the inner function, knn_statistic—that we can use in the exact same way that we used compute_mean.

```
In [9]:
# have to slightly massage data for this scenario
# we use last example as our fixed test example
diabetes_dataset = np.c_[diabetes_ftrs, diabetes_tgt]
```

```
ks = make_knn_statistic(diabetes_ftrs[-1].reshape(1,-1))
compute_bootstrap_statistic(diabetes_dataset, 100, ks)
```

Out[9]:

74.00666666666667

Just like computing the mean will give us different answers depending on the exact dataset we use, the returned value from knn_statistic will depend on the data we pass into it.

We can mimic that process and turn it into our basic algorithm for bagging:
- 1. Sample the data with replacement.
- 2. Create a model and train it on that data.
- 3. Repeat.

To predict, we feed an example into each of the trained models and combine their predictions. The process, using decision trees as the component models, is shown in Figure 12.5.

![](img/d94e4cd766940d79abed0bc6ba4e4344_423_0.png)

Figure 12.5 As with the bootstrapped mean, we sample the dataset and generate a decision tree from each subdataset. Every tree has a say in the final prediction.

Here's some pseudocode for a classification bagging system:

```
In [10]:

def bagged_learner(dataset, base_model, num_models=10):
    # pseudo-code: needs tweaks to run
    models = []
    for n in num_models:
        bs_sample = np.random.choice(dataset, N, replace=True)
        models.append(base_model().fit(*bs_sample))
    return models

def bagged_predict_class(models, example):
    # take the most frequent (mode) predicted class as result
    preds = [m.predict(example) for m in models]
    return pd.Series(preds).mode()
```

We can talk about some practical concerns of bagging using the bias-variance terminology we introduced in Section 5.6. (And you thought that was all just theoretical hand-waving!) Our process of combining many predictions is good at balancing out high variance: conceptually, we're OK with overfitting in our base model. We'll overfit and then let the averaging—or, here, taking the biggest vote getter with the mode—smooth out the rough edges. Bagging doesn't help with bias, but it can help significantly reduce variance. In practice, we want the base_model to have a low bias.

Conceptually, since our learners are created from samples that are taken with replacement, the learners are independent of one another. If we really wanted to, we could train each of the different base models on a separate computer and then combine them together at the end. We could use this separation to great effect if we want to use parallel computing to speed up the training process.

### 12.3.3 Through the Random Forest

Random forests (RFs) are a specific type of a bagged learner built on top of decision trees. RFs use a variation on the decision trees we've seen. Standard decision trees take the best-evaluated feature of all the features to create a decision node. In contrast, RFs subselect a random set of features and then take the best of that subset. The goal is to force the trees to be different from each other. You can imagine that even over a random selection of the examples, a single feature might be tightly related to the target. This alpha feature would then be pretty likely to be chosen as the top split point in each tree. Let's knock down the monarch of the hill.

Instead of a single feature being the top decision point in many bootstrapped trees, we'll selectively ignore some features and introduce some randomness to shake things up. The randomness forces different trees to consider a variety of features. The original random forest algorithm relied on the same sort of majority voting that we described for bagging. However, sklearn's version of RFs extracts class probabilities from each tree in the forest and then averages those to get a final answer: the class with the highest average probability is the winner.
