to another group of users as a collusion type of fake reviewers. If we map such behaviors or activities (e.g., “sends packages,” “gives good ratings,” etc.) to the language of matrix factorization, it suggests that the corresponding entries in the residual matrix should be nonnegative.

Another method, called robust PCA, requires that the residual matrix R to be sparse with most of the rows being empty. The intuition is as follows. For the vast majority of normal data tuples, they can be perfectly reconstructed by the factorized matrices, whereas for a small number of outlying tuples, they bear nonzero reconstruction errors indicated by the corresponding, nonempty rows in the residual matrix R.

Matrix factorization based methods are linear methods in that the new, more succinct representation is a linear combination of the original features. For example, in SVD, each right singular vector is a linear combination of the original features of the input data. For the example in Fig. 11.9, the new representation “Data Mining” is the result of a linear combination of the two conferences including “KDD” and “ICDM.” If we wish to capture the nonlinear relationship between the original features, we can use autoencoder, an unsupervised deep learning architecture introduced in Chapter 10, to reconstruct the original data samples. Again, the data samples with high reconstruction errors are flagged as outliers.

# 11.4.2 Pattern-based compression methods for categorical data

For input data with categorical attributes, we could convert the categorical attributes to binary attributes and then apply the matrix factorization based methods to detect outliers.

Example 11.18. Given an input data set in Fig. 11.14, where each row represents a customer who is described by three categorical attributes, namely “income,” “credit,” and “purchase.” In order to detect abnormal customers, we first convert the input data set into a binary data matrix B in Fig. 11.15(a). Since each categorical attribute has three possible values, including “High,” “Medium,” and “Low,” it is converted into three binary attributes. (How to convert a categorical attribute to binary ones was introduced in Chapter 2.) Next, we approximate the binary data matrix B by the multiplication of two low-rank matrices, say the ones in Fig. 11.15(b), which are in turn used to reconstruct the original data matrix B. By comparing the original and reconstructed data matrices, we find out that the reconstruction errors for the first four customers are all zeros. On the other hand, the reconstruction errors for Tom and Jim are 2.5 and 1.34, respectively, both of whom are thus flagged as outliers.

| | Income | Credit | Purchase |
|---|---|---|---|
| John | High | High | High |
| Amy | High | High | High |
| Carl | Low | Low | Low |
| Mary | Low | Low | Low |
| Tom | High | Low | Medium |
| Jim | High | Low | Low |

FIGURE 11.14 Input data with categorical attributes, including “Income,” “Credit,” and “Purchase.” Each categorical attribute has three values, including “High,” “Medium,” and “Low.”