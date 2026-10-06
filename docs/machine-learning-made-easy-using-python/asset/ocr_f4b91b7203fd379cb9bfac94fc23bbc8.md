# More with ndarrays

We can reverse a ndarray using <array>::[-1] syntax

```
In [56]: import numpy as np
ar = np.array([1, 2, 3, 4])
ar
Out[56]: array([1, 2, 3, 4])
nIn [55]: ar = ar[::1]
ar
Out[55]: array([4, 3, 2, 1])
```

We can broadcast a whole ndarray without doing it the long way

```
In [56]: import numpy as np
ar = np.array([1, 2, 3, 4])
ar
Out[56]: array([1, 2, 3, 4])
In [62]: # the long way - ar + [1,1,1,1]
ar = ar + 1
ar
Out[62]: array([2, 3, 4, 5])
```

We can sort an array with the sort function

```
In [63]: import numpy as np
ar = np.array([5,1,3,9])
ar
Out[63]: array([5, 1, 3, 9])
In [64]: ar.sort()
ar
Out[64]: array([1, 3, 5, 9])
```

There are many built-in ndarray methods that will not be discussed now, but will be used in various steps, you may go to the documentation to find all the functions and their roles, as we don't require every function for our data processing and analyzing, all the miscellaneous functions are not discussed in this book