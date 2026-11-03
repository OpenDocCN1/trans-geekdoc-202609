
### 2.
We have grouped the players by `AGE`, `PLAYING_ROLE`. Instead of using `by`, we have used `keyby` which returns an ordered set.

### 3.
We have passed the column names on which we want to compute the average statistics in `.SDcols`

**[Table 2.41](#10_Chapter02.xhtml#tab2.41)** shows the outcome of the above steps as applied through the code snippet below:

![](images/page39-03.png)![](images/page39-04.png)![](images/page40-01.png)

The `by` operator can be used to group the compute operation on some column w.r.t. the other columns. This argument can also take conditional expressions.

The `.N` is a built-in symbol and holds the number of observations in the current group. This can be used to get the count of observations based on conditional filter on rows.

The `.SD`, which stands for subset of data, along with `.SDcols` is another built-in symbol which can be used to apply compute operations, such as calculating mean, median, standard deviation, etc., on the columns specified under `.SDcols`.

**TABLE 2.42** | T20 wickets and test wickets taken by each player based on the playing role

| PLAYING_ROLE || WICKETS_TAKEN |
| --- | --- |
| Allrounder || 15 |
| --- | --- |
| Allrounder || 19 |
| Allrounder || 47 |
| Allrounder || 73 |
| Allrounder || 5 |
| Allrounder || 2 |

`.SDcols` is optional. However, in this situation, `lapply` will throw an error as the dataset also contains character columns and computing mean does not hold true for character variables.

The compute operation on columns is very flexible in `data.table`. An operation to even flatten a column can be done using `data.table` query syntax. For example, **[Table 2.42](#10_Chapter02.xhtml#tab2.42)** concatenates T20 wickets and test wickets taken by each player based on the playing role:

![](images/page40-02.png)

### 2.6 | Keys and Binary Search-Based Subset
The use of keys in `data.table` makes it much more efficient in subsetting and in handling subsequent downstream activities. Keys can be intuitively thought of as a `row.names` of base R `data.frame` with the exception that:

**1.** Keys can be set on multiple columns and the columns can be of different data types.

**2.** Uniqueness is not enforced in keys

Setting keys in a `data.table`

**1.** Rearranges the rows based on column names provided as keys. The ordering is always in an ascending order.

**2.** Marks the columns used as key columns by setting an attribute called `sorted` to the `data.table`.

![](images/page41-01.png)

A point to note while using keys is that the query structure does not change. This means all the querying syntax discussed in sections 2.4 and 2.5 can still be done using keys, with the advantage of speed and efficiency while dealing with large dataset.

Let us set `COUNTRY` and `TEAM` as keys in `ipl_dt` (**[Table 2.43](#10_Chapter02.xhtml#tab2.43)**)

![](images/page41-02.png)

We can notice from **[Table 2.43](#10_Chapter02.xhtml#tab2.43)** that `ipl_dt` is ordered in ascending order of `COUNTRY` and then by `TEAM`. We can subset the `ipl_dt` by `COUNTRY` or `TEAM` or a combination of both. **[Table 2.44](#10_Chapter02.xhtml#tab2.44)** shows the subset of data by filtering out players from Australia and playing for Chennai Super Kings.

![](images/page41-03.png)

In the above subset query, `AUS` was looked for in the first key column `COUNTRY`. Within the matching rows for `AUS`, `CSK` is matched against the second key column `TEAM`. Since we did not provide any operation on `j`, the query returned all columns corresponding to those row indices.

**[Table 2.45](#10_Chapter02.xhtml#tab2.45)** shows the number of wickets taken by players from Sri Lanka and playing for Mumbai Indians.

![](images/page41-04.png)![](images/page41-05.png)

**TABLE 2.45** | Wickets taken by players of Country SL and playing for Team MI

| PLAYING_ROLE || WICKETS_TAKEN |
| --- | --- |
| Allrounder || 13 |
| --- | --- |
| Bowler || 17 |
| Bowler || 83 |

Notice that the key set for `ipl_dt` was `COUNTRY` `TEAM`

![](images/page42-01.png)

whereas in the above query, the `data.table` has a key set as `PLAYING_ROLE`

![](images/page42-02.png)

Querying with keys performs a binary search compared to the vector scan. Without setting in key, when we write a query like `ipl_dt[COUNTRY == 'AUS' & TEAM == 'CSK']`, it performs a vector scan.

To understand the point, let us assume that `ipl_dt` is a large dataset with one million records. When we write `ipl_dt[COUNTRY == 'AUS' & TEAM == 'CSK']`, the operation, done internally, will be as follows:

**1.** A row by row search performed on Column `COUNTRY` for a value `AUS`. The result will be a logical vector of size one million marking TRUE, FALSE, or NA.

**2.** A row by row search performed on Column `TEAM` for a value `CSK`. The result will be a logical vector of size one million marking TRUE, FALSE, or NA.

**3.** Element wise `&` operation performed on the above two logical vectors returned from step 1 and step 2. Value will be returned wherever the operations on the two logical vectors evaluates to TRUE.

While doing the same query, that is, `ipl_dt[.( 'AUS', 'CSK' )]` by setting `COUNTRY` and `TEAM` as keys, the operation will be halved as the data is sorted based on `COUNTRY` and `TEAM`. The operation which will be done internally will be:

**1.** Middle element of the sorted column `COUNTRY` will be compared with the value `AUS`. Since the value `AUS` is smaller than the middle element, the search space will be set to the upper half of the column.

**2.** Again, the middle element of the upper half of the column `COUNTRY` will be compared to the value `AUS` and the iteration will continue till the value `AUS` is found.

**3.** The above two steps will be repeated for column `TEAM` to find the value for `CSK`.

**4.** The `&` operation on the above two logical vectors returns the value wherever the expression evaluates to TRUE.

Thus, the binary search on a large dataset will be much faster compared to a vector scan. We can see that the binary search reduces the search space by almost half and thus is incredibly fast while querying a large dataset.

### 2.7 | Join operations
We may need to combine columns from multiple data frames into one single data frame. In this case, both data frames need to have a common column. The remaining column values can then be retrieved from both the data frames and joined to create a row in the resulting data frame.

To merge two data frames, `data.table` querying syntax with `on` argument can be used. It can be called on one of the data frames and the other data frame can be passed as a parameter to it. The argument `on` is the common column or a key in data frames and should be present in both the data frames.

**1.** `X[Y, on=*]` is a join operation, looking up `X`'s rows using `Y`'s column name provided using `on=*` or key values of `Y`, as an index. This returns all the rows from `Y` with matching records from `X`.

**2.** `Y[X, on=*]` is a join operation, looking up `Y`'s rows using `X`'s column name provided using `on=*` or key values of `X`, as an index. This returns all the rows from `X` with matching records from `Y`.

Data frames can be joined based on multiple common columns. The join type can be of inner, outer, left, or right joins and should be specified in the `how` parameter.

Let us create two `data.table` representing Chennai Super Kings and Mumbai Indians. We have set `COUNTRY` and `TEAM` as keys by using the below code snippet:

![](images/page43-01.png)

Using the below code snippet, **[Table 2.46](#10_Chapter02.xhtml#tab2.46)** shows the players from `CSK` based on just the key named `TEAM`.

![](images/page43-02.png)

In **[Table 2.46](#10_Chapter02.xhtml#tab2.46)**, the key for `ipl_csk_dt` will be same as that of `ipl_dt`, that is, `COUNTRY` and `TEAM`.
