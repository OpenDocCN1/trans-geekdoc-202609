
**Table 9.10:** Matrix \(C^*\) for the numerical example, MultT.

|   | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | Weights |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 1 | 0 | 1 | 0.40 | 0.60 | 0.18 | 1 | 0.60 | 0.80 | 0.42 | 0 | 1 | 0.11 |
| 2 | 0 | 0 | 0 | 0 | 0.20 | 1 | 0 | 0.80 | 0 | 0 | 1 | 0.11 |
| 3 | 0 | 0.60 | 0 | 1 | 0.40 | 0.60 | 1 | 0.48 | 0.71 | 0 | 1 | 0.11 |
| 4 | 0 | 0 | 0 | 0 | 0.29 | 0 | 1 | 0 | 0.71 | 0 | 1 | 0.11 |
| 5 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 6 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0.11 |
| 7 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0.11 |
| 8 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0.11 |
| 9 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0.11 |
| 10 | 1 | 1 | 0.40 | 0.60 | 0.18 | 1 | 0.60 | 0.80 | 0.42 | 0 | 1 | 0.11 |
| 11 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| **Total** | 0.11 | 0.29 | 0.09 | 0.24 | 0.14 | 0.40 | 0.36 | 0.32 | 0.25 | 0 | 1 |  |
| **Total (normalized)** | **0.03** | **0.09** | **0.03** | **0.07** | **0.04** | **0.12** | **0.11** | **0.10** | **0.08** | **0** | **0.31** |  |

**Table 9.11:** Matrix \(C^*\) for the numerical example, MaxT.

|   | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | Weights |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 1 | 0 | 1 | 0.40 | 0.60 | 0.29 | 1 | 0.60 | 0.80 | 0.60 | 0 | 1 | 0.11 |
| 2 | 0 | 0 | 0 | 0 | 0.20 | 1 | 0 | 0.80 | 0 | 0 | 1 | 0.11 |
| 3 | 0 | 0.60 | 0 | 1 | 0.40 | 0.60 | 1 | 0.60 | 0.71 | 0 | 1 | 0.11 |
| 4 | 0 | 0 | 0 | 0 | 0.29 | 0 | 1 | 0 | 0.71 | 0 | 1 | 0.11 |
| 5 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 6 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0.11 |
| 7 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0.11 |
| 8 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0.11 |
| 9 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0.11 |
| 10 | 1 | 1 | 0.40 | 0.60 | 0.29 | 1 | 0.60 | 0.80 | 0.60 | 0 | 1 | 0.11 |
| 11 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| **Total** | 0.11 | 0.29 | 0.09 | 0.24 | 0.16 | 0.40 | 0.36 | 0.33 | 0.29 | 0 | 1 |  |
| **Total (normalized)** | **0.03** | **0.09** | **0.03** | **0.08** | **0.05** | **0.13** | **0.11** | **0.10** | **0.09** | **0** | **0.31** |  |

### 9.4 Empirical Application — Country Assessment

In this section, the model outlined so far will be applied for evaluation of the level of banking systems interconnectedness. We try to detect countries with the most interconnected financial systems taking into consideration the intensities of countries’ banking systems interactions. At the same time, we understand the limitations of the existing data. The analysis of cross-border country exposures relies primarily on data aggregated at the level of countries, and, hence, overlooks bank-level heterogeneity.

The data is taken from the Bank for International Settlements (BIS) statistics.^1 More precisely, we use the BIS consolidated banking statistics on an ultimate risk basis. For example, suppose that a bank from country A extends a loan to a company from country B and the loan is guaranteed by a bank from country C. On an ultimate risk basis, this loan would be reported as a claim on the country C because, if the company from B were unable to meet its obligations, then ultimately the bank from A would be exposed to the bank from C that guaranteed the loan. In other words, claims are allocated to the country where the final risk lies.

