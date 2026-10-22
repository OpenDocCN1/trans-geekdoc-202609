
![](img/f5b5b8709fc3a81631262f22d3552c5e_89_0.png)

Figure 1.40. (a) The Earth and Moon are locked in the motion, rotating within the period of one month. C0 is the location of their common center of mass which is known as the Earth-Moon barycenter. The Earth-Moon system is kept in a dynamical equilibrium by their centrifugal forces, F_c, and their forces of gravitational attraction, F_g. (b) We here consider gravitational forces due to the Moon acting on the particles A, B, and D with unit mass each. These particles are located on the surface of the Earth. The tide-generating forces are the sums of F_g and F_c. Force F_g at D can be split into horizontal (F_gh) and vertical components. The centrifugal force is the same for all particles (points) in and on Earth.

The rotation rate of the body's system can be defined as ω = v_e/r_c = v_m/(r - r_c). Equation (1.126) can then be rewritten as 

$$ \frac{G m_e m_m}{r^2} = m_e \omega^2 r_c = m_m \omega^2 (r - r_c) \implies m_e r_c = m_m (r - r_c) $$ 

or 

$$ r_c = \frac{m_m}{m_e + m_m} r , $$ 

and thus we can deduce the barycenter location. Note that the Earth is a rigid body, so every material point in it executes an identical orbit, and therefore all its points are subject to the same centrifugal force. Gravitational forces, however, will vary because they vary with the distance between points on Earth and the center of the Moon, as described in equation (1.3) and illustrated in Figure 1.40b.

Let us now consider the Sun-Earth system. The mean distance between the center of the Sun and the center of the Earth is about 1.5 \times 10^{8} km. Their center of mass is located about 450 km (mean) from the center of the Sun. The Sun and the Earth revolve around this common center of mass in one year.

## 1.2.2. Tide-Generating Forces

Figure 1.40b shows two particles with unit mass located at points A and B on opposite sides of the Earth. Point A is the point of the Earth's surface closest to the Moon and point B is the point of the Earth's surface furthest from the Moon. We will analyze how the Moon alters the forces on these two particles. At the center of the Earth, the gravitational force of the Moon is 

$$ \mathbf{F}_{g,O}^{(m)} = \frac{G m_m}{r^2} \mathbf{i}_1 . $$ 

Because of the balance of forces, the centrifugal force at the Earth's center is directed away from the Moon; i.e., 

$$ \mathbf{F}_c^{(m)} = - \frac{G m_m}{r^2} \mathbf{i}_1 . $$ 

At point A on the side of the Earth facing the Moon, the gravitational force of the Moon is 

$$ \mathbf{F}_{g,A}^{(m)} = \frac{G m_m}{(r - R)^2} \mathbf{i}_1 . $$ 

This force is directed toward the Moon, of course and its magnitude is greater than at the center of the Earth because it is closer to the Moon. At point A (see Figure 1.40b), the net Moon's gravitational force is 

$$ \mathbf{F}_A^{(m)} = \mathbf{F}_{g,A}^{(m)} + \mathbf{F}_c^{(m)} = \mathbf{F}_{g,A}^{(m)} - \mathbf{F}_{g,O}^{(m)} $$ 

or 

$$ \mathbf{F}_A^{(m)} = \left[ \frac{G m_m}{(r - R)^2} - \frac{G m_m}{r^2} \right] \mathbf{i}_1 \approx \left[ \frac{G m_m}{r^2} \left(1 + \frac{2R}{r}\right) - \frac{G m_m}{r^2} \right] \mathbf{i}_1 = \frac{2 G m_m R}{r^3} \mathbf{i}_1 .$$

This force is the sum of the attractive force by the Moon and the centrifugal force (or the differences between the gravitational attraction at the center of the Earth and the gravitational attractions at point A), which corresponds to a force directed toward the Moon, and the “tide-generating” force is $F_A^{(m)}$. We used the fact that $(R/r) \ll 1$ as $R/r \approx 1/60$ to carry out the expansion $1/(1-\alpha)^2 \approx 1+2\alpha$ for small $\alpha = R/r$ to obtain the net force toward the Moon in (1.132). The gravitational force of the Earth is not included in (1.132).

At point B, the gravitational field of the Moon is

