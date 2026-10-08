# European options

```
Function bs_opt(S0 As Double,
ByVal X As Double, sigma As Double, T As Double,
r As Double, q As Double, ByVal putcall As Long) As Double
```

* Visual Basic Routine to calculate the value of
either a European Put or European Call option.
* Author: George Levy

```
Dim temp As Double
Dim d1 As Double
Dim d2 As Double
Dim value As Double
```

```
temp = Log (S0 / X) + (r - q + (sigma * sigma / 2)) * T
d1 = temp / (sigma * Sqrt (T))
d2 = d1 - sigma * Sqrt (T)
```

```
If (putcall = 0) Then ' a call option
value = S0 * Exp(-q * T) * Worksheet.NormDist(d1, 0, 1, True)
- Worksheet.NormDist(d2, 0, 1, True) * X * Exp(-r * T)
```

```
Else a put option
value = -S0 * Exp(-q * T) * Worksheet.NormDist(-d1, 0, 1, True) +
- X * Worksheet.NormDist(-d2, 0, 1, True) * Exp(-r * T)
```

```
End If
End Function
```

```
bs_opt = value
```

# Code 4.5 Visual Basic code to price European options using the Black-Scholes formula.

![](bbox=[0.137, 0.528, 0.862, 0.87])

Figure 4.1 Using the function bs_opt interactively within Excel. S = 10.0, X = 9.0, q = 0.0, T = 1.5, r = 0.1, and sigma = 0.2.