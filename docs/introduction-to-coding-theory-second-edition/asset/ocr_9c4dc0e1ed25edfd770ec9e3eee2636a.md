# Chapter 10

# Three-dimensional codes and projective planes

Basic concepts: Projective planes and geometric description of three-dimensional codes. Application to congestion-free networks.

In this chapter we want to learn how to interpret linear codes geometrically. The starting point is a generator matrix of the code. We limit ourselves to the case of three-dimensional codes. The underlying geometry is the projective plane PG(2, q), see Chapter 7. Recall the basic data:

We call **points** of PG(2, q) the one-dimensional subspaces of F_q^3, the two-dimensional subspaces are called **lines**. There are q^2 + q + 1 points and equally many lines. The lines form the blocks of a design, a Steiner system S(2, q + 1, q^2 + q + 1) (in particular each line has q + 1 points). The smallest projective plane is PG(2, 2) (7 points, 7 lines, each line has 3 points, each point is on 3 lines, each pair of points is on precisely 1 line). This binary projective plane PG(2, 2) is also known as the **Fano plane**.

Each nonzero vector (x, y, z) of PG(2, q) generates a one-dimensional subspace, hence a point. We can label the points by these triples. The difference between triples and points is that triples, which are scalar multiples of each other, define the same point. The Fano plane is depicted in Figure 10.

As an example, consider the binary code with generator matrix

G = \begin{pmatrix} 1 0 0 1 1 0 1 \\ 0 1 0 1 0 1 1 \\ 0 0 1 0 1 1 1 \end{pmatrix}.

Here is the link to geometry: we consider the **columns** of G as points of PG(2, 2). In this case each point of the Fano plane occurs precisely once as a column. A geometer would identify this code C (or this generator matrix)