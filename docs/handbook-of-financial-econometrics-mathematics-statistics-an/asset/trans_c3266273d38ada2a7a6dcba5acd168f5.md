
.Value = WorksheetFunction.Max(arCell(iCount - 1) - Me.txtBinomialX, 0)
.Borders(xlBottom).LineStyle = xlContinuous
End With
With rCDown
    .Value = WorksheetFunction.Max(arCell(iCount) - Me.txtBinomialX, 0)
    .Borders(xlBottom).LineStyle = xlContinuous
End With
End If

With rCall
    If Not Me.chkBinomialBSApproximation Then
        .Value = (Me.PFactor * rCup + (1 - Me.PFactor) * rCDown) / (1 + Me.txtBinomialr)
    Else
        .Value = (Me.qU * rCup) + (Me.qD * rCDown)
    End If

Me.CallPrice = .Value   '12/8/2008

    .Borders(xlBottom).LineStyle = xlContinuous
End With

rCup.Offset(1, 0).Resize((rCDown.Row - rCup.Row), 1). _
    Borders(xlEdgeLeft).LineStyle = xlContinuous

End Sub

Sub DecisionTreeFormat()
Dim rTree As Range
Dim nColumns As Integer
Dim rLast As Range
Dim rCell As Range
Dim iCount As Long
Dim lCellSize As Long
Dim vntColumn As Variant
Dim iCount As Long
Dim iTimes As Long
Dim arCell() As Range
Dim sFormatColumn As String
Dim rPrice As Range

Application.StatusBar = "Formatting Tree.. "
Set rTree = Me.TreeWorksheet.UsedRange
nColumns = rTree.Columns.Count

Set rLast = rTree.Columns(nColumns).EntireColumn.SpecialCells(xlCellTypeConstants, 23)
lCellSize = rLast.Cells.Count
For iCount = nColumns To 2 Step -1
sFormatColumn = rLast.Parent.Columns(iCount).EntireColumn.Address
Application.StatusBar = "Formatting column " & sFormatColumn
ReDim vntColumn(1 To (rLast.Cells.Count / 2), 1)

Application.StatusBar = "Assigning values to array for column " & _
rLast.Parent.Columns(iCount).EntireColumn.Address
vntColumn = rLast.Offset(0, -1).EntireColumn.Cells(1).Resize(rLast.Cells.Count / 2, 1)
rLast.Offset(0, -1).EntireColumn.ClearContents

ReDim arCell(1 To rLast.Cells.Count)
lTimes = 1
Application.StatusBar = "Assigning cells to arrays. Total number of cells: " & lCellSize
For Each rCell In rLast.Cells
Application.StatusBar = "Array to column " & sFormatColumn & " Cells " & rCell.Row
Set arCell(iTimes) = rCell
lTimes = lTimes + 1
Next

lTimes = 1
Application.StatusBar = "Formatting leaves for column " & sFormatColumn
For iCount = 2 To lCellSize Step 2
    Application.StatusBar = "Formatting leaves for cell " & arCell(iCount).Address
    If rLast.Cells.Count <> 2 Then
        Set rPrice = arCell(iCount).Offset(-1 * ((arCell(iCount).Row - arCell(iCount - 1).Row) / 2), -1)
        rPrice.Value = vntColumn(lTimes, 1)
    Else
        Set rPrice = arCell(iCount).Offset(-1 * ((arCell(iCount).Row - arCell(iCount - 1).Row) / 2), -1)
        rPrice.Value = vntColumn
    End If
    arCell(iCount).Borders(xlBottom).LineStyle = xlContinuous
    With arCell(iCount - 1)
        .Borders(xlBottom).LineStyle = xlContinuous
        .Offset(1, 0).Resize((arCell(iCount).Row - arCell(iCount - 1).Row), 1). _
        Borders(xlEdgeLeft).LineStyle = xlContinuous
    End With
    lTimes = 1 + lTimes
    CallDecisionTree rPrice:=rPrice, arCell:=arCell, iCount:=iCount
    PutDecisionTree rPrice:=rPrice, arCell:=arCell, iCount:=iCount
    BondDecisionTree rPrice:=rPrice, arCell:=arCell, iCount:=iCount
Next
    Set rLast = rTree.Columns(iCount - 1).EntireColumn.SpecialCells(xlCellTypeConstants, 23)
    lCellSize = rLast.Cells.Count
Next ' / outer next
rLast.Borders(xlBottom).LineStyle = xlContinuous
Application.StatusBar = False
End Sub

'/* ***********************************************************
'/Purpose: To calculate the price value of every state of the
'binomial // decision tree
'/* ***********************************************************
Sub DecisionTree(rCell As Range, nPeriod As Integer, _
dblPrice As Double, sngU As Single, sngD As Single)
Dim lIteminColumn As Long
    If Not nPeriod = 1 Then
        'Do Up
        DecisionTree rCell:=rCell.Offset(0, 1), nPeriod:=nPeriod - 1, _
            dblPrice:=dblPrice * sngU, sngU:=sngU, _
            sngD:=sngD
        'Do Down
        DecisionTree rCell:=rCell.Offset(0, 1), nPeriod:=nPeriod - 1, _
            dblPrice:=dblPrice * sngD, sngU:=sngU, _
            sngD:=sngD
    End If
    lIteminColumn = WorksheetFunction.CountA(rCell.EntireColumn)
    If lIteminColumn = 0 Then
        rCell = dblPrice
    Else
        If nPeriod <> 1 Then
            rCell.EntireColumn.Cells(lIteminColumn + 1) = dblPrice
        Else
            rCell.EntireColumn.Cells(((lIteminColumn + 1) * 2) - 1) = dblPrice
            Application.StatusBar = "The number of binomial calcs are : " & Me.BinomialCalc _
