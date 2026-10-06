# 3.11 Exercises: Working with R

When you run the code of the exercise below, the Titanic dataset will be imported to the frame DataFromInternet, and with select(Survived, Name, Sex), you will create a data frame that includes the variables Survived, Name, and Sex from the imported Titanic dataset:

```
library(rio)
library(tidyverse)
DataFromInternet=\import("https://ai.lang-analytics.com/data/Titanic.csv") |>
select(Survived, Name, Sex)
head(DataFromInternet)
```

Your turn: Another tabular dataset containing wine observations imported from the Internet. The dataset contains 3,198 observations about different wines and was initially developed by Cortez et al. (2009). It includes variables about wine color, chemical properties, and an indicator for quality. The dataset is available as a tabular file at: https://ai.lang-analytics.com/data/WineData.rds.

+   - Adjust the import() command to assign the wine dataset to the data DataFromInternet.
- Change the select command to select only the variables wineColor (renamed to WineColor), acidity (renamed to Acidity), and alcohol (renamed to Alcohol).
- Execute the modified code.

# Exercise 13:

When you run the code below, you will create a data frame DataThreeFriends by manually using the data.frame() command. Since variables (columns) of a data frame are similar to vector objects, you can use the c() command to create vector objects that populate the variables for the data.

```
library(tidyverse)
CurrentYear=2024
DataThreeFriends=data.frame(FirstName=c("Carsten", "Jose", "Jane"),
LastName=c("Lange", "Hernandez", "Doe"),
Age=c(45,54,23),
IsFemale=c(FALSE,FALSE,TRUE))
print(DataThreeFriends)
```

```
## Firstname LastName Age IsFemale
## 1 Carsten Lange 45 FALSE
## 2 Jose Hernandez 54 FALSE
## 3 Jane Doe 23 TRUE
```