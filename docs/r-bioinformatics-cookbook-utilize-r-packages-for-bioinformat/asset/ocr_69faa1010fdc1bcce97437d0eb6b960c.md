# Functional Programming with purrr and base R

+   - Using the map family of functions from purrr
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