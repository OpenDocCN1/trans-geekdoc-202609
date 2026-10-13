
*p*(**y**[*n*]|**x**[*n* − 1]) = ∫*p*(**y**[*n*]|**x**[*n*])*p*(**x**[*n*]|**x**[*n* − 1]) *d***x**[*n*]

![Equation](images/B9780443292385000238/si149.png)

which may not be tractable. Moreover, even if the integral can be computed, sampling from *p*(**y**[*n*]|**x**[*n* − 1]) directly may not be feasible. In any case, even if the optimal proposal distribution cannot be used, we can still select the proposal distribution to be of the form

*q*[*n*](**x**[*n*]|**x**[1 : *n* − 1], **y**[1 : *n*]) = *q*(**x**[*n*]|**x**[*n* − 1], **y**[*n*])

![Equation](images/B9780443292385000238/si151.png)(17.37)

Note that such a choice is particularly convenient, because sampling at time *n* only depends on **x**[*n* − 1] and **y**[*n*], and *not* on the entire history. If, in addition, the goal is to obtain estimates of *p*(**x**[*n*]|**y**[1 : *n*]), then one need not keep in memory all previously generated samples, but only the most recent one, **x**[*n*].

We are now ready to write the first particle filtering algorithm.

### Algorithm 17.4

**SIS particle filtering**

*   •  Select a prior distribution, *p*, to generate particles for the initial state, **x**[0]
*   •  Select the number of particle streams, *N*.
*   •  Select the proposal distribution, *q*.
*   •  **For** *i* = 1, 2, …, *N* **Do**
    1.  –  Draw **x**[0]^((*i*)) ∼ *p*(**x**); Initialize the *N* streams of particles.
    2.  –  Set $w\_{0}^{(i)} = \\frac{1}{N}$; Set all initial weights equal.
*   •  **End For**
*   •  **For** *n* = 1, 2, … **Do**
