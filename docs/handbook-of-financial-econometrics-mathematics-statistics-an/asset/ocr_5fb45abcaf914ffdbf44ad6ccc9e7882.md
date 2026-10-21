```
With Me

.txtBinomialS = 20
.txtBinomialX = 20
.txtBinomialD = 0.95
.txtBinomialU = 1.05
.txtBinomialN = 4
.txtBinomialr = 0.03
.txtSigma = 0.2
.txtTimeT = 4

Me.chkBinomialBSApproximation = False
End With

chkBinomialBSApproximation_Click
Me.Hide
End Sub

Sub BinomialOption()
Dim wbTree As Workbook
Dim wsTree As Worksheet
Dim rColumn As Range
Dim ws As Worksheet

Set Me.TreeWorkbook = Workbooks.Add
Set Me.BondTree = Me.TreeWorkbook.Worksheets.Add
Set Me.PutTree = Me.TreeWorkbook.Worksheets.Add
Set Me.CallTree = Me.TreeWorkbook.Worksheets.Add
Set Me.TreeWorksheet = Me.TreeWorkbook.Worksheets.Add

Set rColumn = Me.TreeWorksheet.Range("a1")

With Me
.BinomialCalc = 0
.PFactor = Me.txtBinomialr
.CallTree.Name = "Call Option Price"
.PutTree.Name = "Put Option Price"
.TreeWorksheet.Name = "Stock Price"
.BondTree.Name = "Bond"
End With

DecisionTree rCell:=rColumn, nPeriod:=Me.txtBinomialN + 1, _
dblPrice:=Me.txtBinomialS, sngU:=Me.txtBinomialU, _
sngD:=Me.txtBinomialD

DecitionTreeFormat

TreeTitle wsTree:=Me.TreeWorksheet, sTitle:="Stock Price "
TreeTitle wsTree:=Me.CallTree, sTitle:="Call Option Pricing"
TreeTitle wsTree:=Me.PutTree, sTitle:="Put Option Pricing"
TreeTitle wsTree:=Me.BondTree, sTitle:="Bond Pricing"

Application.DisplayAlerts = False
For Each ws In Me.TreeWorkbook.Worksheets
If Left(ws.Name, 5) = "Sheet" Then
ws.Delete
Else
ws.Activate
ActiveWindow.DisplayGridlines = False
ws.UsedRange.NumberFormat = "#,##0.0000_;(C#,##0.0000)"
End If
Next
Application.DisplayAlerts = True
Me.TreeWorksheet.Activate
End Sub
Sub TreeTitle(wsTree As Worksheet, sTitle As String)
wsTree.Range("A1:A5").EntireRow.Insert (xIShiftDown)
```