bagels and croissants, we have a matrix with the prices and\profits per sale:

```
$\begin{bmatrix} 2.00 & 1.50 \ 0.20 & 0.10 \end{bmatrix}$
```

To find the total sales per shop and total profit per
shop, we will create a matrix in which the entries in the
ith row and jth column will be the sum of products of the
th row of the prices and profits matrix with the jth row
of the sales matrices. This is the definition of the product of
two matrices:

```
$\begin{bmatrix} 2.00 & 1.50 \ 0.10 & 0.20 \end{bmatrix} \times \begin{bmatrix} 10 & 15 \ 20 & 15 \end{bmatrix} = \begin{bmatrix} 2.00 \times 10 + 1.50 \times 20 & 2.00 \times 15 + 1.50 \times 10 \ 0.10 \times 10 + 0.20 \times 20 & 0.10 \times 15 + 0.20 \times 15 \end{bmatrix} = \begin{bmatrix} 50 & 45 \ 5 & 3.5 \end{bmatrix}$
```

Returning to pagerank, in each round the calculation
of the pagerank vector is really the product of the value
of the pagerank vector in the previous round with the hy-
perlink matrix. As we go through the rounds, we get suc-
cessive estimates of the pageranks—that is, successive
estimates of the pagerank vector that is made up of them.