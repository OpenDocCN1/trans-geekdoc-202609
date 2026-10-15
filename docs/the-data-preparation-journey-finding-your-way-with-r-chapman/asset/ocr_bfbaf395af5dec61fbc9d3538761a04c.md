```
## 6 Mainland/Southwest  Justice In~  13592.  13864.  14141.
## # i abbreviated name: 1: `Economic Development Region`
## # i 7 more variables: `AY 2015/16` <dbl>, `AY 2016/17` <dbl>,
## #   `AY 2017/18` <dbl>, `AY 2018/19` <dbl>, `AY 2019/20` <dbl>,
## #   `AY 2020/21` <dbl>, `AY 2021/22` <dbl>
```

The next step is to use the {tidyr} function drop_na() to omit any row that contains an NA value. In this case, we want to drop what were the header rows that contained just the region name in the first column and no values in the other columns.

These two solutions yield the same result:

```
drop_na(tuition_data_filled)
```

```
tuition_data_filled |>
  drop_na()
```

```
## # A tibble: 25 x 12
##   `Economic Development Region` Institution   `AY 2012/13` `AY 2013/14`
##   <chr>                        <chr>                 <dbl>        <dbl>
## 1 Mainland/Southwest           British Columbi~      17611.       17963.
## 2 Mainland/Southwest           Capilano Univer~      15000        15750
## 3 Mainland/Southwest           Douglas College       14400        15000
## 4 Mainland/Southwest           Emily Carr Univ~      15000.       15600
## 5 Mainland/Southwest           Justice Institu~      13592.       13864.
## 6 Mainland/Southwest           Kwantlen Polyte~      15000        15750
## 7 Mainland/Southwest           Langara College       16500        16950
## 8 Mainland/Southwest           Simon Fraser Un~      16236        17862
## 9 Mainland/Southwest           University of B~      22622.       23300.
## 10 Mainland/Southwest           University of t~      12720        13350
## # i 15 more rows
## # i 8 more variables: `AY 2014/15` <dbl>, `AY 2015/16` <dbl>,
## #   `AY 2016/17` <dbl>, `AY 2017/18` <dbl>, `AY 2018/19` <dbl>,
## #   `AY 2019/20` <dbl>, `AY 2020/21` <dbl>, `AY 2021/22` <dbl>
```

It’s worth noting that the drop_na() function provides an argument where we can specify columns. This gives us the flexibility to drop some rows where there is an “NA” in a specific variable, while keeping other rows that have a value in that variable but not in other variables.