
```vb
'/***************************************************************************
'      Relationship Between the Binomial OPM and Black-Scholes OPM
'      Decision Tree and Microsoft Excel Approach
'      by John Lee
'      JohnLeeExcelVBA@gmail.com
'      All Rights Reserved
'/***************************************************************************
Option Explicit

Dim mwbTreeWorkbook As Workbook
Dim mwsTreeWorksheet As Worksheet
Dim mwsCallTree As Worksheet
Dim mwsPutTree As Worksheet
Dim mwsBondTree As Worksheet
Dim mdbIPFactor As Double
Dim mBinomialCalc As Long
Dim mCallPrice As Double   'jcl 12/8/2008
Dim mPutPrice As Double   'jcl 12/8/2008

' /****************************** */
' Purpose: Keep track the numbers of binomial calc
' /****************************** */
Property Let BinomialCalc(l As Long)
    mBinomialCalc = l
End Property

Property Get BinomialCalc() As Long
    BinomialCalc = mBinomialCalc
End Property

Property Set TreeWorkbook(wb As Workbook)
    Set mwbTreeWorkbook = wb
End Property

Property Get TreeWorkbook() As Workbook
    Set TreeWorkbook = mwbTreeWorkbook
End Property

Property Set TreeWorksheet(ws As Worksheet)
    Set mwsTreeWorksheet = ws
End Property

Property Get TreeWorksheet() As Worksheet
    Set TreeWorksheet = mwsTreeWorksheet
End Property

Property Set CallTree(ws As Worksheet)
    Set mwsCallTree = ws
End Property

Property Get CallTree() As Worksheet
    Set CallTree = mwsCallTree
End Property

Property Set PutTree(ws As Worksheet)
    Set mwsPutTree = ws
End Property

Property Get PutTree() As Worksheet
    Set PutTree = mwsPutTree
End Property

Property Set BondTree(ws As Worksheet)
    Set mwsBondTree = ws
End Property

Property Get BondTree() As Worksheet
    Set BondTree = mwsBondTree
End Property

Property Let CallPrice(dCallPrice As Double)
    '12/8/2008
    mCallPrice = dCallPrice
End Property

Property Get CallPrice() As Double
    Let CallPrice = mCallPrice
End Property

Property Let PutPrice(dPutPrice As Double)
    '12/10/2008
    mPutPrice = dPutPrice
End Property

Property Get PutPrice() As Double
    '12/10/2008
    Let PutPrice = mPutPrice
End Property

Property Let PFactor(r As Double)
    Dim dRate As Double

    dRate = ((1 + r) - Me.txtBinomialD) / (Me.txtBinomialU - Me.txtBinomialD)

    Let mdbIPFactor = dRate
End Property

Property Get PFactor() As Double
    Let PFactor = mdbIPFactor
End Property

Property Get qU() As Double
    Dim dblDeltaT As Double
    Dim dblDown As Double
    Dim dblUp As Double
    Dim dblR As Double

    dblDeltaT = Me.txtTimeT / Me.txtBinomialN
    dblR = Exp(Me.txtBinomialR * dblDeltaT)
    dblUp = Exp(Me.txtSigma * VBA.Sqr(dblDeltaT))
    dblDown = Exp(-Me.txtSigma * VBA.Sqr(dblDeltaT))

    qU = (dblR - dblDown) / (dblR * (dblUp - dblDown))
End Property

Property Get qD() As Double
    Dim dblDeltaT As Double
    Dim dblDown As Double
    Dim dblUp As Double
    Dim dblR As Double

    dblDeltaT = Me.txtTimeT / Me.txtBinomialN
    dblR = Exp(Me.txtBinomialR * dblDeltaT)
    dblUp = Exp(Me.txtSigma * VBA.Sqr(dblDeltaT))
    dblDown = Exp(-Me.txtSigma * VBA.Sqr(dblDeltaT))

    qD = (dblUp - dblR) / (dblR * (dblUp - dblDown))
End Property

Private Sub chkBinomialBSApproximation_Click()
    On Error Resume Next
    'Time and Sigma only BlackScholes parameter
    Me.txtTimeT.Visible = Me.chkBinomialBSApproximation
    Me.lblTimeT.Visible = Me.chkBinomialBSApproximation
    Me.txtSigma.Visible = Me.chkBinomialBSApproximation
    Me.lblSigma.Visible = Me.chkBinomialBSApproximation
    txtTimeT_Change
End Sub

Private Sub cmdCalculate_Click()
    Me.Hide
    BinomialOption
    Unload Me
End Sub

Private Sub cmdCancel_Click()
    Unload Me
End Sub

Private Sub txtBinomialN_Change()
    'jcl 12/8/2008
    On Error Resume Next
    If Me.chkBinomialBSApproximation Then
        Me.txtBinomialU = Exp(Me.txtSigma * Sqr(Me.txtTimeT / Me.txtBinomialN))
        Me.txtBinomialD = Exp(-Me.txtSigma * Sqr(Me.txtTimeT / Me.txtBinomialN))
    End If
End Sub

Private Sub txtTimeT_Change()
    'jcl 12/8/2008
    On Error Resume Next
    If Me.chkBinomialBSApproximation Then
        Me.txtBinomialU = Exp(Me.txtSigma * Sqr(Me.txtTimeT / Me.txtBinomialN))
        Me.txtBinomialD = Exp(-Me.txtSigma * Sqr(Me.txtTimeT / Me.txtBinomialN))
    End If
End Sub

Private Sub UserForm_Initialize()
    With Me
        .txtBinomialS = 20
        .txtBinomialX = 20
        .txtBinomialD = 0.95
        .txtBinomialU = 1.05
        .txtBinomialN = 4
        .txtBinomialR = 0.03
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
        .PFactor = Me.txtBinomialR
        .CallTree.Name = "Call Option Price"
        .PutTree.Name = "Put Option Price"
        .TreeWorksheet.Name = "Stock Price"
        .BondTree.Name = "Bond"
    End With

    DecisionTree rCell:=rColumn, nPeriod:=Me.txtBinomialN + 1, _
                 dblPrice:=Me.txtBinomialS, sngU:=Me.txtBinomialU, _
                 sngD:=Me.txtBinomialD

    DecisionTreeFormat

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
            ws.UsedRange.NumberFormat = "#,##0.0000_);(#,##0.0000)"
        End If
    Next
    Application.DisplayAlerts = True
    Me.TreeWorksheet.Activate
End Sub

Sub TreeTitle(wsTree As Worksheet, sTitle As String)
    wsTree.Range("A1:A5").EntireRow.Insert (xlShiftDown)

    With wsTree
        With .Cells(1)
            .Value = sTitle
            .Font.Size = 20
            .Font.Italic = True
        End With
        With .Cells(2, 1)
            .Value = "Decision Tree"
            .Font.Size = 16
            .Font.Italic = True
        End With
        With .Cells(3, 1)
            .Value = "Price = " & Me.txtBinomialS & _
                     ",Exercise = " & Me.txtBinomialX & _
                     ",U = " & Format(Me.txtBinomialU, "#,##0.0000") & _
                     ",D = " & Format(Me.txtBinomialD, "#,##0.0000") & _
                     ",N = " & Me.txtBinomialN & _
                     ",R = " & Me.txtBinomialR
            .Font.Size = 14
        End With
        With .Cells(4, 1)
            .Value = "Number of calculations: " & Me.BinomialCalc
            .Font.Size = 14
        End With

        If wsTree Is Me.CallTree Then
            With .Cells(5, 1)
                .Value = "Binomial Call Price= " & Format(Me.CallPrice, "#,##0.0000")
                .Font.Size = 14
            End With

            If Me.chkBinomialBSApproximation Then
                wsTree.Range("A6:A7").EntireRow.Insert (xlShiftDown)

                With .Cells(6, 1)
                    .Value = "Black-Scholes Call Price= " & Format(Me.BS_Call, "#,##0.0000") & _
                             ",d1= " & Format(Me.BS_D1, "#,##0.0000") & _
                             ",d2= " & Format(Me.BS_D2, "#,##0.0000") & _
                             ",N(d1)= " & Format(WorksheetFunction.NormSDist(BS_D1), "#,##0.0000") & _
                             ",N(d2)= " & Format(WorksheetFunction.NormSDist(BS_D2), "#,##0.0000")
                    .Font.Size = 14
                End With
            End If
        ElseIf wsTree Is Me.PutTree Then
            With .Cells(5, 1)
                .Value = "Binomial Put Price: " & Format(Me.PutPrice, "#,##0.0000")
                .Font.Size = 14
            End With

            If Me.chkBinomialBSApproximation Then
                wsTree.Range("A6:A7").EntireRow.Insert (xlShiftDown)

                With .Cells(6, 1)
                    .Value = "Black-Scholes Put Price: " & Format(Me.BS_PUT, "#,##0.0000")
                    .Font.Size = 14
                End With
            End If
        End If
    End With
End Sub

Sub BondDecisionTree(rPrice As Range, arCell As Variant, _
                     iCount As Long)
    Dim rBond As Range
    Dim rPup As Range
    Dim rPDown As Range

    Set rBond = Me.BondTree.Cells(rPrice.Row, rPrice.Column)
    Set rPup = Me.BondTree.Cells(arCell(iCount - 1).Row, arCell(iCount - 1).Column)
```
