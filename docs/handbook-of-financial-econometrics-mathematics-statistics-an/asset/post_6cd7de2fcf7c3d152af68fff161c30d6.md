
Carleton’s linear-programming model, to perform financial analysis, planning, and forecasting.

In this chapter, we have also briefly discussed Feltham–Ohlson model for determining equity value. In addition, we have explored the usefulness of integrating WS model and FO model to improve the determination of equity value.

## Bibliography

R. A. Brealey, S. C. Myers, and F. Allen (2016). *Principles of Corporate Finance*, 12th ed. Burr Ridge, IL: McGraw-Hill.

W. T. Carleton (1970). An Analytical Model for Long-Range Financial Planning. *Journal of Finance*, 25, 291–315.

H. Y. Chen, C. F. Lee, and W. K. Shih (2016). Technical, Fundamental, and Combined Information for Separating Winners from Losers. *Pacific-Basin Finance Journal*, 39, 224–242.

H. Y. Chen, C. F. Lee, and W. K. Shih (2015). Alternative Equity Valuation Models. In Cheng F. L. and J. C. Lee (eds.), *Handbook of Financial Econometrics and Statistics*, pp. 2401–2444.

B. E. Davis, G. J. Caccappolo, and M. A. Chandry (1973). An Econometric Planning Model for American Telephone and Telegraph Company. *The Bell Journal of Economics and Management Science*, 4, 29–56.

F. X. Diebold and P. C. Pauly (1987). Structural Change and the Combination of Forecasts. *Journal of Forecasting*, 6, 21–40.

W. J. Elliott (1972). Forecasting and Analysis of Corporate Financial Performance with an Econometric Model of the Firm. *Journal of Financial and Quantitative Analysis*, 1499–1526.

G. A. Feltham and J. A. Ohlson (1995). Valuation and Clean Surplus Accounting for Operating and Financial Activities. *Contemporary Accounting Research*, 11, 689–731.

J. C. Francis (1977). Analysis of Equity Returns: A Survey with Extensions. *Journal of Economics and Business*, 181–192.

J. C. Francis and D. R. Rowell (1978). A Simultaneous-Equation Model of the Firm for Financial Analysis and Planning. *Financial Management*, 7, 29–44.

G. W. Gershefski (1969). Building a Corporate Financial Model. *Harvard Business Review*, 61–72.

C. W. J. Granger and P. Newbold (1973). Some Comments on the Evaluation of Economic Forecasts. *Applied Economics*, 5, 35–47.

A. C. Lee, J. C. Lee, and C. F. Lee (2017). *Financial Analysis, Planning and Forecasting: Theory and Application*, 3rd ed. Singapore: World Scientific Publishing Company.

C. F. Lee (1984). Alternative Financial Planning and Forecasting Models: An Integration and Extension. Mimeo: The University of Illinois at Urbana-Champaign.

C. F. Lee, J. E. Finnerty, and E. A. Norton (1997). *Foundations of Financial Management*, 3rd ed. Minneapolis/St. Paul: West Publishing Co.

C. F. Lee, J. C. Lee, and A. C. Lee (2000). *Statistics for Business and Financial Economics*. Singapore: World Scientific Publishing Co.

C. F. Lee and S. Rahman (1997). Interaction of Investment, Financing, and Dividend Decisions: A Control Theory Approach. *Advances in Financial Planning and Forecasting*, 7.

E. Lerner and W. T. Carleton (1964). The Integration of Capital Budgeting and Stock Valuation. *American Economic Review*, 54, 683–702.

S. C. Myers and A. Pogue (1974). A Programming Approach to Corporate Financial Management. *Journal of Finance*, 29, 579–599.

J. A. Ohlson (1995). Earnings, Book Values, and Dividends in Equity Valuation. *Contemporary Accounting Research*, 11, 661–687.

R. S. Pindyck and D. L. Rubinfeld (1976). *Econometric Models and Economic Forecasts*. New York: McGraw-Hill Book Co.

