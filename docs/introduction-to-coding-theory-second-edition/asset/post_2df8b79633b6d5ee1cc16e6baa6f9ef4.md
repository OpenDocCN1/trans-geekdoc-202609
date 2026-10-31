
cases $d = 30$ and $d = 42$, this yields additive 256-ary codes

$[513, 480_{2}^{1}, 30]_{256}$ and $[513, 467, 42]_{256}$.

The codes proposed in [108], based on computer simulations, are shortened versions of these codes: $[511, 478_{2}^{1}, 30]_{256}$, $[511, 465, 42]_{256}$.

## Convolutional codes

As we mentioned that deep space communication systems use a concatenation scheme one of whose components is a convolutional code, it should at least be explained what the construction idea of these codes is.

We concentrate on a special case, binary convolutional codes of rate $1/2$. Imagine the incoming bitstream as a (potentially) infinite sequence $(x_0, x_1, x_2, \dots)$. The encoding of each bit depends also on the $m-1$ preceding bits. That is why we define $x = (0, \dots, 0, x_0, x_1, x_2, \dots)$, where $x_{-1}=\cdots = x_{-(m-1)}=0$.

Fix two elements $g_1, g_2 \in \mathbb{F}_2^m$. When bit $x_i$ comes in, we consider a window $W_i$ of $m$ consecutive bits: $W_i = (x_{i-m+1}, \dots, x_i) \in \mathbb{F}_2^m$. The output generated at that time is the pair $(W_i \cdot g_1, W_i \cdot g_2) \in \mathbb{F}_2^2$. As $i$ increases, the window shifts to the right (or, if you prefer, the window is fixed, the bitstream moves one to the left). The encoded sequence is

$y = (W_0 \cdot g_1, W_0 \cdot g_2, W_1 \cdot g_1, W_1 \cdot g_2, W_2 \cdot g_1, W_2 \cdot g_2, \dots)$.

As each source bit $x_i$ produces two bits of the encoded message, one speaks of rate $1/2$. Using $k$ instead of 2 tuples $g_i$ would result in a rate $1/k$ code.

Take the example where $m = 4$ and $g_1 = 1101$, $g_2 = 1011$. Let the incoming bitstream, including the prefix of $m-1 = 3$ zeroes, be

$x = 000|010011000101 \dots$

The first window is $W_0 = 0000$ and produces $00$ of course. The second window is $0001$ and produces $(W_1 \cdot g_1, W_1 \cdot g_2) = 11$. The encoded message is

$y = 00|11|01|10|00|10|11|01|11|11|01|01 \dots$

Observe that each window ends with the $(m-1)$-tuple that the next window starts with. We can base ourselves on the $(m-1)$-tuples (the states) and set up the state diagram, where an arrow points from state $S_1$ to $S_2$ if the $(m-2)$-tuple ending $S_1$ is the one starting $S_2$. It follows that two arrows lead out of each state and two lead into each state. If I know the state $S$ and the next bit $x_i$, this gives me window $W_i = (S|x_i)$. The next state is

![](img/2fa0633d317c0872f05788febf717c11_379_0.png)

## FIGURE 18.1: A state diagram

the $(m-1)$-tuple ending $W_i$. The state diagram is completed by writing the output $(W\cdot g_1, W\cdot g_2)$ over each arrow; see Figure 18.1. Movement begins in state 000 (courtesy of the prefix). Given a state, the next input bit decides which of the two arrows emanating from the state to follow. This generates two output bits (the ones written alongside the arrow) and leads to the next state.

As applied mathematicians have a predilection for polynomials and power series, it is customary to represent the incoming bitstream as a power series: instead of $0,0,0,x_0,x_1,x_2\dots$ one writes $m(X)=x_0X^3+x_1X^4+x_2X^5+\dots$. The convolutional code is then described as a transformation on formal power series, thus giving some superficial dignity to the subject. The $m$-tuples $g_1,g_2,\dots$ are represented by polynomials, in our case $g_1(X)=X^3+X+1$, $g_2(X)=X^3+X^2+1$. The calculation of the dot products with $g_i$ corresponds to the computation of the power series $g_i(X)m(X)$ and these computations can be done efficiently using shift registers.

