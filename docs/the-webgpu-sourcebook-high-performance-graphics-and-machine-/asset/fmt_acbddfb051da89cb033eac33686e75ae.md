
```
override vectors_per_row: u32;
override group_size_x: u32;
override group_size_y: u32;

@binding(0) @group(0) var<storage, read_write> aMat : array<vec4f>;
@binding(1) @group(0) var<storage, read_write> bMat : array<vec4f>;
@binding(2) @group(0) var<storage, read_write> cMat : array<f32>;

@compute @workgroup_size(group_size_x, group_size_y)
fn computeMain(@builtin(global_invocation_id) gid : vec3<u32>) {

    var sum = 0.0;
    let a_row = gid.x * vectors_per_row;
    let b_row = gid.y * vectors_per_row;

    // Multiply row of A by row of B^T
    for (var i: u32 = 0; i < vectors_per_row; i++) {
        sum += dot(aMat[a_row + i], bMat[b_row + i]);
    }

    // Store the result to C
    cMat[a_row * 4 + gid.y] = sum;
}
```

Each invocation is responsible for setting a value in the `C` matrix. To compute this value, it reads vectors from the `A` and `B` matrices and adds their `dot` products together. Once all the dot products have been computed, the invocation stores the sum in the `C` matrix at the location given by its global ID.

While matrix multiplication is an important part of many matrix operations, this chapter is particularly concerned with matrix factorization using `QR` decomposition. The factorization methodology discussed in this chapter relies on the Householder transformation, which will be discussed next.

## The Householder Transformation

Most discussions of vector math include addition, subtraction, and multiplication, but `vector reflection` is also important in many applications. The concept is simple: given an input vector and a vector perpendicular to a surface, find the reflection of the input vector across the surface.

The procedure for computing this is called the `Householder transformation`, and this section shows how it can be implemented in `WebGPU`. But first, it's important to be familiar with vector projection.

### Vector Projection

