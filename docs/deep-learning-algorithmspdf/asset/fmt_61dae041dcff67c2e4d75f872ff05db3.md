
# result, Õ # < #

i

(36)

where,

category y with the maximum,

'

indicates

category y and combines with the voting weight w

i

**Figure 6**~ \`~?|

本书版权归Arcler所有

![Image 1526](index-341_1.jpg)

![Image 1527](index-341_2.png)

![Image 1528](index-341_3.jpg)

![Image 1529](index-341_4.png)

![Image 1530](index-341_5.png)

![Image 1531](index-341_6.png)

![Image 1532](index-341_7.png)

Hierarchical Representations Feature Deep Learning for Face Recognition 315

**DESIGNING THE CLASSIFIER COMBINING**

**UNSUPERVISED AND SUPERVISED LEARNING**

Supervised learning systems are domain-specific and annotating a large-scale corpus for each domain is very expensive \[46\]. Recently, semi-supervised learning, which uses a large amount of unlabeled data together with labeled data to build better learners, has attracted more and more attention in pattern recognition and classification \[47\]. In the paper we design a novel classifier of semi-supervised learning, namely combining Ç # #

with Softmax regress (DBNESR) for FR. DBNESR first learns hierarchical representations of feature by greedy layer-wise unsupervised learning in a feed-forward (bottom-up) and back-forward (top-down) manner \[48\] and then makes more efficient classification with Softmax regress by supervised learning. Deep belief network (DBN) is a representative deep learning algorithm, has deep architecture that is composed of multiple levels of nonlinear operations \[49\], which is expected to perform well in semi-supervised learning, because of its capability of modeling hard artificial intelligent tasks \[50\]. Softmax regression is a generalization of the logistic regression in many classification problems.

***1)***

***Problem formulation:-*** The dataset is represented as a matrix: (37)

where, N is the number of training samples, M is the number of test samples, D is the number of feature values in the dataset. Each column of X

corresponds to a sample X. A sample which has all features is viewed as a vector in

, where the jth coordinate corresponds to the jth feature.

Let Y be a set of labels correspond to L labeled training samples and is denoted as:

(38)

where, C is the number of classes. Each column of Y is a vector in

,

where, the jth coordinate corresponds to the jth class: 本书版权归Arcler所有

![Image 1533](index-342_1.jpg)

![Image 1534](index-342_2.png)

![Image 1535](index-342_3.jpg)

![Image 1536](index-342_4.jpg)

![Image 1537](index-342_5.jpg)

![Image 1538](index-342_6.jpg)

![Image 1539](index-342_7.jpg)

![Image 1540](index-342_8.png)

![Image 1541](index-342_9.jpg)

![Image 1542](index-342_10.jpg)

![Image 1543](index-342_11.jpg)

![Image 1544](index-342_12.png)

![Image 1545](index-342_13.png)

![Image 1546](index-342_14.png)

Deep Learning Algorithms

316

(39)

We intend to seek the mapping function

using all the samples in

order to determine Y when a new X comes.

***2)***

***Softmax regression:-*** Softmax regression is a generalization

\# {

##

. The hypothesis function is as following:

(40)

Training model parameters vector

, which can minimize the cost

function:

(41)

Softmax regression #

. It is used for each given sample X, using hypothesis function to estimate the probability value

for each category j. The hypothesis

function is as following:

(42)

where,

denote model parameters vector, the cost function is

as following:

(43)

where, 1{ڄ} denotes:

1 {The value of expression is true} = 1 or 1 {The value of expression is false}

\=

0

(44)

本书版权归Arcler所有

![Image 1547](index-343_1.jpg)

![Image 1548](index-343_2.jpg)

![Image 1549](index-343_3.jpg)

![Image 1550](index-343_4.jpg)

![Image 1551](index-343_5.jpg)

![Image 1552](index-343_6.png)

![Image 1553](index-343_7.png)

![Image 1554](index-343_8.png)

Hierarchical Representations Feature Deep Learning for Face Recognition 317

There are no closed form solutions to minimize the cost function Equation (43) at present. Therefore, we use the iterative optimization algorithm (for example, gradient descent method or L-BFGS). After derivation we get gradient formula is as following:

(45)

Then make the following update operation:

(46)

***3)***

***Deep belief network embedded with Softmax regress (DBNESR):-***

~ !~

(RBM) \[52\] \[53\] of unsupervised learning networks as building blocks for the multi-layer learning systems and uses a supervised

\`#| +

after pre-training. Its architecture is shown in Figure 7. The deep architecture is a fully interconnected directed belief nets with one input layer

hidden layers

and one

labeled layer at the top. The input layer v1 has D units, equal to the number of features of samples. The label layer has C units, equal to the number of classes of label vector Y. The numbers of

+

the experience or intuition. The seeking of the mapping function,

#

for the deep architecture \[54\].

The semi-supervised learning method based on DBN architecture can be divided into two stages: First, DBN architecture is constructed by greedy layer-wise unsupervised learning using

~ # # !

parameter space W with N layers. Second, DBN architecture is trained according to the log-likelihood using gradient descent

!

supervised learning directly, the unsupervised learning stage can abstract the hierarchical representations feature effectively, and

\+ <

\+ + +

本书版权归Arcler所有

![Image 1555](index-344_1.jpg)

![Image 1556](index-344_2.jpg)

![Image 1557](index-344_3.jpg)

![Image 1558](index-344_4.jpg)

![Image 1559](index-344_5.png)

![Image 1560](index-344_6.png)

![Image 1561](index-344_7.jpg)

![Image 1562](index-344_8.jpg)

![Image 1563](index-344_9.png)

![Image 1564](index-344_10.png)

![Image 1565](index-344_11.png)

![Image 1566](index-344_12.png)

Deep Learning Algorithms

318

**Figure 7**. Architecture of deep belief network embedded with Softmax regress (DBNESR).

? "

as \[50\]:

(47)

where,

are the model parameters:

is the symmetric

interaction term between unit i in the layer

and unit j in the layer hk ,

is the ith bias of layer

is the jth bias of layer

is the number of units in the kth layer. The network assigns a probability to every possible data via this energy function. The probability of a training data can be raised by adjusting the weights and biases to lower the energy of 本书版权归Arcler所有

![Image 1567](index-345_1.png)

![Image 1568](index-345_2.png)

![Image 1569](index-345_3.png)

![Image 1570](index-345_4.jpg)

![Image 1571](index-345_5.jpg)

![Image 1572](index-345_6.jpg)

![Image 1573](index-345_7.jpg)

![Image 1574](index-345_8.jpg)

![Image 1575](index-345_9.png)

![Image 1576](index-345_10.png)

![Image 1577](index-345_11.jpg)

![Image 1578](index-345_12.png)

![Image 1579](index-345_13.jpg)

![Image 1580](index-345_14.jpg)

![Image 1581](index-345_15.jpg)

![Image 1582](index-345_16.png)

![Image 1583](index-345_17.jpg)

![Image 1584](index-345_18.png)

![Image 1585](index-345_19.jpg)

![Image 1586](index-345_20.png)

![Image 1587](index-345_21.png)

![Image 1588](index-345_22.png)

![Image 1589](index-345_23.png)

![Image 1590](index-345_24.png)

Hierarchical Representations Feature Deep Learning for Face Recognition 319

that data and to raise the energy of similar, confabulated data that would prefer to the real data. When we input the value of

, the network can learn

the content of

by minimizing this energy function.

(48)

(49)

°\`| ! <

distributions over

are given as:

(50)

(51)

The probability of turning unit j is a logistic function of the states and

:

(52)

The probability of turning unit i is a logistic function of the states of hk and

:

(53)

where, the logistic function been chosen is the sigmoid function: (54)

The derivative of the log-likelihood with respect to the model parameter wk can be obtained from Equation (48):

(55)

where,

denotes an expectation with respect to the data distribution and Model

' #

by the model \[55\]. The expectation

cannot be computed analytically. In

practice,
