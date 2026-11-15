
## Security

To show the security of Shamir secret sharing, we first show a convenient lemma about the distribution of shares in an unauthorized set:

## Lemma 3.12

Let p be a prime and define the following two libraries:

```
$\mathcal{L}_{\text{shamir-real}}$
POLY(m, t, U \subseteq \{1, \dots, p\}):
 if |U| \ge t: return err
 f_1, \dots, f_{t-1} \leftarrow \mathbb{Z}_p
 f(\boldsymbol{x}) := m + \sum_{j=1}^{t-1} f_j x^j
 for i \in U:
 s_i := (i, f(i) \% p)
 return \{s_i \mid i \in U\}
```

```
$\mathcal{L}_{\text{shamir-rand}}$
POLY(m, t, U \subseteq \{1, \dots, p\}):
 if |U| \ge t: return err
 for i \in U:
 y_i \leftarrow \mathbb{Z}_p
 s_i := (i, y_i)
 return \{s_i \mid i \in U\}
```

$\mathcal{L}_{\text{shamir-real}}$ chooses a random degree-(t − 1) polynomial that passes through the point (0, m), then evaluates it at the given x-coordinates (specified by U). $\mathcal{L}_{\text{shamir-rand}}$ simply gives uniformly chosen points, unrelated to any polynomial.

The claim is that these libraries are interchangeable: $\mathcal{L}_{\text{shamir-real}} \equiv \mathcal{L}_{\text{shamir-rand}}$.

## Proof

Fix a message $m \in \mathbb{Z}_p$, fix set $U$ of users with $|U| < t$, and for each $i \in U$ fix a value $y_i \in \mathbb{Z}_p$. We wish to consider the probability that a call to POLY$(m, t, U)$ outputs $\{(i, y_i) \mid i \in U\}$, in each of the two libraries.

In library $\mathcal{L}_{\text{shamir-real}}$, the subroutine chooses a random degree-$(t-1)$ polynomial $f$ such that $f(0) \equiv_p m$. From Corollary 3.10, we know there are $p^{t-1}$ such polynomials.

In order for POLY to output points consistent with our chosen $y_i$’s, the library must have chosen one of the polynomials that passes through $(0, m)$ and all of the $\{(i, y_i) \mid i \in U\}$ points. The library must have chosen one of the polynomials that passes through a specific choice of $|U| + 1$ points, and Corollary 3.10 tells us that there are $p^{t-(|U|+1)}$ such polynomials.

The only way for POLY to give our desired output is for it to choose one of the $p^{t-(|U|+1)}$ “good” polynomials, out of the $p^{t-1}$ possibilities. This happens with probability exactly

```
\frac{p^{t-|U|-1}}{p^{t-1}} = p^{-|U|}
```

Now, in library $\mathcal{L}_{\text{shamir-rand}}$, POLY chooses its $|U|$ output values uniformly in $\mathbb{Z}_p$. There are $p^{|U|}$ ways to choose them. But only one of those ways causes POLY$(m, t, U)$ to output our specific choice of $\{(i, y_i) \mid i \in U\}$. Hence, the probability of receiving this output is $p^{-|U|}$.

For all possible inputs to POLY, both libraries assign the same probability to every possible output. Hence, the libraries are interchangeable.

## Theorem 3.13

Shamir’s secret-sharing scheme (Construction 3.11) is secure according to Definition 3.3.

This is similar to how, in Claim 2.7, we fixed a particular $m$ and $c$ and computed the probability that EAVESDROP$(m) = c$.

## Proof

Let $\mathcal{S}$ denote the Shamir secret-sharing scheme. We prove that $\mathcal{L}_{\text{tss-L}}^{\mathcal{S}} \equiv \mathcal{L}_{\text{tss-R}}^{\mathcal{S}}$ via a hybrid argument.

```
$\mathcal{L}_{\text{tss-L}}^{\mathcal{S}}$:
SHARE(m_L, m_R, U):
  if |U| >= t: return err
  f_1, ..., f_{t-1} <- Z_p
  f(x) := m_L + \sum_{j=1}^{t-1} f_j x^j
  for i \in U:
    s_i := (i, f(i) % p)
  return {s_i | i \in U}
```

Our starting point is $\mathcal{L}_{\text{tss-L}}^{\mathcal{S}}$, shown here with the details of Shamir secret-sharing filled in.

```
SHARE(m_L, m_R, U):
return POLY(m_L, t, U)
```

```
$\mathcal{L}_{\text{shamir-real}}$:
POLY(m, t, U):
  if |U| >= t: return err
  f_1, ..., f_{t-1} <- Z_p
  f(x) := m + \sum_{j=1}^{t-1} f_j x^j
  for i \in U:
    s_i := (i, f(i) % p)
  return {s_i | i \in U}
```

Almost the entire body of the SHARE subroutine has been factored out in terms of the $\mathcal{L}_{\text{shamir-real}}$ library defined above. The only thing remaining is the “choice” of whether to share $m_L$ or $m_R$. Restructuring the code in this way has no effect on the library’s behavior.

```
SHARE(m_L, m_R, U):
return POLY(m_L, t, U)
```

