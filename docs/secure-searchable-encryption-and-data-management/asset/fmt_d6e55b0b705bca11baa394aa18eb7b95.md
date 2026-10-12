
**Proof**: Let `r[1]`, `r[2]`, …, `r[φ(m)]` be a reduced residue system modulo `m`. Then `a*r[1]`, `a*r[2]`, …, `a*r[φ(m)]` is also a reduced residue system modulo `m`, since `(a,m) = 1` and `(r[i],m) = 1`, which implies `(a*r[i],m) = 1`. Therefore, corresponding to each `r[i]`, there is one and only one `a*r[j]` such that `a*r[j] ≡ r[i] (mod m)`. Multiply all such `φ(m)` relations:

```
∏(j=1 to φ(m)) a*r[j] ≡ ∏(i=1 to φ(m)) r[i] (mod m) = a^φ(m) ≡ 1 (mod m)
```

### 1.1.5 Congruence solutions

Let `m[1]`, `m[2]`, … `m[r]` be pairwise relatively prime positive integers. We want to find the solution of the following system: `x ≡ a[1] (mod m[1])`, `x ≡ a[2] (mod m[2])`, …, `x ≡ a[r] (mod m[r])`. One method to find the solution of such equations is by the Chinese remainder theorem (CRT).

The CRT theorem states that the solution of such system exists if `(m[i],m[j]) = 1, ∀ i ≠ j`.

**Proof**: Let `m = m[1] ⋅ m[2] ⋅ … ⋅ m[r]`, then `(m/m[j], m[j]) = 1`. Let `R(m[j])` represents the reduced residue modulo `m`, which contains set of all elements relatively prime to `m[j]`. Therefore, `∀ a ∈ R(m[j]), ∃ x ∈ R(m[j]) : a*x ≡ 1 (mod m[j])`, which implies, `∃ b[j] ∈ R(m[j]) : (m/m[j]) * b[j] ≡ 1 (mod m[j])`. Let `x[0]` be the one solution, then `x[0] = ∑(j=1 to r) ((m/m[j]) ⋅ b[j] ⋅ a[j] mod m[j])` because `((m/m[j]) ⋅ b[j] ⋅ a[j]) ≡ a[j] (mod m[j])`.

### 1.1.6 Quadratic residues

