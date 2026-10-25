# 8.9.4 Example: direct marketing campaigns with XGBoost

In this example, I'll revisit the bank marketing data I analyzed back in Section 7.9.5 using an RF in Spark. Here, I'll fit a GBM using the scalable XGBoost library and show the benefits to early stopping. For brevity, I'll omit the necessary code already shown in Section 7.9.5. To that end, assume we already have the full data set loaded into a data frame called bank.

Next, similar to the RF-based analysis, I'll clean up some of the columns and column names. Since XGBoost requires all the data to be numericP, we have to re-encode the categorical features. The binary variables I'll convert to 0/1, while categorical variables with higher cardinality will be transformed using one-hot encoding (OHE)9. First, I'll deal with the binary variables and column names:

```
names(bank) <- gsub(\\.\\., replacement = "_", x = names(bank))
bank$y <- ifelse(bank$y == "yes", 1, 0)
bank$contact <- ifelse(bank$contact == "telephone", 1, 0)
bank$duration <- NULL # remove target leakage
```

Next, I'll deal with the one-hot encoding. There are several packages that can help with this (e.g., caret's dummyVars() function); I'll do the transformation using pure data.table. The code below identifies the remaining categorical variables (cats) and uses data.table's melt() and dcast() functions to handle the heavy lifting; the left hand side of the generated formula (fo) tells dcast() which variables to not OHE (i.e., the binary and non-categorical features):

```
bank$id <- seq_len(nrow(bank)) # need a unique row identifier
cats <- names(which(sapply(bank, FUN = class) == "character"))
lhs <- paste(setdiff(names(bank), cats), collapse = "+")
fo <- as.formula(paste(lhs, "~ variable + value"))
bank <- as.data.table(bank) # coerce to data.table
bank.ohe <- dcast(melt(bank, id.vars = setdiff(names(bank), cats)),
                  formula = fo, fun = length)
bank$id <- bank.ohe$id <- NULL
```

Now that we have the data encoded properly for XGBoost, we can split the data into train/test sets using the same 50/50 split as before:

```
set.seed(1056) # for reproducibility
trn.id <- caret::createDataPartition(bank.ohe$y, p = 0.5, list = FALSE)
bank.trn <- data.matrix(bank.ohe[trn.id, ]) # training data
bank.tst <- data.matrix(bank.ohe[-trn.id, ]) # test data
```