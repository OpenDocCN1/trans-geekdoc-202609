# 20.8 Other Public-Key Algorithms 501

was first proposed in 1985, broken in 1986 [774], and then strengthened in the same year [286]. In addition to these attacks, there are general attacks for decomposing polynomials over finite fields [605]. Any algorithm that gets its security from the composition of polynomials over a finite field should be looked upon with skepticism, if not outright suspicion.

The Yagisawa algorithm combines exponentiation mod p with arithmetic mod q = 1 [263]; it was broken in [256]. Another public-key algorithm, Tsujii-Kurosawa-Itoh-Fujimoto-Matsumoto [1548] is secure [948]. A third system, Luccio-Mazzone [993], is insecure [717]. A signature scheme based on birational permutations [1425] was broken the day after it was presented [381]. Tatsuti Okamoto has several schemes: one is as secure as the Discrete Logarithm Problem, and another is as secure as the Discrete Logarithm Problem and the Factoring Problem [1206]. Similar schemes are in [709].

Gustav Simmons introduced J-algebras as a basis for public-key algorithms [145,145]. After this was abandoned efficient methods for factoring polynomials were invented [1951]. Special polynomial semigroups have also been studied in [1619,992], but so far nothing has come of it. Harald Niederreiter proposed a public-key algorithm based on shift-register sequences [1166]. Another is based on Lyndon words [146] and on propositional calculus [817]. And a recent public-key algorithm gets its security from the matrix cover problem [82]. Tatsuti Okamoto and Keizo Ohara compare a number of digital signature schemes in [1212].

Prospects for creating new and different public-key cryptography algorithms seem dim. In 1988 Whitehead Diffie noted that most public-key algorithms are based on three hard problems [492,494]:

+   1. Knapsack: Given a set of unique numbers

According to [492,494], the Discrete Logarithm Problem was suggested by J. Gill, the Factoring Problem by Knuth, and the knapsack problem by Diffie. This narrowness in the mathematical foundations of public-key cryptography is worrisome. A breakthrough in either the problem of factoring or of calculating discrete logarithms could render whole classes of public-key algorithms insecure. Diffie points out [492,494] that this risk is mitigated by two factors:

1. The operations on exponentiation, and on factoring—are all fundamental arithmetic phenomen-