& " at cell " & rCell.EntireColumn.Cells(((lIteminColumn + 1) * 2) - 1).Address
    End If

End If
Me.BinomialCalc = Me.BinomialCalc + 1

End Sub
Function BS_D1() As Double
Dim dblNumerator As Double
Dim dblDenominator As Double

On Error Resume Next
dblNumerator = VBA.Log(Me.txtBinomialS / Me.txtBinomialX) + _
    ((Me.txtBinomialr + Me.txtSigma ^ 2 / 2) * Me.txtTimeT)
dblDenominator = Me.txtSigma * Sqr(Me.txtTimeT)

BS_D1 = dblNumerator / dblDenominator

End Function
Function BS_D2() As Double

On Error Resume Next
BS_D2 = BS_D1 - (Me.txtSigma * VBA.Sqr(Me.txtTimeT))

End Function
Function BS_Call() As Double

BS_Call = (Me.txtBinomialS * WorksheetFunction.NormSDist(BS_D1)) - _
    Me.txtBinomialX * Exp(-Me.txtBinomialr * Me.txtTimeT) * _
    WorksheetFunction.NormSDist(BS_D2)

End Function
'Used put-call parity theorem to price put option
Function BS_PUT() As Double

BS_PUT = BS_Call - Me.txtBinomialS + _
    (Me.txtBinomialX * Exp(-Me.txtBinomialr * Me.txtTimeT))

End Function

本页特意留空

## 第85章

## 统计分布、欧式期权、美式期权和期权定价界限

Cheng Few Lee

## 目录

- 85.1 引言 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2930
- 85.2 正态分布 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2931
- 85.3 对数正态分布 . . . . . . . . . . . . . . . . . . . . . . . . . . 2932
- 85.4 对数正态分布及其与正态分布的关系 . . . . . . . . . . . . . . . . . . . 2934
- 85.5 多元正态分布和对数正态分布 . . . . . . . . . . . . 2935
- 85.6 正态分布在二项分布和泊松分布中的应用 . . . . . . . . . . . . . . . . . . . . . . . 2939
- 85.7 对数正态分布在期权定价中的应用 2943
- 85.8 双变量正态密度函数 . . . . . . . . . . . . . . . . . . 2945
- 85.9 美式看涨期权 . . . . . . . . . . . . . . . . . . . . . . . . 2948
- 85.9.1 利用双变量正态分布定价美式看涨期权 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2948
- 85.9.2 美式看涨期权定价：一个例子 . . . . . . . . . . . 2951
- 85.10 期权的定价界限 . . . . . . . . . . . . . . . . . . . . . 2954
- 85.10.1 基于不派息股票的期权 . . . . . . . . . . . 2954
- 85.10.2 基于派息股票的期权 . . . . . . . . . . . . 2955
- 85.11 总结 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2960

参考文献 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2960

附录 85A：用于计算累积双变量正态密度函数的 Microsoft Excel 程序 . . . . . . 2961

附录 85B：用于计算美式看涨期权的 Microsoft Excel 程序 . . . . . . . . . . . . . . . . . . 2962

## 摘要

在本章中，我们首先回顾正态分布和对数正态分布的基本理论及其关系，然后详细分析双变量和多元正态密度函数。接下来，我们从随机股息支付的角度讨论美式期权。然后我们利用双变量正态密度函数分析具有随机股息支付的美式期权。计算机程序被用来展示如何评估美式看涨期权。最后，期权定价界限被详细分析。

## 关键词

正态分布 ● 对数正态分布 ● 美式期权 ● 期权界限 ● 多元正态分布 ● 多元对数正态分布。

## 85.1 引言

正态（或高斯）分布是概率与统计中最重要的分布。采用正态分布的一个理由是中心极限定理。此外，大量统计理论基于正态性假设。然而，在金融研究中，对数正态分布发挥着最重要作用。其原因之一是金融中处理的随机量本质上为正，因此取自然对数是相当合理的。此外，经验数据也经常支持诸如股价变动等随机量的对数正态性假设。

在第85.1节和第85.2节中，我们分别讨论正态分布和对数正态分布。第85.3节解释了对数正态分布与正态分布之间的关系。第85.4节介绍了多元正态分布和对数正态分布。第85.5节将正态分布应用于二项分布。第85.6节涵盖了对数正态分布在期权定价中的应用。第85.7节介绍了双变量正态分布。在第85.8节中，我们利用双变量正态分布对美式看涨期权进行定价，并通过一个例子说明计算过程。第85.9节推导了有息或无息股票期权的定价界限。第85.10节总结并得出前文研究结果的结论。

