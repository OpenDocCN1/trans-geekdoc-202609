
## 6. 17.11

Reproduce [Fig. 17.10](#Chp017_855-884_B9780443292385000238.xhtml#f0060) for the stochastic volatility model of [Example 17.3](#Chp017_855-884_B9780443292385000238.xhtml#enun0065) and observe how the estimated sequence `x̂[n]` follows the true sequence `x[n]` based on the observations `y[n]`.

## 7. 17.12

Develop the MATLAB® code to reproduce the visual tracking of the circle of [Example 17.4](#Chp017_855-884_B9780443292385000238.xhtml#enun0070). Because, at each time instant, we are only interested in `x[n]` and not in the whole sequence, modify the SIS sampling in [Algorithm 17.4](#Chp017_855-884_B9780443292385000238.xhtml#enun0030) to care for this case.

## 8.

Specifically, given Eqs. [(17.28)](#Chp017_855-884_B9780443292385000238.xhtml#deq38) and [(17.29)](#Chp017_855-884_B9780443292385000238.xhtml#deq39), in order to estimate `x[n]` instead of `x[1:n]`, Eq. [(17.31)](#Chp017_855-884_B9780443292385000238.xhtml#deq41) is simplified to

```
p(x_n|y_{1:n}) = \frac{p(y_n|x_n)p(x_n|y_{1:n - 1})}{p(y_n|y_{1:n - 1})},
```
(17.50)

### 1.

where

```
p(x_n|y_{1:n-1}) = \int_{x_{n-1}} p(x_n|x_{n-1}) p(x_{n-1}|y_{1:n-1}) dx_{n-1}.
```
(17.51)

### 1.

The samples are now weighted as
