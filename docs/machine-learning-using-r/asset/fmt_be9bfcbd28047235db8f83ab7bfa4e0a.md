
To select all the rows where Test match runs scored by the player are greater than 5,000, we can use the code snippet provided below to generate output **[Table 2.11](#10_Chapter02.xhtml#tab2.11)**.

![](images/page27-02.png)

The code snippet below selects all rows where Test runs scored by the player is greater than 5,000 and the number of Test wickets is more than 100. As seen in **[Table 2.12](#10_Chapter02.xhtml#tab2.12)**, Jacques Kallis is the only player in IPL 2011 to have achieved this feat.

![](images/page27-03.png)

### 2.4.3 Basic Column Subset Operations

In `data.table`, several operations on column can be performed with ease. For example, the below coded chunk will return a column (`PLAYING_ROLE`) as a vector.

![](images/page27-04.png)![](images/page27-05.png)![](images/page27-06.png)

**TABLE 2.13** | First six observations of the playing role from IPL data

| ROLE |

| --- |

| Allrounder |

| --- |

| Bowler |

| Bowler |

| Bowler |

| Batsman |

| Batsman |

**[Table 2.13](#10_Chapter02.xhtml#tab2.13)** shows the above result as a `data.table` by using the following code:

![](images/page28-01.png)

“.()“ in the aforementioned code is just an alias for `list`. This means we can name columns within `.()` and have named the list as ‘`ROLE`’ and show the first six rows with `head()` . In case the column is not named, it will be named `V1`, by default.

We can apply certain math operation on the columns from within the `data.table`. Say, we want to get the total amount spent by all franchises. The below code snippet will help us get the number, which is $6.7 million.

![](images/page28-02.png)

**[Table 2.14](#10_Chapter02.xhtml#tab2.14)** gives the list of countries represented in the IPL and the count of players from each of those countries.

![](images/page28-03.png)

Apart from India - Australia, South Africa, Sri Lanka, and Pakistan were the top four nations with most representation in IPL 2011.

**[Table 2.15](#10_Chapter02.xhtml#tab2.15)** shows the snapshot of the first five rows and the first 10 features of the `data.table`.

![](images/page28-04.png)

**TABLE 2.14** | Count of players by country

| COUNTRY || Freq |

| --- | --- |

| AUS || 22 |

| --- | --- |

| BAN || 1 |

| ENG || 3 |

| IND || 53 |

| NZ || 7 |

| PAK || 9 |

| SA || 16 |

| SL || 12 |

| WI || 6 |

| ZIM || 1 |

![](images/page29-01.png)![](images/page29-02.png)

The below code can be used to generate **[Table 2.16](#10_Chapter02.xhtml#tab2.16)** which shows the first five rows of the dataset with `PLAYER_NAME`, `AGE` , `COUNTRY`, and `TEAM`:

![](images/page29-03.png)

Let us select column `PAST_IPL_WKTS` (wickets taken in IPL) and column `T_WKTS` (wickets taken in test cricket) and calculate a new column `TOTAL_WKTS` which is the sum of `PAST_IPL_WKTS` and `T_WKTS`. **[Table 2.17](#10_Chapter02.xhtml#tab2.17)** shows the outcome of the below code snippet:

![](images/page29-04.png)

Note that the code snippet created a new `data.table` but did not insert a new column `TOTAL_WKTS` in the `ipl_dt`. This also means there was a copy of `ipl_dt` created when we wrote the above statement. This is inefficient, and can create a lot of overhead and consume more memory while dealing with a large dataset.

`data.table` provides `:=` operator can be used to add/update/delete a column. Note that this can be used only on column `j` but can be combined with the querying syntax of `data.table`, that is, `DT[i,j, by + other arguments]`. The syntax for ‘`:=`‘ is `LHS := RHS`

![](images/page29-05.png)![](images/page30-01.png)

`LHS` takes a character vector of column names and `RHS` a list of values.

**[Table 2.18](#10_Chapter02.xhtml#tab2.18)** adds a new column `TOTAL_WKTS` in ‘`ipl_dt`‘ using the below code.

![](images/page30-02.png)

Note that the **[Table 2.18](#10_Chapter02.xhtml#tab2.18)** does not show the `TOTAL_WKTS` as we are showing the first 10 columns of the ‘`ipl_dt`‘. **[Table 2.18](#10_Chapter02.xhtml#tab2.18)** can also be obtained by writing the query in a functional form, as shown below:

![](images/page30-03.png)

Let us say we would like to delete column `Ln(soldp)`. **[Table 2.19](#10_Chapter02.xhtml#tab2.19)** will be the outcome from the below code snippet. Column `Ln(soldp)` will disappear from **[Table 2.19](#10_Chapter02.xhtml#tab2.19)** (**Note:** Variable `Ln(soldp)` comes after column 10 in the data, and thus does not appear in **[Tables 2.18](#10_Chapter02.xhtml#tab2.18)** and **[2.19](#10_Chapter02.xhtml#tab2.19)**).

![](images/page30-04.png)

We can use `: =` operator to replace values in a column. Assume that wherever the strike rate of the bowlers in T20 cricket is zero, and we would like to replace that value with the strike rate of the bowlers in ODIs. **[Table 2.20](#10_Chapter02.xhtml#tab2.20)** shows we just have one such case in `ipl_dt`.

![](images/page30-05.png)![](images/page30-06.png)![](images/page31-01.png)

Moreover, the strike rate for Abdur Razzak in ODI matches is

![](images/page31-02.png)

For such an operation, if we use `:=` operator, it will make changes in the original `ipl_dt` itself. For many reasons, we may not want that in the original `data.table`. The `copy()` function can help create a copy of the `ipl_dt` on which we will use the `:=` operator.

![](images/page31-03.png)

We can see that the T20 Bowling Strike rate is replaced by the ODI Bowling Strike rate.

![](images/page31-04.png)

Let us add a new column which shows the maximum sold price for each pair of `PLAYING_ROLE`, `TEAM` combination. **[Table 2.21](#10_Chapter02.xhtml#tab2.21)** shows the outcome of the below code snippet:

![](images/page31-05.png)

### 2.4.4 Basic Row and Column Select and Compute Operations

In this section, we will understand the use of row and column selection and applying certain computations on the selected rows and columns.

For example, let us create a table of all players from Australia, South Africa, Sri Lanka, and Pakistan in the top four teams of IPL 2011. Remember that the top four teams were `CSK`, `MI`, `KKR`, and `RCB`.

![](images/page31-06.png)![](images/page32-01.png)

**[Table 2.22](#10_Chapter02.xhtml#tab2.22)** shows the players from `CSK` whose country of origin was Australia, South Africa, Sri Lanka, or Pakistan.

![](images/page32-02.png)

**[Table 2.23](#10_Chapter02.xhtml#tab2.23)** shows the players from `MI` whose country of origin was Australia, South Africa, Sri Lanka, or Pakistan.

![](images/page32-03.png)

Readers are encouraged to create similar tables for `KKR` and `RCB`.

It is interesting to note from **[Table 2.22](#10_Chapter02.xhtml#tab2.22)** that `CSK` had six players in their squad from Australia and South Africa but none from Sri Lanka or Pakistan. In `data.table`, a query like `ipl_dt[COUNTRY == 'SA']` is internally optimized to use binary search and will provide faster results on a large dataset.

However, for more complex queries like the ones used to create **[Table 2.22](#10_Chapter02.xhtml#tab2.22)** and **[Table 2.23](#10_Chapter02.xhtml#tab2.23)**, `data.table` gives a provision to use a parameter ‘`on`’. This parameter helps in fast sub setting using joins. The below code snippet implements ‘`on`’ to query `CSK` players who are from `AUS`, `SA`, `SL`, and `PAK`, and will give the output as shown in **[Table 2.24](#10_Chapter02.xhtml#tab2.24)**.

![](images/page32-04.png)

As shown in **[Table 2.24](#10_Chapter02.xhtml#tab2.24)**, the no-match returns `NA`, implying that there were no players from Sri Lanka and Pakistan who played for `CSK`. To suppress the no-match result, we can execute the below code snippet, which will result in **[Table 2.25](#10_Chapter02.xhtml#tab2.25)**.

![](images/page32-05.png)![](images/page32-06.png)![](images/page33-01.png)![](images/page33-02.png)

We will now try to get the total number of wickets taken in previous IPL editions by players in the top four teams of the IPL. To do so:
