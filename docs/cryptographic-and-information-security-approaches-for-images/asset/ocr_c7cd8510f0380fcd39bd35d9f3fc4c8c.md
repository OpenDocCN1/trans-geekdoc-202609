# Definition 4.46:

For $g : \mathbb{Z}_2^n \to \mathbb{Z}_2$ and $a \in \mathbb{Z}_2^n$, $a \neq 0$, we defined the function by

$$g_a(x) = g(x) \oplus g(x \oplus a), \qquad (4.32)$$

where $g_a$ is called the directional derivative of $g$ in the direction of $a$.

Now we are able to express the SAC in connection with the directional derivative.

# Lemma 4.47:

$[2, \text{Lemma 5.3}]$ A Boolean function $g : \mathbb{Z}_2^n \to \mathbb{Z}_2$ satisfies SAC if and only if the function $g(x) \oplus g(x \oplus a)$ is balanced for every $a \in \mathbb{Z}_2^n$ with $a \neq 0$, Hamming weight 1.

# Definition 4.48:

The autocorrelation $(AC)$ function of a Boolean function in $n$ variables is defined as

$$r_g(a) = \sum_{i=0}^{2^{n}-1} g(x_i) g(x_i \oplus a), \qquad (4.33)$$

for all every $a \in \mathbb{Z}_2^n$.

# Example 4.49:

Let us study the Boolean function $g(x)= x_3 \oplus x_2 x_1$; then the truth table for $g$ is shown in Table 4.4. The AC coefficient for $a = 001$ are given as follows:

$r_g(000)= \sum_{i=0}^{2^{3}-1} g(x_i) \otimes g(x_i \oplus 000), = g(000)g(000 \oplus 000)+ g(001)g(001 \oplus 000)+...+ g(111)g(111 \oplus 000), = 0.0+0.0+...+1.1, =5.$

# Lemma 4.50:

$[2, \text{Lemma 5.5}]$ A Boolean function $g$ in $n$ variables is SAC if and only if the autocorrelation function $r_g(a)$ is equal to $2^{n-1}$ for all $a \in \mathbb{Z}_2^n$ with the Hamming weight 1.

# Example 4.51:

Now take an example for SAC with $a = 01$, (Table 4.5), The given function $g$ doesn’t satisfy the SAC, since $g(x).g(x \oplus a)$ is not balance.