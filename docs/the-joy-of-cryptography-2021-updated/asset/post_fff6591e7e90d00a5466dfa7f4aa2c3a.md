
## Construction 6.4 (GGM PRF)

```
in = arbitrary
out = \lambda

F(k, x \in \{0, 1\}^in):
v := k
for i = 1 to in:
  if x_i = 0 then v := G_L(v)
  if x_i = 1 then v := G_R(v)
return v
```

## Claim 6.5 If G is a secure PRG, then Construction 6.4 is a secure PRF.

Proof We prove the claim using a sequence of hybrids. The number of hybrids in this case depends on the input-length parameter in. The hybrids are defined as follows:

```
\mathcal{L}_{\text{hyb-d}}
T := empty assoc. array
QUERY(x):
  p := first d bits of x
  if T[p] undefined:
    T[p] \leftarrow \{0, 1\}^\lambda
  v := T[p]
  for i = d + 1 to in:
    if x_i = 0 then v := G_L(v)
    if x_i = 1 then v := G_R(v)
  return v
```

The hybrids differ only in their hard-coded value of d. We will show that

\mathcal{L}_{\text{prf-real}}^F \equiv \mathcal{L}_{\text{hyb-0}} \approx \mathcal{L}_{\text{hyb-1}} \approx \dots \approx \mathcal{L}_{\text{hyb-in}} \equiv \mathcal{L}_{\text{prf-rand}}^F.

We first start by understanding the behavior of \mathcal{L}_{\text{hyb-d}} for extreme choices of d. Simplifications to the code are shown on the right.

```
\mathcal{L}_{\text{hyb-0}}
T := empty assoc. array
LOOKUP(x):
  p := first 0 bits of x
  if T[p] undefined: T[p] \leftarrow \{0, 1\}^\lambda
  v := T[p]
  for i = 1 to in:
    if x_i = 0 then v := G_L(v)
    if x_i = 1 then v := G_R(v)
  return v

k := undefined // k is alias for T[\epsilon]
p = \epsilon
if k undefined: k \leftarrow \{0, 1\}^\lambda
v := F(k, x)
return F(k, x)
```

In \mathcal{L}_{\text{hyb-0}}, we always have p = \epsilon, so the only entry of T that is accessed is T[\epsilon]. Then renaming T[\epsilon] to k, we see that \mathcal{L}_{\text{hyb-0}} \equiv \mathcal{L}_{\text{prf-real}}^F. The only difference is when the PRF seed k (T[\epsilon]) is sampled: eagerly at initialization time in \mathcal{L}_{\text{prf-real}}^F vs. at the last possible minute in \mathcal{L}_{\text{hyb-0}}.

```
\mathcal{L}_{\text{hyb-in}}
T := empty assoc. array
LOOKUP(x):
  p := first in bits of x
  if T[p] undefined:
    T[p] \leftarrow \{0, 1\}^\lambda
  v := T[p]
  for i = in + 1 to in:
    if x_i = 0 then v := G_L(v)
    if x_i = 1 then v := G_R(v)
  return v

p = x
if T[x] undefined:
  T[x] \leftarrow \{0, 1\}^\lambda
// unreachable
return T[x]
```

In \mathcal{L}_{\text{hyb-in}}, we always have p = x and the body of the for-loop is always unreachable. In that case, it is easy to see that \mathcal{L}_{\text{hyb-in}} has identical behavior to \mathcal{L}^F_{\text{prf-rand}}.

The general pattern is that \mathcal{L}_{\text{hyb-d}} "chops off" the top d levels of the conceptual binary tree. When computing the output for some string x, we don't start traversing the tree from the root but rather d levels down the tree, at the node whose position is the d-bit prefix of x (called p in the library). We initialize the label of this node as a uniform value (unless it has already been defined), and then continue the traversal to the leaf x.
To finish the proof, we show that \mathcal{L}_{\text{hyb-(d - 1)}} and \mathcal{L}_{\text{hyb-d}} are indistinguishable:

