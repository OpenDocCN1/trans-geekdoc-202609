
## 5.5 (ReSampling: Making More from Less) 137

I'll leave you with one final comment on repeated train-test splits and cross-validation. With k-CV, we will get one, and only one, prediction for each and every example. Each example is in precisely one test bucket. The predictions for the whole dataset will be aggregated from the k models that are developed on different sets of data. With repeated train-test splits, we may completely ignore training or predicting on some examples and make repeated predictions on other examples as we see in Figure 5.8. In repeated train-test splits, it is all subject to the randomness of our selection process.

![](img/d94e4cd766940d79abed0bc6ba4e4344_165_0.png)

Managing the repeated looping to make multiple train-test splits was a bit annoying. It was not heart- or back-breaking, but there are many places we could make a mistake. It would be nice if someone wrapped the process up in a single stand-alone function. Fortunately, sklearn has done that. If we pass in a ShuffleSplit data-splitter to the cv argument of cross_val_score, we get precisely the algorithm we hand-coded above.

```
In [25]:
linreg = linear_model.LinearRegression()
diabetes = datasets.load_diabetes()

# nondefault cv argument
ss = skms.ShuffleSplit(test_size=.25) # default, 10 splits
scores = skms.cross_val_score(linreg,
diabetes.data, diabetes.target,
cv=ss,
scoring='neg_mean_squared_error')

scores = pd.Series(np.sqrt(-scores))
df = pd.DataFrame({'RMSE': scores})
df.index.name = 'Repeat'
```

```
display(df.describe().T)

ax = sns.swarmplot(y='RMSE', data=df)
ax.set_xlabel('Over Repeated\nTrain-Test Splits');
```

|  | count | mean | std | min | 25% | 50% | 75% | max |
|---|---|---|---|---|---|---|---|---|
| RMSE | 10.000 | 55.439 | 3.587 | 50.190 | 52.966 | 55.397 | 58.391 | 60.543 |

![](img/d94e4cd766940d79abed0bc6ba4e4344_166_0.png)

The slight differences with our manual version are due to randomly selecting the train-test splits.

Now, I want to talk about another way that randomness affects us as intrepid students of machine learning. It's the kind of randomness that the computer uses when we ask it to do random things. Here's what's going on behind the scenes with ShuffleSplit. Don't worry, I'll explain random_state in just a second.

```
In [26]:

ss = skms.ShuffleSplit(test_size=.25, random_state=42)

train, test = 0, 1
next(ss.split(diabetes.data))[train][:10]
```

Out[26]:

```
array([ 16, 408, 432, 316,  3,  18, 355,  60, 398, 124])
```

By the way, I use next because ShuffleSplit relies on a Python generator to produce one split after another. Saying next provides me with the next data split. After fetching the next data split, I pick out the training data [train] and then the first ten examples [:10]. Good enough. Let's try again.

```
In [27]:

ss = skms.ShuffleSplit(test_size=.25, random_state=42)
next(ss.split(diabetes.data))[train][:10]
```

```
Out[27]:

array([ 16, 408, 432, 316,   3,  18, 355,  60, 398, 124])
```

That can't be good. Someone call—someone! We need help. The results are the same. Wasn't this supposed to be random? The answer is yes . . . and no. Randomness on a computer is often pseudo-random. It's a long list of numbers that, when put together, are random enough to fake their randomness. We start at some point in that list and start taking values. To an outside observer, they seem pretty random. But if you know the mechanism, you could actually know what values are coming ahead of time. Thus, (1) the values we generate will look mostly random, but (2) the process used to generate them is actually deterministic. This determinism has a nice side effect that we can take advantage of. If we specify a starting point for the sequence of pseudo-random numbers, we can get a reproducible list of the not-so-random values. When we use random_state, we are setting a starting point for ShuffleSplit to use when it asks for randomness. We'll end up getting the same outputs. Repeatable train-test splitting is very useful for creating reproducible test cases, sharing examples with students, and eliminating some degrees of freedom when chasing down bugs.

While we're at it, here's another place where a similar issue comes up. Let's do two separate runs of KFold.

```
In [28]:

train, test = 0, 1
kf = skms.KFold(5)
next(kf.split(diabetes.data))[train][:10]
```

```
Out[28]:

array([89, 90, 91, 92, 93, 94, 95, 96, 97, 98])
```

```
In [29]:

kf = skms.KFold(5)
next(kf.split(diabetes.data))[train][:10]
```

Out[29]:

```
array([89, 90, 91, 92, 93, 94, 95, 96, 97, 98])
```

The lack of randomness, in places we want randomness, is starting to get a little old. The issue here is the default parameters to KFold:

```
skms.KFold(n_splits=3, shuffle=False, random_state=None)
```

