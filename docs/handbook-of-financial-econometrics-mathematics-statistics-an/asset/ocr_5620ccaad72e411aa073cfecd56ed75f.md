By a similar rule, we can use this tree to price a call option. At first, we can draw the option tree based on trinomial underlying asset price tree. The result is shown as follows:

![](bbox=[0.1, 0.25, 0.9, 0.7])

The call option value at time zero is 3.269028 in Cell C12. In addition, we also can write a function to price a call option based on trinomial tree model. The function is shown as follows:

```
' Returns Trinomial Option Value Function TriCall(S, X, r, q, T,
sigma, Nstep, lamda)
Dim dt, erdt, ermqdt, u, d, pu, pm, pd
Dim i As Integer, j As Integer
Dim vvec() As Variant
ReDim vvec(2 * Nstep)
dt = T / Nstep
erdt = Exp(r * dt)
ermqdt = Exp((r - q) * dt)
u = Exp(lamda * sigma * Sqr(dt))
d = 1 / u
pu = 1 / (2 * lamda ^ 2) + (r - sigma ^ 2 / 2) * Sqr(dt) / (2 * lamda * sigma)
pm = 1 - 1 / (lamda ^ 2)
pd = 1 - pu - pm
For i = 0 To 2 * Nstep
vvec(i) = Application.Max(S * (d ^ Nstep) * (u ^ i) - X, 0)
Next i
```