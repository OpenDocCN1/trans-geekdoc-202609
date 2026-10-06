
# Functional Programming with purrr and base R

Functional programming is a programming paradigm that emphasizes immutability, pure functions, and declarative programming, treating computation as the evaluation of mathematical functions and avoiding shared state and side effects. It focuses on composing functions and working with immutable data to create robust and predictable programs. In terms of our day-to-day work, this means focusing on using functions to solve problems and avoiding changing data. We also emphasize writing clear, reusable code that is easier to understand and predictable in its behavior. This style helps us as programmers, especially when code becomes complex or must be maintained over a longer period of time.

R has several base functions, including the apply family, as well as external packages that support functional programming, including purrr, and tidyverse. These tools provide functions and operators that facilitate working with data using a functional programming paradigm, allowing for concise and expressive code that focuses on transformations and operations on data. At the center of this way of working is the dataframe object, but not all, indeed not most, R returns a handy dataframe object. Therefore, we will look at converting objects to dataframes and extending them so that they can be a more complex data type, without compromising the streamlined functionality we've come from packages such as dplyr. We will learn how to take advantage of the functional programming available in R by converting base objects to tidy formats, and then we will work in reproducible scalable pipelines with streamlined code. By the end of the chapter, you'll have a good handle on how to build code that is concise and easier to maintain through functional programming.

In this chapter, we will cover the following recipes:

- Making base R objects tidy
- Using nested dataframes for functional programming
- Using the apply family of functions

# Functional Programming with purrr and base R

- Using the map family of functions from purrr
- Working with lists in purrr

# Technical requirements

We will use renv to manage packages in a project-specific way. To use renv to install packages, you will first need to install the renv package. You can do this by running the following commands in your R console:

Install renv:

```
install.packages("renv")
```

Create a new renv environment:

```
renv::init()
```

This will create a new directory called renv in your current project directory.

You can then install packages with the following:

```
renv::install_packages()
```

You can also use the renv package manager to install Bioconductor packages by running the following command:

```
renv::install("bioc::package name")
```

For example, to install the Biobase package, you would run the following:

```
renv::install("bioc::Biobase")
```

You can use renv to install packages from GitHub like this:

```
renv::install("user name/repo name")
```

For example, to install the danmaclean rbioinfcookbook package, you would run the following:

```
renv::install("danmaclean/rbioinfcookbook")
```

You can also install multiple packages simultaneously by separating the package names with a comma. renv will automatically handle any required dependencies for the packages you install.

Under renv, all packages will be installed in the local directory and not the main central library, meaning you can have multiple versions of the same package, specifically for each project.

All the sample data you need for this package is in the specially created data package on GitHub, danmaclean/rbioinfcookbook. The data will become available in your project after installing that.

For this chapter, we'll need the following packages:

- Regular packages:
  - broom
  - dplyr
  - purrr
  - tidyr
- GitHub:
  - danmaclean/rbioinfcookbook

- Bioconductor:
  - Biobase
  - biobroom

In addition to these packages, we will also need some non-R tools, such as conda; all these will be described at the point of use.

# Further information

Not all the recipes in this section happen in R; some are command-line-based setups. I generally assume a bash terminal will be used for these tasks. Most macOS and Linux machines will have these available in a `Terminal` application. Windows users will likely not need these specific steps, although various packages to run a Linux subsystem on Windows exist if you wish to search them out.

In R, it is normal practice to load a library and use functions by name. Although this is great in short interactions, it can cause confusion when many packages are loaded at once and share function names. To clarify which package and function I am using at a given moment, I will occasionally use the `packageName::functionName()` convention.

Sometimes, in the middle of a recipe, I'll interrupt the code to dive some intermediate output or to look at the structure of an object. When that happens, you'll see a code block where each line begins with `##` (double hash symbols). Consider the following command:

```
letters[1:5]
```

This will give us the following output:

```
## a b c d e
```

Note that the output lines are prefixed with ##.

# Making base R objects "tidy"

The tidyverse packages (including dplyr, tidyr, and ggplot2) have a huge influence on data processing and analysis in R, through their application of the "tidy" way of working. In essence, "tidy" means that data is kept in a particular format, which each row holds a single observation of some variable, and columns the variables recorded and contain all values for those variables across all observations. Such a structure means that analytics have predictable input and can be built into complex pipelines with relative ease. Most base R objects are not tidy, and it can often take significant programming to extract the parts that are needed downstream. In this recipe, we will look at some functions to automatically convert some common base R objects into a tidy dataframe.

# Getting ready

We'll need tidyr, broom, and also biobroom from Bioconductor. For data, we'll use the danmacacle/rbioinfocookbook package and the built-in mtcars and iris datasets.

# How to do it...

Making base R objects tidy can be done using the following steps:

1. Tidy an lm object:

2. Tidy a t.test object:

```
t_test_result <- t.test(x = rnorm(20), y = rnorm(20) )
tidy(t_test_result)
```

3. Tidy an ANOVA object:

```
anova_result <- aov(Petal.Length ~ Species, data = iris)
tidy(anova_result)
post_hoc <- TukeyHSD(anova_result)
tidy(post_hoc)
```

4. Tidy a Bioconductor ExpressionSet object:

```
library(biobroom)
library(BioBase)
library(rbioinfocookbook)
```

# Making base R objects "tidy" 323

```
tidy(modencodefly.eset, addPheno=TRUE)
```

This demonstrates a range of options to tidy common R objects.

# How it works...

We start with step 1 by examining some functions to tidy the common lm object, created by the lm() function. The first task is to create the object, so we perform a multiple regression with the mtcars data, and then use the tidy() function to return an object summary of the components of the model. It looks like this:

| term | estimate std.error statistic | p.value |
| <chr> | dbl | dbl | dbl |
| ## 1 (Intercept) | 47.4 | 8.81 | 5.38 0.000000882 |
| ## 2 cyl | -3.14 | 0.398 | -7.88 |
| ## 3 qsec | -0.442 | 0.398 | -1.11 0.276 |

The augment() function returns per-observation data for the model, which we want. It looks like this:

| rownames | mpg cyl qsec .fitted .resid .hat |
| <chr> | dbl | dbl | dbl | dbl | dbl |
| ## 1 Mazda RX4 | 21 | 6 | 16.5 | 21.3 -0.292 0.0665 | ... |
| ## 2 Mazda RX4 Wag | 21 | 6 | 17.0 | 21.0 -0.0447 0.0453 ... |

The glance() function inspects the model and returns summaries in a tidy format, as follows:

| r.square adj.r.squared sigma statistic | p.value df |
| dbl | dbl | dbl | dbl | dbl |
| ## 1 | 0.719 | 3.19 | 40.7 0.000000382 2 |

The function returns an object that is useful when we want to compare models. Consider comparing these data-frame objects with the default objects.

Step 2 shows the process for the t.test object. First, we run a t-test on some random numbers, to get the object, and then we run tidy() on it. The output looks like this:

| estimate estimate estimate2 statistic | p.value |
| dbl | dbl | dbl | dbl | dbl |
| ## 1 | 0.201 | -0.158 | -0.359 | 0.577 0.567 37.8 | |

With step 3, we run ANOVA on the iris data using the aov() function to look at the effect of petal length - in this case, when we use tidy(), we get a model-level summary, perhaps not what we were expecting, so we instead run tidy() on the result of a post hoc test from TukeyHSD().