shuffle=False, the default, means that we don't shake up the examples before distributing them to different folds. If we want them shaken up, we need to say so. To keep the examples a bit more readable, we'll switch back to the simple pet targets.

In [30]:

```
pet = np.array(['cat', 'dog', 'cat',
    'dog', 'dog', 'dog'])

kf = skms.KFold(3, shuffle=True)

train, test = 0, 1
split_1_group_1 = next(kf.split(pet))[train]
split_2_group_1 = next(kf.split(pet))[train]

print(split_1_group_1,
    split_2_group_1)
```

[0 1 4 5] [0 1 3 5]

If we set a random_state, it's shared by the splitters:

In [31]:

```
kf = skms.KFold(3, shuffle=True, random_state=42)

split_1_group_1 = next(kf.split(pet))[train]
split_2_group_1 = next(kf.split(pet))[train]
print(split_1_group_1,
    split_2_group_1)
```

[2 3 4 5] [2 3 4 5]

### 5.5.5 Leave-One-Out Cross-Validation

I mentioned above that we could take an extreme approach to cross-validation and use as many cross-validation buckets as we have examples. So, with 20 examples, we could potentially make 20 train-test splits, do 20 training fits, do 20 testing rounds, and get 20

resulting evaluations. This version of CV is called *leave-one-out cross-validation* (LOOCV) and it is interesting because *all* of the models we generate are going to have *almost all* of their training data in common. With 20 examples, 90% of the data is shared between any two training runs. You might refer back to Figure 5.7 to see it visually.

```
In [32]:
linreg = linear_model.LinearRegression()
diabetes = datasets.load_diabetes()

loo = skms.LeaveOneOut()
scores = skms.cross_val_score(linreg,
    diabetes.data, diabetes.target,
    cv=loo,
    scoring='neg_mean_squared_error')

scores = pd.Series(np.sqrt(-scores))
df = pd.DataFrame({'RMSE':scores})
df.index.name = 'Repeat'

display(df.describe().T)

ax = sns.swarmplot(y='RMSE', data=df)
ax.set_xlabel('Over LOO\nTrain-Test Splits');
```

|  | count | mean | std | min | 25% | 50% | 75% | max |
|---|---|---|---|---|---|---|---|---|
| **RMSE** | 442.000 | 44.356 | 32.197 | 0.208 | 18.482 | 39.547 | 63.973 | 158.236 |

![](img/d94e4cd766940d79abed0bc6ba4e4344_169_0.png)

Curiously, there are three noticeable points with a high RMSE and there are about twenty points that form a distinct peak above the main body of the errors (RMSE > 100). That means there are about twenty points that are resistant to prediction with the model we are building using almost all of the data. It would be worthwhile to investigate any common factors in those difficult examples.

LOOCV is a deterministic evaluation method. There’s no randomness in the selection because everything is used in the same way every time we run LOOCV. This determinism can be useful for comparing and testing correctness of learning algorithms. However, it can be expensive to run LOOCV because we need to train the model once for each left-out example. Some models have mathematical tricks that can be used to drastically reduce the overhead of retraining. On the evaluation side, the net effect of incorporating lots of training data—all but one example—in every CV partition is that LOOCV gives a relatively unbiased estimate of the real error rate. Because the single-example predictions are so closely related—most of the training data is shared and piped into the same learning algorithm—the estimates of our performance error on new examples can vary widely. Overall, a general recommendation is to prefer 5- or 10-fold CV to LOOCV.

## 5.6 Break-It-Down: Deconstructing Error into Bias and Variance

Let’s imagine that we are at a race track and we start taking some basic measurements. We see cars zooming around the track and we measure where the cars are at and how fast they are going. Let’s say we record two lap times for a total distance d = 2. We’ll also record an average speed s. If I have a table of these values and I don’t remember any high-school physics, I can start trying to relate the different columns together. For example, from the two times and the total time I might come up with the fact that t₁ + t₂ = t_total. Again, imagine we forgot everything we learned in high-school physics or maybe even fourth-grade math.

| Driver | t₁ | t₂ | t_total | s | d |
|---|---|---|---|---|---|
| Mario | 35 | 75 | 110 | .018 | 2 |
| Luigi | 20 | 40 | 60 | .033 | 2 |
| Yoshi | 40 | 50 | 90 | .022 | 2 |

Let’s consider some variations in trying to relate the columns. First, are the measurements perfect or are there errors in how we recorded them? Second, what relationships—what mathematical operations—am I allowed to use to relate the columns? To keep things under control, we’ll limit ourselves to two simple operations, addition and multiplication, and see what happens with them. Lastly, we’ll consider relationships between different sets of columns as inputs and outputs.

In Table 5.2, I’ve laid out the different possibilities and some assessments of how perfectly they can describe the data and what goes wrong.
