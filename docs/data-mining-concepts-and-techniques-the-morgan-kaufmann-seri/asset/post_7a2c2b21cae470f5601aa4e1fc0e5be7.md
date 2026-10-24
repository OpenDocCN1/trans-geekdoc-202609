
![](img/90c930779c8f928df6ff4481fc59f9a3_278_0.png)

FIGURE 6.5
A regression tree for predicting the average yearly income based on an individual’s education. The values of the three leaf nodes are calculated as follows. $50K is the average yearly income of all training individuals who do not have a college degree; $60K is the average yearly income of all training individuals who have a college degree with a GPA less than or equal to 3.5; and $100K is the average yearly income of all training individuals who have a college degree with a GPA higher than 3.5. The leaf node values ($50K, $60K, and $100K) are used to predict the yearly income of any test individual who falls into the corresponding leaf nodes.

categorical value (i.e., class label) in a decision tree. The continuous value of a leaf node is learned during the training phase, which is set as the average output value of all training tuples fallen in the corresponding subregions. CART uses residual sum of squares (RSS) as the objective function, which is the sum of the squared difference between the actual and predicted output values of training tuples

RSS = \(\sum_i (y_i - \hat{y}_i)^2\), (6.1)

where \(y_i\) is the actual output value of the \(i\)th training tuple, and \(\hat{y}_i\) is the predicted output by the regression tree. Choosing the average output of all training tuples in the corresponding subregion is optimal in that it minimizes the RSS in Eq. (6.1). Each leaf node value is then used to predict the output of a test tuple which falls into it. Fig. 6.5 presents an example of a regression tree for predicting the average yearly income based on an individual’s education (e.g., whether or not the individual attended the college, the average GPA at college, etc.).

## 6.2.2 Attribute selection measures

An attribute selection measure is a heuristic for selecting the splitting criterion that “best” separates a given data partition, \(D\), of class-labeled training tuples into individual classes. If we were to split \(D\) into smaller partitions according to the outcomes of the splitting criterion, ideally, each partition would be pure (i.e., all the tuples that fall into a given partition would belong to the same class). Conceptually, the “best” splitting criterion is the one that most closely results in such a scenario. Attribute selection measures are also known as splitting rules because they determine how the tuples at a given node are to be split.

The attribute selection measure provides a ranking for each attribute describing the given training tuples. The attribute having the best score for the measure$^4$ is chosen as the *splitting attribute* for the given tuples. If the splitting attribute is continuous-valued or if we are restricted to binary trees, then, respectively, either a *split point* or a *splitting subset* must also be determined as part of the splitting criterion. The tree node created for partition $D$ is labeled with the splitting criterion, branches are grown for each outcome of the criterion, and the tuples are partitioned accordingly. This section describes three popular attribute selection measures—information gain, gain ratio, and Gini impurity.

The notation used herein is as follows. Let $D$, the data partition, be a training set of class-labeled tuples. Suppose the class label attribute has $m$ distinct values defining $m$ distinct classes, $C_i$ (for \(i = 1, ..., m\)). Let $C_{i,D}$ be the set of tuples of class $C_i$ in $D$. Let $|D|$ and $|C_{i,D}|$ denote the number of tuples in $D$ and $C_{i,D}$, respectively.

### Information gain

ID3 uses **information gain** as its attribute selection measure. This measure is based on pioneering work by Claude Shannon on information theory, which studied the value or “information content” of messages. Let node $N$ represent or hold the tuples of partition $D$. The attribute with the highest information gain is chosen as the splitting attribute for node $N$. This attribute minimizes the information needed to classify the tuples in the resulting partitions and reflects the least randomness or “impurity” in these partitions. Such an approach minimizes the expected number of tests needed to classify a given tuple and guarantees that a simple (but not necessarily the simplest) tree is found.

The expected information needed to classify a tuple in $D$ is given by

$$Info(D) = - \sum_{i=1}^m p_i \log_2(p_i), \quad (6.2)$$

where $p_i$ is the nonzero probability that an arbitrary tuple in $D$ belongs to class $C_i$ and is estimated by $|C_{i,D}|/|D|$. A log function to the base 2 is used, because the information is encoded in bits. $Info(D)$ is just the average amount of information needed to identify the class label of a tuple in $D$. Note that, at this point, the information we have is based solely on the proportions of tuples of each class. $Info(D)$ is also known as the **entropy** of $D$.

Now, suppose we were to partition the tuples in $D$ on some attribute $A$ having $v$ distinct values, \(\{a_1, a_2, ..., a_v\}\), as observed from the training data. If $A$ is discrete-valued, these values correspond directly to the $v$ outcomes of a test on $A$. Attribute $A$ can be used to split $D$ into $v$ partitions or subsets, \(\{D_1, D_2, ..., D_v\}\), where $D_j$ contains those tuples in $D$ that have outcome $a_j$ of $A$. These partitions would correspond to the branches grown from node $N$. Ideally, we would like this partitioning to produce an exact classification of the tuples. That is, we would like for each partition to be pure. However, it is quite likely that the partitions will be impure (e.g., where a partition may contain a collection of tuples from different classes rather than from a single class).

How much more information would we still need (after the partitioning) to arrive at an exact classification? This amount is measured by

\(Info_A(D) = \sum_{j=1}^v \frac{|D_j|}{|D|} \times Info(D_j)\).

The term \(\frac{|D_j|}{|D|}\) acts as the weight of the \(j\)th partition. \(Info_A(D)\) is the expected information required to classify a tuple from \(D\) based on the partitioning by \(A\). The smaller the expected information (still) required, the greater the purity of the partitions. \(Info_A(D)\) is also known as the conditional entropy of \(D\) (conditioned on the attribute \(A\)).

Information gain is defined as the difference between the original information requirement (i.e., based on just the proportion of classes) and the new requirement (i.e., obtained after partitioning on \(A\)). That is,

\(Gain(A) = Info(D) - Info_A(D)\).

In other words, \(Gain(A)\) tells us how much would be gained by branching on \(A\). It is the expected reduction in the information requirement caused by knowing the value of \(A\). The attribute \(A\) with the highest information gain, \(Gain(A)\), is chosen as the splitting attribute at node \(N\). This is equivalent to saying that we want to partition on the attribute \(A\) that would do the “best classification,” so that the amount of information still required to finish classifying the tuples is minimal (i.e., minimum \(Info_A(D)\)).

**Example 6.1.** Induction of a decision tree using information gain. Table 6.1 presents a training set, \(D\), of class-labeled tuples randomly selected from the customer database of an electronics store. (The data are adapted from Quinlan [Qui86]. In this example, each attribute is discrete-valued. Continuous-valued attributes have been generalized.) The class label attribute, buys_computer, has two distinct

| RID | age | income | student | credit_rating | Class: buys_computer |
|---|---|---|---|---|---|
| 1 | youth | high | no | fair | no |
| 2 | youth | high | no | excellent | no |
| 3 | middle_aged | high | no | fair | yes |
| 4 | senior | medium | no | fair | yes |
| 5 | senior | low | yes | fair | yes |
| 6 | senior | low | yes | excellent | no |
| 7 | middle_aged | low | yes | excellent | yes |
| 8 | youth | medium | no | fair | no |
| 9 | youth | low | yes | fair | yes |
| 10 | senior | medium | yes | fair | yes |
| 11 | youth | medium | yes | excellent | yes |
| 12 | middle_aged | medium | no | excellent | yes |
| 13 | middle_aged | high | yes | fair | yes |
| 14 | senior | medium | no | excellent | no |
