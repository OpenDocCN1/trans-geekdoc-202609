
We have relaxed the notational dependence of `Σ` on `u` and we have instead explicitly indicated the order of the matrix, because this will be a very useful index from now on.

We will follow a recursive approach, and our aim will be to express the optimal filter solution of order `m`, denoted from now on as `w[m]`, in terms of the optimal one, `w[m-1]`, of order `m-1`.

The covariance matrix of a wide-sense stationary process is a `Toeplitz` matrix; all the elements along *any* of its diagonals are equal. This property together with its Hermitian nature gives rise to the following *nested* structure:

```
Σ_m = [ Σ_{m-1}       J_{m-1} r_{m-1} ]
      [ r_{m-1}^H J_{m-1}   r(0)       ]
```
(4.60)

```
= [ r(0)         r_{m-1}^T ]
  [ r_{m-1}^*    Σ_{m-1}   ],
```
(4.61)

where

```
r_{m-1} := [ r(1) ]
           [ r(2) ]
           [ ⋮    ]
           [ r(m-1) ]
```
(4.62)

and `J[m-1]` is the antidiagonal matrix of dimension `(m-1) × (m-1)`, defined as:

![Equation](images/B978044329238500010X/fx014.jpg)

Note that right-multiplication of any matrix by `J[m-1]` reverses the order of its columns, while multiplying it from the left reverses the order of the rows as follows:
