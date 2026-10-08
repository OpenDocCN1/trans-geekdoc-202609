
## 4.3 History and Objectives of Data Visualization

In his 1893 book, which carried the title *The Visual Display of Quantitative Information*, the author Edward Tufte defines graphical displays and principles for effective graphical display. The book mentioned, “Excellence in statistical graphics consists of complex ideas communicated with clarity, precision and efficiency”.

Visualization is the process of representing data graphically and interacting with these representations. The objective is to gain insight into the data. Some of the processes are outlined in Watson IBM webpage.

## 4.4 Ingredients for Good Graphics

Good graphics are essential to convey the message from your data visually. They will complement the text for your books, reports or manuscripts. However, you need to make sure that while writing for graphics, you need to consider these ingredients:

- You have good data
- Priorities on substance rather than methodology, graphic design, the technology of graphic production or something else
- Do not distort what the data has to say
- Show the presence of many numbers in a small space
- Coherence for large data sets
- Encourage the eye to compare different pieces of data
- Graphics reveal data at several levels of detail, from a broad overview to the fine structure
- Graphics serve a reasonably clear purpose: description, exploration, tabulation and decoration
- Be closely integrated with a data set's statistical and verbal descriptions.

## 4.5 Graphics Packages in R

There are several packages to create graphics in R. They include packages that perform general data visualization or graphical tasks. The others provide specific graphics for certain statistical or data analyses.

## 4.6 ggplot2 Package

The popular general-purpose graphics in R include: which means it is loaded every time we open R:

- **graphics**: a base R package, a user-contributed package by RStudio, so you must install it first time you use it. as a standalone package but also comes with **tidyverse** package.
- **ggplot2**: this is a user-contributed package. It provides the ability to display multivariate relationships, and it improves on the base-R graphics. This package ports the creation of trellis graphs: graphs that display a variable or.
- **lattice**: this is a user-contributed package.

A few examples of more specific graphical packages include:

- **surminer**: The R package provides functions for facilitating survival analysis and visualization. It contains the function `ggsurvival()` for drawing easily and ready-to-publish survival curves with the number at risk table and censoring point.
- **sjPlot**: Collection of plotting and table output functions for data visualization. Using sjPlot, you can make plots for various statistical analyses including simple and cross-tabulated frequencies, histograms, box plots, (generalized) linear models, mixed effects models, principal component analysis and correlation matrices, clusters, scatters, plots, stacked scales, and effects plots of regression models (including interaction terms).

Except for **graphics** package (a base R package), other packages such as **ggplot2** and **lattice** need to be installed into your R library if you want to use them for the first time.

## 4.6 The ggplot2 Package

We will focus on using the **ggplot2** package for this book. The **ggplot2** package is an elegant, and versatile general graphics package in R. It implements the **grammar of graphics** concept. This concept's advantage is that it fastens the process of learning graphics. It also facilitates the process of creating complex graphics.

To work with ggplot2, remember that at least your R codes:

- start with `ggplot()`
- identify which data to plot data = Your Data
- state variables to plot for example `aes(x = Variable on x-axis, y = Variable on y-axis)` for bivariate
- choose type of graph, for example `geom_histogram()` for histogram, and `geom_points()` for scatterplots

The official website for ggplot2 is here https://ggplot2.tidyverse.org/ which is an excellent resource. The website states that ggplot2 is a plotting system for R, based on the grammar of graphics, which tries to take the good parts of base and lattice graphics and none of the bad parts. It takes care of many fiddly details that plotting is a hassle (like drawing legends) and provides a powerful model of graphics that makes it easy to produce complex multi-layered graphics.

## 4.7 Preparation

### 4.7.1 Create a new RStudio project

We recommend that whenever users want to start working on a new data analysis project in RStudio, they should create a new R project.

- Go to File,
- Click New Project.

If you want to create a new R project using an existing folder, choose this folder directory when requested in the existing Directory in the New Project Wizard window. An R project is useful because RStudio will store and save your codes and outputs in the directory (folder).

If you do not want to create a new project, ensure you are inside the correct directory (R call this a working directory). The working directory is a folder where you store your codes and outputs. If you want to locate your working directory, `getwd()` in the Console.

Inside your working directory:

- we recommend you keep your dataset and your codes (R scripts .R, R markdown files .Rmd)
- RStudio will store your outputs

### 4.7.2 Important questions before plotting graphs

It would be best if you asked yourself these:

- Which variables or (are) the type of that variable?
- What is (or are) the type of that variable?
  - Are they factor (categorical) variables or numerical variables?
- Am I going to plot
  - a single variable?
  - two variables together?
  - three variables together?

## 4.8 Read Data

R can read almost (if not all) types of data. The common data formats in data and statistical analysis include:

- comma-separated files (.csv)
- MS Excel file (.xlsx)
- SPSS file (.sav)
- Stata file (.dta)
- SAS file (.sas)

However, it would help if you had user-connected packages to read data from statistical software. For example: haven and rio packages.

Below we show the functions to read SAS, SPSS and Stata files using the haven package.

1. SAS: `read_sas()` reads .sas7dat + .sas7cat files and `read_xpt()` reads SAS transport files (version 5 and version 8). `write_sas()` writes .sasbat files.
2. SPSS: `read_sav()` reads .sav files and `read_port()` reads the older .por files. `write_sav()` writes .sav files.
3. Stata: `read_dta()` reads .dta files (up to version 15), `write_dta()` writes .dta files (versions 8-15).

Sometimes, users may want to analyze data stored in databases. Some examples of common databases are:

1. MySQL
2. SQLite
3. Postgres
4. MariaDB

To read data from databases, you must connect your RStudio IDE with the database. There is an excellent resource to do this on the Databases webpage.

## 4.9 Load the Packages

The ggplot2 package is one of core member of tidyverse (https://www.tidyverse.org/). So, whenever we load the tidyverse package, we automatically load other packages include **dplyr**, **readr** and of course **ggplot2**.

Loading a package will give you access to:

1. help pages of the package
2. functions available in the package
3. sample datasets (not all packages contain this)

We also load the **here** package in the example below. This package is helpful to point R codes to the specific folder of an R project. We will see this in action.
