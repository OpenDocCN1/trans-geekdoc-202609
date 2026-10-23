![](bbox=[0.25, 0.14, 0.8, 0.45])

Figure 6.4: The marginal entropy, joint entropy, conditional entropy and mutual information represented as information diagrams. Used with kind permission of Katie Everett.

# 6.3.3 Example

As an example, let us reconsider the example concerning prime and even numbers from Sec. 6.1.3. Recall that 𝕀(X) = 𝕀(Y) = 1. The conditional distribution p(Y|X) is given by normalizing each row:

| | Y=0 | Y=1 |
|---|---|---|
| X=0 | 1/4 | 3/4 |
| X=1 | 3/4 | 1/4 |

Hence the conditional entropy is

𝕀(Y|X) = -[ 1/8 log₂ 1/4 + 3/8 log₂ 3/4 + 3/8 log₂ 3/4 + 1/8 log₂ 1/4 ] = 0.81 bits (6.49)

and the mutual information is

𝕀(X;Y) = 𝕀(Y) - 𝕀(Y|X) = (1 - 0.81) bits = 0.19 bits (6.50)

You can easily verify that

𝕀(X,Y) = 𝕀(X|Y) + 𝕀(X;Y) + 𝕀(Y|X) (6.51)
= (0.81 + 0.19 + 0.81) bits = 1.81 bits (6.52)