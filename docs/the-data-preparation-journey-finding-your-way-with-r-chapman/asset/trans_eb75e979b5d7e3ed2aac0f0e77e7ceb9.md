
```
    col_names = c("first", "last", "state", "unique_id")
    )
```

```text
## # A tibble: 3 x 4
##   first last      state unique_id
##   <chr> <chr>     <chr> <chr>
## 1 Toni  Morrison  IL    DJ-1944-QF96
## 2 Kurt  Vonnegut  IN    XN-5632-TP58
## 3 Walt  Whitman   NY    LW-1752-TD08
```

注意，{readr} 会像处理 CSV 文件一样推断变量类型。虽然我们不会在这些示例中实现它，但同样地，read_fwf() 允许我们使用 col_types 规范，以及 na、skip 等参数。有关所有细节，请参阅 https://readr.tidyverse.org/reference/read_fwf.html 上的 read_fwf() 参考文档。

使用这三个作者姓名读取这个固定宽度文件是可行的，但它很容易出错。只要有一个人名字包含三个或更多组成部分（首字母、空格或连字符，如 Ursula K. Le Guin¹ 或 Ta-Nehisi Coates²），或者有一些缺失值，不一致的结构就会使 read_fwf() 解析器出错。

在下面的示例中，我们读取一个更长的作者姓名列表：

```r
authors2_path <- dpjr::dpjr_data("authors2_fwf.txt")

fwf_empty(authors2_path,
    col_names = c("first", "last", "state", "unique_id"))
```

```text
## $begin
## [1]  0 20 30
##
## $end
## [1] 19 22 NA
##
## $col_names
## [1] "first"     "last"      "state"     "unique_id"
```

如返回的“begin”和“end”值所示，fwf_empty() 函数只找到了三列。

¹ https://en.wikipedia.org/wiki/Ursula_K._Le_Guin
² https://en.wikipedia.org/wiki/Ta-Nehisi_Coates

当我们使用读取函数时，它找到三列：

```r
read_fwf(dpjr::dpjr_data("authors2_fwf.txt"))
```

```text
## # A tibble: 10 x 3
##    X1                  X2    X3
##    <chr>               <chr> <chr>
##  1 Toni Morrison       IL    DJ-1944-QF96
##  2 Kurt Vonnegut       IN    XN-5632-TP58
##  3 Walt Whitman        NY    LW-1752-TD08
##  4 Ursula K. Le Guin   CA    EZ-9789-EA77
##  5 Ta-Nehisi Coates    NY    YN-5151-NV82
##  6 W. E. B. Du Bois    MA    HN-6134-NF80
##  7 F. Scott Fitzgerald MN    YH-4405-TR02
##  8 N.K. Jemisin        IA    EF-7340-DW20
##  9 Flannery O'Connor   GA    HB-8269-XC88
## 10 Henry David Thoreau MA   RL-8200-SU83

Rows: 10 Columns: 3— Column specification

chr (3): X1, X2, X3
i Use `spec()` to retrieve the full column specification for this data.
i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

**图 5.3** *read_fwf 消息。*

现在添加 `col_names =` 参数会错误识别这些变量。

```r
read_fwf(authors2_path,
         fwf_empty(
           authors2_path,
           col_names = c("first", "last", "state", "unique_id")
         ))
```

```text
## # A tibble: 10 x 3
##    first                 last  state
##    <chr>                 <chr> <chr>
##  1 Toni Morrison         IL    DJ-1944-QF96
##  2 Kurt Vonnegut         IN    XN-5632-TP58
##  3 Walt Whitman          NY    LW-1752-TD08
##  4 Ursula K. Le Guin     CA    EZ-9789-EA77
##  5 Ta-Nehisi Coates      NY    YN-5151-NV82
##  6 W. E. B. Du Bois      MA    HN-6134-NF80
##  7 F. Scott Fitzgerald   MN    YH-4405-TR02
##  8 N.K. Jemisin          IA    EF-7340-DW20
##  9 Flannery O'Connor     GA    HB-8269-XC88
## 10 Henry David Thoreau   MA    RL-8200-SU83

Rows: 10 Columns: 3— Column specification

chr (3): first, last, state
i Use `spec()` to retrieve the full column specification for this data.
i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

**图 5.4** *read_fwf 消息。*

更可靠的方法是精确指定每一列的宽度。请注意，在下面的示例中，我们只指定“name”，而不将其拆分为 first 和 last。

| 变量 | 宽度 | 起始位置 | 结束位置 |
|----------|-------|----------------|--------------|
| name     | 20    | 1              | 20           |
| state    | 10    | 21             | 30           |
| uniqueID | 12    | 31             | 42           |

可以使用 fwf_widths 参数指定每列的宽度：

```r
read_fwf(authors2_path,
    fwf_widths(widths = c(20, 10, 12),
        col_names = c("name", "state", "unique_id")))
```

