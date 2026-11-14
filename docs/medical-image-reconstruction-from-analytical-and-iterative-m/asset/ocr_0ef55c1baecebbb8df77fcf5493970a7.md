![](bbox=[0.1, 0.09, 0.55, 0.27])

Fig. 5.11: Integration along a line on the cone-beam detector gives a weighted plane integral of the object.

![](bbox=[0.1, 0.34, 0.7, 0.53])

Fig. 5.12: The differential $dt$ in the tangent direction is equal to the angular differential $d\alpha$ times the distance $r$.

factor by the factor $r$, obtaining the derivative of the unweighted plane integral with respect to variable $t$, which is in the normal direction of the plane, that is,

```
\frac{\partial \left( \frac{1}{r} \text{ weighted plane integral} \right)}{\partial \alpha} = \frac{\partial (\text{Radon transform})}{\partial t}. (5.7)
```

Recall that the Radon inversion formula is the second-order derivative of the plane integral with respect to $t$, followed by the 3D Radon backprojection. Therefore, a cone-beam image reconstruction algorithm can be implemented as follows:

+   (i) Form all possible (all orientations and all locations) line integrals on each detector plane (see Figure 5.11), obtaining (1/r)-weighted plane integrals.
+   (ii) Perform the angular derivative on results from (i).
+   (iii) Rebin the results from (ii) to the $(s, \overline{\theta})$ Radon space (see Figure 5.6).