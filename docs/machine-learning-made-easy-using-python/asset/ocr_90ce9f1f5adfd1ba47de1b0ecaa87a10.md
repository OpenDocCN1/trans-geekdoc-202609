# ndarray objects

NumPy aims to provide an array object that is up to 50x faster that traditional Python lists. The array object in NumPy is called ndarray, it provides a lot of supporting functions that make working with ndarray very easy. Arrays are very frequently used in data science, where speed and resources are very important.
In NumPy, we can create 0-D, 1-D, 2-D and 3-D ndarrays.

| 0-D | (33) |
| 1-D | ([ 11, 27, 18]) |
| 2-D | ([ 3, 5, 6], [5, 7, 11]]) |
| 3-D | ([ 5, 8, 19], [6, 9, 10], [4, 1, 11]]) |

+   In breif ndarrays or n-dimensional arrays are:
* It describes the collection of items of the same type.
* Items in the collection can be accessed using a zero-based index.
* Every item in an ndarray takes the same size of block in the memory.
* Each element in ndarray is an object of data-type object (called dtype). Any item extracted from ndarray object (by slicing) is represented by a Python object of one of array scalar types.