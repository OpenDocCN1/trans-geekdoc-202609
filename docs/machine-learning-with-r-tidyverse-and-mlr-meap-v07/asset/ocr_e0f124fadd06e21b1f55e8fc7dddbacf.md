# Listing 7.10 Exploring the model

```
```r
printcp(treeModelData, digits = 3)

Classification tree:
rpart::rpart(formula = f, data = d, xval = 0, minsplit = 7, minbucket = 3,
    cp = 0.0248179216007702, maxdepth = 5)

Variables actually used in tree construction:
[1] airborne aquatic backbone feathers fins   milk

Root node error: 60/101 = 0.594

n= 101

      CP nsplit rel error
1 0.3333      0      1.000
2 0.2167      1      0.667
3 0.1667      2      0.450
4 0.0917      3      0.283
5 0.0500      5      0.100
6 0.0248      6      0.050
```
```

Remember in section 7.1.3 I showed you how the cp values were calculated:

# EQUATION 7.5

$$\mathrm{cp}=\frac{p(\mathrm{incorrect}_{t+1})-p(\mathrm{incorrect}_t)}{n(\mathrm{splits}_t)-n(\mathrm{splits}_{t+1})}$$

So you can get a better understanding of what the cp value means, let’s work through how the cp values were calculated in the table in code listing 7.10.

The cp value for the first split is:

# EQUATION 7.6

$$\mathrm{cp}=\frac{1.00-0.667}{1-0}=0.333$$

The cp value for the second split is: