
care about why your algorithm works nor you can convince them by going into the details of Linear Algebra, then you MUST SIMPLY QUIT and chase your prosperity elsewhere!

Those lines were only simple examples to showcase the importance of Linear Algebra in Machine Learning. It is hard (if not impossible) to touch base on each and every aspect of Linear Algebra that are important in Machine Learning, in just ONE post. I am sure you will, but again, I suggest you to google "*The importance of Linear Algebra in Machine Learning*" to explore more!

It looks impossible to ignore, right? In the beginning, it may be like torture to force ourselves to dig deep into it. BUT, if you are audacious, what you will gain is amazing knowledge which facilitates your climbing the ladder of Machine Learning.

### 1.3. How to Use This Book?

This book aims to teach you the core concepts in a practical way. The focus is on the Linear Algebra topics that are mostly used in Machine Learning and Deep Learning. To further assist you in understanding the materials, for each notion, a practical Python code is provided. Do NOT just run the code. Try to understand everything by going further and modifying the codes to see what you will understand.

## Chapter 2: Basic Linear Algebra Definitions

### 2.1. Introduction

In the process of practicing Machine Learning [1] you keep hearing buzzwords related to Linear Algebra. Vector, matrix, tensor? Those are basic Linear Algebra Definitions. In this chapter, some of the most commonly used Linear Algebra definitions are introduced.

This chapter aims to accomplish the following:

- Provide the basic definitions in Linear Algebra that we hear every day while dealing with Machine Learning.
- Describe the connection between those basic concepts.
- Demonstration of the commonly used notations.

If you already know Linear Algebra and/or familiar with basic definitions, you may still find some aspects of this article useful, such as the representation of "the commonly used notations."

### 2.2. Scalar and Vector

By using mathematical definition, a scalar is "*an element of a field, which is used to define a vector space, usually the field of real numbers.*" Simply speaking, a scalar is just a number. We usually denote a scalar with a lower case symbol, such as a.

It is worth to have a comparison between scalars and vectors. Most probably, you are familiar with measures such as the velocity of a moving car and the direction of moving, which have both quantity and direction. Such elements are called vector as opposed to scalars, which have magnitude only. We denote vectors with bold symbols such as a.

Subscripts usually denote the elements of the vector. For example the second element of the vector v is denoted as v₂. In general, we show a k-dimensional vector as an array of elements:

![](img/37669628775ca7a07835165249fef088_12_0.png)

Fig. 2.1. The red arrow **v** is the vector and *a* and *b* are scalars denoting the magnitudes of **v** in horizontal and vertical directions.

**v** = $\begin{bmatrix} v_1 \\ v_2 \\ \dots \\ v_{k-1} \\ v_k \end{bmatrix}$

**NOTATION:** We denote a k-dimensional vector as **v** ∈ ℝ^k.

### 2.3. Matrix

In mathematics, a matrix is a rectangular array of elements, such as numbers organized in rows and columns. Usually, the matrices are denoted with bold uppercase, such as **M**. An example of a matrix is below:

**A** = $\begin{bmatrix} 1 & -1 & 3 \\ 4 & 11 & -0.2 \end{bmatrix}$

We denote the matrix elements with subscripts. In the matrix **M**, the element in *i*^th row and *j*^th column is denoted as **M**_{i,j}. So you can easily say for the example above, **M**_{1,2} = −1 and **M**_{2,3} = −0.2. Another important notation is when we desire to refer a row or a column as a whole, i.e., all elements in that particular row/column. In this case, we use “:” sign in the subscript. For example, assume we want to refer to all elements of *i*^th row for matrix **M**. We denote that row with **M**_{i,:}. For matrix **A**, **A**_{1,:} is as below:

**A**_{1,:} = $\begin{bmatrix} 1 & -1 & 3 \end{bmatrix}$

**NOTE:** We usually represent a vector using one column and multiple rows of elements. Henceforth, we can call a vector of size $k$ as a $k \times 1$ matrix. In general, we can informally say vectors are special kind of matrices which are 1-dimensional.

