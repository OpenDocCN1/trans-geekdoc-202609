# 1. Plot a clustering graph between ROR and cost

Solution:

+   Step 1: Make an Excel-CSV file using the preceding data.
+   Step 2: Open R-Studio.
+   Step 3: Write command:

```
data1 <- read.csv("your CSV file path")
print(data1)
plot(Cost ~ RoR,data1)
```

Now, if you observe figure 1.42, the graph is not dense. So, let us take a dataset from the internet:

![](bbox=[0.273, 0.403, 0.783, 0.633])

Figure 1.42: Clustering of data with RoR and cost

In the following URL, you can find a lot of datasets:

**https://vincentarelbundock.github.io/Rdatasets/datasets.html**

Here, we have used the item aids from the topic of delay in AIDS Reporting in England and Wales. First, download the file from the link and then write the following commands:

```
Data2 <- read.csv ("your CSV file path")
print(Data2)
plot(quarter ~ y,Data2)
```