# 1 Getting Started with Data in R

Unfortunately, this output does not allow us to explore the data very well, but it gives a nice preview. Let's look at some different ways to explore data frames.

# 1.4.3 Exploring data frames

There are many ways to get a feel for the data contained in a data frame such as flights. We present three functions that take as “argument” (their input) a data frame and a fourth method for exploring one column of a data frame:

+   - Using the view() function, which brings up RStudio's built-in data viewer.
- Using the glimpse() function, which is included in the dplyr package.
- Using the 관계() function, which is included in the knitr package.
- Using the $ extraction operator,” which is used to view a single variable.

# View():

Run View(flights) in your console in RStudio, either by typing it or cutting-and-pasting it into the console pane. Explore this data frame in the resulting pop up viewer. Get used to the habit of viewing any data frames you encounter. Note the uppercase v in View(). R is case-sensitive, so you'll get an error message if you run view(flights) instead of View(flights).

# Learning check

(LC1.3) What does any ONE row in the flights dataset refer to?

+   - A. Data on an airline
- B. Data on a flight
- C. Data on an airport
- D. Data on multiple flights

By running View(flights), we can explore the different variables listed in the columns. Observe that there are many different types of variables. Some of the variables distance, day, and arr_delay are what we will call quantitative variables. These variables are numerical in nature. Other variables are categorical.

If you look at the leftmost column of the View(flights) output, you'll see a column of numbers. These are the row numbers of the dataset. Glancing across a row with the same number, say row 5, you can get an idea of what each row represents. This