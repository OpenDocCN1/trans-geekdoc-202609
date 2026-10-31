![](bbox=[0.28, 0.14, 0.68, 0.42])

# FIGURE 16.1: Z4 as a graph

codes. In fact, the Nordstrom-Robinson code behaves like a self-dual binary code. It has strength 5. Let us see why.

Denote by v(i) the first digit of γ(i), by h(i) its second digit:

v(0,3)=0, v(1,2)=1, h(0,1)=0, h(2,3)=1.

This means γ(i) = (v(i),h(i)) for all i ∈ Z4. Observe also that h(i)=v(−i). Introduce the structure of a graph on Z4, where two elements form an edge if and only if their difference is ±1. The reason is that two different elements of Z4 have the same prescribed value under v or under h if and only if they form a certain edge of this graph; see Figure 16.1.

Two elements form a nonedge of this graph if they differ by 2. For every i ∈ Z4, we have that v(i) ≠ v(2+i), analogously for h.

Now consider N R as an orthogonal array. We want to show it has strength 5. Denote the coordinates of the octacode by s_i, i = 1,...,8 and by v_i and h_i for i = 1,...,8 the coordinates of N R. Here the entry in v_i is the image of the entry in s_i under v, analogously for h_i. By definition, the eight columns {v1,h1,...,v4,h4} are independent.

Also use the result of Exercise 16.5.5: the automorphism group of the octacode is 3-transitive on the eight coordinates, and it has only two orbits on unordered 4-sets of coordinates, with representatives {1,2,3,4} and {1,2,3,8}.

Let M be a set of five columns of the Nordstrom-Robinson code. If they are derived from only three coordinates s_i it can be assumed these are s1,s2,s3 because of the triple transitivity of the automorphism group. It follows that M is independent. The same is true if M is derived from four coordinates s_i if those are in the orbit of {s1,s2,s3,s4}. Assume they are in the orbit of s1,s2,s3,s8. We can assume M = {v1,h1,v2,v3,v8} in this case. The projection of x(a,b,c,d) (see Equation 16.1) on these coordinates is (v(a),h(a),v(b),v(c),v(a−b+c+2d)). Fix a,b,c. When d varies in Z4, the