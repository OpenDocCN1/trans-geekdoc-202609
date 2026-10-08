
```r
scale_x_continuous(breaks = seq(0,12,1)) + 
theme_bw())
```

## Scale for x is already present.
## Adding another scale for x, which will replace the existing scale.

```r
myplot
```

## geom_smooth() using method = 'loess' and formula = 'y - x'

GDP (in log) and life expectancy:

![](img/2bc6b006fe018e0018b86f206ab98644_86_0.png)

We can now see a nice plot. And next, we want to save the plot (currently on the screen) to these formats:

- pdf format
- png format
- jpg format

If we want to save the plots in a folder named as plots, then

- go to working directory
- click New Folder
- name it as plot

This is when the here() function is handy. You can easily point to the correct folder so R knows where to locate the file.

here() is a function under small packages called here. This function helps you retrieve or save file or files or r objects from and to the correct path (including folder). This works even when we are using different machines.

# 4.13 Saving Plots

![](img/2bc6b006fe018e0018b86f206ab98644_87_0.png)

FIGURE 4.3

In Windows OS, click the New Folder icon.

![](img/2bc6b006fe018e0018b86f206ab98644_87_1.png)

FIGURE 4.4

Rename New Folder as plots.

Many of us recall the uncomfortable experiences when the drive name changes automatically (especially when using a thumb drive) on different computers. By using here() from the here package, we will always get to the correct path or folder.

To save the plots in the directory named plots in different image formats, we can do this:

```r
ggsave(plot = myplot,
  here("plots", "my_pdf_plot.pdf"))
```

```r
# Saving 6.5 x 4.5 in image
## geom_smooth() using method = 'loess' and formula = 'y ~ x'
```

```r
ggsave(plot = myplot,
  here("plots", "my_png_plot.png"))
```

```r
# Saving 6.5 x 4.5 in image
## geom_smooth() using method = 'loess' and formula = 'y - x'
```

```r
ggsave(plot = myplot,
  here("plots", "my_jpg_plot.jpg"))
```

```r
## Saving 6.5 x 4.5 in image
## geom_smooth() using method = 'loess' and formula = 'y - x'
```

ggplot2 is flexible and contains many customizations. For example, we want to set these parameters to our plots:

1. width = 10 cm (or you can use in inches)
2. height = 6 cm (or you can use in inches)
3. dpi = 150. dpi per inch

```r
ggsave(plot = myplot,
  here('plots', 'my_pdf_plot2.pdf'),
  width = 10, height = 6, units = "in",
  dpi = 150, device = "pdf")
```

```r
## geom_smooth() using method = 'loess' and formula = 'y - x
```

```r
ggsave(plot = myplot,
  here('plots', 'my_png_plot2.png'),
  width = 10, height = 6, units = "cm",
  dpi = 150, device = "png")
```

```r
## geom_smooth() using method = 'loess' and formula = 'y - x
```

```r
ggsave(plot = myplot,
  here("plots", "my_jpg_plot2.jpg"),
  width = 10, height = 6, units = "cm",
  dpi = 150, device = "jpg")
```

```r
## geom_smooth() using method = 'loess' and formula = 'y - x
```

# 4.14 Summary

In this chapter, we briefly describe important matters before making plots. Then we teach readers to make plots using the ggplot2 package. This package uses the principle of Grammar for Graphics to ensure the codes are more intuitive to users. Readers learn to generate a single plot for one variable plotting two and three variables simultaneously. ggplot2 is also flexible and contains many customizations to help readers generate fantastic plots and how to save them.

# 5
# Data Wrangling

At the end of the chapter, readers will be able to:

- understand the role of data wrangling
- understand the basic capabilities of dplyr package
- acquire skills to perform common data wrangling using dplyr and forcats packages

Data wrangling removes errors and combines complex data sets to make them more accessible and easier to analyze. Due to the rapid expansion of the amount of data and data sources available today, storing and organizing large quantities of data for analysis is becoming increasingly necessary.

Data wrangling is also known as Data Mung or Data Transformation. It is loosely the process of manually converting or mapping data from one "raw" into another format. The process allows for more convenient consumption of the data. You can find more information at mode analytics webpage

Data wrangling is also referred to as data munging. It is the process of transforming and mapping data from one "raw" into another format to make it more appropriate and valuable for downstream purposes such as analytics. The goal of data wrangling is to ensure quality and valuable data. Data analysts typically spend the majority of their time in the process of data wrangling becoming to the actual analysis of the data. Almost all data require data wrangling

> https://community.modeanalytics.com/sql/tutorial/data-wrangling-with-sql/

![](img/2bc6b006fe018e0018b86f206ab98644_90_0.png)

FIGURE 5.1
Main parts of data wrangling.

before further analysis. There are three main parts to data wrangling (Wickham and Grolelemund, 2017).

# 5.3 Data Wrangling with dplyr Package

### 5.3.1 dplyr package

dplyr is a package grouped inside tidyverse collection of packages. dplyr package is very useful to munge, wrangle, or transform your data. It is a grammar of data manipulation. It provides a consistent set of verbs that help you solve the most common challenges. This tidyverse webpage has more information and examples.

### 5.3.2 Common wrangling processes

The common wrangling processes include:

- reducing the size of dataset by selecting certain variables (columns)
- generating new variable from existing variables
- sorting observation of a variable
- grouping observations on certain criteria
- reducing variables to groups in order to estimate statistics

### 5.3.3 Some dplyr functions

For the procedures listed above, the corresponding dplyr functions are:

- dplyr::select() — to select a number of variables from a dataframe
- dplyr::mutate() — to generate new variable from existing variables
- dplyr::arrange() — to sort observation of a variable
- dplyr::filter() — to group observations that fulfill certain criteria
- dplyr::group_by() and dplyr::summarize() – reduce variable to groups in order to provide statistics

# 5.4 Preparation

### 5.4.1 Create a new project or set the working directory

It is essential to ensure you know where your working directory is. The recommended practice is to create a new project every time you want to start an analysis. To do so, create a new project by File -> New Project. If you do not start with an R new project, you still need to know the location of your working directory.

So, again we emphasize that every time you want to start processing your data, please sure:

- use R project. It is much easier and cleaner to start your work with a new project. Once you have done or need to log off your computer, close the project and reopen the next time you need.
- if you are not using R project, you are inside the correct working directory. Type getwd() to display the active working directory. And to set a new working directory, use the function setwd(). Once you know where your working directory is, you can start reading or importing data into your working directory.

Once the project, you can import your data if necessary.

### 5.4.2 Load the libraries

Remember, there are several packages you can use to read the data into R. R can read almost all (if not all) types of data format. For example, we know that common data formats are:

- SPSS (.sav) format
- Stata (.dta) format
- SAS format
- MS Excel (.xlsx) format
- Comma-separated values .csv format

However, there are other formats, too, such as data in DICOM format. DICOM data includes data from CT scans and MRI images. There are data in shapefile format to store geographical information. Three packages - haven, rio, readr and foreign packages - are very useful to read or import your data into R memory.
