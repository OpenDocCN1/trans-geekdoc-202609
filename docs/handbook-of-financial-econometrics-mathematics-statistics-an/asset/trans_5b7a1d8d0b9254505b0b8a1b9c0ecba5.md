
Carleton 的线性规划模型，用于进行财务分析、规划和预测。

在本章中，我们还简要讨论了用于确定股权价值的 Feltham-Ohlson 模型。此外，我们还探讨了将 WS 模型与 FO 模型整合以提高股权价值确定性的有用性。

## 参考文献

R. A. Brealey, S. C. Myers, and F. Allen (2016). *公司财务原理*, 12th ed. Burr Ridge, IL: McGraw-Hill.

W. T. Carleton (1970). 长期财务规划的分析模型. *金融学杂志*, 25, 291–315.

H. Y. Chen, C. F. Lee, and W. K. Shih (2016). 技术、基本面和综合信息在区分赢家与输家中的应用. *太平洋盆地金融杂志*, 39, 224–242.

H. Y. Chen, C. F. Lee, and W. K. Shih (2015). 替代股权估值模型. In Cheng F. L. and J. C. Lee (eds.), *金融计量经济学与统计手册*, pp. 2401–2444.

B. E. Davis, G. J. Caccappolo, and M. A. Chandry (1973). 美国电话电报公司的计量经济学规划模型. *贝尔经济学与管理科学杂志*, 4, 29–56.

F. X. Diebold and P. C. Pauly (1987). 结构变化与预测组合. *预测杂志*, 6, 21–40.

W. J. Elliott (1972). 利用企业计量经济学模型进行公司财务绩效预测与分析. *金融与定量分析杂志*, 1499–1526.

G. A. Feltham and J. A. Ohlson (1995). 经营和财务活动的估值与干净盈余会计. *当代会计研究*, 11, 689–731.

J. C. Francis (1977). 股权回报分析：综述与扩展. *经济学与商业杂志*, 181–192.

J. C. Francis and D. R. Rowell (1978). 用于财务分析与规划的企业联立方程模型. *财务管理*, 7, 29–44.

G. W. Gershefski (1969). 建立企业财务模型. *哈佛商业评论*, 61–72.

C. W. J. Granger and P. Newbold (1973). 关于经济预测评估的若干评论. *应用经济学*, 5, 35–47.

A. C. Lee, J. C. Lee, and C. F. Lee (2017). *财务分析、规划与预测：理论与应用*, 3rd ed. Singapore: World Scientific Publishing Company.

C. F. Lee (1984). 替代财务规划与预测模型：整合与扩展. Mimeo: The University of Illinois at Urbana-Champaign.

C. F. Lee, J. E. Finnerty, and E. A. Norton (1997). *财务管理基础*, 3rd ed. Minneapolis/St. Paul: West Publishing Co.

C. F. Lee, J. C. Lee, and A. C. Lee (2000). *商业与金融经济学统计学*. Singapore: World Scientific Publishing Co.

C. F. Lee and S. Rahman (1997). 投资、融资与股利决策的相互作用：控制理论方法. *财务规划与预测进展*, 7.

E. Lerner and W. T. Carleton (1964). 资本预算与股票估值的整合. *美国经济评论*, 54, 683–702.

S. C. Myers and A. Pogue (1974). 企业财务管理的规划方法. *金融学杂志*, 29, 579–599.

J. A. Ohlson (1995). 股权估值中的收益、账面价值与股利. *当代会计研究*, 11, 661–687.

R. S. Pindyck and D. L. Rubinfeld (1976). *计量经济学模型与经济预测*. New York: McGraw-Hill Book Co.

S. A. Ross, R. W. Westerfield, and J. F. Jaffe (2002). *公司理财*, 6th ed. Boston, MA: McGraw-Hill Irwin Publishing Co.

S. Salzman (1967). 企业计量经济学模型. *经济学与统计评论*, 49, 332–342.

Securities and Exchange Commission, Release No. 5695 (1976). *关于采纳修订 S-X 法规要求披露某些重置成本数据的通知*, March 23.

Securities and Exchange Commission, Release No. 33-5699 (1976). April 23.

J. M. Warren and J. P. Shelton (1971). 财务规划的联立方程方法. *金融学杂志*, 26, 1123–1142.

J. B. Williams (1938). *投资价值理论*. Cambridge, MA: Harvard University Press.

网站: http://finance.yahoo.com.

## 附录 90A：使用 Microsoft Excel 运行 FINPLAN 程序的步骤

FINPLAN 程序可在网站上获取：http://centerforpbefr.rutgers.edu/.

### FINPLAN 输入

