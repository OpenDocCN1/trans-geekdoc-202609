# 3.3.2 Special functions

We can create NumPy arrays using some special NumPy functions. I used a couple of them below for your reference:

```
# Import NumPy library
import numpy as np

### Defining arrays using special functions ###
# Arguments:
# shape: The shape of the numpy array
# dtype: Specifying the data type (not required)

# Defining an all-zero array
zeroArray = np.zeros(shape=(3,5), dtype=np.int16 )
print("zeroArray: ", zeroArray)

# Defining an all-one array
onesArray = np.ones(shape=(3,5), dtype=np.float32 )
print("onesArray: ", onesArray)

# Defining an array filled with one specific elements
fullArray = np.full(shape=(3,5), fill_value=4.2, dtype=np.float64 )
print("fullArray: ", fullArray)
```

```
zeroArray: [[0 0 0 0 0]
 [0 0 0 0 0]
 [0 0 0 0 0]]
onesArray: [[1. 1. 1. 1. 1.]
 [1. 1. 1. 1. 1.]
 [1. 1. 1. 1. 1.]]
fullArray: [[4.2 4.2 4.2 4.2 4.2]
 [4.2 4.2 4.2 4.2 4.2]
 [4.2 4.2 4.2 4.2 4.2]]
```

![](bbox=[0.28, 0.7, 0.48, 0.77])

![](bbox=[0.51, 0.7, 0.71, 0.77])

Fig. 3.3. Defining arrays filled with specific elements

One of the most important special functions is np.arange which is similar to Python range built-in function. An example of using np.arrage is as below: