```
3   moore   1973   blue
4   dalton  1987   green
5   brosnan 1995   blue
6   craig   2006   blue
```

The `data.frame` function is going to take care of recognizing which of these columns are factors and which are numeric. You can see this difference by calling the `str()` and `summary()` functions (the `str` stands for "structure").

```
> str(bonddata)
'data.frame':   6 obs. of  3 variables:
$ bondnames: chr  "connery" "lazenby" "moore" "dalton" ...
$ firstyear: num  1962 1969 1973 1987 1995 ...
$ eyecolor : chr  "brown" "brown" "blue" "green" ...
> summary(bonddata)
bondnames      firstyear        eyecolor
Length:6       Min.   :1962   Length:6
Class :character   1st Qu.:1970   Class :character
Mode :character   Median :1980   Mode :character
          Mean   :1982
          3rd Qu.:1993
          Max.   :2006
```

Note that the year is being treated as a number. You could factorize this column using the `factor()` function if you wanted it treated categorically instead.

And one of the awesome things about dataframes is that you can reference each column using a `$` character plus the column name, as shown here:

```
> bonddata$firstyear <- factor(bonddata$firstyear)
> summary(bonddata)
bondnames      firstyear        eyecolor
Length:6       1962:1         Length:6
Class :character 1969:1         Class :character
Mode :character 1973:1         Mode :character
          1987:1
          1995:1
          2006:1
```

When you run the `summary` function, the years are rolled up by category counts instead of by distribution data.

# # How to Ask for Help in R

To understand what a function does, just type a question mark before it when you put it into the console.

```
> ?sqrt
```

This will pop open a Help window on the function in the bottom right of the IDE (see Figure 11.3).