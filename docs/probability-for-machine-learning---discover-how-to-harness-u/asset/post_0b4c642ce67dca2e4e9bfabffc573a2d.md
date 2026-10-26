
## 23.7 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

### 23.7.1 Books

- *Machine Learning: A Probabilistic Perspective*, 2012.
  https://amzn.to/2xKSTCP
- *Pattern Recognition and Machine Learning*, 2006.
  https://amzn.to/2JwHE7I
- *Deep Learning*, 2016.
  https://amzn.to/21nc3vL

### 23.7.2 API

- Usage of loss functions, Keras API.
  https://keras.io/losses/
- sklearn.metrics.log_loss API.
  https://scikit-learn.org/stable/modules/generated/sklearn.metrics.log_loss.html

### 23.7.3 Articles

- Kullback-Leibler divergence, Wikipedia.
  https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence
- Cross entropy, Wikipedia.
  https://en.wikipedia.org/wiki/Cross_entropy
- Joint Entropy, Wikipedia.
  https://en.wikipedia.org/wiki/Joint_entropy
- Loss functions for classification, Wikipedia.
  https://en.wikipedia.org/wiki/Loss_functions_for_classification

## 23.8 Summary

In this tutorial, you discovered cross-entropy for machine learning. Specifically, you learned:

- How to calculate cross-entropy from scratch and using standard machine learning libraries.
- Cross-entropy can be used as a loss function when optimizing classification models like logistic regression and artificial neural networks.
- Cross-entropy is different from KL divergence but can be calculated using KL divergence, and is different from log loss but calculates the same quantity when used as a loss function.

### 23.8.1 Next

In the next tutorial, you will discover information gain and mutual information between two probability distributions.

## 24.2 What Is Information Gain?

Information Gain, or IG for short, measures the reduction in entropy or surprise by splitting a dataset according to a given value of a random variable. A larger information gain suggests a lower entropy group or groups of samples, and hence less surprise. You might recall that information quantifies how surprising an event is in bits. Lower probability events have more information, higher probability events have less information. Entropy quantifies how much information there is in a random variable, or more specifically its probability distribution. A skewed distribution has a low entropy, whereas a distribution where events have equal probability has a larger entropy.

In information theory, we like to describe the *surprise* of an event. Low probability events are more surprising therefore have a larger amount of information. Whereas probability distributions where the events are equally likely are more surprising and have larger entropy.

- **Skewed Probability Distribution** (*unsurprising*): Low entropy.
- **Balanced Probability Distribution** (*surprising*): High entropy.

Now, let’s consider the entropy of a dataset. We can think about the entropy of a dataset in terms of the probability distribution of observations in the dataset belonging to one class or another, e.g. two classes in the case of a binary classification dataset.

> > One interpretation of entropy from information theory is that it specifies the minimum number of bits of information needed to encode the classification of an arbitrary member of $S$ (i.e., a member of $S$ drawn at random with uniform probability).
> >
> > — Page 58, *Machine Learning*, 1997.

For example, in a binary classification problem (two classes), we can calculate the entropy of the data sample as follows:

$$Entropy = -(p(0) \times \log(P(0)) + p(1) \times \log(P(1))) \tag{24.1}$$

A dataset with a 50/50 split of samples for the two classes would have a maximum entropy (maximum surprise) of 1 bit, whereas an imbalanced dataset with a split of 10/90 would have a smaller entropy as there would be less surprise for a randomly drawn example from the dataset. We can demonstrate this with an example of calculating the entropy for this imbalanced dataset in Python. The complete example is listed below.

```python
# calculate the entropy for a dataset
from math import log2
# proportion of examples in each class
class0 = 10/100
class1 = 90/100
# calculate entropy
entropy = -(class0 * log2(class0) + class1 * log2(class1))
# print the result
print('entropy: %.3f bits' % entropy)
```

Listing 24.1: Example of calculating entropy.

Running the example, we can see that entropy of the dataset for binary classification is less than 1 bit. That is, less than one bit of information is required to encode the class label for an arbitrary example from the dataset.

```
entropy: 0.469 bits
```

Listing 24.2: Example output from calculating entropy.

