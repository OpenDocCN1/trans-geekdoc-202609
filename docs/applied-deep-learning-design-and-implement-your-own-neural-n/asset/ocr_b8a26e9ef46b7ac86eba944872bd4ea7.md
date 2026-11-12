information gain. It is based on the reduction in entropy after splitting of the dataset. The information gained from X on Y is given as follows. Table 1.6 represents the training data set consisting of various product types:

```
I(Y, X) = E(Y) - E(Y|X)
```

where ’E(Y|X)’ is the entropy of Y given X.

# Example:

| YOP (Year of Production) | Market competition | Type | Profit/Loss |
| :--- | :--- | :--- | :--- |
| YOP < 2010 | Yes | Type-A | Loss |
| YOP < 2010 | No | Type-A | Loss |
| YOP < 2010 | No | Type-B | Loss |
| 2010 <YOP < 2015 | Yes | Type-A | Loss |
| 2010 <YOP < 2015 | Yes | Type-B | Loss |
| 2010 <YOP < 2015 | No | Type-B | Profit |
| 2010 <YOP < 2015 | No | Type-A | Profit |
| YOP > 2015 | Yes | Type-A | Profit |
| YOP > 2015 | No | Type-B | Profit |
| YOP > 2015 | No | Type-A | Profit |

Table 1.6: Data for product types

Profit is the class attribute here, as it describes whether the product is giving a profit or not. Here, P is the possibility of getting Profit, and N is the possibility of getting Loss. Here, P = 5 and N = 5. First, calculate the entropy of the class attribute.

```
Entropy(class) = \frac{-P}{P+N} log_2 \left(\frac{P}{P+N}\right) - \frac{N}{P+N} log_2 \left(\frac{N}{P+N}\right)
= \frac{-5}{5 + 5} log_2 \left(\frac{5}{5 + 5}\right) - \frac{5}{5 + 5} log_2 \frac{5}{5 + 5}
Entropy(class) = 1
```

Now to find the root node, determine the information gain, entropy, and gain for each attribute.