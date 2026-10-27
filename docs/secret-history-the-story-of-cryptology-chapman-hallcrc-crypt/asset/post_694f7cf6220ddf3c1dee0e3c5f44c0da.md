
The details of how to test if a matrix is invertible and, if so, calculate its inverse follow below, so that you can create your own keys for matrix encryption. A natural starting point is the following definition.

The **determinant** of a 2 × 2 matrix $M = \begin{pmatrix} a & b \\ c & d \end{pmatrix}$ is given by $ad - bc$. It is often denoted by $\det(M)$.

The determinant offers a quick test to determine if the matrix is invertible.

### Theorem

A matrix M is invertible if and only if its determinant is invertible.

If the entries of the matrix are real numbers, then the matrix is invertible if and only if its determinant is not zero. This is because every nonzero real number is invertible. However, for matrix encryption the entries of the matrix are not real numbers. They are integers modulo $n$. In the Example I provided above, $n = 26$. That means we are only allowed to use the numbers 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, and 25. Which of these numbers are invertible?

### Theorem

A number $a$ is invertible modulo $n$ if and only if $\gcd(a, n) = 1$.

That is, a number $a$ is invertible modulo $n$ if and only if the greatest common divisor of $a$ and $n$ is 1. Another way of saying $\gcd(a, n) = 1$ is “$a$ and $n$ are relatively prime.” A mod 26 multiplication table was given in Section 1.16. You can use it to confirm that in the case of $n = 26$, the invertible values are 1, 3, 5, 7, 9, 11, 15, 17, 19, 21, 23, and 25. This is simply all of the odd values with the exception of 13. You can quickly find the inverse of each of these numbers in the table. Simply look for the number you have to multiply the given number by to get 1.

### Example

If $M = \begin{pmatrix} 6 & 11 \\ 3 & 5 \end{pmatrix}$, then $\det(M) = 6\cdot5 - 11\cdot3 = 30 - 33 = -3 = 23 \pmod{26}$.

Because 23 is invertible (mod 26), the matrix M is invertible.

### Theorem

If $M = \begin{pmatrix} a & b \\ c & d \end{pmatrix}$ is an invertible matrix, then $M^{-1} = (\det(M))^{-1} \begin{pmatrix} d & -b \\ -c & a \end{pmatrix}$.

You can see that the formula won’t work if the determinant of M is not invertible, because the formula begins with the inverse of the determinant. Applying this formula to the matrix used in the encryption example at the beginning of this section, we have

$M^{-1} = (23)^{-1} \begin{pmatrix} 5 & -11 \\ -3 & 6 \end{pmatrix} = 17 \begin{pmatrix} 5 & 15 \\ 23 & 6 \end{pmatrix} = \begin{pmatrix} 17\cdot5 & 17\cdot15 \\ 17\cdot23 & 17\cdot6 \end{pmatrix} = \begin{pmatrix} 7 & 21 \\ 1 & 24 \end{pmatrix}$.

So, if we use $M = \begin{pmatrix} 6 & 11 \\ 3 & 5 \end{pmatrix}$ to encipher, then we can use $M^{-1} = \begin{pmatrix} 7 & 21 \\ 1 & 24 \end{pmatrix}$ to decipher, as was claimed.

There are other methods that can be used to calculate the inverse of a matrix. You can find them detailed in linear algebra textbooks. Some of these generalize easily to larger matrices, which is great because square (invertible) matrices of any dimension may be used for encryption. A 5 × 5 matrix would allow us to encipher characters in groups of five, and a particular word could be enciphered in as many as five different ways depending on its position in the message. There are other advantages to using larger matrices, such as larger keyspaces.

## 6.3 Levine’s Attacks

A brute-force attack on 2 × 2 matrix encryption will quickly yield the plaintext, as there are only 157,248 possible keys. Indeed, Levine pursued this approach back in 1961 for the special case in which an involutory (self-inverse) matrix was used.⁵ There are 736 of these especially convenient keys and even primitive 1961 computer technology was up to the task, although a human was needed to look at the results and determine which provided a meaningful message.⁶

