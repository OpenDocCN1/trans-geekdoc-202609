
## 90.3.2 Procedure for calculating WS model

By using the data above, we are able to calculate the unknown variables as follows:

(1) $Sales_t = Sales_{t-1} \times (1 + GCALS_t)$  
$= 61897.0 \times 0.71$  
$= 43,946.87,$

(2) $EBIT_t = REBIT_{t-1} \times Sales_t$  
$= 0.2710 \times 43,946.87$  
$= 11,909.60,$

(3) $CA_t = RCA_{t-1} \times Sales_t$  
$= 0.6388 \times 43,946.87$  
$= 28,073.26,$

(4) $FA_t = RFA_{t-1} \times Sales_t$  
$= 0.8909 \times 43,946.87$  
$= 39,152.27,$

(5) $A_t = CA_t + FA_t$  
$= 28,073.26 + 39,152.27$  
$= 67,225.53,$

(6) $CL_t = RCL_{t-1} \times Sales_t$  
$= 0.3109 \times 43,946.87$  
$= 13,663.08,$

(7) $NF_t = (A_t - CL_t - PFDIV_t) - (L_{t-1} - LR_t) - S_{t-1} - R_{t-1} - b_t \times \{(1 - T_t)[EBIT_t - i_{t-1}(L_{t-1} - LR_t)] - PFDIV_t\}$  
$= (67,225.53 - 13,663.080) - (8,223.0 - 219.0) - 3,120.0$  
$-67,248.0 - 0.5657 \times \{(1 - 0.2215) \times [11,909.60 - 0.0671 \times (8,223.0 - 219.0)] - 0\}$  
$= -29,817.99,$

(12) $i_t L_t = i_{t-1}(L_{t-1} - LR_t) + i_{t-1}^e \times NL_t$  
$= 0.0671 \times (8,223.0 - 219.0) + 0.0671 \times NL_t$  
$= 537.0684 + 0.0671 \times NL_t,$

(8) $NF_t + b_t(1 - T)[i_{t-1} \times NL_t + U_t^L \times NL_t] = NL_t + NS_t$  
$-29817.99 + 0.5657 \times (1 - 0.2215) \times [0.0671 NL_t + 0.0671 NL_t] = NL_t + NS_t$  
$-29817.99 + 0.0591 \times NL_t = NL_t + NS_t,$

(a) $NS_t + 0.9409 NL_t = -29,817.99,$

(9) $L_t = L_{t-1} - LR_t + NL_t,$  
(b) $L_t = 8,223.0 - 219.0 + NL_t$  
$L_t - NL_t = 8,004,$

(10) $S_t = S_{t-1} + NS_t,$  
(c) $- NS_t + S_t = 3,120.0,$

(11) $R_t = R_{t-1} + b_t \{(1 - T_t)[EBIT_t - i_t L_t - U_t^L NL_t] - PFDIV_t\}$  
$= 67,248.0 + 0.5657 \times \{(1 - 0.2215)$  
$\times [11,909.60 - i_t L_t - 0.0671 NL_t] - 0\},$

Substitute (12) into (11)  
$R_t = 67,248.0 + 0.5657 \times \{0.7785 \times [11,909.60 - (537.0684 + 0.0671$  
$\times NL_t) - 0.0671 NL_t]\}$  
$= 67,248.0 + 5,008.4347 - 0.0591 NL_t,$  
(d) $72,256.435 = R_t + 0.0591 NL_t,$

(13) $L_t = (S_t + R_t) K_t,$  
$L_t = 0.1625 S_t + 0.1625 R_t,$  
(e) $L_t - 0.1625 S_t - 0.1625 R_t = 0,$

(b) - (e) = (f),  
$0 = (L_t - NL_t - 8,004) - (L_t - 0.1625 S_t - 0.1625 R_t),$  
$8,004 = 0.1625 S_t + 0.1625 R_t - NL_t,$

(f) - 0.1625(c) = (g),  
$8,004 - 507 = (0.1625 S_t + 0.1625 R_t - NL_t) - 0.1625(-NS_t + S_t),$  
$7,497 = 0.1625 NS_t - NL_t + 0.1625 R_t,$

(g) - 0.1625(d) = (h),  
$7,497 - 0.1625 \times 72,256.435 = (0.1625 NS_t - NL_t + 0.1625 R_t) - 0.1625(R_t + 0.0591 NL_t)$  
$- 4,244.67 = 0.1625 NS_t - 1.0096 NL_t,$

(h) − 0.1625(a) = (i)  
$0.1625 NS_t - 1.0096 NL_t - 0.1625(NS_t + 0.9409 NL_t) = -4,244.67 + 0.1625(29,817.99)$  
$NL_t = -600.7533/1.1625 = -516.777.$

Substitute $NL_t$ in (a)  
$NS_t + 0.9409 \times (-516.777) = -29,817.99,$  
$NS_t = -29,331.755.$

Substitute $NL_t$ in (b)  
$L_t = 8,223.0 - 219.0 - 516.777$  
$= 7,487.223.$

Substitute $NS_t$ in (c)  
$29,331.755 + S_t = 3,120.0,$  
$S_t = -26211.755.$

Substitute $NL_t$ in (d)  
$72,256.43 = R_t + 0.0591 NL_t,$  
$R_t = 72,256.43 - 0.0591(-516.777),$  
$R_t = 72,286.98.$

Substitute $NL_t, L_t$ in (12)…  
$i_t(7,487.223) = 537.0684 + 0.0671 \times (-516.777),$  
$i_t = 0.0671.$

(14) $EAFCD_t = (1 - T_t)(EBIT_t - i_t L_t - U_t^L NL_t) - PFDIV_t$  
$= 0.7785 \times [11,909.60 - (0.0671)(7,487.223) - 0.0671(-516.777)]$  
$= 8,907.51,$

(15) $CMDIV_t = (1 - b_t)EAFCD_t$  
$= 0.4343(8,907.51)$  
$= 3,868.53,$

(16) $NUMCS_t = X_1 = NUMCS_{t-1} + NEWCS_t,$  
$X_1 = 2754.3 + NEWCS_t,$

(17) $NEWCS_t = X_2 = NS_t/(1 - U_t^E)P_t,$  
$X_2 = -29,331.755/(1 - 0.1053)P_t,$

(18) $P_t = X_3 = m_t EPS_t,$  
$X_3 = 14.5(EPS_t),$

(19) $EPS_t = X_4 = EAFCD_t / NUMCS_t,$  
$X_4 = 8,907.5075/NUMCS_t,$

(20) $DPS_t = X_5 = CMDIV_t / NUMCS_t,$  
$X_5 = 3,868.53/NUMCS_t,$

(A) For (18) and (19), we obtain $X_3 = 14.5(8,907.51)/NUMCS_t = 129,158.9/X_1$.

Substitute (A) into equation (17) to calculate (B)  
(B) $X_2 = -29,331.755/[(1 - 0.1053) \times 129,158.9/X_1],$  
(B) $X_2 = -0.2538X_1.$

Substitute (B) into equation (16) to calculate (C)  
(C) $X_1 = 2754.3 - 0.2538X_1,$  
(C) $X_1 = 2196.76.$

Substitute (C) into (B)…  
(B) $X_2 = -0.2538 \times 2196.76,$  
(B) $X_2 = -557.54.$

From equation (19) and (20), we obtain $X_4, X_5$ and $X_3$:  
$X_4 = 8,907.5075/2196.76 = 4.0548,$  
$X_5 = 3,868.53/2196.76 = 1.7610,$  
$X_3 = 14.5(4.0548) = 58.79.$

The results of the above calculations allow us to forecast the following information regarding JNJ in the 2010 fiscal year (dollars in thousands, except for per share data):

