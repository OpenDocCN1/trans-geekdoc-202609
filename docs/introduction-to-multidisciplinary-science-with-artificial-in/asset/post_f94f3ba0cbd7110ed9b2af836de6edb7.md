
Table 1.8. Global plate motions with respect to the deep (Hawaii) and shallow (Society) hotspot reference frames. (data: Gripp and Gordon, 2002). The second, third, and fourth columns are related to the deep hotspot and the last three columns are related to the shallow hotspot.

| Plate | Lat | Long | \|ω\| °/Ma | Lat | Long | \|ω\| °/Ma |
|---|---|---|---|---|---|---|
| Antarctic | -47.34 | 74.51 | 0.202 | -59.38 | 86.98 | 1.256 |
| Australian | -0.091 | 44.48 | 0.747 | -38.86 | 62.78 | 1.488 |
| African | -43.39 | 21.14 | 0.199 | -61.75 | 76.73 | 1.213 |
| Pacific | -61.47 | 90.33 | 1.061 | -61.47 | 90.33 | 2.123 |
| Eurasian | -61.90 | 73.47 | 0.205 | -62.35 | 87.51 | 1.265 |
| North American | -74.70 | 13.40 | 0.383 | -67.52 | 79.79 | 1.409 |
| Nazca | 35.88 | -90.91 | 0.323 | -71.73 | 91.65 | 0.782 |
| Cocos | 13.17 | -116.0 | 1.162 | -42.84 | -135.9 | 0.982 |
| Caribbean | -73.21 | 25.92 | 0.283 | -65.54 | 82.59 | 1.322 |
| Arabian | 2.95 | 23.17 | 0.508 | -46.99 | 56.73 | 1.239 |
| Indian | 3.069 | 26.47 | 0.521 | -46.05 | 57.93 | 1.256 |
| South American | -70.58 | 80.40 | 0.436 | -64.18 | 88.12 | 1.492 |
| Juan de Fuca | -39.21 | 61.63 | 1.012 | -51.45 | 72.84 | 2.010 |
| Philippine | -53.88 | -16.67 | 1.154 | -68.89 | 25.66 | 1.999 |
| Scotia | -76.91 | 52.23 | 0.445 | -66.65 | 84.27 | 1.488 |
| Lithosphere | -55.90 | 69.93 | 0.436 | -60.24 | 83.66 | 1.490 |

## 1.4.3. The Global Positioning System: Absolute Motion Using the NNR Frame

No-net-rotation (NNR) frame (also known as the mean-lithosphere reference frame) is another example of an approximate Earth-fixed frame. It is based on the assumption that the sum of lithosphere movements is zero; that is, there is no net rotation of the lithosphere as a whole, and therefore there is no net rotation of its N plates (e.g., Solomon and Sleep, 1974; Minster and Jordan, 1978; and Argus et al., 2010). In this frame, plates are imagined to move relative to a fixed Earth center, and the lithosphere does not move relative to the underlying mantle. So, the sum of the absolute motion of all plates weighted by their area is zero; i.e.,

$$\boldsymbol{L} = \sum_{n=1}^{N}\int_{D_n} \left[ \boldsymbol{x} \times \boldsymbol{v}^{(n)}(\boldsymbol{x}) \right] dS(\boldsymbol{x}) = \sum_{n=1}^{N}\int_{D_n} \left[ \boldsymbol{x} \times \left( \boldsymbol{\omega}^{(n)} \times \boldsymbol{x} \right) \right] dS(\boldsymbol{x})$$
$$= \sum_{n=1}^{N}\int_{D_n} \left[ \boldsymbol{\omega}^{(n)} (\boldsymbol{x} \cdot \boldsymbol{x}) - \boldsymbol{x} \left( \boldsymbol{\omega}^{(n)} \cdot \boldsymbol{x} \right) \right] dS(\boldsymbol{x}) = 0, \tag{1.170}$$

