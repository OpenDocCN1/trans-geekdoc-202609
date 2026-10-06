# 206 CHAPTER | 7 Other Financial Derivatives

where

```
$F(t_i, t_{i-1}, t_{i-1} + \tau_i) = \left\{ \frac{DF(t_i, t_{i-1})}{DF(t_i, t_{i-1} + \tau_i)} - 1 \right\} \frac{1}{\tau_i}$$
```

From equation (7.12.14), we thus have

```
$FLT(t) = \sum_{i=k+1}^{n} C_i DF(t, t_i)\n$= P \sum_{i=k+1}^{n} DF(t_i, t_i) \tau_i \left\{ \frac{DF(t_i, t_{i-1})}{DF(t_i, t_i)} - 1 \right\} \frac{1}{\tau_i}\n$= P \left\{ DF(t, t_k) - DF(t, t_{k+1}) + DF(t, t_{k+1}) \dots \right\$\n$-DF(t, t_i) + DF(t, t_i) \dots - DF(t, t_n) \right$\n$= P \left\{ DF(t, t_k) - DF(t, t_n) \right\}$
```

and so the value of the floating leg is

```
$FLT(t) = P \left\{ DF(t, t_k) - DF(t, t_n) \right\}. \quad (7.12.15)$
```

# The Swap Rate

The time $t$ swap rate $SR_t$ is the value of the fixed rate $K$ which makes the $IRS(t)$ zero. Thus, from equations (7.12.12)-(7.12.14),

```
$P \left\{ DF(t, t_k) - DF(t, t_n) \right\} - C DF(t, t_k) = P SR_t \sum_{i=k+1}^{n} DF(t_i, t_i) \tau_i, \quad (7.12.16)$
```

so

```
$SR_t = \frac{\left\{ DF(t, t_k) - DF(t, t_n) \right\} - \frac{C}{P} DF(t, t_k)}{\sum_{i=k+1}^{n} DF(t_i, t_i) \tau_i} \quad (7.12.17)$
```

# Amortisation

So far we have assumed that the principal is fixed and set to the value $P$. We will now deal with the situation the principal varies with time according to the following amortization schedule:

```
$AM_i = P_{i-1} - P_i, \quad i = 0, \dots, n-1, \quad (7.12.18)$
```

where $P_i$ is the value of the principal at time $t_i$ and $P_0 = P$. The value of the floating leg is computed as

```
$FLT(t) = \sum_{i=k+1}^{n} P_{i-1} DF(t, t_i) \tau_i \left\{ \frac{DF(t_i, t_{i-1})}{DF(t_i, t_i)} - 1 \right\} \frac{1}{\tau_i}$
```