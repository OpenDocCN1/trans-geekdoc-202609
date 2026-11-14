

![](img/9c4b3d77873bec9e7da149a75c568d36_398_0.png)

Figure 11.4: Search results for the word TRUE

But the true power of R is in its packages. Packages contain R-scripts created for a specific purpose. For instance, there are packages that help you read in data from multiple sources and run machine learning algorithms. It's not that you can't do this natively with base R, but someone has already thought of many of the issues you'd run into and created a package to make your life easier. Over the years, professionals, grad students, and R-community lovers have worked together to create packages in R that do much of the heavy lifting for you.

As you'll see, we'll be using packages to manipulate data and run algorithms.

> TIP
> 
> For a quick reference of many of the built-in, base-R functions, check out the R reference card at https://cran.r-project.org/doc/contrib/Short-refcard.pdf.

One package that I love is called tidyverse, and it has everything we need when it comes to data cleaning. Before moving forward, we're just going to install it now—and you should make this your standard operating procedure whenever you start a new R project. To gain access to this package, hit the command window with the following:

```
> install.packages('tidyverse')
```

When you type this command, R will begin downloading the entire package from its internal content delivery network (called Comprehensive R Archive Network, or CRAN for short). You'll notice your console begin installing everything like crazy. Just take a step back and let it do its thing.

> **Tidyverse**
> 
> Tidyverse describes itself as “an opinionated collection of R packages designed for data science. All packages share an underlying design philosophy, grammar, and data structures.” You can learn more at www.tidyverse.org.

With our package now installed, we can start using it. You'll see how soon.

Now that we've covered the basics and setup, let's understand the workflow we'll be doing from here on out.

- 1. Bring data into R.
- 2. Do data-sciency things with data.
- 3. Present the results.

## Doing Some Actual Data Science

Let's get started by bringing in some CSV data and then doing some K-means clustering.

## Reading Data into R

> The CSV file used in this section, WineKMC.csv, is available for download at the book's website, www.wiley.com/go/datasmart2e.

To bring the WineKMC data into R, we'll want to deposit it into the working directory. The working directory is the folder in which you can put data so that the R console can find it and read it in. You can see the working directory in the lower-right pane of the IDE on the Files tab. The easiest way to get your files into the working directory is to hit the Upload button in the submenu of the Files tab. This will pop open the Upload Files box. Under Choose File, select WineKMC.csv and click OK. This will bring the file into your working directory (see Figure 11.5).

![](img/9c4b3d77873bec9e7da149a75c568d36_400_0.png)

**Figure 11.5:** The Upload Files box

Now that `WineKMC.csv` is in the working directory, we'll need to read it into R and assign it to a dataframe. In your Console window, type the following command:

```
> winedata <- read.csv('WineKMC.csv')
```

This creates a new variable called `winedata`. You can type `winedata` directly into the console to see the data print directly into the console. This isn't actually very useful because it's just way too much data, but it's the way we used to do it before RStudio.

These days, we can view the dataframe in a more interactive way, which will greatly help in our analysis. For this better “view,” you can either click the `winedata` variable in the Environment tab in the right-hand pane or type `View(winedata)` into the console. Note that simply clicking the variable executes `View(winedata)` in the console.

This brings up a preview pane that's similar to an Excel table in Figure 11.6.

![](img/9c4b3d77873bec9e7da149a75c568d36_401_0.png)

Figure 11.6: Viewing the winedata dataframe in R

Feel free to click around in the dataframe view. You can filter and sort the view without affecting the underlying data. Perhaps you can see how this view is very useful for debugging and exploratory analysis. Click the X button on the tab itself to close the view.

### Spherical K-Means on Wine Data in Just a Few Lines

In this section, you'll cluster based on cosine similarity, also called _spherical K-means_. First, we'll need to bring in the `skmeans` package into R.

```
> install.packages('skmeans')
```

Now that it's been installed, we'll need to tell R we want to use it. We can do this with the `library` command. Notice that this command does not include quotes around the package as compared to when it's installed. This is always the case when you use the `library` command.

```
> library(skmeans)
```

Once the package is loaded, we'll want to isolate the purchase vectors. Now we could use base R to work with the dataframe. But when we installed tidyverse previously, we got access to an incredible R library called dplyr. It's actually similar to M code, the backbone language of Power Query in Excel. Just as you can manipulate data in a series of steps in Power Query, dplyr lets you do the same activities. (Python has its own version of this too in a library called pandas.) To access dplyr, first you'll need to tell R we want to use it via the `library` command:

```
> library(dplyr)
```

Now go back and take a look at Figure 11.6. The algorithms we're about to use won't like all of those NAs, so we'll need to replace them with 0s. Next, we'll need to isolate the customer data that starts in column 8 and stretches out about another 100 columns. Finally, we'll have to transpose the data for skmeans to use it. In Excel, this is a job for Power Query. In R, it's a job for dplyr.

```
> winedata.transposed <-
winedata %>%
select(8:107) %>%
replace(is.na(.), 0) %>%
t()
```

> **TIP**
> 
> Press Shift+Enter to move the next line in the R command window without executing the command.

This code snippet contains some important elements of dplyr. So let's break it down.

The first line is merely the assignment. Whatever we do thereafter gets assigned to the variable winedata.transposed. In R, you're allowed to use periods in your variable names.

The next several lines are actually similar to Power Query. In the second line, we start with winedata. You can think of this as the first “source” step in Power Query. We’re starting with the initial state of our dataframe. Right after that, you see one of the most important features of dplyr—the pipe operator, %>%.

There are some special properties to this character set that go beyond the scope of this book. But you can simply think of it as a way to fluidly chain together multiple data wrangling steps, much like the applied steps in Power Query. Take note that every “step” effectively ends with these characters until the final step.

Let's also take note: this is *not* base R—it's dplyr. The dplyr library uses semantic commands to work with tables, like select(); in fact, this is (again—not to belabor the point) much like in Power Query.

The third line, select(), is selecting columns 8 through 107.

Here's the thing, NAs aren't always allowed when working with statistical packages. Though each package is different, it's still a good idea to handle them anyway. So the next command, replace, replaces all NAs in the dataset with 0s. The period in the is.na() means replace *everything*—we could also supply a specific column in those parentheses instead. Finally, t() simply transposes the data.

> **NOTE**
> 
> Check out the dplyr cheat sheet at www.rstudio.com/wp-content/uploads/2015/02/data-wrangling-cheatsheet.pdf. I use it all the time.

Next we can call skmeans on the dataset, specifying 5 means and the use of a genetic algorithm (much like the algorithm you used in Excel). You'll assign the results back to an object called winedata.clusters.

```
> winedata.clusters <- skmeans(winedata.transposed, 5, method="genetic")
```

Typing the object back into the console, you can get a summary of its contents (your results may vary because of the optimization algorithm).

