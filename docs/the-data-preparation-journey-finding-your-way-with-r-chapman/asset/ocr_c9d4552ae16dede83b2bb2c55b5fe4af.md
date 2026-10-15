```
# convert the resulting object into a "data.set" format
nts_person_2020_ds <- memisc::as.data.set(nts_person_2020)
```

That dataset object is now converted into a tibble, using the as_haven() function. This tibble has all of the variable and value labels assigned, accessible via the functions in the {labelled} package.

```
nts_person_2020_hav <- memisc::as_haven(nts_person_2020_ds)
nts_person_2020_hav
```

```
## # A tibble: 79,771 x 13
##   pumfid verd ate  refyear  quarter inf_q01 inf_q02
##   *   <dbl> <chr>  <int+lbl> <int+l> <int+l> <int+lb>
## 1 1006690 10/12/2~ 2020 [Yea~ 1 [Ref~ 1 [Yes] 35 [Ont~
## 2 1006691 10/12/2~ 2020 [Yea~ 1 [Ref~ 1 [Yes] 35 [Ont~
## 3 1006692 10/12/2~ 2020 [Yea~ 1 [Ref~ 1 [Yes] 24 [Que~
## 4 1006693 10/12/2~ 2020 [Yea~ 1 [Ref~ 1 [Yes] 35 [Ont~
## 5 1006694 10/12/2~ 2020 [Yea~ 1 [Ref~ 1 [Yes] 24 [Que~
## 6 1006695 10/12/2~ 2020 [Yea~ 1 [Ref~ 1 [Yes] 35 [Ont~
## 7 1006696 10/12/2~ 2020 [Yea~ 1 [Ref~ 1 [Yes] 13 [New~
## 8 1006697 10/12/2~ 2020 [Yea~ 1 [Ref~ 1 [Yes] 11 [Pri~
## 9 1006698 10/12/2~ 2020 [Yea~ 1 [Ref~ 1 [Yes] 35 [Ont~
## 10 1006699 10/12/2~ 2020 [Yea~ 1 [Ref~ 1 [Yes] 35 [Ont~
## # i 79,761 more rows
## # i 7 more variables: page_grp <int+lbl>,
## #   gend_bin <int+lbl>, incomgr2 <int+lbl>,
## #   memc18up <int+lbl>, memclt18 <int+lbl>,
## #   resprov <int+lbl>, pumfwp <dbl>
```

In our final step, we save the dataframe as SPSS, Stata, and RDS files for future use.

One important note for Stata users is that there is a “version” argument, which allows us to create a file that can be read by older versions of Stata (the default is Stata 15).

```
# export haven format table as SPSS .sav file
haven::write_sav(nts_person_2020_hav,
  here("data_output", "nts_person_2020.sav"))

# export haven format table as Stata .dta file
```