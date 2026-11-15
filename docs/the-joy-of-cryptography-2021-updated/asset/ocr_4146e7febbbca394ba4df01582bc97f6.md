Through this sequence of hybrid libraries, we showed that:

\(\mathcal{L}_{\text{prg-real}}^{H_1} \equiv \mathcal{L}_{\text{hyb-1}} \approx \mathcal{L}_{\text{hyb-2}} \equiv \mathcal{L}_{\text{hyb-3}} \equiv \mathcal{L}_{\text{hyb-4}} \equiv \mathcal{L}_{\text{hyb-5}} \approx \mathcal{L}_{\text{hyb-6}} \equiv \mathcal{L}_{\text{hyb-7}} \equiv \mathcal{L}_{\text{prg-rand}}^{H_1}\)

Hence, \(H_1\) is a secure PRG.

# Where the Proof Breaks Down for \(H_2\)

The only difference between \(H_1\) and \(H_2\) is that the variable \(y\) is included in the output. How does that minor change affect the reasoning that we applied to \(H_1\)?

```
H2(s):
x||y := G(s)
u||v := G(y)
return x||y||u||v
```

We argued that outputs \(u\) and \(v\) are indistinguishable from uniform since its input \(y\) is also indistinguishable from random. But it’s not quite so simple: A PRG’s output is indistinguishable from random if (1) its seed is uniform, and (2) *the seed is not used for anything else!* This construction \(H_2\) violates condition (2) because it includes the “seed” \(y\) in the output.

We can see this idea reflected in the formal PRG definition. In \(\mathcal{L}_{\text{prg-real}}\), the seed \(s\) is chosen uniformly, given as input to \(G\), and then goes out of scope! If we try to reproduce the security proof for \(H_1\) with \(H_2\) instead, we’ll get stuck when we are trying to factor out the second call to \(G\) in terms of \(\mathcal{L}_{\text{prg-real}}\):

```
QUERY_H2():
x <- {0, 1}^\lambda
y <- {0, 1}^\lambda
u||v := G(y)
return x||y||u||v

~>

QUERY_H1():
x <- {0, 1}^\lambda
u||v := QUERY_G()
return x|| [gray] ||u||v

<> (diamond)

L_prg-real
QUERY_G():
s <- {0, 1}^\lambda
return G(s)
```

scope error! \(y\) undefined

We are trying to factor out the two highlighted lines into a separate library, renaming \(y\) into \(s\) in the process. But \(s\) can only exist inside the private scope of the new library, while there still exists a “dangling reference” to \(y\) in the original library.

Speaking more generally about PRGs, suppose we have a call to \(G\) somewhere and want to argue that its outputs are pseudorandom. We can only express this call to \(G\) in terms of \(\mathcal{L}_{\text{prg-real}}^G\) if the input to \(G\) is uniform and is used nowhere else. That’s not true here – we can’t express one of the calls to \(G\) in terms of \(\mathcal{L}_{\text{prg-real}}^G\), so we can’t be sure that the outputs of that call to \(G\) look random.

These subtle issues are not limited to PRGs. Every hybrid security proof in this course includes steps where we factor out some statements in terms of some pre-existing library. Don’t take these steps for granted! They will fail (often because of scoping issues) if the construction isn’t using the building block correctly. You should always treat such “factoring out” steps as “sanity checks” for your proof.