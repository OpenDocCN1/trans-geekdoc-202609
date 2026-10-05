and "white" throughout this book since those are the actual colors of the balls as seen in the background of the image on our book's First Edition cover^1.) The balls have been mixed beforehand and there does not seem to be any particular pattern for the location of red and white balls inside the bowl.

![](bbox=[0.128, 0.163, 0.871, 0.458])

**FIGURE 7.1:** A bowl with red and white balls.

# 7.1.1 The proportion of red balls in the bowl

We are interested in finding the proportion of red balls in the bowl. To find this proportion we could count the number of red balls and divide this number by the total number of balls. The bowl seen in Figure 7.1 is represented virtually by the data frame included in the modernndive package. The first ten rows are shown here for illustration purposes:

bowl

```
# A tibble: 2,400 x 2
ball_ID color
<int> <chr>
1 1 white
2 2 white
3 3 white
4 4 red
5 5 white
```

> ^1https://modernndive.com/images/logos/book_cover.png