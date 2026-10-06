16 Setting Up R Bioinformatics Working Environment

Step 3 is the first of the steps particular to machines with M1 or M2 Silicon processors. The Apple Silicon xcodechain lacks a Fortran compiler and some other libraries at the time of the writing, and we put them in. Here, we download, unpack, and link the compiler using sudo for root permissions.

Step 4 is similar in that we download and unpack OpenMP, and step 5 sets Bash that R will load from the Makevars script on startup so it uses the tools correctly.

# See also

Naturally, hyperlinks will become become obsolete over time and toolchains will update; though the links in the recipe are correct at the time of writing, you can check here for changes in the future: https://mac.r-project.org.

# Using the renv package to create a project-specific set of packages

In the context of software development, an environment refers to a specific set of dependencies and software versions that is used to run a particular application or project. They are useful for avoiding conflicts between different projects that may require different versions of the same package, and ensuring that the application runs consistently across different development, test, and production environments. The renv R package is a dependency management tool for R projects. It allows the user to create a snapshot of the packages and versions used in a project so that others can easily reproduce the same environment on different machines and team members working on the project. It can help avoid version conflicts by managing complex projects with many dependencies. In effect, renv creates a custom library in a subdirectory of the current project - called renv - all packages are installed here. renv also provides a series of shims for common functions such as [install-packages ()] {custom-style="Code"}, which modifies their behavior such that they interact nicely with the new custom library. In this recipe, we'll look at the renv workflow.

# Getting ready

We just need the renv and devtools packages for this recipe.