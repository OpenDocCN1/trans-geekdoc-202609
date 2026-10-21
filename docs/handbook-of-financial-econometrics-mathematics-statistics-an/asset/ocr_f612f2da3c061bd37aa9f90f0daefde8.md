```
- 1).Address
    End If

End If
Me.BinomialCalc = Me.BinomialCalc + 1

End Sub Function BS_D1() As Double
Dim dblNumerator As Double
Dim dblDenominator As Double

On Error Resume Next
dblNumerator = VBA.Log(Me.txtBinomialS / Me.txtBinomialX) + _
    ((Me.txtBinomialr + Me.txtSigma ^ 2 / 2) * Me.txtTimeT)
dblDenominator = Me.txtSigma * Sqr(Me.txtTimeT)

BS_D1 = dblNumerator / dblDenominator

End Function Function BS_D2() As Double

On Error Resume Next
BS_D2 = BS_D1 - (Me.txtSigma * VBA.Sqr(Me.txtTimeT))

End Function Function BS_Call() As Double

BS_Call = (Me.txtBinomialS * WorksheetFunction.NormSDist(BS_D1)) - _
    - Me.txtBinomialX * Exp(-Me.txtBinomialr * Me.txtTimeT) * _
    WorksheetFunction.NormSDist(BS_D2)

End Function 'Used put-call parity theorem to price put option
Function BS_PUT() As Double

BS_PUT = BS_Call - Me.txtBinomialS + _
    (Me.txtBinomialX * Exp(-Me.txtBinomialr * Me.txtTimeT))

End Function
```