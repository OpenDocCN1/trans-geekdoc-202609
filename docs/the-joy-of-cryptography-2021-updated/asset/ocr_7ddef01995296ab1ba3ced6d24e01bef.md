Proof Let $\mathcal{S}$ denote the Shamir secret-sharing scheme. We prove that $\mathcal{L}_{\text{tss-L}}^{\mathcal{S}} \equiv \mathcal{L}_{\text{tss-R}}^{\mathcal{S}}$ via a hybrid argument.

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