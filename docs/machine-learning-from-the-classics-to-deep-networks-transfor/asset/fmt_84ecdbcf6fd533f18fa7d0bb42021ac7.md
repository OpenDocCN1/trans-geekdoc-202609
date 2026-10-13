
and, also, the optimal MSE for the forward prediction, `J(a[m]) := α[m]^(f)`, is equal to that for the backward prediction, i.e.,

`J(a[m]) = α[m]^(f) = α[m]^(b) = J(b[m])`.

![Equation](images/B978044329238500010X/si301.png)

[Fig. 4.16](#Chp004_119-175_B978044329238500010X.xhtml#f0085) depicts the two prediction tasks. In other words, the optimal forward predictor is the conjugate reverse of the backward one, so that

```
a_m := [a_m(0); ...; a_m(m-1)] = J_m b_m^* := [b_m^*(m-1); ...; b_m^*(0)].
```

![Equation](images/B978044329238500010X/si302.png)

![Figure 4.16 The impulse response of the backward predictor is the conjugate reverse of that of the forward predictor.](images/B978044329238500010X/gr016.jpg)

[Figure 4.16](#Chp004_119-175_B978044329238500010X.xhtml#cf0865) The impulse response of the backward predictor is the conjugate reverse of that of the forward predictor.

This property is due to the stationarity of the involved process. Because the statistical properties only depend on the difference of the time instants, forward and backward predictions are not much different; in both cases, given a set of samples, `u[n-m+1], ..., u[n]`, we predict *one* sample ahead in the future (`u[n+1]` in the forward prediction) or *one* sample back in the past (`u[n-m]` in the backward prediction).
