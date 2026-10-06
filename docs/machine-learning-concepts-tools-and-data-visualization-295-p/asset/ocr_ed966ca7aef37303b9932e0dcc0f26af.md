# 262 Machine Learning: Concepts, Tools and Data Visualization

![](bbox=[0.095, 0.085, 0.893, 0.396])

Figure 12-30 Language data pie chart

# Source (12-30)

```
```
# dataset <- data.frame(lang)
# dataset <- unique(dataset)
set.seed(1)
lang <- sample(x=1:5, size=100, replace=TRUE)
lang <- c("R", "JAVA", "Python", "C", "Swift")[lang]
Lang_data <- data.frame(lang)
Lang_tab <- table(Lang_data)
pie(Lang_data.tab, main="Language Pie Chart")
```
```

You can see that the pie chart has been created, as shown in Figure 12-30.

# 12.3.3 Numerical Bivariate Plot

Before drawing a numerical bivariate plot, you need to install a package to import the Galton data. Enter the following code in R Studio, as shown in Figure 12-31. Set the appropriate region for downloading, and the download will begin.

After the download is completed, enter the following source into R Studio, as shown in Figure 12-32. You can check the structure of the data through the dim () function.