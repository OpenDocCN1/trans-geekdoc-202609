
where we used `n[k]` in place to `x[k]` to be in line with a more standard notation used in DPs. Recall that `n[k]` is the number of times the `k`th variable associated with probability `P = G(T[k])` occurs, after `n` successive experiments. In our setting, `n[k]` is the cardinality of the previously defined set `I[k]`, i.e.,

```
n[k] = #{i: θ[i] ∈ T[k]}.
```

In words, `n[k]` is the number of draws from Θ that lie in `T[k]`.

Having observed `θ[1], …, θ[n]`, we see they are equivalent to specific occurrence numbers, `n[1], …, n[K]`. Thus, taking into account the property of the conjugate pairs, as expressed in Eq. [(12.77)](#Chp012_583-634_B9780443292385000184.xhtml) in the context of [Example 12.6](#Chp012_583-634_B9780443292385000184.xhtml), it can be readily seen that

```
(G(T[1]), …, G(T[K]) | θ[1], …, θ[n]) = Dir(αG[0](T[1]) + n[1], …, αG[0](T[K]) + n[K]).
```

(13.115)

It is not difficult to see (e.g., Problem [13.20](#Chp013_635-716_B9780443292385000196.xhtml#o0200)) that the above can be equivalently written as
