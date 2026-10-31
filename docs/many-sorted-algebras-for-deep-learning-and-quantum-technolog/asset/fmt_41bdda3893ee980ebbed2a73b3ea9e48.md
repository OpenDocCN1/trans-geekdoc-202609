
# Elliptic Curve Addition

### Figure C.1 Elliptic curve addition

![Figure C.1 Elliptic curve addition.](Images/F000114bm01-9780443136979.jpg)

Figure C.1 Elliptic curve addition.

Referring to the figure, the line `y=2x+1` goes through `(0,1)` and `(−1,−1)` and intersects the elliptic curve at `(2,5)`. Accordingly, `(2,-5)` is also a point on the curve. The reflected point is the solution and is called the addition of `(0,1)` and `(−1,−1)`. So the sum of `(0,1)` and `(−1,−1)` is `(2,−5)` (see [Fig. C.1](#FigureC1_373-376_B9780443136979000114.xhtml#f0010)). This time, passing a line through `(0,1)` and `(2,−5)` gives `y=−3x+1`, finding the intersecting point yields `(1/4,1/4)`. Consequently, the point `(1/4.−1/4)` is the solution. Thus `(0,1)` plus `(2,−5)=(1/4.−1/4)`. Continuing, the line `y=x` goes through `(−1,−1)` and `(1,1)` and yields `(1/4.1/4)` as before.

The mechanics behind the Abelian group structure for elliptic curves is as follows: The sum of two points on the curve is found by utilizing the equation of a straight line passing through these two points, then finding where it again intersects the curve, thus determining a third point on the given line, and finally, reflecting this found point about the `x`-axis. If the line through two points is vertical, the third point is `∞`![Equation](Images/F000114si1.png), and the point at infinity is therefore the sum. Thus, by including the point at infinity, the structure is a pointed set. Tangents to the curve are handled similarly; in this case, the point of tangency is added to itself. If the tangent line intersects the curve, for a third time, then the sum is that point with the negative ordinate value applied. When there is no intersection with the curve, the point at infinity `∞`![Equation](Images/F000114si2.png) is used. The set of points under this binary operation so far is a groupoid (see [Fig. C.2](#FigureC1_373-376_B9780443136979000114.xhtml#f0015)).

### Figure C.2 Addition of vertical points on an elliptic curve

![Figure C.2 Addition of vertical points on an elliptic curve.](Images/F000114bm02-9780443136979.jpg)

[Figure C.2](#FigureC1_373-376_B9780443136979000114.xhtml#Bf0015) Addition of vertical points on an elliptic curve.

To see that it is a semigroup, associativity must prevail. Here, returning to projective lines and projective space, a theorem ([Cassels, 1991](#FigureC1_373-376_B9780443136979000114.xhtml#bib1)) is applied: Whenever a cubic curve goes through eight of nine points of intersection with two other cubic curves, then a ninth point of intersection must be included. This is often called the ninth point lemma or the Cayley–Bacharach theorem. The proof of associativity follows from this result ([Cayley, 1889](#FigureC1_373-376_B9780443136979000114.xhtml#bib2)) (refer to [Fig. C.3](#FigureC1_373-376_B9780443136979000114.xhtml#f0020)).

### Figure C.3 Proof of associative law

![Figure C.3 Proof of associative law.](Images/F000114bm03-9780443136979.jpg)

[Figure C.3](#FigureC1_373-376_B9780443136979000114.xhtml#Bf0020) Proof of associative law.

The basic idea is finding two curves `C1` and `C2` which share eight distinct points with a given curve `C`, then showing that these curves are cubic and not equal to `C`, and then applying the aforementioned theorem illustrating that the ninth point is in both `C1` and `C2`. By judicially configuring the eight points in a strategic pattern, containment of the ninth point will prove the associative law. In this figure, the symbol (?) is supposed to be the ninth point. The eight points which are shared by all six straight lines are: `A`, `P`, `Q`, `R`, `B`, `Q+R`, `Z`, and `P+Q`. Points on a straight line depict lines in affine space. The overall objective is to show that `(P+Q)+R=P+(Q+R)`; this will follow because line `L2` and line `M2` intersect at `?`. The three lines `L1`, `L2`, and `L3` each can be given as degree-one homogeneous polynomials: `|1 = |2 = |3 = 0`![Equation](Images/F000114si3.png). In this case, `C1 = |1|2|3`![Equation](Images/F000114si4.png) describes a degenerate cubic. Analogously let `C2=m1m2m3`, where `m1=m2=m3=0` are degree-one homogeneous polynomials describing `M1`, `M2`, and `M3`, respectively. So given the elliptic curve `C`, including the eight points, applying the Cayley–Bacharach theorem shows the ninth point (?) is included and in the intersection of `L2` and `M2`. This shows that the structure is a semigroup. Next, showing that the structure is a monoid follows.

A ZERO must be found and prove that it satisfies the zero law to obtain a monoid. The zero is the point at infinity `∞`![Equation](Images/F000114si5.png). It obeys the zero law because if you take any single point `p`, then the sum of `p+Z` is found by taking the vertical line and connecting these two points. Then for a nontangent point `p`, there exists a third point `q` on this same line, thus the sum is `−q`. However, `−q` is `p`. When `p` is a tangent point and the tangent is vertical, then `p+Z=p`. The next to show is that this structure is a group. For a group, a MINUS is needed, and the minus identity must be satisfied. However, for point `p=(a, b)`, `MINUS(p)=(a, −b)` denoted `−p` for short. Moreover, when these two points are connected with a straight line, the line is always vertical, so `p+(−p)=∞`![Equation](Images/F000114si6.png) as desired. Since there is only one point at infinity, `MINUS(Z)=∞`![Equation](Images/F000114si7.png). Finally, the group is Abelian because the order of choosing two points, `p` and `q`, on a line does not change the resulting third point `r`, on the same line, which is reflected and consequently `p+q=−r=q+p`.

Lastly, a theorem by Mordell specifies the group structure for rational solutions on an elliptic curve with rational coefficients. It states that it is a finitely generated Abelian group provided that it is nonsingular, that is, it has distinct roots ([Silverman, 1986](#FigureC1_373-376_B9780443136979000114.xhtml#bib5)). So by this theorem, there exists a finite set of points `Pj`, in this group such that every point `P` in the group can be expressed as `P=summation j=1 to n of nj Pj` for `nj` in `Z`. Moreover, the structure of this group was proved by Mazur ([Dumber, 2019](#FigureC1_373-376_B9780443136979000114.xhtml#bib3)) to be of the form `T x Z x Z x … x Z`, where `T` is a torsion subgroup with order at most 16, and `T` always being one of fifteen possibilities. Additionally, there are `r` copies of `Z` above, and it is called the rank. Finally, for an elliptic curve `y²\=x³\+ ax+b`, with `a` and `b` in `Z`, Siegel ([Lang, 1978](#FigureC1_373-376_B9780443136979000114.xhtml#bib4)) showed that the associated group has finitely many points with integer coordinates.

## References

* [Cassels, 1991](#FigureC1_373-376_B9780443136979000114.xhtml#BIB_1) Cassels J. London Mathematical Society Student Texts 24 *Lectures on Elliptic Curves* Cambridge University Press 1991;.
* [Cayley, 1889](#FigureC1_373-376_B9780443136979000114.xhtml#BIB_2) Cayley A. *On the Intersection of Curves* Cambridge U. Press 1889;.
* [Dumber, 2019](#FigureC1_373-376_B9780443136979000114.xhtml#BIB_3) Dumber S. *Torsion on Elliptic Curves and Mazur’s Theorem* U. Chicago. Edu 2019;.
* [Lang, 1978](#FigureC1_373-376_B9780443136979000114.xhtml#BIB_4) Lang S. *Elliptic Curves*. vol. 231 Springer 1978; 3-540-08489-4.
* [Silverman, 1986](#FigureC1_373-376_B9780443136979000114.xhtml#BIB_5) Silverman J. 0-387-96203-4 *Arithmetic of Elliptic Curves*. vol 106 Springer-Verlag 1986;.

# Appendix D

## Young diagrams