$$\mathbf{F}_{g,B}^{(m)} = \frac{G m_m}{(r+R)^2} \mathbf{i}_1 \tag{1.133}$$

while the centrifugal force given in (1.129) is the same at $B$. At this point, the magnitude of the gravitational force is less than at the center of the Earth because it is further away from the Moon. The net Moon’s gravitational force at point B is

$$\begin{aligned}
\mathbf{F}_B^{(m)} &= \mathbf{F}_{g,B}^{(m)} - \mathbf{F}_{g,O}^{(m)} = \left[ \frac{G m_m}{(r+R)^2} - \frac{G m_m}{r^2} \right] \mathbf{i}_1 \\
&\approx \left[ \frac{G m_m}{r^2} \left(1 - \frac{2R}{r}\right) - \frac{G m_m}{r^2} \right] \mathbf{i}_1 \\
&= -\frac{2 G m_m R}{r^3} \mathbf{i}_1 .
\end{aligned} \tag{1.134}$$

So the gravitational force prevails over the centrifugal force on point A closest to the Moon and the centrifugal force prevails on point B further from it. In other words, the opposite hemispheres have net forces in opposite directions, causing the ocean to bulge on both sides, as illustrated in Figure 1.40b. The net attraction at point A causes the water on this “near side” of the Earth to be pulled toward the Moon. At point B, the centrifugal force exceeds the gravitational force, and the water tries to keep going in a straight line, moving away from the Earth, also forming a bulge. Thus, the combination of gravity and inertia creates two bulges of water. The bulges on opposite sides of the Earth are proportional to the ratio $m_m / r^3$.

The Sun also affects the size and position of the two tidal bulges. These effects on opposite sides of the Earth, which are approximately proportional to the ratio $m_s / r_s^3$, also give rise to solar tidal forces; i.e.,

$$\mathbf{F}_A^{(s)} \approx \frac{2 G m_s R}{r_s^3} \mathbf{i}_1 , \tag{1.135}$$ 

$$\mathbf{F}_B^{(s)} \approx -\frac{2 G m_s R}{r_s^3} \mathbf{i}_1 , \tag{1.136}$$

where $m_s$ is the mass of the Sun and $r_s$ is the distance between the center of the Earth and the center of the Sun. But because of the much greater distance of the Sun to the Earth, the ratio $m_s / r_s^3$ for the Sun is only about half of that for the Moon [$m_s = 27.07 \times 10^6 m_m$ and $r_s^3 = (389)^3 r^3 = 58.8 \times 10^6 r^3$]. Basically, the gravitational force varies inversely as the square of the distance between the two bodies and the tide-generating force varies inversely as the cube of the distance. This latter observation accounts for the Moon being 2.18 times more influential in causing tides than the Sun.

![](img/f5b5b8709fc3a81631262f22d3552c5e_92_0.png)

Figure 1.41. An illustration of the declination which is the angular distance of the Moon above or below Earth’s equator. The two tidal bulges track the changes in lunar declination.

For simplicity, we have presented the tide-generating forces for selected points A and B (see Figure 1.40b), which are positioned on a line connecting the centers of the Earth and the Moon (or Sun). This representation is incomplete. Each point of the Earth, including the one labeled D, experiences the radial gravity of the Moon and Sun, and therefore the tidal forces, differently. However, only the tidal forces’ horizontal components actually tidally accelerate the water particles since there is almost no resistance. In other words, horizontal components are more effective at moving water than the vertical components that try to lift water. Thus, on the surface of the Earth, the lateral tide-generating forces are more significant than the vertical forces in generating the tide bulges.

Over time, the positions of the Moon and Sun change relative to the Earth’s equator. These changes have a direct effect on daily tidal heights and intensity. As the Moon revolves around the Earth, its angle increases and decreases in relation to the Earth’s equator. This angle is known as its declination (see Figure 1.41). Similarly, the Sun’s relative position to the Earth’s equator changes over the course of a year as the Earth rotates around it. The Sun’s declination also affects the tides. Let us look at specific examples of the declination effects of the Moon and Sun on tides. When the Sun, Moon, and Earth are in alignment (as at the times of the new Moon or full Moon), the two tidal effects reinforce one another, and the solar tide has an additional effect on the lunar tide, creating extra-high tides and very low tides (shown in Figure 1.42a). These tides are called spring tides.
