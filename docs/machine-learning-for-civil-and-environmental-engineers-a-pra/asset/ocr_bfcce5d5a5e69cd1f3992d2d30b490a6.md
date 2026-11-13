![](bbox=[0.112, 0.092, 0.612, 0.285])

```
```r
library(tidyverse)
library(ggplot2)
data=read.csv('C:/Chapter 3.csv ')
data
str(data)
p2<-lines(density(data$Diameter..mm.))
p <- ggplot(data, aes(x=Diameter..mm., y=Yield.strength..MPa.)) +
geom_point() +
theme(legend.position="none")
#marginal histoplot
p5 <- ggMarginal(p, type="boxplot")
```
```

![](bbox=[0.105, 0.515, 0.895, 0.745])

```
```r
library(tidyverse)
library(ggplot2)
data=read.csv('C:/Chapter 3.csv ')
data
str(data)
pairs(data[,1:6],
col = "black",
pch = 16,
main = "A pair plot for dataset")
```
```

Figure 3.4 (Cont'd) Demonstration of a scatter plot (left: unformatted, right: formatted, top: unformatted, bottom: formatted).