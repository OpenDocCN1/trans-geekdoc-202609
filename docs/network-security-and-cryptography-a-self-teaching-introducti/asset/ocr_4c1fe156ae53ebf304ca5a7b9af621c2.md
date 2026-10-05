# 8.5.12 Mathematical Basis for Birthday Attack

+   - Consider a Hash Function $H$ producing an $m$-bit hash value, that is, there can be $2^m$ possible different hash values.
- We apply the hash function to a set $X$ of $k$ random messages and produce a set of $k$ hash values.
- We again apply the same hash function to set $Y$ of $k$ random messages and produce another set of $k$ hash values.
- The minimum value of $k$ to have at least one pair $(x \in X, y \in Y)$ satisfying $H(x)=H(y)$ with a probability greater than $1/2$ is given by:

```
$k = 0.83\sqrt{2}^m = 0.83 \times 2^{m/2}$
```

This forms the mathematical basis for the Birthday Attack on Digital Signatures.

# 8.5.13 Birthday Attack

+   - This attack is carried out by an insider (“Eve”) who enjoys the confidence of a valid signer (“A”), but Eve does not have access to $A$'s Private Key.
- If “A” asks Eve to prepare a message $M$ for $A$'s signatures, then Eve can perform the Birthday Attack as follows:

Let the size of the hash value be $m$ bits.

+   1. Eve generates $2^{m/2}$ variants of the valid message $M$, with all these variants conveying the same meaning as $M$. Let us denote the set of these valid messages by $X$.
2. Eve also prepares $2^{m/2}$ variants of a fraudulent message $M$ that Eve wants to convey. Let us denote the set of these fraudulent messages by $Y$.
3. The two sets of messages are processed to determine a pair of messages $(x \in X, y \in Y)$ that produce the same hash value, that is $H(x)=H(y)$. The probability of getting this pair, by the Birthday Paradox, is greater than $1/2$.
4. If there is no success in step (3), then repeat steps (1) to (3) by generating new variants of the valid message $M$ and fraudulent message $M$.