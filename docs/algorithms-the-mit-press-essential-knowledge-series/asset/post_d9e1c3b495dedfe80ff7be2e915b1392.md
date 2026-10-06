
To express this more succinctly, we write down the prices for the bagels and croissants as a vector:

[2.00 1.50]

We also write down the daily sales in a matrix. The matrix will have two columns, one per shop, and two rows, one for the bagels and one for the croissants:

```
\begin{bmatrix} 10 & 15 \\ 20 & 10 \end{bmatrix}
```

Then to find the total sales per shop, we multiply the elements of the vector with each column of the sales matrix and add them up. This defines the product of the vector with the matrix:

```
[2.00 1.50] \times \begin{bmatrix} 10 & 15 \\ 20 & 10 \end{bmatrix} = [2.00 \times 10 + 1.50 \times 20 \quad 2.00 \times 15 + 1.50 \times 10] = [50 45]
```

The product of a vector with a matrix is a special case of the product of two matrices. Let’s extend the example so that instead of having a vector with the prices of the bagels and croissants, we have a matrix with the prices and profits per sale:

```
$\begin{bmatrix} 2.00 & 1.50 \\ 0.20 & 0.10 \end{bmatrix}
```

To find the total sales per shop and total profit per shop, we will create a matrix in which the entries in the $i$th row and $j$th column will be the sum of products of the $i$th row of the prices and profits matrix with the $j$th row of the sales matrices. This is the definition of the product of two matrices:

```
$\begin{bmatrix} 2.00 & 1.50 \\ 0.10 & 0.20 \end{bmatrix} \times \begin{bmatrix} 10 & 15 \\ 20 & 15 \end{bmatrix} = \begin{bmatrix} 2.00 \times 10 + 1.50 \times 20 & 2.00 \times 15 + 1.50 \times 10 \\ 0.10 \times 10 + 0.20 \times 20 & 0.10 \times 15 + 0.20 \times 15 \end{bmatrix} = \begin{bmatrix} 50 & 45 \\ 5 & 3.5 \end{bmatrix}
```

Returning to pagerank, in each round the calculation of the pagerank vector is really the product of the value of the pagerank vector in the previous round with the hyperlink matrix. As we go through the rounds, we get successive estimates of the pageranks—that is, successive estimates of the pagerank vector that is made up of them.

To get these successive estimates of the pagerank vector we only need to multiply the vector in each round with the hyperlink matrix, thereby getting the vector for the next round.

In the first round, we start with a pagerank vector whose contents are all equal to $1 / n$, where $n$ is the number of pages. If we denote this first pagerank vector by $\pi_1$, the pagerank vector at the end of the first round by $\pi_2$, and the hyperlink matrix by $H$, we have:

$\pi_2 = \pi_1 \times H$

In each round we use the pagerank vector of that round to calculate the pagerank vector for the following round. In the second voting round, where we got our third page-rank estimates—that is, our third pagerank vector—we performed the calculation:

$\pi_3 = \pi_2 \times H = (\pi_1 \times H) \times H = \pi_1 \times (H \times H) = \pi_1 \times H^2$

In the third voting round, we got our fourth pagerank vector:

$\pi_4 = \pi_3 \times H = (\pi_1 \times H^2) \times H = \pi_1 \times (H^2 \times H) = \pi_1 \times H^3$

As in every iteration, we multiply the result of the previous iteration by the hyperlink matrix, and in the end this is a series of products of the successive estimates of the pagerank vector by the hyperlink matrix. As we see, this is equivalent to multiplying the initial pagerank vector with increasing powers of the hyperlink matrix. This method of calculating successive approximations is called the power method. We see therefore that the calculation of the pageranks of a set of web pages is an application of the power method to the pagerank vector and hyperlink matrix, until the resulting pagerank vector does not change, or as we say, until it converges to a stable value—our final pagerank metrics.

We have just reached a more precise description of how to calculate the pageranks of a web graph:

- 1. Form the hyperlink matrix of the graph.
- 2. Start with initial pagerank estimates, giving a pagerank of $1 / n$ to each page, where $n$ is the total number of pages.
- 3. Apply the power method, multiplying the pagerank vector by the hyperlink matrix until the values of the pagerank vector converge.

Apart from being succinct, this formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, 

We have just reached a more precise description of how to calculate the pageranks of a web graph:

- 1. Form the hyperlink matrix of the graph.
- 2. Start with initial pagerank estimates, giving a pagerank of $1 / n$ to each page, where $n$ is the total number of pages.
- 3. Apply the power method, multiplying the pagerank vector by the hyperlink matrix until the values of the pagerank vector converge.

Apart from being succinct, this formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, 

We have just reached a more precise description of how to calculate the pageranks of a web graph:

- 1. Form the hyperlink matrix of the graph.
- 2. Start with initial pagerank estimates, giving a pagerank of $1 / n$ to each page, where $n$ is the total number of pages.
- 3. Apply the power method, multiplying the pagerank vector by the hyperlink matrix until the values of the pagerank vector converge.

Apart from being succinct, this formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, 

We have just reached a more precise description of how to calculate the pageranks of a web graph:

- 1. Form the hyperlink matrix of the graph.
- 2. Start with initial pagerank estimates, giving a pagerank of $1 / n$ to each page, where $n$ is the total number of pages.
- 3. Apply the power method, multiplying the pagerank vector by the hyperlink matrix until the values of the pagerank vector converge.

Apart from being succinct, this formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, 

We have just reached a more precise description of how to calculate the pageranks of a web graph:

- 1. Form the hyperlink matrix of the graph.
- 2. Start with initial pagerank estimates, giving a pagerank of $1 / n$ to each page, where $n$ is the total number of pages.
- 3. Apply the power method, multiplying the pagerank vector by the hyperlink matrix until the values of the pagerank vector converge.

Apart from being succinct, this formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, 

We have just reached a more precise description of how to calculate the pageranks of a web graph:

- 1. Form the hyperlink matrix of the graph.
- 2. Start with initial pagerank estimates, giving a pagerank of $1 / n$ to each page, where $n$ is the total number of pages.
- 3. Apply the power method, multiplying the pagerank vector by the hyperlink matrix until the values of the pagerank vector converge.

Apart from being succinct, this formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, 

We have just reached a more precise description of how to calculate the pageranks of a web graph:

...

Apart from being succinct, this formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, 

We have just reached a more precise description of how to calculate the pageranks of a web graph:

- 1. Form the hyperlink matrix of the graph.
- 2. Start with initial pagerank estimates, giving a pagerank of $1 / n$ to each page, where $n$ is the total number of pages.
- 3. Apply the power method, multiplying the pagerank vector by the hyperlink matrix until the values of the pagerank vector converge.

Apart from being succinct, this formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, 

We have just reached a more precise description of how to calculate the pageranks of a web graph:

- 1. Form the hyperlink matrix of the graph.
- 2. Start with initial pagerank estimates, giving a pagerank of $1 / n$ to each page, where $n$ is the total number of pages.
- 3. Apply the power method, multiplying the pagerank vector by the hyperlink matrix until the values of the pagerank vector converge.

Apart from being succinct, this formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, 

We have just reached a more precise description of how to calculate the pageranks of a web graph:

- 1. Form the hyperlink matrix of the graph.
- 2. Start with initial pagerank estimates, giving a pagerank of $1 / n$ to each page, where $n$ is the total number of pages.
- 3. Apply the power method, multiplying the pagerank vector by the hyperlink matrix until the values of the pagerank vector converge.

Apart from being succinct, this formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, 

We have just reached a more precise description of how to calculate the pageranks of a web graph:

- 1. Form the hyperlink matrix of the graph.
- 2. Start with initial pagerank estimates, giving a pagerank of $1 / n$ to each page, where $n$ is the total number of pages.
- 3. Apply the power method, multiplying the pagerank vector by the hyperlink matrix until the values of the pagerank vector converge.

Apart from being succinct, this formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, 

We have just reached a more precise description of how to calculate the pageranks of a web graph:

- 1. Form the hyperlink matrix of the graph.
- 2. Start with initial pagerank estimates, giving a pagerank of $1 / n$ to each page, where $n$ is the total number of pages.
- 3. Apply the power method, multiplying the pagerank vector by the hyperlink matrix until the values of the pagerank vector converge.

Apart from being succinct, this formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, 

## Dangling Nodes and the Surfer

We now turn to an example of a graph, consisting of three nodes:

![](img/9d8c5a7f9b1c)

We want to find the pageranks of these nodes. We initialize the pagerank with $1/3$, giving equal weight to each. Then we multiply the pagerank with the hyperlink matrix, which is:

```
\begin{bmatrix} 0 & 1/2 & 1/2 \\ 0 & 0 & 1 \\ 1/3 & 1/3 & 1/3 \end{bmatrix}
```

In the first round, we start with a pagerank vector whose contents are all equal to $1 / n$, where $n$ is the number of pages. If we denote this first pagerank vector by $\pi_1$, the pagerank vector at the end of the first round by $\pi_2$, and the hyperlink matrix by $H$, we have:

$\pi_2 = \pi_1 \times H$

In each round we use the pagerank vector of that round to calculate the pagerank vector for the following round. In the second voting round, where we got our third page-rank estimates—that is, our third pagerank vector—we performed the calculation:

$\pi_3 = \pi_2 \times H = (\pi_1 \times H) \times H = \pi_1 \times (H \times H) = \pi_1 \times H^2$

In the third voting round, we got our fourth pagerank vector:

$\pi_4 = \pi_3 \times H = (\pi_1 \times H^2) \times H = \pi_1 \times (H^2 \times H) = \pi_1 \times H^3$

As in every iteration, we multiply the result of the previous iteration by the hyperlink matrix, and in the end this is a series of products of the successive estimates of the pagerank vector by the hyperlink matrix. As we see, this is equivalent to multiplying the initial pagerank vector with increasing powers of the hyperlink matrix. This method of calculating successive approximations is called the power method. We see therefore that the calculation of the pageranks of a set of web pages is an application of the power method to the pagerank vector and hyperlink matrix, until the resulting pagerank vector does not change, or as we say, until it converges to a stable value—our final pagerank metrics.

We have just reached a more precise description of how to calculate the pageranks of a web graph:

- 1. Form the hyperlink matrix of the graph.
- 2. Start with initial pagerank estimates, giving a pagerank of $1 / n$ to each page, where $n$ is the total number of pages.
- 3. Apply the power method, multiplying the pagerank vector by the hyperlink matrix until the values of the pagerank vector converge.

Apart from being succinct, this formulation allows us to transfer the problem to the realm of linear algebra, the formulation allows us to transfer the problem to the realm of linear algebra, 

| Round | Page 1 | Page 2 | Page 3 |
| :--- | :--- | :--- | :--- |
| Initial | 0.33 | 0.33 | 0.33 |
| 1 | 0.11 | 0.53 | 0.36 |
| 2 | 0.19 | 0.31 | 0.50 |
| 3 | 0.17 | 0.35 | 0.48 |
| 4 | 0.21 | 0.33 | 0.46 |
| 5 | 0.20 | 0.35 | 0.46 |
| 6 | 0.22 | 0.33 | 0.45 |
| 7 | 0.23 | 0.33 | 0.44 |
| 8 | 0.23 | 0.33 | 0.44 |
| 9 | 0.23 | 0.33 | 0.44 |
| 10 | 0.23 | 0.33 | 0.44 |
