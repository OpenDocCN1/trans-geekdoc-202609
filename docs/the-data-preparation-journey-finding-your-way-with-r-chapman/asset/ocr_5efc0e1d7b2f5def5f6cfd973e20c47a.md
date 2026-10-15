```
## [1] "readme"              "df_HR_main"
## [3] "df_HR_transaction" "df_HR_train"
```

The one we want for our example is “df_HR_main”, which contains the employee ID, name, birth date, and gender for each of the 999 staff.

In our read_excel() function we can specify either the name of the sheet or the number based on its position in the Excel file. While the default is to read the first sheet, it’s often good practice to be specific, as Excel users are prone to re-arranging the order of the sheets (including adding new sheets). And because they seem (slightly) less likely to rename sheets, we have another reason to use the name rather than the number.

```
df_HR_main <- 
  read_excel(
    path = dpjr::dpjr_data("cr25/cr25_human_resources.xlsx"),
    sheet = "df_HR_main"
  )
```

```
## New names:
## * ` ` -> `...2`
## * ` ` -> `...3`
## * ` ` -> `...4`
## * ` ` -> `...5`
## * ` ` -> `...6`
## * ` ` -> `...7`
```

```
head(df_HR_main)
```

```
## # A tibble: 6 x 7
##   df_HR_main   ...2   ...3   ...4   ...5   ...6   ...7
##   <chr>        <chr>  <chr>  <chr>  <chr>  <lgl>  <chr>
## 1 The main datab... <NA> <NA> <NA> <NA> NA <NA>
## 2 <NA>         <NA> <NA> <NA> <NA> NA <NA>
## 3 <NA>         <NA> <NA> <NA> <NA> NA <NA>
## 4 <NA>         emp_~ date~ name gend~ NA NOTE:
## 5 <NA>         ID001 29733 Avri~ Fema~ NA date~
## 6 <NA>         ID002 26931 Katy~ Fema~ NA <NA>
```

This sheet possesses a structure we commonly see in Excel files: in addition to the data of interest, the creators of the file have helpfully added a title for the sheet. They might also put a note in the “margins” of the data (often to