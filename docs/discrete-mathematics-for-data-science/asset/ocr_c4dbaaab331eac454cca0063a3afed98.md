To evaluate the quality of a received signal, we can compare the joint entropy of sender and receiver data to the entropy of the sender's data. In this context the equation for conditional entropy can be expressed as:

```
H(R | S) = H(S, R) – H(R)
```

Given an uncertain received signal, where R is not likely to reflect S, the sets may be independent or there may too much noise in R.

# 22.7 MUTUAL INFORMATION

Mutual information can tell us how much uncertainty is removed from a message when there is prior knowledge of another message. The mutual information of two sets of symbols is a gauge of how much dependence exists between the sets.

Mutual information I can be expressed in terms of the prior entropy equations.

```
I(A, B) = H(A) – H(A | B)
= H(B) – H(B | A)
= H(A) – H(A, B) – H(B)
= H(A) + H(B) – H(A, B)
```

# 22.8 NOISE, ERROR DETECTION & CORRECTION

Noise amounts to entropy and uncertainty. Therefore, it is to be minimized.

Simplistic approaches to dealing with noise include sending redundant symbols and using a parity bit.

A message can be sent twice and the two instances of the received message can be compared. The information that these messages have in common provides a degree of validation. If re-transmission corroborates the symbols that were received previously, then mutual information will be equivalent to the joint entropy of the redundant sets.

Recall that for mutual information,

```
I(A, B) = H(B) – H(A | B)
```