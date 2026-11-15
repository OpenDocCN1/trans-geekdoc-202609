```
S := ∅; // R := ∅
T, T_inv := empty assoc. arrays

CTXT(m):
  // r ← {0, 1}^λ \ R
  c ← {0, 1}^blen
  // R := R ∪ {r}
  S := S ∪ {c}
  return c

DECRYPT(c ∈ Σ.C):
  if c ∈ S return err
  if T_inv[c] undefined:
    m||r ← {0, 1}^blen
    T_inv[c] := m||r; T[m||r] := c
  // R := R ∪ {r}
  return first n bits of T_inv[c]
```

Consider all the ways that R is used in the previous hybrid. The first line of ct×t uses R to sample r, but then r is subsequently used only to further update R and nowhere else. Both subroutines use R only to update the value of R. It has no effect to simply remove all lines that refer to variable R.

```
S := ∅
T, T_inv := empty assoc. arrays

CTXT(m):
  c ← {0, 1}^blen
  S := S ∪ {c}
  return c

DECRYPT(c ∈ Σ.C):
  if c ∈ S return err
  if T_inv[c] undefined:
    m||r ← {0, 1}^blen
    T_inv[c] := m||r; T[m||r] := c
  return first n bits of T_inv[c]
```

We have applied Lemma 4.12 to the sampling step in decrypt. The standard intermediate steps have been skipped. Now the second if-statement in decrypt exactly matches L_sprp-rand.

```
L^Σ_cca$-rand:
k ← {0, 1}^λ
S := ∅

CTXT(m):
  c ← {0, 1}^blen
  S := S ∪ {c}
  return c

DECRYPT(c ∈ Σ.C):
  if c ∈ S return err
  return first n bits of F^-1(k, c)
```

We have applied the strong PRP security of F to replace L_sprp-rand with L_sprp-real. The standard intermediate steps have been skipped. The result is L_cca$-real.