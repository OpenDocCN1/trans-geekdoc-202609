
## Construction from Young diagram

Now going the other way, given a `Young diagram`, the corresponding unique `Maya diagram` will be constructed. The procedure is given after an initialization or a setting up. Again, consult `Appendix A.4`. `M` is described by `(p, q)`, its integer location in `R²`, along with the length `nj`, of every block, each located adjacent to and underneath each other, left justified. Recall the blocks top down form a finite nonincreasing sequence of lengths. Here, `nj` can equal `n(j+1)`, that is, the block lengths can be repeated underneath each other. It is useful to construct ruled horizontal and vertical lines. These lines are orthogonal to each other meeting at `(p, q)`. Ruled markings increase in the horizontal direction and decrease in the vertical direction all by the same units, the size of a cell edge. The `Y` structure is left justified and are usually located in the fourth quadrant. All rulings are compatible with the cell size making up each bar. Intuitively, all vertical line segments in `Y` symbolize white dots in `M`, and horizontal line segments in `Y` denote black dots.

The setup is crucial; it provides the environment for the initial, recursive, and final stages in determining `M`. The largest location of a white point `w` in `M` for which all smaller half-unit points are also white is easy to find. It is found at half a unit, in the vertical direction, right below the bottom bar of `Y`. So, the leftmost cell of the bottom bar in `Y` is `(p, p+1\] x \[−h, −h+1)`; then `w = - h -1/2`. Here `h` is the total number of bars constituting `Y`; it is the number of `nj`’s. Place white dots at `w` and at all half-integer points to the left of `w` in `M`.

Next, the profile of `Y` is traversed, from left to right and bottom up. This is the lower and left-hand boundary line segments. Black dots are placed in `M` for each horizontal line segment of every cell in `Y` traversed along the profile. White dots are placed in `M`, for every vertical cell wall in the profile when going upward. The location in `M` for each of these dots starts with `w` and is found accumulatively, that is, by adding one black dot to the location in `M` for every line segment of each cell going to the right. Also add one white dot for each line segment going up in the profile of `Y`. Accordingly, dots will be issued to locations `w+1`, `w+2`, and so on. The first black dot is found traversing the bottommost and leftmost cell `(p, p+1\] x \[− h,−h+1)`, going horizontal, and thereby marking a black dot at `w+1 = 1/2 - h`. The next dot is placed at `w+2`; it will be a black dot by going horizontal if the bottom bar has more than one cell, but if the bottom block has one cell only, up is the direction and a white dot is placed at `w+2`. The next dot is placed at `w+3`; it is black for horizontal movement and white for vertical movement per each unit line segment traversed in the profile. The final line segment in the profile must be vertical. It corresponds to the right-hand vertical edge of cell `(p+n1–1, p+n1\] x \[q−1, q)`, indicating a white dot should be placed at `p+n1–1/2`. Finally, `b = p+n1+1/2`, and at `b` and all larger half-integer points, there should be black dots.

### Example 15.10

Consider the `Young diagram` illustrated in [Fig. 15.3](#Ch015_271-288_B9780443136979000291.xhtml#f0020). From this figure, it is seen that the `Y` structure is located at `(p, q) = (0, 1)`, and the length of the bars is given by the finite sequence: `(n1, n2, n3, n4) = (5, 3, 3, 1)`, and `h = 4` since there exist 4 bars in `Y`. As a bound vector, `Y` is `(5,3,3,1)[(0, 1)]`![Equation](Images/F000291si83.png).

![Figure 15.3 Young diagram to find Maya diagram.](Images/F000291f15-03-9780443136979.jpg)

[Figure 15.3](#Ch015_271-288_B9780443136979000291.xhtml#Bf0020) Young diagram to find Maya diagram.

Going half a unit under the lowest bar gives `w = -3 1/2`. This value could be found algebraically by using `w = q - h -1/2 = 1 - 4 -1/2`. That is, it can be found from the bound vector, whose length is four, and starts at `(0, 1)`. The y component is one. In any case, this point should be marked white along with all half-integer values less than `w`. So:

$\\begin{matrix} {11/{2.}} & {{- 9}/{2..}} & {{- 7}/{2..}} & {{- 5}/{2..}} & {{- 3}/{2..}} & {{- 1}/{2..}} & {1/{2\\ldots}} & {3/{2\\ldots}} & {5/{2\\ldots}} & {7/{2\\ldots}} & {9/{2..}} & {11/{2..}} & {13/{2..}} & {15/{2..}} & {17/{2\\ldots}} \\\\ 0 & 0 & {0.} & & & & & & & & & & & & \\\\ \\end{matrix}$

![Equation](Images/F000291si84.png)

Next, the bottom bar consisting of a single cell is encountered; it is horizontal, so a black dot is drawn at position `-5/2`, one unit more than `w`. A single black dot appears since the last tuple in the bound vector is one. Go up on the bottom bar on the profile, of `Y`, producing a white dot at `-3/2`. Now the next to the bottom bar is encountered in a horizontal manner. Since there are two cells involved, two black dots are issued at points `-1/2` and `1/2`. These two black dots appear since the difference between the next to last tuple and the last tuple in the bound vector is two. Consequently, at this point, the `M` diagram is as follows:

$\\begin{matrix} {11/{2.}} & {{- 9}/{2..}} & {{- 7}/{2..}} & {{- 5}/{2..}} & {{- 3}/{2..}} & {{- 1}/{2..}} & {1/{2\\ldots}} & {3/{2\\ldots}} & {5/{2\\ldots}} & {7/{2\\ldots}} & {9/{2..}} & {11/{2..}} & {13/{2..}} & {15/{2..}} & {17/{2\\ldots}} \\\\ 0 & {0.} & {0.} & {X.} & {0.} & {X.} & X & & & & & & & & \\\\ \\end{matrix}$

![Equation](Images/F000291si85.png)

Going up in the profile for blocks 3 and 2 induces white dots at locations `3/2` and `5/2`. Again, these two consecutive white dots could be seen from the bound vector since the two tuples have the same number, three. Then going horizontal on block 1 yields black dots at `7/2` and `9/2`. As before, using the difference between the first and second tuple provides the number of black dots. Finally, the profile traversing ends by providing a white dot at `11/2`. Starting from `13/2` inclusive, all black dots exist. The final `M` structure is:

$\\begin{matrix} {11/{2.}} & {{- 9}/{2..}} & {{- 7}/{2..}} & {{- 5}/{2..}} & {{- 3}/{2..}} & {{- 1}/{2..}} & {1/{2\\ldots}} & {3/{2\\ldots}} & {5/{2\\ldots}} & {7/{2\\ldots}} & {9/{2..}} & {11/{2..}} & {13/{2..}} & {15/{2..}} & {17/{2\\ldots}} & \\\\ 0 & {0.} & {0.} & {X.} & 0 & X & X & {0.} & {0.} & {X.} & {X.} & 0 & {X.} & X & X & {.\\#} \\\\ \\end{matrix}$

![Equation](Images/F000291si86.png)

## 15.6 Maya diagram representation of fermionic Fock space

Fermionic Fock space as a vector space `V = direct sum complex-valued basis indexed by the half-integers`. For an element `w`, in this space it can be expanded in a basis: `w = ej1 & ej2 & …`, where `jk` is a strictly increasing sequence of half-integers. Also, `&` is the wedge, or and type product. Each wedge can be visualized as a `Maya diagram`. Moreover, fermionic Fock space can be viewed as the free span over `C` of all `Maya diagrams`. The standard basis for this space is the `Maya diagrams`. The vacuum state (`vac`) has white dots exclusively at every positive half interval. In general, if there exist black dots only beyond some half-integer `n`, the diagram is said to have a vacuum at level `n`. This is also called the `Fermi level`.
