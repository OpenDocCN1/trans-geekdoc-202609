# 3.9 Data Wrangling with the tidyverse Package

argument. This rule of thumb will help us later when we connect multiple commands (using piping) in Section 3.9.4.

# 3.9 Data Wrangling with the tidyverse Package

Like a herd of cattle, they usually do not come as organized as we wish. As a result, we have to perform what is called data wrangling to clean and organize messy data to prepare for analysis.

The tidyverse package¹³ is by far the most used and powerful package in R for data wrangling and other related tasks. The goal of the tidyverse is to streamline the R data analysis workflow.

The tidyverse is a meta package that includes about 30 other packages, including the dplyr, ggplot, tidyr, and the tibble packages, to name a few. These packages are automatically installed when the user installs the tidyverse. Likewise, when the tidyverse is loaded with library(tidyverse), all containing packages are loaded automatically.

The following sections will cover the tidyverse commands required for this book's R analysis. Related videos are listed in the Digital Resources section at the end of this chapter (see Section 3.12).

The reader is encouraged to to study more about the tidyverse packages and commands. A comprehensive book by the author of the tidyverse is available as a paperback book and freely on the Internet.¹⁴

# 3.9.1 Select Data

With the select() command, you can select variables (columns) from a data frame. This is useful if you do not need all variables from a data frame and to create a new data frame with less variables.

The first argument in the select() command is the name of the data frame you are working with. The other arguments (separated by commas) are the variables you like to select.

In the example, we load the tidyverse and the rio packages,¹⁵ import the complete Titanic dataset from the Internet, and use the select() to assign a subset to a new data frame called Titanic_row. The new dataset should only contain the variables (columns)Survived,

¹³See Wickham et al. (2019).

¹⁴See Wickham and Grolemund (2017).

¹⁵Note that we combine two library() commands in one line separated by a semicolon.