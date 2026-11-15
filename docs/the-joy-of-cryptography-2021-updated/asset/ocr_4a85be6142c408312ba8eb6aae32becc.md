▶ Not every MAC is a PRF. Just like not every encryption scheme has pseudorandom ciphertexts, not every MAC scheme has pseudorandom tags. Imagine taking a secure MAC scheme and modifying it as \(\text{MAC}'(k, m) = \text{MAC}(k, m)||0^\lambda\). Adding 0s to every tag prevents the tags from looking pseudorandom, but does not make the tags any easier to guess. **Something doesn't have to be uniformly random in order to be hard to guess.**

It is true that in the vast majority of cases we will encounter MAC schemes with random tags, and PRFs with long outputs (\(\text{out} \geqslant \lambda\)). But it is good practice to know whether you really need something that is *pseudorandom* or *hard to guess*.

# 10.3 MACs for Long Messages

Using a PRF as a MAC is useful only for short, fixed-length messages, since most PRFs that exist in practice are limited to such inputs. Can we somehow extend a PRF to construct a MAC scheme for long messages, similar to how we used block cipher modes to construct encryption for long messages?

# How NOT to do it

To understand the challenges of constructing a MAC for long messages, we first explore some approaches that *don't* work. The things that can go wrong in an insecure MAC are quite different in character to the things that can go wrong in a block cipher mode, so pay attention closely!

**Example** Let \(F\) be a PRF with \(\text{in} = \text{out} = \lambda\). Below is a MAC approach for messages of length \(2\lambda\). It is inspired by ECB mode, so you know it's going to be a disaster:

```
ECBMAC(k, m_1 || m_2):
t_1 := F(k, m_1)
t_2 := F(k, m_2)
return t_1 || t_2
```

One problem with this approach is that, although the PRF authenticates each block \(m_1, m_2\) individually, it does nothing to authenticate that \(m_1\) is the first block but \(m_2\) is the second one. Translating this observation into an attack, an adversary can ask for the MAC tag of \(m_1 || m_2\) and then predict/forge the tag for \(m_2 || m_1\):

```
\(\mathcal{A}:\)
\(t_1 || t_2 := \text{GETTAG}(0^\lambda || 1^\lambda)\)
\(\text{return CHECKTAG}(1^\lambda || 0^\lambda, t_2 || t_1)\)
```

When \(\mathcal{A}\) is linked to \(\mathcal{L}_{\text{mac-real}}\), it always return *true*, since we can tell that \(t_2 || t_1\) is indeed the valid tag for \(1^\lambda || 0^\lambda\). When \(\mathcal{A}\) is linked to \(\mathcal{L}_{\text{mac-fake}}\), it always return *false*, since the calling program never called \(\text{GETTAG}\) with input \(1^\lambda || 0^\lambda\). Hence, \(\mathcal{A}\) distinguishes the libraries with advantage 1.