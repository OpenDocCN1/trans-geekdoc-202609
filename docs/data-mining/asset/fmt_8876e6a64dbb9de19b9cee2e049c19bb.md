
### [Remarks](#Ch004_91-164_B9780443158889000054.xhtml#s0035) 105

## 4.3 Divide-and-Conquer: Constructing Decision Trees [106](#Ch004_91-164_B9780443158889000054.xhtml#s0040)
### [Calculating Information](#Ch004_91-164_B9780443158889000054.xhtml#s0045) 108
### [Highly Branching Attributes](#Ch004_91-164_B9780443158889000054_a.xhtml#s0050) 111

## 4.4 Covering Algorithms: Constructing Rules [114](#Ch004_91-164_B9780443158889000054_a.xhtml#s0055)
### [Rules Vs. Trees](#Ch004_91-164_B9780443158889000054_a.xhtml#s0060) 115
### [A Simple Covering Algorithm](#Ch004_91-164_B9780443158889000054_a.xhtml#s0065) 115
### [Rules Vs. Decision Lists](#Ch004_91-164_B9780443158889000054_a.xhtml#s0070) 119

## 4.5 Mining Association Rules [120](#Ch004_91-164_B9780443158889000054_a.xhtml#s0075)
### [Item Sets](#Ch004_91-164_B9780443158889000054_a.xhtml#s0080) 121
### [Association Rules](#Ch004_91-164_B9780443158889000054_a.xhtml#s0085) 121
### [Generating Rules Efficiently](#Ch004_91-164_B9780443158889000054_a.xhtml#s0090) 123

## 4.6 Linear Models [128](#Ch004_91-164_B9780443158889000054_a.xhtml#s0095)
### [Numeric Prediction: Linear Regression](#Ch004_91-164_B9780443158889000054_a.xhtml#s0100) 129
### [Linear Classification: Logistic Regression](#Ch004_91-164_B9780443158889000054_a.xhtml#s0105) 130
### [Linear Classification Using the Perceptron](#Ch004_91-164_B9780443158889000054_a.xhtml#s0110) 132
### [Linear Classification Using Winnow](#Ch004_91-164_B9780443158889000054_a.xhtml#s0115) 134

## 4.7 Instance-Based Learning [136](#Ch004_91-164_B9780443158889000054_a.xhtml#s0120)
### [The Distance Function](#Ch004_91-164_B9780443158889000054_a.xhtml#s0125) 136
### [Finding Nearest Neighbors Efficiently](#Ch004_91-164_B9780443158889000054_a.xhtml#s0130) 137
### [Remarks](#Ch004_91-164_B9780443158889000054_a.xhtml#s0135) 142

## 4.8 Clustering [142](#Ch004_91-164_B9780443158889000054_a.xhtml#s0140)
### [Iterative Distance-Based Clustering](#Ch004_91-164_B9780443158889000054_a.xhtml#s0145) 143
### [Faster Distance Calculations](#Ch004_91-164_B9780443158889000054_a.xhtml#s0150) 145
### [Choosing the Number of Clusters](#Ch004_91-164_B9780443158889000054_a.xhtml#s0155) 147
### [Hierarchical Clustering](#Ch004_91-164_B9780443158889000054_a.xhtml#s0160) 147
### [Example of Hierarchical Clustering](#Ch004_91-164_B9780443158889000054_a.xhtml#s0165) 149
### [Incremental Clustering](#Ch004_91-164_B9780443158889000054_a.xhtml#s0170) 150
### [Category Utility](#Ch004_91-164_B9780443158889000054_a.xhtml#s0175) 155
### [Remarks](#Ch004_91-164_B9780443158889000054_a.xhtml#s0180) 156

## 4.9 Multi-Instance Learning [157](#Ch004_91-164_B9780443158889000054_a.xhtml#s0185)
### [Aggregating the Input](#Ch004_91-164_B9780443158889000054_a.xhtml#s0190) 157
### [Aggregating the Output](#Ch004_91-164_B9780443158889000054_a.xhtml#s0195) 158

