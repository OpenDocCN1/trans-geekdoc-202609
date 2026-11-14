![](bbox=[0.18, 0.1, 0.78, 0.29])

Fig. 5.19: The 2D filter transfer function $Q$ for the imaging geometry $\Omega_{\mu}$. 

Now the expression (5.13) is explained below. We need to set up some 3D coordinate systems: the regular $(x, y, z)$ system and the rotated $(u, v, t)$ system. The unit vectors for the $(u, v, t)$ system are defined as 

```
\bar{\theta}_u = (-\sin \phi, \cos \phi, 0) , \quad (5.15)

\bar{\theta}_v = (-\cos \theta \cos \phi, -\cos \theta \sin \phi, \sin \theta) , \quad (5.16)

\bar{\theta}_t = (\sin \theta \cos \phi, \sin \theta \sin \phi, \cos \theta) , \quad (5.17)
```

where the $u$-axis is in the $x$-$y$ plane. The $t$-axis is parallel to the projection rays. The $u$-$v$ plane is the virtual 2D detector. The spatial domain systems are shown in Figure 5.20. The corresponding Fourier domain coordinate systems are shown in Figure 5.21. 

![](bbox=[0.1, 0.58, 0.5, 0.76])

Fig. 5.20: Two 3D coordinate systems: the regular $(x, y, z)$ system and the rotated $(u, v, t)$ system. 

Let us consider a great circle with the normal vector pointing at the direction $\bar{\theta}$. The arc length $\gamma$ as shown in Figure 5.18 is given by 

```
\sin \frac{\gamma}{2} = \frac{\sin \psi}{\sin \theta} , \quad (5.18)
```