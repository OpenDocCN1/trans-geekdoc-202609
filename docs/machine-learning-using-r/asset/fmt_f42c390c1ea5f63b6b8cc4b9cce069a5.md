
`1.` We will subset rows by that is, `C(“CSK’”,MI”,KKR”,RCB’)` on `TEAM`. The use of `on` operator results in binary search and thus is faster compared to writing `TEAM == ‘CSK’ & TEAM == ‘MI’ & TEAM == ‘KKR’ & TEAM == ‘RCB’`.

`2.` Perform operations on column `j`, that is, calculate `TOTAL_WKTS` as a sum of `PAST_IPL_WKT` groupby by `TEAM` using the following code.

**[Table 2.26](#10_Chapter02.xhtml#tab2.26)** shows the outcome of the below code:
![](images/page33-03.png)
Based on this data, it seems that the previous experience level of bowlers contributed to the teams’ performance in IPL 2011 as well. We can re-write the query which resulted in **[Table 2.26](#10_Chapter02.xhtml#tab2.26)**, by using special keyword `.EACHI` which will iterate through each subset of `i`.
![](images/page33-04.png)

### TABLE 2.26 | Total number of wickets taken in previous IPL editions by Team CSK, MI, KKR, and RCB
| TEAM || TOTAL_WKTS |
| --- | --- |
| CSK || 202 |
| --- | --- |
| MI || 178 |
| KKR || 46 |
| RCB || 58 |

### TABLE 2.27 | Total runs scored in previous IPL editions by various teams
| TEAM || TOTAL_IPL_RUNS |
| --- | --- |
| CSK || 8,649 |
| --- | --- |
| CSK+ || 1,118 |
| MI || 3,460 |
| MI+ || 4,855 |
| KKR || 278 |
| KKR+ || 7,322 |
| RCB || 3,952 |
| RCB+ || 7,187 |

**[Table 2.27](#10_Chapter02.xhtml#tab2.27)** shows IPL runs scored by players of the top four teams using the following code:
![](images/page34-01.png)
In **[Table 2.27](#10_Chapter02.xhtml#tab2.27)**, `CSK+` implies that the players have played for other teams apart from `CSK`. Note that the statistics above are just a representation based on the sample of 130 players in this dataset. In reality, the figures may far exceed these statistics. To corroborate this fact, let us look into the batting line-up for `MI` based on the runs scored by players in past T20 matches (**[Table 2.28](#10_Chapter02.xhtml#tab2.28)**).
![](images/page34-02.png)
The maximum runs scored for `MI` is by Indian players (**[Table 2.28](#10_Chapter02.xhtml#tab2.28)**). **[Table 2.29](#10_Chapter02.xhtml#tab2.29)** shows the list of players of `MI` based on `COUNTRY`, `PLAYING_ROLE`, and `RUN_S`
![](images/page34-03.png)![](images/page34-04.png)![](images/page35-01.png)
The `on` parameter in `data.table` can be used for performing efficient conditional filter operation on columns.
The `on` parameter internally uses joins to give faster result on large data sets.
The `.EACHI` which is an inbuilt symbol can be used in `by` operator to perform compute operations on columns for each unique values filtered using `on` operator.
As is evident, this is not the complete list of players who played for `MI`. We have a team `MI+` as well, which contains those who played for other teams in the past.
Let us try to deep dive into the bowling department. How many wickets were taken by players from the top four nations (based on the number of players in the IPL season) representing `CSK`, `MI`, `KKR`, and `RCB`? **[Table 2.30](#10_Chapter02.xhtml#tab2.30)** shows the wickets taken by the `AUS`, `SA`, `SL`, and `PAK` players for team `CSK`.
![](images/page35-02.png)
Well!!! Out of the total 202 wickets taken by `CSK`, 113 came through players from `AUS` and `SA`. [Table 2.31](#10_Chapter02.xhtml#tab2.31) shows the list of bowlers from these two nations who played for `CSK`.
![](images/page35-03.png)
**[Table 2.31](#10_Chapter02.xhtml#tab2.31)** can also be obtained by the below query:
![](images/page35-04.png)![](images/page35-05.png)![](images/page35-06.png)

### 2.5 | Group by Operations
The tabulation of data based on the feature list can be done within the `data.table`. We will compute the average wicket taken by players in past IPL appearances using the following code.
![](images/page36-01.png)
In the above query, we can use `min()`, `quantile()`, `mean()`, `median()`, and `max()` to get a specific summary statistic for a numeric column. **[Table 2.32](#10_Chapter02.xhtml#tab2.32)** shows the average number of T20 wickets taken by players grouped by `PLAYING_ROLE`
![](images/page36-02.png)
**[Table 2.33](#10_Chapter02.xhtml#tab2.33)** shows the average number of T20 wickets taken by `AGE` category (less than 25 years, between 25 and 35 years, and over 35 years) and `PLAYING_ROLE`:
![](images/page36-03.png)
To order the results by column, we can use the below query. Note that **[Table 2.33](#10_Chapter02.xhtml#tab2.33)** and **[Table 2.34](#10_Chapter02.xhtml#tab2.34)** are same, but the result is ordered by `PLAYING_ROLE`.
![](images/page36-04.png)

### TABLE 2.32 | Average wickets taken by Playing role in past IPL edition
| PLAYING_ROLE || AVERAGE_WKT_T20 |
| --- | --- |
| Allrounder || 19.028571 |
| --- | --- |
| Bowler || 32.818182 |
| Batsman || 3.128205 |
| W. Keeper || 0.000000 |
![](images/page36-05.png)![](images/page37-01.png)
Note that the `keyby` argument does not only order the `data.table` but also sets the columns as keys. The concept of keys and its usefulness in fast search will be discussed later.
**[Table 2.35](#10_Chapter02.xhtml#tab2.35)** shows the average number of T20 wickets taken by `AGE`, `COUNTRY`, `TEAM`, and `PLAYING_ROLE`.
![](images/page37-02.png)
How many players auctioned in 2009 are still with `CSK`?
![](images/page37-03.png)
The above query can also be written with `.N`, which is a built-in symbol and holds the number of observations in the current group.
![](images/page37-04.png)![](images/page37-05.png)![](images/page38-01.png)
**[Table 2.36](#10_Chapter02.xhtml#tab2.36)** shows the total number of players for each country-team pair for a particular playing role `Bowler`.
![](images/page38-02.png)
**[Table 2.37](#10_Chapter02.xhtml#tab2.37)** shows **[Table 2.36](#10_Chapter02.xhtml#tab2.36)** in a sorted order. The result is sorted in ascending order for country and decreasing order for team
![](images/page38-03.png)
In the above query, the bowler count was stored in a variable `bowler_count_dt` and then ordered in the next line. We can avoid the temporary variable by chaining the above two queries. The below code snippet will also result in **[Table 2.37](#10_Chapter02.xhtml#tab2.37)**.
![](images/page38-04.png)
The `by` argument of `data.table` can take column names as well as expressions. **[Table 2.38](#10_Chapter02.xhtml#tab2.38)** shows the count of players who have taken more than five wickets in T20 cricket, more than 10 wickets in One-Day Internationals, and more than 20 wickets in Test cricket.
![](images/page38-05.png)
In **[Table 2.38](#10_Chapter02.xhtml#tab2.38)**, the first row corresponds to `T20_5W >5 = TRUE`, `ODI_10W>10 = FALSE`, `TEST_20W>20=FALSE` and the total number of records satisfying this criteria is 15 players.
**[Table 2.39](#10_Chapter02.xhtml#tab2.39)** shows the count which satisfies all three conditions at the same time:
![](images/page38-06.png)![](images/page38-07.png)![](images/page39-01.png)

### TABLE 2.39 | Count of players who have taken more than five wickets in T20 cricket, more than 10 wickets in One-Day Internationals, and more than 20 wickets in Test cricket (all conditions satisfied)
| Condition || N |
| --- | --- |
| FALSE || 89 |
| --- | --- |
| TRUE || 41 |
Another useful built-in symbol in `data.table` is `.SD`, which stands for subset of data. `.SD` in itself is a `data.table` which holds the data of the subset defined using `by` argument of `data.table`. **[Table 2.40](#10_Chapter02.xhtml#tab2.40)** shows the `ipl_dt`, which is printed using the `.SD` symbol.
![](images/page39-02.png)
`.SD` symbol can be used with `lapply()` function to iterate through multiple columns at the same time and compute statistics we are interested in calculating. Let us calculate the average number of wickets taken and average number of runs scored by players in all three formats of the game. For doing this:
`1.` We have used `lapply()` to iterate through the columns.
