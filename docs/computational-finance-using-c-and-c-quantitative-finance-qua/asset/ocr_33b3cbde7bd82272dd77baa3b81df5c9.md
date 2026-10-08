# Computational Finance Using C and C#

The Box–Muller method is contained in Eq. (3.3.5), which shows that the N(0,1) variates are generated in pairs from the uniform U(0,1) variates $V_1$ and $V_2$.

Since the N(0,1) variates are created two at a time, if we want to generate a normal distribution with an odd number of dimensions, $n_{odd}$, it is necessary to generate $n_{add} + 1$ dimensions and discard one of the dimensions.

It is easy to modify Eq. (3.3.5) so that we can specify the means and variances of the variates $x$ and $y$; this is accomplished as follows:

```
$x = \sigma_1(-2 \log V_1)^{1/2} \cos 2\pi V_2 + \mu_1$,$
y = \sigma_2(-2 \log V_1)^{1/2} \sin 2\pi V_2 + \mu_2$
```

where the distributions of $x$ and $y$ are

$x \sim N(\mu_1, \sigma_1^2)$ and $y \sim N(\mu_2, \sigma_2^2)$

Code excerpt 3.1 illustrates how to generate quasi-random normal variates with given mean and standard deviation.

```
long Quasi_Independent(long fcall, long seq, double xmean[], double std[],
long idim, double quasi[])
/*
* Input parameters:
fall -- if fcall == 1 then it is an initialisation call,
      if fcall == 0 then a continuation call
seq -- if seq == 0 then a random sequence, seq == 1 then a Niederre sequence,
      seq == 2 then a Sobol sequence
xmean[] -- the means of the independent normal variates
std[] -- the standard deviation of the independent normal variates, must be less than 40
idim

Output parameters:
quasi[] -- the elements quasi[]; quasi[idim-1] contain the independent normal variates
*/
long ierr, i, j;
double v1, v2, p1;
long indi, indi2;
#define QUASI(i) quasi[(i)-1]
#define STD(i) std[(i)-1]
#define MEAN(i) mean[(i)-1]

if ((idim / 2) * 2 != idim) {
    printf("Error on entry, idim = %ld\n", %ld", idim, idim);
    return 1;
} else if (idim > 40) {
    printf("Error on entry, idim = %ld\n", %ld", idim, idim);
    return 1;
}

for (i = 0; i < idim; i++) {
    if (STD(i) < 0.0) {
        printf("%d entry, the standard deviation is not greater than zero:\n               STD(%d) = %12.4f\n", i, STD(i));
        return 1;
    }
}

pi = 4.0*atan(1.0);
```

**Code excerpt 3.1** Generating quasi-random normal variates using the Box–Muller trans-formation.

*