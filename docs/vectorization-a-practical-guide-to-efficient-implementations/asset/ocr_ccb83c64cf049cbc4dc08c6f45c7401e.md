![](bbox=[0.1, 0.105, 0.85, 0.285])

Figure 1.1 CPU vector computations.

> > **Note**
> 
> Another definition of the term “vectorization” is related to the more recent advances in large language models: using a vector or an array of values to represent a word. This is more commonly known as **embedding** in the literature which originated from the word2vec model in natural language processing. In Chapters 6 and 7, we will introduce the idea of representing string or categorical features as numerical values, i.e. integer indices, sparse one-hot encoding vectors, and dense embedding vectors.

# 1.1.1 A Simple Example of Vectorization in Action

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