```
12. print("Size: ", my_narray.size)
13. Size: 12
```

# Reshaping array

Suppose you want to change the shape of a ndarray (N-dimension array) without losing the data; it can be done using the reshape() or flatten() method.

# Example: 1.16 Reshaping NumPy array

```
1. # Rank 1 Array
2. my_1array = np.array([1,2,3,4,5,6])
3. print(my_1array)
4. [1 2 3 4 5 6]
```

```
1. # converting Rank 1 array to Rank 2 array
2. my_2array = my_1array.reshape(2, 3)
3. print(my_2array)
4. [[1 2 3]
5. [4 5 6]]
```

```
1. #converting Rank 2 array to Rank 1 array
2. my_1array = my_2array.flatten()
3. print(my_1array)
4. [1 2 3 4 5 6]
```

> Note: Here, you can use my_2array.reshape(6) instead of flatten().

# Pandas

Pandas is an open-source, BSD-licensed library providing high-performance, easy-to-use data structures and data analysis tools for the Python programming language. A DataFrame is a 2-dimensional labeled data structure with columns of potentially different types.

You can install the Pandas package using pip:

```
pip install pandas
```

# Example: 1.17 Pandas DataFrame usage

```
1. import pandas as pd
2. df = pd.DataFrame(data={'fruit': ['apple', 'banana', 'orange',
```