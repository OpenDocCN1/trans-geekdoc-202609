```
## 3 Walt Whitman      NY  LW-1752-TD08
## 4 Ursula K. Le Guin  CA  EZ-9789-EA77
## 5 Ta-Nehisi Coates   NY  YN-5151-NV82
## 6 W. E. B. Du Bois    MA  HN-6134-NF80
## 7 F. Scott Fitzgerald MN  YH-4405-TR02
## 8 N.K. Jemisin        IA  EF-7340-DW20
## 9 Flannery O'Connor   GA  HB-8269-XC88
## 10 Henry David Thoreau MA  RL-8200-SU83
```

```
Rows: 10 Columns: 3— Column specification

chr (3): name, state, unique_id
i Use `spec()` to retrieve the full column specification for this data.
i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

FIGURE 5.8 read_fwf message.

# 5.3.1 An extreme example of a fixed-width file

A particularly interesting research question is the relationship between education level and different health outcomes. In this example, we will start the process of importing a large file that contains data that will allow us to explore whether there is a correlation.

Statistics Canada has made available a Public-Use Microdata File (PUMF) of the Joint Canada/United States Survey of Health (JCUSH), a telephone survey conducted in late 2002 and early 2003. There were 8,688 respondents to the survey, 3,505 Canadians and 5,183 Americans. The data file that is available is anonymized, so we have access to the individual responses, which will facilitate additional analysis.

The webpage for the survey, including the PUMF file, data dictionary, and methodological notes, is here: https://www150.statcan.gc.ca/n1/pub/82m0022x/2003001/4069119-eng.htm

The PUMF is a fixed-width file named “JCUSH.txt”. This file is quite a lot larger than the author names example above. There are the 8,688 records, one for each survey respondent. The data also consists of 366 variables, a combination of assigned variables (such as the unique respondent identification number and the country), survey question responses, and derived variables that are calculated as part of the post-survey data processing.