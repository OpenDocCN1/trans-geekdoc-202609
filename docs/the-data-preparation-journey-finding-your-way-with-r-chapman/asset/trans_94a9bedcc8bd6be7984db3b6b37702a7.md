

由于原始 Excel 文件中的“NA”字符串，以 `train_` 开头的变量被存储为字符类型 `_<chr>_`。如果改为逻辑类型存储，这类变量在我们的分析中会更有用。一种选择是在我们环境中对现有对象修改变量类型，或者（采用“在导入阶段尽可能处理”的方法）我们可以重新读取文件内容并在此时应用变量类型定义。第二种方案还让我们能够明确地将那些编码为其他字符的变量定义为 NA。这里 NA 表示为“NA”，但在其他数据中，你可能会遇到“not available”、“9999”、“-”以及许多其他可能性。

```
df_HR_train <- 
  readxl::read_excel(
    dpjr::dpjr_data("cr25/cr25_human_resources.xlsx"),
    sheet = "df_HR_train",
    col_types = c("text", "logical", "logical", "logical", "logical"),
    na = "NA"
  )

glimpse(df_HR_train, width = 65)
```

```
## Rows: 999
## Columns: 5
## $ emp_id       <chr> "ID001", "ID002", "ID003", "ID004", "ID005", ...
## $ train_security <lgl> TRUE, FALSE, TRUE, FALSE, FALSE, FALSE, ...
## $ train_crm     <lgl> TRUE, FALSE, TRUE, TRUE, FALSE, TRUE, TRUE, ...
## $ train_qc      <lgl> NA, FALSE, FALSE, FALSE, FALSE, NA, FALSE, ...
## $ train_history <lgl> TRUE, TRUE, TRUE, TRUE, TRUE, TRUE, TRUE, ...
```

现在这些变量都以适合其表示内容的类型存储，应用 R 的 `summary()` 函数为我们提供了另一种查看数据的方式。

```
summary(df_HR_train)
```

```
##      emp_id      train_security  train_crm      train_qc
##  Length:999   Mode :logical    Mode :logical  Mode :logical
##  Class :character FALSE:500      FALSE:219     FALSE:494
##  Mode  :character TRUE :462      TRUE  :771    TRUE  :110
##                 NA's :37        NA's :9      NA's :395
##  train_history
##  Mode :logical
##  FALSE:16
##  TRUE :971
##  NA's :12
```

## 11.2 探索性数据分析

这个输出是我们的初步 EDA。我们注意到了什么？由于没有数值，我们不需要寻找异常值、哨兵值或值的范围。

在像这样的调查数据框中，出现一些 NA 值是意料之中的，少量 NA 值可能不会对分析产生影响。但 `train_qc` 变量有 395 个缺失值——几乎占 999 条记录的 40%。大量缺失值可能有其原因，分析师的部分责任就是理解这种情况发生的原因。首先，在关于数据的笔记中记录你观察到的这一现象。

对数据及其来源的透彻理解将确保你的分析准确无误。有必要对此情况做进一步调查（并保存记录）。你可以先查看随文件收到的数据文档。如果那里没有解释，可与了解数据采集方式的人员交流，然后与人力资源部门的人员交流——也许有一项政策豁免了一部分员工参加原本的必修课程。

### 11.2.1 数据可视化

图表可以向我们展示大量无法在汇总统计中表达的信息。让我们来探索 `df_HR_main` 工作表中的出生日期变量。

```
df_HR_main <-
  read_excel(
    path = dpjr::dpjr_data("cr25/cr25_human_resources.xlsx"),
    sheet = "df_HR_main",
    range = "B5:E1004"
  )

head(df_HR_main)
```

A tibble: 6 × 4

| emp_id | date_of_birth         | name              | gender |
|---|---|---|---|
| ID001 | 1981-05-27 00:00:00 | Avril Lavigne | Female |
| ID002 | 1973-09-24 00:00:00 | Katy Perry | Female |
| ID003 | 1966-11-29 00:00:00 | Chester Bennington | Male |
| ID004 | 1982-09-17 00:00:00 | Chris Cornell | Male |
| ID005 | 1976-07-17 00:00:00 | Bryan Adams | Male |
| ID006 | 1965-07-03 00:00:00 | Courtney Love | Female |

我们将再次使用 glimpse() 和 summary() 函数来开始探索：

```
glimpse(df_HR_main)
```