## 4.10 Further Reading and Bibliographic Notes [158](#Ch004_91-164_B9780443158889000054_a.xhtml#s0200)
## 4.11 Weka Implementations [161](#Ch004_91-164_B9780443158889000054_a.xhtml#s0205)
## 4.12 Exercises [161](#Ch004_91-164_B9780443158889000054_a.xhtml#s0210)

Now that we’ve seen how the inputs and outputs can be represented, it’s time to look at the learning algorithms themselves. This chapter explains the basic ideas behind the techniques that are used in practical data mining. We will not delve too deeply into the trickier issues—advanced versions of the algorithms, optimizations that are possible, and complications that arise in practice. These topics are deferred to Part II, where we come to grips with more advanced machine learning schemes and data transformations. It is important to understand these more advanced issues so that you know what is really going on when you analyze a particular dataset.

In this chapter we look at the basic ideas. One of the most instructive lessons is that simple ideas often work very well, and we strongly recommend the adoption of a “simplicity-first” methodology when analyzing practical datasets. There are many kinds of simple structure that datasets can exhibit. In one dataset, there might be a single attribute that does all the work and the others are irrelevant or redundant. In another dataset, the attributes might contribute independently and equally to the final outcome. A third might have a simple logical structure, involving just a few attributes, which can be captured by a decision tree. In a fourth, there may be a few independent rules that govern the assignment of instances to different classes. A fifth might exhibit dependencies among different subsets of attributes. A sixth might involve linear dependence among numeric attributes, where what matters is a weighted sum of attribute values with appropriately chosen weights. In a seventh, classifications appropriate to particular regions of instance space might be governed by the distances between the instances themselves. And in an eighth, it might be that no class values are provided: the learning is unsupervised.

In the infinite variety of possible datasets there are many kinds of structure that can occur, and a data mining tool, no matter how capable, looking for one class of structure may completely miss regularities of a different kind, regardless of how rudimentary those may be. The result is a baroque and opaque classification structure of one kind instead of a simple, elegant, immediately comprehensible structure of another.

Each of the eight examples of datasets sketched earlier leads to a different machine learning scheme that is well suited to discovering the underlying concept. The sections of this chapter look at each of these structures in turn. A final section introduces simple ways of dealing with multiinstance problems, where each example comprises several different instances.

## 4.1 Inferring Rudimentary Rules

Here’s an easy way to find very simple classification rules from a set of instances. Called `1 R` for `1-rule`, it generates a one-level decision tree expressed in the form of a set of rules that all test one particular attribute. `1 R` is a simple, cheap method that often comes up with quite good rules for characterizing the structure in data. It turns out that simple rules frequently achieve surprisingly high accuracy. Perhaps this is because the structure underlying many real-world datasets is quite rudimentary, and just one attribute is sufficient to determine the class of an instance quite accurately. In any event, it is always a good plan to try the simplest things first.

The idea is this: we make rules that test a single attribute and branch accordingly. Each branch corresponds to a different value of the attribute. It is obvious what is the best classification to give each branch—use the class that occurs most often in the training data. Then the error rate of the rules can easily be determined. Just count the errors that occur on the training data, that is, the number of instances that do not have the majority class.

Each attribute generates a different set of rules, one rule for every value of the attribute. Evaluate the error rate for each attribute’s rule set and choose the best. It’s that simple! [Fig. 4.1](#Ch004_91-164_B9780443158889000054.xhtml#f0010) shows the algorithm in the form of pseudocode.

![Fig. 4.1 Pseudocode for 1 R.](images/F000054f04-01-9780443158889.jpg)

[Fig. 4.1](#Ch004_91-164_B9780443158889000054.xhtml#Bf0010) Pseudocode for `1 R`.
