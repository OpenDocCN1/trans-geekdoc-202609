```
top_n = 11)
```

#This code shows the XG.boost model importance for all variables in the dataset.

```
>>imp<-xgb.importance(colnames(ytrainxg),model = modelxg) print(imp)
xgb.plot.importance(imp)
```

#Creating explainer model using boost_tree() function as method to generate a model
prepared for further different fitting and DALEX::explain() function as a X-ray to
create explainable model for clarification.

```
>>data$Output<-as.factor(data$Output) fit_xgboost<-boost_tree(learn_rate = 0.3)%>%
set_mode("classification"))%>%
set_engine("xgboost")%>% fit(data$Output~.-1,data=data)
>>data$Output<-as.numeric(data$Output) explainer<-DALEX::explain(
model= fit_xgboost, data = data, y=data$Output, label = "XGBoost"
)
```

#Calling Model studio to visualize the model which automates the explanatory analy-
sis of machine learning model.

```
modelStudio::modelStudio(explainer = explainer)
```

#Required packages for XGboost classification in R programming language to call the
specified packages.

```
library(modelStudio)
library(dplyr)
library(xgboost)
library(DALEX)
library(tidyverse)
library(tidymodels)
library(caret)
library(magrittr)
library(Matrix)
library(corrplot)
```

#Data importation.

```
data<-read.csv('C:/Classification.csv')
```

#Checking the structures lay behind the dataset.

```
str(data)
'data.frame':646 obs. of 11 variables:
$ Water.binder.ratio...: num 0.273 0.273 0.3 0.218 0.218 0.3 0.3 0.3 0.273 0.273 ...
$ Aggregate.binder.ratio...: num 2 2 2 1.37 1.37 ...
$ Sand.binder.ratio...: num 1.05 1.05 1.03 1.2 1.2 ...
$ Heating.rate...C.min.: num 101 101 101 101 101 101 101 101 101 ...
$ Maximum.exposure.temperature...C.: int 1034 1034 1034 1034 1034 1034 1034 1034 1034 1034 ...
1034 ...
$ Silica.fume.binder.ratio...: num 0 0 0 0 0 0 0 0 0 0 ...
$ Aggregate.size...mm.: num 7 14 20 7 7 14 20 20 7 14 ...
$ GGBS.binder.ratio...: num 0.25 0.25 0.25 0.25 0.25 0.25 0.25 0.25 0.25 0.25 ...
$ FA.binder.ratio...: num 0 0 0 0 0 0 0 ...
$ PP.fiber.quantity...kg.m3.: num 0 0 0 0 0 0 0 0 0 0 ...
$ Output: int 1 1 1 1 1 1 1 1 1 ...
```