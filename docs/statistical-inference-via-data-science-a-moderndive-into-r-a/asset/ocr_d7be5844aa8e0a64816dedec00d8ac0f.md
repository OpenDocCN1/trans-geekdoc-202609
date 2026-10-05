# 2.9 Conclusion

question first and the aes() mapping second, you can omit the explicit statement of the argument names data = and mapping.

Going forward for the rest of this book, all ggplot() code will be the second segment: with the data = mapping = explicit naming of the argument omitted with the default ordering of arguments respected. We'll do this for brevity's sake; it's common to see this style when reviewing other R users' code.

# 2.9.3 Additional resources

Solutions to all Learning checks can be found in the Appendices of the online version of the book. The Appendices start at https://modernndive.com/v2/appendix.

An script file of all R code used in this chapter is available at https://www.modernndive.com/v2/scripts/02-visualization.R.

If you want to unlock the power of RStudio's "ggplot2 Data Visualization with ggplot2" cheatsheet. This cheatsheet summarizes much more than we've discussed in this chapter. In particular, it presents many more than the 5 geometric objects we covered in this chapter while providing quick and easy-to-read visual descriptions. For all the geometric objects, it also lists the possible aesthetic attributes one can tweak. In the current version of RStudio in mid 2024, you can access this cheatsheet by going to the RStudio Menu Bar -> Help -> Cheatsheets -> Data Visualization with ggplot2. Alternatively, you can preview the cheat sheet by going to the ggplot2 Github page with this link6.

# 2.9.4 What's to come?

Recall in Figure 2.2 in Section 2.3 we visualized the relationship between department and delay for Envoy Air flights, rather than all flights. This data is saved in the envoy_flights data frame from the modernndive package.

In reality, the envoy_flights data frame is merely a subset of the flights data frame from the nycflights3 package consisting of all flights that left NYC in 2023. We created envoy_flights using the following code that uses dplyr package for data wrapping:

```
library(dplyr)

envoy_flights <- flights |
filter(carrier == "MQ")

gggplot(data = envoy_flights, mapping = aes(x = dep_delay, y = arr_delay)) + 
ge_point())
```

> 6https://github.com/rstudio/cheatsheets/blob/main/data-visualization-2.1.pdf