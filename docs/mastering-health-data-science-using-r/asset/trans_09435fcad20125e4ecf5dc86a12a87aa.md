

#> [1] "ibuprofen" "metformin"
#>
#> $past_weights
#> [1] 136 142 159
ex_list$medications
#> [1] "ibuprofen" "metformin"

要编辑列表，我们可以使用索引访问列表中的不同对象，然后为它们赋予新值。此外，我们还可以使用 `$` 访问器向列表中添加对象。

```
ex_list$supplements <- c("vitamin D", "biotin")
ex_list$supplements[2] <- "collagen"
ex_list
#> $name
#> [1] "John"
#>
#> $medications
#> [1] "ibuprofen" "metformin"
#>
#> $past_weights
#> [1] 136 142 159
#>
#> $supplements
#> [1] "vitamin D" "collagen"
```

## 2.7 练习

- 1. 在 R 中重新创建图 2.6 中的数据框，其中 temperature 和 co2 分别表示 2008 年 1 月以华氏度表示的平均温度和以 mg/m3 表示的平均 CO2 浓度，并将其命名为 city_air_quality。

- 2. 创建一个名为 precipitation 的字符向量，条目为 Yes 或 No，表示这些城市 2008 年 1 月的降水量是否高于平均水平（你可以自行编造这些信息）。然后，将该向量作为新列追加到 city_air_quality 数据框中。

| city | country | temperature | co2 |
|---|---|---|---|
| Beijing | China | 30 | 417.0 |
| Shanghai | China | 40 | 405.0 |
| Paris | France | 37 | 401.2 |
| Rome | Italy | 54 | 398.7 |
| London | United Kingdom | 43 | 412.3 |
| San Francisco | United States | 52 | 419.0 |
| Toronto | Canada | 25 | 399.4 |

图 2.6：城市空气质量数据。

- 3. 将分类列 precipitation 转换为因子。然后，使用 rbind() 函数向 city_air_quality 数据框添加一行，使其与图 2.7 匹配。

| city | country | temperature | co2 | precipitation |
|---|---|---|---|---|
| Reykjavik | Iceland | 29 | 402.1 | No |

图 2.7：更新后的城市空气质量数据。

- 4. 在数据框中，使用单个方括号访问旧金山和巴黎的 precipitation 和 CO₂ 浓度条目。然后，创建一个列表 city_list，其中包含两个列表，一个用于旧金山，一个用于巴黎；每个内部列表包含该城市的城市名称、precipitation 和 CO₂ 浓度信息。

## 3 在 R 中处理数据文件

在本章中，我们将使用 R 处理数据。首先，我们需要将数据加载到 R 中；这需要我们确定所拥有的数据文件类型（例如 .csv、.xlsx、.dta、.txt），并找到合适的函数来加载数据。这样会创建一个包含文件信息的数据框对象。在演示了如何加载此类数据之后，本章将进一步介绍如何查找数据列的信息，包括查找缺失值、汇总列以及对数据进行子集选择。此外，我们还将了解如何通过一些简单的变换创建新列。

在本章以及后续所有章节中，我们都会在章节开头加载所需的库；例如，在本章中，我们只需要一个包 **HDSinRdata**，其中包含本书使用的示例数据集。

```
library(HDSinRdata)
```

### 3.1 导入和导出数据

本章使用的数据包含曾到访匹兹堡大学七家疼痛管理诊所之一的患者信息，其中包括患者在基线时和 3 个月随访时使用协作健康结果信息登记系统（CHOIR）进行的患者自报疼痛评估（Alter 等，2021）。你可以使用帮助运算符 `?pain` 进一步了解这些数据的来源，并阅读其列描述。由于这些数据位于我们的 R 包中，我们可以使用 `data()` 函数将这些数据加载到当前环境中。请注意，该数据共有 21,659 行和 92 列。

```
data(pain)
dim(pain)
#> [1] 21659  92
```

