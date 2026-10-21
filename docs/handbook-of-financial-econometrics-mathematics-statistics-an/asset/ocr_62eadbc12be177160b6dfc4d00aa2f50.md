# Table 3.1: Empirical definitions of variables.

| Variable | Empirical definition | Data source |
|---|---|---|
| **Dependent Variable and Test Variables for Firm i in Country j in Year t** | | |
| $AUDFEE_{ijt}$ | = natural log of audit fees in thousands of US dollars | Worldscope |
| $BTC_{jt}$ | = scaled ranking of the RMSEs obtained from country-year estimates of equation (3.1), where the scaled ranking value ranges between 0 and 1 and a higher value corresponds to higher book-tax conformity | Worldscope |
| $Ln(BTD)_{ijt}$ | = natural log of the absolute value of the spread between pre-tax book income and estimated taxable income, where both incomes are in thousands of US dollars | Worldscope$^a$ |
| **Firm-Specific Control Variables (FSCONTROL) for Firm i in Country j in Year t** | | |
| $Ln(ACC)_{ijt}$ | = natural log of the absolute value of total accruals in thousands of US dollars, where total accruals are measured as the differences between earnings and cash flow from operations | Worldscope |
| $LNTA_{ijt}$ | = natural log of year-end total assets in thousands of US dollars | Worldscope |
| $INVREC_{ijt}$ | = sum of inventories and receivables scaled by total assets | Worldscope |
| $LOSS_{ijt}$ | = 1 when a firm reports a net loss and 0 otherwise | Worldscope |
| $ROA_{ijt}$ | = operating income before depreciation divided by total assets | Worldscope |
| $LEV_{ijt}$ | = ratio of year-end total liabilities to total assets | Worldscope |
| $ISSUE_{ijt}$ | = 1 when a firm has obtained long-term debt or equity financing by issuing bonds or new shares to outside capital suppliers in year t and 0 otherwise | Worldscope |
| $CROSS_{ijt}$ | = 1 when a firm is cross-listed in a foreign country and 0 otherwise | Worldscope |
| $NBS_{ijt}$ | = natural log of 1 plus the number of business segments | Worldscope |
| $NGS_{ijt}$ | = natural log of 1 plus the number of geographical segments | Worldscope |
| $BIG\text{-}N_{ijt}$ | = 1 when a firm uses one of the Big 4 (5, 6, or 8) auditors and 0 otherwise | Worldscope |
| $OPINION_{ijt}$ | = 1 when the firm does not receive a standard unqualified audit opinion and 0 otherwise | Worldscope |
| **Country-Level Control Variables (CLCONTROL) for Country j in Year t** | | |
| $DISCL_j$ | = country's required disclosure level measured by the CIFAR index | CIFAR |
| $GDP_{jt}$ | = natural log of the gross domestic product per capita in thousands of US dollars | World Bank Statistics |
| $FDI_{jt}$ | = foreign direct investment scaled by gross domestic product | World Bank Statistics |

Notes: $^a$The calculation of $Ln(BTD)$ requires the statutory corporate tax rates for each country. We follow Atwood et al. (2012) by manually collecting these statutory tax rates from a KPMG online summary, PricewaterhouseCoopers's online information, Coopers & Lybrand's worldwide tax summary guides, and the website of the Organization for Economic Co-operation and Development.