
invariant FBP algorithm, we need to do something against common sense. In Katsevich's algorithm, a measurement is weighted by either +1 or -1. If a plane is measured once, we must make sure that it is weighted by +1. If a plane is measured three times, we need to make sure that two of them are weighted by +1 and the third one of them is weighted by -1. In other words, we keep one and throw the other two away. Ouch! Further discussion about the weighting and filtering will be given in the next section.

![](img/dd555effd38151c67af30d84800c554a_120_0.png)

The cutting plane intersects the orbit once.

The cutting plane intersects the orbit 3 times.

Fig. 5.17: The \(\pi\)-segment defines a section of helix. A cutting plane is a plane passing through the reconstruction point. The cutting plane either intersects the section of helix one or three times.

In Katsevich's algorithm, the normalization issue is taken care of by selecting a proper filtering direction. Here, filtering means performing the Hilbert transform. After the filtering direction and the normalization issues have been taken care of, Katsevich's algorithm is implemented with the following steps:

- (i) Take the derivative of the cone-beam data with respect to the orbit parameter along the helix orbit.
- (ii) Perform the Hilbert transform along the directions that have been carefully selected.
- (iii) Perform a cone-beam backprojection with a weighting function, similar to the backprojection in Feldkamp's algorithm.

Some later versions of the algorithm have replaced the derivative with respect to the orbit parameters by partial derivative with respect to the detector coordinates.

## 5.4 Mathematical expressions

Some 3D image reconstruction algorithms are presented here without proofs. For the 3D parallel line-integral projections, we have a backprojection-then-filtering algorithm and FBP algorithms, which are not unique. For the parallel plane-integral projections (i.e., the Radon transform), we also have a backprojection-then-filtering algorithm and an FBP algorithm which is the Radon inversion formula.

For cone-beam projections, Feldkamp's circular orbit algorithm and the Katsevich's helical orbit algorithm are highlighted because they are in the form of convolution and cone-beam backprojection. Tuy's relation and Grangeat's relation are also discussed in this section.

### 5.4.1 Backprojection-then-filtering for parallel line-integral data

For this type of algorithm, the projections are backprojected to the image domain first, obtaining b(x, y, z). Then the 3D Fourier transform is applied on b(x, y, z), obtaining B(ωx, ωy, ωz). Next, a Fourier domain filter G(ωx, ωy, ωz) is used to multiply B(ωx, ωy, ωz), obtaining F(ωx, ωy, ωz) = B(ωx, ωy, ωz) G(ωx, ωy, ωz). Finally, the 3D inverse Fourier transform is applied to F(ωx, ωy, ωz) to obtain the reconstructed image f(x, y, z). Here, the filter transfer function G(ωx, ωy, ωz) is imaging geometry dependent. Some of the imaging geometries are shown in Figure 5.5, where the θ→ trajectories are displayed as shaded regions. Let Ω denote the occupied region by the θ→ trajectories on the unit sphere.

When Ω = Ω4π is 4π, that is, Ω4π is the entire unit sphere, G is a ramp filter:

```
G(ωx, ωy, ωz) = √(ωx² + ωy² + ωz²)/π. (5.8)
```

If Ω is not the full sphere, this ramp filter will be modified by the geometry of Ω. Then the general form of G is

```
G(ωx, ωy, ωz) = √(ωx² + ωy² + ωz²)/D(θ→), (5.9)
```

where D(θ→) is half of the arc length of the intersection of a great circle with Ω. The normal direction of the great circle in the Fourier domain is θ→, where θ→ is the direction from the origin to the point (ωx, ωy, ωz).

When Ω = Ωψ is the region shown in Figure 5.18, D(θ→) is the arc length γ, which is orientation θ→ dependent. Using the geometry, we have γ = π if θ ≤ ψ, and we have sin γ/2 = sin ψ / sin θ if θ > ψ.

### 5.4.2 FBP algorithm for parallel line-integral data

In the FBP algorithm, we need to find a 2D filter transfer function for each orientation \(\bar{\theta} \in \Omega\). If \(\Omega = \Omega_{4\pi}\), this filter is a ramp filter

![](img/dd555effd38151c67af30d84800c554a_122_0.png)

Fig. 5.18: The definition of the \(\Omega_\psi\) and the arc length \(\gamma\), which is a part of a great circle.

\(Q(\omega_u, \omega_v) = \sqrt{\omega_u^2 + \omega_v^2}/\pi,\) (5.10)

which is the same for all orientations \(\bar{\theta} \in \Omega\).

If \(\Omega\) is not the full sphere \(\Omega_{4\pi}\), this ramp filter \(Q(\omega_u, \omega_v)\) becomes orientation \(\bar{\theta}\) dependent as \(Q_{\bar{\theta}}(\omega_u, \omega_v)\) (note: a subscript is added) and can be obtained by selecting the “central slice” of \(G(\omega_x, \omega_y, \omega_z)\) with the normal direction \(\bar{\theta}\). Here, the \(u\)-axis and \(v\)-axis are defined by unit vectors \(\bar{\theta}_u\) and \(\bar{\theta}_v\), respectively. The three vectors, \(\bar{\theta}\), \(\bar{\theta}_u\) and \(\bar{\theta}_v\), form an orthogonal system in 3D, where \(\bar{\theta}\) represents the direction of a group of parallel lines perpendicular to a detector, \(\bar{\theta}_u\) and \(\bar{\theta}_v\) are on the detector plane, and \(\bar{\theta}_u\) is also in the \(x\)-\(y\) plane of the global \((x, y, z)\) system in 3D.

