
`Listing 2.25` 初始化数据框 `df` 为 `duplicates.csv` 的内容，然后显示 `df`。接下来的部分显示第 4 到第 7 行（使用 `loc`），以及第 4 到第 6 行（使用 `iloc`）。

Listing 2.29 包含一个导入语句，然后初始化变量 `df` 为 CSV 文件 `emp_ages.csv` 的内容。下一个代码片段定义变量 `new_row`，其内容与 `df` 的结构兼容，然后将 `new_row` 的内容追加到 Pandas 数据框 `df` 中。现在运行 Listing 2.29 中的代码，你会看到以下输出：

```
fname   lname   age
0   New   Person   777
1   Jane   Smith   32
2   Dave   Smith   10
```

## Handling Missing Data in Pandas

Listing 2.30 显示 `employees2.csv` 的内容，Listing 2.31 显示如何在 Pandas 数据框中查找重复行和缺失值，分别对应 `employees2.csv` 和 `dup_missing.py`。

### Listing 2.30: employees2.csv

```
name,year,month
Jane-Smith,2015,Aug
Jane-Smith,2015,Aug
Dave-Smith,2020,
Dave-Stone,,Apr
Jane-Jones,2018,Dec
Jane-Stone,2017,Feb
Jane-Stone,2017,Feb
Mark-Aster,,Oct
Jane-Jones,NaN,Jun
```

### Listing 2.31: missing_values.py
