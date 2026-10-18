
![math](images/eq07002.png)
<m:math display="block" overflow="scroll" xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="left"><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>4</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>5</m:mn></m:mtd></m:mtr><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>2</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>4</m:mn></m:mtd></m:mtr><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>3</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>3</m:mn></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="right"><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mn>3</m:mn></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mrow><m:mo>&#45;</m:mo><m:mn>2</m:mn></m:mrow></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced><m:mo>=</m:mo><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="right"><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mn>2</m:mn></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mrow><m:mo>&#45;</m:mo><m:mn>2</m:mn></m:mrow></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mn>3</m:mn></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced></m:mrow></m:math>

![math](images/eq07003.png)
<m:math display="block" overflow="scroll" xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="left"><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>4</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>5</m:mn></m:mtd></m:mtr><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>2</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>4</m:mn></m:mtd></m:mtr><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>3</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>3</m:mn></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="right"><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mrow><m:mo>&#45;</m:mo><m:mn>2</m:mn></m:mrow></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mn>5</m:mn></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced><m:mo>=</m:mo><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="right"><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mrow><m:mn>17</m:mn></m:mrow></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mrow><m:mn>16</m:mn></m:mrow></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mn>9</m:mn></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced></m:mrow></m:math>

Now all you have to do is take the resulting column vectors and use them to rebuild the output matrix using the multiplication of the first column vector as the first column in the new matrix and so on.

![math](images/eq07004.png)
<m:math display="block" overflow="scroll" xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mtext>XB</m:mtext><m:mo>=</m:mo><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="left"><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>4</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>5</m:mn></m:mtd></m:mtr><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>2</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>4</m:mn></m:mtd></m:mtr><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>3</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>3</m:mn></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="right"><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mn>3</m:mn></m:mtd><m:mtd columnalign="right"><m:mrow><m:mo>&#45;</m:mo><m:mn>2</m:mn></m:mrow></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mrow><m:mo>&#45;</m:mo><m:mn>2</m:mn></m:mrow></m:mtd><m:mtd columnalign="right"><m:mn>5</m:mn></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced><m:mo>=</m:mo><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="right"><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mn>2</m:mn></m:mtd><m:mtd columnalign="right"><m:mrow><m:mn>17</m:mn></m:mrow></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mrow><m:mo>&#45;</m:mo><m:mn>2</m:mn></m:mrow></m:mtd><m:mtd columnalign="right"><m:mrow><m:mn>16</m:mn></m:mrow></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mn>3</m:mn></m:mtd><m:mtd columnalign="right"><m:mn>9</m:mn></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced></m:mrow></m:math>

![Remember](images/remember.png)In matrix multiplication, because of matrix shapes, order matters. Consequently, you cannot invert terms, as you would do in a multiplication of scalar numbers. Multiplying 5\*2 or 2\*5 is the same thing, because of the commutative property of scalar multiplication, but XB is not the same as BX because sometimes the multiplication isn't possible (because the shapes of the matrices are incompatible) or, worse, it produces a different result. When you have a series of matrix multiplications, such as ABC, the order of the operations doesn’t matter; whether you go with AB first or BC first, you get the same result because, like scalars, matrix multiplication is associative.

### Glancing at advanced matrix operations

You may encounter two important matrix operations in some algorithm formulations. They are the transpose and inverse of a matrix. *Transposition* occurs when a matrix of shape n x m is transformed into a matrix m x n by exchanging the rows with the columns. Most tests indicate this operation using the superscript T, as in A^T. You see this operation used most often for multiplication, in order to obtain the right dimensions. When working with Python, you use code like this to perform a transposition:

```
A = np.array([[1, 2, 3], [2, 3, 5], [7, 11, 13]]) print(A.transpose())
```

The output shows the transposition:

```
[[ 1 2 7] [ 2 3 11] [ 3 5 13]]
```

You apply *matrix inversion* to matrices of shape m x m, which are square matrices that have the same number of rows and columns. This operation is quite important because it allows the immediate resolution of equations involving matrix multiplication, such as y=bX, where you have to discover the values in the vector b. Because most scalar numbers (exceptions include zero) have a number whose multiplication results in a value of 1, the idea is to find a matrix inverse whose multiplication will result in a special matrix called the identity matrix, whose elements are zero, except the diagonal elements (the elements in positions where the index i is equal to the index j). Finding the inverse of a scalar is quite easy (the scalar number n has an inverse of n^(\-1) that is 1/n). It’s a different story for a matrix. Matrix inversion involves quite a large number of computations, so special math functions perform the calculations in Python. The inverse of matrix A is indicated as A^(\-1). You use the following code to invert a matrix:

```
print(np.linalg.inv(A))
```

The output shows the inverted matrix:

```
[[-3.2 1.4 0.2] [ 1.8 -1.6 0.2] [ 0.2 0.6 -0.2]]
```

![Remember](images/remember.png)Sometimes, finding the inverse of a matrix is impossible. When a matrix cannot be inverted, it is referred to as a *singular matrix* or a *degenerate matrix*. Singular matrices aren’t the norm; they’re quite rare.

### Using vectorization effectively

If performing matrix operations, such as matrix by vector multiplication, seems a bit hard, consider that your computer does all the hard work. All you have to do is determine in a theoretical formulation what happens to the numbers as you put them into matrices, vectors, and constants, and then you sum, subtract, divide, or multiply them.
