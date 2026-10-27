generator is probably new to you. It is simply a number that, when raised to consecutive powers (mod \(p\)), results in the entire group being generated. That’s why it’s called a *generator* and often denoted by the letter \(g\). If someone is eavesdropping on the line and obtains the values \(p\) and \(g\), that’s okay! After Alice and Bob agree on these numbers, each person (except the eavesdropper!) selects another number. Let’s say Alice chooses \(x\) and Bob chooses \(y\). They keep *these values* secret. Alice calculates \(g^x\pmod p\) and Bob calculates \(g^y\pmod p\). They then exchange these new values. Alice would have great difficulty calculating \(y\) from \(g^y\). Similarly, Bob is unlikely to be able to determine Alice’s \(x\). However, both can form \(g^{xy}\). Alice simply raises the number Bob sent her to the power of \(x\) and Bob raises the number Alice sent him to the power of \(y\). The eavesdropper cannot do this as she knows neither \(x\) nor \(y\). She may have intercepted \(p\), \(g\), \(g^x\), and \(g^y\), but this won’t help her to find \(g^{xy}\). Thus, Alice and Bob now share a secret number. This will serve as their key for future communication, using whatever system they choose.

When \(g\), \(p\), and \(g^x\pmod p\) are known, but not \(x\), determining \(x\) is known as the *discrete log problem*. The security of Diffie–Hellman key exchange sounds like it should be equivalent to this problem, but this has yet to be proven. To recap, the two problems are:

+   1. Discrete Log: Given \(g^x\), find \(g\).
+   2. Diffie–Hellman: Given \(g^x\) and \(g^y\), find \(g^{xy}\).

It is possible that someone may find a way to defeat the key exchange (problem 2) without solving the discrete log problem (problem 1). This is a very big open problem. More will be said about the difficulty of the discrete log problem in *Section 16.8*, which follows a discussion of complexity theory. In any case, we have a lovely system built on nothing more complicated than the laws of exponents and the idea of remainder arithmetic!

Malcolm Williamson discovered Diffie–Hellman key exchange before the individuals it is named after, but he was employed by GCHQ at the time, and his work was classified. It was only released in 1997.

Implemented as described above, the key exchange requires several messages be sent. If we are willing to do this, even some of the cryptosystems discussed earlier in this text may be used to securely send a message to someone with whom a key exchange has not taken place. An analogy will make the process clear, after which it will be described more mathematically.

Alice can send Bob a message she places in a padlock and secures with a padlock. Bob doesn’t try to open it, because he doesn’t have the key. Instead, he simply adds his own padlock and mails it back to Alice. Anyone wishing to see the message at this stage must be able to remove both padlocks. Alice can only remove her own, which she does. She then mails it back to Bob, who removes his padlock and reads the message.

Now for the mathematical version of the physical process described above:

+   - Let \(E_A\), \(E_B\), \(D_A\), and \(D_B\) represent the enciphering and deciphering algorithms (along with the keys \(A\) and \(B\)) used by Alice and Bob.
+   - Alice sends Bob \(E_A(M)\).
+   - Bob sends Alice \(E_B(E_A(M))\).
+   - Alice sends Bob \(D_A(E_B(E_A(M)))\).

*Note:* If \(D_A\) and \(E_B\) commute, \(D_A\) and \(E_A\) will then cancel out and Alice’s final message will amount to \(E_B(M)\)

+   - Bob then applies \(D_B\) to Alice’s last message and reads the plaintext.