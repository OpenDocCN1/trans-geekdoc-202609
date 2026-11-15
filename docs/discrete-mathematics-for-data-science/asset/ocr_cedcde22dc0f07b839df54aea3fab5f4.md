where $P_0$ is the probability that a symbol will be received. This can alternatively be expressed as:

```
$I = \log_2(1/P_0)$
```

⁴This is different than thermodynamic entropy. ≅

By using logarithms in base 2, the system readily corresponds with binary digits and their strings thereof. However, any base can be used. For example:

```
$I_a = \log_a(1/P_0) / \log_a 2$
```

where $a$ is an arbitrary base and $I_a$ is the Shannon Information in base $a$.

Given 100% certainty that a message is received, Shannon Information is computed as:

```
$I = -\log_2 1 = 0$
```

Therefore, there are 0 bits of entropy, meaning that a message gets received with 100% certainty.

Consider a scenario of one of two possible messages being received with equal probability, such as from flipping a coin for heads or tails. Either message has a 0.5 probability of receipt. With only two possible outcomes for a message, a single bit represents the entropy. This can be verified by computing Shannon Information as:

```
$I = -\log_2 0.5 = \log_2(1/0.5) = \log_2 2 = 1$
```

# 22.3 MESSAGES OF MULTIPLE SYMBOLS

Consider a scenario where any one of ten equally probable messages may be received. Shannon Information would then be computed as:

```
$I = -\log_2(1/10) = 3.3$
```

That is 3.3 bits of Shannon Information.

Similarly, if it is known that the symbol ‘B’ occurs 8 times in 64 symbols, then the number of bits required to represent ‘B’ is: