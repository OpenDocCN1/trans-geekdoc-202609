# Setting Up R Bioinformatics Working Environment

In step 3, we create a README.md file using the useth package use_readme_md() function. This creates a skeleton README file in Markdown format. Here we can add the purpose of the project, as any date-related information such as progress updates, and generally, any useful information for the user of the project, including ourselves!

# There's more...

The useth package is extremely useful for simplifying the common tasks whenever we set up a new project. Initially, we only need the README. md file it can create for us, but it has options for many things, including project licenses, badges, Git credentials, setting up unit tests, setting up packages, and more.

# Using the here package to simplify working with paths

The here package in R is for managing file paths in a consistent and platform-independent manner. One of the main advantages of using this package is that it allows the user to easily navigate and manipulate file paths without worrying about the specific file structure of their operating system. The package also provides a number of functions for creating and managing directories, which can be particularly useful when working with complex file structures.

The here package allows for more reliable and reproducible code. When working with file paths, it is common to use the setwd() function to set the working directory. However, this can lead to issues when trying to run the same code on different machines or platforms. The here package addresses this problem by providing a consistent way to specify file paths, regardless of the operating system.

The here package provides a way to handle project-specific file paths with ease. This is particularly useful when working on large projects where the file structure is complex and you may need to navigate through different directories. With the here package, you can specify the project root directory, and all the other file paths can be relative to this root directory. This makes it easier to move the project to a different location or share with others without having to change the file paths in the project. It also helps to handle the differences in path separators on different operating systems, such as the forward slash (/) on Unix-based systems, and the backslash (\) on Windows. This ensures that the file paths are correctly formatted for the specific operating system being used, increasing the reliability and portability of the code.

# Getting ready

For this recipe, we'll need an active R project in a folder (a bit like the one used in the Setting up R project recipe) in a directory and the here package. If you don't want to use an existing project or make the structure yourself, you can pull an example from the danmaclean/rbioinfcookbook GitHub package. Once that is installed, you can find the example folder copied to it with the following:

```
fs::path_package("extdata", "my_project", package="rbioinfcookbook")
```