S. A. Ross, R. W. Westerfield, and J. F. Jaffe (2002). *Corporate Finance*, 6th ed. Boston, MA: McGraw-Hill Irwin Publishing Co.

S. Salzman (1967). An Econometric Model of a Firm. *Review of Economics and Statistics*, 49, 332–342.

Securities and Exchange Commission, Release No. 5695 (1976). *Notice of Adoption of Amendments to Regulations S-X Requiring Disclosure of Certain Replacement Cost Data*, March 23.

Securities and Exchange Commission, Release No. 33-5699 (1976). April 23.

J. M. Warren and J. P. Shelton (1971). A Simultaneous-Equation Approach to Financial Planning. *Journal of Finance*, 26, 1123–1142.

J. B. Williams (1938). *The Theory of Investment Value*. Cambridge, MA: Harvard University Press.

Websites: http://finance.yahoo.com.

## Appendix 90A: Procedure of Using Microsoft Excel to Run FINPLAN Program

The program of FINPLAN is available on the Website: http://centerforpbefr.rutgers.edu/.

### FINPLAN input

| Value of Data | Variable Number | Beginning Period | Last Period | Description |
|---:|---:|---:|---:|---|
| 4 | 1 | 0 | 0 | The number of years to be simulated |
| 61897.0000 | 21 | 0 | 0 | Net Sales at t-1=2009 |
| -0.2900 | 22 | 1 | 4 | Growth in Sales |
| 0.6388 | 23 | 1 | 4 | Current Assets as a Percent of Sales |
| 0.8909 | 24 | 1 | 4 | Fixed Assets as a Percent of Sales |
| 0.3109 | 25 | 1 | 4 | Current Payables as a Percent of Sales |
| 0.0000 | 26 | 1 | 4 | Preferred Stock |
| 0.0000 | 27 | 1 | 4 | Preferred Dividends |
| 8223.0000 | 28 | 0 | 0 | Long Term Debt in Previous Period |
| 219.0000 | 29 | 1 | 4 | Long Term Debt Repayment (Reduction) |
| 3120.0000 | 30 | 0 | 0 | Common Stock in Previous Period |
| 67248.0000 | 31 | 0 | 0 | Retained Earnings in Previous Period |
| 0.5657 | 32 | 1 | 4 | Retention Rate |
| 0.2215 | 33 | 1 | 4 | Average Tax Rate (Income Taxes / Pretax Income) |
| 0.0671 | 34 | 0 | 0 | Average Interest Rate in Previous Period |
| 0.0671 | 35 | 1 | 4 | Expected Interest Rate on New Debt |
| 0.2710 | 36 | 1 | 4 | Operating Income as a Percentage of Sales |
| 0.0671 | 37 | 1 | 4 | Underwriting Cost of Debt |
| 0.1053 | 38 | 1 | 4 | Underwriting Cost of Equity |
| 0.1625 | 39 | 1 | 4 | Ratio of Debt to Equity |
| 2,754.321 | 40 | 0 | 0 | Number of Common Shares Outstanding in Previous Period |
| 14.4700 | 41 | 1 | 4 | Price-Earnings Ratio |

### Pro forma Income Statement

| Item | 2009 | 2010 | 2011 | 2012 | 2013 |
|---|---:|---:|---:|---:|---:|
| Sales | 61897.00 | 43946.87 | 31202.28 | 22153.62 | 15729.07 |
| Operating income | 0.00 | 11909.60 | 8455.82 | 6003.63 | 4262.58 |
| Interest expense | 0.00 | 502.61 | 356.85 | 253.36 | 179.89 |
| Underwriting commission -- debt | 0.00 | 34.69 | 131.05 | 88.79 | 58.77 |
| Income before taxes | 0.00 | 11372.30 | 7967.91 | 5661.48 | 4023.91 |
| Taxes | 0.00 | 2518.44 | 1764.52 | 1253.75 | 891.11 |
| Net income | 0.00 | 8853.87 | 6203.39 | 4407.73 | 3132.80 |
| Preferred dividends | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 |
| Available for common dividends | 0.00 | 8853.87 | 6203.39 | 4407.73 | 3132.80 |
| Common dividends | 0.00 | 3845.23 | 2694.13 | 1914.28 | 1360.58 |
| Debt repayments | 0.00 | 219.00 | 219.00 | 219.00 | 219.00 |
| Additional funds needed for investment | 0.00 | -29848.90 | -18938.76 | -13381.13 | -9435.22 |