A vector projection is the portion of one vector that points in the same direction as a second vector. In [Figure 11.5](#chapter11.xhtml#fig11_5), vector b is split into two components: a component called p, which points in the same direction as a, and q, which points in a direction orthogonal to a. It should be clear that `b = p + q`.

![Figure 11.5 Vector projection.](images/fig11_5.jpg)

[Figure 11.5](#chapter11.xhtml#b11fig11_5) Vector projection.

In this diagram, p is the vector projection of b on a. If θ is the angle between a and b and |b| is the length of b, the length of p equals |b| cos θ. The direction of p is given by a's unit vector. This is obtained by dividing a by its length, denoted as |a|. The following equation shows the result:

$$p = \\left| b \\right|\\cos\\left( \\theta \\right)\\frac{a}{\\left| a \\right|}$$

This would be easy to compute it weren't for the cosine. Thankfully, a relationship exists between the cosine of the angle between two vectors and their dot product. The proof is lengthy, but the result is given as follows:

$$cos\\left( \\theta \\right) = \\frac{a \\cdot b}{\\left| a \\right|\\left| b \\right|}$$

By placing this into the previous equation, we can arrive at a better equation for computing p:

$$p = \\left| b \\right|\\frac{a \\cdot b}{\\left| a \\right|\\left| b \\right|}\\frac{a}{\\left| a \\right|} = \\frac{a \\cdot b}{\\left| a \\right|}\\frac{a}{\\left| a \\right|} = \\frac{a \\cdot b}{\\left| a \\right|^{2}}a$$

In general, the vector projection of vector b on a vector a is expressed with the term `proj[a] b`. `proj[a] b` has the same direction as a, and b – `proj[a] b` is orthogonal to a.

### Vector Reflection

Many algorithms in linear algebra require vector reflection, and the reason for this will become clear shortly. [Figure 11.6](#chapter11.xhtml#fig11_6) illustrates a simple example. We start with two vectors: x and u. u is perpendicular to `M` (which stands for mirror). The goal is to find x′, the vector obtained by reflecting x in `M`. In this two-dimensional case, `M` is simply a line. But it's a plane in three dimensions and a hyperplane in four or more dimensions.

![Figure 11.6 Vector reflection.](images/fig11_6.jpg)

[Figure 11.6](#chapter11.xhtml#b11fig11_6) Vector reflection.

To find x′ in terms of x and u, we need to take vector projections. [Figure 11.7](#chapter11.xhtml#fig11_7) shows how this works. x is split into p and q, where p is the vector projection of x on u and q is orthogonal to p. Similarly, x′ is split into p′ and q′, where p′ is the vector projection of x′ on u and q′ is orthogonal to p′.

![Figure 11.7 Vector reflection in terms of vector projection.](images/fig11_7.jpg)

[Figure 11.7](#chapter11.xhtml#b11fig11_7) Vector reflection in terms of vector projection.

This figure clarifies the relationships between p and p′ and q and q′. Because x′ equals the sum of p′ and q′, we can compute it in the following manner:

$$\\begin{matrix} {x' = p' + q' = \\left( {- proj\_{u}x} \\right) + \\left( {x - proj\_{u}x} \\right)} \\\\ {x' = x - 2proj\_{u}x} \\\\ {x' = x - 2u\\frac{u \\cdot x}{\\left| u \\right|^{2}}} \\\\ \\end{matrix}$$

This final equation gives us a clear relationship between x′, x, and u. This equation helps us compute the `QR` decomposition of a matrix, but before we discuss the decomposition algorithm, I need to introduce the outer product and show how it can be used to form Householder matrices.

### Outer Products and Householder Matrices

A vector can be thought of as a matrix with a single row or a single column. Mathematicians commonly treat vectors as matrices with a single column, and such vectors are called `column vectors`. In contrast, transposed column vectors are considered matrices with a single row, or `row vectors`.

With this matrix interpretation of vectors, we can arrive at a new interpretation of the dot product. Instead of multiplying vectors, the dot product can be thought of as multiplying a 1-by-n matrix and an n-by-1 matrix. The result is a 1-by-1 matrix, or a scalar. With this interpretation, we can refer to the dot product using matrix terminology: `a^Tb` instead of `a ∙ b`. The following equation makes this clearer:

$$a \\cdot b = a^{T}b = \\left| \\begin{matrix} a\_{0} & a\_{1} & a\_{2} & a\_{3} \\\\ \\end{matrix} \\right|\\left| \\begin{matrix} b\_{0} \\\\ b\_{1} \\\\ b\_{2} \\\\ b\_{3} \\\\ \\end{matrix} \\right| = a\_{0}b\_{0} + a\_{1}b\_{1} + a\_{2}b\_{2} + a\_{3}b\_{3}$$

Using this notation, we can arrive at a new type of product called the `outer product`. Instead of multiplying a row vector by a column vector, this product reverses the operation and computes `ab^T` instead of `a^Tb`. Despite the similar appearance, the outer product is significantly different from the dot product. The dot product multiplies a 1-by-n matrix by an n-by-1 matrix and produces a 1-by-1 matrix. The outer product multiplies an n-by-1 matrix by a 1-by-n matrix and produces an n-by-n matrix. This is shown in the following equation:

$$ab^{T} = \\left| \\begin{matrix} a\_{0} \\\\ a\_{1} \\\\ a\_{2} \\\\ a\_{3} \\\\ \\end{matrix} \\right|\\left| \\begin{matrix} b\_{0} & b\_{1} & b\_{2} & b\_{3} \\\\ \\end{matrix} \\right| = \\left| \\begin{matrix} {a\_{0}b\_{0}} & {a\_{0}b\_{1}} & {a\_{0}b\_{2}} & {a\_{0}b\_{3}} \\\\ {a\_{1}b\_{0}} & {a\_{1}b\_{1}} & {a\_{1}b\_{2}} & {a\_{1}b\_{3}} \\\\ {a\_{2}b\_{0}} & {a\_{2}b\_{1}} & {a\_{2}b\_{2}} & {a\_{2}b\_{3}} \\\\ {a\_{3}b\_{0}} & {a\_{3}b\_{1}} & {a\_{3}b\_{2}} & {a\_{3}b\_{3}} \\\\ \\end{matrix} \\right|$$

We can use this vector-as-matrix interpretation to manipulate the equation for vector reflection. If we replace u ∙ x with u^Tx, the new relationship will be given as follows:

$$x' = x - 2u\\frac{u \\cdot x}{\\left| u \\right|^{2}} = x - 2\\frac{u\\left( {u^{T}x} \\right)}{\\left| u \\right|^{2}}$$

As mentioned earlier, matrix multiplication is associative, so `A(BC) = (AB)C`. We can use this relationship to change `u(u^Tx)` in the reflection equation to `(uu^T)x`. This provides the following relationship:
