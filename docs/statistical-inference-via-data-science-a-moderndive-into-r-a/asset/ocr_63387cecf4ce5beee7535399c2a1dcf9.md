# 118

# 5 Simple Linear Regression

of the individual variables in your data, whether any potential relationships exist between variables, whether there are outliers and/or missing values, and (most importantly) how to build your model. Here are three common steps in an EDA:

+   1. Most Crucially, looking at the raw data values.
2. Computing summary statistics, such as means, medians, and maximums.
3. Creating visualizations.

We perform the first common step in an exploratory data analysis: looking at the raw data values. Because this seems so trivial, unfortunately many analysts ignore it. However, getting an early sense of what your raw data looks like can often prevent many issues down the road.

You can do this using RStudio's spreadsheet viewer or by using the glimpse() function as introduced in Subsection 1.4.3 on exploring data frames:

```
glimpse(UN_data_ch5)

Rows: 181
Columns: 4
$ iso <chr>"AFG", "ALB", "DZA", "AGO", "ATG", "ARG", "ARM", "AUS",~
$ life_exp <dbl> 53.6, 79.5, 78.0, 62.1, 77.7, 78.3, 76.1, 83.1, 82.3, 7~
$ fert_rate <dbl> 4.3, 1.4, 2.7, 5.0, 1.6, 1.9, 1.6, 1.6, 1.5, 1.4, 1~~
$ obese <dbl> 5.5, 21.7, 27.4, 8.2, 18.9, 28.3, 20.2, 29.0, 20.1, 19.~
```

Observe that Rows: 181 indicates that there are 181 rows/observations in UN_data_ch5 after filtering out the missing values, where each row corresponds to one observed country/member state. It is important to note that the observational unit is an individual country. Recall from Subsection 1.4.3 the observational unit is the “type of” that is being measured by our variables.

A full description of all the variables included in un_member_states_2024 can be found by reading the associated file (run ?un_member_states_2024 in the console). Let’s describe only the 4 variables we selected in UN_data_ch5:

+   1. iso: An identification variable used to distinguish between the 181 countries in the filtered dataset.
2. fert_rate: A numerical variable representing the country’s fertility rate in 2022 corresponding to the expected number of children born per woman in child-bearing years. This is the outcome variable y of interest.
3. life_exp: A numerical variable representing the country’s average life expectancy in 2022 in years. This is the primary variable x of interest.