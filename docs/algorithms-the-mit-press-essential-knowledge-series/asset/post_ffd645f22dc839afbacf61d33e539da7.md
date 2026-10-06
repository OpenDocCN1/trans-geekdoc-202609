
contribution remained a secret for decades). In a tragic turn of events, Turing died by suicide. He had been arrested and convicted in 1952 for homosexuality, which was criminal in the United Kingdom at the time, and compelled to get hormonal treatment. An official pardon was issued in 2013. His appearance on the new note is a form of rehabilitation that would have been unthinkable a few decades back.²

Throughout this book we have been describing algorithms as consisting of simple steps, elementary enough that they can be carried out using a pen and paper. Given that we implement algorithms in computer programs, the question of what is really is an algorithm will help us understand what can really be computed. This requires us to dig deeper into the nature of these simple steps. After all, what a primary school student can do with a pen and paper is different from what a college graduate can do. Is it possible to define precisely what kind of algorithm could be made of? Turing offered an answer even before digital computers were built. He proposed a model machine in 1936 in order to answer the question of what a computer, any computer, can do. A Turing machine is a simple contraption. It consists of the following parts:³

- 1. A tape. The tape is divided into squares or cells. Each cell can be blank or contain a symbol from some alphabet. The tape can be infinitely long.

> Is it possible to define precisely what kind of steps an algorithm could be made of? . . . [Turing] proposed a model machine in 1936 in order to answer the question of what a computer, any computer, can do.

- 2. A head that can move left and right along the tape, one position at a time. The head can read the symbol in the cell underneath. We call the symbol in that cell the scanned symbol. The head can erase or overwrite the scanned symbol.

- 3. A finite control, also called a state register. The finite control can be in any of a finite set of states. You can think of it as a dial inscribed with states, and an indicator that can point to any one of them.

- 4. A finite instructions table. Each instruction specifies the next move of the machine. This is what the machine will do, given its current state and the scanned symbol.

You can see a Turing machine in the figure on the next page.⁴

The alphabet of this particular Turing machine consists of 1 and ★. The finite control shows that the machine can be in one of seven states, $q_0, q_1, \dots, q_6$. The instructions table has one row for each possible state, and one column for each possible symbol; we use $B$ to stand in for blank so that we can see. The current state is indicated by the row, and the scanned symbol by the column. Each entry in the instructions table contains a triplet, describing a move, or a dash, meaning that the machine has nothing to do in this row and column combination.

## Finite Instructions Table

| State | 1 | $\star$ | B |
| :--- | :--- | :--- | :--- |
| $q_0$ | | | $(q_1, B, R), (q_5, B, R)$ |
| $q_1$ | | $(q_2, \star, R)$ | $(q_1, 1, R)$ |
| $q_2$ | $(q_0, 1, R)$ | | $(q_3, \star, L), (q_1, B, R)$ |
| $q_3$ | | $(q_4, B, R)$ | $(q_3, 1, L)$ |
| $q_4$ | | $(q_5, B, R)$ | $(q_4, 1, L)$ |
| $q_6$ | | | |

![](img/9d8f96a7d5ef19b95ffbdc3918c1b6f3_260_0.png)

A move of the machine consists of three actions:

- 1. The machine may change or remain in the same state. The new state is the first element of the triplets in the finite instructions table.

- 2. It will write a symbol under the head. The symbol may be the same with the one already there (then the result is that the existing symbol remains in the cell). The symbol to be written is the second element of the triplets.

- 3. The head will shift either to the left (L) or right (R) of the current cell. The shift is the third element of the triplets.

Our example Turing machine executes an algorithm that computes the difference of two numbers $a$ and $b$ when $a > b$; otherwise, it returns zero. This operation is called *monus* or *proper subtraction*, and we write a $a \div b$. We have $4 \div 2 = 2$ and $2 \div 4 = 0$.

Initially, we place the machine’s *input* on the tape. The input is a finite string of symbols from the machine’s alphabet. All other cells of the tape, to the left and right of it, are blank. In this Turing machine, the input is $1111 \star 11$. The input represents the numbers four and two in the *unary numeral system*, separated by $\star$.

This machine starts with its head on the leftmost-input cell. The finite control points at the $q_0$ state. Then the machine starts working and performs its moves. If we follow the machine's operation for the first six moves, we'll see that it goes like this:

- 1. We are at state $q_0$ and the scanned symbol is 1:

The instruction table gives us $(q_1,B,R)$, so the machine will change its state to $q_1$, overwrite 1 with blank, and move right. The tape and head will be:

- 2. For the $q_1$ state and scanned symbol 1, the instruction table gives us $(q_1,1,R)$. The machine will read and write 1, leaving the cell as it is, and will move right, remaining at state $q_1$:

| | 1 | 1 | 1 | ★ | 1 |
| :--- | :--- | :--- | :--- | :--- | :--- |

- 3. The machine does the same as step 2, reading and writing 1, remaining at $q_1$, and moving right:

![](img/9d8f96a7d5ef19b95ffbdc3918c1b6f3_263_0.png)

- 4. Again, the machine will read and write 1, leaving the cell as it is, and will move right:

![](img/9d8f96a7d5ef19b95ffbdc3918c1b6f3_264_0.png)

- 5. The head has moved over ★ and remained at $q_1$:

![](img/9d8f96a7d5ef19b95ffbdc3918c1b6f3_265_0.png)

- 6. The head has moved over 1 to state $q_2$:

![](img/9d8f96a7d5ef19b95ffbdc3918c1b6f3_266_0.png)
