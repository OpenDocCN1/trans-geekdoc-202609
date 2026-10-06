# 10.3 Decision Trees

RecipeTitanic=recipe(Survived-,, data=DataTrain)

```
ModelDesignDecTree=decision_tree(tree_depth=3) |>
set_engine("rpart") |>
set_mode("classification")
```

The recipe stored in RecipeTitanic does not scale the data because this is not required for Decision Trees and other tree-based machine learning models.

For the model design

In a real-world application the tree_depth might be greater than three, but it should not be too high as to cause overfitting.

To create a fitted workflow, we add the model design and the recipe to a workflow and use fit(DataTrain) to fit the model to the training data:

```
WfModelTitanic=workflow() |>
add_model(ModelDesignDecTree) |>
add_recipe(RecipeTitanic) |>
fit(DataTrain)
```

The resulting object RModelTitanic can be used for predictions and to generate a graphical representation of the fitted Decision Tree:

```
library(rpart.plot)
rpart.plot(extract_fit_engine(WfModelTitanic),
y="YES",text="NO",round=FALSE)
```

The command extract_fit_engine(WfModelTitanic) extracts the model from the workflow WfModelTitanic and the rpart.plot() plots the graphical representation of the fitted Decision Tree (see Figure 10.1).

We will explain how the Decision Tree works in Figure 10.1. For now, we focus on how the tree can be used for predicting survival on the Titanic.

A Decision Tree like the one in Figure 10.1 consists of hierarchically organized nodes (blue and green rectangles). It can be compared to an ancestry tree. The root node on top of the tree has no ancestors but is a parent to two children. Each of these children is a parent to two other children. This process continues until it reaches the bottom of the tree. The terminal nodes at the bottom have parents but no children.