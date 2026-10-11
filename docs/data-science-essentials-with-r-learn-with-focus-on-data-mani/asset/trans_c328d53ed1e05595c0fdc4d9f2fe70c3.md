

## 代码示例与输出

*   `mean_delicatessen = mean(Delicassen)`
*   `# print the summary`
*   `spending_summary`

### 输出结果

```
## mean_fresh mean_milk mean_grocery mean_frozen mean_detergents_paper mean_delicatessen
## 12000.3 5796. 7951.277 3071.932 2881.493 1524.87
```

在该代码片段中，使用 `dplyr` 包的 `summarise()` 计算整个数据集中不同产品类别的平均支出。值得注意的是，`summarise()` 结合 `group_by()` 使用时最为有用，后者将分析单位从整个数据集更改为由某一列定义的特定分组：

*   `# group by region and calculate the mean spending on Fresh, Milk, and Grocery product category`
*   `grouped_data1 <- wholesale_df %>%`
*   `group_by(Region) %>%`
*   `summarise(mean_fresh = mean(Fresh),`
*   `mean_milk = mean(Milk),`
*   `mean_grocery = mean(Grocery))`
*   `# view the result`
*   `View(grouped_data1)`

### 输出结果

```
## Region mean_fresh mean_milk mean_grocery
## Lisbon 11102.727 5486.416 7403.078
## Oporto 9888.681 5088.170 9219.596
## Other Region 12533.472 5977.085 7896.364
```

上述代码按地区对数据分组，然后计算每个地区三个产品类别的平均年支出。

接下来，计算两个客户渠道（Horeca 和 Retail）在几个产品类别上的总支出：

*   `# group by channel and calculate the total spending on product categories`
*   `grouped_data2 <- wholesale_df %>%`
*   `group_by(Channel) %>%`
*   `summarise(total_fresh = sum(Fresh),`
*   `total_milk = sum(Milk),`
*   `total_grocery = sum(Grocery))`
*   `# view the result`
*   `View(grouped_data2)`

### 输出结果

```
## Channel total_fresh total_milk total_grocery
## Horeca 4015717 1028614 1180717
## Retail 1264414 1521743 2317845
```

*   `# group by region and channel, and calculate the number of customers in each group`
*   `grouped_data3 <- wholesale_df %>%`
*   `group_by(Region, Channel) %>%`
*   `summarise(count = n())`
*   `# view the result`
*   `View(grouped_data3)`

### 输出结果

```
## Region Channel count
## Lisbon Horeca 59
## Lisbon Retail 18
## Oporto Horeca 28
## Oporto Retail 19
## Other Region Horeca 211
## Other Region Retail 105
```

上述代码使用 `group_by` 函数按 `Region` 和 `Channel` 列对数据集分组。然后使用 `summarize` 函数和 `n()` 函数计算每组的客户数量，`n()` 统计每组中的观测值数量。生成的 DataFrame 每行对应地区和渠道的唯一组合，并显示该组中的客户数量。

## 分组数据上的筛选

分组数据通常在与 `summarise()` 函数结合使用时变得非常有价值，可进行简洁的计算和汇总。但值得注意的是，`mutate()` 和 `filter()` 也提供了可在分组数据上执行的便捷操作，如下所示：

*   `region_high_grocery_spending <- wholesale_df %>%`
*   `group_by(Region) %>%`
*   `filter(Grocery > mean(Grocery))`

此处，通过按 `Region` 变量对数据分组，并根据杂货产品的高支出（大于各地区内的平均支出）进行筛选，可找出在其所在地区杂货支出高于平均水平的客户子集。筛选后的数据将识别出消费者在杂货产品上的地区性行为差异和偏好。

## 分组数据上新增列

*   `# Grouping by Region and calculating the total spending per region`
*   `region_total_spending <- wholesale_df %>%`
*   `group_by(Region) %>%`
*   `mutate(total_spending = sum(Fresh, Milk, Grocery, Frozen, Detergents_Paper, Delicassen))`

