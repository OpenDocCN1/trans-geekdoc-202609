>>> n_array[1, 2]
This will select the second array and then select the third value in the array. It can also be considered as an intersection of the first row and the second column of the matrix.
In case a range of values has to be highlighted in a row, then you can write the following command:

```
>>> n_array[ 0, 0:3 ]
[ 0 1 2 ]
```

The 0.3 value represents the first three values of the first row.
The entire row of values can be highlighted using the following command:
>>> n_array[ 0, : ]
[ 0 1 2 ]
By using this command, the whole column of values require to be selected:
>>> n_array[ :, 1 ]
[ 1 5 9 ]

Shape Modification
When the array is created, it can change the shape of it too. The command below flattens the array.
>>> n_array.ravel()
[ 0 1 2 3 4 5 6 7 8 9 10 11]
The above command changes the shape of the array into six rows and two columns format. Additionally, remember that when reshaping, the new shape should have an equal number of elements as the initial one:

```
>>> n_array.shape = (6,2)
>>> n_array
[[ 0 1 ]
[ 4 5 ]
[ 6 7 ]
[ 8 9 ]
[ 10 11]]
```