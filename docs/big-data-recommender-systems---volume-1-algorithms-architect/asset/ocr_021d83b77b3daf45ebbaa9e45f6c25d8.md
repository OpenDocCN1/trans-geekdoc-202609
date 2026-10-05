# 288 Big data recommender systems, volume 1

Table 13.1 Soundex mapping table

| a, e, h, i, o, u, w, y | $ightarrow$ | 0 |
| b, f, p, v | $ightarrow$ | 1 |
| c, g, j, k, q, s, x, z | $ightarrow$ | 2 |
| d, t | $ightarrow$ | 3 |
| l | $ightarrow$ | 4 |
| m, n | $ightarrow$ | 5 |
| r | $ightarrow$ | 6 |

Regarding cost, phonetic encoding algorithms exhibit low complexity. A further advantage is that, traditional database indexes can be deployed over phonetic codes to speed up the matching process even further.

All these properties indicate phonetic algorithms are appropriate for the PPM process. They are efficient, they can handle dirty data, provide privacy through information suppression and reduce the problem of approximate matching to exact matching, unlike the approaches usually followed in the literature [16], where transformations are designed in a way that chunks of encoded words are compared to similarity using a metric.

In our approach, the common fields are encoded using phonetic codes. As the matching process is reduced to exact matching, a secure hash function is applied on the outputs of the phonetic algorithms as to further improve privacy. Finally, to determine whether two records consist a match, the outputs of the hash functions for all common fields are compared, and if they are identical, the matching process indicates a match. More formally, (13.1), when using phonetic algorithms for matching, is substituted by (13.2). The similarity function $sim$ used in the formula as has the inputs $H$ of phonetic PC code on input strings $r_i^{r-j}$, $r_j^{r-i}$ and examines their absolute similarity, returning 1 when the two codes are identical or 0 otherwise.

```
$M(r_i^{r-j}, r_j^{r-i}) = \begin{cases} \text{if } H(PC(r_i^{r-j})) = H(PC(r_j^{r-i})), & \forall j \in [1, m] \ 0, & \text{otherwise}. \end{cases}$
```

# 13.3.3 The Soundex algorithm

Soundex [28], based on English language pronunciation, is the oldest (patented in 1918) and best known phonetic encoding algorithm. It keeps the first letter of a string and converts the rest into numbers using Table 13.1 [8].

All zeros (vowels and "h", "w" and "y") are removed and sequences of same number are merged to a single one (e.g., "333" is replaced with "3”). The final code is the original letter and three numbers (longer codes are stripped-off and shorter codes are padded with zeros). As an example, the Soundex code for “Alan” is "A450,” while the code for “Turing” is "T652.\ A major drawback of Soundex is that it maintains the first letter of the encoded word intact; thus, any error or variation