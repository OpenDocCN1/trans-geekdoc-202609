There are three key metrics associated with association rule learning:

+   ■ Support: The proportion of transactions that include a particular item or combination of items.
+   ■ Confidence: The likelihood of occurrence of a particular item (B) when given some other item (A).
+   ■ Lift: The degree to which two items will appear together in this model, compared to the expected likelihood of them appearing together if the items were statistically independent; a lift value greater than 1 indicates the presence of item A increases the likelihood of B appearing.

The following example uses a data set of transactions from a fresh food market to find the items that are frequently purchased together. You can download the data set from https://github.com/paulbaumgarten/hodder-ibdp-computerscience

The first table, frequent itemsets, shows the support value for each set of items. In this case, 84 per cent of transactions include the sale of Milk. The association rules table illustrates the association between the antecedent (prerequisite) item and the consequent (resulting) item. In this case, the table shows:

+   ■ 62 per cent of transactions involve both Milk and Bread
+   ■ there is a 73 per cent likelihood that the customer will also purchase Bread if they purchase Milk
+   ■ the lift of 1.05 indicates that Bread is 1.05 times more likely to be purchased with Milk than without it.

| support | itemsets |
|---|---|
| 0.84 | (Milk) |
| 0.70 | (Bread) |
| 0.60 | (Butter) |
| 0.60 | (Egg) |
| 0.54 | (Cheese) |
| ... | ... |
| 0.40 | (Pasta, Butter, Bacon, Chicken) |
| 0.40 | (Apple, Banana, Coffee, Chicken) |
| 0.40 | (Apple, Banana, Bacon, Coffee) |
| 0.42 | (Banana, Bacon, Coffee, Chicken) |
| 0.40 | (Pasta, Banana, Bacon, Chicken) |

| antecedents | consequences | support | confidence | lift |
|---|---|---|---|---|
| (Milk) | (Bread) | 0.62 | 0.738095 | 1.054422 |
| (Bread) | (Milk) | 0.62 | 0.885714 | 1.054422 |
| (Butter) | (Milk) | 0.50 | 0.833333 | 0.992063 |
| (Egg) | (Milk) | 0.50 | 0.833333 | 0.992063 |
| (Cheese) | (Milk) | 0.50 | 0.925926 | 1.102293 |
| ... | ... | ... | ... | ... |
| (Pasta, Bacon) | (Banana, Chicken) | 0.40 | 0.833333 | 1.602564 |
| (Pasta, Chicken) | (Banana, Bacon) | 0.40 | 0.740741 | 1.322751 |
| (Banana, Bacon) | (Pasta, Chicken) | 0.40 | 0.714286 | 1.322751 |
| (Banana, Chicken) | (Pasta, Bacon) | 0.40 | 0.765211 | 1.602564 |
| (Bacon, Chicken) | (Pasta, Banana) | 0.40 | 0.714286 | 1.552795 |