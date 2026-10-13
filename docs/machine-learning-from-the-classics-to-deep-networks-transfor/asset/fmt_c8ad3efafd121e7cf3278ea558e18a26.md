
### 4.8.1 The lattice-ladder scheme

So far, we have been involved with the so-called *transversal* implementation of a linear time-invariant FIR filter; in other words, the output is expressed as a convolution between the impulse response and the input of the linear structure. Levinson's algorithm provided a computationally efficient scheme for obtaining the MSE-optimal estimate `w*`. We now turn our attention to an equivalent implementation of the corresponding linear filter, which comes as a direct consequence of Levinson's algorithm.

Define the error signals associated with the *m*th-order optimal forward and backward predictors at time instant *n* as

```
e[m]^(f)(n) := u[n] - a[m]^(H) u[m](n - 1)
```

where `u[m](n)` is the input random vector of the *m*th-order filter, and the order of the filter has been explicitly brought into the notation.^([^(24)](#fn24))

```
e[m]^(b)(n) := u[n - m] - b[m]^(H) u[m](n) = u[n - m] - a[m]^(T) J[m] u[m](n)
```

Employing Eq. [(4.75)](#Chp004_119-175_B978044329238500010X.xhtml#deq129), the order recursion in Eq. [(4.72)](#Chp004_119-175_B978044329238500010X.xhtml#deq126), and the partitioning of `u[m](n)`, which is represented by

```
u[m](n) = [u[m - 1]^(T)(n), u[n - m + 1]]^(T) = [u[n], u[m - 1]^(T)(n - 1)]^(T)
```

in Eq. [(4.74)](#Chp004_119-175_B978044329238500010X.xhtml#deq128), we readily obtain
