
# Download a free PDF copy of this book

Thanks for purchasing this book!

Do you like to read on the go but are unable to carry your print books everywhere?

Is your eBook purchase not compatible with the device of your choice?

Don't worry, now with every Packt book you get a DRM-free PDF version of that book at no cost.

Read anywhere, any place, on any device. Search, copy, and paste code from your favorite technical books
directly into your application.

The perks don't stop there, you can get exclusive access to discounts, newsletters, and great free content
in your inbox daily

Follow these simple steps to get the benefits:

- 1. Scan the QR code or visit the link below

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_21_0.png)

https://packt.link/free-ebook/9781837634279

- 2. Submit your proof of purchase

- 3. That's it! We'll send your free PDF and other benefits to your email directly

## Setting Up Your R Bioinformatics Working Environment

R is a powerful and versatile programming language that is widely used in bioinformatics, data science,
and statistics. One of the key benefits of R is its rich ecosystem of packages and libraries, which allows
users to easily perform complex tasks and analyze large datasets – in particular the tidyverse packages, which
provide a lot of data science functionality, and the Bioconductor packages, which are state of the art
in biological analysis, have provided great power. To get the best out of these make sure that you are working in
the most productive ways, it is important to use the best tools and employ a clear and organized project

structure to ensure that your work is readable, maintainable, and reproducible.

One of the most important aspects of a good project structure is separating the parts into different files
and directories based on their purpose. For example, it is a good practice to keep your data in a separate
directory with your code and to separate into different files for different tasks, such as data cleaning,
analysis, and visualization. A well-set machine and clear project structure that keeps code readable,
maintainable, and reproducible benefit the original developer of the code, others who work on the code later,
and any future users of the code and the scientific results. It is also crucial when we come to writing up
results for publication and being organized this way can save a lot of headaches and stress and even repeating of work.

Computing environments, such as R and Anaconda, are also an important part of a good project structure.
these packages allow you to create a virtual environment that is separate from your systemwide R installation, which
makes it easy to manage different versions of programs, packages, and dependencies. This is particularly
useful when working on multiple projects with other collaborators who may be using different versions of packages.
It can also help recreate a project easily when you haven't worked on it for a while. Using virtual
environments ensures all collaborators have the same software environment.

## Setting Up Your Bioinformatics Working Environment

Biconda and Homebrew are package management systems that make it easy to install and manage bioinformatics
software on your computer. Biconda is focused on bioinformatics software and packages, while Homebrew is a
general-purpose package management system for macOS and Linux. Both are particularly useful for bioinformatics
research as they allow you to easily install and manage the large number of specialized bioinformatics
programs and packages needed for various analyses and pipelines.

In this chapter, you'll learn some essential tips and tricks for setting up your computer so that you can work in
the most productive way.

In this chapter, we will cover the following recipes:

- Setting up an R project in a directory
- Using the here package to simplify working with paths
- Using the devtools package to work with the latest non-CRAN packages
- Setting up your machine for the compilation of source packages
- Using the renv package to create a project-specific set of packages
- Installing and managing different versions of Bioconductor packages in environments
- Using bioconda to install external tools

## Technical requirements

We will use renv to manage packages in a project-specific way. To use renv to install packages, you will
first need to install the renv package. No specific R version seems to be needed for renv, though it's a good idea to use
the latest version of R. renv will automatically record the version of R that you used when starting with it on a
project. Note also that you shouldn't use renv directly in the home directory, only in project-directories. You can
see more information on this working structure in the Setting up an R project directory and Using the renv package to create a project-specific set of recipes.

You can do this by running the following command in your R console:

- 1. Install renv:

```
install.packages("renv")
```

- 2. Next, you will need to create a new renv environment for your project by running the following command:

```
renv::init()
```

This will create a new directory called ".renv" in your current project directory.

- 3. You can then install packages with the following:

```
install.packages("<package name>")
```

- 4. You can also use the renv package manager to install Bioconductor packages by running the following command:

```
renv::install("bioc::<package name>")
```

- 5. For example, to install the BioBase package, you would run the following:

```
renv::install("bioc::BioBase")
```

- 6. You can use renv to install development packages from GitHub like this:

```
renv::install("<user name>/<repo name>")
```

- 7. For example, to install the user danmaclean's rbioinfcookbook package, you would run the following:

```
renv::install("danmaclean/rbioinfcookbook")
```

You can also install multiple packages at once by separating the package names with a comma. renv will automatically handle installing any required dependencies for the packages you install. Under renv, all packages will be installed into the local project directory and not the main central library, meaning you can have multiple versions of the same package – a specific one for each project.

- 8. All the sample data you need for this package is in the specially created data package on GitHub: danmaclean/rbioinfcookbook. The data will become available in your project after installing that.

For this chapter, we'll need the following packages:

- devtools
- here
- renv
- reticulate
- usethis
- GitHub:
- danmaclean/rbioinfcookbook

## Setting Up Your R Bioinformatics Working Environment

In addition to these packages, we will also need non-R tools such as conda; these will be described

## Further information

Not all the recipes in this section have R; some are command-line-based. Most macOS and Linux machines will have these available in Terminal application. Windows users will likely not need these specific steps, though various packages running a Linux subsystem on Windows exist if you wish to search them.

In R, it is a normal practice to load a library and use functions by name. Although this is short in interactive sessions, it can cause confusion when many packages are loaded at once. To clarify which package and function I am using at a given moment, I will occasionally use the packageName : functionName ().

Sometimes, in the middle of a recipe, I'll interrupt the code to dive into some intermediate output or to look at the structure of an object. When happens, you'll see a code block where each line bins with ## (double hash symbols). Consider the following command:

```
letters[1:5]
```

This will give you the following output:

```
## a b c d e
```

Note that the output lines are prefixed with ##.

## Setting an R project in a directory

R is a command-line tool, and historically, users would work at the command line in order to make use of the language, but as the complexity of a user's tasks increases beyond a few simple commands, then that interface becomes limiting, and more powerful and flexible tools are needed.

RStudio is an integrated development environment (IDE) for the R programming language. provides a user-friendly interface for writing and running R code, as well as tools for data visualization and data manipulation. RStudio includes a variety of tools, such as code completion, syntax highlighting, and error checking, which can help users to write and debug their code more efficiently. RStudio provides a powerful and flexible environment that can be customized to suit the needs of individual users. It provides many options for customizing the layout of the interface, including the ability to integrate with GitHub, render help and vignettes, and visually inspect R objects.

An R project is a collection of files and directories that are organized together for a specific project or analysis. When you create an R project, RStudio creates a new directory with a file called .Rproj
