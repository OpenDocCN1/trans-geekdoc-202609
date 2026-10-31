In particular the number of rows is then λ2⁴. The array C above is an OA₂(2,7,2). We record the principle of duality in the following form:

# 2.21 Theorem (binary principle of duality).

Let 𝒞 ⊆ 𝔽₂ⁿ be a linear subspace. Then the minimum distance of 𝒞 and the (maximal) strength of 𝒞⊥ are related by

$d(\mathcal{C}) = t(\mathcal{C}^\perp) + 1.$

So the minimum distance of a binary linear code is precisely one larger than the strength of its dual. For example, the dual of a code [8,4,4]₂ is a code of dimension 4 (hence with 2⁴ = 16 codewords) with strength d − 1 = 4 − 1 = 3. This clearly means that, if we fix any three coordinates and if we fix the 3-tuple in the projection, there will be precisely λ = 16/8 = 2 codewords of our dual code having this 3-tuple in these three coordinates.

The notion of an orthogonal array originated not in information theory but in statistics. It plays a central role in the design of experiments (see the book by Hedayat, Sloane and Stufken [109]) and has many more applications in theoretical computer science and cryptology. The reader is invited to generalize Definition 2.20 from the binary to the general q-ary case.

Observe that any set of n-tuples has a minimum distance and a strength. One speaks of codes if one is primarily interested in the minimum distance, of orthogonal arrays if strength is the center of interest. The principle of duality shows that these two notions are related by duality in the binary linear case. That means we have another large field of applications for our codes.

+   1. The **strength** is the most important parameter of an **orthogonal array**.
+   2. The **principle of duality for binary linear codes** states that the minimum distance of 𝒞 is one more than the strength of its dual.
+   3. An equivalent formulation of the principle of duality is: the minimum distance of 𝒞 is the smallest number t ≥ 1 such that some t columns of a check matrix sum to 0.