# 3.7 join data frames

# 3.7.1 Matching key variable names

In the flights and airlines data frames, the key variable we want to join/merge/match the rows by the same name: carrier. Let's use the inner_join() function to join the two data frames, where the rows will be matched by the variable carrier, and then compare the resulting data frames:

```
flights_joined <- flights |>
inner_join(airlines, by = "carrier")nView(flights)
View(flights_joined)
```

Observe that the flights and flights_joined data frames are identical except that flights_joined has an additional variable name. The values of name correspond to the airline companies' names as indicated in the airlines data frame.

A visual representation of the inner_join() is shown in Figure 3.8 (Grolemund and Wickham, 2017). There are other types of joins available (such as left_join(), right_join(), outer_join(), and anti_join())), but the inner_join() will solve nearly all of the problems you will encounter in this book.

![](bbox=[0.1095, 0.4965, 0.8905, 0.6565])

FIGURE 3.8: Diagram of inner join from R for Data Science.

# 3.7.2 Different key variable names

Say instead you are interested in the destinations of all domestic flights departing NYC in 2023, and you ask questions like: "What cities are these airports in?", or "Is "ORD?, Orlando?," or "Where is "FLL?"

The airports data frame contains the airport codes for each airport:

```
View(airports)
```