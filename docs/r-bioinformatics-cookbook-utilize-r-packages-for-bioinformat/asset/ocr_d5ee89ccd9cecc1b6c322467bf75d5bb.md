5. You can also use the renv package manager to install Bioconductor packages by running the following command:

```
renv::install("bioc::<package name>")
```

6. For example, to install the Biobase package, you would run this command:

```
renv::install("bioc::<Biobase")
```

7. You can use renv to install development packages from GitHub like this: 

```
renv::install("<user name>/<repo name>")
```

For example, to install the danmaclean user's rbioinfcookbook package, you would run the following command:

```
renv::install("danmaclean/rbioinfcookbook")
```

Here are some other tips for installation:

+   - You can also install multiple packages at once by separating the package names with a comma, renv will automatically handle installing any required dependencies for the packages you install.
- Under renv, all packages will be installed in the local project directory and not the main central library, meaning you can have multiple versions of the same package, one specific for each project.
- All the sample data you need for this package is in the specially created data package on GitHub: danmaclean/rbioinfcookbook. The data will become available in your project after installing that.

For this chapter, we will need the following packages:

+   - Regular packages:
  - ggplot2
  - knitr
  - palmerpenguins
  - rmarkdown
  - tidyverse
- GitHub:
  - danmaclean/rbioinfcookbook

These should all install easily, and then we are good to go.