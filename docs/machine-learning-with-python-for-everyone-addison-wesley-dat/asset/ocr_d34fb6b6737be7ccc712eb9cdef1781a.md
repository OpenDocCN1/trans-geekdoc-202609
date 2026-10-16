rectangle areas—between different pairs of variables. The covariance between X and Y is the same as the covariance between Y and X, so the table is going to have repeated entries.

Here’s an example that has relatively little structure in the data. What do I mean by structure? When we look at the covariance matrix, there aren’t too many patterns in it. But there is one. I’ll let you find it.

```
In [43]:

data = pd.DataFrame({'X':[ 1, 3, 6],
    'Y':[ 1, 6, 3],
    'Z':[10, 5, 1]})

data.index.name = 'examples'

# it's not critical to these examples, but Pandas' cov is
# "unbiased" and we've been working with "biased" covariance
# see EOC notes for details
display(data)
print("Covariance:")
display(data.cov())
```

| examples | X | Y | Z |
|---|---|---|---|
| 0 | 1 | 1 | 10 |
| 1 | 3 | 6 | 5 |
| 2 | 6 | 3 | 1 |

Covariance:

|   | X | Y | Z |
|---|---|---|---|
| X | 6.3333 | 1.8333 | -11.1667 |
| Y | 1.8333 | 6.3333 | -5.1667 |
| Z | -11.1667 | -5.1667 | 20.3333 |

I’ll talk about the values in that matrix with respect to the main diagonal—the 6.3, 6.3, and 20.3 values. (Yes, there are two diagonals. The “main” diagonal we care about is the one running from top-left to bottom-right.)

You may have noticed two things. First, the elements are mirrored across the main diagonal. For example, the top-right and bottom-left values are the same (−11.1667). That is not a coincidence; all covariance matrices are symmetric because, as I pointed out above, Cov(X,Y)=Cov(Y,X) for all pairs of features. Second, you may have picked up on the fact that both X and Y have the same variance. It shows up here as Cov(X,X) and Cov(Y,Y).

Now, imagine that our different features are not directionally related to each other. There’s no set pattern: as one goes up, the other can either go up or down. We might be