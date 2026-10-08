# Generation of random variables

We now use the decomposition:

$	ilde{C} = VK(VK)^T$

Under these circumstances the p-element vectors $Y$ and $Y'$ are generated using the following modified versions of Eqs. (3.4.4) and (3.4.5):

$Y = VKX$ and $Y' = VKX + \mu$

The method for generating variates Y$ from a given correlation matrix $C_r$ is identical. In this case nonpositive definite matrices are repaired as $	ilde{C}_r = FVK(FVK)^T$; see Section 3.4.2.

A function to generate correlated normal and lognormal variates is given in Code example 3.2.

```
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

ptre = n+2;
ptrv = n+2;
ptrw = n*n + n + 2;
```

**Code example 3.2** The function Quirasandom_Normal_Lognormal_Correlated generates correlated quasi-random normal variates and correlated quasi-lognormal variates.