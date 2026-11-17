First, you were introduced to the different types of features that you might have to work with.
Identifying the type of variable you’ll be working with is very important for defining the types of
transformations and techniques that can be applied to each case.

Then, you learned how to deal with categorical features. You saw that, sometimes, categorical
variables do have an order (such as the ordinal ones), while other times, they don’t (such as the
nominal ones). You learned that one-hot encoding (or dummy variables) is probably the most
common type of transformation for nominal features; however, depending on the number of unique
categories, after applying one-hot encoding, your data might suffer from sparsity issues. Regarding
ordinal features, you shouldn’t create dummy variables on top of them, since you would be losing the
information about the order that has been incorporated into the variable. In those cases, ordinal
encoding is the most appropriate transformation.

You continued your journey by looking at numerical features, where you learned how to deal with
continuous and discrete data. You walked through the most important types of transformations, such
as normalization, standardization, binning, and discretization. You saw that some types of
transformation rely on the underlying data to find their parameters, so it is very important to avoid
using the testing set to learn anything from the data (it must strictly be used only for testing).

You have also seen that you can even apply pure math to transform your data; for example, you
learned that power transformations can be used to reduce the skewness of your feature and make it
more similar to a normal distribution.

After that, you looked at missing data and got a sense of how important this task is. When you are
modeling, you can’t look at the missing values as a simple computational problem, where you just
have to replace x with y. This is a much bigger problem, and you need to start solving it by exploring
your data and then checking whether your missing data was generated at random or not.

When you are making the decision to remove or replace missing data, you must be aware that you are
either losing information or adding bias to the dataset, respectively. Remember to review all the
important notes of this chapter, since they are likely to be relevant to your exam.

You also learned about outlier detection. You looked at different ways to find outliers, such as the
zscore and box plot approaches. Most importantly, you learned that you can either flag or smooth
them.

At the beginning, you were advised that this chapter would be a long but worthwhile journey about
data preparation. You have also learned how to deal with rare events, since this is one of the most
challenging problems in ML. Now you are aware that, sometimes, your data might be unbalanced,