**NOTATION:** We denote a matrix as $\mathbf{M} \in \mathbb{R}^{m\times n}$ in which $m$ and $n$ are the number of rows and columns, respectively.

### 2.4. Tensor

We usually represent data in machine learning, numerically. Tensors are used for such numerical representation. A tensor is simply a container that holds data in N-dimensional space. A Tensor can host and represent multiple matrices. An example is shown below:

$$\begin{bmatrix}\begin{bmatrix}10 & 3 & 3.1 \\ 6 & 12 & -0.2 \\ 1 & -2 & 7 \\ 4. & 1.1 & 81.1\end{bmatrix} \begin{bmatrix}1.0 & -1 & 3 \\ 4 & 11 & -2 \\ 1.1 & -2 & -2 \\ 4 & 4 & -5\end{bmatrix}\end{bmatrix}$$

You can consider a simple 3D tensor as the data cube depicted below:

![](img/37669628775ca7a07835165249fef088_13_0.png)

**Fig. 2.2.** In this tensor, each color represents a matrix and the concatenation of the matrices, forms the tensor.

### 2.5. Conclusion

In this chapter, some of the most commonly used Linear Algebra definitions in Machine Learning are described. Scalar, vector, matrix, and tensor are what you hear the most. It is crucial to know them before proceeding to learn other concepts in Linear Algebra. For more details about the concepts in this chapter, you can refer to [2–6].

## Chapter 3: An Introduction to NumPy

This chapter is dedicated to NumPy [7], one of the most important scientific computing libraries for Linear Algebra and henceforth, Machine Learning! As we will use it frequently to explain the concepts of Linear Algebra, it is important to know how to utilize it.

### 3.1. Introduction

In almost **any Python program code in Machine Learning** you see ”NumPy” library being used! Why? Doing Machine Learning is impossible without Linear Algebra and Linear Algebra is formed by vectors, matrices, etc. Well, **NumPy is one of the best scientific computing packages, in particular, for Linear Algebra.** So that was the short answer to the ”why” question earlier!

**You can conduct a simple 30 minutes research** to find out if I am right or wrong! Search through the web and look for Machine Learning projects and their available source codes. Check to see how many of them use Numpy. Check Python codes. See how many times you see the expression *”import numpy”* or *”import numpy as np”* on top of the code. Do it! It definitely motivates you unless you already are aware of the importance of Numpy.

Here are what you learn in this chapter:

- What is Numpy?
- How we can define arrays in Numpy?
- What are the basic operations?
- How to leverage Numpy for Machine Learning?
- What are the most used tips and tricks in using Numpy?

### 3.2. Data Types

Here, some of the most important Numpy numeric data types that you frequently encounter are described. Numpy supports numerous data types, perhaps even more than Python itself!

#### 3.2.1 Basic Data Types

The most basic data types are as follows: integer (ex : 1, 2, −10), float (ex : 1.1, 3.24, −7.00111), complex (ex : 1 + 2j, 2.1 + 3j, −2 + 1.4j), and Boolean (ex: True, False). You can use NumPy to convert Python elements in many different ways such as changing an array type to another specific type. Let’s start with the following examples:

```python
# Import NumPy library
import numpy as np

# Define a number
a = 10
print('Type, before converting: ', type(a))

# Change the type to float with NumPy
b = np.float64(a)
print('Type, after converting: ', type(b))

# Change the type to float with NumPy
c = float(a)
print('Type, after converting: ', type(c))
```

```text
Type, before converting:  <class ’int’>
Type, after converting:  <class ’numpy.float64’>
Type, after converting:  <class ’float’>
```

> **Question**
> 
> What is the difference between using “np.float64” and the Python “float” built-in function?

#### 3.2.2 Type Conversion

Now, let’s turn a list to a NumPy array. For now, let’s just focus on the data types and conversion, later in this chapter, you will see how to define NumPy arrays in details.

```python
# Import NumPy library
import numpy as np

# Define a Python list
a = [1, 2, 1.3]
print('Type "a": ', type(a))

# Turn Python list into a NumPy array of type np.int32 (Integer
    (-2147483648 to 2147483647))
```