- Sales = $43,946.87,
- Current Assets = $28,073.26,
- Fixed Assets = $39,152.27,
- Total Assets = $67,225.53,
- Current Payables = $13,663.08,
- Needed Funds = ($29,817.99),
- Earnings before Interest and Taxes = $11,909.60,
- New Debt = ($516.777),
- New Stock = ($29,331.755),
- Total Debt = $7,487.223,
- Common Stock = ($26211.755),
- Retained Earnings = $72,286.98,
- Interest Rate on Debt = 6.71%,
- Earnings Available for Common Dividends = $8,907.51,
- Common Dividends = $3,868.53,
- Number of Common Shares Outstanding = 2196.76,
- New Common Shares Issued = (557.54),
- Price per Share = $58.79,
- Earnings per Share = $4.0548,
- Dividends per Share = $1.7610.

About 18 out of 20 unknowns are listed in Table 90.4, the actual data is also listed to allow the calculation of the forecast errors. In the last column of Table 90.4, the relative absolute forecasting errors ($|(A - F)/A|$) are calculated to indicate the performance of the WS model in forecasting important financial variables. It was found that the quality of the sales-growth rate estimate is the key to successfully using the WS model in financial planning and forecasting.

By comparing the forecast and actual values in Table 90.4, we find that the forecasting numbers generated by FINPLAN are very close to the ones on actual financial statements. During the financial-planning period, the company’s financial policy does not change and the economy is neither in a big recession nor booming. This provides us with an environment in which the historical data are useful for financial planning. From the solution, we know that, under the assumed parameter values, the company must issue both debt and equity. If the company wants to avoid equity financing, WS model also enables us to investigate alternative methods to achieve this goal by changing the parameter values. Therefore, the model can answer what if questions and, hopefully, the company can choose the best alternative. Finally, the model also can help us to understand the impacts of changes in parameters on key financial variables, such as earnings per share (EPS), price per share (PPS), dividend per share (DPS), and earnings before interest and taxes (EBIT), through the complicated interactions among the investment, financial, and dividend policies.

To do multiperiod forecasting and sensitivity analysis, the program of FINPLAN of Microsoft Excel, as listed in Appendix 90A, can be used. Using these programs provided, the pro forma financial statements listed in Tables 90.6 and 90.7 can be produced. The input parameters and the values used to produce the output in Tables 90.6 and 90.7 are listed in Table 90.5. The list of these parameters can be found in Table 90.3. To perform the

## Table 90.4: The comparison of financial forecast of JNJ: Hand calculation and FINPLAN forecasting.

| Category | Manual calculation | Financial plan model | Variance (|(A-F)/A|) (%) |
|---|---|---|---|
| **INCOME STATEMENT** | | | |
| Sales | 43,946.87 | 43,946.87 | 0.0 |
| Operating Income | 11,909.60 | 11,909.60 | 0.0 |
| Interest Expense | 502.39 | 502.39 | 0.0 |
| Income before taxes | 11,372.53 | 11,372.53 | 0.0 |
| Taxes | 2,519.02 | 2,519.02 | 0.0 |
| Net Income | 8,853.52 | 8,853.52 | 0.0 |
| Common Dividends | 3,868.53 | 3,845.08 | 0.6 |
| Debt Repayments | 219.00 | 219.00 | 0.0 |
| **BALANCE SHEET** | | | |
| **Assets** | | | |
| Current Assets | 28,073.26 | 28,073.26 | 0.0 |
| Fixed Assets | 39,152.27 | 39,152.27 | 0.0 |
| Total Assets | 67,225.53 | 67,225.53 | 0.0 |
| **LIABILITIES AND NET WORTH** | | | |
| Current Payables | 13,663.08 | 13,663.24 | 0.0 |
| Total Debt | 7,487.22 | 7,487.20 | 0.0 |
| Common Stock | (26,211.7) | (26,211.89) | 0.0 |
| Retained Earnings | 72,286.98 | 72,286.98 | 0.0 |
| Total Liabilities and Net Worth | 67,225.53 | 67,225.53 | 0.0 |
| **PER SHARE DATA** | | | |
| Price per Share | 58.79 | 58.51 | 0.5 |
| Earnings per Share (EPS) | 4.05 | 4.04 | 0.5 |
| Dividends per Share (DPS) | 1.76 | 1.75 | 0.5 |
