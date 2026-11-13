shown in this paper that not all observations carry the same amount of signal. Instances with ‘average’ label values seem to be on average less informative compared to those with extreme label values.

# 4.8 Additional code and results

# 4.8.1 Impact of rescaling: graphical representation

We start with a simple illustration of the different scaling methods. We generate an arbitrary series and then rescale it. The series is not random so that each time the code chunk is executed, the output remains the same.

```
Length <- 100 # Length of the sequence
x <- exp(sin(1:Length)) # Original data
data <- data.frame(index = 1:Length, x = x) # Data framed into dataframe
ggplot(data, aes(x = index, y = x)) + geom_bar(stat = "identity") # Plot
```

![](bbox=[0.145, 0.403, 0.893, 0.642])

We define and plot the scaled variables below.

```
norm_unif <- function(v){ # This is a function that uniformises a vector.
  v <- v %>% as.matrix()
  return(ecdf(v)(v))
}

norm_0_1 <- function(v){ # This is a function that uniformises a vector.
  return((v-min(v))/(max(v)-min(v))))
}

data_norm <- data.frame(
  index = 1:Length,
  standard = (x - mean(x)) / sd(x),
  norm_0_1 = norm_0_1(x),
  unif = norm_unif(x) %>%
  gather(key = Type, value = value, -index)
ggplot(data_norm, aes(x = index, y = value, fill = Type)) + # Plot!
```