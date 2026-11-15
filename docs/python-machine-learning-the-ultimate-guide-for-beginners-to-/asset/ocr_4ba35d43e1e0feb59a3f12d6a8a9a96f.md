Now let's see an example on how to apply linear regression using Scikit-learn and an open source dataset. We will use the Scikit library because it contains a number of machine learning specific algorithms, as well as certain public datasets. One such dataset is the Boston housing market dataset, which is well-documented and clean. In order to use linear regression efficiently, we will divide the whole set into a training set (80%) and a testing set (20%). Let's get to work:

```
from sklearn.datasets import load_boston
boston = load_boston()
from sklearn.cross_validation import train_test_split
X_train, X_test, Y_train, Y_test = train_test_split(boston.data,
boston.target, test_size=0.2, random_state=0)
```

As you can see, the Python code is easy to read and quite understandable without much explanation. We have imported our dataset and have performed a split in order to obtain a training set and a test set. The splitting function is a perfect example of the tools that the Scikit-learn library contains. You will notice that we have declared the percentages by stating the target test dataset should have a value of 0.2. This means that it will contain 20% of the data. Furthermore, we have a random state parameter which is needed to define the value which will handle the random number generating during the split. Basically, it randomly selects the data that will be categorized as training data or testing data.

In the next phase, we need to apply a regressor in order for our linear regression algorithm to make an accurate prediction. Once it's implemented all we need to do is measure the results to see how it performed. Keep in mind that there are many factors that can influence the accuracy, such as random errors, mislabeled data, outliers, noise, and so on. That is why the pre-processing you perform is rarely enough, and you will have to apply other algorithms to improve the result. This is something you need to keep in mind for the near future when you practice on your own. Now let's see our regressor and the results we obtain: