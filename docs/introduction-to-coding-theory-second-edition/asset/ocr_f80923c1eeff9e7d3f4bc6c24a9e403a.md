Using this in Theorem 18.41 yields an additive quaternary code of dimension (f + 2)/2 and length q = 2^f all of whose codewords have weight either q or q − q/4 = 3q/4.

# 18.45 Corollary.

Proposition 18.44 yields an additive [2^f,1+f/2,3×2^{f−2}]_4 code.

For f = 3 this yields an [8,2.5,6]_4 code. For f = 4 the parameters [16,3,12]_4 are not of independent interest. These are parameters of a quaternary linear code (geometrically, the affine plane AG(2,4)). Case f = 5 yields [32,3.5,24]_4, by concatenation [96,7,48]_2. In fact, the parameters of the resulting binary codes (after concatenation) are identical to those of a family obtained via the (u, u+v) construction in Section 5.2.

Proposition 18.44 also can be used for recursive constructions.

# 18.46 Corollary.

Let f ≥ 2, q = 2^f. If there is an additive [m, f/2, d]_4 code, then there is an additive [q + m, 1 + f/2, Min(q, d + 3q/4)]_4 code.

# PROOF

Assume an additive [m, f/2, d]_4 code exists. Represent it geometrically on the secundum S used in Proposition 18.44. Together with the spread lines this yields a multiset of q + m codelines. Outside each hyperplane H containing S there are precisely q of the codelines, the spread lines. Outside each of the remaining hyperplanes there are 3q/4 spread lines and at least d of the lines in S.

As an example, using [3,1.5,2]_4 as an ingredient (geometrically, three different lines of the Fano plane), yields [11,2.5,8]_4.

Theorem 18.42 is useful to prove nonexistence as well. In fact, an additive [n,k,d]_4 cannot exist if no linear [3n,2k,2d]_2 code exists. As an example, an additive [12,2.5,9]_4 code cannot exist as concatenation would yield a binary [36,5,18]_2 code, which would contradict the Griesmer bound.

On the construction side we can use linear quaternary codes. In order to understand some of the entries in the table, the following linear codes are needed:

+   1. [17,4,12]_4 (geometrically, the elliptic quadric in PG(3,4)); see Section 17.3.
+   2. [21,15,5]_4, from Section 13.4, which implies [13,7,5]_4.
+   3. [18,9,8]_4; see [143].
+   4. [12,6,6]_4 from Section 17.1.
+   5. [12,8,4]_4 (again from the elliptic quadric).

The following genuinely additive (nonlinear) codes are used in the table: