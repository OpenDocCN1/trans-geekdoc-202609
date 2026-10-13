
Our starting point is the simple problem of a *linearly separable* two-class (*ω*₁, *ω*₂) classification task. In other words, we are given a set of training samples, (*y*[*n*], **x**[*n*]), *n* = 1, 2, …, *N*, with *y*[*n*] ∈ {−1, +1}, **x**[*n*] ∈ ℝ^(*l*) and it is assumed that there is a hyperplane,

**θ**[*]*^(*T*)**x** = 0,

such that

**θ**[*]*^(*T*)**x** > 0, if **x** ∈ *ω*₁, **θ**[*]*^(*T*)**x** < 0, if **x** ∈ *ω*₂.

In other words, such a hyperplane classifies correctly *all* the points in the training set. For notational simplification, the bias term of the hyperplane has been absorbed in **θ**[*] after extending the dimensionality of the input space by one, as has been explained in Chapter [3](#Chp003_65-117_B9780443292385000093.xhtml) and used in various parts of this book.

The goal now becomes that of developing an algorithm that iteratively computes a hyperplane that classifies correctly all the patterns from both classes. To this end, a cost function is adopted.

*The perceptron cost*: Let the available vector estimate at the current iteration step of the unknown parameters^([^(115)](#fn115))

![Equation](images/B978044329238500024X/fx001.jpg)(18.1)

where

```
y_n = { +1, if x ∈ ω_1,
       -1, if x ∈ ω_2. }(18.2)
```
