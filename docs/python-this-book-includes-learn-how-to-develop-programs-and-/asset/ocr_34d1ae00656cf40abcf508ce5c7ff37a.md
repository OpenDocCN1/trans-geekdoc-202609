This will result in a “sub-array” of the originalNumPy array but if you would like to generate an “arbitrary array,” you can do so by utilizing "integer array indexing" which enables the generation of arbitrary arrays with the data from another array, as shown in the code below:

```
import numpy as np
a = np.array([[1,2], [3, 4], [5, 6]])
print(a[0, 1, 2], [0, 1, 0])
print(np.array(a[0, 1], a[1], a[2, 0]))
print(a[[0, 0], [1, 1]))
print(np.array(a[0, 1], a[0, 1]]))
```

Basic mathematical operations can be applied to arrays, as shown in the code below, and can be found in “NumPy” as “functions” and “operator overloads.

```
import numpy as np
x = np.array([[1,2],[3,4]], dtype=np.float64
y = np.array([[5,6],[7,8]], dtype=np.float64

print(x + y)
print(np.add(x, y))

print(x - y)
print(np.subtract(x, y))

print(x * y)
print(np.multiply(x, y))

print(x / y)
print(np.divide(x, y))

print(np.sqrt(x))
```