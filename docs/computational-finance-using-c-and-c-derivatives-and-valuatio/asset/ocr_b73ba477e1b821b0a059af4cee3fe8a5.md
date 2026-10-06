# 52 CHAPTER 3 Generation of Random Variates

```
/*
for (i = 1; i < n; i++) { / store a vector of ones and zeros for generating the quasi-random numbers /
  WORK(ptrw(i-1)) = zero;
  WORK(ptrw(i+1)) = one;
}

for (i = m; i <= n1; i++) {
  WORK(ptrw(i-1)) = zero;
  WORK(ptrw(i+1)) = one;
}
/* end of first call section */

/* generate a vector of n random numbers from a standard normal distribution, zero mean and unit variance /
QuasiRandom(call, seq, AWORK(ptrw), AWORK(ptrw), n1, AWORK(ptrw));

printf("/ The quasi random numbers are:\n");
for (i = 1; i <= n; i++) {
  printf("%12.4f\n", WORK(ptrw(i-1)));
}

/* Generate variates with the specified mean and variance /
if (log(variance) < 0) {
  for (i = 1; i <= n; i++) {
    X(i) = log(-MEANS(i))*WORK(ptrc-(i-1)*m+i)/2);
    for (k = 1; k < rank[i]; k++) {
      X(i)-X(k)*WORK(ptrv-(k-1)+(i-1))*WORK(ptrw-k);
    }
  }
} else {
  for (i = 1; i <= n; i++) {
    X(i) = MEANS(i);
    for (k = 1; k < rank[i]; k++) {
      X(i)-X(k)*WORK(ptrv-(k-1)+(i-1))*WORK(ptrw-k);
    }
  }
}

printf("// The generated variates are:\n");
for (i = 1; i <= n; i++) {
  printf("%12.4f\n", X(i));
}

return 0;
```

**Code excerpt 3.2 (Continued).**

In order to visualize the effect of the covariance matrix, we will display the results of function Quasirandom_Normal_LogNormal_Correlated to generate the following variates:

+   * A vector of three normal independent variates with covariance matrix

![](bbox=[0.403, 0.693, 0.596, 0.773])

+   * A vector of three normal variates in the elements of the covariance matrix are all positive; the covariance matrix

![](bbox=[0.403, 0.837, 0.596, 0.917])