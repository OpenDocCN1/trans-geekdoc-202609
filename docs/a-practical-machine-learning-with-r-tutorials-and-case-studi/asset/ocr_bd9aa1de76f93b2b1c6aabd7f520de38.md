# Introduction to R and RStudio

Project for this folder with File -> New Project ... Existing Directory.
Creating an R project ensures that R will always open and save R scripts or data files from this folder, respectively. In addition, when working on a project, one can open a recently used R Project with just a few clicks (File -> Recent Projects). This is faster and more convenient than navigating through the directory tree with a file explorer. Another advantage is that all related files are shown in the Files tab in the lower-right window after the project opens.

At the end of this chapter, the Digital Resources section 3.12, a 5-minute video details the procedure to create a project.

# 3.4 R Packages

R provides many functionalities for statistical research, including tools to organize and visualize data, and run machine learning algorithms. If all of these commands were loaded into memory at startup, the R program would require a lot of memory. To avoid this, R comes only with minimal functionality when installed. Then, the user can add R packages, which provide additional functionality. This way, in any given R session, only functionality for the particular data science project is loaded.

To use an R package, two steps are required:

+   The new package has to be downloaded from the CRAN server (Comprehensive R Archive Network) and saved on your computer's hard drive. This only needs to be done once for R installation. To download and install a package on your hard drive, click Tools in the menu bar and choose install ... Then, enter the package name into the entry and have install checked. This way, all packages that your new package depends on are also automatically downloaded and saved.

Although you can also download packages from other repositories, packages provided through CRAN are authoritative because they are peer-reviewed and tested before being available on CRAN. Thus, the chance of downloading a low-quality or malicious package is low.

+   Before working with a package, it must be loaded into the R memory by executing the library() command. The library() command for each package needs to be executed only once for each R session.

> When choosing New Directory, RStudio will create a new directory for the project directory.