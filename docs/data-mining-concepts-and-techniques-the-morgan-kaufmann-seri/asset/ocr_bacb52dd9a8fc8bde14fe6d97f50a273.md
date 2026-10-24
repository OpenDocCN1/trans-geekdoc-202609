states. For example, the range of the interval-scaled attribute temperature (in Celsius) can be organized into the following states: –30 to –10, –10 to 10, and 10 to 30, representing the categories cold temperature, moderate temperature, and warm temperature, respectively. Let $M_f$ represent the number of possible states that an ordinal attribute can have. These ordered states define the ranking 1, ..., $M_f$.

“How are ordinal attributes handled?” The treatment of ordinal attributes is quite similar to that of numeric attributes when computing dissimilarity between objects. Suppose that $f$ is an attribute from a set of ordinal attributes describing $n$ objects. The dissimilarity computation with respect to $f$ involves the following steps:

+   1. The value of $f$ for the $i$th object is $x_{if}$, and $f$ has $M_f$ ordered states, representing the ranking 1, ..., $M_f$. Replace each $x_{if}$ by its corresponding rank, $r_{if} \in \{1, ..., M_f\}$.

+   2. Since each ordinal attribute can have a different number of states, it is often necessary to map the range of each attribute onto [0.0, 1.0] so that each attribute has equal weight. We perform such data normalization by replacing the rank $r_{if}$ of the $i$th object in the $f$th attribute by

```
$z_{if} = \frac{r_{if} - 1}{M_f - 1}$. (2.26)
```

+   3. Dissimilarity can then be computed using any of the distance measures described in Section 2.3.4 for numeric attributes, using $z_{if}$ to represent the $f$ value for the $i$th object.

# Example 2.22. Dissimilarity between ordinal attributes.

Suppose that we have the sample data shown earlier in Table 2.4, except that this time only the object-identifier and the continuous ordinal attribute, test-2, are available. There are three states for test-2: fair, good, and excellent, that is, $M_f = 3$. For step 1, if we replace each value for test-2 by its rank, the four objects are assigned the ranks 3, 1, 2, and 3, respectively. Step 2 normalizes the ranking by mapping rank 1 to 0.0, rank 2 to 0.5, and rank 3 to 1.0. For step 3, we can use, say, the Euclidean distance defined in Eq. (2.21), which results in the following dissimilarity matrix:

| | | | |
|---|---|---|---|
| 0 | | | |
| 1.0 | 0 | | |
| 0.5 | 0.5 | 0 | |
| 0 | 1.0 | 0.5 | 0 |

Therefore objects 1 and 2 are the most dissimilar, as are objects 2 and 4 (i.e., $d(2, 1) = 1.0$ and $d(4, 2) = 1.0$). This makes intuitive sense since objects 1 and 4 are both excellent. Object 2 is fair, which is at the opposite end of the range of values for test-2.

Similarity values for ordinal attributes can be interpreted from dissimilarity as $sim(i, j) = 1 - d(i, j)$.

# 2.3.6 Dissimilarity for attributes of mixed types

Sections 2.3.2 through 2.3.5 discussed how to compute the dissimilarity between objects described by attributes of the same type, where these types may be either nominal, symmetric binary, asymmetric binary, numeric, or ordinal. However, in many real databases, objects are described by a mixture of attribute types. In general, a database can contain all of these attribute types.