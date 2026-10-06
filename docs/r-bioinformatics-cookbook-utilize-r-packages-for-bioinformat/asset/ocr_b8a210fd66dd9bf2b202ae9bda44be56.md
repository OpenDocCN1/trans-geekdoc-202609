# How it works...

Step 1 explicitly creates a data frame; we do it way so that we can easily understand its structure.

In step 2, we use the method in its simplest form: the group_by () function is used to group the rows of a data frame based on the chromosome_id, and we use summarise () to return a summary data frame. Step 3 is similar but shows how grouping columns can be used to create more granular groups and how more than one summary function can be applied.

Step 4 is complex; the new data frame is a nested data frame, and the samples list column contains a data frame of expression in each cell. When using group_by () functions on a nested data frame, you first need to access the nested data using the tidyr::unnest () function, then group as usual. Note that when using tidyr::unnest (), the new data frame will have multiple rows for each gene, for each sample, it's important to group the data frame by the columns of interest.

# Using datapasta to create R objects from cut-and-paste data

Being able to paste data into source code documents is useful for all sorts of reasons, not least it allows for a reproducible example, also known as a reprodex—a minimal, self-contained example that demonstrates a problem or a concept. By including data in the source code, others can run the code and see the results for themselves, making it easier to understand and replicate the results.

The R datapasta package makes it easy to paste data into R source code documents. It provides a set of functions for converting data to R definitions and is extremely useful when creating static objects in code examples, tests, or when sharing. In this recipe, you will learn how to use datapasta to bring external data into your source code documents by typing them in longterm.

# Getting ready

We will use the datapasta package, though is non-standard. Use this command:

```
renv::install("datapasta", repos = c(mm = "https://ilesmcbain.universe.dev",), getOption("repos"))
```

This should install the package using renv and make us ready to go. Remember to install renv the usual way if you don't already have it.