| 数据值 | 变量编号 | 开始期间 | 结束期间 | 描述 |
|---:|---:|---:|---:|---|
| 4 | 1 | 0 | 0 | 模拟的年数 |
| 61897.0000 | 21 | 0 | 0 | t-1=2009 时的净销售额 |
| -0.2900 | 22 | 1 | 4 | 销售额增长率 |
| 0.6388 | 23 | 1 | 4 | 流动资产占销售额的百分比 |
| 0.8909 | 24 | 1 | 4 | 固定资产占销售额的百分比 |
| 0.3109 | 25 | 1 | 4 | 流动应付款占销售额的百分比 |
| 0.0000 | 26 | 1 | 4 | 优先股 |
| 0.0000 | 27 | 1 | 4 | 优先股股利 |
| 8223.0000 | 28 | 0 | 0 | 上一期间长期债务 |
| 219.0000 | 29 | 1 | 4 | 长期债务偿还（减少） |
| 3120.0000 | 30 | 0 | 0 | 上一期间普通股 |
| 67248.0000 | 31 | 0 | 0 | 上一期间留存收益 |
| 0.5657 | 32 | 1 | 4 | 留存率 |
| 0.2215 | 33 | 1 | 4 | 平均税率（所得税/税前收入） |
| 0.0671 | 34 | 0 | 0 | 上一期间平均利率 |
| 0.0671 | 35 | 1 | 4 | 新债务预期利率 |
| 0.2710 | 36 | 1 | 4 | 经营收入占销售额的百分比 |
| 0.0671 | 37 | 1 | 4 | 债务承销成本 |
| 0.1053 | 38 | 1 | 4 | 股权承销成本 |
| 0.1625 | 39 | 1 | 4 | 债务权益比 |
| 2,754.321 | 40 | 0 | 0 | 上一期间已发行普通股数量 |
| 14.4700 | 41 | 1 | 4 | 市盈率 |

### 预测利润表

| 项目 | 2009 | 2010 | 2011 | 2012 | 2013 |
|---|---:|---:|---:|---:|---:|
| 销售额 | 61897.00 | 43946.87 | 31202.28 | 22153.62 | 15729.07 |
| 经营收入 | 0.00 | 11909.60 | 8455.82 | 6003.63 | 4262.58 |
| 利息费用 | 0.00 | 502.61 | 356.85 | 253.36 | 179.89 |
| 债务承销佣金 | 0.00 | 34.69 | 131.05 | 88.79 | 58.77 |
| 税前收入 | 0.00 | 11372.30 | 7967.91 | 5661.48 | 4023.91 |
| 税款 | 0.00 | 2518.44 | 1764.52 | 1253.75 | 891.11 |
| 净利润 | 0.00 | 8853.87 | 6203.39 | 4407.73 | 3132.80 |
| 优先股股利 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 |
| 可用于普通股股利 | 0.00 | 8853.87 | 6203.39 | 4407.73 | 3132.80 |
| 普通股股利 | 0.00 | 3845.23 | 2694.13 | 1914.28 | 1360.58 |
| 债务偿还 | 0.00 | 219.00 | 219.00 | 219.00 | 219.00 |
| 投资所需额外资金 | 0.00 | -29848.90 | -18938.76 | -13381.13 | -9435.22 |

### 预测资产负债表

| 项目 | 2009 | 2010 | 2011 | 2012 | 2013 |
|---|---:|---:|---:|---:|---:|
| 资产 |  |  |  |  |  |
| 流动资产 | 0.00 | 28073.26 | 19932.01 | 14151.73 | 10047.73 |
| 固定资产 | 0.00 | 39152.27 | 27798.11 | 19736.66 | 14013.03 |
| 总资产 | 0.00 | 67225.53 | 47730.12 | 33888.39 | 24060.76 |
| 负债和净资产 |  |  |  |  |  |
| 流动负债 | 0.00 | 13663.24 | 9700.90 | 6887.64 | 4890.22 |
| 长期债务 | 8223.00 | 7487.20 | 5315.91 | 3774.30 | 2679.78 |
| 优先股 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 |
| 普通股 | 3120.00 | -26212.11 | -43198.58 | -55257.99 | -63816.76 |
| 留存收益 | 67248.00 | 72287.19 | 75991.89 | 78483.54 | 80307.54 |
| 负债和净资产合计 | 0.00 | 67225.53 | 47730.12 | 33888.39 | 24060.76 |
| 计算的债务/权益 | 0.0000 | 0.1625 | 0.1625 | 0.1625 | 0.1625 |
| 总债务利率 | 0.0671 | 0.0671 | 0.0671 | 0.0671 | 0.0671 |
| 每股数据 |  |  |  |  |  |
| 收益 | 0.0000 | 4.0371 | 3.4269 | 2.9494 | 2.5387 |
| 股利 | 0.0000 | 1.7533 | 1.4883 | 1.2809 | 1.1026 |
| 价格 | 0.0000 | 58.4172 | 49.5865 | 42.6783 | 36.7356 |

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
