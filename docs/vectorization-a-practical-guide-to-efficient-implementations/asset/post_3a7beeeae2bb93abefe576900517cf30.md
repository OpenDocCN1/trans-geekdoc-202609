

- All code examples are available at github.com/sapphire008/vectorization-book-supplement. Note that some code examples are simulations using random inputs, so rerunning the notebooks will not necessarily get the same results as the ones provided in the book.

- To further clarify many of the vectorization operations, illustrative figures have been incorporated to visually represent the logic behind them, often accompanied by detailed explanations either within the text body or in the caption.

- The principles discussed in this book should be agnostic to specific versions of Python, NumPy, TensorFlow, or PyTorch. By default, my code examples were tested using python==3.10.6, numpy==1.23.4, pandas==2.1.1, scikit-learn==1.3.0, scipy==1.11.1, tensorflow==2.13.0, keras==2.13.1, and torch==2.1.0. However, I will specify the library versions alongside code examples when the versions used are not the default, or whenever relevant or necessary to emphasize the versions.

## Limitations:

- Note that the carriage return symbol “↲” within the code block (with shaded background) is used to indicate a line break to accommodate formatting of long lines.

- Code examples and case studies implemented to solve certain problems may not always be the most optimal solution, though it is honestly my best effort to come up with these solutions when writing this book. Sometimes, I also specifically made a decision to implement certain things not as efficiently as possible but to illustrate the practical application of the concepts introduced in the chapter. Because the materials of each chapter in the book build upon each other, I have made an explicit choice not to use a functionality that would be introduced in a later chapter. Still, this demonstrates the beauty of vectorization and coding in general: there is not a single solution to a specific problem in practice. Nonetheless, I encourage readers to find more efficient ways to solve the case study problems. On the other hand, if the readers found a bug in one of the implementations, please feel free to open an issue at github.com/sapphire008/vectorization-book-supplement.

- When comparing the vectorization libraries, it is possible that I may be ignorant of certain functionalities specific to the library even though the information contained in this book is to the best of my current knowledge. I may sometimes claim that one library does not implement functionality that another library implements at the time of writing, but if readers found the other library indeed implemented that functionality, I stand corrected and will make the best effort to update this information in future editions of the book.

My hope is that by the end of this book, the readers will be well-versed in the foundational and advanced vectorization techniques of implementing scalable machine learning algorithms and will be ready to tackle real-world challenges.

November 29, 2023
New York

Edward DongBo Cui
Director of Data Science
DotDash Meredith, New York

## Acknowledgment

I express my deepest gratitude to Ryan Beauchemin and Kendall Meyer for their invaluable reviews and contributions, which have greatly enhanced the quality of this book. I also thank Ilmir Moussikaev for believing in my potential and providing me with the opportunity to create something remarkable on the Peacock streaming platform. This specific experience was the cornerstone of my career, leading me to acquire the knowledge necessary to write this book. I also want to extend my heartfelt appreciation to my students. Teaching and mentoring them on various techniques in machine learning and data science provided me with the insights and material needed to write this book. A special thanks to Chris Haroun, whose inspiration and guidance motivated me to embark on this writing endeavor. Lastly, I am immensely thankful to my wife for her unwavering support throughout this journey.

## 1 Introduction to Vectorization

### 1.1 What Is Vectorization

**Vectorization** is a type of parallel computing paradigm that performs arithmetic operations on an array of numbers [Intel, 2022] within a single data processing unit (either CPU or GPU). Modern CPUs can perform between 4 and 16 single precision (float32) parallel computations, depending on the type of instructions [Intel, 2022] (see Figure 1.1).

Here, SSE, or streaming SIMD (single-instruction-multiple-data) extension, has 128-bit registers; each register is used to store 32-bit of data for computations. This is equivalent to performing four single-precision (float32) operations or two double-precision (float64) operations. Intel's AVX512, or Advanced Vector Extension 512, on the other hand, has 512-bit registers and can therefore process 512 bits of data simultaneously. This is equivalent to performing 16 single-precision or 8 double-precision operations.

The term “Vectorization” also refers to the process of transforming an algorithm computable on one data point at a time to an operation that calculates a collection of data simultaneously [Kharchenko, 2018]. A classic example is the dot product operation,

