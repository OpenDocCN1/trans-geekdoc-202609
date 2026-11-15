that some function G is a secure PRG, it **would resolve the famous P vs NP problem** — the most famous unsolved problem in computer science (and arguably, all of mathematics).

The next best thing that cryptographic research can offer are **candidate PRGs**, which are _conjectured_ to be secure. The best examples of such PRGs are the ones that have been subjected to significant public scrutiny and resisted all attempts at attacks so far.

In fact, the entire rest of this book is based on cryptography that is only _conjectured_ to be secure. How is this possible, given the book’s stated focus on _provable security_? As you progress through the book, pay attention to how all of the provable security claims are _conditional_ — if X is secure then Y is secure. You will be able to trace back through this web of implications and discover that there are only a small number of underlying cryptographic primitives whose security is merely _conjectured_ (PRGs are one example of such a primitive). Everything else builds on these primitives in a provably secure way.

With that disclaimer out of the way, surely _now_ you can be shown an example of a conjectured secure PRG, right? There are indeed some conjectured PRGs that are simple enough to show you at this point, but you won’t find them in the book. The problem is that none of these PRG candidates are really used in practice. When you really need a PRG in practice, you would actually use a PRG that is built from something called a block cipher (which we won’t see until Chapter 6). A block cipher is _conceptually_ more complicated than a PRG, and can even be built from a PRG (in principle). That explains why this book starts with PRGs. In practice, a block cipher is just a more useful object, so that is what you would find easily available (even implemented with specialized CPU instructions in most CPUs). When we introduce block ciphers (and pseudorandom functions), we will discuss how they can be used to construct PRGs.

# How NOT to Build a PRG

We can appreciate the challenges involved in building a PRG “from scratch” by first looking at an obvious idea for a PRG and understanding why it’s insecure.

**Example** Let’s focus on the case of a length-doubling PRG. It should take in \(\lambda\) bits and output \(2\lambda\) bits. The output should look random when the input is sampled uniformly. A natural idea is for the candidate PRG to simply repeat the input twice. After all, if the input s is random, then s||s is also random, too, right?

```
G(s):
return s||s
```

To understand why this PRG is insecure, first let me ask you whether the following strings look like they were sampled uniformly from {0, 1}\(^8\):

11011101, 01010101, 01110111, 01000100, ...

Do you see any patterns? Every string has its first half equal to its second half. That is a conspicuous pattern because it is relatively rare for a uniformly chosen string to have this property.