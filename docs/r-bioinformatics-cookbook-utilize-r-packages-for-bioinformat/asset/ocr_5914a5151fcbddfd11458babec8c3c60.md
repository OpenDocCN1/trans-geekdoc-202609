# Finding Genetic Variants with HTS Data

This is a clear plot of markers on a simple genetic map.

# There's more...

We can add data of many different types into data tracks with karyoploteR. The following example shows how to draw some numeric data onto a plot as a simple line. The first step is to prepare our data. We create a data.frame object that has 100 random numbers that are put in 100 windows of chromosome 4 and 3, as before, create a GRanges object. This time, we will have a data track above and below our chromosome - one for SNP markers and the other for the new data (note that this is plot-type=2). Then, we need to set the parameters for the plot - in particular, the margins – to stop labels and data overlapping; that's the same plot calls adding a klines() call. The key parameter here is y, which describes the y value of the data at each plotting point:

+   1. Create numeric_data

```
numeric_data <- data.frame(
  y = rnorm(100,mean = 1,sd = 0.5 ,
  chr = rep("chr4", 100),
  start = seq(1,20862711, 20862711/100),
  end = seq(1,20862711, 20862711/100)
)

numeric_data_gr <- makeGRangesFromDataFrame(numeric_data)
```

+   2. Set up plot margins:

```
plot.params <- getDefaultPlotParams(plot.type=2)
plot.params$dataoutmargin <- 800
plot.params$data2outmargin <- 800
plot.params$topmargin <- 800
```

+   3. Create a plot and add tracks:

```
kp <- plotKaryotype(genome=genome_gr, plot.type = 2, plot.params
  = plot.params)
kpMarkers(kp, snps_gr, labels = snp_labels)
kpLines(kp, numeric_data_gr, y = numeric_data$y, data.panel=2)
```