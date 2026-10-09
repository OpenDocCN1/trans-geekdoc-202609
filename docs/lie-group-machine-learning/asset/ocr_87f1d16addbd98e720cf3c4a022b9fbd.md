Let the data reduction category be C. Then, there is a family of data objects obC. The known objects X ∈ obC are primitive objects of a high-dimensional data set. There is a family morphism such that any pair of objects A, B corresponds to a set C(A, B).

The main purpose of dimensionality reduction is to find the data manifold object category with appropriate low-dimensional coordinates, i.e., the original high-dimensional data set by various object morphisms is mapped into a low-dimensional space. The low-dimensional data object is a simple representation of the original high-dimensional data object.

Therefore, the dimensionality reduction problem of high-dimensional data can be represented by data dimensionality reduction category C:

+   1.  The original high-dimensional data object X: Ω^D ⊂ X, Ω^D is an object set for data samples, Ω^D = {x_n}^{N}_{n=1} ⊂ R^D, D is the dimension of the data.

+   2.  Low-dimensional data objects after dimensionality reduction Y, i.e., the low-dimensional representation space of data: Ω^d ⊂ Y, Ω^d is a low-dimensional data object that is mapped by a series of morphisms for high-dimensional data sample set objects Ω^D, d ≤ D is the dimension of data after dimensionality reduction.

+   3.  Data dimension reduction morphism f: X → Y, f ∈ C(X, Y), X, Y ∈ obC. Take sample data objects, e.g., f(Ω^D): Ω^D → Ω^d. We call Ω^d as the dimension reduction representation of Ω^D.

Similarly, we can obtain the corresponding data recovery process from the data reduction dimension category. The lower-dimensional data objects, which are reduced from the dimension, are transformed by the corresponding morphism to obtain the original high-dimensional data objects, represented as the following data recovery morphism:

f⁻¹ : Y → X, f⁻¹ ∈ C(Y, X), X, Y ∈ obC. The object represented by the sample data object after dimension reduction can be denoted as f⁻¹(Ω^d): Ω^d → Ω^D.

It needs to be explained that the data recovery morphism f⁻¹ needs to satisfy certain conditions. When the condition is not satisfied, the data recovery morphism is meaningless. In general, in the linear data reduction dimension category C, the data recovery morphism f⁻¹ is meaningful, but in the nonlinear dimensionality reduction category, the data recovery morphism f⁻¹ is meaningless.

In the data reduction category C, searching for dimension reduction morphism f is the key to the formation of the whole category. However, the dimensionality reduction morphism f of this data can be of many forms. At present, from the viewpoint of mathematical thought, there are mainly linear and nonlinear representations of a morphism. Hence, we can start from two angles when we describe the data reduction category C.

When the dimensionality reduction morphism of the data reduction category C is represented by a linear representation, the dimensionality reduction algorithm based on the data reduction category can be described as follows: