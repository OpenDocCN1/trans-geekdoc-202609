completeness of the answer returned for a mining query. However, this is a nontrivial task, and its study leads to constraint-based pattern mining.

To study how to use constraints at mining frequent patterns or association rules, we examine the following running example.

**Example 5.10. Constraints on shopping transaction mining.** Suppose that a multidimensional shopping transaction database contains the following interrelated relations:

+   - item(item_ID, item_name, description, category, price)
+   - sales(transaction_ID, day, month, year, store_ID, city)
+   - trans_item(item_ID, transaction_ID)

Here, the item table contains attributes item_ID, item_name, description, category, and price; the sales table contains attributes transaction_ID, day, month, year, store_ID, and city; and the two tables are linked via the foreign key attributes item_ID and transaction_ID, in the table trans_item.

A mining query may contain multiple constraints. For example, we may have a query: “From the sales in Chicago in 2020, find the patterns (i.e., item sets) that which cheap items (where the sum of the prices is less than $10) appear in the same transaction with (hence may promote) which expensive items (where the minimum price is $50).”

This constraint contains the following four constraints: (1) sum(I.price) < $10, where I represents the item_ID of a cheap item; (2) min(J.price) ≥ $50), where J represents the item_ID of an expensive item; (3) T.city = Chicago; and (4) T.year = 2020, where T represents a transaction_ID.

In constraint-based pattern mining, the search space can be pruned in the mining process with two strategies: pruning pattern search space and pruning data search space. The former checks candidate patterns and decides whether a pattern should be eliminated from further processing. For example, it may prune a pattern if all of its superpattern will be useless in the remaining mining process, say, based on the Apriori property. The latter checks the data set to determine whether a particular data object will not be able to contribute to the subsequent generation of satisfiable patterns in the remaining mining process (hence safely pruning the data object).

We examine these pruning strategies in the following subsections.

# 5.3.1 Pruning pattern space with pattern pruning constraints

Based on how a constraint may interact with the pattern mining process, we partition pattern mining constraints into four categories: (1) antimonotonic, (2) monotonic, (3) convertible, and (4) nonconvertible. Let’s examine them one by one.

# *Pattern antimonotonicity*

The first group of constraints are characterized with pattern antimonotonicity. A constraint C is pattern antimonotonic if it has the following property: If an itemset does not satisfy constraint C, none of its supersets will satisfy C.

Let’s examine a constraint “C1 : sum(I.price) ≤ $100” and see what may happen if the constraint is added to our shopping transaction mining query. Suppose we are mining itemsets of size k at the kth iteration using the Apriori algorithm or the like. If the summation of the prices of the items in a candidate itemset S1 is greater than $100, this itemset should be pruned from the search space, since not only the