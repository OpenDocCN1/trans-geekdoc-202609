
## TABLE 3.2: Summary of data wrangling verbs

| Verb | Data wrangling operation |
|---|---|
| filter() | Pick out subset of rows summarize many values to one using a statistic function like mean(), median(), etc. |
| group_by() | Add grouping structure to rows in data frame. Note this does not change values in data frame, rather only the meta-data |
| mutate() | Create new variables by mutating existing ones |
| arrange() | Arrange rows of a data variable in ascending (default) or descending order |
| inner_join() | Join/merge two data frames, matching rows by a key variable |

## Learning check

(LC3.20) Let's now put your newly acquired data-wrangling skills to the test!
An airline industry measure of a passenger airline's capacity is the available seat miles⁴ which is equal to the number of seats available multiplied by the number of miles or kilometers flown over all flights.

For example, let's consider the scenario in Figure 3.10. Since the airplane has 4 seats and it travels 200 miles, the available seat miles are $4 \times 200 = 800$.

## Measure of airline capacity:
Available Seat Miles

![](img/445742518041017e8f01f11b0c3190d9_124_0.png)

Available Seat Miles = 4 seats x 200 miles
= 800 seat miles

FIGURE 3.10: Example of available seat miles for one flight.

> ⁴https://en.wikipedia.org/wiki/Available_seat_miles

## 3.9 Conclusion

Extending this idea, let's say an airline had 2 flights using a plane with 10 seats that flew 500 miles and 3 flights using a plane with 20 seats that flew 1000 miles, the available seat miles will be 2 * 10 * 500 + 3 * 20 * 1000 = 70,000 seat miles.

Using the datasets included in the nycflights23 package, compute the available seat miles for each airline sorted in descending order. After completing all the necessary data-wrangling steps, the resulting data frame should have 16 rows (for each airline) and 2 columns (airline name and available seat miles). Here are some hints:

- 1. **Crucial.** Unless you are very confident in what you are doing, it is worth not starting to code right away. Rather, first sketch out on paper all the necessary data wrangling steps without exact code, but higher-level pseudocode that is informal yet detailed enough to articulate what you are doing. This way you will not confuse what you are trying to do (the algorithm) with how you are going to do it (writing dplyr code).
- 2. Take a look at all the datasets using the View() function: flights, weather, planes, airports, and airlines to identify which variables are necessary to compute available seat miles.
- 3. Figure 3.7 showing how the various datasets can be joined will also be useful.
- 4. Consider the data-wrangling verbs in Table 3.2 as your toolbox!

### 3.9.2 Additional resources

Solutions to all learning checks can be found in the Appendices of the online version of the book. The Appendices start at https://modernndive/v2/appendix.

An R script file of all R code used in this chapter is available at https://www.modernndive.com/v2/scripts/03-wrangling.R.

If you want to further unlock the power of the dplyr package for data wrangling, we suggest that you check out RStudio's 'Data Transformation with dplyr' cheatsheet. This cheatsheet summarizes more than what we've discussed in this chapter, in particular more intermediate and advanced data wrangling functions, providing quick and easy-to-read visual descriptions. In fact, many of the diagrams illustrating data wrangling operations in this chapter, such as Figure 3.1 on filter(), originate from this cheatsheet.

In the current version of RStudio in 2024, you can find this cheatsheet by going to the RStudio Menu Bar -> Help -> Cheatsheets -> "Data Transformation with dplyr."

On top of the data-wrangling verbs and examples we presented in this section, you'd like to see more examples of using the dplyr package for data wrangling, check out Chapter 5 of R for Data Science (Grolenund and Wickham, 2017).

> http://r4ds.had.co.nz/transform.html

### 3.9.3 What's to come?

So far in this book, we've explored, visualized, and wrangled data saved in data frames. These data frames were saved in a spreadsheet-like format: in a rectangular shape with a certain number of rows corresponding to observations and a certain number of columns corresponding to variables describing these observations.

We'll see in the upcoming Chapter 4 that there are actually two ways to represent data in spreadsheet-type rectangular format: (1) "wide" format and (2) "tall/narrow" format. The tall/narrow format is also known as "tidy" format in R user circles. While the distinction between "tidy" and "non-tidy" formatted data is subtle, it has immense implications for our data science work. This is because almost all the packages used in this book, including the ggplot package for data visualization and the dplyr package for data wrangling, all assume that all data frames are in "tidy" format.

In the current version of RStudio in 2024, you can find this cheatsheet by going to the RStudio Menu Bar -> Help -> Cheatsheets -> "Data Transformation with dplyr."

On top of the data-wrangling verbs and examples we presented in this section, you'd like to see more examples of using the dplyr package for data wrangling, check out Chapter 5 of R for Data Science (Grolenund and Wickham, 2017).

## 4 Data Importing and Tidy Data

In this chapter, we'll learn how to import data into R. These data frames were saved in a spreadsheet-like format: in a rectangular shape with a certain number of rows corresponding to observations and a certain number of columns corresponding to variables.

## 4.1 Importing data

Up this point, we've almost entirely used data stored inside an R package. Say instead you have your own data saved on your computer or somewhere online. How can you analyze this data in R? Spreadsheet data is often saved in one of the following three formats:

First, Comma Separated Values .csv file. You can think of a .csv file as a bare-bones spreadsheet where:

- Each line in the file corresponds to one row of data/one observation.
- Values for each line are separated by commas. In other words, the values of different variables are separated by commas.
- The first line is often, but not always, a header indicating the names of the columns/variables.

Second, an .xlsx spreadsheet file. This format is based on Microsoft’s proprietary Excel software. As opposed to bare-bones .csv files, .xlsx files contain a lot of meta-data (data about data). We recall a previous example of meta-data in Section 3.4 when adding “group structure” meta-data to a data frame by using group_by() . Some examples of Excel meta-data include the use of bold and italic fonts, colored cells, different column widths, and formula macros.

Third, a Google Sheets' file, which is a “cloud” or online-based way to work with a spreadsheet. Google Sheets allows you to download your data in both comma-separated values .csv and Excel .xlsx formats.

## Needed packages

Let's load all the packages needed for this chapter (this assumes you've already installed them).

```
library(dplyr)
library(ggplot2)
library(readr)
library(tidyr)
library(nycflights23)
library(fivirtythree)
```
