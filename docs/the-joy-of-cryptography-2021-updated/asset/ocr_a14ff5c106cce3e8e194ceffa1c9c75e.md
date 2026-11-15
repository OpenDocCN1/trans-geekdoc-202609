return false, and so will the call to CHECKTAG(m, t) that we consider.

In both cases, the result of CHECKTAG(m, t) is true **if and only if** (m, t) ∈ T .

```
T := ∅
GETTAG(m):
  t := REVEAL(m)
  T := T ∪ {(m, t)}
  return t
CHECKTAG(m, t):
  return (m, t) ?∈ T
```

```
L_guess-R
T := empty assoc. array
GUESS(m, g):
  return g ?= T[m]
REVEAL(m):
  if T[m] undefined:
    T[m] <- {0, 1}^λ
    return T[m]
```

We have modified CHECKTAG according to the discussion above.

```
T := ∅
GETTAG(m):
  t := LOOKUP(m)
  T := T ∪ {(m, t)}
  return t
CHECKTAG(m, t):
  return (m, t) ?∈ T
```

```
L_prf-rand^F
T := empty assoc. array
LOOKUP(x):
  if T[x] undefined:
    T[x] <- {0, 1}^out
    return T[x]
```

In the previous hybrid, the guess subroutine is never called. Removing that unused subroutine and renaming REVEAL to LOOKUP results in the L_prf-ideal library from the PRF security definition.

```
T := ∅
GETTAG(m):
  t := LOOKUP(m)
  T := T ∪ {(m, t)}
  return t
CHECKTAG(m, t):
  return (m, t) ?∈ T
```

```
L_prf-real^F
k <- {0, 1}^λ
LOOKUP(x):
  return F(k, x)
```

We have applied the PRF security of F again, replacing L_prf-ideal with L_prf-real.

Inlining L_prf-real in the final hybrid, we see that the result is exactly L_mac-fake^F . Hence, we have shown that L_mac-real^F ≈ L_mac-fake^F , which completes the proof. 􀀀

# Discussion

If PRFs are MACs, why do we even need a definition for MACs? The simplest answer to this question is that the concepts of PRF and MAC are indeed different:

+   ► Not every PRF is a MAC. Only **sufficiently long random values are hard to guess**, so only PRFs with long outputs (out ≥ λ) are MACs. It is perfectly reasonable to consider a PRF with short outputs.