Solving the first of these equations for y yields y = 2 + 3z, and plugging this into the second equation yields z = 2. We now have

x = 5 + 2z - 3y
 y = 2 + 3z
 z = 2.
(77A.3)

Substituting z = 2 into the second equation gives y = 8, and substituting z = 2 and y = 8 into the first equation yields x = -15. Therefore, the solution set is the single point (x, y, z) = (-15, 8, 2).

# Method 2: Cramer's rule

Explicit formulas for small systems

(Reference: Wikipedia)

Consider the linear system

\begin{cases} a_1 x + b_1 y = c_1 \\ a_2 x + b_2 y = c_2, \end{cases} \tag{77A.4}

which in matrix format is

\begin{bmatrix} a_1 & b_1 \\ a_2 & b_2 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} c_1 \\ c_2 \end{bmatrix}. \tag{77A.5}

Assume a1b2 - b1a2 non-zero. Then, x and y can be found with Cramer's rule as

x = \begin{vmatrix} c_1 & b_1 \\ c_2 & b_2 \end{vmatrix} / \begin{vmatrix} a_1 & b_1 \\ a_2 & b_2 \end{vmatrix} = \frac{c_1 b_2 - b_1 c_2}{a_1 b_2 - b_1 a_2} \tag{77A.6}

and

y = \begin{vmatrix} a_1 & c_1 \\ a_2 & c_2 \end{vmatrix} / \begin{vmatrix} a_1 & b_1 \\ a_2 & b_2 \end{vmatrix} = \frac{a_1 c_2 - c_1 a_2}{a_1 b_2 - b_1 a_2}. \tag{77A.7}

The rules for 3 × 3 matrices are similar. Given

\begin{cases} a_1 x + b_1 y + c_1 z = d_1 \\ a_2 x + b_2 y + c_2 z = d_2 \\ a_3 x + b_3 y + c_3 z = d_3, \end{cases}

which in matrix format is

\begin{bmatrix} a_1 & b_1 & c_1 \\ a_2 & b_2 & c_2 \\ a_3 & b_3 & c_3 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} d_1 \\ d_2 \\ d_3 \end{bmatrix}. \tag{77A.8}