where $\boldsymbol{L}$ is the total angular momentum summation of the Earth’s lithosphere, $\boldsymbol{v}^{(n)} = \boldsymbol{\omega}^{(n)} \times \boldsymbol{x}$ is the linear horizontal velocity vector of the corresponding surface position vector $\boldsymbol{x}$, $dS(\boldsymbol{x})$ is an infinitesimal element of surface area at $\boldsymbol{x}$, $\boldsymbol{\omega}^{(n)} = [\omega_1^{(n)}, \omega_2^{(n)}, \omega_3^{(n)}]^T$ is the angular velocity of the $n$-plate, which is also known as Euler vector, and $D_n$ is the surface of the $n$-plate. We used the identity $\boldsymbol{a} \times (\boldsymbol{b} \times \boldsymbol{a}) = (\boldsymbol{a} \cdot \boldsymbol{a})\boldsymbol{b} - (\boldsymbol{a} \cdot \boldsymbol{b})\boldsymbol{a}$ in the derivation of (1.170) and define the radius of the Earth to equal one so that $x \cdot x = 1$. Note that the condition in (1.170) is nowadays used to test the accuracy of global reference frames. The closer to zero $|L|$ is, the more accurate the global frame is.

In a compact notation, (1.170) can be written as

$L_k = \sum_{n=1}^{N} \sum_{l=1}^{3} I_{kl}^{(n)} \omega_l^{(n)} = 0$

or

$\left( \sum_{n=1}^{N} I_{kl}^{(n)} \right) \omega_l^{(r)} = - \sum_{n=1}^{N} \sum_{p=1}^{3} I_{kp}^{(n)} \omega_p^{(nr)}$ , (1.171)

the quantities $I_{kl}^{(n)}$, which is known as inertial tensor, is

$I_{kl}^{(n)} = \int_{D_n} (\delta_{kl} - x_k x_l) \, dS(x)$

$= D^{(n)} \delta_{kl} - \int_{D^{(n)}} x_k x_l \, dS(x) = D^{(n)} \delta_{kl} - \int_{D^{(n)}} x_k x_l \sin\theta \, d\theta \, d\phi$ (1.172)

where $\omega^{(n)} = \omega^{(nr)} + \omega^{(r)}$ is the absolute Euler vector of the $n$-th plate, $\omega^{(r)}$ is the Euler vector of the reference plate, $\delta_{kl}$ is the Kronecker delta ($\delta_{kl}=1$ if $k=l$ and $0$ otherwise), and $D^{(n)}$ is the area of the $n$-th plate. In (1.171), we assume that the Earth’s radius is normalized to unity (i.e., $|x|=1$ and the sphere area is $4\pi|x|^2=4\pi$). The first equation in (1.171) can then be written as a linear system of three equations with respect to the three unknown components of $\omega^{(r)}$, as described in (1.171). The tensors $I^{(n)}$ are generally evaluated over small areas such as ($0.6^\circ$ by $0.5^\circ$) (Schettino, 1999). Equation (1.172) can be reduced to the following expression

$I_{kl}^{(n)} = \sum_{p=1}^{K^{(n)}} \left[ D_p^{(n)} \delta_{kl} - x_{k,p}^{(n)} x_{l,p}^{(n)} \right]$ (1.173)

where $K^{(n)}$ is the number of small areas on the $n$-plate. Table 1.9 shows the components of $I^{(n)}$ of major plates. The total $I$ tensor for the whole lithosphere can be obtained simply by summating the tensors $I^{(n)}$ associated with each plate. It results in:

$I_{kl} = \sum_{n=1}^{N} I_{kl}^{(n)} = \frac{8\pi}{3} \delta_{kl}$ . (1.174)

Using (1.171) and (1.174), we obtain $\omega^{(r)}$ in terms of the relative Euler vectors $\omega^{(nr)}$ as follows:

$\omega_k^{(r)} = - \frac{3}{8\pi} \sum_{n=1}^{N} \sum_{p=1}^{3} I_{kp}^{(n)} \omega_p^{(nr)}$ . (1.175)

Figure 1.63. Present-day absolute plate velocities relative to NNR reference frame; that is, we assume no-net rotation of the lithosphere as a whole.

## 1.4.4. The Global Positioning System: Absolute Motion Using the ITR Frame

ITRF: mathematical model. As discussed above, motions and positions can be described with respect to a reference (O, i_x, i_y, i_z), where the origin point O is the center of mass (CM) of the whole Earth, including oceans and atmosphere, and is close to the Earth's center of mass. The vector set (i_x, i_y, i_z), is a right-handed, orthogonal basis. We assume that the basis vectors have the same length (i.e., |e_x| = |e_y| = |e_z| = λ). This length is known as scale. The orientation of the basis is also assumed to be equatorial—that is, e_z is the direction of the pole, e_y is aligned Greenwich meridian, and e_x is aligned with the equator. So a terrestrial fixed reference frame is entirely characterized by its origin, O, its scale, λ, and the orientation of its basis vectors. By definition, the time evolution of the reference fixed frame orientation obeys the no-net-rotation (NNR) condition over the whole Earth’s crust.

The satellite system in the sky has allowed, and continues to allow us, to record a large amount of 3D vector positions and velocities on the surface of the Earth from several hundreds of geodetic stations on the surface of the Earth. The velocities are needed to account for tectonic plate motions. These positions and velocities change with time. If all these positions are standardized to a fixed frame, the problem of determining that frame from the large amount of 3D vector positions and velocities is well-posed and even overdetermined, so long as the distribution of geodetic stations on Earth is dense and not over-sparse (see Figure 1.64). The fact that the Northern Hemisphere has about four times more geodetic stations than that in the Southern Hemisphere and the distribution of geodetic stations is still very sparse, especially in the Southern Hemisphere, limits our capabilities to accurately represent physical Earth and its rotation, and therefore, to determine the global fixed global frame. We can only hope that this other indicator of wealth distribution will be overcome in coming years because understanding Earth tectonics is probably one of the most important factors in our lives, and even in the survival of living things on Earth. Not all stations are GNSS (GPS, GLONASS, Galileo, ...) systems. Other stations are based on very-long-baseline-interferometry (VLBI), satellite-laser-ranging (SLR), and Doppler-orbitography-and-radiopositioning-integrated-by-satellite (DORIS) systems, and these varieties of recording further constraints the frame estimation (see Figure 1.31). We will describe these systems later on. Anyway, the fixed unique reference frame can be related to 3D vector positions and velocities as follows (Altamimi et al., 2016 and 2017):

$$\boldsymbol{x}_s^{(i)}(t) - \delta\boldsymbol{x}_{PSD}^{(i)}(t) = \boldsymbol{x}_c^{(i)}(t_0) + (t - t_0)\frac{d\boldsymbol{x}_c^{(i)}}{dt} + \Delta\boldsymbol{x}_f^{(i)}(t)$$
$$+ \boldsymbol{T}_k + D_k\boldsymbol{x}_c^{(i)} + \boldsymbol{R}_k\boldsymbol{x}_c^{(i)} + [t - t_0]\left[\frac{d\boldsymbol{T}_k}{dt} + \frac{dD_k}{dt}\boldsymbol{x}_c^{(i)} + \frac{d\boldsymbol{R}_k}{dt}\boldsymbol{x}_c^{(i)}\right],\tag{1.176}$$

$$\frac{d\boldsymbol{x}_s^{(i)}}{dt} = \frac{d\boldsymbol{x}_c^{(i)}}{dt} + \frac{d\boldsymbol{T}_k}{dt} + \frac{dD_k}{dt}\boldsymbol{x}_c^{(i)} + \frac{d\boldsymbol{R}_k}{dt}\boldsymbol{x}_c^{(i)},\tag{1.177}$$

with

$$\boldsymbol{R}_k = \begin{bmatrix} 0 & -\Omega_z & \Omega_y \\ \Omega_z & 0 & -\Omega_x \\ -\Omega_y & \Omega_x & 0 \end{bmatrix},\tag{1.178}$$

Table 1.10. NNR Euler vectors of some major modern plates. Similar results were obtained by Schettino (1999).

| Plate | Latitude | Longitude | ω(°/Ma) |
|-------|----------|-----------|---------|
| Africa | 50.640 | -73.591 | 0.291 |
| Antarctica | 63.222 | -115.261 | 0.238 |
| Arabia | 44.935 | -4.437 | 0.544 |
| Australia | 33.866 | 33.154 | 0.647 |
| Caribbean | 25.135 | -92.627 | 0.214 |
| Cocos | 24.526 | -115.758 | 1.509 |
| Eurasia | 50.806 | -111.889 | 0.234 |
| India | 45.432 | 0.348 | 0.546 |
| Nazca | 47.850 | -99.962 | 0.743 |
| North America | -2.299 | -85.540 | 0.207 |
| South America | -25.341 | -123.920 | 0.115 |
| Juan de Fuca | -27.4 | 58.1 | 0.64 |
| Philippine | -37.948 | -35.319 | 0.900 |
| Pacific | -62.990 | 107.041 | 0.641 |
