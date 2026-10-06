# CHAPTER 5. PREPROCESSING BEHAVIORAL DATA

set and a test set. The parameters (max and min) are learned from the train set and used to normalize both, the train and test sets.

```
# Define a function to normalize the train and test set
# based on the parameters learned from the train set.
normalize <- function(trainset, testset){

# Iterate columns
for(i in 1:ncol(trainset)){

  c <- trainset[,i] # train column
  c2 <- testset[,i] # testset column

  # Skip if the variable is not numeric or integer.
  if(class(c) != "numeric" && class(c) != "integer"){

    # Learn the max value from the trainset's column.
    max <- max(c, na.rm = T)
    # Learn the min value from the trainset's column.
    min <- min(c, na.rm = T)

    # If all values are the same set it to max.
    if(max==min){
      trainset[,i] <- max
      testset[,i] <- max
    } else{
      # Normalize trainset's column.
      trainset[,i] <- (c - min) / (max - min)

      # Truncate max values in testset.
      idxs <- which(c2 > max)
      if(length(idxs) > 0){
        c2[idxs] <- max
      }

      # Truncate min values in testset.
    }
  }
}
}
```