### Pro forma Balance Sheet

| Item | 2009 | 2010 | 2011 | 2012 | 2013 |
|---|---:|---:|---:|---:|---:|
| Assets |  |  |  |  |  |
| Current assets | 0.00 | 28073.26 | 19932.01 | 14151.73 | 10047.73 |
| Fixed assets | 0.00 | 39152.27 | 27798.11 | 19736.66 | 14013.03 |
| Total assets | 0.00 | 67225.53 | 47730.12 | 33888.39 | 24060.76 |
| Liabilities and net worth |  |  |  |  |  |
| Current liabilities | 0.00 | 13663.24 | 9700.90 | 6887.64 | 4890.22 |
| Long term debt | 8223.00 | 7487.20 | 5315.91 | 3774.30 | 2679.78 |
| Preferred stock | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 |
| Common stock | 3120.00 | -26212.11 | -43198.58 | -55257.99 | -63816.76 |
| Retained earnings | 67248.00 | 72287.19 | 75991.89 | 78483.54 | 80307.54 |
| Total liabilities and net worth | 0.00 | 67225.53 | 47730.12 | 33888.39 | 24060.76 |
| Computed DBT/EQ | 0.0000 | 0.1625 | 0.1625 | 0.1625 | 0.1625 |
| Int. rate on total debt | 0.0671 | 0.0671 | 0.0671 | 0.0671 | 0.0671 |
| Per share data |  |  |  |  |  |
| Earnings | 0.0000 | 4.0371 | 3.4269 | 2.9494 | 2.5387 |
| Dividends | 0.0000 | 1.7533 | 1.4883 | 1.2809 | 1.1026 |
| Price | 0.0000 | 58.4172 | 49.5865 | 42.6783 | 36.7356 |

```vbnet
On Error GoTo ErrorHandler

Columns("a").ColumnWidth = 29      'Set default column A width

Range("a2").Select                 'Get the year being simulated from cell A2
NDATE = ActiveCell.Value

Range("b5").Select                 'Get the variable code number from cell B5
NUMVR = ActiveCell.Value

bNYEARFound = False
    While NUMVR <> Empty And Not bNYEARFound
        If NUMVR = 1 Then               'If the number of years to be simulated is
                                         found
            N = ActiveCell.Previous.Value + 1
            bNYEARFound = True
        End If

        ActiveCell.Offset(1, 0).Activate
        NUMVR = ActiveCell.Value
    Wend

    If Not bNYEARFound Then N = 5      'If the number of years to be simulated is not
                                        found
                                        'then set the default of N as 5

ReDim NYEAR(N)
ReDim SALES(N)
ReDim GSALS(N)
ReDim ORATE(N)
ReDim T(N)
ReDim CARAT(N)
ReDim FARAT(N)
ReDim CLRAT(N)
ReDim ZL(N)
ReDim ZI(N)
ReDim ZIE(N)
ReDim ZLR(N)
ReDim PFDSK(N)
ReDim PFDIV(N)
ReDim S(N)
ReDim ZNUMC(N)
ReDim R(N)
ReDim B(N)
ReDim ZK(N)
ReDim PERAT(N)
ReDim UL(N)
ReDim US(N)

NYEAR(1) = NDATE
    For i = 2 To N
        NYEAR(i) = NYEAR(i - 1) + 1
    Next

Range("b5").Select
NUMVR = ActiveCell.Value

    While NUMVR <> Empty
        Select Case NUMVR
            Case 21
                SALES(1) = ActiveCell.Previous.Value
```
