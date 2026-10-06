# CHAPTER 7. ENCODING BEHAVIORAL DATA 205

| Transaction ID | Items |
|---|---|n| 1 | {chocolate} |
| 2 | {chocolate, chips, soda} |
| 3 | {chocolate, soda} |
| 4 | {soda} |
| 5 | {soda} |
| 6 | {candies, ice cream} |
| 7 | {soda, ice cream} |
| 8 | {chips, soda} |
| 9 | {candies, chocolate, chips} |
| 10 | {ice cream, chocolate, soda chips} |

Figure 7.4: Example database with 10 transactions.

Transactions can include additional information like customer id, date, total cost, etc. Transactions can be coded as logical matrices where rows represent transactions and columns represent items. A TRUE value indicates that the particular item is present and FALSE indicates the particular item is not part of that set. When the number of possible items is huge and item sets contain a small number of items this type of matrix can be inefficient because there are going to be many entries with a value of FALSE, that is, a sparse matrix. Transactions can also be stored as lists or in a relational database such as MySQL. Below are some advantages of representing data as transactions.

# Advantages:

+   - Association rule mining algorithms such as Apriori can be used to extract interesting behavior relationships.

+   - Recommendation systems can be built based on transactional data.

# Limitations:

+   - Can be inefficient to store them as a logical matrix.

# 7.4 Images