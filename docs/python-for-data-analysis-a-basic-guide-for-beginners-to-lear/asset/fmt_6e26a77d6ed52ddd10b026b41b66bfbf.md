
# Scikit-Learn Overview

In 2007, David Cournapeau developed the foundational code of `Scikit-Learn` as part of a `Summer of Code` project for `Google`. `Scikit-learn` has become one of Python's most famous open-source machine learning libraries since its launch in 2007. But it wasn't until 2010 that Scikit-Learn was released for public use. Scikit-Learn is “an open-sourced and BSD licensed data mining and data analysis tool used to develop supervised and unsupervised machine learning algorithms” build on Python.” `Scikit-learn` offers various “machine learning algorithms” such as “classification,” “regression,” “dimensionality reduction,” and “clustering.” It also offers modules for feature extraction, data processing, and model evaluation.

Designed as an extension to the `SciPy` library, Scikit-Learn is based on `NumPy` and `matplotlib`, the most popular Python libraries. `NumPy` expands Python to support efficient operations on big arrays and multidimensional matrices. `Matplotlib` offers visualization tools and science computing modules are provided by `SciPy`. For scholarly studies, Scikit-Learn is popular because it has a well-documented, easy-to-use, and flexible API. Developers are able to utilize Scikit-Learn for their experiments with various algorithms by only altering a few lines of the code. Scikit-Learn also provides a variety of training datasets, enabling developers to focus on algorithms instead of data collection and cleaning. Many of the algorithms of Scikit-Learn are quick and scalable to all but huge datasets. `Scikit-learn` is known for its reliability, and automated tests are available for much of the library. `Scikit-learn` is extremely popular with beginners in machine learning to start implementing simple algorithms.

## Prerequisites for application of Scikit-Learn library

The `Scikit-Learn` library is based on the `SciPy (Scientific Python)`, which needs to be installed before using `SciKit-Learn.` This stack involves the following:

`NumPy (Base n-dimensional array package)`

`NumPy` is the basic package with Python to perform scientific computations. It includes, among other things: “a powerful N-dimensional array object; sophisticated (broadcasting) functions; tools for integrating C/C++ and Fortran code; useful linear algebra, Fourier transform, and random number capabilities.” The predecessor of `NumPy` called `"Numeric"` was initially developed by Jim Hugunin. In 2005, Travis Oliphant developed `NumPy` by integrating the functionalities of the `Numarray` into `Numeric` and making additional enhancements to it. `NumPy` is widely reckoned as an effective multi-dimensional container of generic data in addition to its apparent scientific uses. It is possible to define arbitrary data types. This enables `NumPy` to integrate with a wide variety of databases seamlessly and quickly. `NumPy` assists the `CPython reference implementation` of Python, which is a `non-optimizing bytecode interpreter.` `NumPy` can partially address the issue of slow execution of mathematical algorithms, by offering multidimensional arrays, functions, and operators that work effectively on arrays by rewriting the code pertaining to the internal loops using `NumPy`.

Python bindings of `OpenCV`'s commonly used computer vision library uses `NumPy arrays` for data storage and operation. Since pictures with various channels are merely depicted as 3-D arrays, indexing, slicing, or masking with other arrays are highly effective methods to access relevant pixels of the picture. The `NumPy array` as a universal data structure in `OpenCV` for pictures, extracted functionality points, filter kernels, and several other, to simplify the `programming workflow and debugging.` The primary objective of `NumPy` is the homogeneity of the multidimensional array. It consists of an element table (generally numbers), all of which are of the same sort and are indicated by tuples of non-negative integers.

The dimensions of `NumPy` are called `axes`, and the array class is called `ndarray`.

These arrays are considered `stridden views on memory.` Unlike the built-in list data structure of Python (also a dynamic array), the `NumPy arrays` can be typed uniformly, which means that `all the elements of a single array must be of the same type.` Such arrays could also be `views of memory buffers assigned to the CPython interpreter by C / C++, Cython, and Fortran extensions without the need to copy data around,` making them compatible with current numerical libraries. The `SciPy package` that incorporates a multitude of such libraries (particularly `BLAS` and `LAPACK`) utilizes this capability. `NumPy` also offers built-in support for `memory-mapped ndarrays.`

To develop `NumPy array` from `Python lists` while accessing elements, use the code below:

```
import numpy as np

a = np.array([1, 2, 3]) 

print(type(a))            

print(a.shape)           

print(a[0], a[1], a[2])  

a[0] = 5               

print(a)               

b = np.array([[1,2,3],[4,5,6]])  

print(b.shape)                     

print(b[0, 0], b[0, 1], b[1, 0])
```

Now, if you would like to index the `NumPy arrays`, you should start with slicing the multidimensional `array` into one dimension with the code below:

```
import numpy as np

a = np.array([[1,2,3,4], [5,6,7,8], [9,10,11,12]])

b = a[:2, 1:3]

print(a[0, 1])   

b[0, 0] = 77     

print(a[0, 1])
```

This will result in a `sub-array` of the original `NumPy array` but if you would like to generate an `arbitrary array`, you can do so by utilizing `integer array indexing` which enables the generation of arbitrary arrays with the data from another array, as shown in the code below:

```
import numpy as np

a = np.array([[1,2], [3, 4], [5, 6]])

print(a[[0, 1, 2], [0, 1, 0]])

print(np.array([a[0, 0], a[1, 1], a[2, 0]]))

print(a[[0, 0], [1, 1]])

print(np.array([a[0, 1], a[0, 1]]))
```

Basic mathematical operations can be applied to arrays, as shown in the code below, and can be found in `NumPy` as `functions` and `operator overloads.`

```
import numpy as np

x = np.array([[1,2],[3,4]], dtype=np.float64)

y = np.array([[5,6],[7,8]], dtype=np.float64)

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

### Matplotlib (Comprehensive 2D/3D plotting)

`Matplotlib` is a 2-dimensional graphic generation library from Python that produces high-quality numbers across a range of hardcopy formats and interactive environments. The `Python script`, the `Python`, `IPython shells`, the `Jupyter notebook`, the web app servers, and select user interface toolkits can be used with matplotlib. `Matplotlib` attempts to further simplify easy tasks and make difficult tasks feasible. With only a few lines of code, you can produce tracks, histograms, scatter plots, bar graphs, error graphs, etc.

A MATLAB-like interface is provided for easy plotting of the `Pyplot Module`, especially when coupled with `IPython`. As a power user, you can regulate the entire line styles, font’s properties, and axis properties through an object-oriented interface or a collection of features similar to the one provided to MATLAB users.

### SciPy (Fundamental library for scientific computing)

`SciPy` is a `collection of mathematical algorithms and convenience functions built on the NumPy extension of Python`, capable of adding more impact to interactive Python sessions, by offering high-level data manipulation and visualization commands and courses for the user. An interactive Python session with `SciPy` becomes an environment that rivals data processing and system prototyping technologies, including `MATLAB, IDL, Octave, R-Lab, and SciLab.`
