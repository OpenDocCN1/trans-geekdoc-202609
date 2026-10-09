set, and for the elements A₁, A₂, and A₃ and the constants f₁, f₂, and f₃, if we have

```
```
[A₁, f₂A₂ + f₃A₃] = f₂ [A₁, A₂] + f₃ [A₁, A₃]      (1.23)
[f₁A₁ + f₂A₂, A₃] = f₁ [A₁, A₃] + f₂ [A₂, A₃]      (1.24)
[A₁, A₂] = -[A₂, A₁]                                (1.25)
[A₁, [A₂, A₃]] + [A₃, [A₁, A₃]] + [A₂, [A₃, A₁]] = 0    (1.26)
```
```

then this linear set called a Lie algebra. With the Lie algebra, we can get the corre-sponding Lie group.

# **1.7.2 Lie group machine learning SO(3) classifier**

For a 0 or 1 classification problem, suppose that the sample set *G* is (*x*₁, *y*₁), (*x*₂, *y*₂),..., (*x*I, *y*I) ∈ Rᴺ × Y, where *Y* = [−1, +1], to seek classifier *f*(*X*), such that *y* · *f*(*x*) > 0.

Then, the SO(3) classifier of Lie group machine learning will be constructed on the basis of the typical group SO(*n*).

**Definition 1.26.** The set of all orthogonal transforms in *n*-dimensional vector space is called an *n*-dimensional orthogonal group *O(n*).*

In this case, the problem is transformed into the three-dimensional vector space, i.e., the three-dimensional orthogonal group *O(3)* is discussed. This group can also be defined as a group of all 3 × 3 orthogonal matrices, since these two groups have isomorphism [12].

**Definition 1.27.** If *R* is an orthogonal matrix, it satisfies the equation *RR*T = *R*T*R* = *I*, where *I* is the identity matrix and *R*T is the transpose matrix of *R*. Take the determinant of both sides of the equation, and note that det *R* = det *R*T, yielding (det *R*)² = 1 or det *R* = ±1, such that the matrix of *O(3)* groups is divided into two groups. A set of matrix determinants is +1 and other set of determinants is −1. Then, all orthogonal matrices with a determinant of +1 form a group called a three-dimensional special orthogonal group, and it is represented by SO(3), i.e., SO(3) = {*O* ∈ *O*(3)| |*O*| = 1}. The SO(3) classifier algorithm is described as follows:

```
```text
Algorithm 1.18: Classification algorithm of SO(3) classifier
Initialisation: G is a group, its group elements are {x_1, x_2, ..., x_n} //
Input: G //
Output: {1, -1}//
    procedure SOClassifier(G)
    if G is a 3 x 3 orthogonal matrix group
        //That is, this input data set is a three-dimensional orthogonal group O(3)//
        then
            for i=1 to n do
                //calculate the matrix determinant value of each group element //
                if detx_i == -1
```
```