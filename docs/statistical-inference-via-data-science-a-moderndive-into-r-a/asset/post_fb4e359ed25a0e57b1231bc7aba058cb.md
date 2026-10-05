
## 8 Getting Started with Data in R

(Wickham et al., 2023) for data wrangling in Chapter 3, the `tidyverse` package (Kim and Ismay, 2024) that accompanies this book, and the infer package (Bray et al., 2024) for “tidy” and transparent statistical inference in Chapters 8, 9, and 10.

A good analogy for R packages is they are like apps you can download onto a mobile phone:

![](img/445742518041017e8f01f11b0c3190d9_42_0.png)

FIGURE 1.4: Analogy of R versus R packages.

So R is like a new mobile phone: while it has a certain amount of features when you use it for the first time, it doesn't have everything. R packages are like the apps you can download onto your phone from Apple's App Store or Android's Google Play.

Let's continue this analogy considering the Instagram app for editing and sharing pictures. Say you have purchased a new phone and you would like to share a photo you have just taken with friends on Instagram. You need to:

- *Install the app*: Since your phone is new and does not include the Instagram app, you need to download the app from either the App Store or Google Play. You do need this once and you're set for the time being. You might need to do this in the future when there is an update to the app.
- *Open the app*: After you've installed Instagram, you need to open it.

Once Instagram is open on your phone, you can then proceed to share your photo with your friends and family. The process is very similar for using an R package. You need to:

- *Install the package*: This is like installing an app on your phone. Most packages are not installed by default when you install R and RStudio. If you want to use a package for the first time, you need to install it first. Once you've installed a package, you likely won't install it again unless you want to update it to a newer version.
- *Load the package*: “Loading” a package is like opening an app on your phone. Packages are not “loaded” by default when you start RStudio on

## 1.3 What are R packages?

your computer; you need to “load” each package you want to use every time you start RStudio.

Let’s perform these two steps for the `ggplot2` package for data visualization.

### 1.3.1 Package installation

> Note about RStudio Server or RStudio Cloud: If your instructor has provided you with a link and access to RStudio Server or RStudio Cloud, you might not need to install packages, as they might be preinstalled for you by your instructor. Being said, it is still a good idea to know this process for later on when you are not using RStudio Server or Cloud, but rather RStudio Desktop on your computer.

There are two ways to install an R package: Let’s install the ggplot2 package the easy way first as shown in Figure 1.5. In the panes of RStudio:

- a) Click on the “Packages” tab.
- b) Click on “Install” next to Update.
- c) Click the type of the package under “Packages (separate multiple with space or comma):” In this case, use ggplot2.
- d) Click “Install.”

![](img/445742518041017e8f01f11b0c3190d9_43_0.png)

FIGURE 1.5: Installing packages in R the easy way.

An alternative but slightly convenient way to install a package is by typing `packages("ggplot2")` in the console pane of RStudio and pressing Return/Enter on your keyboard. Note you must include the quotation marks around the name of the package.

Much like an app on your phone, you only have to install a package once. However, if you want to update a previously installed package to a newer version, you need to re-install it by repeating the earlier steps.

## Learning check

(LC1.1) Repeat the earlier installation steps, but for the `dplyr`, `nycflights23` and `knitr` packages. This will install the earlier mentioned `dplyr` package for data wrangling, `nycflights23` package containing all domestic flights leaving an NYC airport in 2023, and the `knitr` package for generating easy-to-read tables in R. We’ll use these packages in the next section.

### 1.3.2 Package loading

Recall after you've installed a package, you need to “load it.” In other words, you need to “open it.” We do this using the `library()` command.

For example, to load the `ggplot2` package, run the following code in the console pane. What do we mean by “run the following code?” Either type or copy-and-paste the following code into the console pane and hit the Enter key.

```
library(ggplot2)
```

If after running the earlier code

`Error in library(ggplot2) : there is no package called ‘ggplot2’`

- it means you didn't successfully install it. This is an example of an “error message” we discussed in Subsection 1.2.2. If you get this error message, go back to Subsection 1.3.1 on R package installation and make sure to install the `ggplot2` package before proceeding.

## 1.4 Explore first datasets

## Learning check

(LC1.2) Repeat the earlier installation steps, but for the `dplyr`, `nycflights23` and `knitr` packages. This will install the earlier mentioned `dplyr` package for data wrangling, `nycflights23` package containing all domestic flights leaving an NYC airport in 2023, and the `knitr` package for generating easy-to-read tables in R. We’ll use these packages in the next section.

### 1.3.3 Package use

One very common mistake R users make when using particular packages is they forget to “load” them first by using `library()` command. Remember: you have to “load” each package you want to use every time you start RStudio. If you don’t “load” a package, but attempt to use one of its features, you’ll see an error message similar to

`Error: could not find function`

This is a different error message than the one you saw. R is telling you that you are trying to use a function in a package that has not yet “loaded.” Most new users find this annoying, but after some time it will become second nature.

### 1.4.1 nycflights23 package

```
library(nycflights23)
library(dplyr)
library(knitr)
```

At the beginning of all subsequent chapters in this book, we'll always have a list of packages that you should have installed.

- flights: Information on all flights.
- airlines: A table matching airline names and their two-letter Air Transport Association (IATA) airline codes (also known as carrier codes) for 14 airline companies. For example, "DL" is the two-letter code for Delta.
- planes: Information about each of the 4,840 physical aircraft used.
- weather: Hourly meteorological data for each of the three NYC airports. This data frame 26,204 rows, roughly corresponding to the produced hour measurements one can observe at three locations over the course of a year.
- airports: Names, codes, and locations of the 251 domestic destinations.

The nycflights23 package is an updated version of the classic nycfflights13 R package⁴ nycfflights23 was authored by ModernDive co-author Chester Ismay is using the anyflights R package⁵ developed by Simon Couch⁶. Simon granted permission to the ModernDive team to create nycfflights23 and submit the package to CRAN.

>⁴https://nycfflights23.tidiverse.org/
⁵https://anyflights.netlify.app/
⁶https://www.simonpouch.com/
