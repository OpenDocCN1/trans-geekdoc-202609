
In scenarios b)-c), we cannot estimate $\pi_0$ and $\pi_1$ from the learning sample; however, in scenario b) we might have estimates of $\pi_0$ and $\pi_1$, perhaps from historical data. If the data have been artificially balanced, then it's possible to use good estimates of $\pi_0$ and $\pi_1$ to “correct” (or adjust) the output predicted probabilities. With CART and GUIDE, it's possible to provide the true priors and let the tree algorithm handle the adjustment (we saw how this is handled in CART in Section 2.2.4 and provided an example with **rpart** using the letter image recognition example in Section 2.9.5). What if no priors argument is available in your software? Fortunately, you can apply a simple adjustment to the output predicted probabilities, as discussed in Matloff [2017, pp. 197-198]. A simple function to adjust the predicted probabilities is given below. Here, **p** is a vector of predicted probabilities for the positive class (i.e., $\widehat{\Pr}(Y=1|x)$), **observed.ratio** is the ratio of the observed class frequencies (i.e., $N_0/N_1$), and **true.ratio** is the ratio of the true class priors (i.e., $\pi_0/\pi_1$).

```r
prob.adjust <- function(p, observed.ratio, true.ratio) {
  f.ratio <- (1 / p - 1) * (1 / observed.ratio)
  1 / (1 + true.ratio * f.ratio)
}
```

Let's try this out on an RF fit to a down-sampled version of the training data. Below I artificially balance the classes by removing rows corresponding to the dominant class (i.e., y = 0):

```r
trn.1 <- trn[trn$y == 1, ]
trn.0 <- trn[trn$y == 0, ]
trn.down <- rbind(trn.0[seq_len(nrow(trn.1)), ], trn.1)
table(trn.down$y)
#>
#>   0   1
#> 5018 5018
```

Next, I'll fit another (default) RF, but this time to the down-sampled training set. I then apply the adjustment formula to the predicted probabilities for the positive class in the test set:

```r
set.seed(1146) # for reproducibility
rfo2 <- ranger(y ~ . - prob, data = trn.down, probability = TRUE)

# Predicted probabilities for the positive class: P(Y=1|x)
prob2 <- predict(rfo2, data = tst)$predictions[, 2]
mean((prob2 - tst$y) ^ 2) # Brier score
#> [1] 0.0756

mean((prob2 - tst$prob) ^ 2) # MSE
#> [1] 0.0538

prob3 <- prob.adjust(prob2, observed.ratio = 1,
true.ratio = (1 - pi1) / pi1)
mean((prob3 - tst$y) ^ 2) # Brier score
#> [1] 0.0285
mean((prob3 - tst$prob) ^ 2) # MSE between predicted and true probs
#> [1] 0.00609
```

Figure 7.26 shows the predicted vs. true probabilities across three different cases: 1) predicted probabilities (prob1) from an RF applied to the original training data (left display), 2) predicted probabilities (prob2) from an RF applied to a down-sampled version of the original training data, but adjusted using the original class frequencies (middle display), and 3) predicted probabilities (prob2) from an RF applied to a down-sampled version of the original training data with no adjustment (right display).

![](img/2c227bfb3620dc3d159fa5e6598afa30_315_0.png)

FIGURE 7.26: True vs. predicted probabilities for the test set from an RF fit to the original and down sampled (i.e., artificially balanced) training sets. Left: probabilities from the original RF. Middle: Probabilities from the down sampled RF with post-hoc adjustment. Right: Probabilities from the down sampled RF. The calibration curve is shown in orange, with the blue curve representing perfect calibration.

Compared to the predicted probabilities from an RF fit to the original (i.e., unbalanced) learning sample, down sampling appears to have produced biased and poorly calibrated probabilities, although, the adjustment formula seems to provide some relief but requires access to the true class priors (or good estimates thereof).

Basically, it is ill-advised to choose a model based on a metric that forces a classification based on an arbitrary threshold. Instead, choose a model using a proper scoring rule (e.g., or the Brier score) that makes use of the full range of predicted probabilities, and is optimized when the true probabilities are recovered. Down sampling, adjusted or not, seems to highly under or over estimate the true class probabilities.

## 7.9.5 Example: partial dependence with Spark MLlib

In this section, I'll look at a well-known bank marketing data set available from the UC Irvine Machine Learning Repository [Moro et al., 2014]. The data concern the direct marketing campaigns of a Portuguese banking institution, which were based on phone calls. Often, more than one contact to the same client was required, in order to assess if the product, a bank term deposit, would be subscribed or not; hence, this is a binary classification problem with response variable y taking on values yes/no depending on whether or not the client did/did not subscribe to the bank term deposit. For details and a description of the different columns, visit https://archive.ics.uci.edu/ml/datasets/Bank+Marketing.

Furthermore, I'll do the analysis via one of the R front ends to Apache Spark and MLlib: SparkR [Venkataraman et al., 2016]. Starting with Spark 3.1.1, SparkR also provides a distributed data frame implementation that supports common data wrangling operations like selection, filtering, aggregation, etc. (similar to using data.table or dplyr with R data frames, but on large data sets that don't fit into memory). For instructions on installing Spark, visit https://spark.apache.org/docs/latest/sparkr.html.

While the bank marketing data contain 21 columns on 41,188 records, this is by no means “Spark territory.” However, you may find yourself in a situation where you need to use Spark MLlib for scalable analytics, so I think it’s useful to show how to perform common statistical and machine learning tasks in Spark and MLlib, like fitting RFs, assessing performance, and computing PD plots.

To start, I'll download a zipped file containing a directory with the full bank marketing data set. The code downloads the zipped file into a temporary directory, unzips it, and reads in the CSV file of interest. (If the following code does not work for you, then you may find it easier to just manually download the bank-additional-full.csv and read it into R on your own.)

```r
url <- paste0("https://archive.ics.uci.edu/ml/machine-learning",
                      "-databases/00222/bank-additional.zip")
temp <- tempfile(fileext = ".zip") # to store zipped file
download.file(url, destfile = temp)
bank <- read.csv(unz(temp, "bank-additional/bank-additional-full.csv"),
                 sep = ";", stringsAsFactors = FALSE)
unlink(temp) # delete temporary file
```

Next, I'll clean up the data a bit. First off, I'll replace the dots in the column names with underscores; Spark does not like dots in column names! Second, I'll coerce the response (y) from a factor (no/yes) to a binary indicator (0/1) and treat it as numeric to fit a probability forest/machine. Finally, I'll remove the column called duration. Too often have I seen online analyses of the same data, only for the analyst to be fooled into thinking that duration is a useful indicator of whether or not a client will subscribe to a bank term deposit. If you take care and read the data documentation, you'd notice that the value of duration is not known before a call is made to a client. In other words, the value of duration is not known at prediction time and therefore cannot be used to train a model. This is a textbook example of target leakage. KNOW YOUR DATA! Finally, the data are split into train/test sets using a 50/50 split; I could do this manually, but here I'll use the caret package's createDataPartition() function, which uses stratified sampling to ensure that the distribution of classes is similar between the resulting partitions:

```r
names(bank) <- gsub("\\.", replacement = "_", x = names(bank))
bank$y <- ifelse(bank$y == "yes", 1, 0)
bank$duration <- NULL # remove target leakage
```

```r
# Split data into train/test sets using a 50/50 split
set.seed(1056)
trn.id <- caret::createDataPartition(bank$y, p = 0.5, list = FALSE)
bank.trn <- bank[trn.id, ] # training data
bank.tst <- bank[-trn.id, ] # test data
```

Next, I'll load ggplot2, SparkR, and initialize a SparkSession—the entry point into SparkR (see ?SparkR::sparkR.session for details and the various Spark properties that can be set). If you're new to Spark, start with the online documentation: https://spark.apache.org/docs/latest/index.html; you can also find links to SparkR here as well. Note that SparkR is not on CRAN, but is included with a standard install of Apache Spark. To load SparkR in an existing R session, say, in RStudio, you need