If `p` is an odd prime and `a` is an integer relatively prime to `p` then is "a" a perfect square modulo `p`? Finding quadratic residues provides the answer to this question. If `m` is a positive integer, we say integer "a" is a quadratic residue of `m` if `gcd(a,m) = 1` and the congruence `x² ≡ a (mod m)` has a solution. If `x² ≡ a (mod m)` has no solution then "a" is a quadratic non-residue of `m` [[2]](#01chap_01.xhtml#ref1_2), [[3]](#01chap_01.xhtml#ref1_3).

**Example**: Determine which integers are quadratic residues of 11.

*   **Step 1**: Since `m = 11` is a prime number then `{1,2,…10}` are relatively prime to `m`.
*   **Step 2**: Compute the squares of integers `{1,2,…10}`: `1² ≡ 10² ≡ 1 (mod 11)`, `2² ≡ 9² ≡ 4 (mod 11)`, `3² ≡ 8² ≡ 9 (mod 11)`, `4² ≡ 7² ≡ 5 (mod 11)`, `5² ≡ 6² ≡ 3 (mod 11)`.
*   **Quadratic residues**: 1, 3, 4, 5, 9. **Quadratic non-residues**: 2, 6, 7, 8, 10.

**Conclusion**: Given any fixed positive integer `m`, it is possible to determine the quadratic residue by simply listing the positive integers less than and prime to `m`, squaring them and reducing `mod m`.

**Lemma**: If `p` is an odd prime and `a` is an integer relatively prime to `p` then the congruence `x² ≡ a (mod m)` has either no solution or exactly two incongruent solutions modulo `p`.

**Proof**: If `x² ≡ a (mod p)` has a solution, say `x = x[0]`, then we can easily demonstrate that `x = -x[0]` is the second incongruent solution because `(-x[0])² = x[0]² ≡ a (mod p)`.

**Note**: `x[0] ≢ -x[0] (mod p)` ( `2*x[0] ≡ 0 (mod p)`, which is impossible because `p | x[0]`).

Now we have to show that there are no more than two incongruent solutions. Assume `x = x[0]` and `x = x[1]` are both solutions of `x² ≡ a (mod p)`. `x[0]² ≡ a (mod p)` and `x[1]² ≡ a (mod p)` then `x[0]² - x[1]² ≡ 0 (mod p)`. `(x[0]+x[1])(x[0]-x[1]) ≡ 0 (mod p)` i.e. `p | (x[0]+x[1])` or `p | (x[0]-x[1])`. `x[1] ≡ -x[0] (mod p)` or `x[1] ≡ x[0] (mod p)`.

**Theorem**: If `p` is an odd prime then there are exactly `(p - 1)/2` quadratic residues of `p` and `(p - 1)/2` quadratic non-residues of `p`.

**Proof**: Consider all the squares of integers `{1,2,…p−1}`. We know `x² ≡ (p-x)² ≡ a (mod p)`. Let `1 < b < p - 1`. `(p-b)² ≡ b² (mod p)`.

```
1², 2², …, ((p - 1)/2)² ≡ ((p + 1)/2)², …, (p - 2)², (p - 1)²
```

(1.6)

Since `1² ≡ (p-1)² (mod p)` and similarly the same relation can be set among other elements of equation (1.6). Therefore, `1², 2², …, ((p - 1)/2)²` are all distinct.

#### 1.1.6.1 Euler's criterion

Euler's criterion tells us precisely when an integer `a` is a quadratic residue modulo an odd prime `p`. Let `p` be odd prime and `gcd(a,p) = 1`. Then `a` is a quadratic residue modulo `p` if and only if `a^((p - 1)/2) ≡ 1 (mod p)`.

**Proof**: Let `a` be the quadratic residue then `x² ≡ a (mod p)`. `(x²)^((p - 1)/2) ≡ a^((p - 1)/2) (mod p)`. `x^(p - 1) ≡ a^((p - 1)/2) (mod p)`. By Fermat's little theorem, `x^(p-1) ≡ 1 (mod p)`, therefore, `a^((p - 1)/2) ≡ 1 (mod p)`.

**Conversely**: Given `a^((p - 1)/2) ≡ 1 (mod p)`. To prove: "a" is a quadratic residue modulo an odd prime `p`.

**Proof**: We know that there exists a primitive root `g` modulo `p`, such that any integer in `ℤ[p]` can be expressed as `g^(i) (mod p)`, `1 ≤ i ≤ p - 1` and `g^(m) ≡ 1 (mod p)` holds only when `p-1 | m` ( `m=0` or `p-1`). For some `1 ≤ i ≤ p - 1` we have `a ≡ g^(i) (mod p)`. `g^(i((p - 1)/2)) ≡ a^((p - 1)/2) ≡ 1 (mod p)` (Given). By the property of primitive root `p - 1 | i((p - 1)/2)`; therefore, `i` must be even say, `i = 2j` which implies `a ≡ g^(2j) (mod p)`, `a ≡ (g^(j))² (mod p)`. Hence, `a` is a quadratic residue modulo an odd prime `p`.

### 1.1.7 Legendre symbol

It is a convenient notation to indicate whether an integer `a` is a quadratic residue modulo an odd prime `p`. Legendre symbol of `a (mod p)` is denoted as `(a/p)`. Formally, it is defined as:

```
( a/p ) = {  1,  if a is a non-zero quadratic residue modulo p
           { -1,  if a is a non-zero quadratic non-residue modulo p
           {  0,  if p | a
```

(1.7)

Example: `(2/7) = 1`, `(2/5) = -1`, `(12/5) = -1`, `(101/97) = 1`, `(97/101) = 1`.

If `p` divide `a` with remainder, i.e. `a = q*p + r` then `(a/p) = (r/p)`. By Euler's criterion, `a^((p - 1)/2) ≡ (a/p) (mod p)`.

#### 1.1.7.1 Law of quadratic reciprocity

The law of quadratic reciprocity relates the two Legendre symbols `(p/q)` and `(q/p)` where `p` and `q` are odd primes:

```
( p/q ) ( q/p ) = (-1)^(((p - 1)/2) * ((q - 1)/2))
```

(1.8)