If we consider the case of \(\Omega = \Omega_\psi\) shown in Figure 5.18, \(Q_{\bar{\theta}}(\omega_u, \omega_v)\) has two expressions in two separate regions (see Figure 5.19):

\(Q_{\bar{\theta}}^-(\omega_u, \omega_v) = \frac{\sqrt{\omega_u^2 + \omega_v^2}}{\pi}\) (5.11)

if

\(0 \le \sqrt{\omega_u^2 + \omega_v^2 \cos^2 \theta} \le \sqrt{\omega_u^2 + \omega_v^2} \sin \psi;\) (5.12)

\(Q_{\bar{\theta}}^-(\omega_u, \omega_v) = \frac{\sqrt{\omega_u^2 + \omega_v^2}}{2 \sin^{-1} \left( \frac{\sqrt{\omega_u^2 + \omega_v^2 \sin \psi}}{\sqrt{\omega_u^2 + \omega_v^2 \cos^2 \theta}} \right)}\) (5.13)

if

\(\sqrt{\omega_u^2 + \omega_v^2} \sin \psi < \sqrt{\omega_u^2 + \omega_v^2 \cos^2 \theta} \le \sqrt{\omega_u^2 + \omega_v^2}.\) (5.14)

![](img/dd555effd38151c67af30d84800c554a_123_0.png)

Fig. 5.19: The 2D filter transfer function $Q$ for the imaging geometry $\Omega_\psi$.

Now the expression (5.13) is explained below. We need to set up some 3D coordinate systems: the regular $(x, y, z)$ system and the rotated $(u, v, t)$ system. The unit vectors for the $(u, v, t)$ system are defined as

```
\bar{\theta}_u = (-\sin \phi, \cos \phi, 0) , \quad (5.15)

\bar{\theta}_v = (-\cos \theta \cos \phi, -\cos \theta \sin \phi, \sin \theta) , \quad (5.16)

\bar{\theta}_t = (\sin \theta \cos \phi, \sin \theta \sin \phi, \cos \theta) , \quad (5.17)
```

where the $u$-axis is in the $x$-$y$ plane. The $t$-axis is parallel to the projection rays. The $u$-$v$ plane is the virtual 2D detector. The spatial domain systems are shown in Figure 5.20. The corresponding Fourier domain coordinate systems are shown in Figure 5.21.

![](img/dd555effd38151c67af30d84800c554a_123_1.png)

Fig. 5.20: Two 3D coordinate systems: the regular $(x, y, z)$ system and the rotated $(u, v, t)$ system.

Let us consider a great circle with the normal vector pointing at the direction $\bar{\theta}$. The arc length $\gamma$ as shown in Figure 5.18 is given by

```
\sin \frac{\gamma}{2} = \frac{\sin \psi}{\sin \theta} , \quad (5.18)
```

![](img/dd555effd38151c67af30d84800c554a_124_0.png)

Fig. 5.21: The Fourier domain coordinate systems corresponding to the two 3D coordinate systems shown in Figure 5.20.

that is,

```
\(\gamma = 2\sin^{-1}\left(\frac{\sin\psi}{\sin\theta}\right).\) (5.19)
```

Let us consider a different great circle whose normal vector pointing at a different direction \(\vec{\theta}_w\), and the corresponding arc length is \(\gamma = 2\sin^{-1}(\sin\psi / \sin \theta)\).

In the following, we consider a special point \(\vec{\omega}\) in the \(\omega_u - \omega_v\) plane in the 3D Fourier domain as shown in Figure 5.22. The \(\omega_t\) component of \(\vec{\omega}\) is zero. We have

```
\(\vec{\omega} = \omega_u\vec{\theta}_u + \omega_v\vec{\theta}_v,\) (5.20)
```

```
\(\|\vec{\omega}\| = \sqrt{\omega_u^2 + \omega_v^2}.\) (5.21)
```

For this special point \(\vec{\omega}\), the arc length \(\gamma\) given by eq. (5.19) becomes

```
\(\gamma = 2\sin^{-1}\left(\frac{\sin\psi}{\sin\theta_{\vec{\omega}}}\right) = 2\sin^{-1}\left(\frac{\sin\psi}{\sqrt{1-\cos^2\theta_{\vec{\omega}}}}\right) = 2\sin^{-1}\left(\frac{\sin\psi}{\sqrt{1-\left(\frac{\omega_z}{\|\vec{\omega}\|}\right)^2}}\right),\) (5.22)
```

where \(\omega_z\) is the z-component of \(\vec{\omega} = \omega_u\vec{\theta}_u + \omega_v\vec{\theta}_v\), and thus

```
\(\omega_z = \omega_u 0 + \omega_v \sin\theta = \omega_v \sin\theta.\) (5.23)
