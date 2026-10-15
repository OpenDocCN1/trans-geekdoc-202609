
Another option is the `ons_browse_qmi()` function, which opens the relevant ONS page in your web browser software.

```
ons_browse_qmi(id = "retail-sales-index")
```

Finally, we will use the relevant id value in an `ons_get()` function to retrieve the data.

```
df_retail_sales <- ons_get(id = "retail-sales-index")
```

There are 42,400 rows in this data (as of 2023-06-14), with multiple variables for each month. Your analysis will require further filtering and selecting, but with the {onsr} package providing the access to the data, you are well on your way.

## 9.2.2 加拿大统计局

加拿大统计局，加拿大政府的一个部门，提供了一个名为“CANSIM”的社会经济时间序列数据库。发布到数据库中的数据是加拿大统计局定期收集的大部分汇总数据，例如劳动力调查（我们从中获得失业率更新）、消费者价格指数调查（关于通货膨胀）以及从怀孕和出生到预期寿命和死亡的健康相关信息。

包 {cansim}（von Bergmann 和 Shkolnik，2021）使用加拿大统计局创建的 API，以便直接下载数百个数据表和数千个单独的时间序列。

```
library(cansim) # access Statistics Canada's CANSIM data repository
```

One of the many tables related to international travel that is published in CANSIM is “Table: 24-10-0050-01 Non-resident visitors entering Canada, by country of residence”¹.

在 CANSIM 中发布的许多与国际旅行相关的表格之一是“表：24-10-0050-01 按居住国划分进入加拿大的非居民访客”¹。

Here’s a screenshot of the table, showing the number of people arriving by their continent of residence.

以下是该表的屏幕截图，显示按居住大陆到达的人数。

¹The webpage for the table, showing the most recently available data, is here: https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=2410005001

Geography: Canada (map)

地理：加拿大（地图）

| 居住国² | 2023年3月 | 2023年4月 | 2023年5月 | 2023年6月 | 2023年7月 |
|---|---:|---:|---:|---:|---:|
| **访客** |  |  |  |  |  |
| 进入加拿大的非居民访客 | 1,382,309 | 1,674,026 | 2,377,181 | 3,332,607 | 4,000,340 |
| 进入加拿大的美利坚合众国居民 | 1,094,111 | 1,300,810 | 1,831,912 | 2,632,723 | 3,132,681 |
| 进入加拿大的除美利坚合众国以外国家的居民 | 288,198 | 373,216 | 545,269 | 699,884 | 867,659 |
| 美洲，除美利坚合众国以外国家 | 74,654 | 92,600 | 90,704 | 116,030 | 141,622 |
| 北美，除美利坚合众国以外国家 | 42,446 | 56,789 | 49,022 | 56,651 | 69,313 |
| 中美洲 | 3,226 | 5,116 | 4,851 | 6,787 | 6,769 |
| 加勒比地区 | 11,203 | 15,742 | 14,952 | 20,830 | 28,585 |
| 南美洲 | 17,779 | 14,953 | 21,879 | 31,762 | 36,955 |
| 美洲，未另行说明³ | 0 | 0 | 0 | 0 | 0 |

**图 9.1** *CANSIM 表 24-10-0050-01.*

This table might be useful if you were developing a marketing campaign and you wanted to understand where tourists are coming from—the biggest markets and the fastest growing. But as shown, it is at too high a level; this is Canada by continent. For our purposes, we need to see specific country, those entering Canada via British Columbia, and a longer time series.

如果您正在开发营销活动并想了解游客来自哪里——最大的市场和增长最快的市场，该表可能很有用。但如图所示，它处于过高的层级；这是按大陆划分的加拿大。对于我们的目的，我们需要查看具体国家、经不列颠哥伦比亚省进入加拿大的人以及更长的时间序列。

We could use the filters and fiddle around making sure we got the right selections and then download the data, but if we have to do that next month it is going to be inefficient. We could also first click on the “download options” button and select “download entire table...” but again, this is not the most efficient way to do this, since there are a few manual steps we have to take and then open the file into R and filter to select the series we want.

我们可以使用过滤器并反复调整以确保获得正确的选择然后下载数据，但如果下个月必须这样做效率会很低。我们也可以先点击“下载选项”按钮并选择“下载整个表...”，但同样，这不是最高效的方式，因为我们必须执行几个手动步骤，然后将文件打开到 R 中并过滤以选择我们想要的系列。

This is where the {cansim} package comes in.

这就是 {cansim} 包发挥作用的地方。

### 第 1 步：下载数据。

- The `get_cansim()` function takes the table number as the parameter, and connects to CANSIM and downloads the data into an R dataframe.

```
travellers <- get_cansim("24-10-0050-01")
```

We will come back to filtering and variable selection along with working with date fields later, but here’s the code in R using the functions of the {dplyr} package to filter for the British Columbia cases during the month of June 2019:

我们稍后会回到过滤和变量选择以及处理日期字段，但以下是使用 {dplyr} 包的函数在 R 中过滤 2019 年 6 月不列颠哥伦比亚省案例的代码：

```
travellers_bc <- 
travellers |> 
  filter(GEO == "British Columbia",
         REF_DATE == "2019-06")

glimpse(travellers_bc, width = 65)
```

There are 287 rows, one for each of the categories in the Country of residence variable. It’s important to note that these are not just countries, but the variable also includes subtotals. What if we just want a monthly report on a single continent? One option would be for us to filter the “COUNTRY” variable; here we filter for visitors from Europe.

