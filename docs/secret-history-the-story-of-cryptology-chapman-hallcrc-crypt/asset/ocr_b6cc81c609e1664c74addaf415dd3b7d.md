This was not the best place to publish a mathematical idea, but Levine was still a teenager at the time.

Hill’s description came three years later, but it appeared in *American Mathematical Monthly*, so it isn’t hard to see why the system was named after Hill.³ The *American Mathematical Monthly* paper provided a complete explanation of matrix encryption with examples, whereas Levine’s letter didn’t actually reveal his method, although it can be inferred. And, although Levine used algebra, he wasn’t quite doing the same thing as Hill, at least not publicly.

Levine went on to earn a doctorate in mathematics from Princeton University, serve his country in a cryptologic capacity (in the Army), and author many more papers on cryptology, some of which are described in the pages to follow. Hill, on the other hand, only published two papers dealing directly with cryptology. Hill served in the Navy during World War I, but not in a cryptologic capacity. In later decades, he did do some cryptologic work for the Navy, but it appears to have been unsolicited and not considered valuable.⁴ In any case, the military work of both Levine and Hill was not known to the academic community.

# 6.2 How Matrix Encryption Works

Matrix encryption can most easily be explained by example. Consider Oscar Wilde’s quote “THE BEST WAY TO DEAL WITH TEMPTATION IS TO YIELD TO IT.” We first replace each letter with its numerical equivalent:

| A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 | 25 |

This gives

19 7 4 1 4 18 19 22 0 24 19 14 3 4 0 11 22 8 19 7 19 4 12 15
19 0 19 8 14 13 8 18 19 14 24 8 4 11 3 19 14 8 19.

The key we select in this system is an invertible matrix (modulo 26) such as \(\begin{pmatrix}6 & 11 \\ 3 & 5\end{pmatrix}\). To encipher, we simply multiply this matrix by the numerical version of the plaintext in pieces of length two and reduce the result modulo 26; for example,

\[\begin{pmatrix}6 & 11 \\ 3 & 5\end{pmatrix}\begin{pmatrix}19 \\ 7\end{pmatrix}=\begin{pmatrix}6\cdot19+11\cdot7 \\ 3\cdot19+5\cdot7\end{pmatrix}=\begin{pmatrix}191 \\ 92\end{pmatrix}=\begin{pmatrix}9 \\ 14\end{pmatrix}\pmod{26}\]

³ Hill, Lester S., “Cryptography in an Algebraic Alphabet,” *American Mathematical Monthly*, Vol. 36, No. 6, June–July 1929, pp. 306–312.

⁴ For details, see Christensen, Chris, “Lester Hill Revisited,” *Cryptologia* Vol. 38, No. 4, October 2014, pp. 293–332.