```
## Rows: 999
## Columns: 4
## $ emp_id <chr> "ID001", "ID002", "ID003", "ID004", "ID005", "ID006", ...
## $ date_of_birth <dttm> 1981-05-27, 1973-09-24, 1966-11-29, 1982-09-17, ...
## $ name <chr> "Avril Lavigne", "Katy Perry", "Chester Bennington", ...
## $ gender <chr> "Female", "Female", "Male", "Male", "Male", "Female", ...
```

```
summary(df_HR_main)
```

```
## emp_id date_of_birth name
## Length:999 Min. :1901-01-01 00:00:00.000 Length:999
## Class :character 1st Qu.:1965-10-25 12:00:00.000 Class :character
## Mode :character Median :1976-06-21 00:00:00.000 Mode :character
## Mean :1976-01-14 17:53:52.432
## 3rd Qu.:1987-03-08 12:00:00.000
## Max. :1999-01-01 00:00:00.000
## gender
## Length:999
## Class :character
## Mode :character
##
##
##
```

在这些信息中有一个有趣的异常——你可能已经发现了。如果我们绘制数据，这个异常会明显得多。下面是一个密度图，显示了员工出生日期的分布：

```
ggplot(df_HR_main, aes(x = date_of_birth )) +
  geom_density()
```

![](img/b86622d1e9ca82b3cbec45faaffaaf26_160_0.png)

通过图表很容易看到，有少量出生日期在 1900 年前后，然后从 20 世纪 50 年代开始数量激增。

在查看 `summary()` 函数和图表的结果后，我们可能想要进一步探索 `date_of_birth` 变量，以下是一些问题：

- 最早的出生日期是 1901-01-01。这意味着截至数据集创建的时间点 2020-01-01，最年长的员工为 119 岁。你可能已经知道，只有一位年龄经过独立验证的人活到了 120 岁（其去世时为 122 岁 164 天）。维基百科，“经验证的最长寿者名单”¹。一种可能是 1901-01-01 是哨兵值，作为未知或缺失值的占位符。进一步探索将帮助我们理解；我们可以先统计某个特定日期的案例数量：

```r
df_HR_main |>
  group_by(date_of_birth) |>
  tally() |>
  arrange(desc(n)) |>
  head()
```

```
## # A tibble: 6 x 2
##   date_of_birth       n
##   <dttm>          <int>
## 1 1901-01-01 00:00:00 10
## 2 1955-10-26 00:00:00 2
## 3 1955-10-31 00:00:00 2
## 4 1955-11-22 00:00:00 2
## 5 1957-09-11 00:00:00 2
## 6 1958-10-28 00:00:00 2
```

有 10 个案例的出生日期为 1901-01-01。这正是我们使用哨兵值时可能看到的模式。

另一种调查方法是根据出生日期推导出一个单独的“年龄”变量，并使用箱线图按某个分类变量对年龄进行可视化，以便更明显地看出异常值。我们猜想出生日期的“1901-01-01”哨兵值可能与某个职业类别有关。利用关系数据库的“连接”技能，我们将“transaction”表中的职业变量连接起来，并在绘图中使用职业作为分组变量。你会注意到 transaction 表的结构不适合我们的分析需求，因此我们必须先进行一些数据整理。

```
# step 1; read transaction table, which contains occupation
df_HR_transaction <- 
  read_excel(
    path = dpjr::dpjr_data("cr25/cr25_human_resources.xlsx"),
    sheet = "df_HR_transaction",
    na = "NA"
  )

# step 2; determine occupation on the date the table was created
df_HR_occupation_2020 <- df_HR_transaction |> 
  group_by(emp_id) |> 
  summarize(occupation_current = max(occupation, na.rm = TRUE))

# step 3; in the main table calculate age and
#   join the occupation table created in step 2,
#   then plot the result
df_HR_main |> 
  # calculate age on January 1, 2020
  mutate(age_2020 = 
          date_of_birth %--% ymd("2020-01-01") %/% years(1)) |> 
  # join the current occupation table
left_join(df_HR_occupation_2020, by = "emp_id") |>
# plot
ggplot(aes(x = occupation_current, y = age_2020)) +
geom_boxplot()
```

![](img/b86622d1e9ca82b3cbec45faaffaaf26_162_0.png)

在箱线图可视化中，我们看到哨兵值出现在五种职业中的四种中，因此我们的猜想并不正确。

## 11.3 验证方法

探索性数据分析使用可视化和数据摘要扫描来发现潜在脏数据，而验证则是一种结构化的测试过程。

### 11.3.1 {validate} 包

与其他数据分析主题一样，R 用户社区的人们也遇到了脏数据问题，并编写和共享了一些函数来帮助我们其他人。{validate} 包（van der Loo and de Jonge, 2021, van der Loo et al. (2022)）由方法学家编写并维护，他们供职于