Convolutional codes are linear: the sum of two input bitstreams is mapped to the sum of the output bitstreams. The minimum distance therefore equals the minimum weight, which is the smallest weight of a possible output stream different from the all-0 sequence. In our example the minimum distance is $d=6$. In fact, we have to leave state 000 along an edge generating 11 and to come back via state 100, generating 11 again. There is no path along arrows from state 001 to state 100 generating an output of weight less than 2. Such a path of weight 2 is obtained passing through state 010. As $d=6$, the usual argument shows that, in general, we can correct up to two errors using this convolutional code. We will not consider the question of decoding algorithms here.

## The Bose-Bush construction

Let $a \ge b$ and fix a surjective $\mathbb{F}_q$-linear mapping $\Phi : \mathbb{F}_q^{a} \longrightarrow \mathbb{F}_q^{b}$, where of course $a \ge b$. We used this setting in Section 16.7 and constructed a $q^{b}$-ary code $\mathcal{C}_q(a,b)$ of length $q^{a}$, with $q^{a+b}$ codewords, which has strength 2 and minimum distance $q^{a} - q^{b}$.

Recall the construction (see Theorem 16.29): the coordinates are parametrized by the elements $x \in \mathbb{F}_q^{a}$, the codewords by pairs $(u, v)$, where $u \in \mathbb{F}_q^{a}$, $v \in \mathbb{F}_q^{b}$, and the entry of codeword $c(u, v)$ in coordinate $x$ is $c(u, v)_x = \Phi(u x) + v$.

Clearly $\mathcal{C}_q(a, b)$ is $q$-linear. In the terminology of the present chapter we see $\mathcal{C}_q(a, b)$ as a $q$-linear $q^{b}$-ary code of dimension $(a + b)/b = 1 + a/b$. As it has strength 2, its dual is a $q$-linear $[q^{a}, q^{a} - (1 + a/b), 3]_{q^{b}}$ code.

Moreover, we can write $\mathcal{C}_q(a, b)$ as a direct sum:

$\mathcal{C}_q(a, b) = \mathcal{D}_q(a, b) \oplus \mathcal{R}_q(a, b)$

where $\mathcal{D}_q(a, b)$ has as codewords the $c(u, 0)$ and the codewords of $\mathcal{R}_q(a, b)$ are the constant words $c(0, v)$. Both $\mathcal{R}_q(a, b)$ (which we call the repetition code) and $\mathcal{D}_q(a, b)$ are $q$ linear, the first of dimension 1, the second of dimension $a/b \ge 1$. The repetition code clearly has strength 1.

### 18.3 Theorem.
The code $\mathcal{C}_q(a, b)$ (recall $a \ge b$) of Theorem 16.29 is a $q$-linear $q^{b}$-ary code of dimension $(a+b)/b \ge 2$, strength 2 and minimum distance $q^{a} - q^{a-b}$. It is the direct sum of the repetition code $\mathcal{R}_q(a, b)$ (a $q$-linear $[q^{a}, 1]_{q^{b}}$-code of constant weight $q^{a} - q^{a-b}$ and strength 1) and the $q$-linear $q^{b}$-ary code $\mathcal{D}_q(a, b)$.

Consider the construction problem of strength 2 orthogonal arrays. If we restrict to linear codes, the situation is familiar. A linear code $[n, r]_q$ of strength 2 exists if $n \le (q^{r} - 1)/(q - 1)$. This observation led us to the Hamming and Simplex codes (see Section 3.4). What happens if we generalize from linear codes to additive codes? The question is: given $r$, a rational number such that $mr$ is integer, determine the maximal length $n$ of a $q$-linear $q^{m}$-ary code of dimension $r$ and strength 2. Using linear $q^{m}$-ary codes, we reach length $(q^{mr} - 1)/(q^{m} - 1)$ if $r$ should be an integer. The following construction shows that our codes $\mathcal{C}_q(a, b)$ and their subcodes $\mathcal{R}_q(a, b)$, the repetition codes, can be used to obtain additive codes of strength 2 with larger length.

