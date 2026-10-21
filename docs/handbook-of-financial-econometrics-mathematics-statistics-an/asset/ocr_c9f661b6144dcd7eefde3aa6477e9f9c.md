studies addressing earnings management contain documentation indicating that investors prefer stocks with stable earnings to those with a volatile earnings stream (e.g., Trueman and Titman, 1988; Goel and Thakor, 2003). Indicator variables for earnings stability, σ_NI (variance of a firm’s ROA in the past 5 years), and sales-growth stability, σ_SG (variance of a firm’s sales growth in the past 5 years), are assigned a value of one if they are less than the median of all firms in the same industry and zero otherwise. The third group of fundamental indicator variables relates to accounting conservatism. In low book-to-market firms, substantial research and development expenses, advertising expenses, and capital expenditure in the current period generate unrecorded intangible assets because of accounting conservatism. These low book-to-market firms are currently undervalued, but better future growth is expected. Thus, the last three indicator variables — R&D expenses scaled by total assets (RDINT), advertising expenses scaled by total assets (ADINT), and capital expenditure scaled by total assets (CAPINT) — are assigned a value of one if they are greater than the industry median and zero otherwise.

Similar to the construction of the FSCORE, the composite GSCORE is the sum of the indicator variables of these eight fundamental signals.

$$GSCORE_{i,t} = ROA_{i,t} + CFO_{i,t} + Accrual_{i,t} + σ_{NI,i,t} + σ_{SG,i,t} 
+ RDINT_{i,t} + ADINT_{i,t} + CAPINT_{i,t}. \tag{95.3}$$

A higher (lower) GSCORE indicates more (fewer) good fundamental signals of a firm and better financial health for growth stocks. Mohanram (2005) shows that an investment strategy with a long position in high-GSCORE stocks and a short position in low-GSCORE stocks generates excess returns up to two years after the formation of a portfolio. In our model, we employ the FSCORE and the GSCORE as fundamental analysis indicators for value stocks and growth stocks, respectively. These fundamental scores, in addition to technical information such as past returns and trading volume, are expected to improve investors’ ability to separate winners from losers.

# 95.3 Sample Selection and Data Description

# 95.3.1 Sample selection and methodology

We include all non-financial firms listed on the NYSE, AMEX, and NASDAQ that have sufficient monthly return data on CRSP and price and book value