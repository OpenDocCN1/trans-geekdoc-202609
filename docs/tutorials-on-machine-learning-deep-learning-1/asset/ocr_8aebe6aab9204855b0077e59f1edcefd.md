```
# importing data
daset = pd.read_csv('Market_Basket_Optimisation.csv', header = None)
```

```
# creating 'List of Lists': List of product-set
# then rows of transactions and 20 columns of product
transactions = []
for i in range(0
```

dataset.values[i, j]: We keep the values of the dataset as [i, j], we need to add member
.values

Apriori is also extracting items as strings so we need to convert the data into string when we are creating the list
str(dataset.values[i, j]). To create list using [j].

| Index | 0 | 1 | 2 | 3 |
|---|---|---|---|---|n| 0 | shrimp | almonds | avocado | vegetables mix |
| 1 | burgers | meatballs | eggs | nan |
| 2 | chutney | nan | nan | nan |
| 3 | turkey | avocado | nan | nan |
| 4 | mineral water | milk | energy bar | whole wheat rice |
| 5 | low fat yogurt | nan | nan | nan |
| 6 | whole wheat pasta | french fries | nan | nan |
| 7 | soup | light cream | shallot | nan |
| 8 | frozen vegetables | spaghetti | green tea | nan |
| 9 | french fries | nan | nan | nan |

# transactions-List (7501 elements)

| Index | Type | Size | Value |
|---|---|---|---|
| 0 | list | 20 | ['shrimp', 'almonds', 'avocado', 'vegetables mix', 'green grapes', 'wh ... |
| 1 | list | 3 | ['burgers', 'meatballs', 'eggs'] |
| 2 | list | 1 | ['chutney'] |
| 3 | list | 2 | ['turkey', 'avocado'] |
| 4 | list | 5 | ['mineral water', 'milk', 'energy bar', 'whole wheat rice', 'green tea ... |
| 5 | list | 1 | ['low fat yogurt'] |
| 6 | list | 2 | ['whole wheat pasta', 'french fries'] |
| 7 | list | 3 | ['soup', 'light cream', 'shallot'] |
| 8 | list | 3 | ['frozen vegetables', 'spaghetti', 'green tea'] |
| 9 | list | 1 | ['french fries'] |

So you can see this list contains 7501 lists and each list corresponds to one transaction.