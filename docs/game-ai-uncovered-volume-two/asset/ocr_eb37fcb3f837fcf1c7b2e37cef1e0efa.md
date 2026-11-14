![](bbox=[0.115, 0.092, 0.88, 0.235])

IMAGE 15.4 (a) Beta plane Interest and Danger Influence scoring, (b) Beta Result vector assigned.

The algorithm then moves on to the Gamma plane as shown in Image 15.5a and b, repeating the influence scoring process described previously for the Alpha and Beta planes. Notice that because the AI unit is before the obstacle, as shown in Image 15.3d, the Gamma plane will not intersect with the obstacle since the plane sits upright and parallel to the obstacle, as illustrated in Image 15.1c, so the ray casts will miss any threats. Since the algorithm outlines that points of interest will be treated separately, the interest projections on the plane will happen regardless of there being an intersection with Beta.

![](bbox=[0.165, 0.465, 0.835, 0.69])

IMAGE 15.5 (a) Gamma plane Interest and Danger Influence scoring, (b) Gamma Result vector assigned.

With all three result vectors (Ra, Rb, Ry) calculated, they can now be added together to determine the final resulting vector Rf (Image 15.6).