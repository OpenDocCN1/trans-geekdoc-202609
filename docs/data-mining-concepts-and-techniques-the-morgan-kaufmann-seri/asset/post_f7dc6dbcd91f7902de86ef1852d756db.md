
![](img/90c930779c8f928df6ff4481fc59f9a3_364_0.png)

FIGURE 7.12 Rules for the class loan_decision = accept, showing accept (a) and reject (r) tuples.

if logically ANDing a given attribute test to condition would result in a better rule. We call the new condition, condition', where R': IF condition' THEN class = c is our potential new rule. In other words, we want to see if R' is any better than R.

We have already seen entropy in our discussion of the information gain measure used for attribute selection in decision tree induction. It is also known as the expected information needed to classify a tuple in data set, D. Here, D is the set of tuples covered by condition' and pi is the probability of class Ci in D. The lower the entropy, the better condition' is. Entropy prefers conditions that cover a large number of tuples of a single class and few tuples of other classes.

Another measure is based on information gain and was proposed in FOIL (First-Order Inductive Learner), a sequential covering algorithm that learns first-order logic rules. Learning first-order rules is more complex because such rules contain variables, whereas the rules we are concerned with in this section are propositional (i.e., variable-free).5 In machine learning, the tuples of the class for which we are learning rules are called positive tuples, whereas the remaining tuples are negative. Let pos and neg be the number of positive and negative tuples covered by R, respectively. Let pos' and neg' be the number of positive (negative) tuples covered by R', respectively. FOIL assesses the information gained by extending condition' as

```
FOIL_Gain = pos' x ( log2 pos' / (pos' + neg') - log2 pos / (pos + neg) ). (7.20)
```

It favors rules that have high accuracy and cover many positive tuples.

We can also use a statistical test of significance to determine if the apparent effect of a rule is not attributed to chance but instead indicates a genuine correlation between attribute values and classes. The test compares the observed distribution among classes of tuples covered by a rule with the expected distribution that would result if the rule made predictions at random. We want to assess whether any observed differences between these two distributions may be attributed to chance. We can use the likelihood ratio statistic,

```
Likelihood_Ratio = 2 \sum_{i=1}^{m} f_i \log \left( \frac{f_i}{e_i} \right),
```

where m is the number of classes.

For tuples satisfying the rule, $f_i$ is the observed frequency of each class $i$ among the tuples. $e_i$ is what we would expect the frequency of each class $i$ to be if the rule made random predictions. The statistic has a $\chi^2$ distribution with $m-1$ degrees of freedom. The higher the likelihood ratio, the more likely that there is a *significant* difference in the number of correct predictions made by our rule in comparison with a "random guesser." That is, the performance of our rule is not due to chance. The ratio helps identify rules with insignificant coverage.

CN2 uses entropy together with the likelihood ratio test, while FOIL's information gain is used by RIPPER.

### Rule pruning

Learn_One_Rule does not employ a test set when evaluating rules. Assessments of rule quality as described previously are made with tuples from the original training data. These assessments are optimistic because the rules will likely overfit the data. That is, the rules may perform well on the training data but less well on subsequent unseen data (i.e., test data). To compensate for this, we can prune the rules. A rule is pruned by removing a conjunction (attribute test). We choose to prune a rule, $R$, if the pruned version of $R$ has greater quality, as assessed on an independent set of tuples. As in decision tree pruning, we refer to this set as a *pruning set*.

FOIL uses a simple yet effective method. Given a rule, $R$,

```
FOIL_Prune(R) = \frac{pos - neg}{pos + neg},
```

where $pos$ and $neg$ are the number of positive and negative tuples covered by $R$, respectively. This value will increase with the accuracy of $R$ on a pruning set. Therefore if the $FOIL\_Prune$ value is higher for the pruned version of $R$, then we prune $R$.

By convention, RIPPER starts with the most recently added conjunction when considering pruning. Conjunctions are pruned one at a time as long as this results in an improvement.

