The $h$th hybrid library in the sequence is defined as:

```
L_hyb-h
count := 0
T := empty assoc. array
GUESS(m, g):
  count := count + 1
  if T[m] undefined and count > h :
    T[m] <- {0, 1}^lambda
    return g ?= T[m]
  // returns false if T[m] undefined
REVEAL(m):
  if T[m] undefined:
    T[m] <- {0, 1}^lambda
  return T[m]
```

This hybrid library behaves like L_guess-R for the first h queries to GUESS, in the sense that it will always just return false when T[m] is undefined. After h queries, it will behave like L_guess-L by actually sampling T[m] in these cases.

In L_hyb-0, the clause “count > 0” is always true so this clause can be removed from the if-condition. This modification results in L_guess-L, so we have L_guess-L ≡ L_hyb-0.

In L_hyb-q, the clause “count > q” in the if-statement is always false since the calling program makes only q queries. Removing the unreachable if-statement it results in L_guess-R, so we have L_guess-R ≡ L_hyb-q.

It remains to show that L_hyb-h ≈ L_hyb-(h + 1) for all h. We can do so by rewriting these two libraries as follows:

```
L_hyb-h
count := 0
T := empty assoc. array
GUESS(m, g):
  count := count + 1
  if T[m] undefined and count > h :
    T[m] <- {0, 1}^lambda
    if g = T[m] and count = h + 1:
      bad := 1
  return g ?= T[m]
  // returns false if T[m] undefined
REVEAL(m):
  if T[m] undefined:
    T[m] <- {0, 1}^lambda
  return T[m]
```

```
L_hyb-(h + 1)
count := 0
T := empty assoc. array
GUESS(m, g):
  count := count + 1
  if T[m] undefined and count > h :
    T[m] <- {0, 1}^lambda
    if g = T[m] and count = h + 1:
      bad := 1; return false
  return g ?= T[m]
  // returns false if T[m] undefined
REVEAL(m):
  if T[m] undefined:
    T[m] <- {0, 1}^lambda
  return T[m]
```