Of course, this is exactly what is wrong with this simplistic PRG G defined above. Every output of G has equal first/second halves. But it is rare for uniformly sampled strings to have this property. We can formalize this observation as an attack against the PRG-security of G:

```
x||y := QUERY()
return x ?= y
```

The first line means to obtain the result of QUERY and set its first half to be the string x and its second half to be y. This calling program simply checks whether the output of QUERY has equal halves.

To complete the attack, we must show that this calling program has non-negligible bias distinguishing the L<sub>prg-⋆</sub> libraries.

+   - When linked to L<sub>prg-real</sub>, the calling program receives outputs of G, which always have matching first/second halves. So Pr[A ⋄ L<sup>G</sup><sub>prg-real</sub> ⇒ 1] = 1. Below we have filled in L<sub>prg-real</sub> with the details of our G algorithm:

| A | L<sup>G</sup><sub>prg-real</sub> |
|---|---|
| x||y := QUERY() | QUERY(): |
| return x ?= y | s ← {0, 1}<sup>λ</sup> |
| | return s||s |

+   - When linked to L<sub>prg-rand</sub>, the calling program receives uniform samples from {0, 1}<sup>2λ</sup>.

| A | L<sup>G</sup><sub>prg-rand</sub> |
|---|---|
| x||y := QUERY() | QUERY(): |
| return x ?= y | r ← {0, 1}<sup>2λ</sup> |
| | return r |

A outputs 1 whenever we sample a string from {0, 1}<sup>2λ</sup> with equal first/second halves. What exactly is the probability of this happening? There are several ways to see that the probability is 1/2<sup>λ</sup> (this is like asking the probability of rolling doubles with two dice, but each die has 2<sup>λ</sup> sides instead of 6). Therefore, Pr[A ⋄ L<sup>G</sup><sub>prg-rand</sub> ⇒ 1] = 1/2<sup>λ</sup>.

The advantage of this adversary is 1 − 1/2<sup>λ</sup> which is certainly non-negligible — it does not even approach 0 as λ grows. This shows that G is not a secure PRG.

This example illustrates how randomness/pseudorandomness is a property of the *entire process*, not of individual strings. If you take a string of 1s and concatenate it with another string of 1s, you get a long string of 1s. “Containing only 1s” is a property of individual strings. If you take a “random string” and concatenate it with another “random string,” you might not get a “random long string.” Being random is not a property of an individual string, but of the entire process that generates it.

Outputs from this G have equal first/second halves, which is an obvious pattern. The challenge of desiging a secure PRG is that its outputs must have *no discernible pattern*! Any pattern will lead to an attack similar to the one shown above.