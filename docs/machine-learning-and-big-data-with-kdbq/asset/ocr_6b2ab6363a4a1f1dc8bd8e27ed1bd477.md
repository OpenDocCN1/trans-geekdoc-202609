# 512

# MACHINE LEARNING

The scheme to create binned is defined as three split points:

```
binPoints: (:0.1 0.2 0.3);
```

We can finally create bucket by using the binr verb:

```
binPoints binr arrayOffFloats
```

3j, 0j, 2j, 3j, 3j, 2j, 1j, 2j, 3j

The Apriori algorithm is then operating with the binned feature, and the underlying correct numerical values do not play any role for the algorithm itself.
We can now safely assume that our underlying features are of the integer type and the Apriori algorithm builds on the integer-valued features. We convert each integer-valued feature into a list of dummies, where for every possible value of the feature there is a separate binary variable. First, we need to create a function which goes over all possible values of a feature and create a dictionary with dummies:

```
.quantQ.apriori.makeDictionary::[[x]
/ x -- list of discrete unique variables
/ x!x:=x
;
```

The function works as follows:

```
.quantQ.apriori.makeDictionary[1 2 3]
```

```
(1j, 2j, 3j)!(100b;010b;001b)
```

We create a function which identifies in the underlying data table an i-th feature and creates another table with an additional set of dummy variables by using the function defined in the previous display. The function:

```
.quantQ.apriori.createDummies::[[largeTab,i]
// LargeTab -- table to convert
// index of variable to convert
// get all variables except the first one
listCols: largeTab,
// unique values of selected variable
distTMP: asc distinct largeTab[listCols[i]]
// create dictionary
dictTMP: quantQ.apriori.makeDictionary[distTMP]
// vector of values to convert
tabTMP: largeTab[listCols[i]]
// dummy variables
?:(largeTab);0b;(`raise string listCols[i],"_");string til count
-- distTMP!flip (dictTMP tabTMP]);
;
```