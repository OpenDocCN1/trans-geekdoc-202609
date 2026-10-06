A move of the machine consists of three actions:

+   1. The machine may change or remain in the same state. The new state is the first element of the triplets in the finite instructions table.

+   2. It will write a symbol under the head. The symbol may be the same with the one already there (then the result is that the existing symbol remains in the cell). The symbol to be written is the second element of the triplets.

+   3. The head will shift either to the left (L) or right (R) of the current cell. The shift is the third element of the triplets.

Our example Turing machine executes an algorithm that computes the difference of two numbers $a$ and $b$ when $a > b$; otherwise, it returns zero. This operation is called *monus* or *proper subtraction*, and we write a $a \div b$. We have $4 \div 2 = 2$ and $2 \div 4 = 0$.

Initially, we place the machine’s *input* on the tape. The input is a finite string of symbols from the machine’s alphabet. All other cells of the tape, to the left and right of it, are blank. In this Turing machine, the input is $1111 \star 11$. The input represents the numbers four and two in the *unary numeral system*, separated by $\star$.

This machine starts with its head on the leftmost-input cell. The finite control points at the $q_0$ state. Then the