```
T := empty assoc. array
LOOKUP(x):
  p := first d - 1 bits of x
  if T[p] undefined:
    T[p] \leftarrow \{0, 1\}^\lambda
  T[p||0] := G_L(T[p])
  T[p||1] := G_R(T[p])
  p' := first d bits of x
  v := T[p']
  for i = d + 1 to in:
    if x_i = 0 then v := G_L(v)
    if x_i = 1 then v := G_R(v)
  return v
```

The library that is shown here is different from \mathcal{L}_{\text{hyb-(d - 1)}} in the highlighted parts. However, these differences have no effect on the calling program. The library here advances d - 1 levels down the tree (to the node at location p), initializes that node's label as a uniform value, then computes the labels for both its children, and finally continues computing labels toward the leaf. The only significant difference from \mathcal{L}_{\text{hyb-(d - 1)}} is that it computes the labels of both of p's children, even though only one is on the path to x. Since it computes the label correctly, though, it makes no difference when (or if) this extra label is computed.

```
T := empty assoc. array
LOOKUP(x):
  p := first d - 1 bits of x
  if T[p] undefined:
    T[p||0] || T[p||1] := QUERY()
  p' := first d + 1 bits of x
  v := T[p']
  for i = d + 1 to in:
    if x_i = 0 then v := G_L(v)
    if x_i = 1 then v := G_R(v)
  return v
```

```
\mathcal{L}^G_{\text{prg-real}}
QUERY():
  s \leftarrow \{0, 1\}^\lambda
  return G(s)
```

