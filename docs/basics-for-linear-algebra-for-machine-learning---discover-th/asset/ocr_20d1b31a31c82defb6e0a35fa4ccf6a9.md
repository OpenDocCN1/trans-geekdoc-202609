The $L^1$ norm is often used when fitting machine learning algorithms as a regularization method, e.g. a method to keep the coefficients of the model small, and in turn, the model less complex.

# ## 8.4 Vector $L^2$ Norm

The length of a vector can be calculated using the $L^2$ norm, where the 2 is a superscript of the $L$. The notation for the $L^2$ norm of a vector is $||v||_2$ where 2 is a subscript.

$$L^2(v) = ||v||_2$$ (8.3)

The $L^2$ norm calculates the distance of the vector coordinate from the origin of the vector space. As such, it is also known as the Euclidean norm as it is calculated as the Euclidean distance from the origin. The result is a positive distance value. The $L^2$ norm is calculated as the square root of the sum of the squared vector values.

$$||v||_2 = \sqrt{a_1^2 + a_2^2 + a_3^2}$$ (8.4)

The $L^2$ norm of a vector can be calculated in NumPy using the `norm()` function with default parameters.

```
# vector L2 norm
from numpy import array
from numpy.linalg import norm
# define vector
a = array([1, 2, 3])
print(a)
# calculate norm
l2 = norm(a)
print(l2)
```

Listing 8.3: Example of calculating the $L^2$ vector norm.

First, a 3-element vector is defined, then the $L^2$ norm of the vector is calculated. Running the example first prints the defined vector and then the vector's $L^2$ norm.

```
[1 2 3]

3.74165738677
```

Listing 8.4: Sample output from calculating the $L^2$ vector norm.

Like the $L^1$ norm, the $L^2$ norm is often used when fitting machine learning algorithms as a regularization method, e.g. a method to keep the coefficients of the model small and, in turn, the model less complex. By far, the $L^2$ norm is more commonly used than other vector norms in machine learning.

# ## 8.5 Vector Max Norm

The length of a vector can be calculated using the maximum norm, also called max norm. Max norm of a vector is referred to as $L^{inf}$ where inf is a superscript and can be represented with