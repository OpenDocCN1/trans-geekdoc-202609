# 5.6 Sorting Data and Selecting Observation

# 5.6.2 Select observation using filter()

We the filter() to select objects based on certain criteria. Here, in this example, we will create a new dataset (which we will name stroke_m_40) that contains patients who have sex as male and Glasgow Coma Scale (gcs) at 7 or higher:

+   - gender is male
- gcs at 7 or higher

```
stroke_m_7 <- stroke %%
filter(sex == 'male', gcs >= 7)
stroke_m_7
```

```
# A tibble: 85 x 12
# dea dod status sex dm gcs sbp dbp wbc time2
# #<date> <date> <chr> <chr> <dbl> <dbl> <dbl> <dbl> <dbl>
# 1 2011-02-17 2011-02-18 alive male no 15 151 73 12.5 1
# 2 2011-03-20 2011-03-21 alive male no 15 196 123 8.1 1
# 3 2011-05-22 2011-05-23 alive male no 11 171 80 8.7 1
# 4 2011-11-28 2011-11-29 dead no 10 207 128 10 1
# 5 2012-05-22 2012-02-23 male no 7 150 80 15.5 1
# 6 2012-06-25 2012-03-26 alive male no 14 128 79 10.3 1
# 7 2012-04-04 2012-04-03 alive male no 15 143 59 7.1 1
# 8 2011-01-31 2011-02-02 alive male no 15 161 107 9.5 2
# 9 2011-02-06 2011-02-08 alive male no 15 153 61 11.2 2
# 10 2011-10-20 2011-02-22 alive male no 15 143 93 15.6 2
```

```
# i 75 rows
# # i 2 variables: stroke_type <chr>, referral_from <chr>
```

Next, we will create a new dataset (named stroke_high_BP) that contain

+   - stroke_high_BP <- stroke %%
filter(sbp > 130 | dbp > 90)
stroke_high_BP

```
# A tibble: 173 x 12
# dea dod status sex dm gcs sbp dbp wbc time2
# #<date> <date> <chr> <chr> <chr> <dbl> <dbl> <dbl> <dbl>
# 1 2011-02-17 2011-02-18 alive male no 15 151 73 12.5 1
# 2 2011-03-20 2011-03-21 alive male no 15 196 123 8.1 1
# 3 2011-04-12 2011-04-13 dead male no 3 170 103 13.9 1
# 4 2011-05-22 2011-05-23 alive male no 11 171 80 8.7 1
# 5 2011-07-11 2011-07-12 dead female yes 6 170 90 10.5 1
```