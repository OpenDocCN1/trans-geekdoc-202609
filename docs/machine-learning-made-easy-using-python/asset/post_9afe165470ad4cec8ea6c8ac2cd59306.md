
In [4]: from sklearn import preprocessing
Input = preprocessing.scale(dt.drop(columns='Rainfall')).values
Output = dt['Rainfall']
inp_X, tst_X, out_y, tst_y = train_test_split(
Input, Output, test_size=0.2)
CModel = linear_model.LogisticRegression()
CModel.fit(inp_X, out_y)

Out[4]: LogisticRegression()

Our model is trained. Now we can test model’s predictions with actual values. To visualize it we need to use the LabelEncoder and encode the Rainfall labels into numeric values. We will also print the accuracy of our model

Accuracy: 0.4315690860872

Out[5]: <matplotlib.axes.AxesSubplot object at 0x239fe07>

![](img/d75fea3635f5553f1cb0585b399b1b4b_156_0.png)

so our model didn’t perform well. So here’s a question for you - why is the accuracy of our model is below 50%? (without reading further)

So what do you think? Is it because we scaled the data? Yes, you are obviously wrong. The scaling wasn’t necessary but it was included to lure you to think that it would’ve been the reason that’s not it. Instead it is a good practice to do so. The actual reason is the distribution in the data. If you observe the plotted graph of the predicted and actual values

![](img/d75fea3635f5553f1cb0585b399b1b4b_157_0.png)

you’ll notice that the distribution is really different. Our dataset has a spike i.e. less ‘high rainfall’ data only concentrated at one place and no low rainfall a lot. We provided our model with 18000 rows of data but the distribution wasn’t good i.e. we didn’t get enough data for moderate or high rainfall. The places where the lines are overlapping are the predictions made by our model i.e. mostly rainfall and low rainfall. Our model didn’t predict moderate or high rainfall for any value at all. Encountering errors like this helps us counter problems in actual situations. During this time we need to come up with different methods to improve our model (that will be covered in Performance and metrics lesson) or change the algorithm, let’s look at another classification

## Naive Bayes

Naive Bayes algorithm is based on the Bayes theorem which we learned in previous lessons. We have three types of Naive Bayes algorithms:

- Gaussian is used when data labels is drawn from gaussian distribution
- Multinomial is used when data labels is drawn from multinomial distribution
- Bernoulli is used when we have to predict binary features like 0 or 1

So let's use the naive Bayes algorithm to create model to predict whether it will rain or not with the dataset used in logistic regression. We will use Naive Bayes algorithm for this model

| | |
|---|---|
| [1]: import pandas | |
| from sklearn import naive_bayes, metrics | |
| from sklearn.preprocessing import LabelEncoder | |
| from sklearn.model_selection import train_test_split | |
| dt = pandas.read_csv('Rainfall.csv') | |

This time we imported naive_bayes from sklearn to create our model and LabelEncoder to encode the labels while comparing the predictions. Next we can split into training input, testing input, training output and testing output respectively using the train_test_split() and the test_size as 0.1

```
[2]: Input = dt.drop(columns=['Unnamed: 0'])
Output = dt['Rain']
inp_X, test_X, out_y, test_y = train_test_split(
Input, Output, test_size=0.1)
```

We now create our model, we will use the GaussianNB class from naive_bayes and train it with the fit() method

In [3]: Input = dt.drop(columns=['Unnamed: 0'])
Output = dt['Rain']
inp_X, test_X, out_y, test_y = train_test_split(
Input, Output, test_size=0.1)
CModel = naive_bayes.GaussianNB()
CModel.fit(inp_X, out_y)

Out[3]: GaussianNB()

CModel is ready to predict. So let's test our model with the predict() method and compare the answers using the density plot. We will also print the accuracy score

```
In [4]: pred_y = CModel.predict(test_X)
Enc = LabelEncoder().fit(['Yes', 'No'])
cmp = pandas.DataFrame({'Predicted':Enc.transform(pred_y),
'Actual':Enc.transform(test_y)})
acc = metrics.accuracy_score(test_y, pred_y)
print('Accuracy: ',acc)
cmp.plot(kind='density')
```

Accuracy: 0.9275

Out[4]: <matplotlib.axes.AxesSubplot object at 0x26a130ee

![](img/d75fea3635f5553f1cb0585b399b1b4b_159_0.png)

The model has an accuracy of 92% i.e. the predicted line and the actual line in the graph is almost overlapping each other. Our naive Bayes model has performed well than the logistic regression model by 1%

## SUPPORT VECTOR MACHINE

- What is SVM
- SVM Models
- SVM Kernels

![](img/d75fea3635f5553f1cb0585b399b1b4b_160_0.png)

## SUPPORT VECTOR MACHINES

### What is Support Vector Machine

Support vector machines or SVM is case of supervised machine learning which is used for both regressions and classifications. But the working of the SVMs can be considered a bit different. In SVM algorithms divides a dataset into different classes or categories in a hyperplane in multidimensional space. The categories are divided in a manner to find the maximum marginal hyperplanes or MMH. These hyperplanes are generated in an iterative manner to minimize errors

![](img/d75fea3635f5553f1cb0585b399b1b4b_161_0.png)

In the above graph, the data points closest to the hyperplane are called support vectors. The line separating the class A and class B is the line called hyperplane i.e. dividing the data into two class

And for the line called margin is the gap between two lines on the closest data points of different classes. It can be calculated as the perpendicular distance from the line to the support vectors. Large margin is considered as a good margin and small margin is considered as a bad margin. The SVM algorithms find the maximum marginal hyperplane to divide the datapoints into different classes

## Support Vector Machine models

We can create our own SVM model using sample datasets, so jump into your jupyter notebook and import the following modules:

```
import numpy
from matplotlib import pyplot
import seaborn
from sklearn.datasets.samples_generator import
import make_blobs
```

In [1]: import numpy
from matplotlib import pyplot
import seaborn
from sklearn.datasets.samples_generator import make_blobs

We will use numpy, matplotlib and seaborn to visualize the data.

In [2]: X, y = make_blobs(n_samples=100, centers=2, cluster_std=0.5)

Using the make_blobs() function we created a dataset with 100 samples (data points) specified in the n_samples parameter, that's why we passed 2 to the centers parameter

![](img/d75fea3635f5553f1cb0585b399b1b4b_162_0.png)

and finally the standard deviation of the cluster as 0.5 i.e. specified in the cluster_std parameter
