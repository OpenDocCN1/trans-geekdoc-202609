# 204 CHAPTER | 7 Other Financial Derivatives

# Simply Compounded Spot Rate

When simple compounding is $\Delta(t,T) = L(t,T)(T-t)$, where $L(t,T)$ is the simply compounded spot rate between time $t$ and $T$.

```
$$DF(t,T) = \{1 + L(t,T)(T-t)\} = 1$$
```

and so the simply compounded rate

```
$$L(t,T) = \frac{1}{T-t} \left\{ \frac{1}{DF(t,T)} - 1 \right\} \quad (7.2.4)$
```

# 7.2.1 Forward Rate Agreement

A forward rate agreement (FRA) is a contract between two counterparties (referred here as $A$ and $B$), in which one counterparty (say $A$) agrees to pay interest at the (variable) spot rate, while the other agrees to pay a fixed interest. The rate agreement starts at time $T_s$ and end at the maturity $T_m$, at which the counterparties settle the amount that is owed. If $P$ is the principal, then at time $T_m$, the contract has the following value to A:

```
$$V(T_m) = P \{(T_m-T_s)K - L(T_s,T_m)(T_m-T_s)\} \quad (7.2.5)$
```

where $K$ is the agreed fixed rate, and $L(T_s,T_m)$ is the simply compounded rate between times $T_s$ and $T_m$. From equation (7.2.4), we have

```
$$L(T_s,T_m) = \frac{1}{T_m-T_s} \left\{ \frac{1}{DF(T_s,T_m)} - 1 \right\\}$
```

so

```
$$V(T_m) = P \{(T_m-T_s)K - \frac{T_m-T_s}{DF(T_s,T_m)}\}\} \quad (7.2.6)$
```

The value of the FRA to A at time $t \le T_m$ is therefore $FRA(t,T_m) = DF(t,T_m)V(T_m)$ which means

```
$$FRA(t,T_m) = DF(t,T_m)P \left{(T_m-T_s)K - \frac{T_m-T_s}{DF(T_s,T_m)}ight\} \quad (7.2.7)$
```

Using $DF(t,T) = DF(t,T_m)DF(T_m,T)$, we can rewrite equation (7.2.7) as

```
$$FRA(t,T) = DF(t,T)P \left{(T_m-T_s)K - \frac{T_m-T_s}{DF(T_s,T_m)}ight\\} \quad (7.2.8)$
```

The value of $K$ which sets $FRA(t)$ to zero is the time $t$ forward rate between times $T_s$ and $T_m$, and it is denoted by $F(t,T_s,T_m)$. From equation (7.2.8),

```
$$F(t,T_s,T_m) = \frac{1}{T_m-T_s} \left\{ \frac{DF(t,T_s)}{DF(t,T_m)} - 1 \right\} \quad (7.2.9)$
```

Combining equation (7.2.8) and equation (7.2.10), we can express the value of the FRA as

```
$$FRA(t) = DF(t,T_m)P \tau \K - F(t,T_s,T_m)\} \quad (7.2.10)$
```

where $	au = T_m - T_s$ is known as the tenor of the FRA, and $T_s$ is the reset time for forward rate $F(t,T_s,T_s+	au)$.