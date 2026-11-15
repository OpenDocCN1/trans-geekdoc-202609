# Setting up a Restricted Boltzmann machine
for Collaborative Filtering

In this recipe, you will learn how to build a collaborative-filtering-based recommendation
system using an RBM. Here, for every user, the RBM tries to identify similar users based on
their past behavior of rating various items, and then tries to recommend the next best item.

# Getting ready

In this recipe, we will use the movielens dataset from the Grouplens research organization.
The datasets (movies.dat and ratings.dat) can be downloaded from the following link.
Movies.dat contains information of 3,883 movies and Ratings.dat contains information
of 1,000,209 user ratings for these movies. The ratings range from 1 to 5, with 5 being the
highest.

```
http://files.grouplens.org/datasets/movielens/ml-1m.zip
```

# How to do it...

This recipe covers the steps for setting up collaborative filtering using an RBM.

+   1. Read the movies.dat datasets in R:

```
txt <- readLines("movies.dat", encoding = "latin1")
txt_split <- lapply(strsplit(txt, "::"), function(x)
as.data.frame(t(x), stringsAsFactors=FALSE))
movies_df <- do.call(rbind, txt_split)
names(movies_df) <- c("MovieID", "Title", "Genres")
movies_df$MovieID <- as.numeric(movies_df$MovieID)
```

+   2. Add a new column (id_order) to the movies dataset, as the current ID column
+   (UserID) cannot be used to index movies because they range from 1 to 3,952:

```
movies_df$id_order <- 1:nrow(movies_df)
```

+   3. Read the ratings.dat dataset in R:

```
ratings_df <- read.table("ratings.dat",
sep=":", header=FALSE, stringsAsFactors = F)
ratings_df <- ratings_df[,c(1,3,5,7)]
colnames(ratings_df) <- c("UserID","MovieID","Rating","Timestamp")
```