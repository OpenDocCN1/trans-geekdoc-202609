
```r
pain_df$HAS_FOLLOW_UP <-
  !is.na(pain_df$PAIN_INTENSITY_AVERAGE_FOLLOW_UP)
ggplot(pain_df) +
  geom_density(aes(x = PROMIS_PHYSICAL_FUNCTION,
                   group = HAS_FOLLOW_UP,
                   color = HAS_FOLLOW_UP)) +
  scale_x_continuous(breaks = c(0:10)) +
  scale_color_discrete(name = "Follow-Up", labels = c("No", "Yes")) +
  labs(x = "PROMIS Physical Function T-Score",
       y = "Estimated Density") +
  theme_minimal()
```

![](img/58a554e865d49ca347d9a3f76f8f0812_148_0.png)

让我们尝试另一个示例。假设我们想要找到有后续随访和无后续随访的患者的初始整体疼痛分布。在这种情况下，我们想要绘制每个组中每种疼痛评分的比例，而不是比较计数。我们首先需要找到这些比例，我们通过对数据分组并进行汇总来实现。

```r
pain_df_grp <- pain_df %>%
  group_by(HAS_FOLLOW_UP, PAIN_INTENSITY_AVERAGE) %>%
  summarize(tot = n()) %>%
  mutate(prop = tot/sum(tot)) %>%
  ungroup()
head(pain_df_grp)
#> # A tibble: 6 x 4
#>   HAS_FOLLOW_UP PAIN_INTENSITY_AVERAGE   tot   prop
#>   <lgl>         <int>                  <dbl> <dbl>
#> 1 FALSE         0                          8 0.00222
#> 2 FALSE         1                         16 0.00444
#> 3 FALSE         2                         62 0.0172
#> 4 FALSE         3                        132 0.0366
#> 5 FALSE         4                        273 0.0757
#> 6 FALSE         5                        508 0.141
```

我们现在可以使用`geom_col()`函数来创建这些比例的条形图。默认情况下，当存在分组时，此函数会将条形堆叠在一起。尝试在`geom_col()`函数中添加`position="dodge"`，使条形并排而不是彼此堆叠。

```r
ggplot(pain_df_grp)+
  geom_col(aes(x = PAIN_INTENSITY_AVERAGE, y = prop,
               fill = HAS_FOLLOW_UP)) +
  scale_x_continuous(breaks = c(0:10)) +
  scale_fill_discrete(name = "Seen at Follow Up",
                      labels = c("No", "Yes")) +
  labs(x = "Reported Pain Intensity", y = "Proportion") +
  theme_minimal()
```

![](img/58a554e865d49ca347d9a3f76f8f0812_149_0.png)

### 8.3.1 练习题

重新创建图 8.3。

![](img/58a554e865d49ca347d9a3f76f8f0812_150_0.png)

图 8.3：BMI 分布。

```r
# Insert your solution here:
```

另一种按组可视化数据的方法是在你的 ggplot 对象中添加分面。分面根据一个或多个离散变量值将图划分为子图。我们可以使用`facet_grid()`并分别使用`cols`和`rows`参数指定列和行变量，将这些图排列为网格，其中行和/或列对应于我们分组的变量。或者我们可以使用`facet_wrap()`并指定`facets`参数，将图包装成矩形格式。在下面的代码中，我们取之前的某个图，并添加一个分面网格，其中网格的列由种族组决定。如果我们设置`rows = vars(PAT_RACE_CAT)`，那么这将垂直堆叠图。请注意，我们必须在内置的`vars()`函数中指定变量。

```r
ggplot(pain_df)+
  geom_histogram(aes(x = PAIN_INTENSITY_AVERAGE, fill = "Baseline")) +
  geom_histogram(aes(x = PAIN_INTENSITY_AVERAGE_FOLLOW_UP,
                     fill = "Follow-Up")) +
  scale_x_continuous(breaks = c(0:10)) +
  scale_fill_manual(values = c("violetred", "pink"),
                    name = "Measurement") +
  labs(x= "Reported Pain Intensity", y = "Count") +
  facet_grid(rows = vars(PAT_RACE_CAT))+
  theme_minimal()
#> Warning: Removed 3604 rows containing non-finite values outside the scale range (`stat_bin()`).
```

![](img/58a554e865d49ca347d9a3f76f8f0812_151_0.png)

## 8.4 额外选项

对于我们的最终图，我们将演示本章尚未涵盖的一些附加功能。为了创建此图，我们首先找到选择每个身体区域的参与者人数以及这些患者的平均疼痛强度。我们还将每个身体部位区域划分为更大的组。

