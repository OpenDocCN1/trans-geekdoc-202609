Surprisingly, the first of Kepler’s laws, that the planetary paths are elliptical, is the toughest to prove beginning with Newton’s assumption of inverse-square gravitation. Newton himself did it with an ingenious geometrical argument, famously difficult to follow. It can be demonstrated easily using calculus, but even this is non-trivial, and we shall work through it later. The most effective strategy is to attack the laws in reverse order. Thus, we start with the third law under the assumption of circular orbits.

Again, formulas of the satellite’s orbital speed, in (1.6), and of the period of the satellite’s orbit in (1.7) are also valid for the planets (i.e., mass $m_2$) around the Sun. We simply replace the orbiting satellite with the orbiting planet (i.e., mass $m_2$) and the Earth with the Sun (i.e., mass $m_1$). Therefore, by substituting (1.6), in (1.7), we obtain the ratio of the square of the period over the cube of the radius $r$, thus, Kepler’s third law; i.e.,

$$\frac{T^2}{r^3} = \frac{4\pi^2}{G m_1} = k = \text{constant} \tag{1.31}$$

The coefficient of proportionality $k = T^2 / r^3$ is known as Kepler’s constant. It has the same numerical value for all of the Sun’s planets (the Earth, Mars, Venus, Mercury, Jupiter, etc.), as illustrated in Table 1.1. The Moon has a different Kepler’s constant because it orbits a different object, the Earth and not the Sun. In more general terms, $k$ has the same numerical value if the object being orbited stays the same. Note that we will generalize the proof of this third law to elliptic orbits later by replacing the orbital radius, $r$, with the semi-major axis of the ellipse (see Figure 1.10) with $a$.

We can write out Kepler’s third law a couple of different ways by rearranging parameters and variables so that we can cancel out some terms and facilitate some calculations. For example, we know that Kepler’s constant is the same for the planets orbiting the same object, so we can equate the formulas of the Earth and Mars together, as follows:

$$\frac{T_{\text{earth}}^2}{r_{\text{earth}}^3} = \frac{T_{\text{mars}}^2}{r_{\text{mars}}^3} \tag{1.32}$$

**Table 1.1.** Different Kepler’s constants, $k$. Other parameters are the length of year $T$ for each planet in the solar system, and its average distance from the Sun $r$. The Earth, Mars, and Venus give approximately the same value for Kepler’s constant, confirming that Kepler’s third law is correct in predicting that there is a constant ratio between the squared period and cubed radius of objects orbiting the same object. The Moon has a different Kepler’s constant because it orbits a distinct object, the Earth and not the Sun.

| Planet & satellite | Orbit | T (days) | r (km) | k (days²/km³) |
|---|---|---|---|---|
| Earth | Sun | 365 | 149 × 10⁶ | 4.03e-20 |
| Mars | Sun | 684 | 228 × 10⁶ | 3.95e-20 |
| Venus | Sun | 225 | 108 × 10⁶ | 4.01e-20 |
| Moon | Earth | 27.32 | 384400 | 1.31e-14 |