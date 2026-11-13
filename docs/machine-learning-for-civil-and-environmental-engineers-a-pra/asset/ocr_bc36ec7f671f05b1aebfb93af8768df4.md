#Required packages for Random-forest regression in R programming language to retrieve the installed-packages above.

```
>>Library (modelStudio) Library (dplyr)
Library (xgboost) Library (DALEX) Library (tidyverse) Library (tidymodels) Library
(caret) Library (Matrix) Library (corrplot)
```

#Data importation: read.csv() function or Data Input function that reads a file from
a local drive in the user’s computer in the form of a table.

```
>>data=read.csv('C:/Classification.csv')
```

#The str() function is used instead of a summary function to exhibit the internal
structure of dataset.

```
>>str(data)
```

#Splitting the dataset into a training and testing set in this example, 70% of the
sample size for training and the 30% left for the testing set.

```
>>smp_size <- floor(0.7 * nrow(data))
```

#Set the seed to ensure a reproducible training and testing set. The sample ()
function is used to isolate a specified size from sample set.

```
>>set.seed(123)
train_ind <- sample(seq_len(nrow(data)), size = smp_size) trainxg <- data[train_ind,
]
testxg<- data[-train_ind, ]
```

#Isolate X and Y for train set

```
>>ytrainxg<-trainxg$Output
xtrainxg<- trainxg %>% select(-Output)
```

#Isolate X and Y for test set

```
>>ytestxg<-testxg$Output
xtestxg<-testxg %>% select(-Output)
```

#Plot histograms for the features we are interested in. Here, we used for loop to
print the histograms for each variable in one function.

```
>>names<-names(data)
>>classes<-sapply(data,class)
for(name in names[classes == 'numeric']){ dev.new()
hist(data[,name])
}
```

#Another approach is to plot histograms for the features using the hist() function
can be found as follows:

```
>>hist(data$Water.binder.ratio)
hist (data$Aggregate.binder.ratio )
hist (data$Sand.binder.ratio )
hist (data$Heating.rate..C.min.) hist (data$Maximum.exposure.temperature..C.)
hist (data$Silica.fume.binder.ratio )
hist (data$Aggregate.size..mm.) hist (data$GGBS.binder.ratio )
hist (data$FA.binder.ratio)
hist (data$PP.fiber.quantity..kg.m3.) hist (data$Output)
```