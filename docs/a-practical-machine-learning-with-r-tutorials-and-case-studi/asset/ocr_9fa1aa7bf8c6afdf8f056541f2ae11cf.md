# 3.3 RStudio the Integrated Development Environment (IDE) for R

to print the value of A to the R Console window. This approach is better than typing directly into the R Console window because the code can be saved as an R script file (file extension .r) and is, therefore, reproducible.

The lower-right window contains the Files tab: This tab displays all files available in a project folder (see Figure 3.1). In the same window, you can choose different tabs. For example, you can display R output (tab Plots) or a list of installed packages (tab Packages).

The upper-right window contains the Environment tab: This tab displays the content of R objects, initially empty, but when a user assigns a content like a R object, the object and its content are displayed in the Environment tab in the upper-right window. For example, after the user assigned A=1 to the R object, the entry A: 3 is shown in the Environment tab (see Figure 3.1).

When an R object is more complex, such as a data frame (more about data frames in Section 3.5.2), the user can click on it, and RStudio will open it in a separate window.

# 3.3.2 RStudio Configuration

Using the RStudio menu (Tools -> Global Options), you can configure RStudio in many ways. We recommend being conservative with changing options when you are not sure about the consequences.

However, it is strongly recommended to change the following settings:

+   - Use Tools -> Global Options, and then disable Restore .RData into startup.
- Set the Own workspace to .RData on exit. Never.

Saving the R workspace (content of all R objects) when closing an R session is not necessary when working with R scripts as R objects can be re-created with a few clicks as long as the R script has been saved. Keeping R sessions between workspaces can lead to confusion and errors. Note that the Global Options as described above need only to be done once for any RStudio installation.

Another good practice is to assign a specific hard drive to carry each data science project. You decide what you consider a project. Afterward, all files will always be saved into the specified R Project Folder.

When you work with that project, RStudio will save and load all files from/into this project folder by default.

You mark a folder as an R Project Folder by creating an R Project using the RStudio menu. Assuming the folder already exists, you can create an R