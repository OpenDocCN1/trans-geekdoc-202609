
tion of F, so OFB provides security even when F is not invertible. Therefore we will prove security assuming F is simply a PRF.

## Claim 8.5 OFB mode (Construction 8.4) has CPA$ security, if its underlying block cipher F is a secure PRF with parameters in = out = \(\lambda\).

Proof The general structure of the proof is very similar to the proof used for the PRF-based encryption scheme in the previous chapter (Construction 7.4). This is no coincidence: if OFB mode is restricted to plaintexts of a single block, we obtain exactly Construction 7.4!

The idea is that each ciphertext block (apart from the IV) is computed as \(c_i := r \oplus m_i\). By the one-time pad rule, it suffices to show that the \(r\) values are independently pseudorandom. Each \(r\) value is the result of a call to the PRF. These PRF outputs will be independently pseudorandom only if all of the inputs to the PRF are distinct. In OFB mode, we use the output \(r\) of a previous PRF call as input to the next, so it is highly unlikely that this PRF output \(r\) matches a past PRF-input value. To argue this more precisely, the proof includes hybrids in which \(r\) is chosen without replacement (before changing \(r\) back to uniform sampling).

The formal sequence of hybrid libraries is given below:

```
\mathcal{L}^{\text{OFB}}_{\text{cpa\$-real}}:
k \leftarrow \{0, 1\}^\lambda
CTXT(m_1 || \cdots || m_\ell):
  r \leftarrow \{0, 1\}^\lambda
  c_0 := r
  for i = 1 to \ell:
    r := F(k, r)
    c_i := r \oplus m_i
  return c_0 || c_1 || \cdots || c_\ell
```

The starting point is \(\mathcal{L}^{\text{OFB}}_{\text{cpa\$-real}}\), shown here with the details of OFB filled in.

```
CTXT(m_1 || \cdots || m_\ell):
  r \leftarrow \{0, 1\}^\lambda
  c_0 := r
  for i = 1 to \ell:
    r := LOOKUP(r)
    c_i := r \oplus m_i
  return c_0 || c_1 || \cdots || c_\ell
```

```
\mathcal{L}^F_{\text{prf-real}}
k \leftarrow \{0, 1\}^\lambda
LOOKUP(r):
  return F(k, r)
```

The statements pertaining to the PRF F have been factored out in terms of \(\mathcal{L}^F_{\text{prf-real}}\).

```
CTXT(m_1 || \cdots || m_\ell):
r \leftarrow \{0, 1\}^\lambda
c_0 := r
for i = 1 to \ell:
  r := LOOKUP(r)
  c_i := r \oplus m_i
return c_0 || c_1 || \cdots || c_\ell
```

```
\mathcal{L}^F_{\text{prf-rand}}
T := empty
LOOKUP(x):
  if T[x] undefined:
    T[x] \leftarrow \{0, 1\}^\lambda
  return T[x]
```

\(\mathcal{L}^F_{\text{prf-real}}\) has been replaced by \(\mathcal{L}^F_{\text{prf-rand}}\). By the PRF security of F, the change is indistinguishable.

Next, all of the statements that involve sampling values for the variable r are factored out in terms of the \(\mathcal{L}_{\text{samp-L}}\) library from Lemma 4.11:

```
CHALLENGE(m_1 || \cdots || m_\ell):
r := SAMP()
c_0 := r
for i = 1 to \ell:
  r := LOOKUP(r)
  c_i := r \oplus m_i
return c_0 || c_1 || \cdots || c_\ell
```

```
T := empty
LOOKUP(x):
  if T[x] undefined:
    T[x] := SAMP()
  return T[x]
```

```
\mathcal{L}_{\text{samp-L}}
SAMP():
r \leftarrow \{0, 1\}^\lambda
return r
```

\(\mathcal{L}_{\text{samp-L}}\) is then replaced by \(\mathcal{L}_{\text{samp-R}}\). By Lemma 4.11, this change is indistinguishable:

```
CTXT(m_1 || \cdots || m_\ell):
r := SAMP()
c_0 := r
for i = 1 to \ell:
  r := LOOKUP(r)
  c_i := r \oplus m_i
return c_0 || c_1 || \cdots || c_\ell
```

```
T := empty
LOOKUP(x):
  if T[x] undefined:
    T[x] := SAMP()
  return T[x]
```

```
\mathcal{L}_{\text{samp-R}}
R := \emptyset
SAMP():
r \leftarrow \{0, 1\}^\lambda \setminus R
R := R \cup \{r\}
return r
```

Arguments to LOOKUP are never repeated in this hybrid, so the middle library can be significantly simplified:

```
CTXT(m_1 || \cdots || m_\ell):
r := SAMP()
c_0 := r
for i = 1 to \ell:
  r := LOOKUP(r)
  c_i := r \oplus m_i
return c_0 || c_1 || \cdots || c_\ell
```

```
LOOKUP(x):
t := SAMP()
return t
```

```
\mathcal{L}_{\text{samp-R}}
R := \emptyset
SAMP():
r \leftarrow \{0, 1\}^\lambda \setminus R
R := R \cup \{r\}
return r
```

Next, \(\mathcal{L}_{\text{samp-R}}\) is replaced by \(\mathcal{L}_{\text{samp-L}}\). By Lemma 4.11, this change is indistinguishable:

```
CTXT(m_1 || \cdots || m_\ell):
r := SAMP()
c_0 := r
for i = 1 to \ell:
  r := LOOKUP(r)
  c_i := r \oplus m_i
return c_0 || c_1 || \cdots || c_\ell
```

```
LOOKUP(x):
t := SAMP()
return t
```

```
\mathcal{L}_{\text{samp-L}}
SAMP():
r \leftarrow \{0, 1\}^\lambda
return r
```

Subroutine calls to LOOKUP and samp are inlined:

```
CTXT(m_1 || \cdots || m_\ell):
r \leftarrow \{0, 1\}^\lambda
c_0 := r
for i = 1 to \ell:
  r \leftarrow \{0, 1\}^\lambda
  c_i := r \oplus m_i
return c_0 || c_1 || \cdots || c_\ell
```

Finally, the one-time pad rule is applied within the for-loop (omitting some common steps). Note that in the previous hybrid, each value of \(r\) is used _only once_ as a one-time pad. The \(i = 0\) case has also been absorbed into the for-loop. The result is \(\mathcal{L}_{\text{cpa\$-rand}}^{\text{OFB}}\), since OFB encrypts plaintexts of \(\ell\) blocks into \(\ell + 1\) blocks.

```
\mathcal{L}_{\text{cpa\$-rand}}^{\text{OFB}}
CTXT(m_1 || \cdots || m_\ell):
for i = 0 to \ell:
  c_i \leftarrow \{0, 1\}^\lambda
return c_0 || c_1 || \cdots || c_\ell
```

The sequence of hybrids shows that \(\mathcal{L}_{\text{cpa\$-real}}^{\text{OFB}} \approx \mathcal{L}_{\text{cpa\$-rand}}^{\text{OFB}}\), and so OFB mode has pseudorandom ciphertexts.

We proved the claim assuming \(F\) is a PRF only, since OFB mode does not require \(F\) to be invertible. Since we assume a PRF with parameters \(\text{in} = \text{out} = \lambda\), the PRP switching lemma (Lemma 6.7) shows that OFB is secure also when \(F\) is a PRP with blocklength \(n = \lambda\).

## 8.4 Padding & Ciphertext Stealing

So far we have assumed that all plaintexts are exact multiples of the blocklength. But data in the real world is not always so accommodating. How are block ciphers used in practice with data that has arbitrary length?

### Padding

Padding just refers to any approach to encode arbitrary-length data into data that is a multiple of the blocklength. The only requirement is that this encoding is reversible. More formally, a **padding scheme** should consist of two algorithms:

- pad: takes as input a string of any length, and outputs a string whose length is a multiple of the blocklength
- unpad: the inverse of pad. We require that unpad(pad(x)) = x for all strings x.

The idea is that the sender can encrypt pad(x), which is guaranteed to be a multiple of the blocklength; the receiver can decrypt and run unpad on the result to obtain x.

In the real world, data almost always comes in **bytes** and not bits, so that will be our assumption here. In this section we will write bytes in hex, for example `8f`. Typical blocklengths are 128 bits (16 bytes) or 256 bits (32 bytes).

Here are a few common approaches for padding:

**Null padding:** The simplest padding approach is to just fill the final block with null bytes (`00`). The problem with this approach is that it is not always reversible. For example, `pad(31 41 59)` and `pad(31 41 59 00)` will give the same result. It is not possible to distinguish between a null byte that was added for padding and one that was intentionally the last byte of the data.

**ANSI X.923 standard:** Data is padded with null bytes, except for the last byte of padding which indicates how many padding bytes there are. In essence, the last byte of the padded message tells the receiver how many bytes to remove to recover the original message.

Note that in this padding scheme (and indeed in all of them), if the original unpadded data is _already_ a multiple of the block length, then **an entire extra block of padding** must be added. This is necessary because it is possible for the original data to end with some bytes that look like valid padding (e.g., `00 00 03`), and we do not want these bytes to be removed erroneously.

Example Below are some examples of valid and invalid X.923 padding (using 16-byte blocks):

- `01 34 11 d9 81 88 05 57 1d 73 c3 00 00 00 00 00 05` => valid
- `95 51 05 4a d6 5a a3 44 af b3 85 00 00 00 00 03` => valid
- `71 da 77 5a 5e 77 eb a8 73 c5 50 b5 81 d5 96 01` => valid
- `5b 1c 01 41 5d 53 86 4e e4 94 13 e8 7a 89 c4 71` => invalid
- `d4 0d d8 7b 53 24 c6 d1 af 5f d6 f6 00 c0 00 04` => invalid

**PKCS#7 standard:** If _b_ bytes of padding are needed, then the data is padded not with null bytes but with _b_ bytes. Again, the last byte of the padded message tells the receiver how many bytes to remove.
