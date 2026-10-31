Recall that entry $i$ in the check matrix stands for $\epsilon^i$. Let the received vector be

$y = (2,0,1,0,1,1,0,1,2,0,2,1,0,0,2,2,0,2,1,2)$.

The dot products of $y$ with the rows of our check matrix yield

$S_1 = \epsilon^{20},\ S_2 = \epsilon,\ S_4 = \epsilon^{33},\ S_5 = 0,\ S_{10} = 1.$

The remaining syndromes are obtained from the rule $S_{3i}=S_i^3$, where the subscripts are mod 20. The syndrome polynomial is

$s(z)=z^9+\epsilon^{20}z^8+\epsilon^{11}z^7-\epsilon^{20}z^6+\epsilon^3z^5+\epsilon^{33}z^3-\epsilon^{20}z^2+\epsilon z+\epsilon^{20}$.

The next step is the application of the complete Euclidean algorithm to $a=z^{10}$ and $b=s(z)$. This involves a series of long divisions of polynomials. We use the algorithm of Section 13.3. As $deg(v_k(z))=k$ equals the number of errors, the algorithm must terminate when $k=5$ or earlier.

| k | Q | R | U | V |
|---|---|---|---|---|
| -1 |  | $z^{10}$ | 1 | 0 |
| 0 |  | $z^9+\epsilon^{20}z^8+\epsilon^{11}z^7-\epsilon^{20}z^6+\epsilon^3z^5+\epsilon^{33}z^3-\epsilon^{20}z^2+\epsilon z+\epsilon^{20}$ | 0 | 1 |
| 1 | $z-\epsilon^{20}$ | $-\epsilon^6z^8+\epsilon^{26}z^7+\epsilon^{39}z^6+\epsilon^{23}z^5-\epsilon^{33}z^4+\epsilon^{38}z^3+\epsilon^{13}z^2-\epsilon^{33}z-1$ | 1 | $-z+\epsilon^{20}$ |
| 2 | $\epsilon^{34}z+\epsilon^{14}$ | $\epsilon^{34}z^7-\epsilon^{12}z^6+\epsilon^{11}z^5+\epsilon^{30}z^4-\epsilon^{33}z^3-\epsilon^5z^2+\epsilon^{10}z+\epsilon^6$ | $-\epsilon^{34}z-\epsilon^{14}$ | $\epsilon^{34}z^2-\epsilon^{14}z-\epsilon^{26}$ |
| 3 | $\epsilon^{12}z+\epsilon^{14}$ | $\epsilon^6z^6-\epsilon^{17}z^5-\epsilon^{10}z^4+\epsilon^{19}z^3+\epsilon^7z^2-\epsilon^{35}z-\epsilon^{30}-\epsilon^{34}z^3-z^2$ | $-\epsilon^6z^2-\epsilon z-\epsilon^{31}$ | $\epsilon^6z^3-\epsilon^{24}z^2+\epsilon^{33}z-\epsilon^{10}$ |
| 4 | $\epsilon^{28}z-\epsilon^{22}$ | $-z-\epsilon^{38}$ | $\epsilon^{34}z^3+\epsilon z^2-\epsilon^9z+\epsilon^{26}$ | $-\epsilon^{34}z^4+\epsilon^5z^3-\epsilon^{14}z^2-\epsilon^{28}z-\epsilon^{18}$ |

The algorithm ends at $k=4$, so four errors occurred. We have $v_4(z)=\lambda\cdot l(z)$, where $\lambda=v_4(0)=-\epsilon^{18}$. The roots of $v_4(z)$ are $1,-\epsilon^4,-\epsilon^8,-\epsilon^{12}$. The reciprocals of these roots are $1=\alpha^0,\epsilon^{36}=\alpha^9,\epsilon^{32}=\alpha^8$ and $\epsilon^{28}=\alpha^7$. We conclude that the errors occurred in coordinates $0,7,8,9$; in other words $M=\{0,7,8,9\}$. In order to determine these errors, we use $r_4(z)=\lambda\cdot w(z)$, where $w(z)$ is the error evaluator. Let $\beta\in M$. It follows from the definition of $w(z)$ that $w(1/\beta)=e_\beta\beta^l\prod_{\gamma\in M,\gamma\neq\beta}(1-\gamma/\beta)$. The only unknown in this expression is $e_\beta$. Let us work out the case $\beta=1$. We have $r_4(1)=-\epsilon^{34}-1-1-\epsilon^{38}=-\epsilon^{25}$. As $\prod_{\gamma\in M,\gamma\neq1}(1-\gamma)=-\epsilon^7$, we obtain

$-\epsilon^{25}=-\epsilon^{18}e_0\epsilon^7$.