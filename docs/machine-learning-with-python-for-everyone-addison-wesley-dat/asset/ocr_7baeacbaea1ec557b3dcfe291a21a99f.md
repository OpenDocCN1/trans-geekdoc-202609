true weights: (-2, 20)
learned weights: [-1.2809 12.7875]

The weights are different and have gone the wrong way. However, I simply picked our tradeoff between prediction accuracy and complexity C out of a hat. We shouldn't therefore read too much into this: it's a very simple dataset, there aren't too many data points, and we only tried one value of C. Can you find a better C?

# 15.3.2 Logistic Regression with Plus-One Minus-One Coding

Before we leave logistic regression, let's add one last twist. Conceptually, there shouldn't be any difference between having classes that are cat and dog, or donkey and elephant, or zero and one, or +one and -one. We just happened to use 0/1 above because it played well with the binomial data generator we used to flip coins. In reality, there are nice mathematical reasons behind that as well. We'll ignore those for now.

Since the mathematics for some other learning models can be more convenient using -1/+1, let's take a quick look at logistic regression with ±1. The only difference is that we need a slightly different loss function. Before we get to that, however, let's make a helper to deal with converting 01 data to ±1 data.

In [17]:

```
def binary_to_pm1(b):
    ' map {0,1} or {False,True} to {-1, +1} '
    return (b*2)-1
binary_to_pm1(0), binary_to_pm1(1)
```

Out[17]:

```
(-1, 1)
```

Here, we'll update the loss function to work with the ±1 data. Mathematically, we start with the same log loss expression we had above, work through some slightly different algebra using the ±1 values, and get the logreg_loss_pm1. The two logreg_loss functions are just slightly different code expressions of the same mathematical idea.

In [18]:

```
# for logistic regression
def logreg_model(weights, ftrs):
    return rdot(weights, ftrs)

def logreg_loss_pm1(predicted, actual):
    # -actual log(predicted) - (1-actual) log(1-predicted)
```