共有 287 行，每行对应居住国变量中的一个类别。需要注意的是，这些不仅仅是国家，变量还包括小计。如果我们只想要某个大洲的月度报告怎么办？一个选项是我们过滤“COUNTRY”变量；在这里我们过滤来自欧洲的访客。

```
travellers_bc |> 
  filter(`Country of residence` == "Europe")
```

One of the features of CANSIM and other similar tables is that the individual series are given a single identifier. In the case of CANSIM, these are called the “vector numbers”. Scroll to the right on this table, and you’ll see a variable called VECTOR. The vector identifier (sometimes called “the vector number” even though it’s a character string!) for European travellers entering Canada via British Columbia is v1277198032.

CANSIM 和其他类似表格的一个特点是各个系列都有一个唯一标识符。在 CANSIM 的情况下，这些被称为“向量编号”。将此表向右滚动，您会看到一个名为 VECTOR 的变量。经不列颠哥伦比亚省进入加拿大的欧洲旅行者的向量标识符（有时即使它是一个字符字符串也称为“向量编号”！）是 v1277198032。

The {cansim} package also gives us a function to select a single vector number, so we can be more efficient still. We can speed up the download time and skip the filtering steps to get to the one we want. (Note that this function requires us to enter a start date, and converts the reference date variable to the YYYY-MM-DD format.)

{cansim} 包还为我们提供了一个函数来选择单个向量编号，这样我们可以更高效。我们可以加快下载时间并跳过过滤步骤以获取我们想要的。（请注意，此函数要求我们输入开始日期，并将参考日期变量转换为 YYYY-MM-DD 格式。）

```
get_cansim_vector("v1277198032", start_time = "2015-01-01")
```

This table has the shortcoming of not including the “GEO” or “Country of residence” variables, so we need to ensure that we have adequately documented what has been accessed.

此表的缺点是不包括“GEO”或“居住国”变量，因此我们需要确保已充分记录所访问的内容。

The {cansim} package includes other very useful functions if you find yourself exploring Statistics Canada data sets.

如果您发现自己正在探索加拿大统计局数据集，{cansim} 包包含其他非常有用的函数。

The function get_cansim_table_overview() provides an abstract about the data table.

函数 get_cansim_table_overview() 提供有关数据表的摘要。

```
get_cansim_table_overview("24-10-0050-01")
```

## 9.3 用于直接访问数据的其他 R 包

The following is an incomplete list (in alphabetical order by name) of other packages that have been developed to provide direct access to a specific web resource.

以下是按名称字母顺序排列的不完整列表，其中包含为提供对特定网络资源的直接访问而开发的其他包。

- {bcdata} (Teucher et al., 2023) has tools to search, query, and download tabular and ‘geospatial’ data from the British Columbia Data Catalogue.
- {fredr} (Boysel and Vaughan, 2023) connects to the “Federal Reserve Economic Data”, or FRED, hosted by the Federal Reserve Bank of St. Louis. This data repository has (according to Wikipedia) over 800,000 economic time series from various sources.
- {opendatatoronto} (Gelfand and City of Toronto, 2022) provides a direct connection to the City of Toronto Open Data Portal.
- The {readabs} (Cowgill et al., 2023) package downloads and tidies data from the Australian Bureau of Statistics.
- {RBNZ} (Watson, 2020) downloads data from the Reserve Bank of New Zealand Website.
- {tidycensus} (Walker et al., 2023) has tools that connect to the United States Census Bureau and returns tidyverse-ready dataframes with the option of adding geographic details to allow for mapping. (See also (Walker, 2023).)

## 10 连接到关系数据库

In this chapter:

- Importing data directly from relational databases (SQL)
- Using relational data as part of the data preparation workflow

本章内容：

- 直接从关系数据库（SQL）导入数据
- 将关系数据作为数据准备工作流程的一部分使用

### 10.1 关系数据

Relational databases are commonly used for data storage. Unlike a “flat file” which contains all of the variables, the data is stored in multiple tables, which are linked via common variables (known as the “keys”). This facilitates efficient storage, as information does not need to be duplicated in multiple rows. We have seen an example of a relational table earlier, where we built a concordance table for the administrative geography of England and Wales in Chapter 6.

关系数据库通常用于数据存储。与包含所有变量的“平面文件”不同，数据存储在多个表中，这些表通过公共变量（称为“键”）链接。这有助于高效存储，因为信息不需要在多行中重复。我们之前见过一个关系表的例子，其中我们在第 6 章中为英格兰和威尔士的行政地理构建了对照表。

In that example, all of the data was loaded into our computer’s memory. In other instances, the size of the database, across multiple tables, will be such that it exceeds the capacity of your computer. In those cases, a server-based database will be established, and as the data analyst, we will need to retrieve only the variables and records that we need for our work. A database query can also include the calculation of summary statistics, which shifts the computational load to the server.

在那个例子中，所有数据都加载到我们计算机的内存中。在其他情况下，数据库的大小跨多个表，将超过计算机的容量。在这些情况下，将建立基于服务器的数据库，作为数据分析师，我们只需要检索我们工作所需变量和记录。数据库查询还可以包括汇总统计的计算，这将计算负载转移到服务器。

While SQL is the most commonly used query language, there are R packages that allow us to

虽然 SQL 是最常用的查询语言，但有 R 包允许我们

- Connect to a database,
- Write the code for our queries in R,
- Run the query, and
- Do our work in an R environment.

- 连接到数据库，
- 在 R 中编写查询代码，
- 运行查询，并
- 在 R 环境中进行工作。
