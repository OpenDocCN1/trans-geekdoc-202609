As with the addition symbol “+”, the multiplication symbol “×” is merely symbolic (multiplication is not being defined in terms of multiplication).

6 G. Peano, *Arithmetices Principia, Nova Methodo Exposita*. unknown, 1889, pp. 23–29. DOI: [https://github.com/mdnahas/Peano_Book/blob/master/Peano.pdf](https://github.com/mdnahas/Peano_Book/blob/master/Peano.pdf)

Thus, the multiplication of any two natural numbers *a* and *S(b)* can be defined recursively as:

$$a + (a \times b) = a \times S(b)$$

Consider \( a = a \times 1 \). First, having established that \( 1 = S(0) = 1 + 0 \), we therefore we know that:

$$a = a + 0 = a + (a \times 0) = a \times S(0) = a \times 1$$

For \( 3 \times 2 \), since \( 2 = S(1) \), therefore:

$$6 = 3 + 3 = 3 + (3 \times 1) = 3 \times S(1) = 3 \times 2$$

# 11.4 RECURRENCE RELATION

There is a mathematical equation called a *recurrence relation* that is used to formally describe recursion. A recurrence relation expresses a sequence of elements as a conditional successor function, discussed earlier.

Recall the conditions of a recurrence, by which a succession continues or stops. These conditions were referred to as the *general case* and the *base case*, respectively.