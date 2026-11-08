
# Partial Least Squares Directions

There is a simple iterative method for computing the partial least squares directions that involves only dot product operations. Starting with input attributes that have been standardized to have zero mean and unit variance, the attribute coefficients for the first partial least squares direction are found by taking the dot product between each attribute vector and the class vector in turn. To find the second direction the same approach is used, but the original attribute values are replaced by the difference between the attribute’s value and the prediction from a simple univariate regression that uses the first direction as the single predictor of that attribute. These differences are called `residuals`. The process continues in the same fashion for each remaining direction, with residuals for the attributes from the previous iteration forming the input for finding the current partial least squares direction.

Here is a simple worked example that should help make the procedure clear. For the first five instances from the CPU performance data in [Table 1.5](#Ch001_3-42_B9780443158889000029.xhtml#t0030), [Table 6.1A](#Ch006_209-259_B9780443158889000078.xhtml#t0010) shows the values of `CHMIN` and `CHMAX` (after standardization to zero mean and unit variance) and `PRP` (not standardized). The task is to find an expression for the target attribute `PRP` in terms of the other two. The attribute coefficients for the first partial least squares direction are found by taking the dot product between the class and each attribute in turn. The dot product between the `PRP` and `CHMIN` columns is –0.4472, and that between `PRP` and `CHMAX` is 22.981. Thus the first partial least squares direction is

`PLS1 = -0.4472 CHMIN + 22.981 CHMAX`.

![Equation](images/F000078si6.png)

[Table 6.1B](#Ch006_209-259_B9780443158889000078.xhtml#t0010) shows the values for `PLS1` obtained from this formula.

Table 6.1

 The First Five Instances From the CPU Performance Data. (A) Original Values. (B) The First Partial Least Squares Direction. (C) Residuals From the First Direction 

|    || (A) || (B) || (C) |
| --- | --- | --- | --- |
|   || CHMIN || CHMAX || PRP || PLS1 || CHMIN || CHMAX || PRP |
| 1 || 1.7889 || 1.7678 || 198 || 39.825 || 0.0436 || 0.0008 || 198 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 2 || −0.4472 || −0.3536 || 269 || −7.925 || −0.0999 || −0.0019 || 269 |
| 3 || −0.4472 || −0.3536 || 220 || −7.925 || −0.0999 || −0.0019 || 220 |
| 4 || −0.4472 || −0.3536 || 172 || −7.925 || −0.0999 || −0.0019 || 172 |
| 5 || −0.4472 || −0.7071 || 132 || −16.05 || 0.2562 || 0.005 || 132 |

![Image](images/T000078tabt0010.png)

The next step is to prepare the input data for finding the second partial least squares direction. To this end `PLS1` is regressed onto `CHMIN` and `CHMAX` in turn, resulting in linear equations that predict each of these attributes individually from `PLS1`. The coefficients are found by taking the dot product between `PLS1` and the attribute in question and dividing the result by the dot product between `PLS1` and itself. The resulting univariate regression equations are:

`CHMIN = 0.0438 PLS1`

![Equation](images/F000078si7.png)

`CHMAX = 0.0444 PLS1`.

![Equation](images/F000078si8.png)

[Table 6.1C](#Ch006_209-259_B9780443158889000078.xhtml#t0010) shows the CPU data in preparation for finding the second partial least squares’ direction. The original values of `CHMIN` and `CHMAX` have been replaced by residuals, that is, the difference between the original value and the output of the corresponding univariate regression equation given earlier (the target value `PRP` remains the same). The entire procedure is repeated using this data as input to yield the second partial least squares direction, which is

`PLS2 = -23.6002 CHMIN + -0.4593 CHMAX`.

![Equation](images/F000078si9.png)

After this last partial least squares direction has been found, the attribute residuals are all zero. This reflects the fact that, as with principal component analysis, the full set of directions accounts for all of the variance in the original data.

When the partial least squares directions are used as input to linear regression, the resulting model is known as a `partial least squares regression model`. As with principal component regression, if all the directions are used, the solution is the same as that obtained by applying linear regression to the original data.

## Independent Component Analysis

Principal component analysis finds a coordinate system for a feature space that captures the covariance of the data. In contrast, `independent component analysis` (`ICA`) seeks a projection that decomposes the data into sources that are `statistically independent`.

Consider the “cocktail party problem,” where people hear music and the voices of other people; the goal is to un-mix these signals. Of course, there are many other scenarios where a linear mixing of information must be unscrambled. Independent component analysis finds a linear projection of the mixed signal that gives the most statistically independent set of transformed variables.

Principal component analysis is sometimes thought of as seeking to transform correlated variables into linearly uncorrelated variables. However, correlation and statistical independence are two different criteria. `Uncorrelated` variables have correlation coefficients of zero, corresponding to zero entries in a covariance matrix. Two variables are considered `independent` when their joint probability is the product of their marginal probabilities. (We will discuss marginal probabilities in [Section 13.1](#Ch014_485-514_B9780443158889000145.xhtml#s0010).)

A quantity called `mutual information` measures the amount of information one can obtain from one random variable given another. It can be used as an alternative criterion for finding a projection of data, based on minimizing the mutual information between the dimensions of the data in a linearly transformed space. Given a model `s = A x`, where `A` is an orthogonal matrix, `x` is the input data, and `s` is the decomposition into the source signals, it can be shown that minimizing the mutual information between the dimensions of `s` corresponds to transforming the data so that the estimated probability distribution of the sources `p(s)` is as far from Gaussian as possible and the estimates `s` are constrained to be uncorrelated.

A popular technique for performing independent component analysis known as `fast ICA` uses a quantity known as the `negentropy J(s) = H(z) - H(s)`, where `z` is a Gaussian random variable with the same covariance variance matrix as `s` and `H(.)` is the “differential entropy,” defined as
