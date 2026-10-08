
# Generation of random variables

We now use the decomposition:

$\tilde{C} = VK(VK)^T$

Under these circumstances the p-element vectors $Y$ and $Y'$ are generated using the following modified versions of Eqs. (3.4.4) and (3.4.5):

$Y = VKX$ and $Y' = VKX + \mu$

The method for generating variates $Y$ from a given correlation matrix $C_r$ is identical. In this case nonpositive definite matrices are repaired as $\tilde{C}_r = FVK(FVK)^T$; see Section 3.4.2.

A function to generate correlated normal and lognormal variates is given in Code example 3.2.

```c
long Quirasandom_Normal_Lognormal_Correlated(long fcall, long seq, long innorm,
    double means[], long n, double c[], long tdc, double xtol, long *irank,
    double x[], double work[], long *lw) {

/* Input parameters:
=====================
call if fcall == 1 then it is an initialization call,
if fcall == 0 then a continuation call
 seq == 0 then a Faure sequence, if seq == 1 then a Niederer sequence,
if seq == 2 then a Sobol sequence
 innorm == 1 then it is a lognormal distribution,
if innorm == 0 then a normal distribution
 * the number of variates, n must be less than 40
c a matrix which contains the required covariance matrix, C
tdc the second dimension of the matrix C
tol the tolerance used for calculating the rank of the covariance matrix C
means the means of the variates
std the standard deviations of the independent variates
lwk the size of the work array, work

Output parameters:
=================
rank the computed rank of the covariance matrix C
x[] the elements x[0], ... x[n-1] contain the variates

Input/Output parameters:
=================
work a work array
*/
double zero = 0.0, one = 1.0, two = 2.0;
long i, j, k, kk;
double mti, alpha;
long ptr, ptrv, ptrw, ptrw0, ptrw1;
#define C(I,J) c[(I)-(1)] + tdc + ((J)-(1)]
#define MEANS(I) means[(I)-(1)]
#define X(I) x[(I)-(1)]
#define WORK(I) work[(I)-(1)]

if (lw < (2 + 3*n + 2*n + 3)) {
    printf("Error lw is too small \n");
    return 1;
}

ptr = n+2;
ptrv = n+2;
ptrw = n*n + n + 2;
```

**Code example 3.2** The function Quirasandom_Normal_Lognormal_Correlated generates correlated quasi-random normal variates and correlated quasi-lognormal variates.

```c
/* add i to allow for odd values of n */
ptr0 = ptrw + 1 + n;
ptrw1 = ptrw0 + 1 + n;
ptrc = ptrw + n + 1;
ni = n;
if ((n/2) != n) { /* test for odd n */
    n = n + 1;
}
if (ifall) { /* first call for initialisation */
    if (iform) { /* normal distribution */
        for (i = 1; i < n; i++) { /* Load the covariance matrix into WORK */
            for (j = 1; j < n; j++) {
                WORK(ptrc+(i-1)*n+j-1) = log(one+ C(i,j))/(means(i)*means(j));
            }
        }
    } else {
        for (i = 1; i < n; i++) { /* Load the covariance matrix into WORK */
            for (j = 1; j < n; j++) {
                WORK(ptrc+(i-1)*n+j-1) = C(i,j);
            }
        }
    }

/* calculate the eigenvalues and eigenvector of the matrix that
has been loaded into WORK */
calc_eigvals_eigvec(n, &WORK(ptrc), &WORK(ptrw), &WORK(ptrv), &ptrnv);
/* The code uses NAG routine 020abc */
irank = 0;
printf("*the eigenvalues are %d\n", irank);
for (j = 1; j <= irank; j++) {
    printf("*%12.5f\n", ptrv+(j-1));
}

for (j = irank; j <= n-1; j++) { /* use the eigenvalues to calculate the rank of the matrix */
    if (WORK(ptrv+(i-1)*j) < tol) goto L24;
    irank = irank + 1;
}
printf("*irank = %d,*irank;\n", irank,irank);
L24:
mtol = -tol;
if (WORK(ptrv) < mtol) {
    printf("*warning there is an eigenvalue less than %12.4f %d\n", mtol);
}
for (j = 1; j <= irank; j++) {
    kk = 0;
    for (k = 1; k < n; k++) {
        if (WORK(ptrv+(k-1)*n+(j-1)) != 0) goto L28;
        kk = kk + 1;
    }
}
L28:
/* ensure that all eigenvalues have the same sign on different machines */
if (WORK(ptrv+(kk-1)*n+(j-1)) < 0) alpha = -sqrt(ptrv+(j-1));
for (i = 1; i <= n; i++) {
    WORK(ptrv+(i-1)*n+(j-1)) = WORK(ptrv+(j-1)+(i-1)*n)*alpha;
}
}

printf("*the eigenvectors are %d\n", irank);
for (j = 1; j <= irank; j++) {
    for (i = 1; i <= n; i++) {
        printf("*%10.5f, WORK(%d)\n", ptrv+(j-1)+(i-1)*n));
    }
}
printf("*\n");
}

for (i = 1; i <= n; i++) {
    /* store vector of ones and zeros for generating the quasi-random numbers */
    WORK(ptrw0+i-1) = zero;
    WORK(ptrw1+i-1) = one;
}
```

