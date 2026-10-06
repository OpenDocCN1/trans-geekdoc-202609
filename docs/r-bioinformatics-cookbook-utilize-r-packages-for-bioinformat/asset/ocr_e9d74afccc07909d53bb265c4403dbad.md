# How to do it...

To estimate batch effects using SVA, follow these steps:

+   1. Load the necessary libraries and data:

```
library(sva)
library(rbioinfcookbook)
```

+   2. Filter out the rows with too few counts in some experiments:

```
keep <- apply(arab_infection, 1, function(x) {length(x>3)}) >=2
arab_filtered <- arab_infection[keep, ]
```

+   3. Create the initial design:

```
groups <- as.factor(rep(c("mock", "hrcc"), each=3))
```

+   4. Set up the test and null models and run SVA:

```
test_model <- model.matrix(-groups)
null_model <- test_model[,1]
svar <- svaseq(arab_filtered, test_model, null_model, n.sv=1)
```

+   5. Extract the surrogate variables to a new design for downstream use:

```
design <- cbind(test_model, svar$v)
```

And that's all we need to do to generate a new model design for statistical analyses.

# How it works...

In step 1, the sva and rbioinfcookbook libraries are loaded. These libraries provide functions for performing SVA and the data needed for this book, respectively.

In step 2, the arab_infection is filtered to keep the rows that have at least two counts greater than 3 using the apply function. The function is used to apply a function to each row of arab_infection. The function that is being applied checks the number of counts in the row that are greater than 3 and only keeps the row if this number is greater or equal to 2. The filtered data is stored in the arab_filtered variable.

In step 3, the groups variable is set as a factor, which is a categorical variable that can take on one of two values, mock or hrcc, which are repeated three times each.