# YLL Calculation

# Table 3.2 YLLs due to Stroke in the Global region-5 years age groups

```
```r
YLL_global_stroke %>%%
# # head()
# # A tibble: 6 x 5
# # sex age dx le YLL
# # <chr> <ord> dbl dbl dbl
# # 1 male <1 3640. 70.8 125916.
# # 2 female <1 2404. 75.9 182396.
# # 3 both <1 6044. 73.3 443136.
# # 4 male 01-04 2049. 72.0 147563.
# # 5 female 01-04 1505. 76.9 115680.
# # 6 both 01-04 3553. 74.4 264248.
```
```

```
YLL_global_stroke <- deaths_stroke %>%%
full_join(ex2019) %>%%
group_by(age, sex) %>%%
mutate(YLL = dx * le) %>%%
ngroup()```
```

# Global Region: Years of Life Lost (YLLs) due to stroke
Year 2019 - Millions

![](bbox=[0.137, 0.445, 0.882, 0.732])

# Figure 3.2 YLLs due to Stroke in the Global region

Based on these results, we can conclude that the conditions of YLLs due to stroke are essential measures of this condition on the quality of life of individuals in the Global region. The YLLs due to stroke are particularly high in older age groups, where the number of deaths is higher, and the life expectancy is lower. This indicates that stroke has a significant impact on the overall burden of disease in the Global region, particularly among older populations.