通过按 `Region` 变量对数据分组并使用 `mutate()` 函数，代码向数据集新增了一个名为 `total_spending` 的变量。该新变量表示各地区不同产品类别支出的总和。各地区的总支出可帮助企业就资源分配、地区支出差异和市场细分识别做出明智决策。

# 合并数据

让我们看看在 R 中合并数据的方法：

## 绑定数据：`rbind()` 和 `cbind()`

`rbind()` 代表行绑定，允许通过将行堆叠在一起，将两个或多个 DataFrame 合并为单个 DataFrame。为确保生成的 DataFrame 中的列正确对齐且结构一致，必须满足以下条件：

*   待合并的 DataFrame 必须具有相同的列名。
*   待合并的 DataFrame 必须具有相同数量的列。
*   待合并的 DataFrame 中列的顺序应相同。

*   `# create a DataFrame`
*   `player_df1 <- data.frame(`
*   `Player_Name = c("Virat Kohli", "Rohit Sharma", "Suresh Raina"),`
*   `Score = c(102, 53, 45)`
*   `)`
*   `# create another DataFrame`
*   `player_df2 <- data.frame(`
*   `Player_Name = c("Ravindra Jadeja", "Hardik Pandya"),`
*   `Score = c(82, 64)`
*   `)`

这里有两个 DataFrame：`player_df1` 和 `player_df2`，包含印度板球运动员在不同比赛中的得分信息。现在假设我们想将这两个 DataFrame 合并为一个显示所有球员所有得分的 DataFrame。可以使用 `rbind()` 函数实现，请看以下代码片段：

*   `# combine the two DataFrames using rbind()`
*   `player_df_combined <- rbind(player_df1, player_df2)`
*   `# view the combined DataFrame`
*   `player_df_combined`

### 输出结果

```
## Player_Name Score
## Virat Kohli 102
## Rohit Sharma 53
## Suresh Raina 45
## Ravindra Jadeja 82
## Hardik Pandya 64
```

`cbind()` 代表列绑定，允许通过将一个 DataFrame 的列附加到另一个 DataFrame 旁边来合并多个 DataFrame。为确保生成的 DataFrame 结构一致，待合并的 DataFrame 必须具有相同数量的行。

*   `# Create a DataFrame with characteristics of the match`
*   `match_df <- data.frame(`
*   `Venue = c("Mumbai", "Delhi", "Kolkata"),`
*   `Date = c("2023-05-15", "2023-05-16", "2023-05-17")`
*   `)`
*   `# Combine player_df1 and match_df using cbind`
*   `combined_df <- cbind(player_df1, match_df)`
*   `# print combined_df`
*   `combined_df`

### 输出结果

```
## Player_Name Score Venue Date
## Virat Kohli 102 Mumbai 2022-05-15
## Rohit Sharma 53 Delhi 2022-05-16
## Suresh Raina 45 Kolkata 2022-05-17
```

## 连接：内连接、外连接、左连接和右连接

在数据库领域，有一种称为连接的强大操作，允许基于公共列或变量合并两个表。同样，在 R 中，可以使用 `merge()` 函数基于共享列合并两个 DataFrame。

可以将其想象为拼合两块完美契合的拼图碎片。`merge()` 帮助你基于共同特征（如名称或 ID 号码）匹配碎片。DataFrame 合并后，你可以利用合并的信息进行各种分析和可视化。下表定义了 `merge()` 函数的基本参数。

| Argument | Description |
| --- | --- |
| `x` | 要合并的第一个 DataFrame。 |
| `y` | 要合并的第二个 DataFrame。 |
| `by` | 要合并的列。 |
| `all` | 逻辑值，指示是否包含两个 DataFrame 中的所有观测值（行）（外连接）。 |
| `all.x` | 逻辑值，指示是否包含第一个 DataFrame 中的所有观测值，即使第二个 DataFrame 中没有匹配行（左连接）。 |

