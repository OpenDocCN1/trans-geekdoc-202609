+   a. Join: C3 = L2 x L2 = {{I1, I2}, {I1, I3}, {I1, I5}, {I2, I3}, {I2, I4}, {I2, I5}} x {{I1, I2}, {I1, I3}, {I1, I5}, {I2, I3}, {I2, I4}, {I2, I5}} = {{I1, I2, I3}, {I1, I2, I5}, {I1, I3, I5}, {I2, I3, I4}, {I2, I3, I5}, {I2, I4, I5}}.

+   b. Prune using the Apriori property: all nonempty subsets of a frequent itemset must also be frequent. Do any of the candidates have a subset that is not frequent?

+   - The 2-item subsets of {I1, I2, I3} are {I1, I2}, {I1, I3}, and {I2, I3}. All 2-item subsets of {I1, I2, I3} are members of L2. Therefore, keep {I1, I2, I3} in C3.
+   - The 2-item subsets of {I1, I2, I5} are {I1, I2}, {I1, I5}, and {I2, I5}. All 2-item subsets of {I1, I2, I5} are members of L2. Therefore, keep {I1, I2, I5} in C3.
+   - The 2-item subsets of {I1, I3, I5} are {I1, I3}, {I1, I5}, and {I3, I5}. {I3, I5} is not a member of L2, and so it is not frequent. Therefore, remove {I1, I3, I5} from C3.
+   - The 2-item subsets of {I2, I3, I4} are {I2, I3}, {I2, I4}, and {I3, I4}. {I3, I4} is not a member of L2, and so it is not frequent. Therefore, remove {I2, I3, I4} from C3.
+   - The 2-item subsets of {I2, I3, I5} are {I2, I3}, {I2, I5}, and {I3, I5}. {I3, I5} is not a member of L2, and so it is not frequent. Therefore, remove {I2, I3, I5} from C3.
+   - The 2-item subsets of {I2, I4, I5} are {I2, I4}, {I2, I5}, and {I4, I5}. {I4, I5} is not a member of L2, and so it is not frequent. Therefore, remove {I2, I4, I5} from C3.

+   c. Therefore, C3 = {{I1, I2, I3}, {I1, I2, I5}} after pruning.

# FIGURE 4.3

Generation and pruning of candidate 3-itemsets, C3, from L2 using the Apriori property.

The apriori_gen procedure performs two kinds of actions, namely, join and prune, as described before. In the join component, Lk-1 is joined with Lk-1 to generate potential candidates (steps 1–4). The prune component (steps 5–7) employs the Apriori property to remove candidates that have a subset that is not frequent. The test for infrequent subsets is shown in procedure has_infrequent_subset.

# 4.2.2 Generating association rules from frequent itemsets

Once the frequent itemsets from transactions in a database D have been found, it is straightforward to generate strong association rules from them (where strong association rules satisfy both minimum support and minimum confidence). This can be done using Eq. (4.4) for confidence, which we show again here for completeness:

```
confidence (A => B) = P(B|A) = \frac{support\_count (A \cup B)}{support\_count (A)}.
```

The conditional probability is expressed in terms of itemset support count, where support_count (A U B) is the number of transactions containing the itemsets A U B, and support_count (A) is the number of transactions containing the itemset A. Based on this equation, association rules can be generated as follows.

+   - For each frequent itemset l, generate all nonempty subsets of l.
+   - For every nonempty subset s of l, output the rule “s => (l – s)” if \frac{support\_count(l)}{support\_count(s)} \ge min\_conf, where min_conf is the minimum confidence threshold.