We have factored out the body of the if-statement in terms of \mathcal{L}^G_{\text{prg-real}} since it involves a call to G on uniform input. Importantly, the seed to G (called T[p] in the previous hybrid) was not used anywhere else — it was a string of length d-1 while the library only reads T[p'] for p' of length d. The change has no effect on the calling program.

```
T := empty assoc. array
LOOKUP(x):
  p := first d - 1 bits of x
  if T[p] undefined:
    T[p||0] || T[p||1] := QUERY()
  p' := first d + 1 bits of x
  v := T[p']
  for i = d + 1 to in:
    if x_i = 0 then v := G_L(v)
    if x_i = 1 then v := G_R(v)
  return v
```

```
\mathcal{L}^G_{\text{prg-rand}}
QUERY():
  r \leftarrow \{0, 1\}^{2\lambda}
  return r
```

We have applied the security of G and replaced \mathcal{L}^G_{\text{prg-real}} with \mathcal{L}^G_{\text{prg-rand}}. The change is indistinguishable.

```
T := empty assoc. array
LOOKUP(x):
  p := first d - 1 bits of x
  if T[p] undefined:
    T[p||0] \leftarrow \{0, 1\}^\lambda
    T[p||1] \leftarrow \{0, 1\}^\lambda
  p' := first d + 1 bits of x
  v := T[p']
  for i = d + 1 to in:
    if x_i = 0 then v := G_L(v)
    if x_i = 1 then v := G_R(v)
  return v
```

We have inlined \mathcal{L}_{\text{prg-rand}} and split the sampling of 2\lambda bits into two separate statements sampling \lambda bits each. In this library, we advance d levels down the tree, assign a uniform label to a node (and its sibling), and then proceed to the leaf applying G as usual. The only difference between this library and \mathcal{L}_{\text{hyb-d}} is that we sample the label of a node that is not on our direct path. But since we sample it uniformly, it doesn't matter when (or if) that extra value is sampled. Hence, this library has identical behavior to \mathcal{L}_{\text{hyb-d}}.

We showed that \mathcal{L}_{\text{hyb-(d-1)}} \approx \mathcal{L}_{\text{hyb-d}}. Putting everything together, we have:
\mathcal{L}^F_{\text{prf-real}} \equiv \mathcal{L}_{\text{hyb-0}} \approx \mathcal{L}_{\text{hyb-1}} \approx \dots \approx \mathcal{L}_{\text{hyb-in}} \equiv \mathcal{L}^F_{\text{prf-rand}}.

Hence, F is a secure PRF.

## 6.3 Block Ciphers (Pseudorandom Permutations)

After fixing the seed of a PRF, it computes a function from $\{0, 1\}^{\text{in}}$ to $\{0, 1\}^{\text{out}}$. Let’s consider the case where $\text{in} = \text{out}$. Some functions from $\{0, 1\}^{\text{in}}$ to $\{0, 1\}^{\text{out}}$ are invertible, which leads to the question of whether a PRF might realize such a function and be invertible (with knowledge of the seed). In other words, what if it were possible to determine $x$ when given $k$ and $F(k, x)$? While this would be a convenient property, it is not guaranteed by the PRF security definition, even in the case of $\text{in} = \text{out}$. A function from $\{0, 1\}^{\text{in}}$ to $\{0, 1\}^{\text{out}}$ chosen at random is unlikely to have an inverse, therefore a PRF instantiated with a random key is unlikely to have an inverse.

A **pseudorandom permutation (PRP)** — also called a **block cipher** — is essentially a PRF that is guaranteed to be invertible for every choice of seed. We use both terms (PRP and block cipher) interchangeably. The term “permutation” refers to the fact that, for every $k$, the function $F(k, \cdot)$ should be a permutation of $\{0, 1\}^{\text{in}}$. Instead of requiring a PRP to be indistinguishable from a randomly chosen function, we require it to be indistinguishable from a randomly chosen _invertible_ function.$^2$ This means we must modify one of the libraries from the PRF definition. Instead of populating the associative array $T$ with uniformly random values, it chooses uniformly random _but distinct_ values. As long as $T$ gives distinct outputs on distinct inputs, it is consistent with some invertible function. The library guarantees distinctness by only sampling values that it has not previously assigned. Thinking of an associative array $T$ as a key-value store, we use the notation $T.\text{values}$ to denote the set of values stored in $T$.

### Definition 6.6 (PRP syntax)

Let \(F : \{0, 1\}^\lambda \times \{0, 1\}^{\text{\textit{blen}}} \rightarrow \{0, 1\}^{\text{\textit{blen}}}\) be a deterministic function. We refer to blen as the **blocklength** of F and any element of \(\{0, 1\}^{\text{\textit{blen}}}\) as a **block**.

We call F a **secure pseudorandom permutation (PRP) (block cipher)** if the following two conditions hold:

- (**Invertible given k**) There is a function \(F^{-1} : \{0, 1\}^\lambda \times \{0, 1\}^{\text{\textit{blen}}} \rightarrow \{0, 1\}^{\text{\textit{blen}}}\) satisfying

\(F^{-1}(k, F(k, x)) = x\),

for all \(k \in \{0, 1\}^\lambda\) and all \(x \in \{0, 1\}^{\text{\textit{blen}}}\).

- (**Security**) \(\mathcal{L}^F_{\text{prp-real}} \approx \mathcal{L}^F_{\text{prp-rand}}\)

| \(\mathcal{L}^F_{\text{prp-real}}\) |
| :--- |
| \(k \leftarrow \{0, 1\}^\lambda\) |
| \(\underline{\text{LOOKUP}}(x \in \{0, 1\}^{\text{\textit{blen}}})\) |
| return \(F(k, x)\) |

| \(\mathcal{L}^F_{\text{prp-rand}}\) |
| :--- |
| \(T := \text{empty assoc. array}\) |
| \(\underline{\text{LOOKUP}}(x \in \{0, 1\}^{\text{\textit{blen}}})\) |
| if \(T[x]\) undefined: |
| \(T[x] \leftarrow \{0, 1\}^{\text{\textit{blen}}} \setminus T.\text{values}\) |
| return \(T[x]\) |

$^2$As we will see later, the distinction between randomly chosen function and randomly chosen _invertible_ function is not as significant as it might seem.
