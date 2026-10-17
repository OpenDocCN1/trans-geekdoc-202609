In general, the data you will be using is not available in R packages and will instead exist in one or more data files on your personal computer. In order to load in this data to R, you need to use the function that corresponds to the file type you have. For example, you can load a .csv file using the read.csv() function in base R or using the read_csv() function from the readr package, both of which were shown in Chapter 1. As an example, we load the fake_names.csv dataset using both of these functions. Looking at the print output, we can see that there is a slight difference in the data structure and data types storing the data between these two functions. The function read.csv() loads the data as a data frame, whereas the function read_csv() loads the data as a spec_tbl_df, a special type of data frame called a tibble that is used by the tidyverse packages. We cover this data structure in more detail in Chapter 5. For now, note that you can use either function to read in a .csv file.

```
read.csv("data/fake_names.csv")
#>
#>   Name Age       DOB       City State
#> 1  Ken Irwin 37 6/28/85   Providence RI
#> 2  Delores Whittington 56 4/28/67 Smithfield RI
#> 3  Daniel Hughes 41 5/22/82 Providence RI
#> 4  Carlos Fain 83 2/2/40 Warren RI
#> 5  James Alford 67 2/23/56 East Providence RI
#> 6  Ruth Alvarez 34 9/22/88 Providence RI
```

```
readr::read_csv("data/fake_names.csv", show_col_types=FALSE)
#> # A tibble: 6 x 5
#>   Name    Age DOB       City         State
#>   <chr> <dbl> <chr>     <chr>        <chr>
#> 1 Ken Irwin 37 6/28/85   Providence RI
#> 2 Delores Whittington 56 4/28/67 Smithfield RI
#> 3 Daniel Hughes 41 5/22/82 Providence RI
#> 4 Carlos Fain 83 2/2/40 Warren RI
#> 5 James Alford 67 2/23/56 East Providence RI
#> 6 Ruth Alvarez 34 9/22/88 Providence RI
```

In addition to loading data into R, you may also want to save data from R into a data file you can access later or share with others. To write a data frame from R to a .csv file, you can use the write.csv() function. This function has three key arguments: the first argument is the data frame in R that you want to write to a file, the second argument is the file name or the full file path where you want to write the data, and the third argument is whether or not you want to include the row names as an extra column. In this case, we do