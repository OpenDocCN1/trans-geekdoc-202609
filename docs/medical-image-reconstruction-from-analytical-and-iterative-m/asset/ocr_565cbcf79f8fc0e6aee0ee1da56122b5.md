The intersection of a \(\kappa\)-plane \(\kappa(s, \psi)\) with the detector is called a \(\kappa\)-line. The filtering direction \(\vec{\beta}\) is along the \(\kappa\)-line. If you let the point \(\vec{x}\) vary, you will get a bunch of these \(\kappa\)-planes \(\kappa(s, \psi)\), and you will get a bunch of \(\kappa\)-lines on one detector (see Figure 5.31).

On a flat detector, the \(\kappa\)-lines are straight lines. Let us assign a \(u\)-\(w\) coordinate system to the detector plane as indicated in Figure 5.31 with the \(w\)-axis being the helix axis (i.e., the \(z\)-axis). The \(\kappa\)-lines can be described by the \(u\)-\(w\) relation for a fixed \(\psi\):

```
\(\quad w = \frac{Dh}{2\pi R} \left( \psi + \frac{\psi}{\tan \psi D} u \right), \quad (5.56)\)
```

where \(R\) is the radius of the helix, \(h\) is the pitch of the helix, and \(D\) is the distance between the detector plane and the focal point. There are many lines depicted in Figure 5.31, and each line corresponds to a fixed \(\psi\) value.

If a curved detector is used, the \(\kappa\)-lines are no longer straight lines on the detector but are curves. For a fixed \(\psi\), the \(\alpha\)-\(w\) relationship is given as

```
\(\quad w = \frac{Dh}{2\pi R} \left( \psi \cos \alpha + \frac{\psi}{\tan \psi} \sin \alpha \right), \quad (5.57)\)
```

where the angle \(\alpha\) is defined in Figure 5.32. We can plot the curved \(\kappa\)-lines using this relationship for a set of \(\psi\) values to obtain a counterpart of Figure 5.31 for the curved detector (see Figure 5.33).

Finally, we will explain a little more on the curved detector implementation of Katsevich's algorithm, which is again given below:

```
\(f(\vec{x}) = \frac{-1}{2\pi^2} \int_{I_n(\vec{x})} \frac{1}{\|\vec{x} - \vec{a}(s)\|} \int_{-\pi/2}^{\pi/2} \left. \frac{\partial \tilde{g}(\vec{\theta}(y), \vec{a}(q))}{\partial q} \right|_{q=s} \frac{1}{\sin y} dy ds. \quad (5.58)\)
```

![](bbox=[0.17, 0.6, 0.65, 0.86])

Fig. 5.32: The coordinate system for a curved detector cone-beam geometry.