# NUMPY AND OTHER OPERATIONS

NumPy provides the “*” operator to multiply the components of two vectors to produce a third vector whose components are the products of the corresponding components of the initial pair of vectors. This operation is called “Hadamard” product, which is the name of a famous mathematician. If you then add the components of the third vector, the sum is equal to the inner product of the initial pair of vectors.

Listing 2.16 displays the contents of otherops.py that illustrates how to perform other operations on a NumPy array.

# LISTING 2.16: otherops.py

```
import numpy as np

a = np.array([1,2])
b = np.array([3,4])

print(':a:', ',a')
print(':b:', ',b')
print(':a*b:', ',a*b')
print(':np.sum(a*b):', ',np.sum(a*b)')
print(':a*b.sum()):', '(a*b).sum')
```

Listing 2.16 contains two NumPy arrays a and b followed by five print statements that display the contents of a and b, their Hadamard product, and also their inner product that is calculated in two different ways. The output from launching Listing 2.16 is here:

```
('a:', 'array([1, 2])')
('b:', 'array([3, 4])')
('a*b:', 'array([3, 8])')
('np.sum(a*b):', '11')
('a*b.sum()):', '11')
```

# NUMPY AND THE RESHAPE() METHOD