We apply Gaussian elimination to the augmented matrix

$$egin{bmatrix}1&1&-1&-1&|&1\2&5&-7&-5&|&-2\2&-1&1&3&|&4\5&2&-4&2&|&6\end{bmatrix}\xrightarrow{-2R_1}egin{bmatrix}1&1&-1&-1&|&1\0&3&-5&-3&|&-4\0&-3&3&5&|&2\0&-3&1&7&|&1\end{bmatrix}\xrightarrow{-	frac13R_2}egin{bmatrix}1&0&	frac23&0&|&	frac73\0&1&-	frac53&-1&|&-	frac43\0&0&-2&2&|&-2\0&0&-4&4&|&-3\end{bmatrix}\xrightarrow{-2R_3}egin{bmatrix}1&0&	frac23&0&|&	frac73\0&1&-	frac53&-1&|&-	frac43\0&0&-2&2&|&-2\0&0&0&0&|&1\end{bmatrix}$$

The last row of the final linear system shows that the equation system has no solution and thus $S = \emptyset$.

b.

$$A = \begin{bmatrix}1&-1&0&0&1\\1&1&0&-3&0\\2&-1&0&1&-1\\-1&2&0&-2&-1\end{bmatrix},\quad b = \begin{bmatrix}3\\6\\5\\-1\end{bmatrix}$$

We start again by writing down the augmented matrix and apply Gaussian elimination to obtain the reduced row echelon form:

$$egin{bmatrix}1&-1&0&0&1&|&3\\1&1&0&-3&0&|&6\\2&-1&0&1&-1&|&5\\-1&2&0&-2&-1&|&-1\end{bmatrix}\xrightarrow{}\begin{bmatrix}1&-1&0&0&1&|&3\\0&2&0&-3&-1&|&3\\0&1&0&1&-3&|&-1\\0&1&0&-2&0&|&2\end{bmatrix}\xrightarrow{}\begin{bmatrix}1&0&0&1&-2&|&2\\0&1&0&1&-3&|&-1\\0&0&0&-5&5&|&5\\0&0&0&-3&3&|&3\end{bmatrix}\xrightarrow{}\begin{bmatrix}1&0&0&1&-2&|&2\\0&1&0&1&-3&|&-1\\0&0&0&1&-1&|&-1\\0&0&0&0&0&|&0\end{bmatrix}\xrightarrow{}\begin{bmatrix}1&0&0&0&-1&|&3\\0&1&0&0&-2&|&0\\0&0&0&1&-1&|&-1\end{bmatrix}$$

From the reduced row echelon form we apply the “Minus-1 Trick” in order to get the following system: