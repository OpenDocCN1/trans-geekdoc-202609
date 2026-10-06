# 6.7 Project: Tuning a k-Nearest Neighbors Model

The augment() command writes the predictions into a column named .pred and augments the testing data frame with that column. The resulting data is saved as DataTestWithBestModel.

Since the metrics() command needs to compare these predictions with the true values to calculate the metrics, the name of the outcome variable also needs to be provided by substituting <COME VARIABLE> accordingly.

# 6.7 Project: Tuning a k-Nearest Neighbors Model

# Interactive Section

In this section, you will find content with R code to execute, change, and rerun in RStudio.

The best way to read and to work with this section is to open with RStudio. Then you can interactively with R code exercises and R projects within a web browser. This way you can apply what you have learned so far and extend your knowledge. You can also choose to continue reading in the book or online, but you will not benefit from the interactive learning experience.

To work with this section in RStudio in an interactive environment, follow these steps:

+   1. Ensure that both the learner and the shiny package are installed. If not, install them from RStudio's main menu (Tools -> Install Packages..).

+   2. Download the rds file for the interactive section and save it in your project folder. You will find the link for the download below.

+   3. Open the downloaded file in RStudio and click the Run Document button, in the editing window's top-middle area.

For detailed help running the exercises including videos for Windows and Mac users refer to: https://blog.lang-analytics.com/2024/01/interactsections.html

Do not skip this interactive section because besides providing applications of already covered concepts, it will also extend what you have learned so far.

Below is the link to download the interactive section:

https://ai.lang-analytics.com/exc/?file=06-TrainTestExerc100.Rmd

In Section 4.9, you will use a k-Nearest-Neighbor model to predict the color of a wine.

In this section, you will work on the same problem with an interactive project, but you will tune the hyper-parameter k with Cross-Validation to find an optimal k (good approximation of the training data without overfitting). You