Consider 8-ary Reed-Solomon codes. We need the field $\mathbb{F}_8$. Let us just follow the general construction procedure: as $8 = 2^3$, we need an irreducible polynomial $f(X)$ of degree 3 with coefficients in $\mathbb{F}_2$. The constant term cannot vanish (the polynomial would be divisible by $X$ otherwise). This leaves us with four candidates:

$X^3 + 1,\ X^3 + X^2 + 1,\ X^3 + X + 1\ \text{and}\ X^3 + X^2 + X + 1.$

The first and the last of these candidates are reducible, as they satisfy $f(1)=0$. These polynomials are therefore divisible by $X - 1 = X + 1$. The two remaining candidates are irreducible. We choose

$f(X) = X^3 + X^2 + 1.$

Denote by $\epsilon$ the image of $X$ in $\mathbb{F}_8$. The elements of $\mathbb{F}_8$ are the polynomials of degree $\le 2$ in $\epsilon$

$\mathbb{F}_8 = \{0,1,\epsilon,\epsilon+1,\epsilon^2,\epsilon^2+1,\epsilon^2+\epsilon,\epsilon^2+\epsilon+1\}$

This defines the addition. The multiplication is determined by the basic equation (equivalent to the choice of $f(X)$)

$\epsilon^3 = \epsilon^2 + 1.$

We can multiply any two elements of $\mathbb{F}_8$. The basic equation allows us to get rid of all exponents $>2$. Consider the powers of $\epsilon$

$\epsilon^3 = \epsilon^2 + 1,\ \epsilon^4 = \epsilon^3 + \epsilon = \epsilon^2 + \epsilon + 1.$

In the same manner we can determine all powers of $\epsilon$ $\epsilon^5 = \epsilon^3 + \epsilon^2 + \epsilon = \epsilon + 1,\ \epsilon^6 = \epsilon^2 + \epsilon\ \text{and}\ \epsilon^7 = 1.$

We see once again that knowledge of the irreducible polynomial is equivalent to knowledge of the field. To write down generator matrices of the 8-ary Reed-Solomon codes, let $0,1,\epsilon,\dots,\epsilon^6$ parametrize the columns, in this order. Rows are parametrized by the monomials $1,X,X^2,\dots$. The following generator matrix for $\mathcal{RS}(4,8)$ is obtained:

$G = \begin{pmatrix}1&1&1&1&1&1&1&1\\0&1&\epsilon&\epsilon^2&\epsilon^3&\epsilon^4&\epsilon^5&\epsilon^6\\0&1&\epsilon^2&\epsilon^4&\epsilon^6&\epsilon&\epsilon^3&\epsilon^5\\0&1&\epsilon^3&\epsilon^6&\epsilon^2&\epsilon^5&\epsilon&\epsilon^4\end{pmatrix}.$

We know that $\mathcal{RS}(4,8)$ is a self-dual code $[8,4,5]_8$. Also, the Reed-Solomon codes of different dimensions are contained in each other. The first three rows of $G$ generate $\mathcal{RS}(3,8)$, the first two rows generate $\mathcal{RS}(2,8)$ and $\mathcal{RS}(1,8)$ is the repetition code.