## 7.4.4 Associative classification

In this section, you will learn about associative classification. The methods discussed are CBA, CMAR, and CPAR.

Before we begin, however, let's look at association rule mining in general. Association rules are mined in a two-step process consisting of *frequent itemset mining* followed by *rule generation*. The first step searches for patterns of attribute-value pairs that occur repeatedly in a data set, where each attribute-value pair is considered an *item*. The resulting attribute-value pairs form *frequent itemsets* (also referred to as *frequent patterns*). The second step analyzes the frequent itemsets to generate association rules. All association rules must satisfy certain criteria regarding their "accuracy" (or *confidence*) and the proportion of the data set that they actually represent (referred to as *support*). For example, the following is an association rule mined from a data set, *D*, shown with its confidence and support:

```
age = youth ^ credit = OK => buys_computer = yes
[support = 20%, confidence = 93%],
(7.23)
```

where ^ represents a logical “AND.” We will say more about confidence and support later.

More formally, let *D* be a data set of tuples. Each tuple in *D* is described by *n* attributes, *A*1, *A*2, ..., *A*n, and a class label attribute, *A*class. All continuous attributes are discretized and treated as categorical (or nominal) attributes. An **item**, *p*, is an attribute–value pair of the form (*Ai*, *v*), where *Ai* is an attribute taking a value, *v*. A data tuple *X* = (*x*1, *x*2, ..., *xn*) satisfies an item, *p* = (*Ai*, *v*), if and only if *xi* = *v*, where *xi* is the value of the *i*th attribute of *X*. Association rules can have any number of items in the rule antecedent (left side) and any number of items in the rule consequent (right side). However, when mining association rules for use in classification, we are only interested in association rules of the form *p*1 ^ *p*2 ^ ... ^ *pl* => *A*class = *C*, where the rule antecedent is a conjunction of items, *p*1, *p*2, ..., *pl* (*l* <= *n*), associated with a class label, *C*. For a given rule, *R*, the percentage of tuples in *D* satisfying the rule antecedent that also has the class label *C* is called the **confidence** of *R*.

From a classification point of view, this is akin to rule accuracy. For example, a confidence of 93% for Rule in Eq. (7.23) means that 93% of the customers in *D* who are young and have an OK credit rating belong to the class *buys_computer* = *yes*. The percentage of tuples in *D* satisfying the rule antecedent and having class label *C* is called the **support** of *R*. A support of 20% for Rule in Eq. (7.23) means that 20% of the customers in *D* are young, have an OK credit rating, and belong to the class *buys_computer* = *yes*.

In general, associative classification consists of the following steps:

- 1. Mine the data for frequent itemsets, that is, find commonly occurring attribute–value pairs in the data.
- 2. Analyze the frequent itemsets to generate association rules per class, which satisfy confidence and support criteria.
- 3. Organize the rules to form a rule-based classifier.

Methods of associative classification differ primarily in the approach used for frequent itemset mining and in how the derived rules are analyzed and used for classification. We now look at some of the various methods for associative classification.

One of the earliest and simplest algorithms for associative classification is **CBA** (Classification Based on Associations). CBA uses an iterative approach to frequent itemset mining, similar to that described for Apriori in Section 4.2.1, where multiple passes are made over the data and the derived frequent itemsets are used to generate and test longer itemsets. In general, the number of passes made is equal to the length of the longest rule found. The complete set of rules satisfying minimum confidence and minimum support thresholds are found and then analyzed for inclusion in the classifier. CBA uses a heuristic method to construct the classifier, where the rules are ordered according to decreasing precedence based on their confidence and support. If a set of rules has the same antecedent, then the rule with the highest confidence is selected to represent the set. When classifying a new tuple, the first rule satisfying the tuple is used to classify it. The classifier also contains a default rule, having the lowest precedence, which specifies a default class for any new tuple that is not satisfied by any other rule in