Foreign claims in BIS statistics are designed to analyze the exposure of internationally active banks to individual countries and sectors. The sectoral classification consists of (a) banks; (b) official sector, which includes general government, central banks, and international organizations; (c) non-bank private sector, including non-bank financials.

Thus, our figures indicate the $i$th banking system foreign claims on borrowers from different sectors in country $j$, which include its worldwide consolidated direct cross-border claims on country $j$ plus the positions booked by its affiliates (subsidiaries and branches) in country $j$ vis-à-vis residents of country $j$. The data covers on-balance sheet claims as well as some off-balance sheet exposures of banks headquartered in the reporting country and provides a measure of country credit risk exposures consonant with banks’ own risk management systems.

The reporting countries comprise the G10 countries (Belgium, Canada, France, Germany, Italy, Japan, Netherlands, Sweden, Switzerland, UK, and USA) plus Australia, Austria, Chile, Finland, Greece, India, Ireland, South Korea, Portugal, Spain, and Turkey.

BIS consolidated banking statistics, apart from information about banking foreign claims, includes aggregated data on regional country groupings such as regional residuals of developed countries, offshore centers, Africa and the Middle East, Asia-Pacific, Europe, Latin America and the Caribbean, and “Unallocated” claims. These positions are used in BIS Statistics in cases when the balance of payments concept of residence of both the reporting bank and its counterparty could not be applied. In this paper, we analyze only cross-country relationships, so we exclude these groupings from the database as well as a position of international financial organizations.

^1 Table 9D “Foreign claims by nationality of reporting banks, ultimate risk basis” (http://www.bis.org/statistics/r_qa1509_hanx9d_u.pdf).

As a result, we obtained a database covering 22 countries that have bank foreign claims and 198 countries that have obligations for the end of 1Q 2015. Thus, the network considered on the basis of the data includes all information about the international borrowings, except for transactions between countries which do not report. According to BIS Statistical Bulletin, our network covers about 94% of total foreign claims and other potential exposures on an ultimate risk basis.

The important aspect of the analysis is the choice of the critical loan amount threshold level for each country. One possible way to define it is to follow the recommendations of the Basel Committee (BCBS, 2013) on large exposure limits (25% of the Tier 1 capital). At the international level, when we deal with banking system's borrowings, choosing an appropriate threshold level (critical loan amount) is not so obvious. We decided to put on the edges of the network not loans, but the value measured by the ratio of loans to the gross domestic product (GDP) of the lending country in order to take into account the relative size of the loan. In this paper the nominal GDP is used. However, GDP measure can be replaced by the total banking system assets or capital estimations. So, suppose that the threshold q be 10% of the nominal GDP.

Another important issue here is to assign grades to the direct influence values for the threshold procedure. In Table 9.12, we propose the following system of grades which in our opinion is reasonable for this case.

The highest grade corresponds to the highest influence value, the lowest grade indicates the absence of influence between elements.

Thus, we can calculate the influence value of each borrower according to our methodology. Table 9.13 contains a list of countries that were in the

**Table 9.12:** Grades for direct influence values description.

| Grade | Condition | Description |
|---|---|---|
| 7 | $c_{ij}=1$ | ultimately high influence |
| 6 | $0.92 \le c_{ij} < 1$ | very high influence (explanation similar to the capital adequacy ratio for banks, when the loss of more than 92% of assets will lead to the bank's capital fall below zero) |
| 5 | $0.85 \le c_{ij} < 0.92$ | high influence (according to the upper value of the capital adequacy ratio, a standard procedure of Bank of Russia) |
| 4 | $0.75 \le c_{ij} < 0.85$ | average influence |
| 3 | $0.5 \le c_{ij} < 0.75$ | moderate influence |
| 2 | $0.25 \le c_{ij} < 0.5$ | low influence |
| 1 | $0 < c_{ij} < 0.25$ | very low influence |
| 0 | $c_{ij}=0$ | no influence |
