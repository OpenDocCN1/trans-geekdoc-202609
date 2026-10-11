
# Avoid namespace conflicts

You may run into namespace conflicts if you use functions from multiple packages with the same name. To avoid this, you can use the `::` operator to specify which package’s function you want to use. For example, instead of using `summarize()`, you could use `dplyr::summarize()` to specify that you want to use the `summarize()` function from the `dplyr` package.

# Working directories

When working with R, keeping your files organized is essential. This means creating a folder for each project you are working on and keeping related files within that folder. The R working directory is the folder that R starts in by default.

R uses a designated folder on your computer, called a working directory, to locate files related to a specific project. Here, R looks for files to load and saves files. On different computers, the location of your working directory may be different, and you can only have one working directory open at once. To determine the current working directory, you can run the following code:

```
# view the current working directory
getwd()
## “C:/Users/Hp/Documents”
```

When organizing your datasets, you have two options: first, you can put your files into your working directory, and second, to change your working directory to the folder where your files are stored. You can modify your working directory to any folder on your computer by using the function `setwd()` and specifying the file path of the new working directory. Let us take a look at the following example:

```
# set working directory
setwd(“E:/Book_Project”)
```

From the menu bar, you can click on **Session | Set Working Directory | Choose Directory** to move your working directory. To look into the files in the working directory, you can use the function `list.files()`.

It is essential to be mindful of your working directory when reading and writing files in R. If you are not working in the correct folder, you may encounter errors or overwrite existing files. Keeping your files organized and setting your working directory appropriately ensures that your R code is reproducible and easy to share with others.

# Objects

Let us go back to Aarya’s example. To analyze her Netflix usage, Aarya must first comprehend the concept of objects in R. An object is a way to save data by storing it inside a designated name that can be used to recall the stored data. All data is stored in objects, ranging from simple numbers or character strings to complex structures like statistical analysis summaries and plots.

To proceed with her analysis, Aarya created three distinct R objects called `hours_watched_movies`, `hours_watched_tv`, and `total_hours_watched` to save the number of hours she spent watching movies, TV shows, and the total time spent watching Netflix respectively. With these objects, Aarya can perform numerous operations to analyze her data efficiently. To assign a name to a number, you use the assignment operator: `<-` (no space between `<` and `-`). Take a look at the following example:

```
# define hours_watched_movies
hours_watched_movies <- 6

# store the time spent (in hours) watching TV shows
hours_watched_tv <- 12

# save total time spent (in hours) into total_hours_watched
total_hours_watched <- 18
```

To check what is stored in the `total_hours_watched` object, Aarya can simply type its name, `total_hours_watched`, in the R console, and it will display the object value on the following line:

```
# display the value stored in total_hours_watched
total_hours_watched
## 18
```

> **Note:** Throughout the book, the output of R code will be followed by `##`.

Now, let us see how Aarya creates various R objects and assigns values to them to analyze her data efficiently.

# Vectors

A vector is a collection of elements of the same data type. Vectors can contain either numbers, characters, or logicals but not a mixture of these types of data. Vectors are R’s most basic data structure and are used for many different purposes, such as storing data or performing mathematical operations. A vector can be considered as a one-dimensional array, with each element in the vector having an index or position. Understanding how to create and manipulate vectors is essential, as they are the building blocks for more complex data structures and analysis. Let us know more about some of these types of vectors.

## Numeric vector

Aarya can use a numeric vector to store the duration of each movie or TV show she watched on Netflix. For example, she can create a numeric vector named `movie_durations` and assign the duration of each movie she watched to it. For example:

```
# create a vector of durations of movies watched
movie_durations <- c(98, 109, 124, 138, 115, 149)

# print movie_durations
movie_durations
## 98 109 124 138 115 149
```

This creates a numeric vector named `movie_durations` with 6 elements representing the duration of each movie she watched in minutes. The `c()` creates a vector or concatenates two or more vectors together. The `c()` function stands for combine or concatenate, and is one of the most commonly used functions in R.

## Character vector

A character vector stores a sequence of character values. A character value is any text you want to store, such as words, sentences, or individual characters. You can use the `c()` function to create a character vector by enclosing the values in quotation marks. For instance, Aarya creates a character vector to store the movies she watched:

```
# create a vector of movies watched
movie_titles <- c(“Rush Hour”, “Knight and Day”, “The Notebook”, “Shutter Island”, “Now you see me”, “The Da Vinci Code”)

# print movie_titles
movie_titles
## “Rush Hour” “Knight and Day” “The Notebook”
## “Shutter Island” “Now you see me” “The Da Vinci Code”
```

> **Note:** Strings are the individual components of a character vector. So, if you put numbers surrounded by quotes, for example: `1`, it will only be considered a character vector. Anything that is surrounded by quotes is treated as a character string.

Now, if Aarya wants to find out how many movies she watched last month she can use the `length()` function to identify how many elements are there in that vector, as shown in the following example:

```
# count the number of elements in the movie_titles
num_movie_titles <- length(movie_titles)

# print the result
cat(“Number of movies watched on Netflix last month:”, num_movie_titles)
## Number of movies watched on Netflix last month: 6
```

## Logical vector

R’s form of Boolean data is a logical vector that stores `TRUE`s and `FALSE`s. A vector indicating whether Aarya watched a movie on a given day is displayed as follows:

```
# create a logical vector watched
watched <- c(TRUE, FALSE, TRUE, FALSE, TRUE, TRUE, FALSE)

# print watched
watched
## TRUE FALSE TRUE FALSE TRUE TRUE FALSE
```

For a vector indicating whether Aarya watched a movie in a given genre:

```
# create a vector genre
genre <- c(“Action”, “Action”, “Romance”, “Thriller”, “Thriller”, “Thriller”)

# check whether a movie belongs to a “Thriller” or not
watched_thriller <- genre == “Thriller”

# print watched_thriller
watched_thriller
## FALSE FALSE FALSE TRUE TRUE TRUE
```

For a vector indicating whether Aarya gave a thumbs up or thumbs down rating to a movie or TV show:

```
# create a vector rating
rating <- c(“Thumbs Up”, “Thumbs Down”, “Thumbs Down”, “Thumbs Up”, “Thumbs Up”, “Thumbs Up”)

# check whether a movie is rated as “Thumbs Up” or not
watched_good <- rating == “Thumbs Up”

# print watched_good
watched_good
## TRUE FALSE FALSE TRUE TRUE TRUE
```

The most common logical operators used in R are:

| Operators | Description |
| --- | --- |
