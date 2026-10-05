
## 4.1 Importing data

is to go the Google Sheets menu bar -> File -> Download as -> Select "Microsoft Excel" or "Comma-separated values" and then load that data into R. A more advanced way to import Google Sheets data in R is by using the googheets4 package, a method we leave to a more advanced data science book.

We'll cover two methods for importing .csv and .xlsx spreadsheet data in R: one using the console and the other using RStudio's graphical user interface, abbreviated as "GUI".

### 4.1.1 Using the console

First, let's import a Comma Separated Values .csv file that exists on the internet. The .csv file dem_score contains values of democracy in different countries spanning 1952 to 1992 and is accessible at https://moderndive.com/data/dem_score.csv. Let's use the read_csv() function from the readr (Wickham et al., 2024b) package to read it off, import it into R, and see it in a data frame dem_score.

```
library(readr)
dem_score <- read_csv("https://moderndive.com/data/dem_score.csv")
dem_score
```

```
# A tibble: 96 x 10
country '1952' '1957' '1962' '1967' '1972' '1977' '1982' '1987' '1992' '1997'
<chr> dbl dbl dbl dbl dbl dbl dbl dbl dbl dbl
1 Albania -9 -9 -9 -9 -9 -9 -9 5
2 Argentina -9 -1 -1 -9 -9 -8 -8 7
3 Armenia -9 -7 -7 -7 -7 -7 -7 7
4 Australia 10 10 10 10 10 10 10 10
5 Austria 10 10 10 10 10 10 10 10
6 Azerbaijan -9 -7 -7 -7 -7 -7 -7 1
7 Belarus -9 -7 -7 -7 -7 -7 -7
8 Belgium 10 10 10 10 10 10 10 10
9 Bhutan -10 -10 -10 -10 -10 -10 -10 -10
10 Bolivia -4 -3 -3 -4 -7 -7 8 9 9
# with 86 rows
```

In this dem_score data frame, the minimum of -10 corresponds to a highly autocratic nation, whereas a value of 10 corresponds to a highly democratic nation. Note that backticks surround the different variable names. Names in R by default are not allowed to start with a number nor include spaces, but we can get around this by surrounding the column with backticks. We'll revisit the dem_score data frame in the case study in the upcoming Section 4.3.

> 2 https://googheets4.tidyverse.org/

Note that the read_csv() function included in the readr package is different from the read_csv() function that comes installed with R. While the difference in the names might seem trivial (an _ instead of a), the read_csv() function is, in our opinion, easier to use since it can easily read data off the web and generally imports data at a much faster speed. Furthermore, the read_csv() function included in the readr saves data frames as tibbles by default.

### 4.1.2 Using RStudio's interface

Let's read in the same data, but this time from an Excel file saved on your computer. Furthermore, we will do this using RStudio's graphical instead of running read_csv() in the console. First, download the Excel file dem_score.xlsx going to https://moderndive/data/dem_score.xlsx, then:

- Go to the files of RStudio.
- Navigate to the directory (i.e., folder on your computer) where the downloaded dem_score.xlsx Excel file is saved. For example, this might be in your Downloads folder.
- Click on dem_score.xlsx.
- Click "Import Dataset..."

At this point, you will see a screen pop-up like Figure 4.1. After clicking on the "Import" button on the bottom right of Figure 4.1, RStudio will spread this spread-sheet's data in a data frame dem_score and display its contents in the spread sheet viewer.

![](img/445742518041017e8f01f11b0c3190d9_130_0.png)

FIGURE 4.1: Importing an Excel file to R.

## 4.2 Tidy data

Furthermore, note the “Code Preview” block in the bottom right of Figure 4.1. You can copy and paste this code to reload your data later programmatically, instead of repeating this manual point-and-click process.

Let’s now switch gears and learn about the concept of “tidy” data format with a motivating example from the fiftheight package. The fiftivirtyeight package (Kim et al., 2021) provides access to the datasets used in many articles published by the data journalism website, FiveTightyEight.com³. For a complete list of all 128 datasets included in the fiftyeight package, check out the package by going to: https://fivethirtyeight-r.netlify.app/articles/fivethirtyeight.html.

Let’s focus attention on the drinks data frame and look at its first 5 rows:

```
# A tibble: 5 x 5
country  beer_servings  spirit_servings  wine_servings
<chr>    <int>           <int>           <int>
1 Afghanistan  0               132              54
2 Albania      89               0               14
3 Algeria     25              217              312
4 Andorra     245              57               45
5 Angola      217                               0
# # i 1 more variable: total_litres_of_pure_alcohol <dbl>
```

After reading the help file by running `?drinks`, you’ll see that drinks is a data frame containing results from a survey of the average number of servings of beer, spirits, and wine consumed in 193 countries. This data was originally reported on FiftyEight in Mona.

Let’s apply some of the wrangling verbs we learned in:

- 1. filter() to consider only the
- 2. select() all columns except
- 3. rename(beer_servings, spirit_servings, wine)

Let's ask ourselves a question: "How would we create side-by-side barplots displaying:

| country | beer_servings | spirit_servings | wine_servings |
| :--- | :--- | :--- | :--- |
| Afghanistan | 0 | 132 | 54 |
| Albania | 89 | 0 | 14 |
| Algeria | 25 | 217 | 312 |
| Andorra | 245 | 57 | 45 |
| Angola | 217 | | 0 |

³ https://fivethirtyeight.com/
⁴ https://fivethirtyeight.com/
