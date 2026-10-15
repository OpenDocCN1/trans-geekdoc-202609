In the following examples, we will use versions of the data in the {palmer-penguins} data (Horst et al., 2022; Horst, 2020). We will work with SPSS formatted files; the approach is similar for SAS and Stata formats, and only differs in the details. For example, the haven::read_() functions vary only with the extension; a Stata data file has the extension “.dta”, so the read function is read_dta():

```
haven::read_dta(dpjr::dpjr_data("penguins.dta"))
```

The equivalent for a SAS file is as follows:

```
haven::read_sas(dpjr::dpjr_data("penguins.sas"))
```

Here’s the code to read that same data file in SPSS’s “.sav” format and assigns it to an R object penguins_sav:

```
penguins_sav <- haven::read_sav(dpjr::dpjr_data("penguins.sav"))

penguins_sav
```

```
## # A tibble: 344 x 8
##   species   island   bill_length_mm bill_depth_mm
##   <dbl+lbl> <dbl+lbl>         <dbl>         <dbl>
## 1 1 [Adelie] 3 [Torgerse~        39.1          18.7
## 2 1 [Adelie] 3 [Torgerse~        39.5          17.4
## 3 1 [Adelie] 3 [Torgerse~        40.3          18
## 4 1 [Adelie] 3 [Torgerse~        NA            NA
## 5 1 [Adelie] 3 [Torgerse~        36.7          19.3
## 6 1 [Adelie] 3 [Torgerse~        39.3          20.6
## 7 1 [Adelie] 3 [Torgerse~        38.9          17.8
## 8 1 [Adelie] 3 [Torgerse~        39.2          19.6
## 9 1 [Adelie] 3 [Torgerse~        34.1          18.1
## 10 1 [Adelie] 3 [Torgerse~        42            20.2
## # i 334 more rows
## # i 4 more variables: flipper_length_mm <dbl>,
## #   body_mass_g <dbl>, sex <dbl+lbl>, year <dbl>
```

You will notice that the values of the variables in the .sav version of the penguins dataframe are different than what was read in from the .csv version. All of the variables, including those that were character strings, are numeric.