```
$\mathcal{L}_{\text{shamir-rand}}$:
POLY(m, t, U):
  if |U| >= t: return err
  for i \in U:
    y_i <- Z_p
    s_i := (i, y_i)
  return {s_i | i \in U}
```

By Lemma 3.12, we can replace $\mathcal{L}_{\text{shamir-real}}$ with $\mathcal{L}_{\text{shamir-rand}}$, having no effect on the library’s behavior.

```
SHARE(m_L, m_R, U):
return POLY(m_R, t, U)
```

```
$\mathcal{L}_{\text{shamir-rand}}$:
POLY(m, t, U):
  if |U| >= t: return err
  for i \in U:
    y_i <- Z_p
    s_i := (i, y_i)
  return {s_i | i \in U}
```

The argument to poly has been changed from $m_L$ to $m_R$. This has no effect on the library’s behavior, since poly is actually ignoring its argument in these hybrids.

```
SHARE(m_L, m_R, U):
return POLY(m_R, t, U)
```

```
$\mathcal{L}_{\text{shamir-real}}$:
POLY(m, t, U):
  if |U| >= t: return err
  f_1, ..., f_{t-1} <- Z_p
  f(x) := m + \sum_{j=1}^{t-1} f_j x^j
  for i \in U:
    s_i := (i, f(i) % p)
  return {s_i | i \in U}
```

Applying the same steps in reverse, we can replace $\mathcal{L}_{\text{shamir-rand}}$ with $\mathcal{L}_{\text{shamir-real}}$, having no effect on the library’s behavior.

```
$\mathcal{L}_{\text{tss-R}}^{\mathcal{S}}$:
SHARE(m_L, m_R, U):
  if |U| >= t: return err
  f_1, ..., f_{t-1} <- Z_p
  f(x) := m_R + \sum_{j=1}^{t-1} f_j x^j
  for i \in U:
    s_i := (i, f(i) % p)
  return {s_i | i \in U}
```

A subroutine has been inlined, which has no effect on the library’s behavior. The resulting library is $\mathcal{L}_{\text{tss-R}}^{\mathcal{S}}$.

We showed that $\mathcal{L}_{\text{tss-L}}^{\mathcal{S}} = \mathcal{L}_{\text{hyb-1}} = \dots = \mathcal{L}_{\text{hyb-4}} = \mathcal{L}_{\text{tss-R}}^{\mathcal{S}}$, so Shamir’s secret sharing scheme is secure.

### 3.5 Visual Secret Sharing

Here is a fun variant of 2-out-of-2 secret-sharing called **visual secret sharing**. In this variant, both the secret and the shares are black-and-white images. We require the same security property as traditional secret-sharing — that is, a single share (image) by itself reveals no information about the secret (image). What makes visual secret sharing different is that we require the *reconstruction* procedure to be done visually.

More specifically, each share should be printed on transparent sheets. When the two shares are stacked on top of each other, the secret image is revealed visually. We will discuss a simple visual secret sharing scheme that is inspired by the following observations:

- when [icon] is stacked on top of [icon] the result is [icon]
- when [icon] is stacked on top of [icon] the result is [icon]
- when [icon] is stacked on top of [icon] the result is [icon]
- when [icon] is stacked on top of [icon] the result is [icon]

Importantly, when stacking shares on top of each other in the first two cases, the result is a 2 x 2 block that is half-black, half-white (let’s call it “gray”); while in the other cases the result is completely black.

The idea is to process each pixel of the source image independently, and to encode each pixel as a 2 x 2 block of pixels in each of the shares. A white pixel should be shared in

a way that the two shares stack to form a “gray” 2 x 2 block, while a black pixel is shared in a way that results in a black 2 x 2 block.

More formally:

```
Share(m):
initialize empty images s₁, s₂, with dimensions twice that of m
for each position (i, j) in m:
  randomly choose b₁ ← { { } }
  if m[i,j] is a white pixel: set b₂ := b₁
  if m[i,j] is a black pixel: set b₂ to the “opposite” of b₁ (i.e., { { } } \ {b₁})
  add 2 x 2 block b₁ to image s₁ at position (2i, 2j)
  add 2 x 2 block b₂ to image s₂ at position (2i, 2j)
return (s₁, s₂)
```

It is not hard to see that share $s_1$ leaks no information about the secret image $m$, because it consists of uniformly chosen 2 x 2 blocks. In the exercises you are asked to prove that $s_2$ also individually leaks nothing about the secret image.

Note that whenever the source pixel is white, the two shares have identical 2x2 blocks (so that when stacked, they make a “gray” block). Whenever a source pixel is black, the two shares have opposite blocks, so stack to make a black block.

### Example

![](img/da79fa21b263fe549aecaabd2a0a41c8_73_0.png)

### Exercises

- 3.1. Generalize Construction 3.5 to be an n-out-of-n secret-sharing scheme, and prove that your scheme is correct and secure.
- 3.2. Prove Theorem 3.7.
- 3.3. Fill in the details of the following alternative proof of Theorem 3.6: Starting with $\mathcal{L}_{\text{tss-L}}$, apply the first step of the proof as before, to duplicate the main body into 3 branches of a new if-statement. Then apply Exercise 2.3 to the second branch of the if-statement. Argue that $m_L$ can be replaced with $m_R$ and complete the proof.
