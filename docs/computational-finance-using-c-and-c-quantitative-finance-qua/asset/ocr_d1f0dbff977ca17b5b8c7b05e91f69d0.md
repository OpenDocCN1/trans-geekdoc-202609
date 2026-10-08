# 84 Computational Finance Using C and C#

Private Sub MANY_EUROPEANS_Click()

```
Dim i As Long
Dim putcall, As Long
Dim S As Double
Dim q As Double
Dim sigma As Double
Dim T As Double
Dim r As Double

q = 0#
T = 1.5
sigma = 0.2

For i = 1 To 22

0 = Sheet1.Cells(i + 1, 1).value
X = Sheet1.Cells(i + 1, 2).value
putcall = Sheet1.Cells(i + 1, 3).value
Sheet1.Cells(i + 1, 4).value = bs_opt(S0, X, sigma, T, r, putcall)
Next
```

Code example 4.6 Visual Basic code uses the function bs_opt.

![](bbox=[0.118, 0.449, 0.882, 0.783])

Figure 4.2 Excel worksheet for calculation of the European option values.

When the button labelled “CALCULATE OPTIONS” is clicked, the values of 22 European options will be calculated using the data in columns 1–3 on worksheet 1, see Figs. 4.2 and 4.3.