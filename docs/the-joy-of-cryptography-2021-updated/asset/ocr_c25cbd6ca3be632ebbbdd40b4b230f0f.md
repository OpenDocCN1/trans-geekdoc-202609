To decrypt, one can use the decryption key of the public-key scheme to obtain the temporary key. Then the temporary key can be used to decrypt the main payload.

# Construction 15.8 (Hybrid Enc)

Let \(\Sigma_{pub}\) be a public-key encryption scheme, and let \(\Sigma_{sym}\) be a symmetric-key encryption scheme, where \(\Sigma_{sym}.\mathcal{K} \subseteq \Sigma_{pub}.\mathcal{M}\) — that is, the public-key scheme is capable of encrypting keys of the symmetric-key scheme.

Then we define \(\Sigma_{hyb}\) to be the following construction:

```
Enc(pk, m):
  tk <- \Sigma_sym.KeyGen
  c_pub <- \Sigma_pub.Enc(pk, tk)
  c_sym <- \Sigma_sym.Enc(tk, m)
  return (c_pub, c_sym)

M = \Sigma_sym.M
C = \Sigma_pub.C x \Sigma_sym.C

KeyGen:
(pk, sk) <- \Sigma_pub.KeyGen
return (pk, sk)

Dec(sk, (c_pub, c_sym)):
  tk := \Sigma_pub.Dec(sk, c_pub)
  return \Sigma_sym.Dec(tk, c_sym)
```

Importantly, the message space of the hybrid encryption scheme is the message space of the symmetric-key scheme (think of this as involving very long plaintexts), but encryption and decryption involves expensive public-key operations only on a small temporary key (think of this as a very short string).

The correctness of the scheme can be verified via:

```
Dec(sk, Enc(pk, m)) = Dec(sk, (\Sigma_pub.Enc(pk, tk), \Sigma_sym.Enc(tk, m)))
= \Sigma_sym.Dec( \Sigma_pub.Dec(sk, \Sigma_pub.Enc(pk, tk)), \Sigma_sym.Enc(tk, m) )
= \Sigma_sym.Dec( tk, \Sigma_sym.Enc(tk, m) )
= m.
```

To show that hybrid encryption is a valid way to encrypt data, we prove that it provides CPA security, when its two components have appropriate security properties:

# Claim 15.9

If \(\Sigma_{sym}\) is a one-time-secret symmetric-key encryption scheme and \(\Sigma_{pub}\) is a CPA-secure public-key encryption scheme, then the hybrid scheme \(\Sigma_{hyb}\) (Construction 15.8) is also a CPA-secure public-key encryption scheme.

Note that \(\Sigma_{sym}\) does not even need to be CPA-secure. Intuitively, one-time secrecy suffices because each temporary key \(tk\) is used only once to encrypt just a single plaintext.

# Proof

As usual, our goal is to show that \(\mathcal{L}^{\Sigma_{hyb}}_{\text{pk-cpa-L}} \approx \mathcal{L}^{\Sigma_{hyb}}_{\text{pk-cpa-R}}\) which we do in a standard sequence of hybrids: