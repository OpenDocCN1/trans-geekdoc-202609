3. Explicitly tell the installer to use Bioconductor at installation, not initialization:

```
renv::install("bioc::ComplexHeatmap")
```

And that is: declare renv which Bioconductor version you want, and away you go.

# How it works..

Step 1, we use renv::init to initialize the new environment but with the argument to look up Bioconductor repos as the standard CRAN ones, so that the install step finds the right package.

Step 2 replicates step 1, but with an explicit version of Bioconductor, allowing us to specify which version we wish to use. Bioconductor versions are often tied to R versions.

Step 3 tells renv::install() to install from Bioconductor using the bioc:: tag structure. This form can be useful when a project has been initialized without explicitly asking for Bioconductor.

# Using bioconda to install external tools

Using environments for packages in R is extremely useful for managing different versions for different projects. Bioinformatics pipelines have numerous dependencies outside of R, including binary command-line programs and packages from other languages, and it can often be useful to put those under the same set of management. Tools for that do exist.

Anaconda is a distribution of Python and R that is particularly popular for scientific computing, data science, and machine learning. It includes a large number of pre-installed packages and tools, such as NumPy, SciPy, and Jupyter, making it easy to get started with those technologies. Anaconda also includes the conda package manager, which can be used to install additional packages and manage environments. Bioconda is a distribution of bioinformatics software built on top of conda. It includes a wide variety of bioinformatics tools and libraries, making it easy to install and manage those tools in a consistent and reproducible way.

In this recipe, we'll look at how to create and use software in environments.