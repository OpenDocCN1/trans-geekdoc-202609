# CHAPTER 15 Combining Ciphers

# Triple Encryption with Three Keys

If you are going to use triple encryption, I recommend three different keys. The key is longer, but key storage is usually not a problem. Bits are cheap.

```
C = E_{k1}(D_{k2}(E_{k3}(P)))
P = D_{k1}(E_{k2}(D_{k3}(C)))
```

The best memory-time attack takes 2^n steps and requires 2^n blocks of memory; it is a middle-in-the-middle attack [1075]. Triple encryption, with three independent keys, is as secure as one might expect double encryption to be.

# Triple Encryption with Minimum Key (TEMK)

There is a secure way of using triple encryption with two keys that prevents the previous attack, called Triple Encryption with Minimum Key (TEMK) [858]. The trick is to derive three keys from two: X1 and X2;

```
K1 = E_{xi}(D_{xj}(E_{xi}(T1)))
2 = E_{xi}(D_{xj}(E_{xi}(T2)))
3 = E_{xi}(D_{xj}(E_{xi}(T3)))
```

T1, T2, and T3 are constants, which do not have to be secret. This is a special construction that guarantees for any particular pair of keys, the best attack is a known-plaintext attack.

# Triple-Encryption Modes

It's not enough to justify triple encryption; there are several ways to do it. The decision of which to use affects both security and efficiency. Here are two possible triple-encryption modes:

**Inner-CBC:** Encrypt the file in CBC mode three different times [see Figure 15.1a]. This requires three IVs.

```
C1 = E_{k1}(S0 ⊕ P)
S1 = D_{k2}(T1 ⊕ S0)
P1 = T1 ⊕ D_{k1}(T1)
T2 = S1 ⊕ E_{k2}(S1)
S2 = C1 ⊕ D_{k1}(C2)
```

**Outer-CBC:** Triple-encrypt the file in CBC mode [see Figure 15.1b]. This requires one IV.

```
C1 = E_{k3}(D_{k2}(E_{k1}(P ⊕ C0 - 1))
P1 = C1 ⊕ D_{k3}(E_{k2}(D_{k1}(C1)))
```

Both require more resources than single encryption: hardware or more time. However, given three encryption chips, the throughput of inner-CBC is no slower than single encryption. Since the three CBC encryptions are independent, three chips can be kept busy all the time, each feeding back into itself.

On the other hand, outer-CBC feedback is outside the three encryptions. This means that with three chips, the throughput is only one-third of single