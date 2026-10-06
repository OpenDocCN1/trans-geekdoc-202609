# CHAPTER 1. INTRODUCTION

contextual information about a given user such as location, current activity, mood, and so on. Unsupervised learning methods (clustering and association rules) will be covered in chapter 6.

# 1.3 Terminology

This section introduces some basic terminology that will be helpful for the rest of the book.

# 1.3.1 Tables

Since data is the most important ingredient in machine learning, let's start with some related terms. First, data needs to be stored/structured so it can be easily manipulated and processed. Most of the time, datasets will be stored as *tables* or in R terminology, *data frames*. Figure 1.4 shows the mtcars dataset stored in a data frame.

Columns represent *variables* and rows represent *examples* also known as *instances* or *data points*. In this table, there are 5 variables *mpg*, *cyl*, *hp* and the *model* (the first column). In this example, the first column does not have a name, but it is still a variable.

# Table / Data Frame

| | mpg | cyl | disp | hp |
|---|---|---|---|--|
| Mazda RX4 | 21.0 | 6 | 160.0 | 110 |
| Mazda RX4 Wag | 21.0 | 6 | 160.0 | 110 |
| Datsun 710 | 22.8 | 4 | 108.0 | 93 |
| Hornet 4 Drive | 21.4 | 6 | 258.0 | 110 |
| Hornet Sportabout | 18.7 | 8 | 360.0 | 175 |
| Valiant | 18.1 | 6 | 225.0 | 105 |

Figure 1.4: Table/Data frame components.