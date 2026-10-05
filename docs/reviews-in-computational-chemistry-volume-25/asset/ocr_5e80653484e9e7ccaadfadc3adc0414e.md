# Selected Case Studies

# SELECTED CASE STUDIES

The last few years have seen an explosion in the number of atomic-levelntribological simulations aimed not just at understanding fundamental aspectsnof friction, but also at determining the frictional properties of systems used in
real-world applications. In this section, we will discuss selected studies in
to demonstrate how the principles discussed earlier in this chapter are\used in practice. Unfortunately, it is not possible to consider all of the important, high-caliber research within the space of this chapter. Instead, we focus
of a few keys areas that encompass both fundamental and applied research in
computational tribology.

# Instabilities, Hysteresis, and Energy Dissipation

Earlier we used a relatively simple model composed of a slider and subststrate to demonstrate how mechanical instabilities lead to energy dissipation
ofriction. However, realistic contacts are much more complex. For
instance, real contacts can rarely be described as one-dimensional and almost
always some molecules that act as impurities. Understanding the frictionalaspects of these systems will require a consideration of the role instabilities plays that are more complex than the PT model. In this section,
we discuss studies that investigate instabilities in more realistic systems.

The role of instabilities involving confined impurity atoms has
investigated by Müller using a model in which two-dimensional (1D)-or
2-D surfaces were separated by a low concentration of confined atoms
and slid past one another.25 The motion of the confined atoms was simulated
with Langevin dynamics where the interactions between these atoms were
neglected and the atom-wall interactions were described

```
$V_t = V_t^0\cos((x-v_0)/b_t) + V_t^1\cos(2(x-v_0)/b_t) + \dots$
$V_b = V_b^0\cos(x/b_h) + V_b^1\cos(2x/b_h) \quad [38]$
```

where the subscripts $t$ and $b$ denote the top and bottom walls; respectively;
2b_t$ and $2b_h$ are the periods of the top and bottom walls; and $v_0$ is the sliding
velocity. Only $V_1 = V_{1,b}^0$. In this study, the "impurity" limit was considered in which
t concentration of impurity atoms is so low that interactions between
atoms can be neglected.

Simulations with consensus, 1-D surfaces showed that the behavior
of system was sensitive to $V_1$, as summarized in Figure 17. In the case
where $V_1 < 0$, the atom becomes unstable at some point in time and slides
into the next minimum. However, the curve representing the mechanically
stable position $x_{ms}$ is continuous and the atom can always remain close