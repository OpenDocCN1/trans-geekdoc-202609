```
tunedSvmPars
tune result:
Op. pars: kernel=polynomial; degree=1; cost=5.82; gamma=1.56
mmce.test.mean=0.0645372
tunedSvmPars$x
$kernel
[1] "polynomial"
$degree
[1] 1
$cost
[1] 5.816232
$gamma
[1] 1.561584
```

> IMPORTANT Are your values different to mine? They probably are! This is the nature of the random search. It may find different winning combinations of hyperparameter values each time it's run. To reduce this variance, we should commit to increasing the number of iterations it makes.



Now we've tuned our hyperparameters, let's build our model using the best-performing combination. Recall from chapter 3 that we use the setHyperPars() function to combine a learner with a set of pre-defined hyperparameter values. The first argument is the learner we want to use, and the par.vals argument is the object containing our tuned hyperparameter values. We then train a model using our tunedSvm learner with the train() function.



```
tunedSvm <- setHyperPars(makeLearner("classif.svm"),
    par.vals = tunedSvmPars$x)
tunedSvmModel <- train(tunedSvm, spamTask)
```

> TIP As we already defined our learner in code listing 6.8, we could simply have run setHyperPars(svm, par.vals = tunedSvmPars$x) to achieve the same result.



You've built your model using tuned hyperparameters. In this section you'll cross-validate your model to estimate how it will perform on new, unseen data.