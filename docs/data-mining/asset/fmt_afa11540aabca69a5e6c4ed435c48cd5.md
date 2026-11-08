
An example will help to explain how candidate item sets are generated. Suppose there are 5 three-item sets—`(A B C)`, `(A B D)`, `(A C D)`, `(A C E)`, and `(B C D)`—where A is a feature such as `outlook` = `sunny`. The union of the first two, `(A B C D)`, is a candidate four-item set because its other three-item subsets `(A C D)` and `(B C D)` have greater than minimum coverage. If the three-item sets are sorted into lexical order, as they are in this list, then we need only consider pairs whose first two members are the same. For example, we do not consider `(A C D)` and `(B C D)` because `(A B C D)` can also be generated from `(A B C)` and `(A B D)`, and if these two are not three-item sets with minimum coverage then `(A B C D)` cannot be a candidate four-item set. This leaves the pairs `(A B C)` and `(A B D)`, which we have already explained, and `(A C D)` and `(A C E)`. This second pair leads to the set `(A C D E)`, whose three-item subsets do not all have the minimum coverage, so it is discarded. The hash table assists with this check; we simply remove each item from the set in turn and check that the remaining three-item set is indeed present in the hash table. Thus in this example there is only one candidate four-item set `(A B C D)`. Whether or not it actually has minimum coverage can only be determined by checking the instances in the dataset.

The second stage of the procedure takes each item set and generates rules from it, checking that they have the specified minimum accuracy. If only rules with a single test on the right-hand side were sought, it would be simply a matter of considering each condition in turn as the consequent of the rule, deleting it from the item set, and dividing the coverage of the entire item set by the coverage of the resulting subset—obtained from the hash table—to yield the accuracy of the corresponding rule. Given that we are also interested in association rules with multiple tests in the consequent, it looks like we must evaluate the effect of placing each `subset` of the item set on the right-hand side, leaving the remainder of the set as the antecedent.

This brute-force method will be excessively computation intensive unless item sets are small because the number of possible subsets grows exponentially with the size of the item set. However, there is a better way. We observed when describing association rules in [Section 3.4](#Ch003_67-89_B9780443158889000042.xhtml#s0025) that if the double-consequent rule

```
If windy = false and play = no
```
then `outlook` = `sunny` and `humidity` = `high`

holds with a given minimum coverage and accuracy, then both single-consequent rules formed from the same item set must also hold:

```
If humidity = high and windy = false and play = no
```
then `outlook` = `sunny`

```
If outlook = sunny and windy = false and play = no
```
then `humidity` = `high`

Conversely, if one or the other of the single-consequent rules does not hold, there is no point in considering the double-consequent one. This gives a way of building up from single-consequent rules to candidate double-consequent ones, from double-consequent rules to candidate triple-consequent ones, and so on. Of course, each candidate rule must be checked against the hash table to see if it really does have more than the specified minimum accuracy. But this generally involves checking far fewer rules than the brute force method. It is interesting that this way of building up candidate (`n` + 1<mml:math><mml:mi>n</mml:mi><mml:mo>+</mml:mo><mml:mn>1</mml:mn></mml:math>![Equation](images/F000054si59.png))-consequent rules from actual `n`-consequent ones is really the same as building up candidate (`n` + 1<mml:math><mml:mi>n</mml:mi><mml:mo>+</mml:mo><mml:mn>1</mml:mn></mml:math>![Equation](images/F000054si60.png))-item sets from actual `n`-item sets, described earlier.

[Fig. 4.9](#Ch004_91-164_B9780443158889000054_a.xhtml#f0050) shows pseudocode for the two parts of the association rule mining process. [Fig. 4.9A](#Ch004_91-164_B9780443158889000054_a.xhtml#f0050) shows how to find all item sets of sufficient coverage. In an actual implementation, the minimum coverage (or support) would be specified by a parameter whose value the user can specify. [Fig. 4.9B](#Ch004_91-164_B9780443158889000054_a.xhtml#f0050) shows how to find all rules that are sufficiently accurate for a particular item set found by the previous algorithm. Again, in practice, minimum accuracy (or confidence) would be determined by a user-specified parameter.

![Fig. 4.9 Pseudocode for association rule mining. (A) Finding all item sets with sufficient coverage. (B) Finding all sufficiently accurate association rules for a k-item set.](images/F000054f04-09-9780443158889.jpg)

Fig. 4.9 Pseudocode for association rule mining. (A) Finding all item sets with sufficient coverage. (B) Finding all sufficiently accurate association rules for a `k`-item set.

To find all rules for a particular dataset, the process shown in the second part would be applied to all the item sets found using the algorithm in the first part. Note that the code in the second part requires access to the hash tables established by the first part, which contain all the sufficiently frequent item sets that have been found, along with their coverage. In this manner, the algorithm in [Fig. 4.9B](#Ch004_91-164_B9780443158889000054_a.xhtml#f0050) does not need to revisit the original data at all; accuracy can be estimated based on the information in these tables.

Association rules are often sought for very large datasets, and efficient algorithms are highly valued. The method we have described makes one pass through the dataset for each different size of item set. Sometimes the dataset is too large to read into main memory and must be kept on disk; then it may be worth reducing the number of passes by checking item sets of two consecutive sizes in one go. For example, once sets with two items have been generated, all sets of three items could be generated from them before going through the instance set to count the actual number of items in the sets. More three-item sets than necessary would be considered but the number of passes through the entire dataset would be reduced.

In practice, the amount of computation needed to generate association rules depends critically on the minimum coverage specified. The accuracy has less influence because it does not affect the number of passes that must be made through the dataset. In many situations we would like to obtain a certain number of rules—say 50—with the greatest possible coverage at a prespecified minimum accuracy level. One way to do this is to begin by specifying the coverage to be rather high and to then successively reduce it, re-executing the entire rule-finding algorithm for each coverage value and repeating until the desired number of rules has been generated.

The tabular input format that we use throughout this book, and in particular the standard attribute-relation file format (`ARFF`) format based on it, is very inefficient for many association-rule problems. Association rules are often used in situations where attributes are binary—either present or absent—and most of the attribute values associated with a given instance are absent. This is a case for the sparse data representation described in [Section 2.4](#Ch002_43-66_B9780443158889000030.xhtml#s0035); the same algorithm for finding association rules applies.

## 4.6 Linear Models
