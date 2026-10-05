# 7.1 First activity: Red balls

6 6 white
7 7 red
8 8 white
9 9 red
10 10 white
# i 2,390 more rows

The bowl has 2400 rows representing the 2400 balls in the bowl shown in Figure 7.1. You can view and scroll through View(bowl) in RStudio's data viewer. The first variable ball_id is used as an identification variable as discussed in Subsection 1.4.4; none of the balls in the actual bowl are marked with numbers.

The second variable color indicates whether a particular virtual ball is red or white. We compute the proportion of red balls in the bowl using the dplyr data wrangling verbs presented in Chapter 3. A few steps are needed to determine this proportion. We present these steps separately to remind you how they work but later introduce all the steps together by using the mutate() function from Section 3.5 that allows us to create a new Boolean variable called is_red.

```
bowl |>
mmutate(is_red = (color == "red"))
```

```
# A tibble: 2,400 x 3
ball_ID color is_red
<int> <chr> <lgl>
1 1 white FALSE
2 2 white FALSE
3 3 white FALSE
4 4 red TRUE
5 5 white FALSE
6 6 white FALSE
7 7 red TRUE
8 8 white FALSE
9 9 red TRUE
10 10 white FALSE
# i 2,390 more rows
```

The variable is_red returns the Boolean (logical) value TRUE for each row where color == "red" and FALSE for every row where color is not equal to "red". Since R treats TRUE like the number 1 and FALSE like the number 0, accounting for TRUES AND FALSEES