```r
pain_body_map <- data.frame(part = names(pain_df)[2:75])
pain_body_map$num_patients <- colSums(pain_df[, 2:75])
pain_body_map$perc_patients <- pain_body_map$num_patients /
                              nrow(pain_df)

pain_body_map$avg_pain <- colSums(pain_df[, 2:75] *
                                  pain_df$PAIN_INTENSITY_AVERAGE) /
                          pain_body_map$num_patients

pain_body_map <- pain_body_map %>%
    mutate(region = case_when(
    part %in% c("X208", "X209", "X218", "X219", "X212",
                "X213", "X222") ~ "Back",
    part %in% c("X105", "X106", "X205", "X206") ~ "Neck",
    part %in% c("X107", "X110", "X207", "X210") ~ "Shoulders",
    part %in% c("X108", "X109", "X112", "X113") ~ "Chest/Abs",
    part %in% c("X126", "X127", "X228", "X229",
                "X131", "X132", "X233", "X234") ~ "Legs",
    part %in% c("X111", "X114", "X211", "X214", "X115", "X116",
                "X117", "X118", "X217", "X220") ~ "Arms",
    part %in% c("X119", "X124", "X221", "X226", "X125", "X128",
                "X227", "X230") ~ "Wrists/Hands",
    part %in% c("X215", "X216") ~ "Elbows",
    part %in% c("X135", "X136", "X237", "X238", "X133", "X134",
                "X235", "X236") ~ "Feet/Ankles",
    part %in% c("X129", "X130", "X231", "X232") ~ "Knees",
    part %in% c("X101", "X102", "X103", "X104", "X201", "X203",
                "X202", "X204") ~ "Head",
    part %in% c("X120", "X121", "X122", "X123", "X222", "X223",
                "X224", "X225") ~ "Hips"))

head(pain_body_map)
#>  part num_patients perc_patients avg_pain region
#> 1 X101          323        0.0646      6.69    Head
#> 2 X102          322        0.0644      6.82    Head
#> 3 X103          165        0.0330      6.86    Head
#> 4 X104          165        0.0330      6.95    Head
#> 5 X105          493        0.0986      6.90    Neck
#> 6 X106          507        0.1014      6.92    Neck
```

在我们选择的主题中，我们可以更新任何主题选项（参见`?theme`）。在下面的代码中，我们使用`theme()`函数将图例位置更新到底部，并将网格线更新为浅粉色。此外，我们使用`geom_hline()`函数添加一条水平线（`geom_vline()`和`geom_abline()`可以分别添加垂直或对角线），并使用`annotate()`函数添加文本注释。生成的图显示了每个身体部位的平均疼痛值以及将其归类为疼痛的患者比例。

```r
ggplot(pain_body_map) +
geom_label(aes(x = perc_patients, y = avg_pain, label = part,
color = region)) +
geom_hline(yintercept = mean(pain_body_map$avg_pain)) +
annotate(geom = "text", label = "Average Pain Value",
x = 0.35, y = 7.0) +
labs(x = "Proportion Patients Selected Region",
y = "Average Pain of Patients") +
theme_minimal() +
theme(legend.position="bottom",
panel.grid.major = element_line(color = "lightpink"))
```

![](img/58a554e865d49ca347d9a3f76f8f0812_153_0.png)

到目前为止，我们还没有将任何图形保存为对象。在下一个示例中，我创建两个图并将它们保存为名为 p1 和 p2 的对象。如果我们想保存这些图，可以使用`ggsave()`函数，该函数会将最后生成的图保存到提供的文件名下。此外，我可以使用 patchwork 包将多个图组合在一起。图之间的`+`将它们合并为一个图形，然后`plot_layout()`函数允许我们指定用于排列图形的网格。我们使用`guide_area()`函数添加了一个额外元素来创建图例的占位符，然后在`plot_layout()`函数中使用`guide = "collect"`参数来指定所有图例应放在一起。

```r
p1 <- ggplot(pain_body_map) +
  geom_label(aes(x = perc_patients, y = avg_pain, label = part,
                 color = region)) +
  geom_hline(yintercept = mean(pain_body_map$avg_pain)) +
  annotate(geom = "text", label = "Average Pain Value",
           x = 0.35, y = 7.0) +
  labs(x = "Proportion of Patients Selecting Region",
       y = "Average Pain of Patients") +
  scale_color_discrete(name="Body Part")+
  theme_minimal()+
  theme(legend.position = "bottom",
        panel.grid.major = element_line(color = "lightpink"))

p2 <- ggplot(pain_body_map) +
  geom_histogram(aes(x = perc_patients), color = "violetred",
                 fill = "lightpink") +
  labs(x = "Proportion of Patients Selecting Region", y = "Count") +
  theme_minimal()+
  theme(panel.grid.major = element_line(color = "lightpink"))
```

```r
p1 + p2 + guide_area() + plot_layout(ncol=1, guides = "collect",
                                   axes = "collect")
```

