# 2.2 Basic language elements

# 2.2.1 Basic data types and arrays

As a general purpose language, Python contains basic programming concepts such as basic data types, loops, conditional statements, and subroutines. We will briefly review the associated syntax with examples that are provided in file FirstProgram.ipynb. In addition to such programming constructs, major programming languages as Python are supported by a large number of libraries that enable a wide array of programming styles and specialized functions. We are mainly interested in scientific computing, in contrast to system programming. We therefore base almost all programs in this book on the NumPy library. NumPy provides basic support of common scientific constructs and functions such as trigonometric functions and random number generators. Most importantly, it provides support for N-dimensional arrays. NumPy has become the standard in scientific computing with Python. We will use these established constructs to implement vectors, matrices and higher dimensional arrays. While there is a separate matrix class, this construct is limited to a two dimensional structure and has gained widespread acceptance.

An established way to import the NumPy library in our programs is to map them to the space "np" with the command import numpy as np. In this way, the specific methods or functions of NumPy are accessed with the prefix np.. In addition to importing NumPy, we always import a plotting library as plotting results will we specifically use the popular PyQt package of the Matplotlib library. Hence, we nearly always start our program with the two lines

Listing 2.1 FirstProgram.ipynb (part 1)
import numpy as np
import matplotlib.pyplot as plt

In the following, we will walk through a program in the Jupyter environment FirstProgram. These lines of code are intended to show the syntax of the basic programming constructs that we need in this book. We start by demonstrating the basic data types that we will be using frequently. We are mainly concerned with numerical data, of which a scalar is the simplest example.

Listing 2.2 FirstProgram.ipynb (part 2) with output
#basic data types
aScalar=4
print(aScalar)
4

We here show the code as well as the response of running the program with the print() function. Comment lines can be included with the hash-tag symbol #. The type of variables are dynamically assigned in Python. That is, a variable name and corresponding memory space is allocated the first time a variable is used on the left hand side of an assignment operator =\. In this case it is an integer value, but we could also assign a real-valued variable with textScalar=4.