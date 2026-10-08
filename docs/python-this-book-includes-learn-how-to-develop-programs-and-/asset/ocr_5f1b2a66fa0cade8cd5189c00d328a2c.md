# Squaring an Array

This command raises each element to the power of 2 to get the following result:

```
>>> b**2
[1 4 9 16]
```

# A Trigonometric Function Conducted on the Array

This command uses cosine to every value within the b array to attain the following result:

```
>>> np.cos(b)
[ 0.54030231 -0.41614684 -0.9899925 -0.65364362]
```

# Conditional Operations

The conditional command applies a conditional operation to every element of the b array to generate the required Boolean values:

```
>>> b<2
[True False False False]
```

# Matrix Multiplication

Two matrices can be multiplied element by element or using a dot product. The commands below will evaluate element-by-element multiplication:

```
>>> A1 = np.array([[1, 1]],
[0, 1]])
>>> A2 = np.array([[2, 0]],
[3, 4]])
>>> A1 * A2
[[2 0]
[0 4]]
```

The dot product can be computed using the following command:

```
>>> np.dot(A1, A2)
[[5 4]
[3 4]]
```

# Indexing and Slicing

If you would like to select a given element of an array, you can complete this step using indexes: