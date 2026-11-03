
In case we want to have a different key for `ipl_csk_dt`, we will have to use the ‘`keyby`’ argument. However, ‘`keyby`’ or ‘`by`’ expects column ‘`j`’ to be provided. We can use the built-in operator `.SD` to pass all the columns or provide a specific column name. **[Table 2.47](#10_Chapter02.xhtml#tab2.47)**, generated using the below code snippet, shows all matching rows for TEAM CSK and selects columns `TEAM`, `COUNTRY`, and `SOLD_PRICE` grouped by `AGE` and `PLAYING_ROLE`:

![](images/page43-03.png)![](images/page43-04.png)![](images/page44-01.png)

**[Table 2.48](#10_Chapter02.xhtml#tab2.48)**, generated using the below code snippet, shows all matching rows for TEAM MI and selects columns `TEAM`, `COUNTRY`, and `SOLD_PRICE` grouped by `AGE` and `PLAYING_ROLE`:

![](images/page44-02.png)

Let us join `ipl_csk_dt`, that is, **[Table 2.47](#10_Chapter02.xhtml#tab2.47)** with `ipl_mi_dt`, that is, **[Table 2.48](#10_Chapter02.xhtml#tab2.48)** using their keys. When we write `ipl_csk_dt[ipl_mi_dt]`, the join operation is going to look up `ipl_csk_dt` using the `AGE` and `PLAYING_ROLE` keys of `ipl_mi_dt`.

1. In **[Table 2.48](#10_Chapter02.xhtml#tab2.48)**, with `AGE==2` and `PLAYING_ROLE==BOWLER`, the `ipl_mi_dt` has three records. We also see in **[Table 2.47](#10_Chapter02.xhtml#tab2.47)** that there are two records corresponding to `AGE==2` and `PLAYING_ROLE==BOWLER`. Each of the records of `ipl_csk_dt` will appear in combination with `ipl_mi_dt`. This will make up for the first six records in joined `data.table`.
2. In **[Table 2.48](#10_Chapter02.xhtml#tab2.48)**, with `AGE==3` and `PLAYING_ROLE==Allrounder`, there are two records. We also see in **[Table 2.47](#10_Chapter02.xhtml#tab2.47)** that there are no records corresponding to `AGE==3` and `PLAYING_ROLE==Allrounder`. Thus, the join operation will report NA values from the `ipl_csk_dt` and show it in combination with `ipl_mi_dt`. This will make up for the next two records in joined `data.table`.

![](images/page44-03.png)

3. In **[Table 2.48](#10_Chapter02.xhtml#tab2.48)**, with `AGE==3` and `PLAYING_ROLE==Batman`, the `ipl_mi_dt` has one record. We also see in **[Table 2.47](#10_Chapter02.xhtml#tab2.47)** that there are three records corresponding to `AGE==3` and `PLAYING_ROLE==Batsman`. Each of the records of `ipl_csk_dt` will appear in combination with `ipl_mi_dt`. This will make up for the last three records in joined `data.table`.

This is a right join and the output is shown in **[Table 2.49](#10_Chapter02.xhtml#tab2.49)**.

![](images/page45-01.png)

Note, that `ipl_csk_dt[ipl_mi_dt, on =.(AGE,PLAYING_ROLE)]` is optional. We did not provide the key, so the join happened on the keys which were set for the `ipl_csk_dt` and `ipl_mi_dt`.

We can suppress the NA records, which will be similar to inner join as shown in **[Table 2.50](#10_Chapter02.xhtml#tab2.50)**:

![](images/page45-02.png)

What if we want to create a join, like `ipl_mi_dt[ipl_csk_dt]` ? This operation will look up `ipl_mi_dt` using the key values of `ipl_csk_dt`.

1. As in **[Table 2.47](#10_Chapter02.xhtml#tab2.47)**, with `AGE==1` and `PLAYING_ROLE==Batsman`, the `ipl_csk_dt` has one record. There is no record in `ipl_mi_dt`, corresponding to `AGE==1` and `PLAYING_ROLE==Batsman` (**[Table 2.48](#10_Chapter02.xhtml#tab2.48)**). Thus, the join operation will report NA values from the `ipl_mi_dt` and show it in combination with `ipl_csk_dt`. This will make up for the first records in the joined `data.table`.

![](images/page45-03.png)![](images/page45-04.png)

2. The next three combinations of `AGE` and `PLAYING_ROLE` in `ipl_csk_dt` (**[Table 2.47](#10_Chapter02.xhtml#tab2.47)**), that is,

• `AGE==1` and `PLAYING_ROLE==Bowler`

• `AGE==2` and `PLAYING_ROLE==Allrounder`

• `AGE==2` and `PLAYING_ROLE==Batsman`

also do not have any corresponding match in `ipl_mi_dt` (**[Table 2.48](#10_Chapter02.xhtml#tab2.48)**). So, the next seven records of the resultant `data.table` will be NA records corresponding to `ipl_mi_dt` and will show up in combination of `ipl_csk_dt`.
3. As in **[Table 2.47](#10_Chapter02.xhtml#tab2.47)**, with `AGE==2` and `PLAYING_ROLE==BOWLER`, the `ipl_csk_dt` has two records. We also see that `ipl_mi_dt` has three records corresponding to `AGE==2` and `PLAYING_ROLE==BOWLER` (**[Table 2.48](#10_Chapter02.xhtml#tab2.48)**). Each of the records of `ipl_mi_dt` will appear in combination with `ipl_csk_dt`. This will make up for the next six records in joined `data.table`.
4. In **[Table 2.47](#10_Chapter02.xhtml#tab2.47)**, with `AGE==2` and `PLAYING_ROLE==W.Keeper`, the `ipl_csk_dt` has one record. The `ipl_mi_dt` has no records corresponding to `AGE==2` and `PLAYING_ROLE==W.Keeper` (**[Table 2.48](#10_Chapter02.xhtml#tab2.48)**). Thus, the join operation will report NA values from the `ipl_mi_dt` and show it in combination with `ipl_csk_dt`. This will make up for the next record in joined `data.table`.
5. Finally, With `AGE==3` and `PLAYING_ROLE==Batman`, the `ipl_csk_dt` has three records as seen in **[Table 2.47](#10_Chapter02.xhtml#tab2.47)**. We also see in **[Table 2.48](#10_Chapter02.xhtml#tab2.48)** that `ipl_mi_dt` has one record corresponding to `AGE==3` and `PLAYING_ROLE==Batsman`. This record of `ipl_mi_dt` will appear in combination with `ipl_csk_dt`. This will make up for the last three records in joined `data.table`.

![](images/page46-01.png)

**[Table 2.51](#10_Chapter02.xhtml#tab2.51)** shows the joined table following the above steps:

**[Table 2.52](#10_Chapter02.xhtml#tab2.52)** shows the suppressed table with no match records being removed and making it an inner join (left table having matching rows in right table).

![](images/page46-02.png)

Some more join operations are shown below. **[Table 2.53](#10_Chapter02.xhtml#tab2.53)** shows the join operation of `ipl_mi_dt` on `ipl_csk_dt` and the `SOLD_PRICE` for each key:

![](images/page46-03.png)

**[Table 2.54](#10_Chapter02.xhtml#tab2.54)** shows all the records from `ipl_csk_dt` which do not have a matching record in `ipl_mi_dt`. This is as good as looking up the `ipl_csk_dt` for the `AGE` and `PLAYING_ROLE` combination which is not present in `ipl_mi_dt`:

![](images/page46-04.png)![](images/page47-01.png)![](images/page47-02.png)![](images/page47-03.png)

What if we want to join the two `data.tables` with a column name which is not set as a key? This can be done by explicitly passing the column name in `on = *` argument. **[Table 2.55](#10_Chapter02.xhtml#tab2.55)** shows the join of `ipl_csk_dt` with `ipl_mi_dt` based on the country name present in `ipl_mi_dt`.

Join operation can be used to merge data tables by using the syntax ‘`Table1[Table2]`’. The order of the table in this syntax drives whether the resultant table is a left join or a right join. The columns used to perform the match is specified using ‘`on`’ operation. If ‘`on`’ operator is not specified, then the join happens based on the table keys.

![](images/page48-01.png)![](images/page48-02.png)![](images/page48-03.png)

## 2.8 | Data Table, Data Frame, and Package DT

Let us see the basic differences between the following:

1. `data.table` and `data.frame`
2. package `data.table` and package `DT`

### 2.8.1 Data Table vs. Data Frame

Experienced users of R understand the advantages of creating a `data.table` compared to reading as `data.frame`. Here, we will highlight one important distinction between reading a file using `fread()` (creates a `data.table`) and `read.table()` (creates a `data.frame`). While reading a file as `data.frame` using base R `read.table()`, we will get a rowname which we also refer to as an index column. For demonstration purposes, we have used `read.table()` to read the `ipl.csv` file and create a new `data.frame` as shown in **[Table 2.56](#10_Chapter02.xhtml#tab2.56)**.

![](images/page49-01.png)![](images/page49-02.png)
