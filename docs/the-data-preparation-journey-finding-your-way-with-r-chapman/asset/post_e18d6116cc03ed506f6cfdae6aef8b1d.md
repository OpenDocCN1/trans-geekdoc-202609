
Another option is the `ons_browse_qmi()` function, which opens the relevant ONS page in your web browser software.

```
ons_browse_qmi(id = "retail-sales-index")
```

Finally, we will use the relevant id value in an `ons_get()` function to retrieve the data.

```
df_retail_sales <- ons_get(id = "retail-sales-index")
```

There are 42,400 rows in this data (as of 2023-06-14), with multiple variables for each month. Your analysis will require further filtering and selecting, but with the {onsr} package providing the access to the data, you are well on your way.

## 9.2.2 Statistics Canada

Statistics Canada, a department of the Government of Canada, provides a socioeconomic time series database known as “CANSIM”. The data posted to the database is most of the aggregate data collected by Statistics Canada on a regular basis, such as the Labour Force Survey (from which we get updates on the unemployment rate), the Consumer Price Index Survey (about inflation), and health-related information from pregnancy and births to life expectancy and deaths.

The package {cansim} (von Bergmann and Shkolnik, 2021) uses the API that Statistics Canada has created in order to facilitate direct download of hundreds of data tables and thousands of individual time series.

```
library(cansim) # access Statistics Canada's CANSIM data repository
```

One of the many tables related to international travel that is published in CANSIM is “Table: 24-10-0050-01 Non-resident visitors entering Canada, by country of residence”¹.

Here’s a screenshot of the table, showing the number of people arriving by their continent of residence.

¹The webpage for the table, showing the most recently available data, is here: https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=2410005001

Geography: Canada (map)

| Country of residence² | March 2023 | April 2023 | May 2023 | June 2023 | July 2023 |
|---|---:|---:|---:|---:|---:|
| **Visitors** |  |  |  |  |  |
| Non-resident visitors entering Canada | 1,382,309 | 1,674,026 | 2,377,181 | 3,332,607 | 4,000,340 |
| United States of America residents entering Canada | 1,094,111 | 1,300,810 | 1,831,912 | 2,632,723 | 3,132,681 |
| Residents of countries other than the United States of America entering Canada | 288,198 | 373,216 | 545,269 | 699,884 | 867,659 |
| Americas, countries other than the United States of America | 74,654 | 92,600 | 90,704 | 116,030 | 141,622 |
| North America, countries other than the United States of America | 42,446 | 56,789 | 49,022 | 56,651 | 69,313 |
| Central America | 3,226 | 5,116 | 4,851 | 6,787 | 6,769 |
| Caribbean | 11,203 | 15,742 | 14,952 | 20,830 | 28,585 |
| South America | 17,779 | 14,953 | 21,879 | 31,762 | 36,955 |
| Americas, n.o.s.³ | 0 | 0 | 0 | 0 | 0 |

**FIGURE 9.1** *CANSIM table 24-10-0050-01.*

This table might be useful if you were developing a marketing campaign and you wanted to understand where tourists are coming from—the biggest markets and the fastest growing. But as shown, it is at too high a level; this is Canada by continent. For our purposes, we need to see specific country, those entering Canada via British Columbia, and a longer time series.

We could use the filters and fiddle around making sure we got the right selections and then download the data, but if we have to do that next month it is going to be inefficient. We could also first click on the “download options” button and select “download entire table...” but again, this is not the most efficient way to do this, since there are a few manual steps we have to take and then open the file into R and filter to select the series we want.

This is where the {cansim} package comes in.

### Step 1: download the data.

- The `get_cansim()` function takes the table number as the parameter, and connects to CANSIM and downloads the data into an R dataframe.

```
travellers <- get_cansim("24-10-0050-01")
```

We will come back to filtering and variable selection along with working with date fields later, but here’s the code in R using the functions of the {dplyr} package to filter for the British Columbia cases during the month of June 2019:

```
travellers_bc <- 
travellers |> 
  filter(GEO == "British Columbia",
         REF_DATE == "2019-06")

glimpse(travellers_bc, width = 65)
```

There are 287 rows, one for each of the categories in the Country of residence variable. It’s important to note that these are not just countries, but the variable also includes subtotals. What if we just want a monthly report on a single continent? One option would be for us to filter the “COUNTRY” variable; here we filter for visitors from Europe.

```
travellers_bc |> 
  filter(`Country of residence` == "Europe")
```

One of the features of CANSIM and other similar tables is that the individual series are given a single identifier. In the case of CANSIM, these are called the “vector numbers”. Scroll to the right on this table, and you’ll see a variable called VECTOR. The vector identifier (sometimes called “the vector number” even though it’s a character string!) for European travellers entering Canada via British Columbia is v1277198032.

The {cansim} package also gives us a function to select a single vector number, so we can be more efficient still. We can speed up the download time and skip the filtering steps to get to the one we want. (Note that this function requires us to enter a start date, and converts the reference date variable to the YYYY-MM-DD format.)

```
get_cansim_vector("v1277198032", start_time = "2015-01-01")
```

This table has the shortcoming of not including the “GEO” or “Country of residence” variables, so we need to ensure that we have adequately documented what has been accessed.

The {cansim} package includes other very useful functions if you find yourself exploring Statistics Canada data sets.

The function get_cansim_table_overview() provides an abstract about the data table.

```
get_cansim_table_overview("24-10-0050-01")
```

## 9.3 Other R packages for direct access to data

The following is an incomplete list (in alphabetical order by name) of other packages that have been developed to provide direct access to a specific web resource.

- {bcdata} (Teucher et al., 2023) has tools to search, query, and download tabular and ‘geospatial’ data from the British Columbia Data Catalogue.
- {fredr} (Boysel and Vaughan, 2023) connects to the “Federal Reserve Economic Data”, or FRED, hosted by the Federal Reserve Bank of St. Louis. This data repository has (according to Wikipedia) over 800,000 economic time series from various sources.
- {opendatatoronto} (Gelfand and City of Toronto, 2022) provides a direct connection to the City of Toronto Open Data Portal.
- The {readabs} (Cowgill et al., 2023) package downloads and tidies data from the Australian Bureau of Statistics.
- {RBNZ} (Watson, 2020) downloads data from the Reserve Bank of New Zealand Website.
- {tidycensus} (Walker et al., 2023) has tools that connect to the United States Census Bureau and returns tidyverse-ready dataframes with the option of adding geographic details to allow for mapping. (See also (Walker, 2023).)

## 10 Linking to relational databases

In this chapter:

- Importing data directly from relational databases (SQL)
- Using relational data as part of the data preparation workflow

### 10.1 Relational data

Relational databases are commonly used for data storage. Unlike a “flat file” which contains all of the variables, the data is stored in multiple tables, which are linked via common variables (known as the “keys”). This facilitates efficient storage, as information does not need to be duplicated in multiple rows. We have seen an example of a relational table earlier, where we built a concordance table for the administrative geography of England and Wales in Chapter 6.

In that example, all of the data was loaded into our computer’s memory. In other instances, the size of the database, across multiple tables, will be such that it exceeds the capacity of your computer. In those cases, a server-based database will be established, and as the data analyst, we will need to retrieve only the variables and records that we need for our work. A database query can also include the calculation of summary statistics, which shifts the computational load to the server.

While SQL is the most commonly used query language, there are R packages that allow us to

- Connect to a database,
- Write the code for our queries in R,
- Run the query, and
- Do our work in an R environment.