\(\sum_{i}^{n} a_i b_i = \mathbf{a} \cdot \mathbf{b}\)

where \(\mathbf{a} := [a_1, a_2, a_3, \dots, a_n]\), and \(\mathbf{b} := [b_1, b_2, b_3, \dots, b_n]\).

The dot product operation on the right-hand side of the equation is the vectorized form of the summation process on the left. Instead of operating on one element of the array at a time, it operates on the collections or arrays, \(\mathbf{a}\) and \(\mathbf{b}\).

![](img/e891acaacd4fb5b80dab2ed824618203_23_0.png)

Figure 1.1 CPU vector computations.

> **Note**
> 
> Another definition of the term “vectorization” is related to the more recent advances in large language models: using a vector or an array of values to represent a word. This is more commonly known as **embedding** in the literature which originated from the word2vec model in natural language processing. In Chapters 6 and 7, we will introduce the idea of representing string or categorical features as numerical values, i.e. integer indices, sparse one-hot encoding vectors, and dense embedding vectors.

### 1.1.1 A Simple Example of Vectorization in Action

Suppose we want to take the dot product of 1 million random numbers drawn from the uniform distribution. Using Python’s `for` loop, we would typically implement this algorithm as the follows:

```
import random
def sqrt_of_n_random_numbers(n=1_000_000) :
    result = 0
    for _ in range(n) :
        a = random.uniform(0, 1)
        b = random.uniform(0, 1)
        result += a * b
    return result
```

On my M1 MacBook Pro under Python 3.11.4, this is the runtime of the above function:

```
294 ms ± 1.39 ms per loop (mean ± std. dev. of 7 runs, 1 loop each)
```

If we implement the algorithm using numpy with vectorization

```
import numpy as np

def sqrt_of_n_random_numbers_np(n=1_000_000) :
    a = np.random.rand(n)
    b = np.random.rand(n)
    result = np.dot(a, b)
    return result
```

Under the same setup, we have the following runtime of the vectorized implementation.

```
7.9 ms ± 119 μs per loop (mean ± std. dev. of 7 runs, 100 loops each)
```

This is a ~37× speed-up by vectorization!

### 1.1.2 Python Can Still Be Faster!

However, the above example is not to discount that certain native Python operations are still faster than NumPy’s implementations, despite NumPy being often used for vectorization operations to simplify for-loops in Python.

For example, we would like to split a list of strings delimited by periods “.”.

Using Python’s list comprehension, we have

```
X = ["foo.bar", "bar.foo", "x.y", "z.k"] * 1000
[x.split(".") for x in X]
```

Line 2 runs for

```
299 μs ± 5.98 μs per loop (mean ± std. dev. of 7 runs, 1,000 loops each)
```

However, in comparison, if we use NumPy’s “vectorized” split operation

```
Y = ["foo.bar", "bar.foo", "x.y", "z.k"] * 1000
Y = np.array(Y)
np.core.defchararray.split(Y, ".")
```

Line 3 runs for

```
1.18 ms ± 4.37 µs per loop (mean ± std. dev. of 7 runs, 1,000
loops each)
```

which is about ~4.0x slower than native Python.

### 1.1.3 Memory Allocation of Vectorized Operations

When using vectorized operations, we need to consider the trade-off between memory and speed. Sometimes, vectorized operations would need to allocate more memory for results from intermediate steps. Therefore, this has implications on the overall performance of the program, in terms of space vs. time complexity. Consider a function in which we would like to compute the sum of the squares of the elements in an array. This can be implemented as a for-loop, where we iterate through each element, take the square, and accumulate the square values as the total. Alternatively, the function can also be implemented as a vectorized operation where we take the square of each element first, store the results in an array, and then sum the squared vector.

```
import numpy as np

def sum_of_square_vectorized(X):
    x = np.asarray(X)
    x_sq = np.square(x) # x ** 2
    res = x_sq.sum()
    return res

def sum_of_square_for_loop(X):
    res = 0
    for x in X:
        res += x * x
    return res
```

Let us use the memory_profiler package to examine the memory usage of each line of the two functions. We can first install the package by pip

