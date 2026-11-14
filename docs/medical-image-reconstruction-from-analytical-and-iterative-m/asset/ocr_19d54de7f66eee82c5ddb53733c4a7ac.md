# 7.6 Worked examples

**Example 1:** The vector M has three components: M_x, M_y, and M_z. Does the magnitude \(\sqrt{M_x^2 + M_y^2 + M_z^2}\) always remain constant?

**Answer** No. During relaxation, M_x and M_y relax to zero faster than M_z relaxes back to its equilibrium maximum value. This makes the magnitude \(\sqrt{M_x^2 + M_y^2 + M_z^2}\) time varying.

**Example 2:** The received MRI signal is converted to a discrete signal via an analog-to-digital converter (ADC). Does the sampling rate of the ADC determine the image resolution?

**Answer** No. The image resolution in MRI is determined by how far out the k-space is sampled. The distance from the farthest sample in the k-space to the origin (i.e., the DC point) gives the highest resolution in the image. The sampling time interval in the ADC determines the image field of view. If the sampling rate of the ADC is not high enough, you will see image aliasing artifacts (e.g., the nose appears at the back of the head).

**Example 3:** Design a pulse sequence that gives a spiral k-space trajectory.

**solution** In this case, the x- and y-gradients must be turned on simultaneously. The generic expressions for k_x and k_y are

```
k_x(t) = \gamma \int_0^t G_x(\tau)d\tau \quad \text{and} \quad k_y(t) = \gamma \int_0^t G_y(\tau) d \tau, \quad (7.23)
```

respectively. On the other hand, a k-space spiral can be expressed as

```
\begin{cases} k_x(t) = a(t)cos(\beta(t)), \\ k_y(t) = a(t)sin(\beta(t)), \end{cases} \quad (7.24)
```

respectively, for some parameters a(t) and b(t). Therefore, we can choose

```
\begin{cases} G_x(t) = \frac{1}{\gamma} \frac{d(a(t)cos(\beta(t)))}{dt}, \\ G_y(t) = \frac{1}{\gamma} \frac{d(a(t)sin(\beta(t)))}{dt}. \end{cases} \quad (7.25)
```