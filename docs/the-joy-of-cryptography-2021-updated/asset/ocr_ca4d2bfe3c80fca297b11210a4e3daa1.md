```
L^\Sigma_{pad-L}

k \leftarrow \Sigma.KeyGen
\underline{eavesdrop(m_L, m_R \in \Sigma.M):}
if |m_L| \neq |m_R| return err
return \Sigma.Enc(k, pad(m_L))
\underline{paddingoracle(c \in \Sigma.C):}
return validpad(\Sigma.Dec(k, c))
```

```
L^\Sigma_{pad-R}

k \leftarrow \Sigma.KeyGen
\underline{eavesdrop(m_L, m_R \in \Sigma.M):}
if |m_L| \neq |m_R| return err
return \Sigma.Enc(k, pad(m_R))
\underline{paddingoracle(c \in \Sigma.C):}
return validpad(\Sigma.Dec(k, c))
```

That is, a CCA-secure encryption scheme hides underlying plaintexts in the presence of padding-oracle attacks.

Note: The distinguisher can even send a ciphertext c obtained from eavesdrop as an argument to paddingoracle. Your proof should somehow account for this when reducing to the CCA security of \(\Sigma\).

9.16. Show that an encryption scheme \(\Sigma\) has CCA$ security if and only if the following two libraries are indistinguishable:

```
L^\Sigma_{left}

k \leftarrow \Sigma.KeyGen
\underline{eavesdrop(m \in \Sigma.M):}
return \Sigma.Enc(k, m)
\underline{decrypt(c \in \Sigma.C):}
return \Sigma.Dec(k, c)
```

```
L^\Sigma_{right}

k \leftarrow \Sigma.KeyGen
D := empty assoc. array
\underline{eavesdrop(m \in \Sigma.M):}
c \leftarrow \Sigma.C(|m|)
D[c] := m
return c
\underline{decrypt(c \in \Sigma.C):}
if D[c] exists: return D[c]
else: return \Sigma.Dec(k, c)
```

Note: In \(\mathcal{L}_{left}\), the adversary can obtain the decryption of *any* ciphertext via decrypt. In \(\mathcal{L}_{right}\), the decrypt subroutine is “patched” (via D) to give reasonable answers to ciphertexts generated in eavesdrop.