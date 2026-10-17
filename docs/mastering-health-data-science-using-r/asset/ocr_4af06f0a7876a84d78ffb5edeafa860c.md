```
```r
#' Euclidean distance
#'
#' @description Calculates the Euclidean distance between two points
#'
#' @param pt1 numeric vector
#' @param pt2 numeric vector
#' @return the Euclidean distance from pt1 to pt2
euclidean_dist <- function(pt1, pt2){
  return((sum((pt1 - pt2)^2))^0.5)
}
```
```

Each comment should start with a pound sign and backtick. The first block of lines is the introduction, and the first line of the comment block is reserved for the title. This is the first information we want the user to know about the function and should be a single line. For all other information besides the title, we use certain tags.

+   - `@description` This tag should be placed first and is a place where you can briefly put more information about the function beyond the title. You can also add more details with the `@details` tag.
+   - `@param` This tag comes before each input argument’s description. For each argument, we want to include the name and type, but we might also include information on how that argument is used.
+   - `@return` This tag documents the returned object and specifies the type. If we are returning a list, then we might include information about each object in the list.

# 18.2.1 Practice Question

Write the documentation for the following coin flip function.

```
```r
#' Insert your solution here:
coin_flips <- function(prob, n = 10){
  results <- rbinom(n = n, size = 1, prob = prob)
  return(list(percent_heads = sum(results)/n, results = results))
}
```
```