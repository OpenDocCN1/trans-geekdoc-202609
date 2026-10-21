![](bbox=[0.09, 0.09, 0.9, 0.46])

We use bisection method to write a function to calculate the implied volatility of CEV model. Following code can accomplish this task.

```
' Estimate implied volatility by Bisection
' Uses BSCall fn
Function CEVIVBisection(S, X, r, q, T, alpha, callprice, a, b)
    Dim yb, ya, c, yc
    yb = CEVCall(S, X, r, q, T, b, alpha) - callprice
    ya = CEVCall(S, X, r, q, T, a, alpha) - callprice
    If yb * ya > 0 Then
        CEVIVBisection = CVErr(xlErrValue)
    Else
        Do While Abs(a - b) > 0.000000001
```