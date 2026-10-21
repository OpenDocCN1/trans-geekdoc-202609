As a result, we obtained a database covering 22 countries that have bank foreign claims and 198 countries that have obligations for the end of 1Q 2015. Thus, the network considered on the basis of the data includes all information about the international borrowings, except for transactions between countries which do not report. According to BIS Statistical Bulletin, our network covers about 94% of total foreign claims and other potential exposures on an ultimate risk basis.

The important aspect of the analysis is the choice of the critical loan amount threshold level for each country. One possible way to define it is to follow the recommendations of the Basel Committee (BCBS, 2013) on large exposure limits (25% of the Tier 1 capital). At the international level, when we deal with banking system's borrowings, choosing an appropriate threshold level (critical loan amount) is not so obvious. We decided to put on the edges of the network not loans, but the value measured by the ratio of loans to the gross domestic product (GDP) of the lending country in order to take into account the relative size of the loan. In this paper the nominal GDP is used. However, GDP measure can be replaced by the total banking system assets or capital estimations. So, suppose that the threshold q be 10% of the nominal GDP.

Another important issue here is to assign grades to the direct influence values for the threshold procedure. In Table 9.12, we propose the following system of grades which in our opinion is reasonable for this case.

The highest grade corresponds to the highest influence value, the lowest grade indicates the absence of influence between elements.

Thus, we can calculate the influence value of each borrower according to our methodology. Table 9.13 contains a list of countries that were in the

# Table 9.12: Grades for direct influence values description.

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