```text
## # A tibble: 10 x 3
##   name                state unique_id
##   <chr>               <chr> <chr>
## 1 Toni Morrison       IL    DJ-1944-QF96
## 2 Kurt Vonnegut       IN    XN-5632-TP58
## 3 Walt Whitman        NY    LW-1752-TD08
## 4 Ursula K. Le Guin   CA    EZ-9789-EA77
## 5 Ta-Nehisi Coates    NY    YN-5151-NV82
## 6 W. E. B. Du Bois    MA    HN-6134-NF80
## 7 F. Scott Fitzgerald MN    YH-4405-TR02
## 8 N.K. Jemisin        IA    EF-7340-DW20
## 9 Flannery O'Connor   GA    HB-8269-XC88
## 10 Henry David Thoreau MA   RL-8200-SU83

Rows: 10 Columns: 3— Column specification

chr (3): X1, X2, X3
i Use `spec()` to retrieve the full column specification for this data.
i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

**图 5.5** *read_fwf 消息。*

第三种选择是使用 fwf_positions() 提供两个位置列表，第一个包含起始位置，第二个包含结束位置。第一个变量 name 从位置 1 开始，到位置 20 结束；第二个变量 unique_id 从位置 31 开始，到位置 42 结束。注意，我们不会读取 state 变量，它占据了从 21 到 30 的十列。

```r
read_fwf(authors2_path,
    fwf_positions(start = c(1, 31), end = c(20, 42),
        col_names = c("name", "unique_id")))
```

```text
## # A tibble: 10 x 2
##   name               unique_id
##   <chr>              <chr>
## 1 Toni Morrison      DJ-1944-QF96
## 2 Kurt Vonnegut      XN-5632-TP58
## 3 Walt Whitman       LW-1752-TD08
## 4 Ursula K. Le Guin  EZ-9789-EA77
## 5 Ta-Nehisi Coates   YN-5151-NV82
## 6 W. E. B. Du Bois   HN-6134-NF80
## 7 F. Scott Fitzgerald YH-4405-TR02
## 8 N.K. Jemisin       EF-7340-DW20
## 9 Flannery O'Connor  HB-8269-XC88
## 10 Henry David Thoreau RL-8200-SU83

Rows: 10 Columns: 2— Column specification

chr (2): name, unique_id
i Use `spec()` to retrieve the full column specification for this data.
i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

**图 5.6** *read_fwf 消息。*

第四种选择是第三种选择的语法变体，使用相同的值但顺序不同。这一次，关于每个变量的所有相关信息都聚合在一起，变量名后跟起始位置和结束位置。

```r
read_fwf(authors2_path,
         fwf_cols(name = c(1, 20), unique_id = c(31, 42)))
```

```text
## # A tibble: 10 x 2
##    name                 unique_id
##    <chr>                <chr>
##  1 Toni Morrison        DJ-1944-QF96
##  2 Kurt Vonnegut        XN-5632-TP58
##  3 Walt Whitman         LW-1752-TD08
##  4 Ursula K. Le Guin    EZ-9789-EA77
##  5 Ta-Nehisi Coates     YN-5151-NV82
##  6 W. E. B. Du Bois     HN-6134-NF80
##  7 F. Scott Fitzgerald  YH-4405-TR02
##  8 N.K. Jemisin         EF-7340-DW20
##  9 Flannery O'Connor    HB-8269-XC88
## 10 Henry David Thoreau  RL-8200-SU83

Rows: 10 Columns: 2— Column specification

chr (2): name, unique_id
i Use `spec()` to retrieve the full column specification for this data.
i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

**图 5.7** *read_fwf 消息。*

最后，{readr} 提供了第五种读取固定宽度文件的方法，它类似于我们见过的第二种方法，将名称和宽度值聚合在一起。

```r
read_fwf(authors2_path,
         fwf_cols(name = 20, state = 10, unique_id = 12))
```

```text
## # A tibble: 10 x 3
##    name                 state unique_id
##    <chr>                <chr> <chr>
##  1 Toni Morrison        IL    DJ-1944-QF96
##  2 Kurt Vonnegut        IN    XN-5632-TP58
##  3 Walt Whitman         NY    LW-1752-TD08
##  4 Ursula K. Le Guin    CA    EZ-9789-EA77
##  5 Ta-Nehisi Coates     NY    YN-5151-NV82
##  6 W. E. B. Du Bois     MA    HN-6134-NF80
##  7 F. Scott Fitzgerald  MN    YH-4405-TR02
##  8 N.K. Jemisin         IA    EF-7340-DW20
##  9 Flannery O'Connor    GA    HB-8269-XC88
## 10 Henry David Thoreau  MA    RL-8200-SU83

Rows: 10 Columns: 3— Column specification

chr (3): name, state, unique_id
i Use `spec()` to retrieve the full column specification for this data.
i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

**图 5.8** *read_fwf 消息。*

## 5.3.1 一个固定宽度文件的极端示例

一个特别有趣的研究问题是教育水平与不同健康结果之间的关系。在这个示例中，我们将开始导入一个大文件的过程，该文件包含的数据将使我们能够探索是否存在相关性。

加拿大统计局提供了加拿大/美国联合健康调查（JCUSH）的公共使用微观数据文件（PUMF），该调查是于 2002 年底和 2003 年初进行的一项电话调查。调查共有 8,688 名受访者，其中 3,505 名加拿大人和 5,183 名美国人。可用的数据文件是匿名的，因此我们可以访问个人回答，这将有助于进一步分析。

该调查的网页，包括 PUMF 文件、数据字典和方法说明，位于：https://www150.statcan.gc.ca/n1/pub/82m0022x/2003001/4069119-eng.htm

PUMF 是一个名为“JCUSH.txt”的固定宽度文件。这个文件比上面的作者姓名示例大得多。共有 8,688 条记录，每条记录对应一名调查受访者。数据还包含 366 个变量，其中包括指定变量（如受访者唯一识别号和所在国家）、调查问题答复，以及在调查后数据处理过程中计算出的派生变量。