### 18.4 Proposition.
Assume the following $q^{m}$-ary $q$ linear codes exist:
- An $[n, K]$ code $\mathcal{C}$ of strength 2 containing an $[n, k]$ subcode $\mathcal{R}$ of strength 1, and
- a code $[l, K - k]$ of strength 2 (the auxiliary code).

Then we can construct such a code $[n + l, K]$ of strength 2.

### PROOF
It may be easiest to work with $\mathbb{F}_q$ generator matrices. Choose such a generator matrix (with $Km$ rows) for $\mathcal{C}$ such that the first $km$ rows form a generator matrix for $\mathcal{R}$. Lengthen this generator matrix by a generator matrix of the auxiliary code in the last $m(K - k)$ rows, and by a $0$ matrix in the first rows. The result is a generator matrix of a code with the right dimension, clearly of strength $2$.

The generator matrix of the code resulting from Proposition 18.4 has the form $G = \begin{pmatrix} A & 0 \\ C & D \end{pmatrix}$, where the left part generates $\mathcal{C}$, $A$ generates $\mathcal{R}$ and $D$ generates the strength $2$ auxiliary code. Should the auxiliary code possess a strength $1$ subcode again, it will, together with $\mathcal{R}$, generate a strength $1$ subcode of the resulting code. It is then possible to apply Proposition 18.4 again.

Start with code $\mathcal{C}_q(a,b)$. As it contains a $b$ dimensional strength $1$ subcode ($\mathbb{F}_q$ dimensions), we can apply Proposition 18.4 with $\mathcal{C}_q(a - b, b)$ as auxiliary code (provided $a - b \ge b$). The resulting code has a $2b$ dimensional subcode of strength $1$. Apply Proposition 18.4 again, with $\mathcal{C}_q(a - 2b, b)$ as auxiliary code. Proceed inductively in this fashion. The last inductive step occurs when $a - lb \ge b$, but $a - (l + 1)b < b$. Clearly $l = \lfloor a/b \rfloor - 1$. In this last step there is no need to use a strength $2$ code with a strength $1$ subcode. Instead of $\mathcal{C}_q(a - lb, b)$ we use the code of length $q^{a - lb} + 1$ (see Exercise 18.1.4) and obtain as end product a code of length $1 + \sum_{i=0}^{l} q^{a - ib}$.

### 18.5 Theorem.
Let $a \ge b$ be integers, $l = \lfloor a/b \rfloor - 1$. Then there is a $q$-linear $q^b$-ary code of strength $2$, dimension $(a + b)/b$ and length

$n = 1 + \sum_{i=0}^{l} q^{a - ib} = 1 + \left(q^{a + b} - q^{a - lb}\right)/\left(q^{b} - 1\right).$

The OA parameters of Theorem 18.5 are due to Bose and Bush [36], see also Hedayat, Sloane and Stufken [109]. The approach used in our proof of Theorem 18.5 is due to Y. Edel; see [17].

How much better is the Bose-Bush construction of strength $2$ orthogonal arrays than the linear construction? Only when $a$ is a multiple of $b$ is a direct comparison possible. We leave it to the reader to verify that, in these cases, the length in Theorem 18.5 equals the maximum length of linear OA. We gain nothing in these situations. What Theorem 18.5 does: it embeds the linear construction in a vaster family of strength $2$ OA where the index $\lambda$ and the alphabet are powers of the same prime. In OA notation we have

$OA_{\lambda}(2, n, Q), \text{ where } Q = q^{b}, \ \lambda = q^{a - b}$

and $n$ is the length from Theorem 18.5.

Let $b < a < 2b$. Write $a = b + i$, where $i < b$. Then $l = 0$, $n = q^{b + i} + 1$ and $\lambda = q^{i}$. We obtain $OA_{q^{i}}(2, q^{b + i} + 1, q^{b})$, for example, $OA_{2}(2, 9, 4)$, $OA_{4}(2, 17, 8)$.
