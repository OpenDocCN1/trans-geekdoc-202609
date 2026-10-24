| | I/H | I/M | I/L | C/H | C/M | C/L | P/H | P/M | P/L |
|---|---|---|---|---|---|---|---|---|---|
| John | 1 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 |
| Amy | 1 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 |
| Carl | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 |
| Mary | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 |
| Tom | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 0 |
| Jim | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 1 |

(a) Representing the input categorical data as binary matrix B

![](bbox=[0.312, 0.242, 0.703, 0.318])

(b) The two factorized matrices

| | I/H | I/M | I/L | C/H | C/M | C/L | P/H | P/M | P/L |
|---|---|---|---|---|---|---|---|---|---|
| John | 1 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 |
| Amy | 1 | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 |
| Carl | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 |
| Mary | 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 1 |
| Tom | 0.5 | 0 | 0.5 | 0.5 | 0 | 0.5 | 0.5 | 0 | 0.5 |
| Jim | 0.3 | 0 | 0.7 | 0.3 | 0 | 0.7 | 0.3 | 0 | 0.7 |

(c) The reconstructed matrix

# FIGURE 11.15

Using matrix factorization based method to detect outliers of input data with categorical attributes. (a) Representing the input data by a binary data matrix B by converting the categorical attributes to binary attributes. (b) The two factorized matrices F and G to approximate the binary data matrix B. “I/H,” “I/M,” and “I/L” represent the attribute values of “Income” being “High,” “Medium,” and “Low,” respectively. Likewise, “C/H,” “C/M,” and “C/L” represent the attribute values of “Credit” being “High,” “Medium,” and “Low,” respectively; and “P/H,” “P/M,” and “P/L” represent the attribute values of “Purchase” being “High,” “Medium,” and “Low,” respectively. (c) The reconstructed matrix.

When a categorical attribute has many different values, the binary data matrix B would have many columns since we need to create a separate column (i.e., binary feature) for each categorical attribute value. This might make the matrix factorization process computationally intensive and the detection results hard to interpret. For example, it might be hard to tell why “Tom” and “Jim” are flagged as outliers by just looking at the factorized matrices F and G in Fig. 11.15(b). So, how can we do better?

An alternative method is to use pattern-based compression methods to detect outliers for input data with categorical attributes.

For the input data set in Fig. 11.14, we can construct a code table (also known as dictionary), shown in Fig. 11.16. At the first glance, the table might look a bit abstract to you. Let us explain the details.

The first column of Fig. 11.16 consists of a set of code words, also known as a pattern. Each code word or pattern (e.g., “[I/H, C/H, P/H]”) consists of one or more items, which are essentially an attribute-value pairs (e.g., “I/H” meaning the value of “Income” is “High”). (Recall that we have used the similar notations for pattern-based classification in Chapter 7.) The second column of Fig. 11.16 contains the binary codes that are used to represent the corresponding code words, and the last column is