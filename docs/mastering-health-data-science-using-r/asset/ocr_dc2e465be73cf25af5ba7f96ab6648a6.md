# 20
Writing Efficient Code

When we talk about efficient code, we are talking about computational efficiency or writing code that is fast to execute. For this topic, we need to peek under the hood to consider how R is implementing our code in order to understand what can slow down our code. We use the **microbenchmark** package (Mersmann 2023) to time our code execution. For demonstration, we use a subset of the pain dataset from the **HDSinRdata** package.

```
```r
library(microbenchmark)
library(HDSinRdata)
library(tidyverse)

data(pain)
pain <- pain %>%
  select(-c(BMI, GH_MENTAL_SCORE, GH_PHYSICAL_SCORE,
            PROMIS_PAIN_BEHAVIOR)) %>%
  na.omit()
```
```

The function `Sys.time()` returns the current system time. This allows us to find the net time required to execute a chunk of code. For example, the following code finds how long it takes to loop through the data to find the number of people who had an improvement in pain.

```
```r
start_time <- Sys.time()
num <- 0
for (i in 1:nrow(pain)){
  if (pain$PAIN_INTENSITY_AVERAGE[i] <=
      pain$PAIN_INTENSITY_AVERAGE.FOLLOW_UP[i]){
    num <- num + 1
  }
}
end_time <- Sys.time()
end_time - start_time
#> Time difference of 0.0198 secs
```
```