Code 3.2 (Continued).

# Generation of random variables

```c
for (i = n; i <= n; i++) {
    WORK(ptrw0+i-1) = zero;
    WORK(ptrw1+i-1) = one;
}
/* end of first call */

/* generate a vector of Normal variables from a standard distribution,
zero mean and variance */
Quasi_Normal_Independent(fcall, seq, &WORK(ptrw0), &WORK(ptrw1), n1, &WORK(ptrw));

printf("The quasi random numbers are:\n");
for (i = 1; i <= n; i++) {
    printf("%.12f \n", WORK(ptrw+(i-1)));
}
/* Now generate variates with the specified mean and variance */
if (inorm) /* a lognormal distribution */
    for (i = 1; i <= n; i++) {
        X(i) = log(MEAN(i) + WORK(ptrc+(i-1)*n+i-1)/two);
        for (k = 1; k <= rank[i]; k++) {
            X(i) = X(i) + WORK(ptrw+(k-1)*n + (i-1));
        }
    }
else /* a normal distribution */
    for (i = 1; i <= n; i++) {
        X(i) = MEANS(i);
        for (k = 1; k <= rank[i]; k++) {
            X(i) = X(i) + WORK(ptrw+(k-1)*n + (i-1));
        }
    }
printf("The generated variates are:\n");
for (i = 1; i <= n; i++) {
    printf("%.12f \n", X(i));
}
return 0;
```

Code 3.2 (Continued).

In order to visualize the effect of a covariance matrix we will display the results using function Quirasandom_Normal_Lognormal_Correlated to generate the following variates:

- A vector of three independent variates with covariance matrix:
$C_1 = \begin{pmatrix} 1.0 & 0.0 & 0.0 \\ 0.0 & 1.0 & 0.0 \\ 0.0 & 0.0 & 1.0 \end{pmatrix}$

- A vector of three normal variates in which the elements of the covariance matrix are positive:
$C_2 = \begin{pmatrix} 1.0 & 0.8 & 0.8 \\ 0.8 & 1.0 & 0.8 \\ 0.8 & 0.8 & 1.0 \end{pmatrix}$

![img/603dc1da1bd8dca364a8fe29eaa_68_0.png]

**Figure 3.5** Scatter diagram for a sample of 3000 observations $(Z_i, i = 1, \dots, 3000)$ generated from a multivariate distribution consisting of three variates with covariance matrix $C$ and mean $\mu$. Here we plot the values of the first variate against the values of the second. If we use the notation of Eq. (3.4.2), then the $(x, y)$ coordinates for the points are $x_i = Z_{i,1}, i = 1, \dots, 3000$, and $y_i = Z_{i,2}, i = 1, \dots, 3000$.

- A vector of three normal variates in which elements of the covariance matrix are negative:
$C_3 = \begin{pmatrix} 1.0 & -0.7 & 0.2 \\ -0.7 & 1.0 & 0.2 \\ 0.2 & 0.2 & 1.0 \end{pmatrix}$

In all cases the mean vector is given by:
$\mu = \begin{pmatrix} 2.0 \\ 2.0 \\ 2.0 \end{pmatrix}$

The results are displayed in Figs. 3.5–3.7.

# 3.4.4 Lognormal distribution

The multivariate lognormal distribution is important because it is the asset return assumed by the Black-Scholes equation.

Let the $p$-element vectors $Y$ and $X$ be related by $Y = \log(X)$ where $Y \sim N(\mu, \Sigma)$, $\mu$ is a $p$-element vector, and $\Sigma$ is a $p \times p$ matrix. Then $X = \exp(Y)$ and $X$ has multivariate lognormal distribution, which we denote by $X \sim \Lambda(\mu, \Sigma)$. We will represent the $p$-element mean vector of $X$ by $\hat{m}$ and the $p \times p$ covariance matrix of $X$ by $\mathcal{S}$.

![img/603dc1da1bd8dca364a8fe29eaa_69_0.png]

**Figure 3.6** Scatter diagram for a sample of 3000 observations $(Z_i, i = 1, \dots, 3000)$ generated from a multivariate distribution consisting of three variates with covariance matrix $C_2$ and mean $\mu$. Here we plot the values of the first variate against the values of the second variate. If we use the notation of Eq. (3.4.2), then the $(x, y)$ coordinates for the points are $x_i = Z_{i,1}, i = 1, \dots, 3000$, and $y_i = Z_{i,2}, i = 1, \dots, 3000$.

![img/603dc1da1bd8dca364a8fe29eaa_69_1.png]

**Figure 3.7** Scatter diagram for a sample of 3000 observations $(Z_i, i = 1, \dots, 3000)$ generated from a multivariate distribution consisting of three variates with covariance matrix $C_3$ and mean $\mu$. Here we plot the values of the first variate against the values of the second variate. If we use the notation of Eq. (3.4.2), then the $(x, y)$ coordinates for the points are $x_i = Z_{i,1}, i = 1, \dots, 3000$, and $y_i = Z_{i,2}, i = 1, \dots, 3000$.
