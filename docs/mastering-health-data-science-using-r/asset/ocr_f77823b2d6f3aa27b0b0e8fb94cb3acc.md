```
```r
while(time+next_arrival <= 10){
  # Update list of arrivals and current time
  arrivals <- c(arrivals, next_arrival)
  time <- time + next_arrival

  # Generate the next arrival
  next_arrival <- rexp(1, rate = 3)
}
```
```

Given that we have two types of loops, how do you know which to use? You should use a for loop when you know how many times you go through the loop and/or if there is a clear object to iterate through. On the other hand, while loops are useful if you don’t know how many times you go through the loop and you want to iterate through the loop until something happens. Within a for loop, you can also break out early using the `break` operator. This stops the loop similar to a while loop but is sometimes less succinct. The following code loops through the blood pressure measurements we defined earlier to find if any of the observations meet the criteria for hypertension.

```
```r
# Start with assumption that the result is FALSE
res <- FALSE
for (i in 1:length(sbp_measurements)){

  # If above threshold, update the result and stop the loop
  if (sbp_measurements[i] > 140 | dbp_measurements[i] < 90){
    res <- TRUE
    break
  }
}
```
```

# 17.2.1 Practice Question

Use a loop to find the smallest integer number x such that $2.3^x \ge 100$. The answer should be 6.

```
```r
# Insert your solution here:
```
```