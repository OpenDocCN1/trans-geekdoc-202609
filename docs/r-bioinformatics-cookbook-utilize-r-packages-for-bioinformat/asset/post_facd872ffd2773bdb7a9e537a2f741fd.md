
# Setting Up Your R Bioinformatics Working Environment

5. Load in a set of reused custom functions within that file:

```
source(here::here("R","functions.R"))
```

And that is how we use the package to make all references to files relative to a project directory.

# How it works...

This slightly repetitive recipe serves to highlight the fact that there are really only two functions used in the here workflow and the pattern of use is quite straightforward. In the first part of the pattern, the user uses the i_am() function to declare where the script is - this helps work out the project structure. Then, here() function itself is used every time we want to use a path. We simply think think of all our paths relative to the project root - the my_project folder. Note that all these steps are performed as edits to the recipe files and not typed into the console.

In step 1, we get our script to declare its position in the project tree, allowing here to work out the structure.

In step 2, we create a path for the input file elsewhere in the project file structure, independent of the syntax of the operating system, and the value of getwd() using the here() function. Each element passed to here() is just a step on the path to the file.

In step 3, we are repeating the initialization we did in step 1 for this different file - here, an R Markdown document - so the new code must go in the first chunk.

And in step 4, we use the here() function to build a path to our functions.R file and load its contents for the current document.

# There’s more…

You can use the here() function without arguments to tell it where it thinks the project root is currently. You can also use the dr_here() to tell you why that it is the project root.

# Using the devtools package to work with the latest-CRAN packages

A R package contains the plain source code for an R package, which can be installed and built on the user's machine. A binary R package, on the other hand, is a pre-built version of an R package that contains pre-compiled code and can be installed and used directly without the need to build the package from the source, and without needing all the tools and programs needed for the compilation progress. When we install packages from CRAN using install.packages(), we are typically getting a pre-compiled binary version of the code.

Using the devtools package to work with the latest non-CRAN packages 11

The devtools R package is a collection of tools that make it easier to develop R packages. It includes functions for creating and installing source packages, building and reloading documentation, and more. Additionally, it provides functionality to check packages, build documentation, manage package dependencies, and test package functionality. It allows users to easily share and collaborate on R package development, making it a popular choice among R Developers. We will briefly discuss its for installing packages from sources that have not been uploaded to CRAN. Often, this will be newer versions of packages that are on CRAN but the developer has added new features or fixes that have not yet made it into a suitable form for the main library.

# Getting ready

For this recipe, we'll need the devtools package and we will use some particular branches and pull requests (PRs) of the rbioinfcookbook package. Remember to pull the default version back at the end after you run through the recipe for the full functionality of package.

# How to do it...

Working with devtools to install packages follows a basic pattern; we give a repo/username argument to manage this like this:

- 1. Install a source package that lives on GitHub:
```
devtools::install_github("danmaclean/rbioinfcookbook")
```

- 2. Install the example_devtools_branch:
```
library(rbioinfcookbook)
# The next line won't work...
rbioinfcookbook::function_from_branch()

# Now it will
detach("package:rbioinfcookbook", unload=TRUE)
devtools::install_github("danmaclean/rbioinfcookbook@example_devtools_branch")

rbioinfcookbook::function_from_branch()
```

- 3. Install a specific pull request:
```
# The next line won't work...
rbioinfcookbook::function_from_PR()

# Now it will
detach("package:rbioinfcookbook", unload=TRUE)
devtools::install_github("danmaclean/rbioinfcookbook#1")
rbioinfcookbook::function_from_PR()
```

- 4. Clean up using the package from GitHub, R memory and then from disk:

```
detach(package:rbioinfbook", unload=TRUE)
remove.packages("rbioinfbook")
```

- 5. Restart and put back the default version of the package:

```
install.packages("danmaclean/rbioinfbook")
```

This process works that us installing and replacing the rbioinfbook package to find functions that only exist in particular branches of the GitHub repository.

# How it works...

In step 1, we simply install a source package that resides on GitHub, with the install_github() function. The syntax of the argument function is username/repo. By default, the function pulls and installs the latest main branch update. If you already initialized renv for working on a project, devtools will install it into the renv library, though that isn't mandatory.

In step 2, we go a step further and install from a specific branch – example_devtools_branch – which adds a function that is not in the main branch, function_from_branch() (note for cleanliness in memory, we use the detach() function to clear out the previously loaded version from each time). We test the function before installation and after to verify that we have the new code. At some points in installations, R databases of packages can lose track. Restarting usually fixes this, so if it doesn't appear to work at this stage, first using detach() again, and if it doesn't work, try restarting R.

In step 3, we specify a pull request from which to install. This likely represents very experimental code that the package maintainers haven't incorporated into their package, but when you need the bleeding edge case, this is the way to get it. Here, #1 indicates the number of the specific pull request to get, which provides the function_from_PR function. Again, we test it before and after installation.

In step 4, we clean up. The installation and uninstallation of packages can confuse R. If you've used library() at any point, the code will be in memory and needs to be removed – that's what the detach function does. Then, we actually remove the package from the disk.

In step 5, we bring the package back to parity and install the full version, which is good for all the recipes.

# There's more...

This recipe concentrates on installing packages from GitHub, but there are related functions for other version control:

- install_gitlab() from GitHub
- install_bitbucket() from Bitbucket
- install_url() from an arbitrary URL
- install_git() and install_svn() from an arbitrary Git or SVN repository
- install_local() from a local file on disk
- install_version() from a specific version on CRAN

# Setting up your machine for the compilation of source packages

Compilation of source code is the process of converting human-readable code into machine-readable code that can be executed by a computer. It varies on different chips and operating systems because the machine code that is produced must be specific to the architecture of the target platform. A compiler is a program that performs the compilation process.

Some R packages are written in C or Fortran which are low-level programming languages that can execute faster than R in certain situations. Additionally, C code can be easily integrated into R packages, allowing for faster computations and improved performance. To take advantage of the better performance, some R packages from the source will need to have their foreign language parts compiled. In this brief recipe, we'll look at tricks and shims for installing code that must be compiled on various platforms.

# Getting ready

We don't need anything specific prior to this recipe, as we assume a machine that is not already prepped for compilation.

# How to do it...

The steps here sometimes refer to different operating systems; not everything is applicable to all computers. I've marked the operating system that each is designed to use:

- Set it up for Windows, and install the correct version of Rtools.exe. We can get it from https://cran.r-project.org/bin/windows/Rtools/, (see Figure 1.5 and Figure 1.6).
