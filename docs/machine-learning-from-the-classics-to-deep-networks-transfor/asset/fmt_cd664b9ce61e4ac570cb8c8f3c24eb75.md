
## Visual tracking

Consider the problem of visual tracking of a circle, which has a constant and known radius. We seek to track its position, that is, the coordinates of its center, **x** = [*x*[1], *x*[2]]^T. This vector will comprise the state variable. The model for generating the observations is given by

```
x_n = x_{n-1} + η_n,
y_n = x_n + v_n,
```

where **η**[n] is a uniform noise in the interval [−10, 10] pixels, for each dimension. Note that due to the uniform nature of the noise, Kalman filtering, in its standard formulation, is no longer the optimal choice, in spite of the linearity of the model. The noise **v**[n] follows a Gaussian PDF 𝒩(**0**, Σ[v]), where

```
Σ_v = [[2, 0.5],
       [0.5, 2]].
```

Initially, the target circle is located in the image center. The particle filter employs *N*=50 particles and the SIS sampling method was used (see, also, Computer Exercise 17.12).

Figure 17.11 shows the circle and the generated particles, which attempt to track the center of the circle from the noisy observations, for different time instants. Observe how closely the particles track the center of the circle as it moves around. A related video is available from the companion site of this book.

![Figure 17.11 The circle (in gray) and the generated particles (in red) for time instants n=1, n=30, n=60, and n=120.](images/B9780443292385000238/gr011.jpg)

## Problems

### 17.1

Let

```
μ := 𝔼[f(x)] = ∫ f(x) p(x) dx
```

and let *q*(**x**) be the proposal distribution. Show that if
