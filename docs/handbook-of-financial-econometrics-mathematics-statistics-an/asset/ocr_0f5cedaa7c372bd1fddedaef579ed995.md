Equation (85.66) represents a joint PDF for X and Y. If ρ = 0, then equation (85.66) becomes

f(X,Y) = f(X)f(Y). (85.69)

This implies that the joint PDF of X and Y is equal to the PDF of X times the PDf of Y. We also know that both X and Y are normally distributed. Therefore, X is independent of Y.

# Example 85.1. Using a Mathematics Aptitude Test to Predict Grade in Statistics.

Let X and Y represent scores in a mathematics aptitude test and numerical grade in elementary statistics, respectively. In addition, we assume that the parameters in equation (85.66) are

μ_X = 550   σ_X = 40   μ_Y = 80   σ_Y = 4   ρ = 0.7.

Substituting this information into equations (85.67) and (85.68), respectively, we obtain

E(Y|X) = 80 + 0.7(4/40)(X − 550) = 41.5 + 0.07X,   (85.70)
σ²(Y|X) = (16)(1 − 0.49) = 8.16.   (85.71)

If we know nothing about the aptitude test score of a particular student (say, john), we have to use the distribution of Y to predict his elementary statistics grade.

95% interval = 80±(1.96)(4) = 80 ± 7.84.

That is, we predict with 95% probability that John's grade will fall between 87.84 and 72.16.

Alternatively, suppose we know that John's mathematics aptitude score is 650. In this case, we can use equations (85.70) and (85.71) to predict John's grade in elementary statistics.

E(Y|X = 650) = 41.5 + (0.07)(650) = 87,

and

σ²(Y|X) = (16)(1 − 0.49) = 8.16.

We can now base our interval on a normal probability distribution with a mean of 87 and a standard deviation of 2.86.

95% interval = 87±(1.96)(2.86) = 87 ± 5.61.