In this way, entropy can be used as a calculation of the purity of a dataset, e.g. how balanced the distribution of classes happens to be. An entropy of 0 bits indicates a dataset containing one class; an entropy of 1 or more bits suggests maximum entropy for a balanced dataset (depending on the number of classes), with values in between indicating levels between these extremes. Information gain provides a way to use entropy to calculate how a change to the dataset impacts the purity of the dataset, e.g. the distribution of classes. A smaller entropy suggests more purity or less surprise.

> > ... information gain, is simply the expected reduction in entropy caused by partitioning the examples according to this attribute.
> 
> — Page 57, *Machine Learning*, 1997.

For example, we may wish to evaluate the impact on purity by splitting a dataset S by a random variable with a range of values. This can be calculated as follows:

$IG(S, a) = H(S) - H(S|a)$
(24.2)

Where $IG(S, a)$ is the information for the dataset $S$ for the variable $a$ for a random variable, $H(S)$ is the entropy for the dataset before any change (described above) and $H(S|a)$ is the conditional entropy for the dataset given the variable $a$. This calculation describes the gain in the dataset $S$ for the variable $a$. It is the number of bits saved when transforming the dataset. The conditional entropy can be calculated by splitting the dataset into groups for each observed value of $a$ and calculating the sum of the ratio of examples in each group out of the entire dataset multiplied by the entropy of each group.

$H(S|a) = \sum_{\{v\in a\}} \frac{Sa(v)}{S} \times H(Sa(v))$
(24.3)

Where $\frac{Sa(v)}{S}$ is the ratio of the number of examples in the dataset with variable $a$ has the value $v$, and $H(Sa(v))$ is the entropy of group of samples where variable $a$ has the value $v$. This might sound a little confusing. We can make the calculation of information gain concrete with a worked example.

## 24.3 Worked Example of Calculating Information Gain

In this section, we will make the calculation of information gain concrete with a worked example. We can define a function to calculate the entropy of a group of samples based on the ratio of samples that belong to class 0 and class 1.

```
# calculate the entropy for the split in the dataset
def entropy(class0, class1):
    return -(class0 * log2(class0) + class1 * log2(class1))
```

Listing 24.3: Example of defining a function for calculating entropy.

Now, consider a dataset with 20 examples, 13 for class 0 and 7 for class 1. We can calculate the entropy for this dataset, which will have less than 1 bit.

```
...
# split of the main dataset
class0 = 13 / 20
class1 = 7 / 20
# calculate entropy before the change
s_entropy = entropy(class0, class1)
print('Dataset Entropy: %.3f bits' % s_entropy)
```

Listing 24.4: Example of calculating the entropy for the dataset.

Now consider that one of the variables in the dataset has two unique values, say value1 and value2. We are interested in calculating the information gain of this variable. Let’s assume that if we split the dataset by value1, we have a group of eight samples, seven for class 0 and one for class 1. We can then calculate the entropy of this group of samples.

```
...
# split 1 (split via value1)
s1_class0 = 7 / 8
s1_class1 = 1 / 8
# calculate the entropy of the first group
s1_entropy = entropy(s1_class0, s1_class1)
print('Group1 Entropy: %.3f bits' % s1_entropy)
```

Listing 24.5: Example of calculating the entropy for split 1.

Now, let’s assume that we split the dataset by value2; we have a group of 12 samples with six in each group. We would expect this group to have an entropy of 1.

```
...
# split 2 (split via value2)
s2_class0 = 6 / 12
s2_class1 = 6 / 12
# calculate the entropy of the second group
s2_entropy = entropy(s2_class0, s2_class1)
print('Group2 Entropy: %.3f bits' % s2_entropy)
```

Listing 24.6: Example of calculating the entropy for split 2.

Finally, we can calculate the information gain for this variable based on the groups created for each value of the variable and the calculated entropy. The first variable resulted in a group of eight examples from the dataset, and the second group had the remaining 12 samples in the data set. Therefore, we have everything we need to calculate the information gain. In this case, information gain can be calculated as:

H(Dataset) − Count(Group1)/Count(Dataset) × H(Group1) + Count(Group2)/Count(Dataset) × H(Group2) (24.4)
