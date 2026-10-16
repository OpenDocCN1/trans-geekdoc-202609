I don’t want to get into too many details of too many tasks here. Still, there is one complication I feel compelled to introduce. Many presentations of learning start off using a teach-to-the-test evaluation scheme called *in-sample evaluation* or *training error*. These have their uses. However, not teaching to the test is such an important concept in learning systems that *I refuse to start you off on the wrong foot!* We just can’t take an easy way out. We are going to put our big girl and big boy pants and do this like adults with a real, *out-of-sample* or test error evaluation. We can use these as an estimate for our ability to generalize to unseen, future examples.

Fortunately, `sklearn` gives us some support here. We’re going to use a tool from `sklearn` to avoid teaching to the test. The `train_test_split` function segments our dataset that lives in the Python variable `iris`. Remember, that dataset has two components already: the *features* and the *target*. Our new segmentation is going to split it into two buckets of examples:

+   1. A portion of the data that we will use to study and build up our understanding and
+   2. A portion of the data that we will use to test ourselves.

We will only study—that is, learn from—the *training* data. To keep ourselves honest, we will only evaluate ourselves on the *testing* data. We promise not to peek at the testing data. We started by breaking our dataset into two parts: features and target. Now, we’re breaking each of those into two pieces:

+   1. Features → training features and testing features
+   2. Targets → training targets and testing targets

We’ll get into more details about `train_test_split` later. Here’s what a basic call looks like:

```
```python
In [5]:
# simple train-test split
(iris_train_ftrs, iris_test_ftrs,
 iris_train_tgt, iris_test_tgt) = skms.train_test_split(iris.data,
                                                       iris.target,
                                                       test_size=.25)
print("Train features shape:", iris_train_ftrs.shape)
print("Test features shape:", iris_test_ftrs.shape)
```
```

```
```text
Train features shape: (112, 4)
Test features shape: (38, 4)
```
```

So, our training data has 112 examples described by four features. Our testing data has 38 examples described by the same four attributes.

If you’re confused about the two splits, check out Figure 3.3. Imagine we have a box drawn around a table of our total data. We identify a special column and put that special column on the right-hand side. We draw a vertical line that separates that rightmost column from the rest of the data. That vertical line is the split between our predictive