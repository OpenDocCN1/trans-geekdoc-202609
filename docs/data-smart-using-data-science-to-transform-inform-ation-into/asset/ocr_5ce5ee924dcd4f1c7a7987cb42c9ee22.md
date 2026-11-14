```
winedata.transposed %>%
aggregate(by = list(clusters.df$cluster.id), sum) %>%
select(-1) %>%
t()
```

```
winedata.plus.counts <-
winedata %>%
select(1:7) %>%
cbind(winedata.clustercount)
```

That's it—from reading in the data all the way to analyzing the clusters. Pretty nuts! And that's because the call to `skmeans()` pretty much isolates all the complexity of this method away from you.

# Building AI Models on the Pregnancy Data

> The CSV files used in this section, `Pregnancy.csv` and `Pregnancy_Test.csv`, are available for download at the book's website, www.wiley.com/go/datasmart2e.

In this section, you're going to replicate some of the pregnancy prediction models you built in this book. Specifically, you're going to build two classifiers using the `glm()` function (general linear model) with a logistic link function and then with the `randomForest()` function.

The training and test data are separated into two CSV files, called `Pregnancy.csv` and `Pregnancy_Test.csv`. Go ahead and upload them into your working directory and then load them into a couple of dataframes.

```
> PregnancyData <- read.csv('Pregnancy.csv')
> PregnancyData.Test <- read.csv('Pregnancy_Test.csv')
```

You can then run `summary()` and `str()` on the data to get a feel for it. It's immediately apparent that the gender and address type data have been loaded as categorical data, but as you can see in the `str()` output, the response variable (1 for pregnant, 0 for not pregnant) has been treated as numeric instead of as two distinct classes:

```
> str(PregnancyData)
'data.frame':   1000 obs. of  18 variables:
$ Implied.Gender   : chr  "M" "M" "M" "U" ...
$ Home.Apt..PO.Box : chr  "A" "H" "H" "H" ...
$ Pregnancy.Test   : int  1 1 1 0 0 0 0 0 0 0 ...
$ Birth.Control    : int  0 0 0 0 0 0 1 0 0 ...
$ Feminine.Hygiene : int  0 0 0 0 0 0 0 0 0 ...
$ Folic.Acid       : int  0 0 0 0 0 0 1 0 0 ...
```