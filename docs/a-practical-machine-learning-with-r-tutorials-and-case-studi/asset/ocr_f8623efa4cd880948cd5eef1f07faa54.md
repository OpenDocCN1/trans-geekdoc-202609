# 4.7 Using Tidymodels for k-Nearest Neighbors

R will randomly assign 70% of the observations to the training data and the rest to the testing data. The argument strata=Wine uses WineColor as the stratifying variable to ensure that red and white wines are equally represented in the training and testing data.

Finally, we extract the training and testing data from the R object Split7030 and assign them to DataTrain and DataTest, respectively:

```
set.seed(8786)
initial_split(DataWine, prop=0.7, strata=WineColor)
DataTrain=training(Split7030)
DataTest=testing(Split7030)
```

```
## WineColor Sulfur Acidity
## 1 red 37 18.8
## 2 red 38 6.7
## 3 red 12 7.5
## 4 red 25 7.1
## 5 red 114 8.0
## 6 red 66 7.6
```

The first records of DataTrain are printed above for reference. If you like to review the details of splitting a dataset into training and testing data, go to Section 4.3.

Remember that we need to initialize R's random number generator to ensure that the randomly generated training and testing datasets are the same each we run the code (see Section 4.3 for more details).

In this section and throughout the book, we will use recipes from the tidymodels package to pre-process our data. This will simplify data pre-processing and, in addition, clearly show the pre-processing structure.

You can compare a tidymodel recipe to a recipe in a cookbook. First, the ingredients are listed, and then you find the steps to use these ingredients to cook the meal.

```
RecipeWine=recipe(WineColor=Acidity+Sulfur, data=DataTrain)
step_normalize(all_predictors())
step_naomit()
```

Analogous, a tidymodels recipe starts with the command recipe() that selects