The keyspace grows rapidly with the size of the matrix. For 3 × 3 matrix encryption there are 1,634,038,189,056 possible keys and for the 4 × 4 case we have 12,303,585,972,327,392,870,400 invertible matrices (modulo 26) to consider. The references at the end of this chapter include a paper showing how these values are calculated. When larger matrices are used, cryptanalysts need an attack significantly better than brute-force, if they hope to recover the message.

If we are able to guess the beginning of a message (or any other part), the combination of known plaintext and ciphertext makes it easy to recover the matrix and break the rest of the cipher.⁷ This is referred to as a known-plaintext attack. However, we often have a word or phrase that we believe appears in the message, although we don’t know where. Such suspected plaintexts are called cribs.

In another 1961 paper, Levine demonstrated how cribs can be applied to break matrix encryption.⁸ The mathematics needed to understand this attack consists of two very basic facts:

- 1. The product of two integers is odd if and only if both of the integers are odd.
- 2. The sum of two integers is odd if and only if exactly one of the integers is odd.

To see how these facts become useful, suppose we are enciphering with a matrix of the form $\begin{pmatrix} even & odd \\ odd & even \end{pmatrix}$. There are four distinct possibilities for the form of the plaintext pair that is enciphered at each step, namely
$\left(\begin{array}{c} even \\ even \end{array}\right), \left(\begin{array}{c} even \\ odd \end{array}\right), \left(\begin{array}{c} odd \\ even \end{array}\right), \left(\begin{array}{c} odd \\ odd \end{array}\right)$

Labeling these four forms as 0, 1, 2, and 3, we see (by applying the facts above in the context of matrix multiplication) that the enciphering matrix sends form 0 to another pair of letters having form 0. In the case of form 1, enciphering yields a pair of letters having form 2. A nice symmetry exists, as a plaintext pair of form 2 will be sent to a ciphertext pair of form 1. Finally, a plaintext pair of form 3 will be sent to a ciphertext pair of form 3.

These pairings can be tersely expressed as

0 ↔ 0, 1 ↔ 2, 3 ↔ 3

If the enciphering matrix has a form other than ( even odd / odd even ), these pairings may differ, but the pairings are always constant for a given matrix and we always have 0 ↔ 0. If the matrix is self-inverse, the pairings will be reciprocal, otherwise some of the arrows could be one-way.

Now consider the following ciphertext obtained by enciphering with a 2×2 self-inverse matrix of unknown form:

```
CRSFS HLTWB WCSBG RKBCI PMQEM FOUSC
PESHS GPDVF RTWCX FJDPJ MISHE W
```

If this message was sent from one mathematician to another, we might guess that the word MATHEMATICS appears somewhere in the plaintext. Word spacing has not been preserved in the ciphertext, so we cannot immediately locate the word’s position. However, the word can appear in only two fundamentally different positions with respect to the enciphering matrix. We have either:

- 1. MA TH EM AT IC Sx
- or
- 2. xM AT HE MA TI CS

We disregard the pairs with an x (representing an unknown plaintext letter) in them. The remaining pairs have the forms (0, 3, 0, 1, 0) and (1, 2, 0, 2, 0), respectively. Finding the forms of the ciphertext pairs yields:

```
1 1 1 3 1 0 1 1 1 0 2 0 1 0 0 2 1 0 3 3 3
CR SF SH LT WB WC SB GR KB CI PM QE MF OU SC PE SH SG PD VF RT

0 3 3 3 0 1 0
WC XF JD PJ MI SH EW
```

Suppose MATHEMATICS lined up with the enciphering matrix in the manner of the first possibility listed, (0, 3, 0, 1, 0). Could the message begin with this word? If it did, this would imply the plaintext/ciphertext pairing 0 ↔ 1, while we know 0 ↔ 0 for all matrices. Therefore, if MATHEMATICS appears in the message, it cannot be at the very beginning. Lining up with the first zero in the ciphertext gives:

```
0 3 0 1 0
1 1 1 3 1 0 1 1 1 0 2 0 1 0 0 2 1 0 3 3 3 0 3 3 3 0 1 0
```

This is not possible, because the middle pairing is 0 ↔ 1. Also, if 3 ↔ 1, we must have 1 ↔ 3, but the above alignment has 1 ↔ 1. We now line up the first 0 in our proposed plaintext with the second zero in the ciphertext.
