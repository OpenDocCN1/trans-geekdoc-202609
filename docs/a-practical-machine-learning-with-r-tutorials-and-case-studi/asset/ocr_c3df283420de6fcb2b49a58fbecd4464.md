# 5.4 Univariate Mockup: Study Time and Grades

We suggest that you use a finer grid. Copy the code block below into R script. The code includes all commands we used before but uses a finer grid by changing the increment for $eta_1$, from 0.1 to 0.01, creating 201 different $eta_1$ values ranging from 3 to 5 in steps of 0.01. The increment for $eta_2$ is changed from 1 to 0.1, creating 201 different $eta_2$ values ranging from 50 to 70 in steps of. Now the GridBetaPairs is more granular, but it also contains 40,401 rows (201-201) with pairs of $eta$s. The model $R$ has to calculate the $MSE$ for 40,401 pairs of $eta$s. When you execute the code, it will take a while. It took about 15 minutes on a computer with four cores and an Intel $i5$ processor to enjoy while waiting.

Spoiler Alert: In the end, you will get parameters close to the ones we calculated in $OLS^4$.

```
library(rio);library(tidyverse)
FctMSE=import("https://ai.lang-analytics.com/source/FctMSE.rds")
DataMockup=
import("https://ai.lang-analytics.com/data/StudyTimeMockup.rds")

VecBetaValues=seq(3, 5, 0.01) #creates 201 beta values
VecBeta2Values=seq(50, 70, 0.1) #creates 201 beta values

GridBetaPairs=expand.grid(Beta1=VecBetaValues, Beta2=VecBeta2Values)
cat("GridBetaPairs", nrow(GridBetaPairs), "rows.")

MSEMSE=apply(GridBetaPairs, FUN=FctMSE,data=DataMockup,MARGIN=1)

GridBetaPairs=mutate(GridBetaPairs, MSE=min(MSE))

BestModel=filter(GridBetaPairs, MSE=min(MSE))
print(BestModel)
```

In summary, we can say that Grid Search finds optimal parameters for the solution is within the range used for the search and if the grid is fine enough. On the other hand, a more refined grid, unfortunately, increases computing time exponentially as $MSE$ for all combinations to be calculated.

We will use Grid Search in Chapter 6 when tuning hyper-parameters.

> $4$For those who like to push it a little further: Install the future package and load it at the beginning of the code block with library(future.apply). Also, execute the command plan(multisession). Now when you run the code and change the apply() (all arguments as they are), your code will be executed on different cores of your computer and be faster - assuming your computer has two or more cores.