通常，你将要使用的数据并不在 R 包中，而是位于个人电脑上的一个或多个数据文件中。要将这些数据加载到 R 中，你需要使用与文件类型相对应的函数。例如，你可以使用基础 R 中的 read.csv() 函数或 readr 包中的 read_csv() 函数加载 .csv 文件，这两种函数均已在第 1 章中介绍过。作为示例，我们用这两个函数加载 fake_names.csv 数据集。查看打印输出，我们可以发现这两个函数在存储数据的数据结构和数据类型上略有差异。read.csv() 函数将数据加载为数据框；而 read_csv() 函数将数据加载为 spec_tbl_df，这是一种称为 tibble 的特殊数据框类型，tidyverse 系列包会使用这种数据框。我们将在第 5 章更详细地介绍这种数据结构。目前，请注意，你可以使用任一函数读取 .csv 文件。

```
read.csv("data/fake_names.csv")
#>
#>   Name Age       DOB       City State
#> 1  Ken Irwin 37 6/28/85   Providence RI
#> 2  Delores Whittington 56 4/28/67 Smithfield RI
#> 3  Daniel Hughes 41 5/22/82 Providence RI
#> 4  Carlos Fain 83 2/2/40 Warren RI
#> 5  James Alford 67 2/23/56 East Providence RI
#> 6  Ruth Alvarez 34 9/22/88 Providence RI
```

```
readr::read_csv("data/fake_names.csv", show_col_types=FALSE)
#> # A tibble: 6 x 5
#>   Name    Age DOB       City         State
#>   <chr> <dbl> <chr>     <chr>        <chr>
#> 1 Ken Irwin 37 6/28/85   Providence RI
#> 2 Delores Whittington 56 4/28/67 Smithfield RI
#> 3 Daniel Hughes 41 5/22/82 Providence RI
#> 4 Carlos Fain 83 2/2/40 Warren RI
#> 5 James Alford 67 2/23/56 East Providence RI
#> 6 Ruth Alvarez 34 9/22/88 Providence RI
```

除了将数据加载到 R 中，你可能还想将 R 中的数据保存到数据文件中，以便日后访问或与他人共享。要将 R 中的数据框写入 .csv 文件，可以使用 write.csv() 函数。该函数有三个关键参数：第一个参数是要写入文件的 R 数据框；第二个参数是用于写入数据的文件名或完整文件路径；第三个参数是是否要将行名作为额外的一列包含在内。在本例中，我们不包含行名。如果不指定文件路径，R 会将文件保存到当前工作目录。

```
df <- data.frame(x = c(1, 0, 1), y = c("A", "B", "C"))
write.csv(df, "data/test.csv", row.names=FALSE)
```

如果你的数据不是 .csv 文件，则可能需要使用另一个包来读取该文件。最常见的两个包是 readxl 包（Wickham 和 Bryan，2023）和 haven 包（Wickham、Miller 和 Smith，2023）。readxl 包可以轻松读取 Excel 文件，haven 包可以导入 SAS、SPSS 和 Stata 文件。对于每个函数，你都需要指定数据文件的路径。

- 制表符分隔文件：可以使用基础 R 中的 read.delim() 函数读取制表符分隔的 .txt 文件。
- Excel 文件：可以使用 readxl::read_excel() 读取 .xls 或 .xlsx 文件，该函数允许你指定文件中的工作表和/或单元格范围（例如 read_excel('test.xlsx', sheet="Sheet1")）。
- SAS：haven::read_sas() 读取 .sas7bdat 或 .sas7bcat 文件，haven::read_xpt() 读取 SAS 传输文件。
- Stata：haven::read_dta() 读取 .dta 文件。
- SPSS：haven::read_spss() 读取 .spss 文件。

### 3.2 汇总和创建数据列

现在我们来看看已加载到名为 pain 的数据框中的数据。我们使用 head() 函数打印前六行。但请注意，列数太多，并非所有列都会显示出来！对于显示出来的列，我们可以在列名下方看到每列的数据类型。例如，我们可以看到 PATIENT_NUM 列是类型为 dbl 的数值列。由于患者识别号在本质上属于名义型变量，我们可以考虑以后是否应将此列转换为因子或字符表示形式。我们可以使用 names() 函数打印所有列名。请注意，X101 至 X238 列对应身体疼痛地图上的编号（有关该地图的图像，请参阅数据文档）。如果患者表示相应身体部位有疼痛，则这些列中的每一列取值为 1，否则为 0。

