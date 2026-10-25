# 2.9.4 Example: employee attrition

In this example, I'll revisit the employee attrition data (Section 1.4.6) and build a classification tree using rpart with altered priors to help understand drivers of employee attrition and confirm my previous calculations from Section 2.2.4.1.

Figure 2.6 showed two classification trees for the employee attrition data, one using the default priors and one with altered priors based on a specific loss matrix with unequal misclassification costs. In rpart, you can specify the loss matrix, priors, or both—it's quite flexible!

The next code chunk fits three depth-two classification trees to the employee attrition data. The first tree (tree1) assumes equal misclassification costs and uses the default (i.e., observed) class priors. The other two trees use different, but equivalent, approaches: tree2 uses the previously defined loss matrix from Section 2.2.4.1, while tree3 uses the associated altered priors I computed by hand back in Section 2.2.4.1. Although the internal statistics used in constructing each tree differ slightly, both trees are equivalent in terms of splits and will make the same classifications. The resulting tree diagrams are displayed in Figure 2.26.

```
data(attrition, package = "modeldata")

# Fit classification trees with default priors and costs
set.seed(904) # for reproducibility
tree1 <- rpart(Attrition ~ OverTime + MonthlyIncome, data = attrition,
               maxdepth = 2, cp = 0)

# Specify unequal misclassification costs
loss <- matrix(c(0, 8, 1, 0), nrow = 2)
tree2 <- rpart(Attrition ~ OverTime + MonthlyIncome, data = attrition,
               maxdepth = 2, cp = 0, parms = list("loss" = loss))

# Equivalent approach using altered priors
tree3 <- rpart(Attrition ~ OverTime + MonthlyIncome, data = attrition,
               maxdepth = 2, cp = 0,
               parms = list("prior" = c(1 - 0.6059444, 0.6059444)))

# Display trees side by side (Figure 2.26)
par(mfrow = c(1, 3))
tree_diagram(tree1) # default costs and priors
tree_diagram(tree2) # unequal costs
tree_diagram(tree3) # altered priors
```

The subtle difference between tree2 and tree3 is that the within-node class proportions for tree2 are not adjusted for cost/loss; hence, the predicted class probabilities will not match between the two trees. In essence, the tree based on the loss matrix (tree2) makes classifications using a predicted probability